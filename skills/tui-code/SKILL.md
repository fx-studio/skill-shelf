---
name: tui-code
description: Disciplined code-generation workflow for the team. Use this skill whenever the user asks to write, add, implement, fix, refactor, or otherwise change code in the repo — including casual Vietnamese phrasings like "viết tính năng", "thêm chức năng", "sửa bug", "refactor", "sửa code" — even if they don't explicitly ask for planning or documentation. It auto-classifies the task on a 5-rung rigor ladder (TRIVIAL/SMALL/MEDIUM/LARGE/SPEC) to decide documentation depth and whether to plan before coding. Goal: solve two pains — (1) code is unreadable the next day, and (2) code gets generated before the task is understood. Do NOT use it for pure theory questions, documentation lookups, concept explanations, or any answer that does not change code.
allowed-tools: Read, Write, Edit, Bash, Grep, Glob
---

# tui-code

> Write code that still makes sense tomorrow. Auto-pick a rigor rung, plan only when it pays off, always leave traces.

## Why this skill exists

Vibe coding is fast but tends to produce code that nobody understands the next day, and to start generating before the task is actually understood. This skill fixes both by adding a tiny, size-proportional amount of structure — and by having Claude do the structure work so the human only reviews it. Keep friction low: tiny tasks should feel almost the same as before; only large tasks earn a real plan.

### Core principles

- **Friction scales with size.** Never force a plan for a few-line change. The whole skill fails the moment it feels like paperwork.
- **Claude writes the plan/notes; the human reads and approves or tweaks.** Don't make people write documentation by hand.
- **Comments explain WHY, not what the code does.** The "why" is what's missing the next day, not the syntax.
- **Silent at low rungs, vocal at high rungs.** Trivial and small changes just appear, with no commentary. Medium and up surface a plan, because at that size the plan is the thing worth reviewing.

### Language policy

- Instructions in this file are in English (better model adherence).
- Everything a human on the team reads stays in Vietnamese: the `--menu` text, the plan/spec file templates, and the chat plan at the MEDIUM rung.
- Code comments follow the language already used in the codebase; default to Vietnamese if there is no established convention.

---

## Activation

This skill auto-loads whenever a request touches code (write / fix / refactor). It is also exposed as the `/tui-code` slash command for explicit control.

### Slash command + flags

```
/tui-code <request>            -> DEFAULT (auto-pick rung 1-4)
/tui-code --plan <request>     -> force rung 4 (LARGE)
/tui-code --spec <request>     -> force rung 5 (SPEC)
/tui-code --quick <request>    -> cap at rung 2 (SMALL), drop all ceremony
/tui-code --menu               -> print the guide, do NOT generate code
```

The request text arrives as `$ARGUMENTS`. Detect any `--xxx` token inside it and act per the flag table. When the skill auto-loads from a natural prompt (no slash command, no flag), treat it as DEFAULT.

### Flag table

| Flag | Effect |
|---|---|
| (none) | DEFAULT — auto-pick rung 1-4 by size |
| `--plan` | Force rung 4: always write a plan file for approval before coding, even if the task looks small |
| `--spec` | Force rung 5: write spec file + plan file + code + reconciliation review |
| `--quick` | Cap at rung 2: skip plan/file/approval-gate/review, only inline comments + function headers |
| `--menu` | Print the guide block at the end of this file; do not generate code |

### Flag precedence

`--menu` > `--spec` > `--plan` > `--quick` > auto. If the user passes conflicting flags (e.g. `--quick --spec`), follow this order and state in one short line which rung was chosen.

---

## The 5-rung ladder

