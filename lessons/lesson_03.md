---
render_with_liquid: false
title: "Lesson 3 — HTML Elements: Anatomy, Nesting, Empty Elements & Case Sensitivity"
nav_order: 3
---

## Lesson Introduction

Welcome to Lesson 3! In Lessons 1 and 2, you learned what HTML is, how a document is structured, and how to use tags like `<h1>`, `<p>`, `<a>`, and `<img>`. You have already been *using* HTML elements — but do you truly understand what an element actually *is*?

In this lesson, we go deeper. We step back and study the fundamental building block of every single web page ever made: **the HTML element**.

By the end of this lesson you will be able to:

- Precisely define what an HTML element is and name all of its parts
- Understand why elements are nested inside each other and how to read that nesting clearly
- Explain the full nesting structure of a standard HTML document from the outside in
- Identify empty elements and explain why they have no closing tag
- Know why HTML is case insensitive but why you should always write in lowercase
- Confidently diagnose and fix common element-related mistakes
- Build a structured, multi-section web page using correct element nesting

> **Real-world connection:** Every developer, whether they are building a personal blog, a banking app, or a space agency's website, must have a rock-solid understanding of HTML elements and nesting. This is the grammar of the web — once it clicks, reading and writing HTML becomes effortless.

---

## Prerequisite Concepts

Before exploring elements in depth, let us briefly revisit two things from Lesson 2 that directly connect to this lesson.

### Quick Recap — Tags vs Elements

In Lesson 2, you used **tags** like `<p>` and `</p>`. But a **tag** and an **element** are not the same thing. Understanding the difference is the first step of this lesson.

- A **tag** is just the label itself: `<p>` or `</p>`
- An **element** is the *complete package*: the opening tag + the content + the closing tag

Think of it this way:

| Term | What it is | Example |
|------|-----------|---------|
| Opening tag | The starting label | `<p>` |
| Closing tag | The ending label | `</p>` |
| Content | The text or other elements inside | `Hello, world!` |
| **Element** | **All three combined** | `<p>Hello, world!</p>` |

---

## Part 1 — What Exactly Is an HTML Element?

### The Official Definition

An **HTML element** is defined as everything from the **start tag** to the **end tag**, including the content between them.

The formal structure is:

```
<tagname>Content goes here...</tagname>
```

Where:
- `<tagname>` is the **opening tag** (or start tag)
- `Content goes here...` is the **element content** — the text or other elements it holds
- `</tagname>` is the **closing tag** (or end tag) — note the forward slash `/` that distinguishes it from the opening tag

---

### Breaking Down Three Real Elements

Let us look at three familiar elements and label every part:

**Element 1 — A Heading:**

```html
<h1>My First Heading</h1>
```

| Part | Symbol | Meaning |
|------|--------|---------|
| Opening tag | `<h1>` | "A level-1 heading starts here" |
| Content | `My First Heading` | The visible text |
| Closing tag | `</h1>` | "The heading ends here" |

**Element 2 — A Paragraph:**

```html
<p>My first paragraph.</p>
```

| Part | Symbol | Meaning |
|------|--------|---------|
| Opening tag | `<p>` | "A paragraph starts here" |
| Content | `My first paragraph.` | The visible text |
| Closing tag | `</p>` | "The paragraph ends here" |

**Element 3 — A Line Break (special case — covered fully in Part 4):**

```html
<br>
```

| Part | Symbol | Meaning |
|------|--------|---------|
| Opening tag | `<br>` | "Insert a line break here" |
| Content | *none* | This element has no content |
| Closing tag | *none* | This element has no closing tag |

> **Analogy:** Think of an HTML element like a labelled container at a post office. The label on the front (`<p>`) tells the postal worker (browser) what kind of item is inside. The contents (text, images, other elements) are what gets delivered to the screen. The label on the back (`</p>`) seals the container shut.

---

### A Visual Map of an HTML Element

Here is a diagram labelling every part of one element:

```
     Opening tag          Content          Closing tag
         │                   │                  │
         ▼                   ▼                  ▼
      <tagname>   Content goes here...   </tagname>
         │                                      │
         └──────────── HTML Element ────────────┘
```

Everything between and including the two tags is **one complete HTML element**.

---

### Simple Example — Seeing Elements Clearly

```html
<!DOCTYPE html>
<html>
<body>

<h1>My First Heading</h1>
<p>My first paragraph.</p>

</body>
</html>
```

**Expected output in browser:**

```
My First Heading     ← rendered by the <h1> element
My first paragraph.  ← rendered by the <p> element
```

In this short page, there are **four** HTML elements:
1. The `<html>` element — wraps everything
2. The `<body>` element — wraps the visible content
3. The `<h1>` element — the heading
4. The `<p>` element — the paragraph

> **Thinking prompt:** Can you count the total number of *tags* in this example? (Answer: 8 — four opening tags and four closing tags.)

---

## Part 2 — Nested HTML Elements

### What Does "Nested" Mean?

