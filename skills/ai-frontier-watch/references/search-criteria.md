# Search Criteria for AI Frontier Watch Agent

## Time Windows

**Daily Brief**:
- Primary: 24h
- Extended: 48h khi cuối tuần / news volume thấp

**Weekly Brief**:
- Primary: 7 ngày
- Extended context: 30 ngày cho trend comparison

**Paper Digest**:
- Primary: 7 ngày
- arXiv crossref: 14 ngày để bắt paper được retweet/discussed sau publish

**Policy/Compliance Watch**:
- Lookahead: 180 ngày tới (EU AI Act phase rollout cần biết sớm)
- Lookback: 30 ngày

**Model Release Watch**:
- Continuous (event-driven)
- Lookback 7 ngày sau release để gom community evaluation

**Deep Dive**:
- 30-90 ngày tuỳ chủ đề

**Competitive Scan**:
- 7 ngày cho regular
- 30 ngày cho quarterly view

**Monthly/Quarterly Review**:
- 30 / 90 ngày
- Prefer trend analysis over item-by-item

## Topic Inclusion Criteria

### Foundation Models & LLMs
1. Frontier model release (OpenAI GPT-5+, Anthropic Claude 4+, Google Gemini 3+, xAI Grok 4+, Meta Llama 4+, Mistral Large+, DeepSeek V4+, Qwen 3+)
2. Reasoning model / "thinking" model variant
3. Multimodal model (text + image/video/audio)
4. Long-context / large-output model
5. Subquadratic / efficient architecture (Mamba, RWKV, SubQ)
6. Small language model (SLM) for edge

### AI Agents
7. Coding agents (Claude Code, Codex CLI, Cursor Composer, Devin, Augment, Aider, OpenCode, Cline, Roo Code)
8. Browser/computer-use agents (Anthropic Computer Use, OpenAI Operator, Browser Use)
9. Research agents (Perplexity Deep Research, OpenAI Deep Research, Gemini Deep Research)
10. Autonomous agents (Manus, AutoGPT successors)
11. Multi-agent framework (LangGraph, CrewAI, AutoGen, MetaGPT)
12. Agent protocols (Model Context Protocol/MCP, Agent2Agent/A2A, Agent Communication Protocol/ACP)
13. Tool use, function calling improvements

### Research & Methods
14. New training method (DPO successors, RLAIF variants, synthetic data)
15. Post-training technique (distillation, quantization, model merging, LoRA variants)
16. Inference-time technique (speculative decoding, batching, KV cache, prompt caching)
17. RAG advances (better retrievers, agentic RAG, GraphRAG, hybrid retrieval)
18. Embedding model release
19. Vector DB / retrieval infra (Weaviate, Pinecone, pgvector, LanceDB, Turbopuffer)
20. Agent memory architectures
21. Evaluation methodology (LLM-as-judge, head-to-head arena, simulator-based)

### Benchmarks
22. New benchmark release
23. Benchmark contamination report / methodology issue
24. Leaderboard major shift
25. Domain-specific eval (medical, legal, finance, science, math)

### Open-source AI
26. Open-weight frontier-tier model release
27. Open dataset release
28. Open evaluation framework
29. Fine-tuning recipe / cookbook
30. Inference engine (vLLM, SGLang, TensorRT-LLM, llama.cpp, MLX, ExecuTorch, Ollama, LM Studio)
31. Model quantization technique (GGUF, AWQ, GPTQ, FP4)

### Infrastructure
32. NVIDIA chip / NVLink / Blackwell, AMD MI300/MI400, Groq, Cerebras, Tenstorrent, Etched
33. Google TPU updates
34. Cloud provider AI capacity (AWS, GCP, Azure, Oracle, CoreWeave, Lambda)
35. AI data center buildout, energy/cooling
36. Model serving platforms (Together, Fireworks, Replicate, Modal, RunPod)
37. Inference pricing changes (frontier APIs, open-source endpoints)

### AI Safety & Security
38. Frontier model safety report (Anthropic RSP, OpenAI Preparedness, Google Frontier Safety)
39. Alignment research (interpretability, scalable oversight, weak-to-strong)
40. Jailbreak / prompt injection new technique
41. Agent security (privilege escalation, data exfiltration, prompt injection in tool use)
42. Model weight theft / supply chain risk
43. OWASP Top 10 for LLM Applications updates
44. METR autonomous capability evaluation

### Policy & Regulation
45. **EU AI Act milestones** (especially Aug 2, 2026 enforcement)
46. EU AI Office guidelines, GPAI Code of Practice updates
47. US executive order on AI
48. NIST AI Risk Management Framework updates
49. UK AISI / US AISI evaluations and pre-deployment access
50. China AI regulation (generative AI rules, deep synthesis, algorithmic recommendation)
51. Korea AI Basic Act, Japan AI Promotion Act
52. Copyright lawsuit (NYT v OpenAI, music labels v Anthropic, authors v Meta, etc.)
53. Election / deepfake regulation
54. Frontier Model Forum, voluntary commitments

### Business & Strategic
55. AI lab funding round
56. Strategic partnership (lab × cloud, lab × hardware, lab × enterprise vertical)
57. Enterprise AI deployment story (with numbers)
58. Earnings call AI revenue figures
59. M&A in AI ecosystem
60. Leadership change at major lab
61. AI startup hiring / market signal

### Developer Tooling
62. IDE AI integration (Cursor, Windsurf, Zed AI, JetBrains AI Assistant, Xcode Predictive)
63. Agent platform (LangSmith, Helicone, Langfuse, Pydantic AI)
64. Eval platform (Braintrust, Promptfoo, OpenAI evals)
65. LLM gateway (LiteLLM, Portkey, OpenRouter)
66. AI observability / tracing

