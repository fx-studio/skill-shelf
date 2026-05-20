# Infographic Design Guide for AI Frontier Watch Skill

Hướng dẫn render brief markdown thành HTML infographic. Có 2 mode + 3 theme reference + anti AI-slop checklist.

---

## 0. Khi nào trigger

Skill **chỉ** render HTML khi user explicit request bằng keyword:
- `infographic this`, `infographic version`
- `render dưới dạng html`, `tạo html đẹp`
- `version để share`, `share-ready`, `Slack version`
- `cho tôi infographic`, `pdf version`

**Không tự động render**. Markdown brief là default. Lý do: render HTML tốn token + thời gian, đa số daily brief không cần.

**Pre-requisite**: brief markdown phải đã tồn tại trong conversation (skill cần data để render). Nếu chưa có brief, hỏi user: "Bạn muốn render infographic cho brief vừa rồi, hay tôi cần chạy brief mới trước?"

---

## 1. Workflow

1. **Parse user intent**: detect theme pin (xem section 2). Nếu không pin → mode A (Creative).
2. **Identify brief content**: lấy brief markdown gần nhất trong conversation làm source. Extract: title, date, TL;DR bullets, sections, items với category/priority/source/date/deadline, action items table.
3. **Decide aesthetic** (mode A) hoặc **load template** (mode B):
   - Mode A: phân tích content tone (xem section 3) → tự design typography + palette + layout
   - Mode B: đọc `assets/theme-{editorial|terminal|sober}.html` làm base
4. **Render** thành single HTML self-contained tới `/mnt/user-data/outputs/{slug}-{YYYYMMDD}.html`
5. **Self-check** pass anti AI-slop checklist (section 5)
6. **Present** bằng `present_files` để user download. Mention: "có thể save PDF từ browser (Cmd/Ctrl+P)".

---

## 2. Two modes

### Mode A — Creative (default khi không pin theme)

Skill có **freedom** trong:
- Font pairing (display + body)
- Color palette (dominant + accent)
- Layout (asymmetry, density, decorative elements)
- Decorative motifs (ascii dividers, drop caps, pull quotes, numbered annotations, footnotes)

Mục tiêu: mỗi brief có visual identity riêng. **Tránh** lặp lại visual giống brief trước.

Trước khi design, skill phân tích content:
- **Brief type**: daily / weekly / quarterly / paper / policy / agents / security?
- **Tone signal**: alert (security CVE)? scholarly (paper digest)? competitive (lab comparison)? regulatory (policy alert)?
- **Density**: dense data (cost analysis)? narrative-heavy (deep dive)? list-heavy (daily brief)?
- **Audience hint**: leadership (executive brief)? engineer (technical deep dive)? compliance (policy)?

Từ đó pick aesthetic direction. Ví dụ:
- Daily brief với 5 security alerts → terminal-leaning, dark, alert red accents, monospace
- Weekly brief về competitive landscape OpenAI vs Anthropic → magazine-style, editorial serif, comparative columns
- Quarterly review cho CTO → sober + restrained, large numbers, single accent color, generous whitespace
- Paper digest top 5 → academic, serif body, footnote-style citations, two-column dense
- EU AI Act policy alert → formal, government white paper feel, restrained palette, hierarchical numbered sections

### Mode B — Theme mode (khi user pin)

User gõ:
- `infographic this with editorial theme` / `editorial style`
- `infographic this terminal` / `terminal style`
- `infographic this sober` / `sober style`

→ Đọc file template tương ứng từ `assets/`:
- `assets/theme-editorial.html`
- `assets/theme-terminal.html`
- `assets/theme-sober.html`

→ Fill placeholders với brief data. Giữ aesthetic theme nguyên — chỉ thay nội dung.

Dùng mode B khi user share series bài cần visual consistency.

---

## 3. Three theme references

### 3.1 Editorial

**Inspired by**: Stratechery, The Information weekend essays, Financial Times Weekend Magazine, MIT Technology Review feature articles

**Typography**:
- Display/headline: serif characterful (GT Sectra, Tiempos Headline, Source Serif Pro, PT Serif). **Tránh**: Playfair (overused), Georgia (default-feeling).
- Body: sans với good rhythm (IBM Plex Sans, Söhne, National 2, PT Sans). **Tránh**: Inter, Roboto, Open Sans.
- Accent: italic serif cho quotes, small caps cho labels

