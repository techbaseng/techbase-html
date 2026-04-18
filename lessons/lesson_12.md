---
render_with_liquid: false
title: "Lesson 12: HTML Styles — Introduction to CSS (Cascading Style Sheets)"
nav_order: 12
---

# Lesson 12: HTML Styles — Introduction to CSS (Cascading Style Sheets)

---

## Lesson Introduction

So far in this HTML course, you have been building the **structure** of web pages — headings, paragraphs, links, images, colours, and more. But your pages still look plain and basic. That is about to change!

In this lesson, you will meet **CSS** — the language that makes websites look beautiful. CSS controls colours, fonts, sizes, spacing, borders, backgrounds, and much more. You will also learn the **three different ways** to add CSS to your HTML, and you will practise using the most important CSS properties that every web developer uses daily.

By the end of this lesson, you will be able to style an entire webpage using CSS, understand how each styling method works, and confidently use properties like `color`, `font-family`, `font-size`, `border`, `padding`, and `margin`.

---

## Prerequisite Concepts

Before we begin, let's make sure you are comfortable with these ideas from earlier lessons:

- **HTML elements** — things like `<h1>`, `<p>`, `<body>` that hold your content
- **HTML attributes** — extra information placed inside an opening tag, like `style="..."` or `href="..."`
- **The `<head>` section** — the invisible part of an HTML page that holds settings and linked files
- **The `<body>` section** — the visible part of the page that holds your content

If any of those feel unfamiliar, quickly review Lessons 3–5 before continuing here.

---

## Part 1: Conceptual Understanding — What is CSS?

### 1.1 What Does CSS Stand For?

**CSS** stands for **Cascading Style Sheets**.

Let's break that down word by word:

- **Style Sheets** — A "sheet" (or file) of instructions that describe how things should *look*. Think of it like a design manual.
- **Cascading** — This is the clever part. Styles "cascade" (flow downward) from parent elements to their children. For example, if you tell the `<body>` element to use blue text, ALL text inside the body — headings, paragraphs, links — will automatically become blue, unless you specifically tell one of them to be a different colour.

> **Analogy:** Imagine a parent company sends a dress-code policy to all its branches. Every branch follows that policy automatically — unless a specific branch has its own special rule that overrides it. CSS works exactly the same way.

### 1.2 What Problem Does CSS Solve?

Before CSS, if you wanted to make every heading on your website red, you would have to write `color="red"` inside every single `<h1>` tag on every single page. If you had 500 pages, you would have to edit 500 places!

CSS solves this by letting you write your styling instructions **once** in one place, and that one place controls the look of your entire website. Change it once — the whole site updates.

> **Real-world use:** Professional websites like news portals, e-commerce shops, banking apps, and school websites all use CSS to control their visual design. The styling rules are written once and applied across hundreds of pages automatically.

### 1.3 What Can CSS Control?

CSS can control a very wide range of visual properties. Here is a quick overview:

- **Text colour** — make your headings blue, paragraphs red, links green
- **Font** — choose the typeface (Verdana, Arial, Courier, etc.)
- **Font size** — make headings large and body text smaller
- **Background colour or image** — change the colour of the whole page or a specific box
- **Borders** — draw lines around elements
- **Padding** — add space *inside* an element, between the content and its border
- **Margin** — add space *outside* an element, pushing other elements away
- **Layout and positioning** — control where elements sit on the screen
- **Different displays for different screen sizes** — look different on mobile vs desktop

In this lesson, we will focus on the most essential and commonly used CSS properties to build a solid foundation.

---

## Part 2: The Three Ways to Add CSS to HTML

CSS can be added to your HTML in **three different ways**. Each has a specific use case, and it's important to understand all three.

### Method 1: Inline CSS

**What is it?** Inline CSS is styling written directly inside an HTML element's opening tag using the `style` attribute.

**When to use it?** Use inline CSS when you want to style just one specific element differently from everything else on the page. It is the most targeted approach.

**How it works:**

```html
<tagname style="property: value;">Content here</tagname>
```

- `style` — the attribute name (this always stays the same)
- `property` — the CSS property you want to change (e.g., `color`, `font-size`)
- `value` — the value you want to apply (e.g., `blue`, `20px`)
- The colon `:` separates the property from its value
- The semicolon `;` ends each style rule (important when you have more than one!)

#### Simple Example — Inline CSS

```html
<h1 style="color:blue;">A Blue Heading</h1>

<p style="color:red;">A red paragraph.</p>
```

**Expected Output:**
```
A Blue Heading       ← displayed in blue text
A red paragraph.     ← displayed in red text
```

