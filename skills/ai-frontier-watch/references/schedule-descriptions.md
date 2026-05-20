# Schedule Descriptions for AI Frontier Watch Agent

Bộ lịch chạy theo giờ Việt Nam (ICT, UTC+7). Lưu ý timezone: phần lớn AI labs ở US (PT/ET), event/release thường rơi 09:00-17:00 PT = 23:00-07:00 ICT ngày hôm sau. Daily Brief chạy 08:30 ICT để bắt được tin "đêm qua".

---

## 1. Daily AI Brief

### Mô tả
Chạy mỗi ngày làm việc (Mon-Fri) lúc **08:30 ICT**. Tổng hợp tin AI 24-48h qua. Phù hợp đọc 10 phút trước standup sáng.

### Task prompt
```
Mỗi ngày làm việc (Thứ Hai đến Thứ Sáu) lúc 08:30 giờ Việt Nam, chạy AI Frontier Daily Brief.

Phạm vi:
- Frontier model releases (OpenAI, Anthropic, Google DeepMind, xAI, Meta, Mistral, DeepSeek, Qwen, Cohere)
- AI Agents (coding, browser-use, computer-use, research, autonomous)
- Research papers (arXiv, HF Papers)
- Open-source AI (open-weight, datasets, inference tools)
- Benchmarks & evaluations
- AI safety, security, alignment
- Policy & regulation (especially EU AI Act timeline)
- Infrastructure (chips, serving, capacity, pricing)
- Business & strategic signals
- Developer tooling

Window: 24-48h.
Up to 10 items + 3 papers (nhưng "up to" — không ép).
Bắt buộc có:
- Executive summary (TL;DR) 3-5 bullets
- Critical & High items với deadline rõ ràng
- Action items table (Action | Who | Deadline | Priority)
- What to watch next

Note self-reported vs verified benchmark. Note contamination caveat khi nói SWE-bench Verified.

Nếu ngày low-news, viết brief ngắn nói rõ thay vì nhồi item kém chất lượng.

Trả lời tiếng Việt, giữ tiếng Anh cho proper noun (model name, benchmark, framework).
```

### RRULE concept
```
FREQ=WEEKLY;BYDAY=MO,TU,WE,TH,FR;BYHOUR=8;BYMINUTE=30;BYSECOND=0
TIMEZONE=Asia/Ho_Chi_Minh
```

---

## 2. Weekly AI Brief

### Mô tả
Chạy mỗi **Thứ Sáu lúc 17:00 ICT**. Trend-focused, action consolidated. Dành cho Tech Lead / Founder / EM review cuối tuần.

### Task prompt
```
Mỗi Thứ Sáu lúc 17:00 giờ Việt Nam, chạy AI Frontier Weekly Brief cho 7 ngày qua.

Cách viết:
- Gom theo trend, không list đơn lẻ
- Mỗi trend: evidence, why it matters, confidence, affected roles, watch next
- Có bảng major releases (Frontier models, Agent platforms, Open-source)
- Top 5-7 papers tuần với full schema
- Benchmark updates / contamination notes
- Pipeline policy & compliance với deadline gần nhất
- Competitive landscape snapshot matrix
- Bảng action items consolidated
- What to watch next week

Trả lời tiếng Việt.
```

### RRULE concept
```
FREQ=WEEKLY;BYDAY=FR;BYHOUR=17;BYMINUTE=0;BYSECOND=0
TIMEZONE=Asia/Ho_Chi_Minh
```

---

## 3. AI Agents Watch

### Mô tả
Chạy mỗi **Thứ Tư lúc 17:00 ICT**. Track AI agent-specific developments — area phát triển nhanh nhất 2025-2026.

### Task prompt
```
Mỗi Thứ Tư lúc 17:00 giờ Việt Nam, chạy AI Agents Watch cho 7-14 ngày qua.

Phạm vi:
- Coding agents: Claude Code, Codex CLI, Codex Cloud, Cursor Composer, Devin, Augment, Aider, OpenCode, Cline, Roo Code, GitHub Copilot agent mode, Replit Agent
- Browser/computer-use: Anthropic Computer Use, OpenAI Operator, Browser Use
- Research agents: Perplexity Deep Research, OpenAI Deep Research, Gemini Deep Research
- Autonomous agents: Manus, OpenHands, AutoGPT successors
- Multi-agent frameworks: LangGraph, CrewAI, AutoGen, MetaGPT, Mastra
- Agent protocols: MCP, A2A, ACP
- Agent memory architectures
- Agent evaluation: SWE-bench Verified/Pro, Terminal-Bench 2.0, GDPval, Humanity's Last Exam

Note benchmark version rõ ràng. Note contamination warnings.

Recommended actions cho AI builder/product team cuối brief.

Trả lời tiếng Việt.
```

### RRULE concept
```
FREQ=WEEKLY;BYDAY=WE;BYHOUR=17;BYMINUTE=0;BYSECOND=0
TIMEZONE=Asia/Ho_Chi_Minh
```