| Rung | When | Documentation | Artifact | Approval gate |
|---|---|---|---|---|
| 1 TRIVIAL | 1 file, <=~10 lines, rename / typo / constant / string, no logic change | Inline comment only where the reason isn't obvious | — | None |
| 2 SMALL | 1-2 files, one function/component, self-contained bug fix, no sensitive area | + function header (purpose / input / output / main logic) | — | None |
| 3 MEDIUM | A few functions or 2-3 files, small feature / in-module refactor | Documentation-style docstrings | Plan shown in **chat** | Soft (show, then code in the same turn) |
| 4 LARGE | Many files / cross-module, cross-layer feature, public API change, OR touches a sensitive area | Full documentation | **File** in `docs/plans/` | Hard (approve the file, then code) |
| 5 SPEC | Only via `--spec`: large/high-risk work needing a spec | Full documentation | **Files** in `docs/specs/` + `docs/plans/` | Hard (approve spec, then approve plan) |

DEFAULT auto-selects rungs 1-4. Rung 5 is reachable only via `--spec`.

A note on auto-loading: Claude tends to skip consulting a skill for trivially simple one-step asks. That's fine here — a true TRIVIAL change is meant to be near-invisible anyway. The skill matters most from SMALL upward, which is exactly where it reliably engages.

---

## Rung detection (for DEFAULT)

Estimate from **countable** signals, not vibes:

- Number of files touched, lines changed, new functions/logic units.
- 1 file + tiny change -> rung 1. Contained to one function -> rung 2. A few functions / 2-3 files -> rung 3. Cross-module / many files -> rung 4.

**Mandatory escalation (minimum rung 4):** if the change touches auth/permissions, money/payments, data migration, concurrency, timezone, or an external service integration, escalate to rung 4 regardless of line count. These areas fail quietly and expensively, so they always deserve a written plan.

When torn between two rungs, **pick the lower one** (less friction). The user can always force up with `--plan`/`--spec` or down with `--quick`.

---

## Per-rung behavior

**Rung 1 — TRIVIAL.** Make the change, stay silent. Add an inline comment only if the reason for the change isn't obvious.

**Rung 2 — SMALL.** Generate immediately, stay silent. Each function/main unit gets a short header: purpose, input, output, main logic.