> **What happened?** The `style` attribute on the `<h1>` tag told the browser: "Make this specific heading blue." The `style` attribute on the `<p>` tag said: "Make this specific paragraph red." Only those two elements are affected.

#### Second Example — Multiple Inline Styles

You can apply more than one style at once by separating them with semicolons:

```html
<p style="color:green; font-size:20px;">This paragraph is green and bigger.</p>
```

**Expected Output:**
```
This paragraph is green and bigger.   ← green, larger text
```

> **Thinking prompt:** What happens if you remove the semicolon between the two styles? Try it and observe the result!

---

### Method 2: Internal CSS

**What is it?** Internal CSS is written inside a `<style>` element in the `<head>` section of the HTML page.

**When to use it?** Use internal CSS when you want to style an entire single HTML page consistently. All elements of the same type (e.g., every `<p>`, every `<h1>`) on that page will be styled the same way with one rule.

**How it works:**

You write CSS rules inside `<style>` tags in the `<head>`. A CSS rule looks like this:

```css
selector {
  property: value;
}
```

- **Selector** — tells CSS *which* HTML elements to style (e.g., `h1` targets all `<h1>` elements, `p` targets all `<p>` elements, `body` targets the whole page body)
- **Curly braces `{ }`** — wrap the styling instructions for that selector
- **Property: value;** — the actual styling rule

#### Simple Example — Internal CSS

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background-color: powderblue;
    }
    h1 {
      color: blue;
    }
    p {
      color: red;
    }
  </style>
</head>
<body>

  <h1>This is a heading</h1>
  <p>This is a paragraph.</p>

</body>
</html>
```

**Expected Output:**
```
Page background: light blue (powderblue)
"This is a heading"   ← blue text
"This is a paragraph." ← red text
```

Let's walk through every line:

- `<style>` — opens the CSS rule block inside the HTML head
- `body { background-color: powderblue; }` — targets the entire `<body>` element and sets its background colour to a soft blue called "powderblue"
- `h1 { color: blue; }` — targets EVERY `<h1>` element on this page and makes the text blue
- `p { color: red; }` — targets EVERY `<p>` element on this page and makes the text red
- `</style>` — closes the style block

> **Key difference from Inline CSS:** With internal CSS, one rule like `p { color: red; }` automatically applies to ALL paragraph elements on that page. You didn't have to add `style="color:red;"` to every individual `<p>` tag!

---

### Method 3: External CSS

**What is it?** External CSS is written in a completely separate file (with a `.css` extension) and then linked to your HTML page using the `<link>` element.

**When to use it?** This is the **most powerful and most recommended method** for real websites. One external CSS file can control the styling of an **entire website** — all pages, all at once. If you update the file, every page updates automatically.

**How it works:**

Step 1 — In your HTML file, add a `<link>` tag inside the `<head>` section:

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <h1>This is a heading</h1>
  <p>This is a paragraph.</p>

</body>
</html>
```

Step 2 — Create a separate file named `styles.css` and write your CSS rules inside it:

```css
body {
  background-color: powderblue;
}
h1 {
  color: blue;
}
p {
  color: red;
}
```

**Expected Output:**
```
Page background: light blue (powderblue)
"This is a heading"    ← blue text
"This is a paragraph." ← red text
```

The visual result is identical to the internal CSS method — but now the styling lives in its own file!

> **Why is this so powerful?** Imagine your website has 200 HTML pages. Every page links to `styles.css`. You want to change all headings from blue to green. You just open `styles.css`, change `color: blue;` to `color: green;`, save it — and all 200 pages instantly have green headings. Without external CSS, you would have to edit 200 files!

#### Understanding the `<link>` Tag

```html
<link rel="stylesheet" href="styles.css">
```

- `<link>` — this HTML element creates a connection between your HTML file and another file
- `rel="stylesheet"` — tells the browser that the linked file is a CSS stylesheet
- `href="styles.css"` — specifies the path/location of the CSS file

#### Linking to External CSS — Three Path Options

You can link to a CSS file using three types of paths:

**Option 1 — Full URL (for external websites):**
```html
<link rel="stylesheet" href="https://www.w3schools.com/html/styles.css">
```

**Option 2 — Relative path from a folder on the same website:**
```html
<link rel="stylesheet" href="/html/styles.css">
```
(This means: go to the `html` folder at the root of the website, then find `styles.css`)

**Option 3 — Same folder as the HTML file (most common for beginners):**
```html
<link rel="stylesheet" href="styles.css">
```
(This means: find `styles.css` in the same folder as this HTML file)

