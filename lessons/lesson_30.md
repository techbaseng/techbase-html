---
render_with_liquid: false
title: "HTML Charsets, URL Encoding, and XHTML"
nav_order: 30
---

# Lesson 30: HTML Charsets, URL Encoding, and XHTML

---

## Lesson Introduction

Have you ever visited a website and seen strange symbols like `â€™` or `Ã©` instead of normal text? Or copied a URL from a browser and seen something like `https://example.com/search?q=hello%20world`? Or wondered why your browser sometimes shows broken characters when a page contains non-English text?

All of these mysteries come down to three closely connected topics that every web developer must understand:

1. **Character Sets (Charsets)** — how computers agree on which patterns of bits represent which letters and symbols
2. **URL Encoding** — how web addresses safely carry special characters across the internet
3. **XHTML** — a stricter version of HTML that follows XML rules, and what it teaches us about writing clean, correct HTML

By the end of this lesson, you will be able to:
- Explain what a character set is and why UTF-8 is the global standard
- Correctly declare a character set in any HTML page
- Read and decode URL-encoded strings
- Understand the full anatomy of a web address (URL)
- Explain the key differences between HTML and XHTML
- Write HTML that meets XHTML's stricter standards — making your code cleaner and more reliable

> **Real-World Connection:** When you build a website that must display Yoruba, Arabic, Chinese, or French characters alongside English — or when you build a search form whose data travels safely through URLs — these three topics are exactly what you need.

---

## Prerequisite Concepts

Before diving in, let's make sure three foundational ideas are clear.

### What is a Bit and a Byte?

A **bit** is the smallest unit of data in a computer. It can only be a `0` or a `1`. Think of it like a light switch — either OFF (`0`) or ON (`1`).

A **byte** is a group of 8 bits. With 8 switches, each either on or off, you can make 2⁸ = **256 different combinations**.

```
00000000 = 0
00000001 = 1
00000010 = 2
01000001 = 65
11111111 = 255
```

### What is a Character?

A **character** is any single letter, digit, punctuation mark, or symbol that you can type or display. For example: `A`, `z`, `3`, `@`, `£`, `é`, `₦`, `中`.

### What is Encoding?

**Encoding** is a system of rules that assigns a number to each character. The computer stores that number in binary (as bits), and when you read it back, the rules decode the number back into the right character.

Without agreed-upon encoding rules, one computer sending a letter `A` might look like `£` on another computer — complete garbled nonsense.

---

## Part 1: HTML Character Sets (Charsets)

### 1.1 — Why Browsers Need to Know the Character Set

When a browser receives an HTML file from a server, it sees a stream of raw bytes — just numbers. Those bytes represent text, but the browser cannot display the correct characters unless it knows **which encoding was used** to write that file.

This is like receiving a secret message in code. Before you can read it, you need to know which cipher (code system) was used.

The `<meta charset="...">` tag in the `<head>` section of your HTML page tells the browser which encoding to use to decode the file.

**The standard way to declare a character set in HTML5:**

```html
<meta charset="UTF-8">
```

This one line, placed inside `<head>`, is all you need. The browser will then correctly decode and display all characters in the file using the UTF-8 rules.

> **Important:** The HTML specification strongly encourages all web developers to use **UTF-8**. It is the recommended character set for all modern webpages.

---

### 1.2 — The History of Character Sets: From ASCII to UTF-8

Character encoding systems have evolved over decades. Understanding this history helps you understand why we use UTF-8 today.

---

#### Stage 1: ASCII — The Original Internet Character Set

**ASCII** stands for **American Standard Code for Information Interchange**.

ASCII was **the first character encoding standard used on the web**. It defined **128 different characters** — enough for the English language and basic symbols.

Here is what ASCII covers:
- English letters: `a` to `z` and `A` to `Z`
- Digits: `0` to `9`
- Common symbols: `! $ + - ( ) @ < > . # ?`

ASCII uses numbers 0 to 127. Each character is stored as a number in that range.

**ASCII number examples:**

| Character | ASCII Number | Binary |
|-----------|-------------|--------|
| A | 65 | 01000001 |
| B | 66 | 01000010 |
| a | 97 | 01100001 |
| 0 | 48 | 00110000 |
| Space | 32 | 00100000 |

**Simple Example — What ASCII "sees":**

If you type the word `Hi` in ASCII, the computer stores it as:

```
H = 72 = 01001000
i = 105 = 01101001
```

The file actually contains these two byte values. When the browser reads them back and uses ASCII rules, it displays `Hi`.

**The Problem with ASCII:**
ASCII only covers 128 characters — great for English, but the world has thousands of other scripts: Arabic, Chinese, Yoruba, Greek, Hebrew, Hindi, Japanese, and many more. ASCII has no way to represent any of them.

---

#### Stage 2: ANSI (Windows-1252)

**ANSI** — also called **Windows-1252** — was the character set used by Windows operating systems.

Key facts about ANSI:
- Characters 0–127 are identical to ASCII (same numbers, same letters)
- Characters 128–159 are special symbols specific to ANSI (e.g., `€`, `Ž`, `™`)
- Characters 160–255 are the same as UTF-8 in that range

To use ANSI in HTML5, you would write:

```html
<meta charset="Windows-1252">
```

**Why ANSI is no longer recommended:**
ANSI was designed for Western European languages. It still does not support Arabic, Chinese, or most African language scripts. It was a step forward from ASCII but still far too limited for the global web.

---

#### Stage 3: ISO-8859-1 — The Default for HTML 4

**ISO-8859-1** (also called Latin-1) was the **default character set for HTML version 4** (the version before HTML5).

Key facts about ISO-8859-1:
- Characters 0–127 are identical to ASCII
- Characters 128–159 are NOT used (left empty)
- Characters 160–255 are the same as ANSI and UTF-8 in that range

