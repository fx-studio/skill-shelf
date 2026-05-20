# Command Catalog for AI Frontier Watch Skill

Catalog gộp toàn bộ commands skill nhận diện được: 10 lệnh định kỳ (mode brief) + 24 lệnh on-demand (custom). Khi user gõ `help/menu/?` → output Menu Display Format ở cuối file này.

---

## Menu Display Format (output khi user gõ `help`/`menu`/`?`)

```markdown
# AI Frontier Watch — Menu

Chào bạn. Đây là các lệnh có sẵn. Bạn có thể gõ tên lệnh ngắn (vd: `daily ai`), gõ số (vd: `1`), hoặc paste prompt chi tiết.

## 📅 A. Định kỳ — Brief lập lịch chạy đều

| # | Lệnh ngắn | Mô tả |
|---|---|---|
| 1 | `daily ai` / `brief hôm nay` | Daily Brief AI 24-48h, up to 10 items + 3 papers |
| 2 | `weekly ai` / `weekly` | Weekly Brief 7 ngày, gom theo trend |
| 3 | `agents watch` | AI Agents deep: coding agents, browser-use, MCP, autonomous |
| 4 | `paper digest` | Top papers tuần qua từ arXiv, HF Papers, conferences |
| 5 | `model release` | Model releases tuần qua từ frontier & open labs |
| 6 | `open-source ai` | Open-weight models, datasets, inference tooling |
| 7 | `safety policy` | AI safety, security, regulation, copyright |
| 8 | `infra watch` | Inference, chips, data centers, serving, scaling |
| 9 | `competitive scan` | So sánh OpenAI vs Anthropic vs Google vs Meta vs xAI vs DeepSeek vs Qwen |
| 10 | `builder action` | Trích action cho AI builder từ tin tuần này |

## 🔍 B. On-demand — Custom prompt theo nhu cầu

### Nhìn lại (Retrospective)
| # | Lệnh ngắn | Mô tả |
|---|---|---|
| 11 | `3 tháng qua` / `quarterly retro` | Tổng hợp 90 ngày qua + bài học |
| 12 | `tháng qua` / `last month` | Tổng hợp 30 ngày qua |
| 13 | `recap {{event}}` | Recap event cụ thể (NeurIPS, ICML, OpenAI DevDay, Anthropic event) |
| 14 | `model retro` | Đánh giá model team đã chọn còn phù hợp không |

### Nhìn tới (Forward-looking)
| # | Lệnh ngắn | Mô tả |
|---|---|---|
| 15 | `tháng tới` / `30 ngày tới` | Sự kiện & deadline 30 ngày tới |
| 16 | `90 ngày tới` / `quý tới` | Look-ahead quarterly |
| 17 | `chuẩn bị {{event}}` / `pre neurips` | Pre-event prep |
| 18 | `năm tới` / `yearly forecast` | Forecast 12 tháng cho leadership |

### Stack-aware (cần input team)
| # | Lệnh ngắn | Mô tả |
|---|---|---|
| 19 | `stack check` / `health check` | Audit AI stack hiện tại |
| 20 | `model migration {{from}} to {{to}}` | Lập migration plan model |
| 21 | `dependency scan` / `CVE check` | Scan vuln SDK AI đang dùng |

### Decision support
| # | Lệnh ngắn | Mô tả |
|---|---|---|
| 22 | `model selection` | Chọn model cho use case cụ thể |
| 23 | `frontier vs open-weight` | So sánh closed vs open frontier |
| 24 | `cost analysis` / `LLM cost` | Phân tích cost cho scale cụ thể |
| 25 | `on-prem vs API` | Self-host vs API decision |
| 26 | `build vs buy` | Build agent in-house vs platform |

### Communication helpers
| # | Lệnh ngắn | Mô tả |
|---|---|---|
| 27 | `standup` | Tóm tắt cho team standup, 3-5 bullets |
| 28 | `PM summary` | Tóm tắt non-technical cho PM |
| 29 | `leadership brief` | Brief 200 từ cho CTO/founder/investor |
| 30 | `onboarding` | Context cho hire mới (AI engineer / PM) |

### Deep-dive
| # | Lệnh ngắn | Mô tả |
|---|---|---|
| 31 | `deep dive {{topic}}` | Deep dive 1 chủ đề (MCP, agent memory, RAG arch...) |
| 32 | `model review {{name}}` | Review 1 model cụ thể |
| 33 | `benchmark deep-dive {{name}}` | Phân tích 1 benchmark |
| 34 | `compliance {{region}}` | EU AI Act / US executive order / Korea / China / Vietnam compliance |

## 🎨 C. Output formatting

| Lệnh | Mô tả |
|---|---|
| `infographic this` | Render brief vừa rồi thành HTML infographic (skill tự design theme) |
| `infographic this editorial` | Như trên, theme Editorial (serif, magazine-style) |
| `infographic this terminal` | Theme Terminal (monospace, dark, tech) |
| `infographic this sober` | Theme Sober (typographic, restrained, like Anthropic blog) |

## 💡 Tips

- Hỏi câu cụ thể bất kỳ → tôi trả lời ad-hoc kèm link Tier 1.
- Combine được: `stack check + model migration` → tôi chạy tuần tự.
- Sau khi nhận output, gõ `deep dive item N` hoặc `expand action cho researcher` để zoom in.
- Sau brief markdown, gõ `infographic this` để có version HTML cho Slack/LinkedIn.

Bạn muốn chạy lệnh nào?
```