> **Important:** The external CSS file must be saved with the `.css` file extension and must NOT contain any HTML code — only CSS rules.

---

### Comparison Table: The Three CSS Methods

| Method | Where it's written | What it affects | Best use case |
|---|---|---|---|
| Inline | Inside the HTML tag's `style` attribute | Only that single element | Quick one-off styling |
| Internal | Inside `<style>` tags in `<head>` | All matching elements on one page | Single-page styling |
| External | A separate `.css` file, linked with `<link>` | All pages that link to it | Multi-page websites |

> **Tip:** In professional web development, **External CSS** is almost always the preferred method. However, for learning and quick demos, Inline and Internal CSS are perfectly fine.

---

## Part 3: Core CSS Properties

Now that you know how to add CSS, let's learn the most important CSS properties you will use constantly.

### 3.1 The `color` Property — Text Colour

The `color` property sets the **colour of the text** inside an element.

```css
h1 {
  color: blue;
}
```

You can specify colours in several ways:
- **Named colours:** `red`, `blue`, `green`, `orange`, `powderblue`, `tomato`, etc.
- **Hex codes:** `#ff0000` (red), `#0000ff` (blue)
- **RGB values:** `rgb(255, 0, 0)` (red)

For this lesson, we will use named colours since they are the easiest to read.

#### Example

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    h1 { color: navy; }
    p  { color: tomato; }
  </style>
</head>
<body>
  <h1>Welcome to My Page</h1>
  <p>This is a stylish paragraph.</p>
</body>
</html>
```

**Expected Output:**
```
"Welcome to My Page"      ← dark navy blue text
"This is a stylish paragraph."  ← tomato red text
```

---

### 3.2 The `font-family` Property — Choosing the Font (Typeface)

The `font-family` property specifies which **typeface/font** the text should use.

```css
p {
  font-family: verdana;
}
```

Common font choices:
- `verdana` — clean and modern, great for body text
- `courier` — looks like a typewriter, often used for code
- `arial` — very commonly used, clean sans-serif
- `times new roman` — traditional serif font
- `georgia` — elegant serif font

#### Example

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    h1 {
      color: blue;
      font-family: verdana;
    }
    p {
      color: red;
      font-family: courier;
    }
  </style>
</head>
<body>
  <h1>This is a heading</h1>
  <p>This is a paragraph.</p>
</body>
</html>
```

**Expected Output:**
```
"This is a heading"    ← blue, Verdana font
"This is a paragraph." ← red, Courier (typewriter-style) font
```

> **Thinking prompt:** What happens if you switch the font-family values between h1 and p? What does it look like?

---

### 3.3 The `font-size` Property — Text Size

The `font-size` property controls how **large or small** the text appears.

```css
h1 {
  font-size: 300%;
}
```

You can specify size in several units:
- `%` (percentage) — relative to the default browser size (usually 16px). `200%` means twice as big.
- `px` (pixels) — an exact number of pixels. `24px` is 24 pixels tall.
- `em` — relative to the current font size. `2em` means twice the current size.

For beginners, `px` and `%` are the easiest to understand.

#### Example

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    h1 {
      color: blue;
      font-family: verdana;
      font-size: 300%;
    }
    p {
      color: red;
      font-family: courier;
      font-size: 160%;
    }
  </style>
</head>
<body>
  <h1>This is a heading</h1>
  <p>This is a paragraph.</p>
</body>
</html>
```

**Expected Output:**
```
This is a heading      ← blue, Verdana, VERY LARGE (300% of default)
This is a paragraph.   ← red, Courier, medium-large (160% of default)
```

> **Thinking prompt:** What happens if you change `300%` to `50%`? The heading would be smaller than normal default text! Try it.

---

### 3.4 The `border` Property — Drawing a Box Around Elements

The `border` property draws a visible rectangular line around an HTML element.

The full `border` shorthand looks like this:

```css
p {
  border: 2px solid powderblue;
}
```

Breaking that value apart:
- `2px` — the **width** (thickness) of the border line in pixels
- `solid` — the **style** of the border line (other options: `dashed`, `dotted`, `double`)
- `powderblue` — the **colour** of the border

#### Example

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    p {
      border: 2px solid powderblue;
    }
  </style>
</head>
<body>
  <p>This paragraph has a border around it.</p>
  <p>This one does too!</p>
</body>
</html>
```

**Expected Output:**
```
┌─────────────────────────────────────────────┐
│  This paragraph has a border around it.     │
└─────────────────────────────────────────────┘

┌─────────────────────────────────────────────┐
│  This one does too!                         │
└─────────────────────────────────────────────┘
```
(Both paragraphs have a 2-pixel-wide solid light-blue border)