**Nesting** means placing one element *inside* another element. The element that sits inside is called the **child element**. The element it sits inside is called the **parent element**.

Think of Russian nesting dolls (matryoshka dolls). The big doll is the outermost parent. Inside it sits a slightly smaller doll (its child). Inside that doll sits an even smaller one. HTML elements work exactly the same way.

Or think of it like folders on your computer:
- The Drive is the outermost container
- Inside the Drive is a Folder
- Inside the Folder is a Sub-folder
- Inside the Sub-folder is a File

In HTML:
- `<html>` is the Drive
- `<body>` is the Folder
- `<h1>` and `<p>` are the Files inside

---

### The Full Nesting Structure — Explained Layer by Layer

Here is the complete example document, and we will peel it apart layer by layer:

```html
<!DOCTYPE html>
<html>
<body>

<h1>My First Heading</h1>
<p>My first paragraph.</p>

</body>
</html>
```

#### Layer 1 — The `<html>` Element (The Root)

The `<html>` element is the **root element**. It defines the entire HTML document. Every other element in the file lives inside it.

```html
<html>
  ...everything else lives here...
</html>
```

Think of `<html>` as the outer walls of a house. Nothing in the house can exist outside those walls.

The `<html>` element has:
- A start tag: `<html>`
- An end tag: `</html>`
- Content: everything between them (including `<body>`)

---

#### Layer 2 — The `<body>` Element (Lives Inside `<html>`)

Inside the `<html>` element lives the `<body>` element:

```html
<body>
  <h1>My First Heading</h1>
  <p>My first paragraph.</p>
</body>
```

The `<body>` element defines the **document's body** — all the visible content the user sees on the page.

The `<body>` element has:
- A start tag: `<body>`
- An end tag: `</body>`
- Content: the `<h1>` and `<p>` elements

Notice: `<body>` is a **child** of `<html>`, and `<html>` is the **parent** of `<body>`.

---

#### Layer 3 — The `<h1>` and `<p>` Elements (Live Inside `<body>`)

Inside the `<body>` element there are two more elements:

```html
<h1>My First Heading</h1>
<p>My first paragraph.</p>
```

- The `<h1>` element defines a heading. Its content is the text `My First Heading`.
- The `<p>` element defines a paragraph. Its content is the text `My first paragraph.`

Both `<h1>` and `<p>` are **children** of `<body>`. They are also **siblings** of each other (two children of the same parent).

---

### Visualising Nesting as a Tree

Developers often think of an HTML document as a **tree structure**, where each element branches off from its parent:

```
html
├── body
│   ├── h1  →  "My First Heading"
│   └── p   →  "My first paragraph."
```

This tree shows:
- `html` is the root (top of the tree)
- `body` is a child of `html`
- `h1` and `p` are children of `body` (and siblings of each other)
- The text content hangs off each leaf element

> **Real-world connection:** This tree structure is called the **DOM** — the Document Object Model. Every JavaScript programme that interacts with a web page does so by navigating and manipulating this tree. Learning nesting now is your first step toward understanding how web apps and frameworks like React work.

---

### A More Complex Nesting Example

Nesting is not limited to two levels. Elements can be nested many levels deep:

```html
<!DOCTYPE html>
<html>
<body>

<h1>My Tech Blog</h1>

<p>Welcome to my blog about <a href="https://www.w3schools.com">web development</a>.</p>

</body>
</html>
```

**Expected output in browser:**

```
My Tech Blog

Welcome to my blog about web development.
                         ^^^^^^^^^^^^^^^^
                         (blue, underlined, clickable link)
```

Here the `<a>` element is nested **inside** the `<p>` element. The tree looks like:

```
html
└── body
    ├── h1  →  "My Tech Blog"
    └── p
        ├── text: "Welcome to my blog about "
        ├── a   →  "web development"
        └── text: "."
```

The `<a>` element is a **child** of `<p>`. The `<p>` element is the **parent** of `<a>` and also a **child** of `<body>`.

> **Thinking prompt:** Why does it make sense to put the `<a>` tag *inside* the `<p>` tag rather than outside it? Because the link is part of the sentence — it is content that belongs within the paragraph. Always nest elements in the order that reflects the natural structure of your content.

---

### The Golden Rule of Nesting

When you open an element inside another element, you **must close the inner element before closing the outer element**.

```html
<!-- CORRECT: Inner closes before outer -->
<p>Welcome to <a href="#">my site</a>.</p>

<!-- WRONG: Overlapping — inner closes after outer -->
<p>Welcome to <a href="#">my site</p></a>
```

Think of it like brackets in maths:
- Correct: `( [ ] )` — inner brackets closed before outer
- Wrong: `( [ ) ]` — brackets overlapping, which makes no sense

---

## Part 3 — Never Skip the End Tag

### The Browser Is Forgiving — But You Should Not Be

HTML browsers are designed to be tolerant. In many cases, if you forget a closing tag, the browser will guess what you meant and still display something.

