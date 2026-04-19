---
render_with_liquid: false
title: "HTML Style Guide, Character Entities, Symbols & Emojis"
nav_order: 29
---

# Lesson 29: HTML Style Guide, Character Entities, Symbols & Emojis

---

## Lesson Introduction

Imagine reading a book where every page uses a different font size, some
sentences are randomly CAPITALISED, and paragraphs jump all over the page with
no consistent spacing. Even if the words are correct, it feels messy and
unprofessional.

HTML code works the same way. Two developers can write HTML that produces
*identical* web pages — but one codebase is clean, consistent, and easy to
understand, while the other is a chaotic mess that no one else wants to work
with.

Beyond writing clean code, every HTML developer also needs to know how to
display characters that you cannot simply type on a keyboard — things like the
© copyright symbol, the € euro sign, the ™ trademark symbol, mathematical
operators like ∑ (sigma), Greek letters like Δ (delta), and even emojis like
😄 and 🚀 — all directly inside an HTML page.

This lesson covers four tightly related topics in one smooth progression:

1. **HTML Style Guide** — the rules and conventions for writing clean, readable,
   professional HTML
2. **HTML Character Entities** — how to display reserved and special characters
   using entity names and entity numbers
3. **HTML Symbols** — a rich world of special symbols including currencies,
   arrows, mathematics, and Greek letters
4. **HTML Emojis** — how emojis work as UTF-8 characters and how to add them
   to any web page

By the end of this lesson, you will write clean, professional code and be
able to place any character, symbol, or emoji on a web page with confidence.

---

## Prerequisite Concepts

### What is a Character Set?

A **character set** (or **charset**) is the system a computer uses to map
numbers to letters, symbols, and characters. Every character stored on a
computer is secretly just a number.

For example:
- The letter **A** = number **65**
- The letter **B** = number **66**
- The symbol **©** = number **169**
- The emoji **😄** = number **128516**

**UTF-8** (Unicode Transformation Format — 8-bit) is the standard character
set used on the web. It supports almost every character from every language on
Earth — English, Arabic, Chinese, Yoruba, Hindi, Greek — plus thousands of
symbols and emojis.

> 💡 **Why does this matter?** When you add `<meta charset="UTF-8">` to your
> HTML, you are telling the browser: "Use the UTF-8 system to decode this
> page's characters." Without it, special characters may appear garbled.

### What is an HTML Entity?

An **HTML entity** is a special code you write in HTML to display a character
that HTML would otherwise misinterpret, or that does not exist on a standard
keyboard.

There are two forms:
- **Entity name**: `&lt;` → displays `<`
- **Entity number**: `&#60;` → displays `<`

You will learn both in depth throughout this lesson.

---

## Part 1 — HTML Style Guide and Coding Conventions

### Why Does Coding Style Matter?

A style guide is a set of rules that make your HTML code consistent, clean,
and readable — even when many people work on the same project. Think of it
like grammar rules for a language: you *can* break them and still be
understood, but following them makes communication much smoother.

> 💡 **Real-world analogy:** A coding style guide is like the formatting rules
> in a professional report — consistent heading sizes, margins, fonts, and
> paragraph spacing. The content may be great, but inconsistent formatting
> makes it harder to read and looks unprofessional.

The HTML style guide recommendations below are the industry-accepted best
practices followed by professional developers worldwide.

---

### Rule 1 — Always Declare the Document Type

Every HTML file should begin with `<!DOCTYPE html>` on the very first line.
This tells the browser you are writing modern HTML5.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>My Page</title>
</head>
<body>
  <p>Content here.</p>
</body>
</html>
```

Without `<!DOCTYPE html>`, browsers enter a mode called **"Quirks Mode"**
where they try to guess what kind of document it is. This can cause layout
bugs and inconsistent rendering across different browsers.

---

### Rule 2 — Use Lowercase Element Names

HTML allows you to write tags in uppercase or lowercase. However, always use
**lowercase**. Lowercase is the professional standard, easier to read, and
faster to type.

```html
<!-- ✅ Good: -->
<body>
  <p>This is a paragraph.</p>
</body>

<!-- ❌ Bad: -->
<BODY>
  <P>This is a paragraph.</P>
</BODY>
```

**Why does this matter?** Mixing uppercase and lowercase looks messy.
Developers universally use lowercase, and some tools and systems are case
sensitive. Lowercase is simply the standard.

---

### Rule 3 — Always Close All HTML Elements

HTML does not *require* you to close every element — for example, a `<p>` tag
without a closing `</p>` will still work in many browsers. But it is strongly
recommended to always close all elements.

```html
<!-- ✅ Good: -->
<section>
  <p>This is a paragraph.</p>
  <p>This is another paragraph.</p>
</section>

<!-- ❌ Bad (missing closing tags): -->
<section>
  <p>This is a paragraph.
  <p>This is another paragraph.
</section>
```

**Why it matters:** Unclosed tags can cause unexpected layout behaviour,
especially in complex pages. Browsers try to guess where tags end, and they
don't always guess correctly.

---

### Rule 4 — Use Lowercase Attribute Names

Just like element names, attribute names should always be lowercase.

```html
<!-- ✅ Good: -->
<a href="https://www.example.com">Visit here</a>

<!-- ❌ Bad: -->
<a HREF="https://www.example.com">Visit here</a>
```

---

### Rule 5 — Always Quote Attribute Values

Attribute values should always be wrapped in double quotes, even when quotes
are technically optional. There are situations where missing quotes cause bugs
— especially when the value contains spaces.

```html
<!-- ✅ Good: -->
<table class="striped-table">

<!-- ❌ Bad (no quotes): -->
<table class=striped-table>

<!-- ⛔ Very Bad — breaks because value has a space: -->
<table class=table striped>
```

The third example above will fail completely because the browser reads
`class=table` and then is confused by the word `striped` floating alone
without an attribute name.

---

### Rule 6 — Always Specify `alt`, `width`, and `height` for Images

Every `<img>` element should always have three attributes: `alt`, `width`,
and `height`.

```html
<!-- ✅ Good: -->
<img src="photo.jpg" alt="A sunset over Lagos Lagoon" width="640" height="480">

<!-- ❌ Bad: -->
<img src="photo.jpg">
```

**Why each one matters:**
- `alt` — describes the image for screen readers (accessibility) and displays
  if the image fails to load
- `width` and `height` — tell the browser how much space to reserve before
  the image loads, preventing the page from "jumping" as images load

---

### Rule 7 — No Spaces Around Equal Signs in Attributes

Keep attribute assignments tight, with no spaces around the `=` sign.

```html
<!-- ✅ Good: -->
<link rel="stylesheet" href="styles.css">