---

## A. Định kỳ — Brief modes (10 commands)

### A1. Daily Brief

**Trigger**: `daily ai`, `brief hôm nay`, `daily brief`, `1`

**Prompt template**:
```
Chạy AI Frontier Daily Brief cho hôm nay theo giờ Việt Nam. Tìm tin trong 24-48h qua về AI, LLM, AI Agents, model releases, research papers, open-source AI, safety/security, regulation, developer tooling, infrastructure và enterprise adoption. Ưu tiên nguồn chính chủ (Tier 1), research source (arXiv, HF Papers), và journalism uy tín. Trả về up to 10 items quan trọng, 3 papers đáng đọc, signals to watch và recommended actions. Trả lời tiếng Việt.
```

Template output: A (Daily Brief) trong `output-templates.md`.

### A2. Weekly Brief

**Trigger**: `weekly ai`, `weekly`, `2`

**Prompt template**:
```
Chạy AI Frontier Weekly Brief cho 7 ngày gần nhất. Đừng chỉ liệt kê tin; gom thành các xu hướng lớn. Bao quát frontier model release, AI Agents, research papers, open-source AI, benchmarks, infra/tooling, safety, policy và business signals. Với mỗi xu hướng, nêu evidence, impact, confidence và what to monitor next. Bao gồm action items consolidated cuối brief.
```

Template: B (Weekly Brief).

### A3. AI Agents Watch

**Trigger**: `agents watch`, `3`

**Prompt template**:
```
Tổng hợp diễn biến mới nhất về AI Agents trong 7-14 ngày qua. Tập trung vào coding agents (Claude Code, Codex CLI, Cursor, Devin, Augment, Aider, OpenCode), browser/computer-use agents, research agents (Perplexity Deep Research, OpenAI Deep Research), autonomous agents (Manus), multi-agent frameworks (LangGraph, CrewAI, AutoGen), MCP/A2A protocols, agent memory, agent evaluation (SWE-bench Verified/Pro, Terminal-Bench 2.0, GDPval). Note benchmark version rõ ràng (Verified vs Pro). Chỉ dùng nguồn Tier 1-2. Kết thúc bằng recommended actions cho AI builder/product team.
```

### A4. Research Paper Digest

**Trigger**: `paper digest`, `papers tuần này`, `4`

**Prompt template**:
```
Tổng hợp research papers đáng chú ý nhất trong 7 ngày qua về LLM, AI Agents, reasoning, multimodal, RAG, inference optimization, evaluation, AI safety. Với mỗi paper, nêu problem, core method, key result + benchmark, code availability, limitation, và vì sao đáng đọc. Phân nhóm theo theme nếu có ≥3 papers cùng theme.
```