For example, this will likely still display two paragraphs in most browsers:

```html
<html>
<body>

<p>This is a paragraph
<p>This is a paragraph

</body>
</html>
```

**What the browser might show:**

```
This is a paragraph
This is a paragraph
```

It looks fine! But this is dangerous. Here is why.

---

### Why Missing End Tags Cause Real Problems

Even though the browser guesses correctly in simple cases, relying on this behaviour creates serious risks:

**Problem 1 — Unpredictable results across browsers.** Different browsers (Chrome, Firefox, Safari, Edge) may guess differently. Your page might look correct in one browser and broken in another.

**Problem 2 — Cascading errors.** When nesting elements, a missing closing tag can confuse the browser about which element contains what. This leads to entire sections of your page rendering incorrectly.

**Problem 3 — JavaScript and CSS failures.** Code that reads your HTML structure (like JavaScript or CSS selectors) relies on properly closed elements. Missing tags can break interactivity and styling.

**Problem 4 — Validation failures.** Professional web projects use HTML validators to check code quality. Missing tags cause validation errors that can block deployment.

#### Example of Cascading Nesting Error

```html
<!-- WRONG: Missing </p> inside a larger structure -->
<body>
  <p>First paragraph
  <p>Second paragraph
  <div>
    <p>Third paragraph inside a box
  </div>
</body>
```

The browser has to guess where the `<p>` elements end. In complex layouts, this guessing frequently goes wrong — columns collapse, text appears in the wrong place, or entire sections disappear.

```html
<!-- CORRECT: All tags properly closed -->
<body>
  <p>First paragraph</p>
  <p>Second paragraph</p>
  <div>
    <p>Third paragraph inside a box</p>
  </div>
</body>
```

> **Rule to live by:** Always close your tags. Every single time. No exceptions. The habit of always closing tags will save you hours of debugging confusion throughout your career.

---

## Part 4 — Empty HTML Elements

### What is an Empty Element?

An **empty element** (also called a **void element**) is an HTML element that:
- Has **no content** between its tags
- Therefore has **no closing tag**

The most common empty element you will use early on is `<br>`.

### The `<br>` Element — Line Break

The `<br>` tag forces a **line break** — it moves the following content to the next line, without starting a whole new paragraph.

```html
<p>This is a <br> paragraph with a line break.</p>
```

**Expected output in browser:**

```
This is a
paragraph with a line break.
```

Notice: the text wraps onto the next line at the exact point where `<br>` appears.

---

### Why Does `<br>` Have No Closing Tag?

Think about it logically. A line break is not a *container* for content. It does not "hold" anything. It is simply an instruction: *"break the line here."* Since there is nothing to wrap around, there is nothing to close.

Compare this to `<p>`, which **does** hold content:

```html
<!-- <p> holds content, so it needs opening AND closing tags -->
<p>This paragraph holds content.</p>

<!-- <br> holds nothing, so it has only one tag -->
<br>
```

> **Analogy:** `<br>` is like a full stop at the end of a spoken sentence. It is just a signal — a momentary pause — not a container. You do not "open" a full stop and then "close" it.

---

### Common Empty Elements Reference

Here are the empty elements you will encounter most frequently:

| Tag | What it does |
|-----|-------------|
| `<br>` | Creates a line break within text |
| `<img>` | Embeds an image (you learned this in Lesson 2!) |
| `<input>` | Creates a form input field (covered in a later lesson) |
| `<hr>` | Creates a horizontal dividing line across the page |
| `<meta>` | Provides metadata about the page (in the `<head>` section) |
| `<link>` | Links an external stylesheet (in the `<head>` section) |

You already used `<img>` in Lesson 2. Now you know *why* it has no closing tag — because it is an empty element that simply points to an image file, rather than wrapping around content.

---

### Simple Example — Using `<br>` in a Real Context

```html
<!DOCTYPE html>
<html>
<body>

<h1>My Contact Details</h1>
<p>
  Amara Okafor<br>
  14 Victoria Island<br>
  Lagos, Nigeria<br>
  Tel: +234 801 234 5678
</p>

</body>
</html>
```

**Expected output in browser:**

```
My Contact Details

Amara Okafor
14 Victoria Island
Lagos, Nigeria
Tel: +234 801 234 5678
```

Each line is part of the **same paragraph** (one `<p>` element), but `<br>` forces each address line onto its own line. Without `<br>`, all the text would run together as one long line.

---

### Second Example — `<br>` Compared to `<p>`

Understanding *when* to use `<br>` versus `<p>` is important. Here is the difference:

```html
<!-- Using <br>: Same paragraph, different lines -->
<p>Line one.<br>Line two.<br>Line three.</p>

<!-- Using <p>: Three separate paragraphs with spacing between -->
<p>Paragraph one.</p>
<p>Paragraph two.</p>
<p>Paragraph three.</p>
```

**Expected output with `<br>`:**