<!-- ❌ Bad: -->
<link rel = "stylesheet" href = "styles.css">
```

Spaces around `=` are harder to read and look non-standard.

---

### Rule 8 — Avoid Very Long Code Lines

Very long lines of HTML are difficult to read — you have to scroll
horizontally in your editor. Break long lines onto multiple lines where it
makes sense.

```html
<!-- ✅ Good — broken into readable lines: -->
<meta
  name="description"
  content="A beginner-friendly guide to growing tomatoes at home in Lagos.">

<!-- ❌ Hard to read: -->
<meta name="description" content="A beginner-friendly guide to growing tomatoes at home in Lagos.">
```

---

### Rule 9 — Use Blank Lines and Indentation Sensibly

Use **two spaces** for indentation inside elements. Do NOT use the Tab key
for indentation (different editors render tabs differently, causing
inconsistency). Add blank lines to separate large logical blocks of code, but
not between every line.

```html
<!-- ✅ Good: -->
<body>

  <h1>Famous Cities</h1>

  <h2>Lagos</h2>
  <p>Lagos is the largest city in Nigeria and a major African metropolis.</p>

  <h2>Accra</h2>
  <p>Accra is the capital city of Ghana.</p>

</body>

<!-- ❌ Bad — cramped and unreadable: -->
<body>
<h1>Famous Cities</h1>
<h2>Lagos</h2><p>Lagos is the largest city in Nigeria and a major African metropolis.</p>
<h2>Accra</h2><p>Accra is the capital city of Ghana.</p>
</body>
```

**Good table indentation example:**

```html
<table>
  <tr>
    <th>City</th>
    <th>Country</th>
  </tr>
  <tr>
    <td>Lagos</td>
    <td>Nigeria</td>
  </tr>
</table>
```

**Good list indentation example:**

```html
<ul>
  <li>HTML</li>
  <li>CSS</li>
  <li>JavaScript</li>
</ul>
```

---

### Rule 10 — Never Skip the `<title>` Element

The `<title>` element is **required** in HTML. It defines the page title that
appears in the browser tab and is used by search engines.

```html
<title>HTML Style Guide and Best Practices</title>
```

Always make the title accurate and descriptive.

---

### Rule 11 — Never Omit `<html>`, `<head>`, and `<body>`

While technically a browser will render a page without these wrapper tags, you
should **always include them**. Omitting `<body>` can cause errors in older
browsers. Omitting `<html>` can crash XML or DOM-processing tools.

```html
<!-- ✅ Always write the full structure: -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My Page</title>
</head>
<body>
  <h1>Hello!</h1>
</body>
</html>
```

---

### Rule 12 — Add the `lang` Attribute to `<html>`

Always declare the language of your page by including the `lang` attribute
on the `<html>` tag. This helps search engines and screen readers understand
what language the page is in.

```html
<html lang="en">       <!-- English -->
<html lang="fr">       <!-- French -->
<html lang="yo">       <!-- Yoruba -->
<html lang="ar">       <!-- Arabic -->
<html lang="zh">       <!-- Chinese -->
```

---

### Rule 13 — Meta Data: Charset and Viewport First

The character encoding declaration and viewport setting should appear as the
very first items inside `<head>`, before anything else:

```html
<!DOCTYPE html>
<html lang="en-us">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Title</title>
</head>
```

---

### Rule 14 — Use Consistent Comment Style

Short comments go on one line:

```html
<!-- This is a short comment -->
```

Long comments span multiple lines with indentation:

```html
<!--
  This is a longer comment describing
  the purpose of the section below.
  It spans multiple lines for clarity.
-->
```

---

### Rule 15 — Use Lowercase Filenames

Some web servers (Linux/Apache) are **case-sensitive** about file names.
`photo.jpg` and `Photo.jpg` would be treated as different files. Other servers
(Windows/IIS) are case-insensitive.

To avoid your website breaking when moved between servers: **always use
lowercase filenames**.

```
✅ Good:   index.html,  style.css,  logo.png
❌ Bad:    Index.HTML,  Style.CSS,  Logo.PNG
```

---

### Rule 16 — Use Correct File Extensions

- HTML files: `.html` (`.htm` is allowed but `.html` is preferred)
- CSS files: `.css`
- JavaScript files: `.js`

There is no functional difference between `.htm` and `.html` — browsers
treat both identically.

---

### Rule 17 — Know About Default Filenames

When a browser visits a URL like `https://www.mysite.com/`, and no filename
is specified, the web server looks for a **default file**. Common default
names are `index.html`, `index.htm`, `default.html`. Always name your main
page `index.html` unless your server is configured differently.

---

### Rule 18 — JavaScript in HTML: Keep It Simple

When loading external JavaScript files, no `type` attribute is needed:

```html
<!-- ✅ Simple and correct: -->
<script src="myscript.js"></script>

<!-- No need for: -->
<script type="text/javascript" src="myscript.js"></script>
```

---

### Rule 19 — Case Sensitivity Matters for JavaScript

When HTML IDs and JavaScript work together, case matters. These two lines
target **different** elements:

```javascript
document.getElementById("Demo").innerHTML = "Hello";  // Targets id="Demo"
document.getElementById("demo").innerHTML = "Hello";  // Targets id="demo"
```

Always use consistent lowercase IDs in your HTML and match exactly in your
JavaScript.

---

### Quick Style Guide Reference

| Rule | Do This | Avoid This |
|---|---|---|
| Document type | `<!DOCTYPE html>` | No DOCTYPE |
| Element names | `<body>`, `<p>` | `<BODY>`, `<P>` |
| Attribute names | `href=`, `class=` | `HREF=`, `CLASS=` |
| Attribute values | `class="nav"` | `class=nav` |
| Closing tags | `<p>text</p>` | `<p>text` |
| Indentation | 2 spaces | Tab key |
| Image alt text | Always include | Omit |
| `lang` attribute | `<html lang="en">` | `<html>` |
| Filenames | `index.html` | `Index.HTML` |

---

## Part 2 — HTML Character Entities

### The Problem: Characters That Confuse HTML

Some characters have special meaning inside HTML. The most obvious example is
the **angle bracket** (`<`). When the browser sees `<`, it assumes an HTML
tag is starting. So what happens if you want to display the actual character
`<` as text on your page?

If you write this:

```html
<p>5 < 10</p>
```

The browser sees `< 10</p>` and gets confused, thinking `< 10</p>` might be
a tag. The text may display incorrectly or not at all.

The solution is **HTML character entities**.

---

### What is an HTML Character Entity?