**Rung 3 — MEDIUM.** Before coding, show a simple plan in chat:
```
[PLAN]
• Hiểu đề: <restate the request in your own words>
• Cách làm: <2-4 steps>
• Đụng vào: <files/functions>
• Lưu ý: <edge cases if any>
```
This is a **soft gate**: show the plan, then generate code in the SAME turn (the plan lets the user glance and stop if it's wrong, without typing "ok"). Code carries documentation-style docstrings.

**Rung 4 — LARGE.** Before coding, write a **plan file** into `docs/plans/`, then **STOP** and ask the user to open the file and approve. Only code after approval. Full documentation. Reuse the plan file content as the PR description.

**Rung 5 — SPEC.** In order:
1. Write a **spec file** into `docs/specs/`. Stop, wait for spec approval.
2. Write a **plan file** into `docs/plans/`. Stop, wait for plan approval.
3. Generate documented code.
4. **Reconciliation review** of the new code against the spec + plan (see Review section).

---

## Approval gate & durability rule

For rungs 4-5, anchor the approval gate to the **file on disk**, not to session memory. Claude Code sessions are continuous, but context can be compacted and the skill may not be re-consulted on a later turn — the file keeps the gate reliable regardless.

- The plan/spec file on disk is the **durable source of truth**.
- When the user approves later (e.g. "ok làm đi"), read the **most recent** plan/spec file in `docs/plans/` (or `docs/specs/`) and implement exactly against it.
- Rung 3 (chat plan) deliberately uses a soft gate (plan then code in one turn), so nothing depends on a cross-turn handoff.

---

## Plan/spec file conventions

**Directories:** plans in `docs/plans/`, specs in `docs/specs/`. Create them if missing.

**Filename:** date-time prefix + a slug summarizing the request (no diacritics, hyphen-joined):
```
docs/plans/2026-05-29-1430-loc-don-hang-theo-ngay.md
docs/specs/2026-05-29-1430-loc-don-hang-theo-ngay.md
```
Prefix format: `YYYY-MM-DD-HHMM-<slug>.md`. Get the timestamp with `date +%Y-%m-%d-%H%M`.

**Plan file template (Vietnamese, human-facing):**
```
# Plan: <tên việc>   (<ngày giờ>)

## Hiểu đề
<restate the request in your own words>

## Các bước
1. ...
2. ...

## File sẽ đụng tới
- path/to/file — what changes

## Rủi ro / điểm cần chốt
- ...

## Còn nợ (TODO)
- ...
```

**Spec file template (rung 5, Vietnamese, human-facing):**
```
# Spec: <tên việc>   (<ngày giờ>)

## Mục tiêu
<problem to solve, why>

## Phạm vi
- Trong phạm vi: ...
- Ngoài phạm vi: ...

## Tiêu chí chấp nhận
- [ ] ...
- [ ] ...

## Ràng buộc / giả định
- ...
```

After merge, the file content has already gone into the PR description; the team may archive or delete the file to keep the repo clean (team policy — the skill does not auto-delete).

---

## Review step (rung 5 only)

This is a **reconciliation**, not a quality audit — and it is self-grading, so don't expect it to catch subtle bugs. Follow the checklist and report plainly:

```
[REVIEW đối chiếu]
- Acceptance criteria in the spec: which are met / not met
- Drift from the plan: which step/file differs, and why
- Remaining TODOs in the code
- Risks listed in the spec: handled or not
```
No vague "looks good" conclusion. Just item-by-item reconciliation.

---

## Documentation rules (all rungs)

- **Comment = WHY:** why this approach, what trade-off, why not the obvious way. Don't write comments that narrate what the code is doing.
- **Docstring = CONTRACT:** purpose, input/output, assumptions.
- **Name things clearly.** No `data`, `tmp`, `handle2`.
- **Mark debt** with `TODO:` / `FIXME:` right where it is, with a short reason.
- Comment in the language already used in the codebase; default to Vietnamese if none is established.
- **Don't over-document.** Documentation at high rungs means docstrings + "why" comments at the hard spots, not comments sprinkled everywhere. Excess comments make code harder to read — the very thing this skill fights.

**Example — comment quality:**
Input: `// loop through the orders and filter by date`
Output: `// Lọc theo giờ server, không theo client TZ, để tránh lệch ngày giữa các múi giờ`

---

## Silent / vocal rule

- **Rungs 1-2:** run silently. Just emit code. No "I classified this as SMALL so...", no preamble/postamble.
- **Rungs 3+:** surface the plan (that's the value to review). Add nothing beyond plan + code + (rung 5) review.

---

## What this skill does NOT do

- Doesn't change architecture beyond the request. Surgical changes, touch only what's needed, match existing style.
- Doesn't delete/edit unrelated nearby code (mention dead code, don't remove it).
- Doesn't write tests unless asked (keep v1 scope tight).
- Doesn't run dangerous commands (delete branches, force push, modify production...).

---

## --menu block

On `--menu` (or when the user asks how to use it), print exactly the block below and do NOT generate code:

```
TUI-CODE — viết code để hôm sau đọc vẫn hiểu

Tự động chạy khi bạn yêu cầu viết/sửa/refactor code.
Gọi thủ công: /tui-code [--flag] <yêu cầu>

Flag:
  (không flag)   Tự dò nấc theo quy mô việc
  --plan         Ép lập file plan để duyệt rồi mới code
  --spec         Ép làm spec + plan + code + review đối chiếu
  --quick        Làm gọn, bỏ mọi nghi thức (chỉ comment nhẹ)
  --menu         Hiện hướng dẫn này

5 nấc rigor (tự xếp khi không có flag):
  1 TRIVIAL  sửa vài dòng        -> comment inline
  2 SMALL    1 hàm / bug nhỏ     -> + header hàm (in/out/xử lý)
  3 MEDIUM   vài hàm / 2-3 file  -> plan ở chat + docstring
  4 LARGE    liên module/nhạy cảm-> file plan duyệt + document-hóa
  5 SPEC     việc lớn rủi ro cao -> file spec + plan + review

File plan ở docs/plans/, spec ở docs/specs/
Tên file: YYYY-MM-DD-HHMM-<tom-tat>.md

Mẹo: việc chạm auth/tiền/migration/timezone luôn tự nâng lên nấc 4.
```