```
Line one.
Line two.
Line three.
```
(No extra spacing between lines — they are all inside one paragraph.)

**Expected output with `<p>`:**

```
Paragraph one.

Paragraph two.

Paragraph three.
```
(Extra spacing between each paragraph — each is a separate block.)

> **When to use each:**
> - Use `<br>` for content that is one logical unit but needs line breaks — like an address, a poem, or song lyrics.
> - Use `<p>` for genuinely separate paragraphs of content.

---

### Common Beginner Mistake — Adding a Closing `</br>` Tag

```html
<!-- WRONG: <br> does not have a closing tag -->
<p>Line one.</br>Line two.</p>

<!-- CORRECT: <br> is an empty element, no closing tag needed -->
<p>Line one.<br>Line two.</p>
```

Some older tutorials you might find online write `<br />` (with a self-closing slash). This was the style used in a stricter version of HTML called XHTML. In modern HTML5, you can write either `<br>` or `<br />` and both work. W3Schools and modern best practice recommends simply `<br>`.

---

## Part 5 — HTML is Not Case Sensitive

### What Does "Not Case Sensitive" Mean?

**Case sensitivity** means whether the computer treats uppercase and lowercase letters as the same or different.

In HTML, the browser does **not** distinguish between uppercase and lowercase tag names. All of these mean exactly the same thing to the browser:

```html
<P>This is a paragraph.</P>
<p>This is a paragraph.</p>
<P>This is a paragraph.</p>
<p>This is a paragraph.</P>
```

All four lines produce identical output:

```
This is a paragraph.
```

The browser treats `<P>`, `<p>`, and even `<P>` with a `</p>` closer as the same element.

---

### So... Can I Write in Uppercase?

Technically? Yes. The browser will not complain.

Practically? **No. Always use lowercase.**

Here is why:

**Reason 1 — Industry standard.** The World Wide Web Consortium (W3C) — the organisation that defines HTML standards — *recommends* lowercase for HTML and *requires* lowercase for stricter document types like XHTML. Following this standard makes your code compatible with more tools and frameworks.

**Reason 2 — Readability.** Teams of developers working on the same codebase all using lowercase makes code far easier to read, scan, and maintain. Mixed-case code is jarring and hard to follow.

**Reason 3 — Consistency with other web technologies.** CSS and JavaScript *are* case sensitive in certain contexts. Developing a habit of lowercase-everywhere prevents costly mistakes when you move to those languages.

**Reason 4 — Tool compatibility.** HTML minifiers, validators, linters, and build tools all expect lowercase tags. Uppercase tags may generate warnings or fail entirely in some toolchains.

---

### The Simple Rule

> **Always write HTML tag names in lowercase. No exceptions.**

```html
<!-- WRONG: uppercase tags -->
<H1>My Heading</H1>
<P>My paragraph.</P>

<!-- WRONG: mixed case -->
<H1>My Heading</h1>
<P>My paragraph.</P>

<!-- CORRECT: all lowercase -->
<h1>My Heading</h1>
<p>My paragraph.</p>
```

**Expected output for all three:** Identical — the browser renders the same heading and paragraph regardless. But your code quality, professionalism, and compatibility are far better with the lowercase version.

---

## Part 6 — Key HTML Elements Reference

The following table lists the most fundamental HTML elements you have encountered so far. These are the building blocks you will use in almost every HTML page you ever write.

| Tag | Description | Type |
|-----|-------------|------|
| `<html>` | Defines the root of an HTML document | Parent container |
| `<body>` | Defines the document's visible body | Parent container |
| `<h1>` to `<h6>` | Defines HTML headings (h1 = largest, h6 = smallest) | Block element |
| `<p>` | Defines a paragraph | Block element |
| `<a>` | Defines a hyperlink | Inline element |
| `<img>` | Embeds an image | Empty element |
| `<br>` | Inserts a line break | Empty element |

> You will learn the difference between **block** and **inline** elements in a later lesson — it is an important concept for understanding page layout. For now, just know that block elements (like `<p>` and `<h1>`) always start on a new line, while inline elements (like `<a>`) sit within the flow of text.

---

## Guided Practice Exercises

Work through these exercises in order. Each one builds on the last.

---

### Exercise 1 — Label the Parts of an Element

Look at each HTML line below and identify: the opening tag, the content, and the closing tag.

**Line 1:**
```html
<h2>Introduction to Python</h2>
```

**Answers:**
- Opening tag: `<h2>`
- Content: `Introduction to Python`
- Closing tag: `</h2>`

---

**Line 2:**
```html
<p>Learning to code is one of the best skills you can develop.</p>
```

**Answers:**
- Opening tag: `<p>`
- Content: `Learning to code is one of the best skills you can develop.`
- Closing tag: `</p>`

---

**Line 3:**
```html
<a href="https://www.github.com">Visit GitHub</a>
```

**Answers:**
- Opening tag: `<a href="https://www.github.com">` ← note: the full opening tag includes the attribute
- Content: `Visit GitHub`
- Closing tag: `</a>`

