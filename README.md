# مهارة الخطبة المنبرية
### (Arabic Khutba Skill — Fiqh + Craft + Verification)

**Arabic khutba skill for AI agents** — writes and revises Friday and occasion khutbas with a madhhab-aware fiqh layer, a two-khutba structure, delivery notes, and a strict reference-verification protocol. It asks for the user's madhhab before drafting, refuses to fabricate Quran/hadith citations, keeps a reference ledger, asks permission before adding poetry, and flags sensitive topics. Works with Claude Code, Codex, Antigravity and VS Code agent harnesses.

🔗 **الموقع المرجعي (الدليل والفقه والبناء والتحقق والنماذج): [specailm5.github.io/arabic-khutba-skill](https://specailm5.github.io/arabic-khutba-skill/)**

> مهارة برمجية وشرعية لوكلاء الذكاء الاصطناعي لكتابة **الخطبة المنبرية** على أصولها: سؤال المذهب، وبناء الخطبتين، والمراجع المتحققة، وبوابة الشعر، وحساسية المنبر — مستندة إلى **«فن الخطابة»** لحسين بن محمد آل شامر، و**«الخطابة الإسلامية»** لعبد العاطي محمد شلبي، و**«خطبة الجمعة في الكتاب والسنة»** لعبد الرحمن بن محمد الحمد، و**«الفقه على المذاهب الأربعة»** لعبد الرحمن الجزيري.

> **تنبيه:** هذه المهارة **لصناعة الخطبة وتحريرها، لا للفتوى**. تعرض أقوال المذاهب كما في مصادرها، والفتوى للجهة التي يتبعها المستخدم أو لعالمه.

---

## 📖 ما هي المهارة؟

مهارة تُعلِّم الوكيل الذكي أربعة أمور لا تتفرّق:

1. **السؤال قبل الكتابة:** ما المذهب؟ ما المناسبة؟ من الجمهور؟ ما الرسالة الواحدة؟ هل يُسمح بالشعر؟
2. **البناء:** خطبتان على عقد واضح: افتتاح، تمهيد، تأصيل، نقطتان، تطبيق، خاتمة؛ ثم جلوس؛ ثم خطبة ثانية ودعاء.
3. **الفقه المذهبي:** الأركان والشروط واللغة والجلوس والدعاء عند الحنفية والمالكية والشافعية والحنابلة، بلا خلط ولا فتوى.
4. **التحقق:** كل آية بسورة وآية، وكل حديث بمصدر ورقم وحكم، وكل أثر بكتاب وموضع، وكل بيت بشاعر وديوان — أو يُحذف.

**القواعد الأربع:**
> **اسأل عن المذهب. رسالة واحدة. لا نصّ بلا مصدر. المنبر للرحمة.**

---

## 📂 بنية المهارة

```
arabic-khutba-skill/
│
├── skills/arabic-khutba-skill/
│   ├── SKILL.md                          # الدليل الأساسي (المنهج + الفقه + التحقق)
│   ├── references/
│   │   ├── fiqh_madhahib.md             # الأركان والشروط والسنن عند المذاهب الأربعة
│   │   ├── structure_and_delivery.md     # البناء والجمهور والإلقاء
│   │   ├── reference_verification.md     # بروتوكول التحقق وسجل المراجع
│   │   └── occasions_and_sensitivity.md  # المناسبات والحساسية وبوابة الشعر
│   └── examples/
│       ├── verified_khutba_outline.md    # نموذج خطبة بمراجع متحققة
│       └── before_after_khutba.md        # نماذج قبل/بعد
│
├── docs/                                 # الموقع المرجعي (GitHub Pages)
├── .agents/skills/arabic-khutba-skill/   # مسار Codex و Antigravity
└── .claude/skills/arabic-khutba-skill/   # مسار Claude Code
```

---

## 🚀 التثبيت

### أولاً: بأمر واحد عبر `npx`

```bash
npx skills add specailm5/arabic-khutba-skill -g -y
```

أو لبيئات محددة:

```bash
npx skills add specailm5/arabic-khutba-skill -a claude-code -a codex
npx skills add specailm5/arabic-khutba-skill --skill arabic-khutba-skill -g -y
```

### ثانياً: يدوياً (Windows)

```powershell
$src = "skills\arabic-khutba-skill"

New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills\arabic-khutba-skill"
Copy-Item -Recurse -Force "$src\*" "$env:USERPROFILE\.claude\skills\arabic-khutba-skill\"

New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills\arabic-khutba-skill"
Copy-Item -Recurse -Force "$src\*" "$env:USERPROFILE\.agents\skills\arabic-khutba-skill\"

New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.gemini\config\skills\arabic-khutba-skill"
Copy-Item -Recurse -Force "$src\*" "$env:USERPROFILE\.gemini\config\skills\arabic-khutba-skill\"
```

### ثالثاً: داخل مشروع (VS Code Workspace)

انسخ `skills/arabic-khutba-skill` إلى `.agents/skills/` أو `.claude/skills/` في جذر مشروعك.

---

## ⚡ كيف تعمل؟

### الأسئلة الخمسة

| السؤال | لماذا؟ |
| :--- | :--- |
| **ما مذهبك/مذهب المسجد؟** | الأركان والشروط واللغة تختلف |
| **ما المناسبة؟** | لكل مناسبة عقدها |
| **من الجمهور؟** | المستوى والطول والأمثلة |
| **ما الموضوع والرسالة الواحدة؟** | الخطبة التي تحمل عشر رسائل لا تحمل رسالة |
| **هل تسمح بالشعر؟** | لا يُقحم بلا إذن، ولا يُنسب بلا تحقق |

### الفقه: الجدول الجامع

<table dir="rtl">
<thead>
<tr><th align="right">المسألة</th><th align="right">الحنفي</th><th align="right">المالكي</th><th align="right">الشافعي</th><th align="right">الحنبلي</th></tr>
</thead>
<tbody>
<tr><td><strong>الأركان</strong></td><td>واحد: مطلق الذكر</td><td>واحد: تحذير/تبشير</td><td>خمسة</td><td>أربعة</td></tr>
<tr><td><strong>الحمد</strong></td><td>ليس ركناً</td><td>ليس ركناً</td><td>ركن</td><td>ركن</td></tr>
<tr><td><strong>الدعاء للمؤمنين</strong></td><td>سنة</td><td>سنة</td><td><strong>ركن</strong> في الثانية</td><td>سنة</td></tr>
<tr><td><strong>اللغة</strong></td><td>تصح بغير العربية</td><td><strong>العربية شرط</strong></td><td>الأركان بتفصيل</td><td>العربية للقادر</td></tr>
<tr><td><strong>الجلوس</strong></td><td>سنة</td><td>سنة</td><td><strong>شرط</strong></td><td>سنة</td></tr>
</tbody>
</table>

### سجل المراجع

<table dir="rtl">
<thead>
<tr><th align="right">النص</th><th align="right">المصدر</th><th align="right">الرقم</th><th align="right">الحكم</th><th align="right">الحالة</th></tr>
</thead>
<tbody>
<tr><td>«إن طول صلاة الرجل وقصر خطبته...»</td><td>مسلم</td><td>٨٦٩</td><td>صحيح</td><td>متحقق</td></tr>
<tr><td>«من تخطى رقاب الناس... جسراً إلى جهنم»</td><td>الترمذي</td><td>—</td><td>ضعيف</td><td>محذوف</td></tr>
<tr><td>«أدِّ الأمانة إلى من ائتمنك...»</td><td>أبو داود ٣٥٣٤ / الترمذي ١٢٦٤</td><td>—</td><td>حسن غريب وفيه كلام</td><td>لا يُستخدم وحده</td></tr>
</tbody>
</table>

### بوابة الشعر

- اسأل أولاً: «هل تسمح بإضافة أبيات شعرية؟»
- ١–٣ أبيات فقط.
- في الافتتاح/التطبيق/الخاتمة.
- تحقق من الشاعر والديوان.
- إن لم تتحقق: «يُنسب إلى...» أو احذف.

---

## 📚 المصادر والاعتماد

1. **«فن الخطابة»** — حسين بن محمد آل شامر — PDF على الألوكة:
   <https://www.alukah.net/books/files/book_14140/bookfile/faankhtabah.pdf>
2. **«الخطابة الإسلامية»** — عبد العاطي محمد شلبي — المكتب الجامعي الحديث، ٢٠٠٦ — نصّ المكتبة الشاملة (قابل للتصدير PDF):
   <https://shamela.ws/book/10779>
   وعارض PDF: <https://shamela.org/pdf/9f5c62c903d0a4d5479fa12a0be87512>
3. **«خطبة الجمعة في الكتاب والسنة»** — عبد الرحمن بن محمد الحمد — وزارة الشؤون الإسلامية السعودية — PDF:
   <https://d1.islamhouse.com/data/ar/ih_books/single/ar_Friday_sermon_in_the_book_and_sonh.pdf>
4. **«الفقه على المذاهب الأربعة»** — عبد الرحمن الجزيري — دار الكتب العلمية — أرشيف الإنترنت:
   <https://archive.org/details/waq78101>

> **حالة المصادر:** الكتب الأربعة متاحة على الإنترنت: ثلاثة منها بنسخ PDF مباشرة، والرابع («الخطابة الإسلامية») بنصّ كامل على المكتبة الشاملة قابل للتصدير PDF. وقد روجعت نسخها عند بناء المهارة، ولا تُضمَّن في المستودع.

> **إقرار بالفضل:** هذه المهارة صياغة تعليمية مستقلة لمبادئ هذه الكتب وأمثلتها، مع نقل اقتباسات وأمثلة بإسنادها إلى مؤلفيها. ولا يتضمّن المستودع نسخاً كاملة من الكتب، ولا يُغني عن الرجوع إلى الأصل.

---

## ⚠️ حدود المسؤولية

- المهارة **ليست فتوى**.
- الأحكام الفقهية تُعرض كما في المصادر، والفتوى للجهة المختصة.
- المستخدم مسؤول عن مراجعة النص النهائي مع عالمه/جهته.
- التحقق من المراجع **شرط**، لا خيار.
- لا تُستخدم المهارة للتحريض أو التكفير أو التجريح.

---

## 📜 الترخيص

هذه المهارة مفتوحة المصدر ومتاحة للاستخدام الشخصي والتجاري والبحثي لدعم الخطبة العربية الموثقة.