A **character entity** is a code you write inside HTML to represent a
character. There are two formats:

**Entity name format:**
```
&entity_name;
```
Example: `&lt;` displays as `<`

**Entity number format:**
```
&#entity_number;
```
Example: `&#60;` displays as `<`

Both formats work identically. The entity name is easier to remember, while
the entity number is more universal (every character has a number, but not
every character has an entity name).

> ⚠️ **Important:** Entity names are **case-sensitive**. `&lt;` is correct.
> `&LT;` is NOT the same thing.

The general structure:
- Starts with an ampersand `&`
- Followed by the name or `#` and number
- Ends with a semicolon `;`

Think of it like a word surrounded by punctuation: `&name;`

---

### The Reserved Characters You Must Escape

These four characters have special meaning in HTML and **must always be
written as entities** when you want to display them as visible text:

| Character | What it does in HTML | Entity Name | Entity Number |
|---|---|---|---|
| `<` | Opens a tag | `&lt;` | `&#60;` |
| `>` | Closes a tag | `&gt;` | `&#62;` |
| `&` | Starts an entity | `&amp;` | `&#38;` |
| `"` | Starts/ends attribute value | `&quot;` | `&#34;` |

### Simple Example — Displaying Code in a Paragraph

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Entities Demo</title>
</head>
<body>
  <p>In HTML, a paragraph tag looks like this: &lt;p&gt;</p>
  <p>An anchor tag looks like this: &lt;a href="..."&gt;</p>
  <p>The price is 5 &amp; 10 naira.</p>
</body>
</html>
```

**Output displayed on the page:**
```
In HTML, a paragraph tag looks like this: <p>
An anchor tag looks like this: <a href="...">
The price is 5 & 10 naira.
```

Without entities, the browser would try to *execute* the `<p>` and `<a>` as
actual tags instead of displaying them as text.

---

### The Non-Breaking Space: `&nbsp;`

One of the most commonly used entities is the **non-breaking space**: `&nbsp;`

A regular space in HTML can cause the browser to wrap text to a new line if
the line gets too long. A non-breaking space prevents that — the two words
on either side of it will always stay together on the same line.

**When is this useful?**
- Phone numbers: `+234&nbsp;080&nbsp;1234&nbsp;5678`
- Units: `10&nbsp;km/h`, `35&nbsp;°C`, `5&nbsp;kg`
- Legal sections: `§&nbsp;10`
- Names: `Dr.&nbsp;Eze`

```html
<p>The temperature is 35&nbsp;°C outside today.</p>
<p>Contact us at §&nbsp;10 of the agreement.</p>
```

**Output:**
```
The temperature is 35 °C outside today.
Contact us at § 10 of the agreement.
```

The space between `35` and `°C` will never break onto a new line.

**Second use of `&nbsp;` — adding multiple spaces:**

HTML normally collapses multiple spaces into just one. To add extra visible
spaces, use multiple `&nbsp;`:

```html
<p>Name:&nbsp;&nbsp;&nbsp;Amara</p>
<p>Age:&nbsp;&nbsp;&nbsp;&nbsp;25</p>
```

**Output:**
```
Name:   Amara
Age:    25
```

---

### The Non-Breaking Hyphen: `&#8209;`

Similarly, the **non-breaking hyphen** (`&#8209;`) is a hyphen that refuses
to break onto a new line. Useful for hyphenated names or compound words where
splitting across lines would be confusing.

```html
<p>Dr.&nbsp;Akin&#8209;Obi is the lead researcher.</p>
```

The hyphen in `Akin-Obi` will now never be the point at which a line breaks.

---

### Complete Table of Useful HTML Entities

| Symbol Displayed | Description | Entity Name | Entity Number |
|---|---|---|---|
| (space) | Non-breaking space | `&nbsp;` | `&#160;` |
| `<` | Less than | `&lt;` | `&#60;` |
| `>` | Greater than | `&gt;` | `&#62;` |
| `&` | Ampersand | `&amp;` | `&#38;` |
| `"` | Double quotation mark | `&quot;` | `&#34;` |
| `'` | Single quotation mark | `&apos;` | `&#39;` |
| `¢` | Cent sign | `&cent;` | `&#162;` |
| `£` | Pound sign | `&pound;` | `&#163;` |
| `¥` | Yen sign | `&yen;` | `&#165;` |
| `€` | Euro sign | `&euro;` | `&#8364;` |
| `©` | Copyright | `&copy;` | `&#169;` |
| `®` | Registered trademark | `&reg;` | `&#174;` |
| `™` | Trademark | `&trade;` | `&#8482;` |

---

### Practical Example — A Product Page with Entities

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Bright Smile Toothpaste</title>
</head>
<body>
  <h1>Bright Smile&trade; Toothpaste</h1>
  <p>Price: &euro;3.99 &nbsp;|&nbsp; &pound;3.49 &nbsp;|&nbsp; &#8358;2,500</p>
  <p>Effective for teeth &lt; 30 years old &amp; sensitive gums.</p>
  <p>&copy; 2025 BrightCare Ltd. &reg;</p>
</body>
</html>
```

**Output on the page:**
```
Bright Smile™ Toothpaste

Price: €3.99  |  £3.49  |  ₦2,500

Effective for teeth < 30 years old & sensitive gums.