---

**Line 4:**
```html
<br>
```

**Answers:**
- Opening tag: `<br>`
- Content: *none*
- Closing tag: *none — this is an empty element*

---

### Exercise 2 — Draw the Nesting Tree

Look at the following HTML and draw its nesting tree on paper (or type it out). Then check against the answer below.

```html
<!DOCTYPE html>
<html>
<body>

<h1>My Portfolio</h1>
<p>I am a <a href="#">web developer</a> based in Lagos.</p>
<p>Check out my work below.</p>

</body>
</html>
```

**Your nesting tree should look like this:**

```
html
└── body
    ├── h1  →  "My Portfolio"
    ├── p
    │   ├── text: "I am a "
    │   ├── a   →  "web developer"
    │   └── text: " based in Lagos."
    └── p   →  "Check out my work below."
```

**Self-check questions:**
- Which element is the root? (`html`)
- Which element is the parent of both `<p>` elements? (`body`)
- Which element is a child of the first `<p>`? (`a`)
- Are the two `<p>` elements siblings? (Yes — same parent, `body`)

---

### Exercise 3 — Fix the Broken Nesting

The following HTML has **four nesting and structural errors**. Find all four and write the corrected version.

**Broken code:**

```html
<!DOCTYPE html>
<HTML>
<body>

<h1>My Recipe Blog
<P>Welcome to my cooking website.</p>

<p>Today's recipe is <a href="#">Jollof Rice</p></a>

<br></br>

</body>
</HTML>
```

**Hint — Four errors:**
1. One tag uses incorrect case for the root element
2. One opening tag is missing its closing partner
3. The nesting order of two tags is wrong (they overlap)
4. An empty element has been given an incorrect closing tag

**Corrected code:**

```html
<!DOCTYPE html>
<html>                                         <!-- Fix 1: lowercase <html> -->
<body>

<h1>My Recipe Blog</h1>                        <!-- Fix 2: added missing </h1> -->
<p>Welcome to my cooking website.</p>          <!-- <P> could also be lowercase, but <p> was already fine as a closing tag match -->

<p>Today's recipe is <a href="#">Jollof Rice</a></p>   <!-- Fix 3: </a> before </p>, not after -->

<br>                                           <!-- Fix 4: <br> is empty — no </br> closing tag -->

</body>
</html>
```

**Expected output in browser:**

```
My Recipe Blog

Welcome to my cooking website.

Today's recipe is Jollof Rice
                  ^^^^^^^^^^^^
                  (clickable link)

[line break]
```

---

### Exercise 4 — Build a Structured Nested Page

**Objective:** Create a complete, correctly nested HTML page for a school timetable.

**Requirements:**
- Valid document structure (`<!DOCTYPE>`, `<html>`, `<body>`)
- One `<h1>` for the page title
- Three `<h2>` headings for three school days
- Under each day, at least two `<p>` elements listing subjects
- At least one `<br>` used appropriately
- All tags in lowercase
- All tags correctly closed

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>

<h1>My Weekly Timetable</h1>

<h2>Monday</h2>
<p>9:00am — Mathematics</p>
<p>11:00am — English Language<br>12:00pm — Break</p>

<h2>Wednesday</h2>
<p>9:00am — Physics</p>
<p>11:00am — Computer Science</p>

<h2>Friday</h2>
<p>9:00am — Biology</p>
<p>11:00am — Chemistry<br>12:00pm — Break</p>

</body>
</html>
```

**Expected output in browser:**

```
My Weekly Timetable

Monday

9:00am — Mathematics

9:00am — English Language
12:00pm — Break

Wednesday

9:00am — Physics
11:00am — Computer Science

Friday

9:00am — Biology

11:00am — Chemistry
12:00pm — Break
```

---

## HTML Elements Code Challenges

These challenges test your understanding of element structure, nesting, empty elements, and case sensitivity.

---

### Challenge 1 — Spot All the Elements

Look at the code below and answer the questions that follow:

```html
<!DOCTYPE html>
<html>
<body>
<h2>African Wildlife</h2>
<p>The <a href="https://www.wwf.org">African elephant</a> is the largest land animal on Earth.</p>
<img src="elephant.jpg" alt="An African elephant" width="400" height="300">
<p>Conservation efforts are critical to protecting these animals.<br>Learn more at the link above.</p>
</body>
</html>
```

**Questions:**

1. How many HTML elements are in this document (not counting `<!DOCTYPE>`)?
2. Which element is the root?
3. Which elements are empty (have no closing tag)?
4. Which element is nested inside a `<p>` element?
5. What would happen if you removed the `</p>` from the last paragraph?

**Answers:**

1. **7 elements:** `<html>`, `<body>`, `<h2>`, `<p>` (first), `<a>`, `<img>`, `<p>` (second) — plus `<br>` inside the last `<p>` = **8 elements total**
2. **`<html>`** is the root element
3. **`<img>`** and **`<br>`** are empty elements (no closing tags)
4. **`<a>`** is nested inside the first `<p>` element
5. The browser would likely still display it, but it is bad practice — the body or html tag might be treated as the end of the paragraph instead, potentially breaking CSS and JavaScript that target the element

---

### Challenge 2 — Rewrite in Correct Case and Structure

The following code is written with inconsistent case and has missing end tags. Rewrite it entirely in correct, professional HTML:

```html
<!DOCTYPE HTML>
<HTML>
<BODY>

