# Output Templates for AI Frontier Watch Agent

## Template A — Daily Brief

```markdown
# AI Frontier Daily Brief — {{DATE}}

## 1. TL;DR
- {{Top development 1 + ai cần action}}
- {{Top development 2}}
- {{Top development 3}}

## 2. Critical & High Priority

### {{Title}}
- Category: {{Model / Agent / Research / Open-source / Infra / Safety / Policy / Business / Tooling}}
- Priority: {{Critical / High}}
- Source: {{Tier 1/2/3 + link}}
- Date: {{YYYY-MM-DD}}
- Deadline: {{YYYY-MM-DD if any / "N/A"}}
- Summary: 2-3 câu
- Why it matters: Tác động cụ thể tới AI builder/team
- Who should act: {{Builder / Researcher / PM / Founder / Compliance / Infra / Data scientist}}
- Recommended action: Cụ thể
- Scores: R{{x}} N{{x}} I{{x}} A{{x}} C{{x}}

## 3. Frontier Model Releases
- {{Item 1 ngắn + link, kèm benchmark label}}

## 4. AI Agents & Tool Use
- {{Item với benchmark version rõ}}

## 5. Research Papers Worth Reading

### {{Paper title}}
- Source: {{arXiv link / HF Papers}}
- Date: {{}}
- Status: {{Preprint / Peer-reviewed / Industry}}
- Problem: {{}}
- Method: {{Core idea}}
- Key result: {{Benchmark + score}}
- Code: {{Yes/No/Unknown}}
- Limitations: {{}}
- Why read: {{}}
- Action: {{Read / Test / Monitor / Skip}}

## 6. Open-source AI
- {{Items}}

## 7. AI Safety, Security & Policy
- {{Items with deadline}}

## 8. Infrastructure & Developer Tooling
- {{Items, pricing change nếu có}}

## 9. Business & Strategic Signals
- {{Items}}

## 10. Action Items
| Action | Who | Deadline | Priority |
|---|---|---|---|

## 11. What to Watch Next
- {{Signals}}
```

---

## Template B — Weekly Brief

```markdown
# AI Frontier Weekly Brief — {{DATE RANGE}}

## 1. Executive Summary
- {{Trend 1}}
- {{Trend 2}}
- {{Trend 3}}

## 2. What Changed This Week — by Trend

### Trend 1: {{e.g., "Coding agents diverge by use case"}}
- Evidence: {{Sources}}
- Why it matters: {{}}
- Confidence: {{High/Medium/Low}}
- Affected: {{Roles}}
- Watch next: {{}}

## 3. Major Releases This Week

### Frontier Models
| Model | Lab | Release | Key capability | Benchmark | Pricing |
|---|---|---|---|---|---|

### Agent Platforms
| Platform | Update | Significance |
|---|---|---|

### Open-source
| Model/Tool | Lab | License | Key fact |
|---|---|---|---|

## 4. Research Papers (top 5 of the week)
{{Full schema per paper: problem / method / result / code / limits / why read}}

## 5. Benchmark Updates
- {{New benchmark / contamination / shift}}

## 6. Open-source AI Ecosystem
{{Items}}

## 7. AI Infrastructure
{{Chips, serving, pricing, capacity}}

## 8. Safety, Security & Governance
| Item | Region | Effective | Action |
|---|---|---|---|

## 9. Business & Enterprise Signals
{{Funding, deals, deployment stories with numbers}}

## 10. Competitive Landscape Snapshot
| Lab | Capability move | Agent move | Pricing move | Open-source move | Safety move |
|---|---|---|---|---|---|

## 11. Contradictions / Unresolved
{{When sources disagree}}

## 12. Action Items (consolidated)
| # | Action | Role | Deadline | Priority | Reference |
|---|---|---|---|---|---|

## 13. What to Watch Next Week
- {{Signals}}
```

---

## Template C — Deep Dive

```markdown
# Deep Dive: {{TOPIC}} — {{Date}}

## 1. Bottom Line
{{One paragraph: current state + what team should do}}

## 2. Background
{{Context: why this matters for AI builder/team}}

## 3. Timeline
- {{Date}}: {{Event}}

## 4. Primary Sources
- {{Source 1}}
- {{Source 2}}

## 5. Technical Details
{{Specific architecture / method / API}}

## 6. Impact on Different Roles
### Builders
{{Specific impact}}

### Researchers
{{Specific impact}}

### Product / Founder
{{Specific impact}}

### Compliance / Legal
{{Specific impact}}

## 7. Migration / Adoption Path
- Step 1: {{}}
- Step 2: {{}}

## 8. Risks
- {{Risk 1}}
- {{Risk 2}}

## 9. Cost Analysis
{{Effort, blockers, dependencies}}

## 10. Open Questions
{{Questions}}

## 11. What to Monitor Next
- {{Signal 1}}

## 12. Recommended Actions
| # | Action | Owner | Deadline | Effort |
|---|---|---|---|---|
```