---

## 4. Research Paper Digest

### Mô tả
Chạy mỗi **Thứ Bảy lúc 09:00 ICT**. Tổng hợp papers tuần. Cho researcher + builder đọc cuối tuần.

### Task prompt
```
Mỗi Thứ Bảy lúc 09:00 giờ Việt Nam, chạy AI Research Paper Digest cho 7 ngày qua.

Phạm vi:
- arXiv cs.AI / cs.CL / cs.LG / cs.CV / cs.RO
- Hugging Face Daily Papers
- Papers with Code
- Conference proceedings (NeurIPS, ICML, ICLR, ACL, EMNLP, CVPR, COLM khi đang publish)

Tập trung: LLM, AI Agents, reasoning, multimodal, RAG, inference optimization, evaluation, AI safety, alignment.

Với mỗi paper:
- Title + authors + affiliation
- Source link + status (preprint / accepted / industry)
- Problem
- Method (core idea, key components)
- Key result + benchmark + delta vs baseline
- Code availability + GitHub link nếu có
- Limitations
- Why read (for builder vs researcher)
- Recommended action

Phân nhóm theo theme nếu ≥3 papers cùng theme.

Top 5-7 papers deep + mention list 5-10 papers tốt nhưng không deep-dive.

Trả lời tiếng Việt.
```

### RRULE concept
```
FREQ=WEEKLY;BYDAY=SA;BYHOUR=9;BYMINUTE=0;BYSECOND=0
TIMEZONE=Asia/Ho_Chi_Minh
```

---

## 5. AI Safety & Policy Watch

### Mô tả
Chạy mỗi **Thứ Hai và Thứ Tư lúc 09:00 ICT**. Cực kỳ quan trọng vì EU AI Act enforcement bắt đầu Aug 2, 2026.

### Task prompt
```
Mỗi Thứ Hai và Thứ Tư lúc 09:00 giờ Việt Nam, chạy AI Safety & Policy Watch.

Phạm vi:
- EU AI Act timeline updates (especially Aug 2, 2026 high-risk enforcement)
- EU AI Office guidelines, GPAI Code of Practice updates
- US executive order on AI, US AISI
- UK AISI evaluations
- NIST AI RMF updates
- China generative AI regulations
- Korea AI Basic Act, Japan AI Promotion Act
- Copyright lawsuits (NYT, music labels, authors)
- Frontier model safety reports (Anthropic RSP, OpenAI Preparedness, Google FSF)
- Alignment research breakthroughs
- Jailbreak / prompt injection techniques
- Agent security
- METR / Apollo evaluations
- OWASP LLM Top 10 updates

Output:
- Bảng: Policy | Effective Date | Days from now | Region | AI system type | Required action
- Sắp xếp theo deadline gần nhất
- Highlight deadline < 60 ngày: Critical
- Highlight deadline 60-180 ngày: High
- Penalty range cho từng policy

Trả lời tiếng Việt.
```

### RRULE concept
```
FREQ=WEEKLY;BYDAY=MO,WE;BYHOUR=9;BYMINUTE=0;BYSECOND=0
TIMEZONE=Asia/Ho_Chi_Minh
```

---

## 6. Open-source AI Watch

### Mô tả
Chạy mỗi **Thứ Năm lúc 14:00 ICT**. Track open-weight model + inference ecosystem.

### Task prompt
```
Mỗi Thứ Năm lúc 14:00 giờ Việt Nam, chạy Open-source AI Watch cho 7 ngày qua.

Phạm vi:
- Open-weight model releases (Llama, Mistral, Qwen, DeepSeek, Gemma, Phi, Kimi, etc.)
- Dataset releases (instruction tuning, multimodal, reasoning, domain-specific)
- Fine-tuning recipes / cookbooks
- Inference engines: vLLM, SGLang, TensorRT-LLM, llama.cpp, MLX, ExecuTorch, Ollama, LM Studio
- Quantization: GGUF, AWQ, GPTQ, FP4, INT4
- Open eval frameworks: lm-evaluation-harness, OpenAI evals, Promptfoo
- Hugging Face ecosystem updates (Transformers, PEFT, TRL, Accelerate)

Cho mỗi model release:
- License + intended use
- Parameter count + active params (if MoE)
- Benchmark (note Tier of source)
- Hardware requirement
- Recommended use case
- Comparison vs closest closed model

Đề xuất 2-3 model team builder có thể thử trong quý này.

Trả lời tiếng Việt.
```

### RRULE concept
```
FREQ=WEEKLY;BYDAY=TH;BYHOUR=14;BYMINUTE=0;BYSECOND=0
TIMEZONE=Asia/Ho_Chi_Minh
```

---

## 7. Competitive Scan

### Mô tả
Chạy 2 tuần 1 lần, **Thứ Sáu xen kẽ** lúc 14:00 ICT. Dành cho Founder / Tech Lead / strategy review.