Template: E (Paper Digest).

### A5. Model Release Watch

**Trigger**: `model release`, `new models`, `5`

**Prompt template**:
```
Tìm các model release mới nhất từ OpenAI, Anthropic, Google DeepMind, xAI, Meta, Mistral, Cohere, DeepSeek, Qwen, Moonshot, Zhipu, Microsoft, NVIDIA. Với mỗi model, kiểm tra:
- Nguồn chính chủ + model card / system card
- Capability mới
- Benchmark verified (cross-reference Artificial Analysis + LMArena nếu có)
- Pricing tier (input/output/cached/batch)
- API endpoints + region availability
- Open-weight status + license
- Safety evaluation + pre-deployment AISI access
- Tác động với developer/product team

Label rõ self-reported vs verified benchmark. Note contamination caveat khi nói SWE-bench Verified.
```

Template: D (Model Release Report).

### A6. Open-source AI Watch

**Trigger**: `open-source ai`, `open source`, `6`

**Prompt template**:
```
Tổng hợp cập nhật đáng chú ý về open-source AI trong 7 ngày gần nhất:
- Open-weight model release (Llama, Mistral, Qwen, DeepSeek, Gemma, Phi, etc.)
- Dataset release
- Fine-tuning recipe / cookbook
- Inference optimization
- Inference engines (vLLM, SGLang, TensorRT-LLM, llama.cpp, MLX, ExecuTorch, Ollama)
- Quantization technique (GGUF, AWQ, GPTQ, FP4)
- Open evaluation framework

Ưu tiên nguồn Hugging Face Blog, lab GitHub, papers. Note license và intended use.
```

### A7. Safety / Policy Watch

**Trigger**: `safety policy`, `safety`, `policy watch`, `7`

**Prompt template**:
```
Tổng hợp diễn biến quan trọng về AI safety, LLM security, prompt injection, jailbreak, agent security, alignment research, model safety report, AI regulation, EU AI Act (đặc biệt Aug 2, 2026 enforcement), US/UK AISI evaluations, copyright lawsuit, governance. Ưu tiên nguồn regulator (EU AI Office, NIST, AISI), official lab safety posts (Anthropic RSP, OpenAI Preparedness, Google Frontier Safety), METR, Apollo Research, OWASP LLM, Stanford HAI, Frontier Model Forum.

Với policy: nêu effective date, region, AI system type affected, required action, penalty range.
```

Template: F (Policy & Compliance Alert).

### A8. Infrastructure Watch

**Trigger**: `infra watch`, `8`

**Prompt template**:
```
Tổng hợp cập nhật AI infrastructure trong 7-14 ngày:
- Chips: NVIDIA Blackwell GB200/GB300, AMD MI300/MI400, Groq LPU, Cerebras wafer-scale, TPU v6, Tenstorrent, Etched
- Cloud AI capacity: AWS, GCP, Azure, Oracle, CoreWeave, Lambda Labs
- Data center buildout, energy/cooling
- Model serving platforms: Together, Fireworks, Replicate, Modal, RunPod, OpenRouter
- Inference pricing trends (frontier API + open-weight serving)
- Inference techniques: prompt caching, speculative decoding, batching, KV cache

Highlight pricing change và capacity bottleneck.
```

### A9. Competitive Scan

**Trigger**: `competitive scan`, `compare labs`, `9`

**Prompt template**:
```
So sánh các diễn biến mới nhất giữa OpenAI, Anthropic, Google DeepMind, xAI, Meta, Mistral, DeepSeek, Qwen, Cohere trong tuần qua. Tạo matrix:
- Capability (top model + benchmark)
- Agent strategy
- Developer platform
- API pricing
- Open-source posture
- Safety posture
- Enterprise adoption signals

Cuối brief: 3-5 paragraphs interpretation về ai đang dẫn ở đâu, strategic moves đáng chú ý, và gaps.
```