**It supported 256 characters total** — covering Western European languages like French, Spanish, German, and Portuguese.

**How to declare ISO-8859-1:**

In HTML 4 (old style):
```html
<meta http-equiv="Content-Type" content="text/html;charset=ISO-8859-1">
```

In HTML5 (simpler):
```html
<meta charset="ISO-8859-1">
```

**Why ISO-8859-1 is no longer used:**
Like ANSI, 256 characters is nowhere near enough for the world's writing systems. Modern HTML5 pages should always use UTF-8.

---

#### Stage 4: UTF-8 — The Universal Standard

**UTF-8** stands for **Unicode Transformation Format — 8-bit**.

UTF-8 is the **modern, universal character encoding** used by virtually all websites today. Here is what makes it special:

- Characters 0–127 are **identical to ASCII** — so all basic English text works perfectly
- Characters 128–159 are NOT used (for safety)
- Characters 160–255 are the same as ANSI and ISO-8859-1
- Characters 256 and beyond extend to **over 1,000,000 characters** — covering every writing system on Earth

**What UTF-8 can display:**
- All English letters and numbers ✓
- Western European accented letters (é, ñ, ü, ô) ✓
- African scripts (Yoruba: ẹ, ọ, ṣ) ✓
- Arabic (مرحبا) ✓
- Chinese (你好) ✓
- Japanese (こんにちは) ✓
- Hindi (नमस्ते) ✓
- Emojis (😊 🌍 🎉) ✓
- Mathematical symbols (∑ ∞ √) ✓
- Currency symbols (£ € ¥ ₦ ₹) ✓

**How to declare UTF-8 (the modern, correct way):**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My UTF-8 Page</title>
</head>
<body>
  <p>Hello World!</p>
  <p>Bonjour le monde!</p>
  <p>Olá Mundo!</p>
  <p>مرحبا بالعالم</p>
  <p>你好世界</p>
</body>
</html>
```

**Expected Output in browser:**

```
Hello World!
Bonjour le monde!
Olá Mundo!
مرحبا بالعالم
你好世界
```

All five lines display correctly because UTF-8 knows how to decode every character.

> **Thinking Prompt:** What do you think would happen if the page used `charset="ISO-8859-1"` instead of `charset="UTF-8"`, but the file actually contained Chinese characters? The browser would try to decode the Chinese bytes using ISO-8859-1 rules and display completely wrong symbols — the classic "mojibake" (garbled text) problem.

---

### 1.3 — The Unicode System and UTF-8

**Unicode** is an international standard that assigns a unique number (called a **code point**) to every character from every writing system in the world.

Think of Unicode as a universal dictionary: every character in every language has a unique ID number.

For example:
- `A` is Unicode code point U+0041
- `é` is Unicode code point U+00E9
- `中` is Unicode code point U+4E2D
- `₦` (Naira symbol) is Unicode code point U+20A6
- `😊` is Unicode code point U+1F60A

**UTF-8** is the most popular *way of storing* Unicode code points in bytes. It is efficient: common characters (like English letters) use just 1 byte, while rarer characters use 2, 3, or 4 bytes.

---

### 1.4 — Character Set Quick Reference Table

| Character Set | Year Popular | Characters Covered | Recommended? |
|---------------|-------------|-------------------|--------------|
| ASCII | 1960s–1990s | 128 (English + basic symbols) | No — too limited |
| ANSI (Windows-1252) | 1990s–2000s | 256 (Western Europe + English) | No — legacy only |
| ISO-8859-1 | 1990s–2000s | 256 (Western Europe + English) | No — HTML 4 era |
| UTF-8 | 2000s–now | 1,000,000+ (all world languages) | YES — always use this |

---

### 1.5 — A Sample of UTF-8 Character Groups

UTF-8 can represent an enormous variety of scripts. Here are some of the character groups available:

- **Basic Latin** — `ABCD abcd 0123 ?#$%` (same as ASCII)
- **Latin Extended A** — `ĀĂĄ ĆĈĊ ĒĔĖĘ` (extra letters for European languages)
- **Latin Extended B** — `ƀƁƂ ƆƇ ƉƊ` (more phonetic and historic Latin)
- **Diacritical Marks** — `àáâã èéêẽ òóôõ` (accent marks added to letters)
- **General Punctuation** — `‰ ‱ ⁒ ‼ ⁇ ⁈` (advanced punctuation)
- **Super and Subscript** — `C⁰ Cⁱ C⁴ C₆ C₇` (for scientific notation)
- **Braille** — `⠓⠑⠇⠇⠕` (for accessibility)
- Hundreds more groups covering Arabic, Hebrew, Devanagari, CJK (Chinese/Japanese/Korean), African scripts, emoji, symbols, and more

---

### 1.6 — Where to Put the `charset` Declaration

The `<meta charset="UTF-8">` tag **must go inside the `<head>` section**, and it should be one of the very first lines — ideally within the first 1,024 bytes of the file. This is because the browser begins decoding the file immediately, and it needs to know the character set before it encounters any non-ASCII characters.

**Correct placement:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">          <!-- ← Must be near the top of <head> -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Title</title>
</head>
<body>
  <!-- page content here -->
</body>
</html>
```

**Common mistake — wrong placement:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Page</title>
  <!-- Other meta tags -->
  <meta charset="UTF-8">    <!-- ← Too late! Should come first in <head> -->
</head>
```

---

## Part 2: URL Encoding

### 2.1 — What is a URL?

Before we can understand URL encoding, we need to understand what a URL is and how it is structured.

**URL** stands for **Uniform Resource Locator**. It is the technical name for a **web address** — the string you type into your browser to visit a website.

**Examples of URLs:**

```
https://www.google.com
https://www.w3schools.com/html/default.asp
ftp://files.example.com/documents/report.pdf
file:///C:/Users/Jane/Documents/index.html
```