<H1>Technology News
<H2>Artificial Intelligence</H2>
<P>AI is transforming industries worldwide.
<P>From healthcare to agriculture, the possibilities are endless.

</BODY>
</HTML>
```

**Corrected version:**

```html
<!DOCTYPE html>
<html>
<body>

<h1>Technology News</h1>
<h2>Artificial Intelligence</h2>
<p>AI is transforming industries worldwide.</p>
<p>From healthcare to agriculture, the possibilities are endless.</p>

</body>
</html>
```

**Expected output in browser:**

```
Technology News

Artificial Intelligence

AI is transforming industries worldwide.

From healthcare to agriculture, the possibilities are endless.
```

---

### Challenge 3 — Fix the Overlapping Nesting

The following code has **overlapping elements** — the most common nesting mistake beginners make. Find and fix the overlapping.

```html
<!DOCTYPE html>
<html>
<body>

<p>Visit <a href="https://www.bbc.com">BBC News</p></a> for the latest updates.

</body>
</html>
```

**What is wrong:** The `<a>` element is opened inside `<p>`, but it is closed *after* `</p>` has already closed. This is an overlap — the inner element (`<a>`) must close before the outer element (`<p>`) closes.

**Corrected version:**

```html
<!DOCTYPE html>
<html>
<body>

<p>Visit <a href="https://www.bbc.com">BBC News</a> for the latest updates.</p>

</body>
</html>
```

**Expected output in browser:**

```
Visit BBC News for the latest updates.
      ^^^^^^^^
      (blue, underlined, clickable)
```

---

### Challenge 4 — Build a Poem Page Using `<br>`

**Task:** Write an HTML page that displays the following poem correctly. Each line of the poem must appear on its own line, but **all four lines must be inside a single `<p>` element** (not four separate `<p>` tags). Use `<br>` to create the line breaks.

```
The web is built with tags and code,
Each element carrying its load,
Nested deep and structured right,
Turning words to pages bright.
```

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>

<h1>A Developer's Poem</h1>

<p>
  The web is built with tags and code,<br>
  Each element carrying its load,<br>
  Nested deep and structured right,<br>
  Turning words to pages bright.
</p>

</body>
</html>
```

**Expected output in browser:**

```
A Developer's Poem

The web is built with tags and code,
Each element carrying its load,
Nested deep and structured right,
Turning words to pages bright.
```

All four lines sit inside one paragraph block, with `<br>` forcing each line onto a new line while keeping them in the same paragraph.

---

### Challenge 5 — The Full Nesting Analysis

Study this more complex page and answer the questions:

```html
<!DOCTYPE html>
<html>
<body>

<h1>My Coding Journey</h1>

<h2>Languages I Am Learning</h2>
<p>I started with <a href="https://www.w3schools.com/html">HTML</a> and <a href="https://www.w3schools.com/css">CSS</a>.</p>
<p>Next, I will learn <a href="https://www.w3schools.com/js">JavaScript</a>.</p>

<h2>My First Project</h2>
<p>I built a personal page.<br>It used headings, paragraphs, links, and images.</p>

</body>
</html>
```

**Questions:**

1. Draw the complete nesting tree for this document.
2. How many `<a>` elements are on this page?
3. How many `<p>` elements are on this page?
4. Which `<p>` element contains a `<br>`?
5. Which elements are siblings of `<h1>`?

**Answers:**

**1. Nesting tree:**
```
html
└── body
    ├── h1   →  "My Coding Journey"
    ├── h2   →  "Languages I Am Learning"
    ├── p
    │   ├── text: "I started with "
    │   ├── a    →  "HTML"
    │   ├── text: " and "
    │   └── a    →  "CSS"
    ├── p
    │   ├── text: "Next, I will learn "
    │   └── a    →  "JavaScript"
    ├── h2   →  "My First Project"
    └── p
        ├── text: "I built a personal page."
        ├── br
        └── text: "It used headings, paragraphs, links, and images."
```

**2.** There are **3** `<a>` elements (HTML, CSS, JavaScript).

**3.** There are **3** `<p>` elements.

**4.** The **third `<p>`** (under "My First Project") contains the `<br>`.

**5.** Siblings of `<h1>` are: both `<h2>` elements and all three `<p>` elements — because they all share `<body>` as their parent.

---

## Mini Project — Build a Multi-Section Article Page

Now you will combine everything from Lessons 1 through 3 into a polished, correctly structured article page with proper nesting throughout.