> **Tip:** You can apply borders to nearly any HTML element — headings, divs, images, tables, and more!

---

### 3.5 The `padding` Property — Space Inside the Border

**Padding** is the space between the **content** (text/image) and the **border** of an element.

Think of it like the cushioning inside a box — the padding keeps the content from touching the walls.

```css
p {
  border: 2px solid powderblue;
  padding: 30px;
}
```

- `30px` means add 30 pixels of space on ALL four sides (top, right, bottom, left) between the text and the border.

#### Example — Before and After Padding

Without padding:
```
┌──────────────────────────────┐
│This text is right at the edge│
└──────────────────────────────┘
```

With `padding: 30px`:
```
┌────────────────────────────────────┐
│                                    │
│   This text has breathing room.    │
│                                    │
└────────────────────────────────────┘
```

#### Full Example Code

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    p {
      border: 2px solid powderblue;
      padding: 30px;
    }
  </style>
</head>
<body>
  <p>This paragraph has a border and padding.</p>
</body>
</html>
```

**Expected Output:**
```
A paragraph element with a light-blue border and 30 pixels of inner breathing space on all sides.
```

---

### 3.6 The `margin` Property — Space Outside the Border

**Margin** is the space **outside** the border of an element — it pushes other elements away.

Think of it like the gap between two picture frames hanging on a wall. The margin keeps them from touching each other.

```css
p {
  border: 2px solid powderblue;
  margin: 50px;
}
```

- `50px` means add 50 pixels of space on ALL four sides OUTSIDE the border, between this element and anything near it.

#### Padding vs. Margin — The Key Difference

This is one of the most important concepts in CSS layout:

```
┌────────────────────────────────────────────────────────┐
│  MARGIN (outside space — pushes other elements away)   │
│  ┌──────────────────────────────────────────────────┐  │
│  │  BORDER (the visible line)                       │  │
│  │  ┌────────────────────────────────────────────┐  │  │
│  │  │  PADDING (inside space — cushions content) │  │  │
│  │  │  ┌──────────────────────────────────────┐  │  │  │
│  │  │  │  CONTENT (your text or image)        │  │  │  │
│  │  │  └──────────────────────────────────────┘  │  │  │
│  │  └────────────────────────────────────────────┘  │  │
│  └──────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────┘
```

> **Analogy:** Think of a framed painting hanging on a wall.
> - The **painting itself** = the content
> - The **matte board** inside the frame around the painting = padding
> - The **frame** = border
> - The **wall space** around the frame = margin

#### Full Example Code

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    p {
      border: 2px solid powderblue;
      margin: 50px;
    }
  </style>
</head>
<body>
  <p>This paragraph has a border and a large margin outside.</p>
  <p>This second paragraph is pushed far away from the first.</p>
</body>
</html>
```

**Expected Output:**
```
(50px gap from top of page)
┌──────────────────────────────────────────────────────┐
│ This paragraph has a border and a large margin.      │
└──────────────────────────────────────────────────────┘
(50px gap between paragraphs)
┌──────────────────────────────────────────────────────┐
│ This second paragraph is pushed far away.            │
└──────────────────────────────────────────────────────┘
(50px gap from bottom)
```

---

### 3.7 The `background-color` Property

The `background-color` property sets the **background colour** of an element (or the whole page if applied to `body`).

```css
body {
  background-color: lightgrey;
}

h1 {
  background-color: yellow;
}
```

#### Example

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background-color: lightgrey;
    }
    h1 {
      background-color: yellow;
    }
    p {
      background-color: white;
    }
  </style>
</head>
<body>
  <h1>Yellow Background Heading</h1>
  <p>White background paragraph on a grey page.</p>
</body>
</html>
```

**Expected Output:**
```
Entire page background: light grey
"Yellow Background Heading" ← has a yellow background highlight
"White background paragraph..." ← white background box
```

---

## Part 4: Combining CSS Properties

Now let's see all these properties working together in one complete example.

### Combined Example — Complete Styled Page

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background-color: powderblue;
    }
    h1 {
      color: blue;
      font-family: verdana;
      font-size: 300%;
    }
    p {
      color: red;
      font-family: courier;
      font-size: 160%;
      border: 2px solid powderblue;
      padding: 30px;
      margin: 50px;
    }
  </style>
</head>
<body>

  <h1>Welcome to My Styled Page</h1>
  <p>This is the first paragraph. It has colour, font, size, a border, padding, and margin.</p>
  <p>This is the second paragraph. It gets all the same styles automatically.</p>

</body>
</html>
```