© 2025 BrightCare Ltd. ®
```

---

### Diacritical Marks (Accent Marks)

A **diacritical mark** is a small symbol added to a letter to change its
pronunciation. Examples: `à`, `é`, `â`, `ã`. These are created by combining
a base letter with a mark entity number.

The pattern is: write the letter, then immediately write the mark's entity
number (no space between them).

| Mark | Letter | Code | Result |
|---|---|---|---|
| Grave accent (`) | a | `a&#768;` | à |
| Acute accent (´) | a | `a&#769;` | á |
| Circumflex (^) | a | `a&#770;` | â |
| Tilde (~) | a | `a&#771;` | ã |
| Grave accent (`) | O | `O&#768;` | Ò |
| Acute accent (´) | O | `O&#769;` | Ó |
| Circumflex (^) | O | `O&#770;` | Ô |
| Tilde (~) | O | `O&#771;` | Õ |

```html
<p>Caf&eacute;</p>     <!-- Shows: Café -->
<p>na&iuml;ve</p>      <!-- Shows: naïve -->
<p>O&#769;Brien</p>    <!-- Shows: Óbrién (Irish name with accent) -->
```

> 💡 Many accented European letters also have their own named entities:
> `&eacute;` = é, `&agrave;` = à, `&ntilde;` = ñ, `&uuml;` = ü

---

## Part 3 — HTML Symbols

### What are HTML Symbols?

Beyond the standard entities for reserved characters, HTML gives you access
to hundreds of **special symbols** that do not exist on a standard keyboard:
currency signs, arrows, mathematical operators, playing card suits, Greek
letters, and much more.

All symbols can be displayed using either their **entity name** (if one exists)
or their **entity number** — in decimal (`&#NNNN;`) or hexadecimal
(`&#xHHHH;`).

---

### The Three Ways to Display Any Symbol

All three methods produce the same result. Using the Euro sign as an example:

```html
<p>I will display &euro;</p>      <!-- Entity name -->
<p>I will display &#8364;</p>     <!-- Decimal entity number -->
<p>I will display &#x20AC;</p>    <!-- Hexadecimal entity number -->
```

**All three display:** €

---

### Common Symbol Entities Table

| Symbol | Decimal | Entity Name | Description |
|---|---|---|---|
| © | `&#169;` | `&copy;` | Copyright |
| ® | `&#174;` | `&reg;` | Registered trademark |
| ™ | `&#8482;` | `&trade;` | Trademark |
| € | `&#8364;` | `&euro;` | Euro sign |
| ← | `&#8592;` | `&larr;` | Left arrow |
| ↑ | `&#8593;` | `&uarr;` | Up arrow |
| → | `&#8594;` | `&rarr;` | Right arrow |
| ↓ | `&#8595;` | `&darr;` | Down arrow |
| ♠ | `&#9824;` | `&spades;` | Spade (card suit) |
| ♣ | `&#9827;` | `&clubs;` | Club (card suit) |
| ♥ | `&#9829;` | `&hearts;` | Heart (card suit) |
| ♦ | `&#9830;` | `&diams;` | Diamond (card suit) |

### Simple Example — Using Symbol Entities

```html
<p>All prices are in &euro; (Euros).</p>
<p>Navigate: &larr; Back &nbsp; | &nbsp; Forward &rarr;</p>
<p>Card suits: &spades; &clubs; &hearts; &diams;</p>
<p>This product is &copy; 2025 and &trade; registered.</p>
```

**Output:**
```
All prices are in € (Euros).
Navigate: ← Back  |  Forward →
Card suits: ♠ ♣ ♥ ♦
This product is © 2025 and ™ registered.
```

---

### Mathematical Symbol Entities

HTML supports a rich set of mathematical symbols — useful for science websites,
educational content, data analysis pages, and engineering documentation.

| Symbol | Decimal | Entity Name | Description |
|---|---|---|---|
| ∀ | `&#8704;` | `&forall;` | For all |
| ∂ | `&#8706;` | `&part;` | Partial differential |
| ∃ | `&#8707;` | `&exist;` | There exists |
| ∅ | `&#8709;` | `&empty;` | Empty set |
| ∇ | `&#8711;` | `&nabla;` | Nabla (del operator) |
| ∈ | `&#8712;` | `&isin;` | Element of |
| ∉ | `&#8713;` | `&notin;` | Not an element of |
| ∋ | `&#8715;` | `&ni;` | Contains as member |
| ∏ | `&#8719;` | `&prod;` | Product (capital pi) |
| ∑ | `&#8721;` | `&sum;` | Summation (sigma) |

### Example — A Simple Maths Reference Page

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Math Symbols</title>
</head>
<body>
  <h2>Common Math Symbols</h2>
  <p>Summation: &sum;</p>
  <p>For all values: &forall;</p>
  <p>There exists: &exist;</p>
  <p>Empty set: &empty;</p>
  <p>Is an element of: &isin;</p>
  <p>Is NOT an element of: &notin;</p>
</body>
</html>
```

**Output:**
```
Summation: ∑
For all values: ∀
There exists: ∃
Empty set: ∅
Is an element of: ∈
Is NOT an element of: ∉
```

> 💡 **Real-world use:** Science education sites, engineering textbooks
> converted to HTML, academic research portals, physics and chemistry
> reference pages.

---

### Greek Letter Entities

Greek letters are widely used in mathematics (π, Σ), physics (Ω, λ), science
(Δ, α, β), and statistics (μ, σ). HTML provides entity names for all of them.

| Symbol | Decimal | Entity Name | Description |
|---|---|---|---|
| Α | `&#913;` | `&Alpha;` | Greek capital Alpha |
| Β | `&#914;` | `&Beta;` | Greek capital Beta |
| Γ | `&#915;` | `&Gamma;` | Greek capital Gamma |
| Δ | `&#916;` | `&Delta;` | Greek capital Delta |
| Ε | `&#917;` | `&Epsilon;` | Greek capital Epsilon |
| Ζ | `&#918;` | `&Zeta;` | Greek capital Zeta |
| α | `&#945;` | `&alpha;` | Greek small alpha |
| β | `&#946;` | `&beta;` | Greek small beta |
| γ | `&#947;` | `&gamma;` | Greek small gamma |
| δ | `&#948;` | `&delta;` | Greek small delta |
| π | `&#960;` | `&pi;` | Greek small pi |
| σ | `&#963;` | `&sigma;` | Greek small sigma |
| μ | `&#956;` | `&mu;` | Greek small mu |
| ω | `&#969;` | `&omega;` | Greek small omega |
| Ω | `&#937;` | `&Omega;` | Greek capital Omega |
| Σ | `&#931;` | `&Sigma;` | Greek capital Sigma |

### Example — A Physics Formula Page

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Physics Formulas</title>
</head>
<body>
  <h2>Key Physics Constants</h2>
  <p>Pi (&pi;) = 3.14159...</p>
  <p>Ohm (&Omega;) is the unit of resistance.</p>
  <p>Delta (&Delta;) means "change in" a value.</p>
  <p>Sigma (&sigma;) represents standard deviation in statistics.</p>
  <p>Mu (&mu;) represents the mean (average).</p>
</body>
</html>
```

**Output:**
```
Pi (π) = 3.14159...
Ohm (Ω) is the unit of resistance.
Delta (Δ) means "change in" a value.
Sigma (σ) represents standard deviation in statistics.
Mu (μ) represents the mean (average).
```

---

### More Symbol Categories in HTML

HTML (via UTF-8) provides symbols in many more categories. Here is a preview
of what's available:

- **Currency symbols:** € £ ¥ ¢ ₿ ₽ (Bitcoin, Ruble, etc.)
- **Arrows:** ← ↑ → ↓ ⇐ ⇑ ⇒ ⇓ (and dozens more)
- **Weather symbols:** ☀ ☁ ☂ ☃ ★ ☆
- **Playing card suits:** ♠ ♣ ♥ ♦
- **Chess pieces:** ♔ ♕ ♘ ♖
- **Musical notes:** ♩ ♪ ♫ ♬
- **Geometric shapes:** ▲ △ ▣ ▧ ◐
- **Recycling/peace:** ♲ ♻ ☮ ☯
- **Gender/planet symbols:** ♂ ♀ ☿ ♃

All of these can be used in HTML using their entity numbers.

---

## Part 4 — HTML Emojis

### What Are Emojis? They Are NOT Images!

This surprises many beginners: **emojis are not images**. They are
**characters** — letters from the UTF-8 character set, just like A, B, C.
This means emojis behave exactly like text:

- They can be **sized** with CSS `font-size`
- They can be **coloured** with CSS (in some cases)
- They can be **copied and pasted** as text
- They can be placed inside any HTML element
- They work everywhere that text works

```
😄 = UTF-8 character number 128516
😍 = UTF-8 character number 128525
💗 = UTF-8 character number 128151
```

---

### How to Display an Emoji Using an Entity Number

Since emojis are just UTF-8 characters with very high numbers, you display
them exactly like any other character entity: using `&#` followed by the
number, followed by `;`.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
</head>
<body>
  <p>&#128512;</p>
</body>
</html>
```

**Output:** 😀

> ⚠️ **Critical:** You MUST have `<meta charset="UTF-8">` in your `<head>` for
> emojis to display correctly. Without it, the emoji will appear as a garbled
> string of characters.

---

### The Connection Between UTF-8 and Emojis

Let us first understand with regular letters to build the concept:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
</head>
<body>
  <p>I will display A B C</p>
  <p>I will display &#65; &#66; &#67;</p>
</body>
</html>
```

**Both lines display:** `A B C`

Because `A = 65`, `B = 66`, `C = 67` in UTF-8. Now apply the same logic to
emojis:

```html
<p>&#128512; &#128516; &#128525; &#128151;</p>
```

**Displays:** 😀 😄 😍 💗

The browser reads each `&#NNNNNN;`, looks up that UTF-8 number, and renders
the corresponding character — which happens to look like a colourful picture.

---

### Sizing Emojis with CSS

Because emojis are characters, you can resize them using the `font-size` CSS
property, just like text:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Sized Emojis</title>
</head>
<body>

  <p style="font-size: 14px;">Small emojis: &#128512; &#128516;</p>
  <p style="font-size: 32px;">Medium emojis: &#128512; &#128516;</p>
  <p style="font-size: 64px;">Large emojis: &#128512; &#128516;</p>
  <p style="font-size: 100px;">Huge emojis: &#128512; &#128516;</p>

</body>
</html>
```

**Visual output:** Each line shows the same two emojis at progressively larger
sizes — from small inline text size all the way to giant display-size.

---

### Emoji Entity Number Reference Table

| Emoji | Entity Number | Description |
|---|---|---|
| 😀 | `&#128512;` | Grinning face |
| 😁 | `&#128513;` | Grinning with smiling eyes |
| 😂 | `&#128514;` | Face with tears of joy |
| 😃 | `&#128515;` | Smiley face |
| 😄 | `&#128516;` | Smiling face with open mouth |
| 😅 | `&#128517;` | Smiling face with sweat |
| 😍 | `&#128525;` | Heart eyes |
| 💗 | `&#128151;` | Pink heart |
| 🗻 | `&#128507;` | Mount Fuji |
| 🗽 | `&#128509;` | Statue of Liberty |

---

### Emoji Categories Available in HTML

The UTF-8 character set includes emojis covering every area of modern life:

**Smileys and emotions:** 😀 😂 😊 😎 😜
**Hand gestures:** ✌ ✊ ☝ ✋ 👌
**People:** 👮 🧕 👦 💏 🤴
**Office & work:** 📈 💻 📌 📆 📒
**Places & landmarks:** ⛺ 🌋 🗽 🗿 🏢
**Transport:** 🚈 🚗 🚢 🚌 🚀
**Animals:** 🐴 🐕 🐘 🐻 🐞
**Food & drink:** ☕ 🌭 🍞 🍩 🍣
**Plants:** 🌴 🌳 🌼 🍁 🥑
**Fruits:** 🍇 🍊 🍏 🥝 🥥
**Sports:** ⚽ 🏆 🤿 🏋 ⛳
**Weather:** ⛅ ☔ 🌈 🌂 ⛄
**Celebration:** 🎁 🎃 🎈 🎓 🎂
**Symbols:** 💡 💰 🔐 🔞 🔔

---

## Guided Practice Exercises

### ✅ Exercise 1 — Clean Up Messy HTML Code

**Objective:** Apply the HTML Style Guide rules to fix a messy HTML file.

**The broken code (contains 8 style violations):**

```html
<!DOCTYPE HTML>
<HTML LANG="EN">
<HEAD>
<TITLE>MY WEBSITE</TITLE>
</HEAD>
<BODY>
<H1>Welcome</H1>
<P>This is a page about Nigeria.
<P>Lagos is the biggest city.
<img SRC=lagos.jpg>
</BODY>
</HTML>
```

**Your task:** Identify and fix all 8 violations.

**Violations to find:**
1. `DOCTYPE HTML` — should be `DOCTYPE html` (lowercase)
2. `<HTML LANG="EN">` — should be `<html lang="en">` (lowercase)
3. `<HEAD>`, `<TITLE>`, `<BODY>`, `<H1>`, `<P>`, `<IMG>` — all uppercase
4. `<P>This is a page...` — no closing `</p>` tag
5. `<P>Lagos is the biggest city.` — no closing `</p>` tag
6. `SRC=lagos.jpg` — attribute name uppercase, value not quoted
7. No `<meta charset="UTF-8">`
8. No `alt`, `width`, or `height` on the image

**Corrected version:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Website</title>
</head>
<body>
  <h1>Welcome</h1>
  <p>This is a page about Nigeria.</p>
  <p>Lagos is the biggest city.</p>
  <img src="lagos.jpg" alt="Aerial view of Lagos skyline" width="640" height="480">
</body>
</html>
```

**Self-check:** Can you find any remaining violations? (There should be none.)

---

### ✅ Exercise 2 — Using Reserved Character Entities

**Objective:** Write a page that displays HTML tag examples as text content.

**Scenario:** You are writing an HTML tutorial page and need to show code
examples *as visible text* rather than having the browser execute them.

**Your task:** Create a paragraph that displays this exact text on screen:

```
An HTML link looks like: <a href="url">Link text</a>
An image tag looks like: <img src="photo.jpg" alt="description">
Use & to join things together.
```

**Solution:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>HTML Tutorial Page</title>
</head>
<body>
  <p>An HTML link looks like:
    &lt;a href="url"&gt;Link text&lt;/a&gt;</p>
  <p>An image tag looks like:
    &lt;img src="photo.jpg" alt="description"&gt;</p>
  <p>Use &amp; to join things together.</p>
</body>
</html>
```

**Expected output:**
```
An HTML link looks like: <a href="url">Link text</a>
An image tag looks like: <img src="photo.jpg" alt="description">
Use & to join things together.
```

**Self-check:** What happens if you remove the `&lt;` and write `<a` instead?
(Answer: The browser tries to create an actual link instead of showing the text.)

---

### ✅ Exercise 3 — Building a Price List with Currency Entities

**Objective:** Use currency entities to build a product pricing table.

**Scenario:** You run an online store and need a clean pricing table showing
prices in multiple currencies.

**Your task:** Build this output:

```
Product Price List
==================
Item            Price
Laptop          €850 / £730 / ¥95,000
Coffee Mug      €12 / £10.50 / ¥1,400
Notebook        €5.99 / £4.99 / ¥650
© 2025 ShopEasy™ — All prices include VAT.
```

**Solution:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Price List – ShopEasy</title>
</head>
<body>
  <h2>Product Price List</h2>
  <table>
    <tr>
      <th>Item</th>
      <th>Price</th>
    </tr>
    <tr>
      <td>Laptop</td>
      <td>&euro;850 / &pound;730 / &yen;95,000</td>
    </tr>
    <tr>
      <td>Coffee Mug</td>
      <td>&euro;12 / &pound;10.50 / &yen;1,400</td>
    </tr>
    <tr>
      <td>Notebook</td>
      <td>&euro;5.99 / &pound;4.99 / &yen;650</td>
    </tr>
  </table>
  <p>&copy; 2025 ShopEasy&trade; &mdash; All prices include VAT.</p>
</body>
</html>
```

> 💡 `&mdash;` is the entity for an em-dash (—), the long dash used in
> formal writing. Its number is `&#8212;`.

---

### ✅ Exercise 4 — A Science Page with Greek Letters and Math Symbols

**Objective:** Use Greek letter and math symbol entities in a real content
context.

**Scenario:** You are building a physics reference website for students.

**Your task:** Create a page with these formulas and terms displayed correctly:

```
Area of a circle: A = π × r²
Summation formula: ∑ (sigma)
Standard deviation: σ (sigma lowercase)
Change in temperature: ΔT
Ohm's Law: V = I × Ω
Angular velocity: ω (omega)
```

**Solution:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Physics Reference – Key Formulas</title>
</head>
<body>
  <h2>Key Physics &amp; Maths Symbols</h2>
  <p>Area of a circle: A = &pi; &times; r&sup2;</p>
  <p>Summation formula: &sum; (sigma)</p>
  <p>Standard deviation: &sigma; (sigma lowercase)</p>
  <p>Change in temperature: &Delta;T</p>
  <p>Ohm&apos;s Law: V = I &times; &Omega;</p>
  <p>Angular velocity: &omega; (omega)</p>
</body>
</html>
```

**Output:**
```
Area of a circle: A = π × r²
Summation formula: ∑ (sigma)
Standard deviation: σ (sigma lowercase)
Change in temperature: ΔT
Ohm's Law: V = I × Ω
Angular velocity: ω (omega)
```

> 💡 Bonus entities used here:
> - `&times;` = × (multiplication sign, `&#215;`)
> - `&sup2;` = ² (superscript 2, `&#178;`)
> - `&apos;` = ' (apostrophe, `&#39;`)

---

### ✅ Exercise 5 — Emoji Showcase Page

**Objective:** Create a fun page using emoji entity numbers with different sizes.

**Scenario:** You are building a school project submission page and want to
add fun visual elements using emojis without images.

**Your task:** Create a page that shows emojis in three sizes with labels.

**Solution:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Emoji Showcase – School Project</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; }
    .small { font-size: 20px; }
    .medium { font-size: 48px; }
    .large { font-size: 96px; }
    h2 { color: #333; }
  </style>
</head>
<body>

  <h2>How I Feel About This Project</h2>

  <p class="small">
    Small: &#128512; &#128516; &#128525; &#128151;
  </p>

  <p class="medium">
    Medium: &#128512; &#128516; &#128525; &#128151;
  </p>

  <p class="large">
    Large: &#128512; &#128516;
  </p>

  <h2>Subjects I Love</h2>
  <p style="font-size: 40px;">
    Maths &#128203; &nbsp;
    Science &#128300; &nbsp;
    Sports &#9917; &nbsp;
    Music &#127925;
  </p>

</body>
</html>
```

**Visual output:**
- Three rows of the same smiley emojis, each at a progressively larger font size
- A second section showing different topic emojis at 40px

---

## Mini Project: A Complete "About Us" Page Using Style Guide, Entities & Emojis

### Project Description

You will build a complete, professionally written "About Us" page for a
fictional business called **NairaTrack Finance**, applying every concept from
this lesson:

- Correct HTML style guide conventions throughout
- Character entities for reserved and special characters
- Currency, trademark, and copyright symbols
- Mathematical and Greek symbols (relevant to finance)
- Emojis used tastefully to add personality

---

### Stage 1 — Base Structure with Style Guide Applied

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description"
    content="NairaTrack Finance helps you track spending in ₦, &euro;, &pound;, and &dollar;.">
  <meta name="author" content="Adaeze Okonkwo">
  <title>About Us – NairaTrack Finance &#128200;</title>
</head>
<body>
  <!-- Content added in next stages -->
</body>
</html>
```

**Milestone:** The browser tab shows: `About Us – NairaTrack Finance 📈`

---

### Stage 2 — Adding the Hero Section

```html
<body>

  <h1>NairaTrack Finance &trade;</h1>
  <p>Empowering Nigerians to manage their money smarter. &#128200; &#128176;</p>

  <h2>What We Do</h2>
  <p>
    NairaTrack helps you track all your expenses across
    multiple currencies: &dollar;, &euro;, &pound;, &yen;, and &#8358;.
    We analyse your spending patterns using advanced &sigma; (standard deviation)
    and &Delta; (delta) change calculations to show your financial trends.
  </p>

</body>
```

**Milestone output on page:**
```
NairaTrack Finance ™

Empowering Nigerians to manage their money smarter. 📈 💰

What We Do
NairaTrack helps you track all your expenses across multiple currencies:
$, €, £, ¥, and ₦. We analyse your spending patterns using advanced
σ (standard deviation) and Δ (delta) change calculations to show
your financial trends.
```

---

### Stage 3 — Pricing Table with Currency and Entity Symbols

```html
  <h2>Our Plans &amp; Pricing</h2>
  <table>
    <tr>
      <th>Plan</th>
      <th>Price / Month</th>
      <th>Features</th>
    </tr>
    <tr>
      <td>Starter &#127775;</td>
      <td>&euro;0 &nbsp;/&nbsp; &pound;0 &nbsp;/&nbsp; &#8358;0</td>
      <td>Track &lt; 50 transactions</td>
    </tr>
    <tr>
      <td>Pro &#128640;</td>
      <td>&euro;9.99 &nbsp;/&nbsp; &pound;8.49 &nbsp;/&nbsp; &#8358;7,500</td>
      <td>Unlimited transactions &amp; &Delta;analysis</td>
    </tr>
    <tr>
      <td>Enterprise &#127919;</td>
      <td>&euro;49 &nbsp;/&nbsp; &pound;42 &nbsp;/&nbsp; &#8358;37,000</td>
      <td>Full &sum; reporting &amp; team access</td>
    </tr>
  </table>
```

**Milestone output (pricing table):**
```
Plan        | Price / Month                  | Features
Starter ⭐  | €0 / £0 / ₦0                  | Track < 50 transactions
Pro 🚀      | €9.99 / £8.49 / ₦7,500        | Unlimited transactions & Δanalysis
Enterprise 🎯 | €49 / £42 / ₦37,000         | Full ∑ reporting & team access
```

---

### Stage 4 — Footer with Copyright and Legal Entities

```html
  <hr>
  <footer>
    <p>
      &copy; 2025 NairaTrack Finance Ltd. &reg;
      &nbsp;|&nbsp;
      All trademarks are property of NairaTrack&trade;
      &nbsp;|&nbsp;
      Prices shown &lt; VAT may apply in some regions.
    </p>
    <p>
      Our team: &#128101; &nbsp; Based in Lagos &#127475;&#127468;
      &nbsp; Working globally &#127758;
    </p>
  </footer>
```

**Footer output:**
```
© 2025 NairaTrack Finance Ltd. ®  |  All trademarks are property of NairaTrack™  |  Prices shown < VAT may apply in some regions.
Our team: 👥   Based in Lagos 🇳🇬   Working globally 🌎
```

> 💡 `&#127475;&#127468;` is the flag of Nigeria (🇳🇬) — country flag emojis
> are created by combining two "Regional Indicator" letter symbols. N = 127475,
> G = 127468.

---

### Stage 5 — Final Complete File

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description"
    content="NairaTrack Finance: Track spending in multiple currencies.">
  <meta name="author" content="Adaeze Okonkwo">
  <title>About Us – NairaTrack Finance &#128200;</title>
  <style>
    body {
      font-family: 'Segoe UI', Arial, sans-serif;
      max-width: 800px;
      margin: 0 auto;
      padding: 24px;
      color: #222;
    }
    h1 { color: #006600; }
    h2 { color: #004400; }
    table {
      width: 100%;
      border-collapse: collapse;
      margin: 16px 0;
    }
    th, td {
      border: 1px solid #ccc;
      padding: 10px 14px;
      text-align: left;
    }
    th { background-color: #e8f5e9; }
    footer { margin-top: 40px; color: #666; font-size: 14px; }
    hr { border: none; border-top: 1px solid #ddd; margin: 32px 0; }
  </style>
</head>
<body>

  <h1>NairaTrack Finance &trade;</h1>
  <p>Empowering Nigerians to manage their money smarter. &#128200; &#128176;</p>

  <h2>What We Do</h2>
  <p>
    NairaTrack helps you track all your expenses across multiple currencies:
    &dollar;, &euro;, &pound;, &yen;, and &#8358;. We analyse your spending
    patterns using advanced &sigma; (standard deviation) and &Delta; (delta)
    change calculations to show your financial trends.
  </p>

  <h2>Our Plans &amp; Pricing</h2>
  <table>
    <tr>
      <th>Plan</th>
      <th>Price / Month</th>
      <th>Features</th>
    </tr>
    <tr>
      <td>Starter &#127775;</td>
      <td>&euro;0 / &pound;0 / &#8358;0</td>
      <td>Track &lt; 50 transactions</td>
    </tr>
    <tr>
      <td>Pro &#128640;</td>
      <td>&euro;9.99 / &pound;8.49 / &#8358;7,500</td>
      <td>Unlimited transactions &amp; &Delta; analysis</td>
    </tr>
    <tr>
      <td>Enterprise &#127919;</td>
      <td>&euro;49 / &pound;42 / &#8358;37,000</td>
      <td>Full &sum; reporting &amp; team access</td>
    </tr>
  </table>

  <hr>

  <footer>
    <p>
      &copy; 2025 NairaTrack Finance Ltd. &reg;
      &nbsp;|&nbsp;
      All trademarks are property of NairaTrack&trade;
      &nbsp;|&nbsp;
      Prices shown &lt; VAT may apply.
    </p>
    <p>
      Our team: &#128101; &nbsp; Based in Lagos &#127475;&#127468;
      &nbsp; Working globally &#127758;
    </p>
  </footer>

</body>
</html>
```

---

### Project Reflection Questions

1. Why does the `<table>` cell `Track &lt; 50 transactions` use `&lt;`
   instead of just writing `<`? What would happen without the entity?
2. Why must `<meta charset="UTF-8">` be present for the emojis to show
   correctly?
3. The footer uses `&nbsp;` between sections. What does that do?
4. What is the difference between `&copy;`, `&reg;`, and `&trade;`? When
   would a real business use each one?
5. Why should you always use lowercase element names and attribute names,
   according to the HTML Style Guide?

---

## Common Beginner Mistakes

### Mistake 1 — Forgetting the Semicolon at the End of an Entity

❌ **Wrong (semicolon missing):**
```html
<p>Copyright &copy 2025 My Company</p>
```

✅ **Correct:**
```html
<p>Copyright &copy; 2025 My Company</p>
```

**Output difference:**
- Wrong: `Copyright &copy 2025 My Company` (literally shows `&copy`)
- Correct: `Copyright © 2025 My Company`

The semicolon `;` is **mandatory**. Without it, the browser does not recognise
the entity and displays it as raw text.

---

### Mistake 2 — Using Wrong Case in Entity Names

❌ **Wrong (wrong case):**
```html
<p>&COPY; 2025</p>
<p>&LT;p&GT;</p>
```

✅ **Correct:**
```html
<p>&copy; 2025</p>
<p>&lt;p&gt;</p>
```

Entity names are **case-sensitive**. `&copy;` works. `&COPY;` does not.

---

### Mistake 3 — Using `<` Directly in Text Content

❌ **Wrong (will confuse the browser):**
```html
<p>If x < 10 and y > 5, the condition is true.</p>
```

✅ **Correct:**
```html
<p>If x &lt; 10 and y &gt; 5, the condition is true.</p>
```

**Output:** `If x < 10 and y > 5, the condition is true.`

The browser sees raw `<` as the beginning of a tag. Always use `&lt;` for
the less-than sign in text content, and `&gt;` for the greater-than sign.

---

### Mistake 4 — Writing `&` Directly in Text or Attributes

❌ **Wrong:**
```html
<p>Bread & Butter Café</p>
<a href="page.html?a=1&b=2">Link</a>
```

✅ **Correct:**
```html
<p>Bread &amp; Butter Café</p>
<a href="page.html?a=1&amp;b=2">Link</a>
```

The raw `&` has special meaning in HTML as the start of an entity. To display
the `&` character itself, always write `&amp;`. This applies inside URLs
(href attributes) too.

---

### Mistake 5 — Forgetting `<meta charset="UTF-8">` Before Using Emojis or Special Characters

❌ **Wrong (emojis may not display):**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>My Page</title>
</head>
<body>
  <p>&#128512;</p>
</body>
```

✅ **Correct:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My Page</title>
</head>
<body>
  <p>&#128512;</p>
</body>
```

Without `<meta charset="UTF-8">`, the browser may not know how to decode
large character numbers (like those used for emojis) and may show garbled
symbols or question marks instead.

---

### Mistake 6 — Using Uppercase Element or Attribute Names

❌ **Wrong:**
```html
<P CLASS="intro">Hello</P>
<IMG SRC="photo.jpg" ALT="A photo">
```

✅ **Correct:**
```html
<p class="intro">Hello</p>
<img src="photo.jpg" alt="A photo">
```

Always lowercase. Always.

---

### Mistake 7 — Not Quoting Attribute Values

❌ **Wrong:**
```html
<img src=photo.jpg alt=Lagos skyline>
```

✅ **Correct:**
```html
<img src="photo.jpg" alt="Lagos skyline">
```

The unquoted version with spaces fails entirely because the browser reads
`alt=Lagos` as one attribute and then sees `skyline` as a stray word with
no attribute to attach to.

---

### Mistake 8 — Trying to Resize an Emoji with `width` and `height` (Like an Image)

❌ **Wrong (emojis are not images):**
```html
<img src="😀" width="50" height="50">  <!-- This doesn't work -->
```

✅ **Correct (use font-size since emojis are characters):**
```html
<p style="font-size: 50px;">&#128512;</p>
```

Emojis are characters, not images. Use CSS `font-size` to control their size.

---

## Completion Checklist

Check off each item when you feel confident about it:

- [ ] I know why HTML coding style matters and can name at least 5 style rules
- [ ] I always use lowercase element names and attribute names
- [ ] I always close all HTML elements
- [ ] I always quote attribute values
- [ ] I always include `alt`, `width`, and `height` for images
- [ ] I always include `<meta charset="UTF-8">` in my pages
- [ ] I understand what an HTML character entity is and why it exists
- [ ] I can write the entities for `<`, `>`, `&`, `"`, and `'` from memory
- [ ] I know what `&nbsp;` does and when to use it
- [ ] I can display currency symbols using entities (`&euro;`, `&pound;`, `&yen;`)
- [ ] I can display copyright (`&copy;`), trademark (`&trade;`), and registered (`&reg;`)
- [ ] I know how to use Greek letter entities like `&pi;`, `&sigma;`, `&Delta;`
- [ ] I know how to use mathematical entities like `&sum;`, `&exist;`, `&isin;`
- [ ] I understand that emojis are UTF-8 characters, not images
- [ ] I can display emojis using entity numbers like `&#128512;`
- [ ] I know how to resize emojis using CSS `font-size`
- [ ] I have completed the mini project
- [ ] I can identify and fix all 8 types of common mistakes listed

---

## Reflection Questions

1. Why can't you just type `<` directly into your paragraph text?
2. What is the difference between `&lt;` (entity name) and `&#60;`
   (entity number)? Which should you use and why?
3. If an emoji appears as garbled characters or question marks on your page,
   what is the most likely cause and how do you fix it?
4. Why do professional developers always use lowercase HTML element and
   attribute names, even though HTML technically allows uppercase?
5. You want to display the text `Price: 5 < 10 & tax = €2`. Write the
   correct HTML for this sentence using the appropriate entities.
6. What would happen if you tried to write `A & B Tours` in an `href`
   attribute without using `&amp;`? Why?

---

## Lesson Summary

This lesson covered four tightly connected areas of HTML writing expertise.

The **HTML Style Guide** establishes the professional conventions every web
developer follows: lowercase element and attribute names, always closing
tags, always quoting attribute values, 2-space indentation, including
`lang` on `<html>`, never skipping `<title>`, and using lowercase filenames.
Following these rules makes code readable, collaborative, and reliable.

**HTML Character Entities** solve the fundamental problem that some characters
— especially `<`, `>`, `&`, and `"` — have special meaning in HTML. Entities
allow you to display these as visible text using codes like `&lt;`, `&gt;`,
`&amp;`, and `&quot;`. Entities also give you access to characters not on
your keyboard, like `&euro;` (€), `&copy;` (©), `&trade;` (™), and the
non-breaking space `&nbsp;`. Every entity ends with a semicolon (`;`) and
entity names are case-sensitive.

**HTML Symbols** extend this concept to hundreds of additional characters:
currency signs, arrows (`&larr;`, `&rarr;`), card suits (`&hearts;`, `&spades;`),
mathematical operators (`&sum;`, `&exist;`, `&isin;`), and Greek letters
(`&pi;`, `&sigma;`, `&Delta;`, `&Omega;`). Symbols can be referenced by entity
name, decimal entity number (`&#8364;`), or hexadecimal entity number
(`&#x20AC;`).

**HTML Emojis** are not images — they are UTF-8 characters with large entity
numbers (like `&#128512;` for 😀). They require `<meta charset="UTF-8">` to
display correctly. Because they are characters, they scale with CSS
`font-size` and can be placed anywhere text can go.

Together, these skills allow you to write clean, professional, internationally
compatible HTML pages that can display any character, symbol, or emoji from
any human language or technical domain.

---

> 🎓 **What's next?** In Lesson 30 you will learn about **HTML Character
> Sets** — how encoding works at a deeper level, the history of ASCII and
> Unicode, how the browser decides which charset to use, and the differences
> between common encodings like ISO-8859-1 and UTF-8.