---

## Template D — Model Release Report

```markdown
# Model Release Report: {{Model Name}} — {{Date}}

## 1. Headline
- Lab: {{}}
- Type: {{Frontier / Open-weight / Reasoning / Multimodal / SLM}}
- Status: {{Research preview / Public beta / GA}}
- Released: {{YYYY-MM-DD}}

## 2. Capabilities (verified)
| Benchmark | Score | Source | Notes |
|---|---|---|---|
| SWE-bench Verified | {{}} | {{lab / Artificial Analysis / 3rd party}} | {{contamination caveat?}} |
| SWE-bench Pro | {{}} | {{}} | |
| GPQA Diamond | {{}} | {{}} | |
| Humanity's Last Exam | {{}} | {{}} | |
| MMLU-Pro | {{}} | {{}} | |
| Terminal-Bench 2.0 | {{}} | {{}} | |
| GDPval | {{}} | {{}} | |
| AIME | {{}} | {{}} | |

## 3. Architecture & Technical
- Parameter count: {{if known}}
- Context window: {{in tokens}}
- Output limit: {{}}
- Modalities: {{text / image / audio / video}}
- Reasoning mode: {{Yes / No / Optional}}

## 4. Pricing
| Tier | Input ($/M tok) | Output ($/M tok) | Notes |
|---|---|---|---|
| Standard | | | |
| Cached input | | | |
| Batch API | | | |

## 5. Access
- API: {{available endpoints, regions}}
- Web: {{ChatGPT/Claude.ai/Gemini app integration}}
- Open-weight: {{license, HF link}}

## 6. Safety / System Card
- Safety evaluation summary
- Pre-deployment access (US AISI / UK AISI)
- Known limitations from system card
- Refusal/safety category

## 7. Competitive Context
| vs | Coding | Reasoning | Multimodal | Cost | Speed |
|---|---|---|---|---|---|

## 8. Strengths
- {{}}

## 9. Weaknesses / Caveats
- {{}}

## 10. Recommended Use Cases
- {{Use case 1}}
- {{Use case 2}}

## 11. Recommended Action for Team
| Action | Owner | Effort | Timeline |
|---|---|---|---|
| Run our own eval on production tasks | ML eng | 2-3 days | Sprint |
| Update model selection guide | Tech Lead | 1 day | Next week |
| Cost re-projection | Finance/Eng | 0.5 day | This sprint |
| Migrate {{specific use case}} | Builder | TBD | After eval |

## 12. Open Questions
- {{}}
```

---

## Template E — Paper Digest

```markdown
# AI Paper Digest — {{Date Range}}

## Top Picks (5-7 papers)

### {{Paper title}}
- Authors: {{}}
- Affiliation: {{Lab / University / Industry}}
- Source: {{arXiv link / venue}}
- Status: {{Preprint / Submitted to {{venue}} / Accepted {{venue}}}}
- Date: {{}}
- Code: {{GitHub link / Not available}}

**Problem**: {{1-2 câu}}

**Method**: {{Core idea, có thể có sub-bullet}}
- {{Component 1}}
- {{Component 2}}

**Key results**:
- {{Result 1: benchmark X, score Y, vs baseline Z}}
- {{Result 2}}

**Limitations**:
- {{From paper's own discussion}}
- {{Independent observation if any}}

**Why read**: {{For builder / researcher / both}}

**Recommended action**: {{Read / Test / Watch for follow-up / Skip}}

---

(Repeat for each paper)

## By Theme

### Theme 1 (e.g., "Reasoning models improvements")
{{1-line synthesis across papers in this theme}}

### Theme 2 (e.g., "Agent memory architectures")
{{}}

## Notable but not deep-dived (mention only)
- {{Paper title}} — {{1 line}}

## Code & Reproducibility Watch
- Released with code: {{count, list}}
- No code: {{count}}
- Notable replication / failed replication: {{}}
```

---

## Template F — Policy & Compliance Alert