---

### 2.2 — The Anatomy of a URL

Every URL is made up of several named parts. Let's break down this example:

```
https://www.w3schools.com/html/default.asp
```

The full URL syntax is:

```
scheme://prefix.domain:port/path/filename
```

Let's understand each part:

| Part | Name | What it does | Example |
|------|------|-------------|---------|
| `https` | **Scheme** | Defines the type of internet service | `http`, `https`, `ftp`, `file` |
| `www` | **Prefix** | Defines the domain prefix | `www` is the default for web pages |
| `w3schools.com` | **Domain** | The internet domain name (the website's address) | `google.com`, `bbc.co.uk` |
| (not shown) | **Port** | The port number at the host | Default for http is `80`, https is `443` |
| `/html/` | **Path** | A path (folder) at the server | `/html/`, `/images/`, `/blog/` |
| `default.asp` | **Filename** | The specific document or resource | `default.asp`, `index.html` |

**Let's break down a more complete URL:**

```
https://www.bbc.co.uk:443/news/world/africa/article.html
  │        │    │       │    │          │
  │        │    │       │    │          └── filename: article.html
  │        │    │       │    └── path: /news/world/africa/
  │        │    │       └── port: 443
  │        │    └── domain: bbc.co.uk
  │        └── prefix: www
  └── scheme: https (secure)
```

> **Thinking Prompt:** Why do you think websites use `https://` instead of `http://`? The `s` stands for **secure** — the data is **encrypted** so no one can spy on what you send or receive.

---

### 2.3 — Common URL Schemes

A **scheme** tells the browser what *type of service* it is connecting to.

| Scheme | Stands For | Used For |
|--------|-----------|---------|
| `http` | HyperText Transfer Protocol | Regular web pages — NOT encrypted |
| `https` | Secure HyperText Transfer Protocol | Secure web pages — encrypted |
| `ftp` | File Transfer Protocol | Uploading or downloading files |
| `file` | (none) | Opening a file stored on your local computer |

**Simple examples:**

```
http://www.oldsite.com              ← Not encrypted (avoid for sensitive data)
https://www.bankwebsite.com         ← Encrypted (good for login, payments)
ftp://files.myserver.com/report.pdf ← File download via FTP
file:///C:/my-project/index.html    ← Local file on your computer
```

> **Real-World Note:** Modern browsers show a padlock icon 🔒 for `https://` pages and may warn users about `http://` pages. Always use `https://` for any site that handles personal data.

---

### 2.4 — Why URL Encoding Exists

Here is the key rule you must know:

> **URLs can only contain characters from the ASCII character set.**

This means URLs cannot contain spaces, accented letters, symbols like `£`, or characters from non-English scripts like Arabic or Chinese — at least not directly.

But what if a user types a search query like `hello world` or `café` into a search box? Or what if a web address needs to contain a `&`, `=`, or `?` in a path where those characters have special meaning?

The solution is **URL Encoding**: a system that converts any problematic character into a safe format that URLs can carry.

---

### 2.5 — How URL Encoding Works

URL encoding works by replacing unsafe characters with a **percent sign `%`** followed by **two hexadecimal digits** representing that character's value in UTF-8.

**Key rule:**
> `unsafe character` → `%` + hex code

The most important example is the **space character**:
- A space is encoded as `%20` (or sometimes a `+` sign in form data)

**Examples of URL encoding:**

| Character | URL Encoded Form | Explanation |
|-----------|-----------------|-------------|
| Space ` ` | `%20` or `+` | Space is not allowed in URLs |
| `&` | `%26` | `&` has special meaning in URLs (separates parameters) |
| `=` | `%3D` | `=` has special meaning (assigns parameter values) |
| `#` | `%23` | `#` has special meaning (page anchors) |
| `+` | `%2B` | `+` is used for space, so literal `+` needs encoding |
| `/` | `%2F` | `/` separates URL path segments |
| `?` | `%3F` | `?` starts the query string |
| `@` | `%40` | `@` has special meaning in URLs |
| `£` | `%C2%A3` | Non-ASCII character (British Pound) |
| `©` | `%C2%A9` | Non-ASCII character (copyright symbol) |
| `€` | `%E2%82%AC` | Non-ASCII character (Euro sign) |
| `®` | `%C2%AE` | Non-ASCII character (registered trademark) |

> **Notice:** Non-ASCII characters like `£`, `©`, `€` need **multiple percent-encoded bytes** because in UTF-8 they require more than one byte to represent.

---

### 2.6 — Real-Life URL Encoding Examples

**Example 1 — A search query with spaces:**

When you search for `Lagos weather today` on Google, your browser converts this to:

```
https://www.google.com/search?q=Lagos%20weather%20today
```

- `?` — begins the query string
- `q=` — the parameter name (query)
- `Lagos%20weather%20today` — the search text, with spaces encoded as `%20`

**Example 2 — A URL with special characters:**

Searching for `C++ programming`:

```
https://www.example.com/search?q=C%2B%2B+programming
```

- `C%2B%2B` — the `+` signs are encoded as `%2B` (because `+` itself means space in form data)
- `+programming` — the space before "programming" is encoded as `+`

**Example 3 — Multiple URL parameters:**

A shopping website might build this URL when you filter products:

```
https://shop.example.com/products?category=books&price=1000&sort=newest
```

- `?` — starts the query string
- `category=books` — first parameter
- `&` — separates parameters (this is why `&` itself needs to be encoded if it appears inside a value)
- `price=1000` — second parameter
- `&sort=newest` — third parameter

---

### 2.7 — ASCII Encoding Examples by Character Set

The same character can be encoded differently depending on the character set being used. Here is a comparison between Windows-1252 (ANSI) and UTF-8 encodings for the same characters:

| Character | Name | Windows-1252 Encoding | UTF-8 Encoding |
|-----------|------|----------------------|----------------|
| `€` | Euro sign | `%80` | `%E2%82%AC` |
| `£` | Pound sign | `%A3` | `%C2%A3` |
| `©` | Copyright | `%A9` | `%C2%A9` |
| `®` | Registered mark | `%AE` | `%C2%AE` |
| `À` | A with grave | `%C0` | `%C3%80` |
| `Á` | A with acute | `%C1` | `%C3%81` |
| `Â` | A with circumflex | `%C2` | `%C3%82` |
| `Ä` | A with umlaut | `%C4` | `%C3%84` |
| `Å` | A with ring | `%C5` | `%C3%85` |

> **Why are they different?** Because Windows-1252 uses a single byte for each of these characters (fitting into the range 128–255), while UTF-8 needs two or three bytes for the same characters. Each byte gets its own `%XX` code. This is why the HTML5 specification defaults to UTF-8 — it ensures consistent encoding everywhere.

---

### 2.8 — How URL Encoding Appears in Practice

When you use an HTML form to send data, the browser automatically encodes the input before sending it. You don't need to encode manually in most cases — but you do need to understand what is happening.

**Example — A simple search form:**

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Search Example</title>
</head>
<body>

  <form action="/search" method="GET">
    <label for="query">Search:</label>
    <input type="text" id="query" name="q">
    <button type="submit">Search</button>
  </form>

</body>
</html>
```

**What happens when user types "Lagos Festival 2026" and clicks Search:**

The browser automatically URL-encodes the input and navigates to:

```
/search?q=Lagos+Festival+2026
```

or equivalently:

```
/search?q=Lagos%20Festival%202026
```

The spaces become either `+` or `%20` — both are valid. The server receives the value and decodes it back to `Lagos Festival 2026`.

> **Thinking Prompt:** What URL would the browser generate if the user typed `naira ₦ exchange rate`? The `₦` (Naira symbol) is not ASCII, so it would be encoded in UTF-8 bytes as `%E2%82%A6`.

---

## Part 3: HTML vs. XHTML

### 3.1 — What is XHTML?

**XHTML** stands for **eXtensible HyperText Markup Language**.

It is a version of HTML that was rewritten to follow the strict rules of **XML** (eXtensible Markup Language).

Think of it this way:
- **HTML** is like a forgiving teacher — if you make small mistakes (like forgetting a closing tag), the browser will try its best to fix them and still show the page.
- **XHTML** is like a strict examiner — if you make any mistake at all, the document is considered invalid and may not work.

---

### 3.2 — Why Was XHTML Created?

**The Problem with "Forgiving" HTML:**

Standard HTML browsers have always been very tolerant of mistakes. If you forget a closing tag, use uppercase tag names, or miss a quote on an attribute value, most browsers will still display the page. They have built-in error correction code to guess what you meant.

This sounds helpful, but it caused problems:
- Developers got lazy and wrote sloppy code
- Browsers had to implement complex (and sometimes inconsistent) error-fixing logic
- Pages sometimes looked different in different browsers because each browser guessed differently
- HTML pages could not easily be processed by other software that expected clean, well-formed data

**The XHTML Solution:**

XML is a stricter data format used across the web for data exchange. XHTML applied XML's strict rules to HTML:
- All tags must be properly nested
- All tags must be closed
- All attributes must be quoted
- Tag and attribute names must be lowercase

This made documents predictable, consistent, and processable by any XML tool.

---

### 3.3 — The Nine Key Differences: HTML vs. XHTML

Here are all the important rules that XHTML requires that standard HTML does not enforce:

---

#### Difference 1: `<!DOCTYPE>` is Mandatory in XHTML

In HTML5, the doctype is short and simple. In XHTML, a longer, specific DOCTYPE declaration is required.

**XHTML DOCTYPE (required):**

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
```

**HTML5 DOCTYPE (much simpler):**

```html
<!DOCTYPE html>
```

---

#### Difference 2: The `xmlns` Attribute in `<html>` is Mandatory

In XHTML, the `<html>` tag must include a special attribute called `xmlns` (XML Namespace) that declares this document follows XHTML rules.

**XHTML `<html>` tag:**

```html
<html xmlns="http://www.w3.org/1999/xhtml">
```

**HTML5 `<html>` tag:**

```html
<html lang="en">
```

---

#### Difference 3: `<html>`, `<head>`, `<title>`, and `<body>` are All Mandatory

In HTML5, technically some of these can be omitted (the browser implies them). In XHTML, all four must be present. A minimum valid XHTML document looks like this:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <title>Title of document</title>
</head>
<body>
  <p>Some content here...</p>
</body>
</html>
```

---

#### Difference 4: Elements Must Always be Properly Nested

**Nesting** means opening and closing tags must be correctly matched — inner tags must close before outer tags close.

**Correct (XHTML and good HTML):**

```html
<b><i>Bold and italic text</i></b>
```

The `<i>` tag opens *inside* `<b>`, so `<i>` must close *before* `<b>` closes.

**Wrong (invalid in XHTML, but browsers may fix it in HTML):**

```html
<b><i>Bold and italic text</b></i>
```

Here `<b>` closes before `<i>`, which is incorrect overlapping.

**Analogy:** Think of nested tags like nested cups. If you put a small cup inside a large cup, you must take the small cup out first before you can move the large cup. Tags work the same way.

---

#### Difference 5: Elements Must Always be Closed

In HTML, some elements do not require a closing tag. Browsers assume where they end. In XHTML, **every element must be explicitly closed**.

**HTML (lenient — this is allowed):**

```html
<p>This is a paragraph
<p>This is another paragraph
```

**XHTML (strict — closing tags required):**

```html
<p>This is a paragraph</p>
<p>This is another paragraph</p>
```

---

#### Difference 6: Empty Elements Must Always be Closed

**Empty elements** are tags that have no content and no closing tag in HTML — for example `<br>`, `<hr>`, `<img>`. In XHTML, even empty elements must be closed using a self-closing slash.

| Element | HTML (allowed) | XHTML (required) |
|---------|---------------|-----------------|
| Line break | `<br>` | `<br />` |
| Horizontal rule | `<hr>` | `<hr />` |
| Image | `<img src="x.jpg">` | `<img src="x.jpg" />` |
| Input | `<input type="text">` | `<input type="text" />` |
| Meta | `<meta charset="UTF-8">` | `<meta charset="UTF-8" />` |
| Link | `<link rel="stylesheet" href="style.css">` | `<link rel="stylesheet" href="style.css" />` |

The trailing space and slash `/>` is what closes the empty element in XHTML.

---

#### Difference 7: Elements Must be in Lowercase

In HTML, tag names are case-insensitive — `<P>`, `<p>`, and `<P>` all work. In XHTML, **all tag names must be lowercase**.

**XHTML Correct:**

```html
<body>
  <p>This is a paragraph</p>
</body>
```

**XHTML Wrong:**

```html
<BODY>
  <P>This is a paragraph</P>
</BODY>
```

---

#### Difference 8: Attribute Names Must be in Lowercase

Just like element names, attribute names in XHTML must also be lowercase.

**XHTML Correct:**

```html
<a href="https://www.example.com">Visit us</a>
```

**XHTML Wrong:**

```html
<a HREF="https://www.example.com">Visit us</a>
```

---

#### Difference 9: Attribute Values Must be Quoted

In HTML, attribute values can sometimes be written without quotes. In XHTML, **all attribute values must always be in quotation marks**.

**XHTML Correct:**

```html
<a href="https://www.example.com">Visit us</a>
```

**XHTML Wrong:**

```html
<a href=https://www.example.com>Visit us</a>
```

---

#### Difference 10: Attribute Minimization is Forbidden

In HTML, some attributes can be written as just the attribute name alone — this is called **attribute minimization**. For example, the `checked` attribute on a checkbox, or `disabled` on an input.

In XHTML, every attribute must have a full `name="value"` pair — attribute minimization is not allowed.

**XHTML Correct:**

```html
<input type="checkbox" name="vehicle" value="car" checked="checked" />
<input type="text" name="lastname" disabled="disabled" />
```

**XHTML Wrong (minimized attributes — forbidden):**

```html
<input type="checkbox" name="vehicle" value="car" checked />
<input type="text" name="lastname" disabled />
```

---

### 3.4 — A Complete Comparison: HTML5 vs. XHTML 1.1

Here is a side-by-side comparison of the same page written in HTML5 and XHTML 1.1:

**HTML5 version (flexible and modern):**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My Page</title>
</head>
<body>
  <h1>Hello World</h1>
  <p>This is a paragraph.
  <p>This is another paragraph.
  <br>
  <img src="photo.jpg" alt="A photo">
  <input type="text" name="name" disabled>
</body>
</html>
```

**XHTML 1.1 version (strict XML rules):**

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta charset="UTF-8" />
  <title>My Page</title>
</head>
<body>
  <h1>Hello World</h1>
  <p>This is a paragraph.</p>
  <p>This is another paragraph.</p>
  <br />
  <img src="photo.jpg" alt="A photo" />
  <input type="text" name="name" disabled="disabled" />
</body>
</html>
```

**Key differences visible in the comparison:**

- DOCTYPE is much longer in XHTML
- `<html>` tag has `xmlns` in XHTML
- `<meta>` is self-closed with `/>` in XHTML
- `<p>` tags have closing `</p>` in XHTML
- `<br>` becomes `<br />` in XHTML
- `<img>` is self-closed with `/>` in XHTML
- `disabled` becomes `disabled="disabled"` in XHTML

---

### 3.5 — Should You Use HTML5 or XHTML Today?

**For almost all modern projects: Use HTML5.**

HTML5 is the current standard. It is powerful, flexible, well-supported by all browsers, and simpler to write. XHTML is no longer the recommended standard for new web projects.

**However, XHTML's rules have lasting value:**

Even though we use HTML5 today, following XHTML-style best practices makes your HTML much cleaner, more consistent, and professional:
- Close all your tags
- Write all tag names in lowercase
- Always quote attribute values
- Properly nest your elements

Many professional developers and coding style guides follow these XHTML-style conventions even when writing HTML5, because it leads to fewer bugs and more readable code.

> **Real-World Connection:** Many server-side templating systems, XML parsers, and email HTML renderers (like those used for marketing emails) require XHTML-style well-formed HTML. Knowing XHTML rules means your HTML works correctly in ALL environments, not just forgiving web browsers.

---

## Part 4: Guided Practice Exercises

### Exercise 1 — Character Set Detective

**Objective:** Identify charset issues and fix them.

**Scenario:** Your friend built a webpage for a French restaurant. The page should display French accented characters like `é`, `ê`, `à`, `ü`, `ç`, but instead it shows strange symbols. You need to diagnose and fix the problem.

**Broken page code:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Restaurant Menu</title>
</head>
<body>
  <h1>Café Élysée</h1>
  <p>Spécialités du jour: Crème brûlée, Île flottante, Châteaubriand</p>
</body>
</html>
```

**The Fix:**

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">   <!-- ← Add this as the FIRST line inside <head> -->
  <title>Restaurant Menu</title>
</head>
<body>
  <h1>Café Élysée</h1>
  <p>Spécialités du jour: Crème brûlée, Île flottante, Châteaubriand</p>
</body>
</html>
```

**Expected Output in browser:**

```
Café Élysée
Spécialités du jour: Crème brûlée, Île flottante, Châteaubriand
```

All accented French characters display correctly now.

**Self-Check Questions:**

- What was missing from the broken page?
- Where exactly must `<meta charset="UTF-8">` be placed?
- Why did the accented characters fail to display without the charset declaration?

**What-If Challenge:**
- What if you change the language to Yoruba and add: `<p>Ẹ káàárọ̀! Ẹ káabọ̀!</p>` — will UTF-8 still handle it? (Yes — UTF-8 covers Yoruba characters too!)

---

### Exercise 2 — Decode a URL

**Objective:** Read and decode a URL-encoded string.

**Scenario:** You receive these URLs in a log file. Decode what the user was searching for.

**URL 1:**
```
https://example.com/search?q=World+Cup+2026
```

**Decoded:** `World Cup 2026` (the `+` signs represent spaces)

**URL 2:**
```
https://example.com/search?q=Lagos%20music%20festival
```

**Decoded:** `Lagos music festival` (`%20` = space)

**URL 3:**
```
https://shop.example.com/products?category=food%20%26%20drink&price=500
```

**Decoded:**
- `category` = `food & drink` (`%20` = space, `%26` = `&`)
- `price` = `500`

**URL 4:**
```
https://example.com/weather?city=S%C3%A3o+Paulo
```

**Decoded:** `city` = `São Paulo` (`%C3%A3` is the UTF-8 encoding of `ã`)

**Exercise Task:**
Build a URL manually. Encode this search query for a URL parameter: `naira & dollar rates 2026`

**Answer:**
```
naira%20%26%20dollar%20rates%202026
```

or:

```
naira+%26+dollar+rates+2026
```

So the full URL would be:

```
https://example.com/search?q=naira+%26+dollar+rates+2026
```

---

### Exercise 3 — HTML to XHTML Conversion

**Objective:** Convert an HTML5 page to valid XHTML.

**Starting HTML5 code (has several XHTML violations):**

```html
<!DOCTYPE html>
<html>
<head>
<title>Student Records</title>
</head>
<body>
<H1>Student Records</H1>
<P>Welcome to the student portal.
<P>Please log in below.
<BR>
<IMG SRC="school-logo.png" ALT="School Logo">
<input type="text" name="username" PLACEHOLDER="Enter username">
<input type="checkbox" name="remember" checked>
<label for="remember">Remember me</label>
</body>
</html>
```

**XHTML violations in the code above:**
1. Missing `xmlns` attribute on `<html>`
2. Missing XHTML DOCTYPE
3. `<H1>` is uppercase — should be `<h1>`
4. `<P>` tags are uppercase AND not closed
5. `<BR>` is uppercase and not self-closed
6. `<IMG>` is uppercase, not self-closed, `SRC` and `ALT` are uppercase
7. `<input>` has `PLACEHOLDER` in uppercase
8. `checked` is minimised (not `checked="checked"`)

**Corrected XHTML version:**

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta charset="UTF-8" />
  <title>Student Records</title>
</head>
<body>
  <h1>Student Records</h1>
  <p>Welcome to the student portal.</p>
  <p>Please log in below.</p>
  <br />
  <img src="school-logo.png" alt="School Logo" />
  <input type="text" name="username" placeholder="Enter username" />
  <input type="checkbox" name="remember" checked="checked" />
  <label for="remember">Remember me</label>
</body>
</html>
```

**Self-Check Questions:**

- How many changes did you count between the two versions?
- What is the key change for empty elements like `<br>` and `<img>`?
- Why is `checked="checked"` used instead of just `checked`?

---

## Part 5: Mini Project — Multilingual Contact Page with Clean XHTML-Style HTML

You will now build a complete, professional-quality multilingual contact page. It will correctly declare UTF-8, display text in multiple languages, build a working URL query string, and follow XHTML-style best practices throughout.

---

### Stage 1 — Build the HTML Structure

Create a file called `contact.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Global Contact Page</title>
</head>
<body>

  <header>
    <h1>Global Contact Page</h1>
    <p>Reach us in your language — we speak many!</p>
  </header>

  <!-- Multilingual Greetings Section -->
  <section>
    <h2>Greetings from Around the World</h2>
    <ul>
      <li>🇬🇧 English: <strong>Hello, World!</strong></li>
      <li>🇫🇷 French: <strong>Bonjour le monde!</strong></li>
      <li>🇳🇬 Yoruba: <strong>Ẹ káàbọ̀! (Welcome!)</strong></li>
      <li>🇸🇦 Arabic: <strong>مرحبا بالعالم</strong></li>
      <li>🇨🇳 Chinese: <strong>你好，世界！</strong></li>
      <li>🇧🇷 Portuguese: <strong>Olá Mundo!</strong></li>
      <li>🇩🇪 German: <strong>Hallo Welt!</strong></li>
      <li>🇯🇵 Japanese: <strong>こんにちは世界！</strong></li>
    </ul>
  </section>

  <!-- Contact Form Section -->
  <section>
    <h2>Contact Us</h2>
    <form action="/contact-submit" method="GET">

      <label for="name">Full Name:</label><br />
      <input type="text" id="name" name="name" placeholder="Enter your full name" /><br /><br />

      <label for="email">Email Address:</label><br />
      <input type="email" id="email" name="email" placeholder="you@example.com" /><br /><br />

      <label for="country">Country:</label><br />
      <input type="text" id="country" name="country" placeholder="e.g. Nigeria" /><br /><br />

      <label for="message">Message:</label><br />
      <textarea id="message" name="message" rows="5" cols="40"
        placeholder="Type your message here..."></textarea><br /><br />

      <label>
        <input type="checkbox" name="subscribe" value="yes" />
        Subscribe to our newsletter
      </label><br /><br />

      <button type="submit">Send Message</button>

    </form>
  </section>

  <!-- URL Encoding Demonstration -->
  <section>
    <h2>How Your Data Travels in the URL</h2>
    <p>When you submit this form, your browser encodes your input into a URL like this:</p>
    <code>
      /contact-submit?name=Jane+Doe&amp;email=jane%40example.com&amp;country=Nigeria&amp;message=Hello%21&amp;subscribe=yes
    </code>
    <p>Notice: <code>@</code> becomes <code>%40</code>, spaces become <code>+</code>,
       <code>!</code> becomes <code>%21</code>,
       and <code>&amp;</code> separates each field.</p>
  </section>

  <footer>
    <p>&copy; 2026 Global Contact Page. Charset: UTF-8. Built with clean HTML.</p>
  </footer>

</body>
</html>
```

**Milestone 1 Output (no CSS yet):** You should see all eight multilingual greetings with their flags, a contact form with four fields, a URL encoding explanation, and a footer. All characters display correctly thanks to `charset="UTF-8"`.

---

### Stage 2 — Add CSS Styling

Add this inside `<head>` before `</head>`:

```html
<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    color: #333;
    line-height: 1.7;
  }

  header {
    background-color: #1a237e;
    color: white;
    padding: 25px 30px;
    text-align: center;
  }

  header h1 { font-size: 2em; }
  header p { font-size: 1.1em; margin-top: 5px; opacity: 0.9; }

  section {
    background-color: white;
    margin: 20px auto;
    padding: 25px 30px;
    max-width: 700px;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  }

  h2 {
    color: #1a237e;
    border-bottom: 2px solid #1a237e;
    padding-bottom: 8px;
    margin-bottom: 15px;
  }

  ul {
    list-style: none;
    padding-left: 0;
  }

  ul li {
    padding: 8px 0;
    border-bottom: 1px solid #eee;
    font-size: 1.05em;
  }

  label {
    font-weight: bold;
    color: #333;
  }

  input[type="text"],
  input[type="email"],
  textarea {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 1em;
    font-family: Arial, sans-serif;
  }

  button[type="submit"] {
    background-color: #1a237e;
    color: white;
    border: none;
    padding: 12px 30px;
    font-size: 1em;
    border-radius: 5px;
    cursor: pointer;
  }

  button[type="submit"]:hover {
    background-color: #283593;
  }

  code {
    display: block;
    background-color: #f0f0f0;
    padding: 12px;
    border-radius: 5px;
    font-size: 0.9em;
    word-break: break-all;
    margin: 10px 0;
    border-left: 4px solid #1a237e;
  }

  footer {
    text-align: center;
    padding: 20px;
    background-color: #1a237e;
    color: white;
    font-size: 0.9em;
  }
</style>
```

**Milestone 2 Output:** A polished multilingual contact page with a dark blue header, white content cards, a clean form, and a styled URL encoding demo section. All characters from all eight languages display perfectly.

---

### Stage 3 — Test and Verify

1. Open the file in your browser.
2. Confirm all eight language greetings appear correctly without garbled symbols.
3. Fill in the contact form and click "Send Message."
4. Look at the browser's address bar — you should see the URL-encoded query string.
5. Try typing a name with special characters like `José Díaz` and observe how the URL changes.

**Optional Advanced Extension:**
Add a ninth language of your choice to the greetings list. For example, Igbo: `Nnọọ n'ụwa!` or Hausa: `Barka da zuwa!`. Since we use UTF-8, any of these will display perfectly.

---

## Part 6: Common Beginner Mistakes

---

### Mistake 1 — Forgetting `<meta charset="UTF-8">` Entirely

**Broken code:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Page</title>
</head>
<body>
  <p>Café, naïve, résumé</p>
</body>
</html>
```

**Problem:** Without a charset declaration, browsers may default to a legacy encoding and display `CafÃ©, naÃ¯ve, rÃ©sumÃ©` — complete nonsense.

**Fixed code:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">   <!-- ← Always include this! -->
  <title>My Page</title>
</head>
<body>
  <p>Café, naïve, résumé</p>
</body>
</html>
```

---

### Mistake 2 — Placing `<meta charset>` Too Late in the `<head>`

**Broken code:**

```html
<head>
  <title>My Page</title>
  <link rel="stylesheet" href="style.css">
  <script src="app.js"></script>
  <meta charset="UTF-8">   <!-- ← Too late! Browser may have already started decoding -->
</head>
```

**Fixed code:**

```html
<head>
  <meta charset="UTF-8">   <!-- ← Must be first inside <head> -->
  <title>My Page</title>
  <link rel="stylesheet" href="style.css">
  <script src="app.js"></script>
</head>
```

---

### Mistake 3 — Putting Spaces Directly in URLs

**Wrong:**

```html
<a href="my page about dogs.html">Dog Page</a>
```

A space in a URL will break the link. The browser either truncates it at the space or produces an error.

**Fixed:**

```html
<a href="my-page-about-dogs.html">Dog Page</a>
```

Use hyphens instead of spaces in file names and URLs. If you must pass a space in a query string, the browser will encode it automatically for form submissions, but in hand-coded URLs, you should use `%20`:

```html
<a href="/search?q=dog%20training">Search for dog training</a>
```

---

### Mistake 4 — Writing Uppercase Tags in HTML (Bad Habit from Old Code)

**Old-style code (works but not best practice):**

```html
<BODY>
  <H1>My Heading</H1>
  <P>My paragraph.</P>
  <BR>
</BODY>
```

**Modern HTML5 best practice (lowercase, XHTML-style):**

```html
<body>
  <h1>My Heading</h1>
  <p>My paragraph.</p>
  <br />
</body>
```

Lowercase tag names are standard, cleaner, and compatible with XHTML tools.

---

### Mistake 5 — Forgetting to Close Empty Tags (Important for XHTML and Email HTML)

**HTML5 (this is technically valid but not best practice):**

```html
<br>
<hr>
<img src="logo.png" alt="Logo">
<input type="text" name="email">
<meta charset="UTF-8">
```

**XHTML-style (best practice — always self-close empty tags):**

```html
<br />
<hr />
<img src="logo.png" alt="Logo" />
<input type="text" name="email" />
<meta charset="UTF-8" />
```

This habit is especially important when building HTML emails (which are rendered by email clients that expect XHTML-style markup) or working with XML-based systems.

---

### Mistake 6 — Not Quoting Attribute Values

**Wrong:**

```html
<a href=https://example.com>Visit</a>
<img src=photo.jpg alt=My Photo>
```

**Fixed:**

```html
<a href="https://example.com">Visit</a>
<img src="photo.jpg" alt="My Photo" />
```

Always quote every attribute value. Unquoted values break in XHTML and can cause unpredictable behavior in HTML when the value contains spaces.

---

### Mistake 7 — Misreading URL Encoded Characters

**Common confusion:** Seeing `%20` in a URL and not knowing what it means.

```
https://example.com/search?q=web%20development%20course
                                 ↑                ↑
                               %20 = space      %20 = space
```

**Decoded:** The user searched for `web development course`.

Another common one:

```
https://example.com/login?redirect=%2Fdashboard
                                    ↑
                                  %2F = /
```

**Decoded:** Redirect to `/dashboard` after login.

---

## Part 7: Reflection Questions

Think through these questions carefully. Articulating the answers will deepen your understanding.

1. **Why does UTF-8 support so many more characters than ASCII?** ASCII uses 7 bits (128 combinations). How many bits does UTF-8 use for its extended characters, and what does this tell us about its range?

2. **Imagine you are building a Nigerian government website** that must display names in English, Yoruba, Igbo, and Hausa. Which character set would you use, and why? What would happen if you chose ASCII instead?

3. **When you search for "café au lait" on a search engine**, what does the URL in your browser's address bar look like? (Hint: Think about spaces and the accented `é` character.)

4. **A URL contains the string `?name=John%20Doe&city=S%C3%A3o+Paulo`.** Decode the full name and city from this URL.

5. **Why was XHTML created even though HTML already existed?** What problem was it trying to solve, and was it successful in its goals?

6. **Which of the nine XHTML rules do you think is the most important for writing clean, professional HTML — even if you are not using XHTML?** Explain why.

7. **In the URL anatomy, what is the difference between the `path` and the `filename`?** Give an example URL and label its path and filename.

8. **Why does `https://` matter more than `http://` for websites that handle login forms or payment information?** What does the `s` in `https` actually do for users?

---

## Completion Checklist

Go through this checklist before considering this lesson complete:

- [ ] I can explain what a character set (charset) is and why it is necessary
- [ ] I know the four main character sets: ASCII, ANSI, ISO-8859-1, and UTF-8
- [ ] I understand why UTF-8 is the recommended standard for all modern webpages
- [ ] I can correctly write `<meta charset="UTF-8">` and know exactly where to place it
- [ ] I know that UTF-8 supports over 1,000,000 characters including all world scripts and emojis
- [ ] I can explain what a URL (Uniform Resource Locator) is
- [ ] I can identify and name all 6 parts of a URL (scheme, prefix, domain, port, path, filename)
- [ ] I understand the 4 common URL schemes: http, https, ftp, file
- [ ] I understand why URLs can only use ASCII characters
- [ ] I know that URL encoding replaces unsafe characters with `%` followed by hex digits
- [ ] I know that spaces are encoded as `%20` or `+`
- [ ] I can read and decode common URL-encoded strings
- [ ] I can explain what XHTML is and why it was created
- [ ] I know all 9 key differences between HTML and XHTML
- [ ] I can convert HTML code to valid XHTML
- [ ] I understand why XHTML-style practices improve HTML quality even in HTML5
- [ ] I completed Exercise 1 (charset fix)
- [ ] I completed Exercise 2 (URL decoding)
- [ ] I completed Exercise 3 (HTML to XHTML conversion)
- [ ] I built the multilingual contact page mini-project
- [ ] I understand the 7 common beginner mistakes and how to avoid them

---

## Lesson Summary

This lesson covered three foundational topics that explain how HTML handles text, web addresses, and code standards.

**Character Sets** are the agreed-upon rules that tell a browser how to decode bytes into readable characters. ASCII was the original 128-character standard, covering only English. ANSI and ISO-8859-1 expanded to 256 characters for Western European languages. UTF-8 is the modern universal standard, covering over 1,000,000 characters from every writing system on Earth — and it is fully backward-compatible with ASCII. Every HTML5 page should declare `<meta charset="UTF-8">` as the very first element inside `<head>`.

**URL Encoding** exists because URLs can only carry ASCII characters across the internet. Any character outside this set — including spaces, accented letters, and symbols — must be converted to a `%` followed by hexadecimal digits. A space becomes `%20`, an `&` becomes `%26`, and multi-byte UTF-8 characters like `£` become `%C2%A3`. Browsers handle this encoding automatically for form submissions, but developers need to understand the system to read, build, and debug URLs correctly. Every URL also has a fixed anatomy: scheme, prefix, domain, port, path, and filename.

**XHTML** is a stricter, XML-based version of HTML. Its nine key rules — mandatory DOCTYPE and xmlns, mandatory structural elements, proper nesting, closed elements, self-closed empty elements, lowercase tags, lowercase attributes, quoted attribute values, and no attribute minimization — were designed to make HTML more predictable and compatible with other data systems. While HTML5 has replaced XHTML as the recommended standard, following XHTML-style habits produces cleaner, more professional, and more universally compatible HTML code.

---

*Sources: W3Schools HTML Charset — https://www.w3schools.com/html/html_charset.asp | W3Schools HTML URL Encoding — https://www.w3schools.com/html/html_urlencode.asp | W3Schools HTML vs. XHTML — https://www.w3schools.com/html/html_xhtml.asp*