**Palette**:
- Background: cream (#FAF7F2, #F4EFE6, #FBF9F4) — không pure white
- Text: warm ink (#1A1814, #2A2620) — không pure black
- Accent (chọn 1): deep teal (#0E4D5A), oxblood (#722F37), forest (#2C4A2C), navy ink (#0F2A44)
- Subtle: warm gray (#7A7368), beige border (#D4CBB8)

**Layout**:
- 2-column body với generous gutter (40-60px gap)
- Drop cap mở đầu major section
- Pull quote inline (large italic serif, 1.5-2x body size)
- Footnote-style citations (numbered superscript inline → footnote at bottom)
- Section dividers: thin rule hoặc small ornament (◆, ❦, ❧)

**Use case**: weekly brief, quarterly review, leadership brief, paper digest narrative

### 3.2 Terminal

**Inspired by**: vim color schemes (Tokyo Night, Catppuccin, Dracula), hacker terminal screenshots, retro tech magazine (Wired 1995), Phrack zine

**Typography**:
- Primary: monospace (JetBrains Mono, IBM Plex Mono, Berkeley Mono, IosevkaCommitMono). **Tránh**: Courier New, Consolas (system default).
- Optional accent sans cho hierarchy contrast: Söhne, Inter Display (use sparingly)
- All caps + letter-spacing cho status labels

**Palette**:
- Background: dark (#0D1117, #1A1B26, #1E1E2E, #181825)
- Foreground: warm white (#C0CAF5, #CDD6F4, #E5E5E5) — không pure white
- Accents (pick 2-3):
  - Terminal green (#7AA2F7, #A6E3A1, #50FA7B)
  - Amber/yellow (#E0AF68, #F9E2AF, #F1FA8C)
  - Cyan (#7DCFFF, #94E2D5, #8BE9FD)
  - Alert red (#F7768E, #F38BA8, #FF5555) — cho deadline / critical
  - Magenta (#BB9AF7, #CBA6F7, #BD93F9) — cho secondary accent

**Layout**:
- Status line top: `[ AI FRONTIER WATCH ] [ 2026-05-20 ] [ DAILY BRIEF ]`
- ASCII box dividers: `═══════` hoặc `─────────` hoặc `┌─ ─┐`
- Prompt prefix: `$` hoặc `>` hoặc `▶` cho action items
- Monospace tables với column alignment chính xác (padding bằng space)
- Box drawing chars (┌ ┐ └ ┘ ─ │) cho callout
- Blinking cursor element (CSS animation) cho 1 critical alert

**Use case**: daily brief, security alert, infra watch, agent watch, CVE report

### 3.3 Sober

**Inspired by**: Anthropic blog, Bloomberg Opinion, government white papers, McKinsey reports, Edward Tufte typography

**Typography**:
- Primary: refined sans (Söhne, National 2, ABC Diatype, IBM Plex Sans). Inter ONLY nếu thực sự không option khác.
- Secondary accent: minimal serif (cho quotes hoặc 1 large headline)
- Numbers: tabular figures (lining numerals) — quan trọng cho data viz

**Palette**:
- Background: pure white (#FFFFFF) hoặc near-white (#FAFAFA)
- Text: near-black (#0A0A0A, #1A1A1A) — không pure black
- Single muted accent: forest (#1B4332), navy (#1B263B), burgundy (#7D1935), slate (#475569)
- Border: light gray (#E5E5E5, #D4D4D4)

**Layout**:
- Generous whitespace (60-100px between sections)
- Strong typographic hierarchy: H1 huge (48-72px), H2 mid (24-32px), body 16-18px
- Minimal decoration — thin hairline rules only
- Numbered sections (1.1, 1.2) — government doc style
- Large pull statistics: 1 number 80-120px font size làm focal point
- Tables minimal: no zebra stripes, only horizontal rules between rows

**Use case**: policy alert, compliance brief, executive summary, leadership brief for skeptical audience

---

## 4. Technical constraints

### Self-contained
- Single HTML file (inline CSS, inline JS if minimal)
- Google Fonts OK (only allowed CDN). URL format: `<link href="https://fonts.googleapis.com/css2?family=...&display=swap" rel="stylesheet">`
- Không Tailwind CDN, không Chart.js, không React/Vue, không jQuery
- SVG icons inline OK (max 2-3 per page)
- File size target: < 80KB

### Responsive
- Min width 360px (mobile)
- Max width 800-1000px (centered, không full-screen)
- Test mental render: laptop 1440px, iPad 768px, iPhone 390px

### Print-friendly
```css
@media print {
  body { background: white !important; color: black !important; }
  .no-print { display: none; }
  a { color: black; text-decoration: underline; }
  a[href]:after { content: " (" attr(href) ")"; font-size: 0.7em; }
}
```

### Accessibility minimum
- Contrast ratio ≥ 4.5:1 cho body text (đặc biệt Terminal theme dark backgrounds)
- Semantic HTML: `<header>`, `<main>`, `<section>`, `<article>`, `<footer>`
- Alt text cho mọi SVG meaningful

---

## 5. Anti AI-slop Checklist

**Trước khi finalize HTML, verify từng dòng**:

### Fonts (CRITICAL)
- [ ] **Không** Inter / Roboto / Open Sans / Arial / Helvetica làm primary font
- [ ] Display font ≠ body font (font pairing có chủ đích)
- [ ] Tối thiểu 1 font có character (serif characterful, mono distinctive, hoặc condensed display)
- [ ] Đã link Google Fonts đúng URL với `display=swap`

### Color (CRITICAL)
- [ ] **Không** purple-to-blue gradient (`linear-gradient(to right, purple, blue)`)
- [ ] **Không** "tech glow" / neon glow / mặc định glass morphism
- [ ] Background **không** phải pure white `#FFFFFF` cho Editorial/Terminal (Sober được phép)
- [ ] Có rõ 1 dominant color + 1-2 accents, không "rainbow palette"
- [ ] Contrast ≥ 4.5:1 body text

### Layout (CRITICAL)
- [ ] **Không** 3-card-grid layout default (đây là AI slop signature)
- [ ] **Không** centered hero + 3 features below pattern
- [ ] Hierarchy rõ: 1 thứ là biggest, mọi thứ khác phải nhỏ hơn nhiều
- [ ] Asymmetry hoặc dense-vs-sparse contrast (không everything-evenly-spaced)
- [ ] Ít nhất 1 decorative element (ascii border, drop cap, pull quote, footnote, numbered annotation, large stat)

### Content fidelity (CRITICAL)
- [ ] Mọi số liệu trong infographic match markdown brief — không hallucinate
- [ ] Link Tier 1 visible (footer hoặc inline citations)
- [ ] Date format consistent với brief gốc
- [ ] Vietnamese narrative + English proper noun rule giữ nguyên
- [ ] Recommendation có role owner (giữ nguyên từ brief)

### Technical
- [ ] File saved to `/mnt/user-data/outputs/{slug}-{YYYYMMDD}.html`
- [ ] File size < 100KB
- [ ] Single HTML, no external resources except Google Fonts
- [ ] `@media print` block included
- [ ] Mobile rendering OK (mental test 390px width)
- [ ] No console errors mental simulate

**Nếu fail ≥ 1 CRITICAL item → rewrite, không deliver.**

---

## 6. Common pitfalls

1. **3-card grid default**: skill mới mở thường output 3 columns evenly spaced cards. Đây là AI slop signature. Tránh bằng cách: bắt đầu với hierarchy đơn (1 large + 2-3 small), hoặc asymmetric (60/40, 70/30).

2. **Inter font reflex**: skill auto-pick Inter vì nó "neutral & safe". Đây là sign AI generated. Force lấy font khác — đặc biệt cho display headline.

3. **Purple gradient on white**: classic AI slop. Tuyệt đối không.

4. **Emoji decoration spam**: 🎯🚀✨💡 mọi section. Mỗi emoji là 1 dấu hiệu lazy design. Cho phép tối đa 1 emoji functional (🚨 cho alert), không decoration.

5. **Quên `@media print`**: user save PDF ra trắng/đen lộn xộn vì dark background không print-adapt.

6. **Mock data nếu brief không có**: nếu user chưa chạy brief, đừng render infographic với data tự bịa. Hỏi user chạy brief trước.

7. **HTML file ở `/home/claude/...`**: user không thấy. Phải save vào `/mnt/user-data/outputs/`.

8. **Quên `present_files`**: file đã có ở outputs nhưng user không biết link. Phải call `present_files` ở cuối.

9. **Theme template fill bằng `replace()` raw**: nếu placeholder `{{TITLE}}` có ký tự đặc biệt trong content → break HTML. Phải HTML-escape khi inject.

10. **Render quá nhiều theme cùng 1 brief**: user gõ "infographic this" → chỉ render 1 version. Không output cả 3 theme. Nếu user muốn so sánh, render 1 cái rồi hỏi "muốn thử theme khác không?".

---

## 7. Implementation hint

```python
# Pseudo-code workflow trong skill execution

# 1. Detect theme
user_input = "infographic this terminal"
theme = detect_theme(user_input)  # 'editorial' | 'terminal' | 'sober' | None (creative)

# 2. Extract brief data
brief = parse_recent_brief(conversation_history)

# 3. Render
if theme:
    template = read_file(f"assets/theme-{theme}.html")
    html = fill_template(template, brief)
else:
    html = design_creative_html(brief)  # use creative mode, follow anti-slop rules

# 4. Self-check
checks = run_anti_slop_checklist(html)
if not all(checks):
    html = fix_failed_checks(html, checks)

# 5. Save + present
slug = slugify(brief.title)
date = brief.date.strftime('%Y%m%d')
output_path = f"/mnt/user-data/outputs/{slug}-{date}.html"
write_file(output_path, html)
present_files([output_path])
```

Không phải skill thực sự chạy Python — đây là mental model để skill follow.

---

## 8. Examples of good output (mental references)

Khi skill design, mental reference những visual đẹp đã có:
- Stratechery weekly essay layout
- The Information's "Org Charts" deep dives
- Anthropic's blog post about Sonnet 4.5
- OpenAI's safety report formatting
- METR's agent capability evaluation report
- EU AI Office's "AI Act Guidelines" PDF formatting
- Edward Tufte's "Visual Display of Quantitative Information" examples
- Information is Beautiful infographics
- Government white papers (UK AISI evaluation reports)

Không phải skill xem được những thứ này live — nhưng pattern visual của chúng là gold standard.