```markdown
# AI Policy Alert: {{Policy Name}} — {{Date Issued}}

## Severity
{{Critical / High / Medium}}

## Summary
{{1-2 câu policy là gì}}

## Effective Date
{{YYYY-MM-DD}} ({{Number of days from today}})

## Region Applied
{{EU / US (federal/state) / UK / China / Korea / Japan / Vietnam / Global}}

## AI Systems Affected
- {{Type 1: e.g., GPAI models}}
- {{Type 2: e.g., GPAI with systemic risk}}
- {{Type 3: e.g., High-risk Annex III}}

## Required Action
1. {{}}
2. {{}}

## Penalty
- {{Max fine: e.g., €35M or 7% global turnover for prohibited practices}}
- {{Lower tier: e.g., €15M or 3% for GPAI obligations}}

## Reference
- Official source: {{regulator link}}
- Code of Practice / guideline: {{}}
- Related lawsuit / enforcement action: {{if any}}

## Internal Action Plan
| # | Action | Owner | Deadline | Status |
|---|---|---|---|---|
| 1 | Inventory affected AI systems | Compliance + Tech Lead | {{}} | TODO |
| 2 | Classify risk tier | Compliance | {{}} | TODO |
| 3 | Prepare technical documentation | Tech Lead | {{}} | TODO |
| 4 | Submit to AI Office / authority if required | Compliance | {{}} | TODO |
| 5 | Update internal AI policy | Compliance | {{}} | TODO |
| 6 | Train team on compliance | PM / Eng manager | {{}} | TODO |

## Estimated Effort
{{Person-weeks, blocker, region-specific notes}}
```

---

## Template G — Competitive Scan

```markdown
# AI Competitive Scan — {{Date Range}}

## TL;DR — Big Picture Shifts
- {{Lab X did Y, which signals Z}}
- {{Lab pricing war / open-source push / agent focus}}

## Capability Matrix
| Lab | Top model | SWE-bench Pro | GPQA | HLE | Notes |
|---|---|---|---|---|---|
| OpenAI | GPT-5.5 | | | | |
| Anthropic | Claude Opus 4.7 | | | | |
| Google DeepMind | Gemini 3.1 Pro | | | | |
| xAI | Grok 4 | | | | |
| Meta | Llama X | | | | |
| Mistral | | | | | |
| DeepSeek | DeepSeek V4 Pro | | | | |
| Qwen | Qwen | | | | |

## Agent Strategy Matrix
| Lab | Coding agent | Browser/computer use | Research agent | MCP support | Pricing model |
|---|---|---|---|---|---|

## Developer Platform Matrix
| Lab | Primary API | IDE integration | CLI agent | Cloud agent | Plugins/MCP |
|---|---|---|---|---|---|

## Pricing Snapshot (per million tokens)
| Model | Input | Output | Cached | Batch | Notes |
|---|---|---|---|---|---|

## Open-source Posture
| Lab | Open-weight tier | License | Recent release | Strategy |
|---|---|---|---|---|

## Safety Posture
| Lab | Public framework | Pre-deployment AISI access | System card depth | Recent safety publication |
|---|---|---|---|---|

## Trend Synthesis
{{3-5 paragraphs interpreting the matrices: who's winning where, what's the strategic move, what gaps exist}}

## What to Watch
- {{}}
```

---

## Template H — Quick Alert (urgent breaking)

```markdown
# 🚨 AI Alert — {{Date+Time}}

**Topic**: {{}}
**Severity**: {{Critical/High}}
**Category**: {{Model release / Safety incident / Policy / Security / Strategic}}
**Affects**: {{Specific users/products/regions}}

## What happened
{{2-3 câu}}

## Why urgent
{{Deadline / exploit available / production impact / regulatory exposure}}

## Immediate action
1. {{}}
2. {{}}

## Source
- {{Primary link Tier 1}}
- {{Confirmation Tier 2/3 if available}}

## Owner
{{Role}}

## Follow-up
{{Will issue deep dive in {{N}} days / monitor for {{event}}}}
```

---

## Common Formatting Rules

- **Dates**: ISO `YYYY-MM-DD` HOẶC `DD/MM/YYYY` — chọn một, nhất quán trong brief.
- **Model name**: giữ format vendor (Claude Opus 4.7, GPT-5.5, Gemini 3.1 Pro, DeepSeek V4 Pro, Llama 4, Qwen).
- **Benchmark name**: full version (SWE-bench Verified, SWE-bench Pro, Terminal-Bench 2.0, MMLU-Pro, GPQA Diamond, Humanity's Last Exam, GDPval, GDPval-MM, AIME).
- **Pricing**: `$X/M tok` (input) / `$Y/M tok` (output). Note cached/batch if relevant.
- **Link**: full URL Markdown.
- **Citation**: với mỗi major claim, link Tier 1/2.
- **Vietnamese**: narrative tiếng Việt, technical noun tiếng Anh.
- **Tables**: dùng khi >= 3 items cùng schema.
- **Self-reported label**: bắt buộc khi benchmark từ lab's own harness.
- **Contamination caveat**: bắt buộc note khi nói SWE-bench Verified.
- **Emoji**: không dùng trong brief chính thức (trừ 🚨 alert).
