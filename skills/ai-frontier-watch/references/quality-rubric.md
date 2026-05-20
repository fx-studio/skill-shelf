# Quality Rubric for AI Frontier Watch Agent

## A. Source Reliability

- **5** — Primary: Lab official post, model card, system card, paper, regulator filing (EU AI Office, NIST, AISI), SEC filing.
- **4** — Tier 2: Conference video, reputable engineer/researcher blog (Simon Willison, Jay Alammar, Lilian Weng, Sebastian Raschka), top-tier journalism with multiple named sources (Reuters, FT, Bloomberg).
- **3** — Established community blog with evidence, reputable tech press reporting on primary source.
- **2** — Single secondary, paywall content without verification, tutorial site.
- **1** — Rumor, social-only, unattributed, AI-generated SEO.

---

## B. Novelty

- **5** — New frontier-scale model with SOTA on major benchmark, new architecture paradigm, major safety/policy event.
- **4** — New strategically meaningful: new agent capability, new framework version, new evaluation methodology.
- **3** — Useful incremental: minor version bump with notable feature, new technique with demonstrated improvement.
- **2** — Re-statement of known info, marginal update.
- **1** — Recycled story, rumor repeated.

---

## C. Impact (for AI builder/team)

- **5** — Changes product strategy, model selection, cost structure significantly, or creates regulatory exposure.
  - Example: EU AI Act enforcement starting Aug 2, 2026 for GPAI
  - Example: New model 10x cheaper at same quality
  - Example: Critical jailbreak affecting all major frontier models
- **4** — Affects roadmap, architecture decision, hiring decision, quarterly planning.
  - Example: New SOTA agent on SWE-bench Pro that changes coding workflow
  - Example: Open-weight model reaching frontier capability
- **3** — Worth evaluating for next quarter.
  - Example: New RAG technique with 5-10% improvement
  - Example: New IDE integration
- **2** — Nice-to-know for specific role.
- **1** — Background noise.

---

## D. Actionability

- **5** — Action required by specific date < 60 days.
  - Example: "EU AI Act high-risk obligations enforce Aug 2, 2026"
  - Example: "API model deprecated in 30 days"
  - Example: "Critical CVE in production agent framework"
- **4** — Evaluate within current/next sprint.
- **3** — Monitor next release.
- **2** — Bookmark for later.
- **1** — No action.

---

## E. Confidence

- **5** — Confirmed by primary source + supporting evidence (paper + code, model card + system card, regulator official + Code of Practice).
- **4** — Confirmed primary source, partial docs (announced but pricing/availability not full).
- **3** — Credible but incomplete (rumor with multiple named sources).
- **2** — Conflicting / weak.
- **1** — Unconfirmed leak / single anonymous source.

---

## Priority Mapping

### Critical
At least one of:
- Impact = 5 AND Confidence ≥ 4
- Hard deadline < 60 days (especially EU AI Act enforcement)
- Critical security vulnerability with production exploit
- Major lab safety incident requiring immediate response
- Frontier model release that changes top-3 ranking

### High
- Impact ≥ 4 AND Confidence ≥ 4
- Major framework / agent platform release worth testing in current sprint
- Deadline 60-180 days
- New benchmark contamination report affecting model selection

### Medium
- Impact ≥ 3 AND Confidence ≥ 3
- Worth tracking this quarter
- Foundation for strategic decision

### Low
- Context only
- Background reading

---

## AI-Specific Bonus Modifiers

- **+1 priority**: Item affects EU AI Act compliance (Aug 2, 2026 is approaching)
- **+1 priority**: Item changes API pricing structure significantly
- **+1 priority**: Item is security/jailbreak with proof-of-concept
- **+1 priority**: Item is safety incident from frontier lab (RSP / Preparedness trigger)
- **−1 priority**: Item is research-only without practical applicability
- **−1 priority**: Item is region-limited and team doesn't deploy there

---

## Benchmark Reporting Sub-Rubric

When reporting any benchmark number, MUST include:

### Source of benchmark
- **5**: Independent verification (Artificial Analysis, LMArena, METR, public leaderboard)
- **3**: Lab's official report with reproducible setup
- **1**: Self-reported with custom harness (label clearly)

### Version specificity
**MANDATORY**: Always specify benchmark version:
- ❌ "SWE-bench 80%"
- ✅ "SWE-bench Verified 80.9% (self-reported, OpenAI harness)"
- ✅ "SWE-bench Pro 64.3% (Anthropic-reported, January 2026)"

### Contamination warning
**MANDATORY** when citing SWE-bench Verified (post Feb 23, 2026 OpenAI Frontier Evals warning):
- Always note: "OpenAI Frontier Evals team stopped reporting SWE-bench Verified in Feb 2026 due to contamination concerns"
- Cross-reference Terminal-Bench, GDPval, or real-world repos when available

---

## Model Release Reporting Sub-Rubric

For each model release, capture:

### Capability claims
- Top 3 benchmarks with score + source
- Cross-reference: lab self-reported vs Artificial Analysis vs LMArena
- Note discrepancies > 5 percentage points