---

### Project Overview

**Project name:** My HTML Knowledge Base Article  
**Goal:** A fully valid, correctly nested HTML article page on any topic you choose, demonstrating mastery of document structure, element anatomy, nesting, empty elements, and correct case usage.

---

### Stage 1 — The Document Skeleton

Start with the correctly structured skeleton:

```html
<!DOCTYPE html>
<html>
<body>

<!-- Article content will go here -->

</body>
</html>
```

**Milestone check:** Open in browser → blank white page with no errors.

---

### Stage 2 — Add the Article Structure

Choose any topic you are interested in (technology, sport, cooking, science, history). Build out the structure using headings and paragraphs:

```html
<!DOCTYPE html>
<html>
<body>

<h1>The History of the Internet</h1>

<h2>Early Beginnings</h2>
<p>The internet began as a US military research project called ARPANET in the late 1960s.</p>
<p>It was designed to allow multiple computers to communicate on a single network.</p>

<h2>The World Wide Web</h2>
<p>In 1989, British scientist Tim Berners-Lee invented the World Wide Web.</p>
<p>He proposed a system of interlinked hypertext documents accessible over the internet.</p>

<h2>The Internet Today</h2>
<p>Today, over 5 billion people use the internet worldwide.</p>
<p>It powers commerce, communication, education, and entertainment on a global scale.</p>

</body>
</html>
```

**Milestone output:**

```
The History of the Internet

Early Beginnings

The internet began as a US military research project...
It was designed to allow multiple computers...

The World Wide Web

In 1989, British scientist Tim Berners-Lee...
He proposed a system of interlinked hypertext...

The Internet Today

Today, over 5 billion people use the internet...
It powers commerce, communication, education...
```

---

### Stage 3 — Add Links, an Image, and Line Breaks

Enhance your article with links, an image, and at least one appropriate `<br>`:

```html
<!-- Add this after your first <h2> paragraph block -->
<p>Learn more at <a href="https://www.internetsociety.org">The Internet Society</a>.</p>

<!-- Add an image after your <h1> tag -->
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Internet_map_1024.jpg/320px-Internet_map_1024.jpg"
     alt="A visual map of internet connections worldwide"
     width="320"
     height="213">

<!-- Use <br> to format a caption under the image -->
<p>
  Image: A visual map of internet traffic.<br>
  Source: Wikimedia Commons.
</p>
```

---

### Stage 4 — Final Complete Page

Your finished article page should look like this:

```html
<!DOCTYPE html>
<html>
<body>

<h1>The History of the Internet</h1>

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Internet_map_1024.jpg/320px-Internet_map_1024.jpg"
     alt="A visual map of internet connections worldwide"
     width="320"
     height="213">

<p>
  Image: A visual map of internet traffic.<br>
  Source: Wikimedia Commons.
</p>

<h2>Early Beginnings</h2>
<p>The internet began as a US military research project called ARPANET in the late 1960s.</p>
<p>It was designed to allow multiple computers to communicate on a single network.</p>
<p>Learn more at <a href="https://www.internetsociety.org">The Internet Society</a>.</p>

<h2>The World Wide Web</h2>
<p>In 1989, British scientist Tim Berners-Lee invented the <a href="https://www.w3.org">World Wide Web</a>.</p>
<p>He proposed a system of interlinked hypertext documents accessible over the internet.</p>

<h2>The Internet Today</h2>
<p>Today, over 5 billion people use the internet worldwide.</p>
<p>It powers commerce, communication, education, and entertainment on a global scale.</p>

</body>
</html>
```

---

### Stage 5 — Nesting Tree of Your Final Page

Draw the complete nesting tree of your finished page. This is excellent practice for visualising structure:

```
html
└── body
    ├── h1      →  "The History of the Internet"
    ├── img     [empty — no children]
    ├── p
    │   ├── text: "Image: A visual map of internet traffic."
    │   ├── br   [empty]
    │   └── text: "Source: Wikimedia Commons."
    ├── h2      →  "Early Beginnings"
    ├── p       →  "The internet began..."
    ├── p       →  "It was designed..."
    ├── p
    │   ├── text: "Learn more at "
    │   ├── a   →  "The Internet Society"
    │   └── text: "."
    ├── h2      →  "The World Wide Web"
    ├── p
    │   ├── text: "In 1989, British scientist Tim Berners-Lee invented the "
    │   ├── a   →  "World Wide Web"
    │   └── text: "."
    ├── p       →  "He proposed a system..."
    ├── h2      →  "The Internet Today"
    ├── p       →  "Today, over 5 billion..."
    └── p       →  "It powers commerce..."
```

---

### Stage 6 — Reflection Questions

1. What is the difference between a tag and an element?
2. In your finished project, identify one parent element, one child element, and two sibling elements.
3. You used both `<img>` and `<br>` in this project. Why does neither of them need a closing tag?
4. If someone opened your page in Internet Explorer 6 from the year 2001, what could go wrong if you had forgotten closing tags?
5. What would happen to the image caption paragraph if you removed all the `<br>` tags?