Template: G (Competitive Scan).

### A10. Builder Action Brief

**Trigger**: `builder action`, `10`

**Prompt template**:
```
Từ các tin AI mới nhất trong tuần, hãy trích ra những điều một AI builder/product team nên làm ngay:
- Model/API cần thử
- Paper cần đọc + ưu tiên
- Framework / SDK cần evaluate
- Risk cần kiểm tra (security, compliance, cost)
- Regulation cần lưu ý + deadline
- Cơ hội sản phẩm mới
- Pricing change cần re-project

Output: bảng action với role chịu trách nhiệm, effort estimate, deadline.
```

---

## B. On-demand — Custom prompts (24 commands)

### B11. Quarterly Retrospective

**Trigger**: `3 tháng qua`, `quarterly retro`, `quý vừa rồi`, `Q1 retro`, `Q2 retro`, `last quarter`, `11`

**Prompt**:
```
Tổng hợp tất cả sự kiện AI quan trọng trong 90 ngày qua. Gom theo nhóm (Frontier models / Agents / Research / Open-source / Infra / Safety / Policy / Business). Với mỗi sự kiện: ngày, source Tier 1, summary 2 câu, impact đã/đang tác động. Cuối brief:
- Top 5 sự kiện quan trọng nhất quý
- Capability ceiling shift (Intelligence Index from X to Y)
- Pricing trend (avg input/output $/M tokens)
- Deadline đã pass — team đã / chưa kịp respond?
- Deadline còn lại trong tháng tới
- Bài học rút ra cho quý sau
```

### B12. Last Month Retro

**Trigger**: `tháng qua`, `monthly retro`, `30 ngày qua`, `last month`, `12`

**Prompt**:
```
Tổng hợp sự kiện AI trong 30 ngày qua. Tách thành:
- Major model releases (full benchmark + pricing)
- Major agent platform updates
- Top papers (top 10)
- Policy updates đã effective
- Security advisories / jailbreaks reported
- Business news strategic (M&A, partnership, funding >$100M)
- Open-source highlights

Cuối brief: 3 điều team đã/nên đã action, 3 điều cần catch up nếu chưa.
```

### B13. Event Recap

**Trigger**: `recap {event}`, `tổng kết {event}`, `sau {event}`, `13`

**Prompt**:
```
Recap toàn diện sự kiện {{EVENT_NAME, ví dụ "OpenAI DevDay 2026", "Anthropic event 2026", "Google I/O AI track", "NeurIPS 2025", "ICML 2025", "ICLR 2026"}}. Bao gồm:
- Headline announcement (top 5)
- New model / framework / API
- Pricing changes
- Benchmark / evaluation updates
- Strategic positioning vs competitors
- Top sessions / papers worth reviewing
- Team adoption plan: must-do / should-evaluate / watch
- Open questions cần follow up
```

### B14. Model Retro

**Trigger**: `model retro`, `đánh giá model`, `model còn phù hợp`, `14`

**Prompt**:
```
Đánh giá lại model team đã chọn ({{MODEL_NAME}}) có còn phù hợp không trong 90 ngày qua:
- Capability changes (model updates, new versions, deprecation)
- Pricing changes (input/output/cache)
- Competitive context (alternative đã ra mắt từ lúc chọn)
- Issues team gặp (rate limit, hallucination, refusal pattern, latency)
- Better fit available now?
- Migration cost estimate nếu muốn đổi

Output: Stay / Re-evaluate / Migrate. Kèm reasoning + condition để re-evaluate.
```

### B15. Next 30 Days

**Trigger**: `tháng tới`, `30 ngày tới`, `sắp tới`, `upcoming`, `15`

**Prompt**:
```
Liệt kê sự kiện và deadline AI trong 30 ngày tới. Bao gồm:
- EU AI Act / regulation effective dates
- Major lab events đã announce (DevDay, Anthropic event, conference keynote)
- Conferences (NeurIPS, ICML, ICLR, ACL, EMNLP, CVPR, COLM nếu trong khung)
- Expected model releases dựa trên past cadence
- API deprecation dates
- AI Safety Institute pre-deployment access milestones
- US/EU regulatory consultations closing

Sắp xếp theo ngày tăng dần. Highlight cái nào team chưa action.
```

