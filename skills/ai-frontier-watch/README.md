# AI Frontier Watch — Skill

Phiên bản **skill** (Anthropic skill format) của bộ AI Frontier Watch Agent. Đây là dạng compact + cross-conversation của agent zip gốc, dùng được ở bất cứ conversation Claude nào không cần switch project.

## Bộ này làm gì

Theo dõi và brief biên giới AI cho engineering team Việt Nam:

- Frontier model releases (GPT-5.5, Claude Opus 4.7, Gemini 3.1 Pro, Llama 4, DeepSeek V4 Pro, Grok 4, Qwen)
- AI Agents (Claude Code, Codex CLI, Cursor, Devin, MCP ecosystem)
- Research papers (arXiv, HF Papers, NeurIPS/ICML/ICLR)
- AI safety & regulation (EU AI Act Aug 2 2026, US executive order, AISI, NIST)
- Benchmarks (SWE-bench Verified/Pro, GPQA, Terminal-Bench, GDPval, Humanity's Last Exam)
- Open-source AI (Llama, Mistral, Qwen, DeepSeek, Gemma)
- Infrastructure & API pricing (NVIDIA, AMD, Groq, Cerebras, cloud capacity)
- Business signals (revenue, M&A, partnership)
- Developer tooling (IDE agents, eval platforms, LLM gateways)

## Cấu trúc

```
ai-frontier-watch/
├── SKILL.md                          # Master + workflow router (203 lines)
├── references/
│   ├── search-criteria.md            # Topic scope, time window, query templates
│   ├── source-whitelist.md           # 5-tier source list (Tier 1 mandatory cho fact)
│   ├── output-templates.md           # 8 brief templates (Daily/Weekly/Deep Dive/Model/Paper/Policy/Competitive/Quick Alert)
│   ├── command-catalog.md            # 34+ commands chia 2 nhóm A định kỳ + B on-demand
│   ├── schedule-descriptions.md      # 9 schedule Vietnam timezone (cho external scheduler)
│   ├── quality-rubric.md             # 5-dim scoring + priority mapping + sub-rubrics
│   └── infographic-design.md         # HTML render workflow + anti AI-slop rules
└── assets/
    ├── theme-editorial.html          # Editorial theme (Stratechery / FT Weekend)
    ├── theme-terminal.html           # Terminal theme (Tokyo Night / hacker)
    ├── theme-sober.html              # Sober theme (Anthropic blog / white paper)
    └── theme-tokens.css              # Shared CSS variables (reference)
```

## Khác gì so với bộ agent zip gốc?

| Aspect | Agent zip | Skill |
|---|---|---|
| **Trigger** | Paste file 00 vào project instructions, agent luôn in-character | Description frontmatter, kích hoạt theo context |
| **Load** | 8 files load đồng thời (tốn token) | Progressive disclosure — chỉ SKILL.md load mặc định |
| **Cross-conversation** | Phải mở project riêng | Bất kỳ conversation Claude nào |
| **Help trigger** | Trigger bằng "chào/hi" | Bỏ "chào". Giữ "menu/help/?" |
| **HTML infographic** | Không có | **MỚI** — `infographic this` để render |
| **Schedule task** | File 05 paste vào Claude Scheduled Tasks / ChatGPT Tasks | File 05 giữ nguyên — skill không tự chạy schedule |

## Tính năng MỚI: HTML Infographic

Sau khi có brief markdown, gõ:
- `infographic this` — skill tự design theme dựa trên nội dung (creative mode)
- `infographic this editorial` — theme magazine (serif, dense, scholarly)
- `infographic this terminal` — theme tech (monospace, dark, alert)
- `infographic this sober` — theme executive (typographic, restrained)

Output: single HTML self-contained → save vào `/mnt/user-data/outputs/`. User download và share Slack/LinkedIn, hoặc save PDF từ browser (Cmd/Ctrl+P).

Skill tuân thủ anti AI-slop checklist nghiêm ngặt: không Inter font primary, không purple gradient on white, không 3-card-grid layout default, có decorative element thực sự (drop cap, ASCII border, large hero stat, footnotes).

## Cách cài đặt

### Claude.ai Skill

1. Zip folder `ai-frontier-watch/` thành `ai-frontier-watch.skill`
2. Upload vào Claude.ai → Settings → Skills → Install
3. Skill sẽ tự kích hoạt khi bạn hỏi về AI news/models/regulation/benchmarks

### Dùng dạng folder cho ChatGPT Custom GPT / Gemini Gem

1. Copy nội dung `SKILL.md` vào Instructions (có thể cần move 1 số section qua Knowledge nếu vượt 8000 char limit của ChatGPT)
2. Upload các file `references/*.md` vào Knowledge
3. Upload `assets/*.html` để có thể reference khi render infographic
4. Bật web browsing capability (bắt buộc)

### Dùng làm reference cho n8n / Zapier / Make scheduled

1. Copy `references/schedule-descriptions.md` để biết task prompt cho 9 schedule
2. Setup cron → API call Anthropic / OpenAI với system prompt là SKILL.md + relevant reference

## Triết lý xuyên suốt

7 nguyên tắc gốc giữ 100%:

1. **Deadline-first** — Mỗi item quan trọng có anchor deadline (EU AI Act Aug 2 2026 là deadline lớn nhất hiện tại)
2. **Role-aware action** — Không "team should". Phải có role chịu trách nhiệm cụ thể
3. **5-tier source whitelist** — Tier 1 bắt buộc cho fact, Tier 5 chỉ discover
4. **Vietnam timezone aware** — Daily Brief 08:30 ICT để bắt tin US đêm qua
5. **Vietnamese narrative + English proper noun** — Câu chuyện tiếng Việt, giữ tiếng Anh cho model name/benchmark/framework
6. **Help/Menu behavior** — Trigger `menu/help/?` → list 34+ lệnh
7. **No hype, no padding** — Không "cách mạng", "game-changer". Ngày low-news viết brief ngắn

## Khi nào dùng skill này vs agent zip?

| Tình huống | Format |
|---|---|
| Hỏi ad-hoc xuyên conversation, không setup riêng | **Skill** |
| Daily scheduled brief, team consume định kỳ | **Agent zip** (paste vào project Claude / ChatGPT Tasks) |
| Cần HTML infographic share Slack/LinkedIn | **Skill** |
| Team mới onboarding cần "chào → menu" | **Agent zip** (skill không trigger bằng greeting) |
| Stack-aware long-term memory | **Agent zip** với project memory |

Có thể dùng cả 2 đồng thời — không xung đột.

## Roadmap

Sau 1-2 tháng deploy, có thể:

- Tạo thêm theme cho infographic (Print-zine, Cyberpunk, Brutalist)
- Bonus reference file: `team-stack.md` — user maintained, ghi stack hiện tại, skill consult khi recommend
- Cross-skill integration: nếu user có `mobile-frontier-watch` skill cùng install → có thể combine brief
- Tích hợp dữ liệu offline: `assets/data/eu-ai-act-timeline.json`, `assets/data/lab-events-2026.json` để skill query nhanh không cần web search mỗi lần

## License

Free to fork, modify, share trong team. Nếu cải tiến đáng kể, share lại với community Vietnamese AI builder.

---

**Last updated**: 2026-05-20
**Format version**: Skill v1 (Anthropic skill format)
**Source agent**: AI Frontier Watch Agent v2 (zip format)
**Designed for**: AI builder, researcher, PM, founder, compliance, infra engineer
**Critical deadline tracked**: EU AI Act Aug 2, 2026 (high-risk obligations enforcement)