**Expected Output:**
```
Page background: powderblue

"Welcome to My Styled Page"
  → blue text, Verdana font, very large (300%)

(50px gap)
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│   This is the first paragraph. It has colour, font, size,     │  ← 30px padding
│   a border, padding, and margin.                               │
│                                                                │
└────────────────────────────────────────────────────────────────┘
                 ← text: red, Courier font, medium-large (160%)
(50px gap)
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│   This is the second paragraph. It gets all the same          │
│   styles automatically.                                        │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

> **Notice:** You only wrote the CSS rules once, but BOTH paragraphs got all the styling automatically. This is the power of CSS!

---

## Part 5: HTML Style Tags Reference

Here is a quick reference for the HTML tags used with CSS:

| Tag | What it does |
|---|---|
| `<style>` | Defines internal CSS style rules inside the `<head>` section |
| `<link>` | Creates a link to an external CSS file (or other resources) |

---

## Part 6: Guided Practice Exercises

Now it's time to practise! Work through each exercise carefully. Read the objective, write your own code, then check the expected output.

---

### Exercise 1 — Warm-Up: Inline CSS Practice

**Objective:** Use inline CSS to change the appearance of individual elements.

**Scenario:** You are building a simple webpage for a science club announcement.

**Steps:**
1. Create an `<h1>` element that says "Science Club News" with blue text.
2. Create a `<p>` element that says "Our next meeting is on Friday." with dark green text.
3. Create another `<p>` that says "Everyone is welcome!" with orange text and a font size of 20px.

**Your code:**

```html
<!DOCTYPE html>
<html>
<body>

  <h1 style="color:blue;">Science Club News</h1>
  <p style="color:darkgreen;">Our next meeting is on Friday.</p>
  <p style="color:orange; font-size:20px;">Everyone is welcome!</p>

</body>
</html>
```

**Expected Output:**
```
"Science Club News"           ← blue text (large heading)
"Our next meeting is on Friday." ← dark green text
"Everyone is welcome!"        ← orange text, slightly larger than default
```

**Self-check Questions:**
- Does each element only affect that single line?
- What happens if you remove the semicolon between `color:orange` and `font-size:20px`?
- Could you add a `font-family` to any of these inline styles?

**What-if challenge:** What happens if you add `background-color:yellow;` to the first paragraph's inline style?

---

### Exercise 2 — Internal CSS for a Student Profile Page

**Objective:** Use an internal `<style>` block to style an entire single HTML page.

**Scenario:** You are building a simple student profile page. Use internal CSS to make it look polished.

**Steps:**
1. Set the page background colour to `lightyellow`.
2. Make all `<h1>` elements navy blue, using the Verdana font.
3. Make all `<h2>` elements dark green.
4. Make all `<p>` elements dark grey (`#333333` or `darkgrey`), using the Arial font with a font size of 18px.
5. Add a `2px solid navy` border around all `<p>` elements, with `15px` padding.

**Your code:**

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background-color: lightyellow;
    }
    h1 {
      color: navy;
      font-family: verdana;
    }
    h2 {
      color: darkgreen;
    }
    p {
      color: darkgrey;
      font-family: arial;
      font-size: 18px;
      border: 2px solid navy;
      padding: 15px;
    }
  </style>
</head>
<body>

  <h1>Student Profile</h1>
  <h2>Personal Information</h2>
  <p>Name: Amara Johnson</p>
  <p>School: Greenfield Academy</p>
  <h2>Interests</h2>
  <p>Coding, Mathematics, and Robotics</p>

</body>
</html>
```

**Expected Output:**
```
Page background: light yellow

"Student Profile"         ← navy, Verdana (large H1 heading)
"Personal Information"    ← dark green (H2 heading)
┌────────────────────────────────┐
│  Name: Amara Johnson           │  ← dark grey, Arial 18px, navy border, 15px padding
└────────────────────────────────┘
┌────────────────────────────────┐
│  School: Greenfield Academy    │
└────────────────────────────────┘
"Interests"               ← dark green (H2 heading)
┌────────────────────────────────┐
│  Coding, Mathematics, Robotics │
└────────────────────────────────┘
```

**Self-check Questions:**
- How many `<p>` elements did you have to add the border to manually? (Answer: zero — CSS did it automatically!)
- What is the difference between what `padding` and `margin` would do here?
- What would you change to make the border red instead of navy?

**What-if challenge:** Add `margin: 20px;` to the `p` rule. What changes about the spacing between paragraphs?

---

### Exercise 3 — External CSS File Setup

**Objective:** Create a two-file project (HTML + CSS) using the external CSS method.

**Scenario:** You are starting a mini website for a fictional bakery.

**Steps:**

First, create your HTML file (`bakery.html`):

```html
<!DOCTYPE html>
<html>
<head>
  <title>Sweet Treats Bakery</title>
  <link rel="stylesheet" href="bakery.css">