### Task prompt
```
Mỗi 2 tuần (Thứ Sáu lẻ tuần) lúc 14:00 giờ Việt Nam, chạy AI Competitive Scan.

So sánh OpenAI, Anthropic, Google DeepMind, xAI, Meta, Mistral, DeepSeek, Qwen, Cohere trong 14 ngày qua.

Tạo matrix:
- Capability (top model + benchmark snapshot)
- Agent strategy
- Developer platform
- API pricing (input/output/cached/batch)
- Open-source posture
- Safety posture
- Enterprise adoption signals
- Strategic move (partnership, hiring, funding)

Cuối brief: 3-5 paragraphs interpretation về ai đang dẫn ở đâu, strategic moves đáng chú ý, và gaps.

Trả lời tiếng Việt.
```

### RRULE concept
```
FREQ=WEEKLY;INTERVAL=2;BYDAY=FR;BYHOUR=14;BYMINUTE=0;BYSECOND=0
TIMEZONE=Asia/Ho_Chi_Minh
```

---

## 8. Quarterly Strategic Review

### Mô tả
Chạy đầu mỗi quý (1st Monday of Jan, Apr, Jul, Oct) lúc **10:00 ICT**. Review lớn cho leadership.

### Task prompt
```
Đầu mỗi quý lúc 10:00 ICT (1st Monday of Jan/Apr/Jul/Oct), chạy AI Frontier Quarterly Strategic Review.

Window: 90 ngày qua.

Cấu trúc:
1. Big shifts (3-5 trend major)
2. Frontier model state (capability ceiling, pricing trend)
3. Agent landscape state
4. Open-source vs closed gap analysis
5. Infrastructure / chip / pricing trend
6. Policy & regulation pipeline (next 180 ngày tới)
7. Safety / alignment progress
8. Business signals (revenue, deals, deployment)
9. Skill gap risks for team
10. Recommended priorities cho quý tới (technical + organizational + compliance)

Audience: Engineering leadership + Founder + Compliance.

Trả lời tiếng Việt.
```

### RRULE concept
```
FREQ=YEARLY;BYMONTH=1,4,7,10;BYDAY=1MO;BYHOUR=10;BYMINUTE=0;BYSECOND=0
TIMEZONE=Asia/Ho_Chi_Minh
```

---

## 9. On-demand Alert (event-driven)

### Mô tả
Trigger ngay khi có:
- Frontier model release (top-3 lab)
- EU AI Act enforcement milestone
- Critical CVE / jailbreak với production impact
- Major lab safety incident / model recall
- AISI pre-deployment block
- $1B+ deal

### Task prompt
```
Khi phát hiện sự kiện AI khẩn cấp, chạy Quick Alert với Template H:

- Topic
- Severity (Critical/High)
- Category (Model release / Safety / Policy / Security / Strategic)
- Affects (users/products/regions)
- What happened
- Why urgent
- Immediate action 1-3 bước
- Source link Tier 1
- Owner (role)
- Follow-up plan

Output cực ngắn (<300 từ). Trả lời tiếng Việt.
```

### Suggested cadence
Check Tier 1 sources every 4-6h cho:
- Lab official news pages
- arXiv recent (cs.AI)
- EU AI Office press releases
- AISI announcements
- Major chip / infra vendor releases

---

## Summary Table

| Brief | Frequency | Time (ICT) | Audience | Length |
|---|---|---|---|---|
| Daily AI Brief | Mon-Fri | 08:30 | Toàn team | ~10 min |
| Weekly AI Brief | Friday | 17:00 | Tech Lead + Founder + EM | ~20 min |
| AI Agents Watch | Wednesday | 17:00 | Builder + Product | ~15 min |
| Research Paper Digest | Saturday | 09:00 | Researcher + Builder | ~15 min |
| Safety & Policy Watch | Mon + Wed | 09:00 | Compliance + Legal + Tech Lead | Table-focused |
| Open-source AI Watch | Thursday | 14:00 | Builder + ML eng | ~15 min |
| Competitive Scan | Friday biweekly | 14:00 | Founder + Strategy | ~20 min |
| Quarterly Review | 1st Mon Jan/Apr/Jul/Oct | 10:00 | Leadership | ~30 min |
| Quick Alert | Event-driven | Realtime | Role owner | <300 từ |

---

## Notes về implementation

- **ChatGPT Tasks** / **Claude Scheduled Tasks** / **Gemini Scheduler** chỉ accept natural language, không RRULE. RRULE để tham khảo cho người setup thủ công + n8n/Zapier/Make.
- Nếu nền tảng giới hạn schedule, ưu tiên:
  1. Daily AI Brief (must-have)
  2. Weekly AI Brief
  3. Safety & Policy Watch (đặc biệt khi đến gần Aug 2, 2026)
  4. AI Agents Watch
  5. Research Paper Digest
- **Timezone**: Asia/Ho_Chi_Minh.
- **Cold start**: lần đầu, agent nên hỏi user xác nhận stack hiện tại (model đang dùng, budget tier, use case chính, region deploy) để tailor recommendation.