### B16. Next 90 Days

**Trigger**: `90 ngày tới`, `quý tới`, `next quarter`, `16`

**Prompt**:
```
Look-ahead 90 ngày cho team AI. Bao gồm:
- EU AI Act phase rollout (chú ý Aug 2, 2026 nếu trong khung)
- Conference dates + topics expected
- Earnings season (NVIDIA, Microsoft, Google, Meta, OpenAI nếu IPO)
- Lab event windows
- Expected major releases dựa trên cadence
- Regulation effective dates
- Beta cycle milestones (model preview to GA)

Output: calendar grid theo tuần. Highlight tuần có ≥2 sự kiện.
```

### B17. Pre-event Prep

**Trigger**: `chuẩn bị {event}`, `pre {event}`, `trước {event}`, `17`

**Prompt**:
```
Tuần trước sự kiện {{EVENT}}:
- Rumor và speculation (Reuters, FT, Bloomberg, The Information) — label rõ
- Expected announcements team nên chuẩn bị mental model
- What we should prepare: doc review, beta enrollment, schedule team viewing
- Watch list: paper / session / model nào ưu tiên nếu release sớm
- Compliance prep nếu là regulatory deadline
```

### B18. Year Forecast

**Trigger**: `năm tới`, `forecast năm`, `12 tháng tới`, `yearly forecast`, `18`

**Prompt**:
```
Forecast 12 tháng tới cho team AI. Bao gồm:
- Frontier capability ceiling expected (Intelligence Index projection)
- Pricing trajectory ($/M tokens trend)
- Agent capability frontier (SWE-bench Pro / Terminal-Bench projection)
- Open-source vs closed gap forecast
- EU AI Act phase tiếp theo (Aug 2, 2027 deadline)
- US AISI / UK AISI expanded scope expected
- Regulation timeline: Korea, Japan, China, India, US states
- Chip availability (NVIDIA Blackwell ramp, AMD MI400, custom silicon)
- Skill gap risk for team

Tone strategic, không quá technical.
```

### B19. Stack Health Check

**Trigger**: `stack check`, `audit stack`, `health check`, `kiểm tra stack`, `19`

**Prompt**:
```
Đánh giá AI stack hiện tại của team (user cần cung cấp hoặc đã save):
- Primary LLM, Fallback LLM, Embedding model, Vector DB, Agent framework, Orchestration, Eval framework, Observability, Deployment region

Với mỗi item, search verify:
- Còn được lab/vendor support
- Có version mới / better alternative
- Có security advisory
- Pricing change từ lúc chọn
- Có conflict với compliance

Output: bảng "Item | Current | Latest/Alternative | Risk | Recommended action | Deadline".
```

### B20. Model Migration Plan

**Trigger**: `model migration`, `migration plan model`, `migrate from to`, `chuyển model`, `20`

**Prompt**:
```
Lập migration plan chi tiết từ {{FROM_MODEL}} sang {{TO_MODEL}}.

Phase 0 — Eval (W1-W2): paired evaluation production task subset
Phase 1 — Spike (W3): refactor prompt, integration smoke test
Phase 2 — Phased rollout (W4-Wn): 1% → 10% → 50% → 100%
Phase 3 — Cleanup: remove old SDK, update docs

Mỗi phase có: deadline, owner role, deliverable, risk, exit criteria, rollback trigger.
```

### B21. Dependency Scan

**Trigger**: `dependency scan`, `CVE check`, `security scan`, `21`

**Prompt**:
```
Scan dependency AI stack:
- LLM client SDKs (openai, anthropic, google-genai, transformers)
- Agent frameworks (langchain, llamaindex, crewai, autogen, langgraph)
- Vector DB clients (pinecone, weaviate, qdrant, chromadb, pgvector)
- Inference engines (vllm, sglang, llama.cpp)
- Eval tools

Check NVD, GitHub Security Advisory, Snyk DB. Output: bảng CVE ID | Severity (CVSS) | Affected versions | Fixed version | Action.
```