</head>
<body>

  <h1>Sweet Treats Bakery</h1>
  <h2>Our Menu</h2>
  <p>Chocolate Cake — ₦2,500</p>
  <p>Croissants — ₦800</p>
  <p>Sourdough Bread — ₦1,200</p>
  <h2>Opening Hours</h2>
  <p>Monday to Saturday: 7am – 8pm</p>
  <p>Sunday: 9am – 5pm</p>

</body>
</html>
```

Then, create your CSS file (`bakery.css`) in the same folder:

```css
body {
  background-color: #fff8f0;
  font-family: georgia;
}

h1 {
  color: #8B0000;
  font-size: 250%;
}

h2 {
  color: #d2691e;
  font-size: 150%;
}

p {
  color: #333;
  font-size: 18px;
  border-left: 4px solid #d2691e;
  padding: 8px 16px;
  margin: 10px 0;
}
```

**Expected Output:**
```
Page background: warm cream colour
Font throughout: Georgia (elegant serif)

"Sweet Treats Bakery"     ← dark red, very large
"Our Menu"                ← chocolate brown, medium-large
│ Chocolate Cake — ₦2,500  ← dark text, left brown border bar
│ Croissants — ₦800
│ Sourdough Bread — ₦1,200
"Opening Hours"           ← chocolate brown, medium-large
│ Monday to Saturday...
│ Sunday...
```

**Self-check Questions:**
- What is the file extension for the CSS file?
- What HTML tag links the HTML file to the CSS file?
- What attribute on the `<link>` tag tells the browser it is a stylesheet?
- If you added a third HTML page (e.g., `contact.html`) and linked the same `bakery.css`, what would happen?

---

## Part 7: Mini Project — Personal Hobby Page with Full CSS Styling

Now let's combine everything you have learned into one complete mini project!

### Project Brief

Build a "My Hobbies" personal page that is fully styled using **internal CSS** (since we are practising in one file). The page must demonstrate all the CSS properties learned in this lesson.

### Stage 1: Setup — Basic HTML Structure

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Hobbies Page</title>
</head>
<body>

  <h1>My Favourite Hobbies</h1>
  <p>Welcome to my hobbies page. Here I share what I love to do in my free time.</p>

  <h2>Hobby 1: Coding</h2>
  <p>I love building websites and solving programming challenges. It sharpens my logical thinking.</p>

  <h2>Hobby 2: Reading</h2>
  <p>I enjoy science fiction and history books. They expand my imagination and knowledge.</p>

  <h2>Hobby 3: Photography</h2>
  <p>Capturing moments with a camera teaches me to observe the world more carefully.</p>

</body>
</html>
```

**Milestone 1 Output:** Plain unstyled page — text, headings, paragraphs. No colour, no fonts, no borders. Just structure.

---

### Stage 2: Add Internal CSS Styling

Now add a `<style>` block in the `<head>` section:

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Hobbies Page</title>
  <style>

    /* Page background */
    body {
      background-color: #f0f4f8;
      font-family: arial;
    }

    /* Main heading */
    h1 {
      color: #1a1a2e;
      font-family: verdana;
      font-size: 280%;
    }

    /* Sub-headings */
    h2 {
      color: #16213e;
      font-size: 160%;
      border-bottom: 2px solid #0f3460;
    }

    /* Paragraphs */
    p {
      color: #444;
      font-size: 18px;
      border: 1px solid #b0c4d8;
      padding: 20px;
      margin: 15px 0;
      background-color: white;
    }

  </style>
</head>
<body>

  <h1>My Favourite Hobbies</h1>
  <p>Welcome to my hobbies page. Here I share what I love to do in my free time.</p>

  <h2>Hobby 1: Coding</h2>
  <p>I love building websites and solving programming challenges. It sharpens my logical thinking.</p>

  <h2>Hobby 2: Reading</h2>
  <p>I enjoy science fiction and history books. They expand my imagination and knowledge.</p>

  <h2>Hobby 3: Photography</h2>
  <p>Capturing moments with a camera teaches me to observe the world more carefully.</p>