### Pricing accuracy
- Verify on official API pricing page
- Include: input, output, cached input, batch
- Note tier (e.g., context length tier)

### Availability scope
- Regions launched
- Open-weight: license + commercial use rights
- API: rate limits at launch

### Safety report
- Lab's own safety eval summary
- Pre-deployment AISI access (US AISI / UK AISI)
- Notable refusal/safety category

### Competitive positioning
- vs same-tier from competitor (Claude Opus 4.7 vs GPT-5.5 vs Gemini 3.1 Pro)
- vs open-weight equivalent

---

## Paper Reporting Sub-Rubric

For each paper, capture:

### Reproducibility
- **High**: Code released + dataset released + clear instructions
- **Medium**: Code released, dataset reference
- **Low**: No code, only claims

### Author affiliation
- **High signal**: Major lab researchers (Anthropic, OpenAI, DeepMind, FAIR, MSR)
- **Medium**: Top university lab (Stanford CRFM, MIT CSAIL, Berkeley BAIR, CMU)
- **Note**: First-time authors, single-author papers warrant more scrutiny

### Status
- Preprint (arXiv only)
- Submitted to {{venue}}
- Accepted at {{venue}}
- Workshop paper (lower bar)
- Industry technical report (rigor varies)

### Self-reported vs verified
- Lab paper with internal benchmark: self-reported
- Reproduction by 3rd party: verified
- Benchmark official with submitted results: verified

---

## Final Brief Quality Checklist

### Source quality
- [ ] ≥ 70% major claims have Tier 1-2 link
- [ ] Rumor / leak labeled explicitly
- [ ] Self-reported benchmark labeled
- [ ] SWE-bench Verified contamination caveat included

### Accuracy
- [ ] Model name exact (Claude Opus 4.7, not "Claude 4")
- [ ] Benchmark version specific (Verified vs Pro vs Multimodal)
- [ ] Date format consistent in brief
- [ ] Pricing has source link
- [ ] EU AI Act dates correct (Aug 2 milestones)

### Actionability
- [ ] Each item has Recommended action
- [ ] Action has role owner (not generic "team")
- [ ] Action has deadline when applicable
- [ ] Items with deadline < 60 days are Critical/High

### Completeness
- [ ] Executive summary is actionable, not summary-of-summary
- [ ] Action items consolidated
- [ ] What to Watch Next

### Format
- [ ] Vietnamese narrative
- [ ] English for proper nouns
- [ ] Consistent date format
- [ ] Markdown links
- [ ] Tables when ≥ 3 items same schema

### Anti-pattern check
- [ ] No padding to hit item count
- [ ] No decorative emoji
- [ ] No hype language ("revolutionary", "game-changer", "cách mạng")
- [ ] No "best" claims without comparative evidence
- [ ] No recommendation without risk note

---

## Self-Check Questions

After writing, ask:

1. Builder reading this knows what model to test this sprint?
2. Researcher knows what paper to read tonight?
3. PM knows what compliance deadline is approaching?
4. Founder knows competitive landscape change?
5. Infra eng knows pricing/cost change to model?
6. Compliance knows EU AI Act exposure?
7. Tech Lead knows architecture decisions to revisit?
8. Is there a repo/SDK team should monitor?

If brief doesn't answer ≥ 5/8 for actual user's team, rewrite.

---

## Quality Anti-Patterns

### Generic AI news pattern (BAD)
> "OpenAI released GPT-5.5 with new reasoning capabilities..."

### Specific actionable pattern (GOOD)
> "GPT-5.5 released Apr 23, 2026 (OpenAI news + system card). Benchmarks: 60.24 Artificial Analysis Intelligence Index xhigh (self-reported, third-party verified by Artificial Analysis), 84.9% GDPval-MM (verified). Pricing: $2.25/M input, $11/M output (matches Claude Opus 4.7). For our team using GPT-4o-mini for summarization at 100k req/day: GPT-5.5 nano tier may offer better quality at similar cost — but no nano variant announced yet. Action: ML eng spike 2-day eval on production task subset before considering migration. Owner: ML Tech Lead. Deadline: end of sprint."

### Hype pattern (BAD)
> "Cách mạng AI agents với MCP — game changer!"

### Sober analysis pattern (GOOD)
> "MCP (Model Context Protocol, Anthropic) đã có hơn 500 servers community-built tính đến tháng 5/2026, được Claude Code, Cursor, Windsurf, và OpenAI Codex CLI adopt. Production patterns đang ổn định: hierarchical config scope (managed/user/project/local). Risk: prompt injection qua tool result vẫn là open problem (OWASP LLM Top 10 #1 2026 edition). Use case team có thể thử: kết nối GitHub + Linear + Sentry vào coding agent để tạo loop issue→PR. Caveat: enterprise governance cho MCP server permissions còn ad-hoc. Action: Builder evaluate trên 1 nội bộ workflow Q3; Compliance review MCP server inventory trước khi production."
