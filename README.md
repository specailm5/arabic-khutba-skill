# مهارة الخطبة المنبرية
### (Arabic Khutba Skill — Fiqh + Craft + Verification)

<p align="center">
  <a href="https://github.com/specailm5/arabic-khutba-skill/blob/master/LICENSE"><img alt="License" src="https://img.shields.io/github/license/specailm5/arabic-khutba-skill?style=flat-square"></a>
  <a href="https://github.com/specailm5/arabic-khutba-skill/commits/master"><img alt="Last commit" src="https://img.shields.io/github/last-commit/specailm5/arabic-khutba-skill?style=flat-square"></a>
  <a href="https://specailm5.github.io/arabic-khutba-skill/"><img alt="Docs" src="https://img.shields.io/badge/docs-live-brightgreen?style=flat-square"></a>
  <img alt="Agent Skills" src="https://img.shields.io/badge/Agent%20Skills-compatible-5B21B6?style=flat-square">
</p>

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

## 🚀 التثبيت

```bash
npx skills add specailm5/arabic-khutba-skill -g -y
```

<details>
<summary>تثبيت يدوي، أو لبيئة واحدة فقط</summary>

**لبيئات محددة:**

```bash
npx skills add specailm5/arabic-khutba-skill -a claude-code -a codex
```

**Windows (PowerShell):**

```powershell
$src = "skills\arabic-khutba-skill"

New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills\arabic-khutba-skill"
Copy-Item -Recurse -Force "$src\*" "$env:USERPROFILE\.claude\skills\arabic-khutba-skill\"

New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills\arabic-khutba-skill"
Copy-Item -Recurse -Force "$src\*" "$env:USERPROFILE\.agents\skills\arabic-khutba-skill\"

New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.gemini\config\skills\arabic-khutba-skill"
Copy-Item -Recurse -Force "$src\*" "$env:USERPROFILE\.gemini\config\skills\arabic-khutba-skill\"
```

**macOS / Linux:**

```bash
src=skills/arabic-khutba-skill

mkdir -p ~/.claude/skills/arabic-khutba-skill
cp -r "$src/." ~/.claude/skills/arabic-khutba-skill/

mkdir -p ~/.agents/skills/arabic-khutba-skill
cp -r "$src/." ~/.agents/skills/arabic-khutba-skill/

mkdir -p ~/.gemini/config/skills/arabic-khutba-skill
cp -r "$src/." ~/.gemini/config/skills/arabic-khutba-skill/
```

**داخل مشروع واحد (VS Code):**

```powershell
New-Item -ItemType Directory -Force -Path ".agents\skills\arabic-khutba-skill"
Copy-Item -Recurse -Force "path\to\skills\arabic-khutba-skill\*" ".agents\skills\arabic-khutba-skill\"
```

**بدون بيئة برمجية:** انسخ محتوى [`skills/arabic-khutba-skill/SKILL.md`](skills/arabic-khutba-skill/SKILL.md) إلى التعليمات المخصصة أو System Prompt.

</details>

---

## ⚡ كيف تعمل؟

### الأسئلة الخمسة

<table dir="rtl" align="right">
<thead>
<tr>
<th align="right">السؤال</th>
<th align="right">لماذا؟</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>ما مذهبك/مذهب المسجد؟</strong></td>
<td>الأركان والشروط واللغة تختلف</td>
</tr>
<tr>
<td><strong>ما المناسبة؟</strong></td>
<td>لكل مناسبة عقدها</td>
</tr>
<tr>
<td><strong>من الجمهور؟</strong></td>
<td>المستوى والطول والأمثلة</td>
</tr>
<tr>
<td><strong>ما الموضوع والرسالة الواحدة؟</strong></td>
<td>الخطبة التي تحمل عشر رسائل لا تحمل رسالة</td>
</tr>
<tr>
<td><strong>هل تسمح بالشعر؟</strong></td>
<td>لا يُقحم بلا إذن، ولا يُنسب بلا تحقق</td>
</tr>
</tbody>
</table>
<br clear="all">

### الفقه: الجدول الجامع

<table dir="rtl" align="right">
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
<br clear="all">

### سجل المراجع

<table dir="rtl" align="right">
<thead>
<tr><th align="right">النص</th><th align="right">المصدر</th><th align="right">الرقم</th><th align="right">الحكم</th><th align="right">الحالة</th></tr>
</thead>
<tbody>
<tr><td>«إن طول صلاة الرجل وقصر خطبته...»</td><td>مسلم</td><td>٨٦٩</td><td>صحيح</td><td>متحقق</td></tr>
<tr><td>«من تخطى رقاب الناس... جسراً إلى جهنم»</td><td>الترمذي</td><td>—</td><td>ضعيف</td><td>محذوف</td></tr>
<tr><td>«أدِّ الأمانة إلى من ائتمنك...»</td><td>أبو داود ٣٥٣٤ / الترمذي ١٢٦٤</td><td>—</td><td>حسن غريب وفيه كلام</td><td>لا يُستخدم وحده</td></tr>
</tbody>
</table>
<br clear="all">

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

## 🤝 المساهمة

نرحب بالمساهمات التي تحسّن المادة أو التحرير أو التوثيق. اقرأ [CONTRIBUTING.md](CONTRIBUTING.md) قبل فتح طلب سحب، والتزم بـ[قواعد السلوك](CODE_OF_CONDUCT.md).


---

## 🛡️ الأمان

إن وجدت مشكلة أمنية، فلا تفتح قضية عامة؛ راجع [SECURITY.md](SECURITY.md).


---

## 📄 سجل التغييرات

راجع [CHANGELOG.md](CHANGELOG.md) لمعرفة ما أُضيف في كل إصدار.


---

## 📬 الدعم

للأسئلة والاقتراحات: [افتح قضية](https://github.com/specailm5/arabic-khutba-skill/issues).

---

## 📜 الترخيص

هذه المهارة مفتوحة المصدر ومتاحة للاستخدام الشخصي والتجاري والبحثي لدعم الخطبة العربية الموثقة.