## Exclusion Criteria

Exclude:
- Generic AI opinion piece without new evidence
- SEO listicle ("Top 10 prompts", "Best AI tools 2026") without primary research
- Influencer hot takes
- App review của AI product không có technical insight
- Funding < $50M not strategically important
- Speculation without sourcing (X/Twitter rumor)
- Duplicate coverage same announcement
- Marketing post without technical/strategic detail
- Hardware review (consumer device AI feature) trừ khi có dev API impact
- AI ethics philosophy debate without concrete event

## Search Query Templates

### Daily frontier AI
- site:openai.com/news
- site:anthropic.com/news
- site:deepmind.google/discover/blog
- site:ai.meta.com/blog
- site:mistral.ai/news
- site:x.ai/news
- site:qwenlm.github.io
- site:machinelearning.apple.com
- "model card" OR "system card" 2026
- "frontier model" release announcement
- "context window" "API" model

### Daily AI agents
- "Claude Code" release notes
- "Codex CLI" OR "Codex Cloud" update
- "Cursor" release announcement
- "Devin" Cognition release
- "MCP" "Model Context Protocol" server
- "A2A" "Agent2Agent" protocol
- "browser use" agent benchmark
- "computer use" agent
- "SWE-bench Verified" 2026
- "Terminal-Bench" 2026
- "GDPval" benchmark
- "agent memory" framework

### Research papers
- site:arxiv.org/abs cs.AI recent
- site:arxiv.org/list/cs.CL/recent
- site:huggingface.co/papers
- site:paperswithcode.com
- "arXiv" LLM reasoning
- "arXiv" multimodal large language
- "arXiv" agent evaluation benchmark
- "arXiv" RAG retrieval
- "arXiv" inference optimization

### Open-source AI
- site:huggingface.co/blog
- "Llama" release new
- "Mistral" open-weight
- "Qwen" release Apache
- "DeepSeek" model open
- "Gemma" release
- "vLLM" version release
- "SGLang" release
- "llama.cpp" release
- "Ollama" model new

### Safety & policy
- "EU AI Act" 2026 enforcement
- site:ai-act-service-desk.ec.europa.eu
- site:digital-strategy.ec.europa.eu
- "GPAI Code of Practice"
- "AI Safety Institute" frontier model
- "NIST AI RMF"
- "METR" agent evaluation
- "prompt injection" 2026 attack
- "jailbreak" frontier model
- "copyright lawsuit" AI 2026

### Infrastructure
- "NVIDIA Blackwell" GB200 GB300
- "AMD MI300" OR "MI400"
- "Groq" LPU inference
- "Cerebras" wafer-scale
- "TPU v6" OR "Trillium" Google
- "data center" AI capacity 2026
- "inference cost" per million tokens

### Business
- "AI revenue" earnings call 2026
- "OpenAI" valuation
- "Anthropic" funding partnership
- "enterprise AI" deployment 2026
- "AI partnership" cloud
- site:reuters.com AI lab
- site:ft.com AI

### Benchmarks
- "LMArena" leaderboard
- "Artificial Analysis" intelligence index
- "Humanity's Last Exam"
- "GPQA Diamond"
- "MMLU-Pro"
- "SWE-bench Pro"
- "Terminal-Bench 2.0"
- "GDPval"
- "AIME" 2026 model
- benchmark contamination 2026

### Pricing / API
- "API pricing" OpenAI Anthropic Google 2026
- "deprecation" model OpenAI
- "$/M tokens" frontier 2026
- "prompt caching" pricing
- "batch API" discount

## Ranking — rank higher when

- Item từ Tier 1 (official lab post, model card, paper)
- Item áp đặt deadline trong 60-180 ngày
- Item là frontier-tier release (top-3 capability)
- Item có cross-reference benchmark từ multiple sources
- Item ảnh hưởng cost cấu trúc (pricing change, new efficiency)
- Item là safety/security với evidence
- Item là policy với enforcement date confirmed

## Ranking — rank lower when

- Speculation chưa confirmed
- Self-reported benchmark only
- Region availability không match user
- Old story rehash

## Reliability Labels

- **High**: Lab official, model card, system card, paper với code, regulator filing
- **Medium**: Conference video, reputable engineer blog, top-tier journalism multi-source
- **Low**: Social media, anonymous leak, single-source rumor

## Confidence Labels

- **High**: Primary + corroboration
- **Medium**: Credible secondary, primary chưa available
- **Low**: Rumor / The Information / Reuters single source

## Actionability Labels

- **High**: Cần migrate / patch / submit / review compliance < 90 ngày
- **Medium**: Evaluate quý này
- **Low**: Monitor

## Special Triggers

### Recurring milestones
- **Feb 2** (annual): EU AI Act prohibited practices anniversary, retro review
- **Aug 2, 2026**: **EU AI Act high-risk enforcement begins** — CRITICAL
- **Aug 2, 2027**: EU AI Act fully applicable + retroactive GPAI compliance
- **Quarterly earnings**: NVIDIA, Microsoft, Google, Meta — AI revenue/capex signal
- **Major events**: NeurIPS (Dec), ICML (Jul), ICLR (May), CVPR (Jun), OpenAI DevDay, Anthropic event

### Auto-escalate to Critical
- Frontier model release với SOTA on major benchmark
- EU AI Act enforcement action announced
- CVE >= 9.0 trong agent framework phổ biến
- Major lab safety incident / model recall
- US/UK AISI pre-deployment block
- $1B+ deal trong AI ecosystem
