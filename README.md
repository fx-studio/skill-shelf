# skill-shelf

A small, growing shelf of [Claude Skills](https://www.anthropic.com/news/skills) — each one solves a narrow problem well, none of them try to be a platform.

Pick what you need. Leave the rest on the shelf.

> 🇻🇳 [Đọc bản tiếng Việt bên dưới](#tiếng-việt) ↓

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
| [ai-frontier-watch](./skills/ai-frontier-watch) | Daily/weekly brief on AI frontier... | Khi cần track model release, paper, EU AI Act |

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
# Clone the repo
git clone https://github.com/<your-username>/skill-shelf.git

# Project-scoped (recommended for team skills)
mkdir -p .claude/skills
cp -r skill-shelf/skills/<skill-name> .claude/skills/

# User-scoped (available across all your projects)
mkdir -p ~/.claude/skills
cp -r skill-shelf/skills/<skill-name> ~/.claude/skills/
```

Restart Claude Code and the skill is picked up.

### API / agent frameworks

Skills are just folders with a `SKILL.md` at the root. Most agent frameworks let you load them as system context or as tools. Check the framework's docs for the loader pattern.

---

## Repo structure

```
skill-shelf/
├── README.md
├── LICENSE
└── skills/             # All skills live here
    ├── <skill-a>/
    │   └── SKILL.md
    ├── <skill-b>/
    │   └── SKILL.md
    └── ...
```

One folder per skill under `skills/`. Each skill is self-contained — clone the repo, copy the folder you want into your Claude skills directory, done.

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

[MIT](./LICENSE). Use them, fork them, modify them, ship them in your own products. A credit link back is appreciated but not required.

---

## Acknowledgments

Built with [Claude](https://claude.com) by Anthropic. The skill format is theirs; the contents here are mine and contributors'.

If a skill saves you an afternoon, consider opening a PR with one of your own. That's the only currency this shelf trades in.

---
---

# Tiếng Việt

Một cái kệ nhỏ chứa các [Claude Skill](https://www.anthropic.com/news/skills) — mỗi skill giải quyết tốt một bài toán hẹp, không có cái nào cố trở thành platform.

Cần cái nào thì lấy. Cái nào không cần thì để yên trên kệ.

---

## Skill là gì?

Skill là một thư mục Claude đọc khi cần. Bạn bỏ vào đó một file `SKILL.md` (phần instruction chính), kèm các file tham khảo, script, hoặc template mà task cần. Khi bạn hỏi Claude một việc khớp với description của skill, nó load thư mục đó và chạy theo playbook bên trong.

Coi như là *muscle memory bạn có thể copy-paste*. Thay vì mỗi lần lại giải thích "đây là cách tôi muốn render diagram", bạn viết ra một lần và Claude tự với tới mỗi khi đụng đến chủ đề đó.

Skill trong repo này tuân theo một quy tắc: **bề mặt hẹp, dùng được thật, không thừa nghi lễ.** Nếu một skill cần năm đoạn intro để biện minh cho sự tồn tại, nó chưa xứng đáng lên kệ này.

---

## Trên kệ

> Skill được sắp xếp theo *việc giúp bạn làm gì*, không theo *được build trên cái gì*.

| Skill | What it does | When to reach for it |
|---|---|---|
| [ai-frontier-watch](./skills/ai-frontier-watch) | Daily/weekly brief on AI frontier... | Khi cần track model release, paper, EU AI Act |

Mỗi thư mục skill là self-contained. Đọc `SKILL.md` của nó để xem trigger condition, input cần có, và ví dụ output.

---

## Triết lý

Vài điều rút ra khi build mấy cái này:

**Hẹp thắng rộng.** Một skill làm tốt một việc giá trị hơn mười skill làm được tất cả nhưng đều tàm tạm. Khi bạn thấy mình đang thêm "và cũng xử lý X, Y, Z" vào description, đó là dấu hiệu phải tách.

**Description chính là sản phẩm.** Claude chỉ load skill khi description khớp với request. Description mơ hồ = skill không bao giờ fire. Đầu tư thời gian viết description nhiều hơn viết body.

**File tham khảo thay vì nhồi rule inline.** Nếu skill có checklist 30 dòng, tách ra file riêng để skill đọc khi cần. Giữ `SKILL.md` ngắn — vì nó được load vào mọi conversation đụng đến domain của skill.

**Skill compose được.** Hai skill nhỏ dùng kết hợp thường thắng một skill to cố đoán trước mọi combination.

**Giá trị nhỏ mỗi ngày > giá trị lớn hiếm khi dùng.** Một skill tiết kiệm 90 giây × 5 lần/tuần giá trị hơn skill tiết kiệm 1 tiếng nhưng cả quý dùng một lần — vì cái đầu bạn *thực sự dùng*.

---

## Cài đặt

### Claude (web / desktop / mobile)

1. Vào Settings → **Capabilities** → **Skills**
2. Click **Upload skill** rồi chọn thư mục skill (đã zip) hoặc từng file riêng
3. Skill có sẵn cho mọi conversation — Claude tự quyết khi nào dùng dựa vào description

### Claude Code

```bash
# Clone repo
git clone https://github.com/<your-username>/skill-shelf.git

# Scope project (recommended cho team skill)
mkdir -p .claude/skills
cp -r skill-shelf/skills/<skill-name> .claude/skills/

# Scope user (dùng được cho mọi project của bạn)
mkdir -p ~/.claude/skills
cp -r skill-shelf/skills/<skill-name> ~/.claude/skills/
```

Khởi động lại Claude Code, skill được pick up.

### API / agent framework

Skill chỉ là thư mục có `SKILL.md` ở root. Hầu hết agent framework cho phép load như system context hoặc tool. Đọc docs của framework để biết loader pattern.

---

## Cấu trúc repo

```
skill-shelf/
├── README.md
├── LICENSE
└── skills/             # Tất cả skill nằm ở đây
    ├── <skill-a>/
    │   └── SKILL.md
    ├── <skill-b>/
    │   └── SKILL.md
    └── ...
```

Một thư mục cho một skill, đặt dưới `skills/`. Mỗi skill là self-contained — clone repo, copy thư mục bạn cần vào Claude skills directory, xong.

---

## Cấu trúc một skill

Mọi skill trên kệ này đều theo cấu trúc tối thiểu giống nhau:

```
<skill-name>/
├── SKILL.md           # Bắt buộc. Description + instruction.
├── reference/         # Tùy chọn. File Claude đọc khi cần.
├── scripts/           # Tùy chọn. Script helper skill có thể chạy.
└── examples/          # Tùy chọn. Sample input/output.
```

`SKILL.md` bắt đầu bằng frontmatter:

```yaml
---
name: my-skill
description: Một câu mô tả nó làm gì. Trigger condition khi nào dùng.
---
```

Description là dòng quan trọng nhất trong toàn bộ skill. Claude đọc *chỉ mỗi description* trước; chỉ load phần còn lại nếu description khớp.

Description tốt phải nêu: **task**, **trigger** (keyword, kiểu file, ngữ cảnh), và lý tưởng là một **non-trigger** (khi nào *không* dùng). Description dở thường viết "giúp làm X" — mơ hồ, ambiguous, recall thấp.

---

## Đóng góp

PR welcome. Tiêu chuẩn:

- **Giải quyết một việc.** Nếu skill cần mode selector hoặc cây sub-command, nhiều khả năng nó là hai skill.
- **Description sắc.** Người đọc *chỉ description* phải biết task của họ có khớp không.
- **Test được.** Bỏ ít nhất một example vào `examples/` để behavior quan sát được.
- **Không trùng.** Check kệ trước. Cải thiện skill có sẵn thắng add một skill gần giống.

Không chắc ý tưởng có hợp không, mở issue trước. Tôi thà bàn về shape còn hơn reject PR.

---

## Cái gì không có ở đây

Không phải prompt hữu ích nào cũng xứng đáng thành skill. Một số thứ repo này cố tình *không* chứa:

- **Prompt một-lần.** Nếu bạn dùng 2 lần rồi thôi, paste là đủ. Skill là cho việc lặp lại nhiều lần.
- **Wrapper quanh capability cơ bản của Claude.** Claude đã viết code, tóm tắt document, dịch sẵn rồi. Một skill nói "viết code cho tốt" không phải là skill.
- **Skill cần credential hoặc dịch vụ trả phí ngay cả để đọc.** Skill ở đây phải inspect được end-to-end mà không cần account nào.

---

## License

[MIT](./LICENSE). Dùng, fork, sửa, đóng gói vào sản phẩm của bạn. Credit ngược lại được trân trọng nhưng không bắt buộc.

---

## Lời cảm ơn

Build với [Claude](https://claude.com) của Anthropic. Format skill là của họ; nội dung trong này là của tôi và các contributor.

Nếu một skill ở đây tiết kiệm cho bạn một buổi chiều, cân nhắc mở PR đóng góp một skill của bạn. Đó là loại tiền tệ duy nhất kệ này trao đổi.