### B22. Model Selection

**Trigger**: `model selection`, `chọn model`, `which model`, `22`

**Prompt**:
```
Chọn model cho use case {{USE_CASE}}.

Phân tích: required capability, latency, cost budget, privacy, region, compliance.

Bảng option: Model | Lab | Capability fit | Cost/req | Latency | Privacy | Compliance | Overall

Recommended primary + fallback. Test plan để verify trên production subset.
```

### B23. Frontier vs Open-weight

**Trigger**: `frontier vs open-weight`, `closed vs open`, `OpenAI vs Llama`, `23`

**Prompt**:
```
So sánh frontier closed (OpenAI, Anthropic, Google) vs open-weight (DeepSeek V4, Llama 4, Qwen, Mistral Large) cho use case {{USE_CASE}}:

Bảng dimensions: Top-tier capability / Cost at scale / Latency / Privacy / Customization / Compliance / Vendor lock-in / Time to production / Operational complexity

3 scenarios where each option wins. Recommendation cho team với assumption.
```

### B24. Cost Analysis

**Trigger**: `cost analysis`, `LLM cost`, `tính cost`, `24`

**Prompt**:
```
Phân tích cost cho use case {{USE_CASE}} ở scale {{X req/day, Y avg input, Z avg output}}:

Options: OpenAI GPT-5.5/mini, Anthropic Opus 4.7/Sonnet 4.6/Haiku 4.5, Google Gemini 3.1 Pro/Flash, xAI Grok 4, DeepSeek V4, Self-host Llama 4 / Qwen.

Include: Batch API discount, Prompt caching, Reserved capacity, Self-host TCO (GPU + ops).

Recommendation theo priority: cost-first / quality-first / balanced.
```

### B25. On-prem vs API

**Trigger**: `on-prem vs API`, `self-host vs API`, `tự host hay API`, `25`

**Prompt**:
```
Quyết định self-host open-weight vs gọi API frontier cho use case {{USE_CASE}}:
- Volume threshold (break-even)
- Privacy / data residency
- Latency requirement
- Quality requirement
- Customization (fine-tune)
- Team capability
- TCO 12 tháng

Bảng comparison + recommendation. Note risk mỗi option.
```

### B26. Build vs Buy

**Trigger**: `build vs buy`, `build agent in-house`, `platform vs build`, `26`

**Prompt**:
```
Quyết định build agent in-house vs platform ({{PLATFORM}}):

Bảng comparison: Time to MVP / Customization / Cost (12 months) / Maintenance / Vendor lock-in / Compliance control / Integration / Risk if platform pivot

Recommendation kèm assumption về team size, timeline, strategic priority.
```

### B27. Standup Format

**Trigger**: `standup`, `cho standup`, `slack format`, `27`

**Prompt**:
```
Tóm tắt cho team standup sáng mai:
- 3-5 bullets ngắn về AI tin tức 24h qua
- Ưu tiên item ảnh hưởng project hiện tại
- Mỗi bullet < 25 từ
- Có emoji 1 cái ở đầu (🧠 Model, 🤖 Agent, 📄 Paper, 🔓 Open-source, ⚠️ Policy, 🔒 Security, 💰 Pricing, ⚙️ Infra)
- Cuối có link
```

### B28. PM Summary

**Trigger**: `PM summary`, `tóm tắt cho PM`, `non-technical summary`, `28`

**Prompt**:
```
Tóm tắt brief AI tuần qua cho PM không technical:
- Không jargon (không "MoE", "RAG", "MCP")
- Focus business impact: roadmap impact / user-facing change / compliance risk / revenue/cost impact
- Không hơn 300 từ
- Cuối: "Questions for engineering team" — 2-3 câu PM nên hỏi 1-1 với Tech Lead
```

### B29. Leadership Brief

**Trigger**: `leadership brief`, `cho CTO`, `executive brief`, `founder brief`, `29`

