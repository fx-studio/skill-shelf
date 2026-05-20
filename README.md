# skill-shelf

A small, growing shelf of [Claude Skills](https://www.anthropic.com/news/skills) — each one solves a narrow problem well, none of them try to be a platform.

Pick what you need. Leave the rest on the shelf.

---

## What's a skill?

A skill is a folder Claude reads on demand. Drop in a `SKILL.md` (the instructions), plus any reference files, scripts, or templates the task needs. When you ask Claude something that matches the skill's description, it loads the folder and follows the playbook.

Think of it as muscle memory you can copy-paste. Instead of re-explaining "here's how I want my diagrams rendered" every conversation, you write it once and Claude reaches for it automatically.

Skills here follow a rule: **small surface, real use, no ceremony.** If a skill needs a five-paragraph intro to justify itself, it doesn't belong on this shelf yet.

---

## On the shelf

> Skills are organized by what they help you do, not by what they're built on.

| Skill | What it does | When to reach for it |
|---|---|---|
| _(populate as you publish)_ | | |

Each skill folder is self-contained. Read its `SKILL.md` to see the trigger conditions, required inputs, and example outputs.

---

## Philosophy

A few things I've learned building these:

**Narrow beats general.** A skill that does one thing well is worth ten skills that do everything okay. If you find yourself adding "also handles X, Y, Z" to a description, split it.

**Trigger description is the product.** Claude only loads a skill when its description matches the request. A vague description means the skill never fires. Spend more time on the description than on the body.

**Reference files over inline rules.** If a skill has a 30-line checklist, put it in a separate file the skill reads when needed. Keep `SKILL.md` itself short — it's loaded into every conversation that touches the skill's domain.

**Skills compose.** Two small skills used together usually beat one big skill that tries to anticipate the combination.

**Small daily value > big rare value.** A skill that saves you 90 seconds five times a week is more valuable than one that saves an hour once a quarter — because you'll actually use it.

---

## Install

### Claude (web / desktop / mobile)

1. Open Settings → **Capabilities** → **Skills**
2. Click **Upload skill** and select the skill's folder (zipped) or the individual files
3. The skill is now available in any conversation — Claude decides when to use it based on the description

### Claude Code

```bash
# Project-scoped (recommended for team skills)
mkdir -p .claude/skills/<skill-name>
cp -r path/to/skill/* .claude/skills/<skill-name>/

# User-scoped (available across all your projects)
mkdir -p ~/.claude/skills/<skill-name>
cp -r path/to/skill/* ~/.claude/skills/<skill-name>/
```

Restart Claude Code and the skill is picked up.

### API / agent frameworks

Skills are just folders with a `SKILL.md` at the root. Most agent frameworks let you load them as system context or as tools. Check the framework's docs for the loader pattern.

---

## Skill anatomy

Every skill on this shelf follows the same minimal structure:

```
<skill-name>/
├── SKILL.md           # Required. Description + instructions.
├── reference/         # Optional. Files Claude reads when needed.
├── scripts/           # Optional. Helper scripts the skill can run.
└── examples/          # Optional. Sample inputs/outputs.
```

`SKILL.md` starts with frontmatter:

```yaml
---
name: my-skill
description: One sentence on what it does. Trigger conditions on when to use it.
---
```

The description is the most important line in the whole skill. Claude reads only the description first; it loads the rest only if the description matches.

A good description names the **task**, the **triggers** (keywords, file types, contexts), and ideally a **non-trigger** (when not to use it). Bad descriptions say "helps with X" — vague, ambiguous, low recall.

---

## Contributing

PRs welcome. The bar:

- **Solves one thing.** If the skill needs a mode selector or a sub-command tree, it's probably two skills.
- **Has a sharp description.** Someone reading just the description should know whether their task matches.
- **Is testable.** Include at least one example in `examples/` so behavior is observable.
- **Doesn't duplicate.** Check the shelf first. Improving an existing skill beats adding a near-duplicate.

If you're not sure whether your idea fits, open an issue first. I'd rather discuss the shape than reject a PR.

---

## What's not here

Not every useful prompt deserves a skill. Some things this repo intentionally doesn't host:

- **One-off prompts.** If you'll use it twice and never again, just paste it. Skills are for repeated use.
- **Wrappers around basic Claude capabilities.** Claude already writes code, summarizes documents, and translates. A skill that says "write code well" isn't a skill.
- **Skills that need credentials or paid services to even read.** Skills here should be inspectable end-to-end without an account.

---

## License

MIT. Use them, fork them, modify them, ship them in your own products. A credit link back is appreciated but not required.

---

## Acknowledgments

Built with [Claude](https://claude.com) by Anthropic. The skill format is theirs; the contents here are mine and contributors'.

If a skill saves you an afternoon, consider opening a PR with one of your own. That's the only currency this shelf trades in.