**Optional extension challenges:**
- Add a `<h3>` subsection under one of your `<h2>` headings
- Nest a link inside one of your image captions
- Add a second image and write a proper `alt` description for it
- Create a second HTML file (`timeline.html`) and link to it from your main article

---

## Common Beginner Mistakes — Full Summary for This Lesson

**Element Structure Mistakes:**
- Confusing a tag (`<p>`) with an element (`<p>content</p>`) — they are not the same thing
- Forgetting the forward slash `/` in closing tags: writing `<p` again instead of `</p>`
- Writing the attribute in the closing tag: `</a href="#">` — attributes only go in opening tags

**Nesting Mistakes:**
- Overlapping elements — closing the outer element before the inner one: `<p><a>text</p></a>`
- Skipping levels of nesting — putting `<h1>` directly inside `<p>` makes no semantic sense
- Putting content outside `<body>` — all visible content must be inside `<body>`

**Empty Element Mistakes:**
- Adding a closing tag to `<br>`: `<br></br>` — empty elements have no closing tags
- Adding a closing tag to `<img>`: `<img src="x.jpg"></img>` — also wrong
- Confusing `<br>` (line break within a paragraph) with `<p>` (a separate paragraph block)

**Case Sensitivity Mistakes:**
- Writing `<H1>` or `<BODY>` instead of `<h1>` and `<body>`
- Mixing cases: `<H1>Heading</h1>` — always match case, and always use lowercase
- Thinking uppercase HTML will break in all browsers — it will not, but it is still wrong practice

---

## Reflection Questions

Take a moment to test your understanding before moving on:

1. In your own words, what are the three parts of an HTML element?
2. What does "nesting" mean in HTML? Give a real-world analogy of your own.
3. If you forget to close a `</p>` tag, the browser may still display the page. Why is this still dangerous?
4. What is the difference between `<br>` and `<p>` when it comes to how they handle line breaks?
5. Name three HTML empty elements and explain what each does.
6. The browser does not care whether you use `<H1>` or `<h1>`. So why should *you* care?
7. Look at this element: `<a href="https://example.com">Click here</a>`. Where does the element begin? Where does it end? What is the content?
8. You are reviewing a colleague's HTML and find this: `<p>Hello <strong>world</p></strong>`. What is wrong and how do you fix it?

---

## Lesson Completion Checklist

Use this checklist before moving to Lesson 4:

- [ ] I can name all three parts of an HTML element: opening tag, content, and closing tag
- [ ] I understand that a **tag** and an **element** are not the same thing
- [ ] I can explain what "nesting" means and give an example
- [ ] I can draw a nesting tree for a given HTML document
- [ ] I understand that `<html>` is the root element of every document
- [ ] I understand that `<body>` holds all visible content
- [ ] I know the parent–child–sibling relationship between elements
- [ ] I know the Golden Rule of nesting: inner elements must close before outer elements
- [ ] I understand why missing closing tags are dangerous even when the browser forgives them
- [ ] I can identify and correctly use the `<br>` empty element
- [ ] I know which elements are empty elements and why they have no closing tag
- [ ] I know the difference between `<br>` and `<p>` for line breaks
- [ ] I understand that HTML is not case sensitive but always use lowercase
- [ ] I completed all four guided exercises
- [ ] I completed all five code challenges
- [ ] I built the multi-section article project
- [ ] I drew the nesting tree for my project page
- [ ] I answered all reflection questions

---

## Lesson Summary

In Lesson 3 you went deeper than just *using* HTML — you now truly understand its fundamental building block: **the element**.

**The HTML Element:** Every element consists of an opening tag, content, and a closing tag. A tag alone is not an element — the complete package is.

**Nesting:** HTML documents are built by nesting elements inside other elements. The `<html>` element is the root; `<body>` lives inside `<html>`; all visible content lives inside `<body>`. Inner elements always close before their outer parents.

**Never Skip End Tags:** Browsers are forgiving, but missing closing tags lead to unpredictable rendering across browsers, broken CSS and JavaScript, and validation failures. Always close your tags.

**Empty Elements:** Some elements like `<br>` and `<img>` have no content and therefore no closing tag. These are called empty or void elements.

**Case Insensitivity:** HTML tags work in any case, but always write them in lowercase — it is the industry standard, improves readability, and ensures compatibility with other technologies.

> **Coming up in Lesson 4:** You will learn about **HTML Attributes** — the extra information you add inside opening tags. You already used attributes (`href`, `src`, `alt`, `width`, `height`) without fully studying them. In the next lesson, you will master exactly how attributes work, the rules for writing them correctly, and the most important global attributes used on every kind of element.

---

*Sources: W3Schools HTML Elements (https://www.w3schools.com/html/html_elements.asp) and HTML Elements Code Challenges (https://www.w3schools.com/html/html_challenges_elements.asp)*