**Prompt**:
```
Brief AI tuần qua cho engineering leadership / CTO / Founder / Investor:
- 1 paragraph TL;DR strategic
- 3 bullets: biggest risk, biggest opportunity, biggest unknown
- Numbers: deadline gần nhất, cost impact, competitive shift
- Resource ask
- Decisions needed: 1-3 quyết định cần leadership input

Không hơn 200 từ. Memo format.
```

### B30. Onboarding Context

**Trigger**: `onboarding`, `new hire`, `cho member mới`, `intro ai`, `30`

**Prompt**:
```
Context onboarding cho member mới team AI:
- State of AI 2025-2026 (1 paragraph)
- Frontier landscape: top 5 labs + flagship
- Agent landscape: top platforms + MCP
- Open-source frontier
- Critical regulation
- 5 key resources Tier 1
- 3 podcast/YouTube/newsletter
- Glossary thuật ngữ
```

### B31. Deep Dive

**Trigger**: `deep dive {topic}`, `phân tích sâu`, `31`

**Prompt**:
```
Deep dive về topic {{TOPIC}}:
- Bottom line (1 paragraph)
- Background + state of art
- Timeline of key papers/releases
- Primary sources
- Technical details
- Production patterns emerging
- Open problems
- Recommended action for team
```

Template: C (Deep Dive).

### B32. Model Review

**Trigger**: `model review {name}`, `review {model}`, `đánh giá {model}`, `32`

**Prompt**:
```
Review chi tiết model {{MODEL_NAME}}:
- Full Model Release Report (template D)
- Sau 30+ ngày từ launch: real-world feedback (Reddit, HN, GitHub issues)
- Issues reported (hallucination, refusal, latency)
- Cost-effectiveness verdict
- Recommended use case + avoid case
- Migration cost từ previous version
```

### B33. Benchmark Deep Dive

**Trigger**: `benchmark deep-dive {name}`, `phân tích benchmark`, `33`

**Prompt**:
```
Phân tích benchmark {{BENCHMARK_NAME}}:
- What it measures (tasks, scoring methodology)
- Who created + when
- Top performers + scores (current leaderboard)
- Methodology critiques / contamination concerns
- Compare benchmark sibling (SWE-Verified vs Pro)
- Relevance cho real-world use case
- Recommended use khi evaluate model
```

### B34. Region Compliance

**Trigger**: `compliance {region}`, `EU AI Act compliance`, `US AI executive order`, `34`

**Prompt**:
```
Focus compliance cho region {{REGION}}:
- Active regulation hiện tại
- Effective dates of upcoming rules
- AI system types affected
- Required action cho provider vs deployer
- Penalty range
- Code of Practice / guideline available
- Source: regulator primary + reputable analysis
```

---

## Recognition Priority Rules

Khi user gõ ngắn, skill match theo thứ tự:

1. **Exact match** từ table A (số 1-10) hoặc B (số 11-34) → execute trực tiếp
2. **Partial match** từ trigger keywords → execute trực tiếp
3. **Multiple match** → hỏi 1 câu ngắn confirm (chỉ 1 câu, không nhiều)
4. **No match** → treat như ad-hoc question (G1 trong file 07 gốc): trả lời 3-7 câu kèm link Tier 1

**Không bao giờ hỏi nhiều câu clarify cùng lúc.** Nếu user gõ "tháng tới", hiểu là B15.

---

## C. Output formatting commands

### C1. Infographic — Auto theme

**Trigger**: `infographic this`, `infographic version`, `render dưới dạng html`, `tạo html đẹp`, `version để share`, `share-ready`

→ Đọc `infographic-design.md`, mode A (Creative — skill tự design theme dựa trên content).

### C2. Infographic — Pinned theme

**Trigger**:
- `infographic this editorial` / `editorial style`
- `infographic this terminal` / `terminal style`
- `infographic this sober` / `sober style`

→ Đọc `infographic-design.md`, mode B (Theme mode — áp dụng đúng theme từ `assets/`).