</body>
</html>
```

**Milestone 2 Output:**
```
Page background: soft blue-grey (#f0f4f8)
Font: Arial throughout

"My Favourite Hobbies"
  → very dark navy, Verdana, very large

"Hobby 1: Coding"     ← dark navy, with a blue underline border below
┌────────────────────────────────────────────────────────────┐
│                                                            │
│  I love building websites and solving programming         │
│  challenges. It sharpens my logical thinking.             │
│                                                            │
└────────────────────────────────────────────────────────────┘
  (white background card, light blue border, 20px padding, 15px gap)

(... same pattern for Hobby 2 and Hobby 3 ...)
```

---

### Stage 3: Enhancements — Add Your Personal Touch

Now make the page your own! Try making these changes:

1. Change the `background-color` of the body to a colour you prefer
2. Change the `h1` colour to your favourite colour
3. Change the `font-family` of `h1` to `georgia` or `times new roman`
4. Change the `border` on paragraphs from `1px` to `3px` and from `solid` to `dashed`
5. Add `margin: 40px;` to the `body` to add space around the entire page content

**Final Output Challenge:** Your page should look like a professional personal webpage with consistent, attractive styling. Every styling property from this lesson (`color`, `font-family`, `font-size`, `border`, `padding`, `margin`, `background-color`) should be present.

---

### Reflection Questions for the Mini Project

1. Why is it better to use internal CSS than inline CSS for this page?
2. What would be the benefit of converting this to external CSS if you had 5 hobby sub-pages?
3. If you changed the `border` colour in the CSS rule for `p`, how many places would you need to edit?
4. What does `margin: 15px 0;` mean? (Hint: the two values are for top/bottom and left/right!)

---

## Part 8: Common Beginner Mistakes — And How to Fix Them

### Mistake 1: Missing Semicolon in CSS

**Wrong:**
```css
p {
  color: red
  font-size: 18px;
}
```

**Problem:** The missing semicolon after `color: red` causes the browser to merge the two rules together and ignore them both.

**Correct:**
```css
p {
  color: red;
  font-size: 18px;
}
```

> **Rule:** Every CSS declaration (property: value pair) must end with a semicolon `;`.

---

### Mistake 2: Missing Curly Braces `{}` in Internal/External CSS

**Wrong:**
```css
p
  color: red;
  font-size: 18px;
```

**Correct:**
```css
p {
  color: red;
  font-size: 18px;
}
```

> **Rule:** Every CSS selector must be followed by curly braces `{ }` that wrap all its rules.

---

### Mistake 3: Using CSS Syntax in an Inline `style` Attribute

**Wrong:**
```html
<p style="p { color: red; }">Hello</p>
```

**Problem:** Inside the `style` attribute, you do NOT use the selector name or curly braces. Those are only for internal/external CSS.

**Correct:**
```html
<p style="color: red;">Hello</p>
```

> **Rule:** Inside the `style` attribute, just write `property: value;` directly — no selector, no curly braces.

---

### Mistake 4: Forgetting `rel="stylesheet"` in the `<link>` Tag

**Wrong:**
```html
<link href="styles.css">
```

**Problem:** The browser does not know what kind of file `styles.css` is, so it may not apply the styles.

**Correct:**
```html
<link rel="stylesheet" href="styles.css">
```

> **Rule:** Always include `rel="stylesheet"` in your `<link>` tag.

---

### Mistake 5: Writing HTML Tags Inside a `.css` File

**Wrong** (inside `styles.css`):
```html
<style>
  body {
    background-color: blue;
  }
</style>
```

**Problem:** CSS files must contain ONLY CSS rules — no HTML tags at all, including no `<style>` tags.

**Correct** (inside `styles.css`):
```css
body {
  background-color: blue;
}
```

> **Rule:** A `.css` file contains raw CSS rules only. The `<style>` tag is only used inside an HTML file for internal CSS.

---

### Mistake 6: Confusing `padding` and `margin`

**Wrong thinking:** "I want more space between the paragraph and the next heading, so I'll add padding."

**Why it's wrong:** Padding adds space **inside** the element (between the text and the border). Margin adds space **outside** (between elements).

**Correct:** If you want space **between** two elements, use `margin`. If you want breathing room **inside** an element, use `padding`.

---

## Part 9: Reflection Questions

Think through these questions carefully. They test your deep understanding:

1. What does the word "Cascading" in "Cascading Style Sheets" mean? Give a simple example.
2. You have a website with 100 HTML pages. You decide to change the font of all paragraphs from Arial to Georgia. Which CSS method (inline, internal, or external) would require the least work? Why?
3. What is the difference between `padding` and `margin`? Draw a simple box diagram in your notes.
4. If you write `body { color: blue; }`, what happens to the text in all `<h1>` and `<p>` elements inside the body?
5. What file extension must a CSS file have?
6. What HTML tag do you use to link an external CSS file to your HTML page?
7. Can you use the same external CSS file for two different HTML pages? What would be the advantage?
8. Write (from memory, without looking) the CSS rule that would make all `<h2>` elements have: red text, Arial font, 20px size, a 3-pixel solid green border, and 25px padding.

---

## Part 10: CSS Code Challenge — Internal Style Sheet

This challenge is based on the W3Schools HTML CSS Code Challenge. The goal is to test your ability to create an internal style sheet.

### Challenge Brief

Build an HTML page from scratch that uses an **internal style sheet** to apply the following requirements:

- The page background should be `lightblue`
- All `<h1>` elements should have the colour `white`
- All `<p>` elements should have the colour `darkblue`
- All `<p>` elements should have a `5px solid navy` border
- All `<p>` elements should have `10px` padding
- All `<p>` elements should have `20px` margin

### Your Solution

```html
<!DOCTYPE html>
<html>
<head>
  <style>

    body {
      background-color: lightblue;
    }

    h1 {
      color: white;
    }

    p {
      color: darkblue;
      border: 5px solid navy;
      padding: 10px;
      margin: 20px;
    }

  </style>
</head>
<body>

  <h1>CSS Code Challenge Solution</h1>
  <p>This paragraph demonstrates all the required styles.</p>
  <p>This second paragraph also gets the same styling automatically from CSS.</p>

</body>
</html>
```

**Expected Output:**
```
Page background: light blue

"CSS Code Challenge Solution"
  → white text heading (visible against the blue background)

(20px gap from top)
┌─────────────────────────────────────────────────────┐
│          (10px padding)                             │
│  This paragraph demonstrates all the required...   │  ← dark blue text, 5px solid navy border
│          (10px padding)                             │
└─────────────────────────────────────────────────────┘
(20px gap)
┌─────────────────────────────────────────────────────┐
│          (10px padding)                             │
│  This second paragraph also gets the same...       │
│          (10px padding)                             │
└─────────────────────────────────────────────────────┘
```

---

## Completion Checklist

Before moving on to the next lesson, confirm that you can do each of the following:

- [ ] Explain what CSS stands for and what "cascading" means
- [ ] Describe the purpose of CSS in web development
- [ ] Write inline CSS using the `style` attribute
- [ ] Write internal CSS using `<style>` tags inside `<head>`
- [ ] Create and link an external `.css` file using `<link rel="stylesheet" href="...">`
- [ ] Use the `color` property to change text colour
- [ ] Use the `font-family` property to change the font
- [ ] Use the `font-size` property using `px` and `%` units
- [ ] Use the `background-color` property on both `body` and individual elements
- [ ] Use the `border` property with width, style, and colour values
- [ ] Use `padding` to add space inside an element
- [ ] Use `margin` to add space outside an element
- [ ] Explain the difference between padding and margin
- [ ] Identify and fix the 6 common CSS beginner mistakes
- [ ] Complete the internal style sheet challenge

---

## Lesson Summary

In this lesson, you were introduced to **CSS — Cascading Style Sheets**, the language that transforms plain HTML into beautiful, professional-looking webpages.

**The three ways to add CSS:**
- **Inline CSS** — `style` attribute inside a tag; affects only that one element
- **Internal CSS** — `<style>` block in `<head>`; affects all matching elements on one page
- **External CSS** — separate `.css` file linked with `<link>`; affects all pages that link to it

**The core CSS properties you learned:**
- `color` — changes text colour
- `font-family` — changes the font/typeface
- `font-size` — changes the size of text (using `px`, `%`, or other units)
- `background-color` — sets the background colour of an element
- `border` — draws a visible line around an element (width, style, colour)
- `padding` — adds space **inside** the border (between content and border)
- `margin` — adds space **outside** the border (between elements)

**Key HTML tags for CSS:**

| Tag | Purpose |
|---|---|
| `<style>` | Contains internal CSS rules in the `<head>` |
| `<link>` | Links to an external CSS file |

**The cascading principle:** Styles set on a parent element automatically flow down to all child elements, unless overridden by a more specific rule.

**Real-world connection:** Every website you have ever visited uses CSS to control its appearance. As a web developer, CSS is one of the three core technologies you will use every day — alongside HTML (structure) and JavaScript (behaviour).

> **You are now ready for Lesson 13: HTML Links — making text and images into clickable hyperlinks that connect pages together!**

---

*Sources: W3Schools HTML CSS Tutorial (https://www.w3schools.com/html/html_css.asp) and W3Schools HTML CSS Code Challenge (https://www.w3schools.com/html/html_challenges_css.asp)*
