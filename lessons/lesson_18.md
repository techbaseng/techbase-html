---
render_with_liquid: false
title: "Lesson 18: HTML Block & Inline Elements, Div & Span"
nav_order: 18
---

# Lesson 18: HTML Block & Inline Elements, `<div>` & `<span>`

---

## Lesson Introduction

Welcome to Lesson 18! In this lesson, you are going to learn one of the most important ideas in HTML: the difference between **block-level elements** and **inline elements**.

You will also master two incredibly powerful and widely used HTML elements — `<div>` and `<span>` — which are the building blocks of almost every real website you see today.

By the end of this lesson, you will:
- Understand what "block" and "inline" mean in HTML
- Know when each type of element is used
- Be able to use `<div>` to group and structure sections of a page
- Be able to use `<span>` to style specific parts of text
- Know how to place multiple `<div>` elements side by side using CSS

This lesson naturally builds on everything you have learned so far about HTML elements, attributes, and inline CSS styling.

---

## Prerequisite Concepts

Before we dive in, let us make sure you understand a few ideas that this lesson builds on.

### What is an HTML element?

An HTML element is a piece of content wrapped between an opening tag and a closing tag. For example:

```html
<p>This is a paragraph.</p>
```

Here, `<p>` is the opening tag, `</p>` is the closing tag, and "This is a paragraph." is the content in between.

### What is CSS?

CSS stands for **Cascading Style Sheets**. It is a language used to control how HTML elements look — their colour, size, position, background, and much more. In this lesson, we will use a small amount of inline CSS (written directly inside an HTML tag using the `style` attribute) to style our elements.

```html
<p style="color: red;">This text is red.</p>
```

- `style` — the attribute that lets us add CSS directly to a tag
- `color: red;` — a CSS rule that changes the text colour to red

You do not need to be a CSS expert yet. We will explain every CSS property we use, line by line.

---

## Part 1: Block-Level vs. Inline Elements

### What Is a "Display Value"?

Every single HTML element has a built-in **display value**. Think of this like a default behaviour that tells the browser: *"How should I position this element on the page?"*

There are two main display types you need to know right now:

1. **Block** — the element takes up the full width of the page and starts on a new line
2. **Inline** — the element only takes up as much space as its content needs, and it sits side by side with other content

Let us understand each one thoroughly.

---

### Block-Level Elements

**What is a block-level element?**

A block-level element is like a paragraph in a book. When you start a new paragraph, it always goes on a **new line**. It doesn't squeeze in next to the previous paragraph — it occupies its own full row.

In HTML, a block-level element:
- Always **starts on a new line**
- Automatically **stretches to fill the full width** available (from left to right edge)
- The browser automatically adds a small **margin (empty space)** above and below it

**Analogy:** Imagine you are stacking bricks. Each brick (block element) gets its own row. You can't put two bricks side by side unless you deliberately change how they are positioned.

#### The Two Most Common Block Elements: `<p>` and `<div>`

The `<p>` element defines a paragraph of text.
The `<div>` element defines a division or section (a container for other elements).

Both are block-level elements.

#### Example 1 — Your First Look at Block Elements

```html
<!DOCTYPE html>
<html>
  <body>
    <p>Hello World</p>
    <div>Hello World</div>
  </body>
</html>
```

**Expected Output (in browser):**
```
Hello World
Hello World
```

Even though both pieces of text say "Hello World", each one appears on its **own separate line**. That is the block behaviour in action. Neither one tried to sit next to the other.

> **Thinking Prompt:** What would happen if you put three `<p>` tags one after another? Would they all be on separate lines or bunched together? Try it!

---

#### The Full List of Block-Level Elements in HTML

Here is every block-level element in HTML. You do not need to memorise them all right now — just recognise that these are the elements that behave as "full-width, new line" boxes:

`<address>`, `<article>`, `<aside>`, `<blockquote>`, `<canvas>`, `<dd>`, `<div>`, `<dl>`, `<dt>`, `<fieldset>`, `<figcaption>`, `<figure>`, `<footer>`, `<form>`, `<h1>` through `<h6>`, `<header>`, `<hr>`, `<li>`, `<main>`, `<nav>`, `<noscript>`, `<ol>`, `<p>`, `<pre>`, `<section>`, `<table>`, `<tfoot>`, `<ul>`, `<video>`

You have already used many of these in previous lessons: `<p>`, `<h1>` through `<h6>`, `<ul>`, `<ol>`, `<li>`, `<table>`. Notice how they all start on new lines? Now you know exactly why.

---

### Inline Elements

**What is an inline element?**

An inline element is the opposite of a block element. It does **not** start on a new line. Instead, it sits **within** a line of text or content, flowing along with everything around it.

An inline element:
- Does **NOT** start on a new line
- Only takes up **as much width as its content needs**
- Lives inside other content, like words inside a sentence

**Analogy:** Think of inline elements like words inside a sentence. The word "big" in "That is a **big** dog" does not jump to a new line — it sits right there among the other words.

#### The Most Common Inline Element: `<span>`

The `<span>` element is an inline container. It is used to wrap a small part of text or content — perhaps just one word or one sentence — so you can style it differently from the rest.

#### Example 2 — Your First Inline Element

```html
<!DOCTYPE html>
<html>
  <body>
    <p>My favourite colour is <span style="color: blue;">blue</span>.</p>
  </body>
</html>
```

**Expected Output:**
```
My favourite colour is blue.
```
(The word "blue" appears in blue colour, while the rest stays in the default colour.)

Notice that `<span>` did not move "blue" to a new line. It stayed right inside the sentence — that is inline behaviour.

> **Thinking Prompt:** What happens if you change `<span>` to `<p>` in the example above? Would "blue" still appear on the same line as the rest of the sentence?

---

#### The Full List of Inline Elements in HTML

`<a>`, `<abbr>`, `<acronym>`, `<b>`, `<bdo>`, `<big>`, `<br>`, `<button>`, `<cite>`, `<code>`, `<dfn>`, `<em>`, `<i>`, `<img>`, `<input>`, `<kbd>`, `<label>`, `<map>`, `<object>`, `<output>`, `<q>`, `<samp>`, `<script>`, `<select>`, `<small>`, `<span>`, `<strong>`, `<sub>`, `<sup>`, `<textarea>`, `<time>`, `<tt>`, `<var>`

You have used many of these already: `<a>` (links), `<img>` (images), `<b>` (bold), `<i>` (italic), `<em>`, `<strong>`. They all flow within lines, not below them.

---

### Critical Rule: Inline Cannot Contain Block

> ⚠️ **Important Rule:** An **inline element cannot contain a block-level element.**

This means you should NEVER put a `<p>`, `<div>`, or `<h1>` inside a `<span>`. Browsers may not display it correctly, and it violates HTML standards.

**Wrong — do NOT do this:**
```html
<span>
  <p>This is wrong!</p>
</span>
```

**Correct — this is fine:**
```html
<p>This is correct. <span>This span is inside a paragraph.</span></p>
```

---

### Side-by-Side Comparison: Block vs. Inline

| Feature | Block Element | Inline Element |
|---|---|---|
| Starts on new line? | ✅ Yes, always | ❌ No, flows with content |
| Full width? | ✅ Yes, stretches to edges | ❌ No, only as wide as content |
| Can contain block elements? | ✅ Yes | ❌ No |
| Common example | `<p>`, `<div>`, `<h1>` | `<span>`, `<a>`, `<img>` |
| Use case | Structure/sections of a page | Styling part of a sentence |

---

## Part 2: The `<div>` Element — Your Layout Superpower

### What Is `<div>`?

The `<div>` element stands for **division**. It is a **block-level container** — meaning it is an empty box you can fill with other HTML elements.

Think of `<div>` like a cardboard box. The box itself has no meaning — it is just a container. But you can put anything inside it (text, images, headings, lists), and then use CSS to style the whole box at once: give it a background colour, a border, a size, or a position on the page.

**Why does `<div>` exist?** Because HTML needed a way to group things together so they could be styled or positioned as one unit. Before `<div>`, you had no easy way to say "make this entire section of the page have a dark background."

The `<div>` element has **no required attributes**, but three are commonly used:
- `style` — to add CSS styling directly
- `class` — to apply a CSS class (you will learn this in Lesson 19)
- `id` — to give it a unique name (you will learn this in Lesson 20)

---

### `<div>` Is a Block Element

Since `<div>` is a block element, it always takes up the full available width and creates a line break before and after itself.

#### Example 3 — `<div>` Takes Full Width

```html
<!DOCTYPE html>
<html>
  <body>
    Lorem Ipsum <div>I am a div</div> dolor sit amet.
  </body>
</html>
```

**Expected Output:**
```
Lorem Ipsum
I am a div
dolor sit amet.
```

Even though we put the `<div>` in the middle of text, it broke onto its own line. "Lorem Ipsum" appeared before it, and "dolor sit amet." appeared after it on a new line. The `<div>` took up its own full-width row.

---

### Using `<div>` as a Container

The real power of `<div>` is grouping elements together. You can put a heading, paragraphs, images, and lists all inside one `<div>`, and then style or move them all at once.

#### Example 4 — `<div>` Grouping Elements

```html
<!DOCTYPE html>
<html>
  <body>
    <div>
      <h2>London</h2>
      <p>London is the capital city of England.</p>
      <p>London has over 9 million inhabitants.</p>
    </div>
  </body>
</html>
```

**Expected Output:**
```
London          (displayed as a heading)

London is the capital city of England.

London has over 9 million inhabitants.
```

All three elements (`<h2>` and both `<p>` tags) are now wrapped inside one `<div>`. They are a group. This means we can now apply one style to the `<div>` and ALL the content inside it will be affected.

---

### Styling a `<div>` with CSS

Here is where `<div>` becomes incredibly powerful. Let us give the whole "London" section a dark background with white text and some padding.

#### Example 5 — Styled `<div>` Container

```html
<!DOCTYPE html>
<html>
  <body>
    <div style="background-color: black; color: white; padding: 20px;">
      <h2>London</h2>
      <p>London is the capital city of England. It is the most populous city
      in the United Kingdom, with a metropolitan area of over 13 million
      inhabitants.</p>
    </div>
  </body>
</html>
```

**Expected Output:**
A box with a black background containing white-coloured text. The heading "London" and the paragraph text both appear white on the black box, with 20 pixels of space around them.

Let us break down each CSS property used in `style="..."`:

- `background-color: black;` — Sets the background colour of the `<div>` to black. You can use colour names like `black`, `red`, `blue`, or HEX codes like `#000000`.
- `color: white;` — Sets the text colour inside the `<div>` to white. This applies to ALL text inside the div — the heading AND the paragraph.
- `padding: 20px;` — Adds 20 pixels of space **inside** the box, between the text and the box edges. Without padding, the text would be pressed right against the edges.

> **Thinking Prompt:** What would happen if you removed `padding: 20px;`? The text would be very close to the edges of the black box. Try it!

---

### Multiple `<div>` Elements on One Page

You can use as many `<div>` elements as you need. Each one creates its own section.

#### Example 6 — Three `<div>` Sections

```html
<!DOCTYPE html>
<html>
  <body>

    <div>
      <h2>London</h2>
      <p>London is the capital city of England.</p>
      <p>London has over 9 million inhabitants.</p>
    </div>

    <div>
      <h2>Oslo</h2>
      <p>Oslo is the capital city of Norway.</p>
      <p>Oslo has over 700,000 inhabitants.</p>
    </div>

    <div>
      <h2>Rome</h2>
      <p>Rome is the capital city of Italy.</p>
      <p>Rome has over 4 million inhabitants.</p>
    </div>

  </body>
</html>
```

**Expected Output:**
```
London
London is the capital city of England.
London has over 9 million inhabitants.

Oslo
Oslo is the capital city of Norway.
Oslo has over 700,000 inhabitants.

Rome
Rome is the capital city of Italy.
Rome has over 4 million inhabitants.
```

Each `<div>` is a separate block that flows one after another, from top to bottom.

---

### Centering a `<div>` Element

By default, a `<div>` takes up the full width available. But what if you make a `<div>` narrower — say only 300 pixels wide — and want to centre it on the page?

You use the CSS property `margin: auto;`. This tells the browser to automatically calculate equal space on both the left and right sides of the element, effectively centering it.

#### Example 7 — Centering a `<div>`

```html
<!DOCTYPE html>
<html>
  <style>
    div {
      width: 300px;
      margin: auto;
    }
  </style>
  <body>
    <div>
      <h2>London</h2>
      <p>London is the capital city of England.</p>
      <p>London has over 9 million inhabitants.</p>
    </div>
  </body>
</html>
```

**Expected Output:**
The London section appears centred on the page, with 300px width.

Breaking down the CSS:
- `width: 300px;` — Limits the `<div>` to 300 pixels wide (instead of the full page width)
- `margin: auto;` — Splits the remaining space equally on the left and right, causing the `<div>` to sit in the centre

---

### Placing Multiple `<div>` Elements Side by Side

By default, since `<div>` is a block element, multiple `<div>`s stack on top of each other (vertically). But in real web design, we often want columns side by side — like a three-column layout.

There are **four main CSS techniques** to achieve this. Let us explore each one.

---

#### Method 1: CSS Float

The CSS `float` property was originally designed for things like wrapping text around images, but it has been widely used for years to place `<div>` elements side by side.

`float: left;` tells an element to "float" to the left and allow other elements to appear next to it on the right.

#### Example 8 — Float Method

```html
<!DOCTYPE html>
<html>
  <style>
    .mycontainer {
      width: 100%;
      overflow: auto;
    }
    .mycontainer div {
      width: 33%;
      float: left;
    }
  </style>
  <body>
    <div class="mycontainer">

      <div>
        <h2>London</h2>
        <p>London is the capital city of England.</p>
        <p>London has over 9 million inhabitants.</p>
      </div>

      <div>
        <h2>Oslo</h2>
        <p>Oslo is the capital city of Norway.</p>
        <p>Oslo has over 700,000 inhabitants.</p>
      </div>

      <div>
        <h2>Rome</h2>
        <p>Rome is the capital city of Italy.</p>
        <p>Rome has over 4 million inhabitants.</p>
      </div>

    </div>
  </body>
</html>
```

**Expected Output:** Three columns side by side — London on the left, Oslo in the middle, Rome on the right.

CSS explanation:
- `.mycontainer` — This is a CSS class selector. It targets any element with `class="mycontainer"`. (You will learn classes fully in Lesson 19.)
- `width: 100%;` — The outer container takes the full page width
- `overflow: auto;` — Prevents layout issues caused by floated children
- `.mycontainer div` — Targets every `<div>` *inside* the `.mycontainer`
- `width: 33%;` — Each inner div is 33% wide (three of them = ~99% of the container)
- `float: left;` — Each div floats to the left, placing them side by side

---

#### Method 2: Inline-Block

Remember how `<div>` is a block element? What if we changed its display behaviour to `inline-block`? Then it would still be a block (able to have width and height), but it would no longer force a line break after itself.

#### Example 9 — Inline-Block Method

```html
<!DOCTYPE html>
<html>
  <style>
    div {
      width: 30%;
      display: inline-block;
    }
  </style>
  <body>
    <div>
      <h2>London</h2>
      <p>London is the capital city of England.</p>
      <p>London has over 9 million inhabitants.</p>
    </div>

    <div>
      <h2>Oslo</h2>
      <p>Oslo is the capital city of Norway.</p>
      <p>Oslo has over 700,000 inhabitants.</p>
    </div>

    <div>
      <h2>Rome</h2>
      <p>Rome is the capital city of Italy.</p>
      <p>Rome has over 4 million inhabitants.</p>
    </div>
  </body>
</html>
```

**Expected Output:** Three columns appear side by side.

CSS explanation:
- `display: inline-block;` — Changes how the `<div>` behaves. It acts like a block (you can set width/height) but flows inline (no automatic line break after it).
- `width: 30%;` — Each div is 30% of the page width (three × 30% = 90%, leaving some breathing room)

---

#### Method 3: Flexbox (flex)

The CSS Flexbox Layout Module is a modern, powerful way to build layouts. It makes it easy to align elements horizontally or vertically, and it handles spacing automatically.

To use flex, you wrap your `<div>` elements inside a parent `<div>`, and then give that parent `display: flex;`.

#### Example 10 — Flexbox Method

```html
<!DOCTYPE html>
<html>
  <style>
    .mycontainer {
      display: flex;
    }
    .mycontainer > div {
      width: 33%;
    }
  </style>
  <body>
    <div class="mycontainer">

      <div>
        <h2>London</h2>
        <p>London is the capital city of England.</p>
        <p>London has over 9 million inhabitants.</p>
      </div>

      <div>
        <h2>Oslo</h2>
        <p>Oslo is the capital city of Norway.</p>
        <p>Oslo has over 700,000 inhabitants.</p>
      </div>

      <div>
        <h2>Rome</h2>
        <p>Rome is the capital city of Italy.</p>
        <p>Rome has over 4 million inhabitants.</p>
      </div>

    </div>
  </body>
</html>
```

**Expected Output:** Three columns side by side.

CSS explanation:
- `display: flex;` — Turns the parent container into a "flex container". Its direct children (the three `<div>`s) automatically line up side by side.
- `.mycontainer > div` — The `>` symbol means "direct children". This targets only the `<div>` elements that are directly inside `.mycontainer`.
- `width: 33%;` — Each child div takes up one-third of the container

Flexbox is the **most recommended modern method** for this kind of layout.

---

#### Method 4: CSS Grid

CSS Grid is the newest and most powerful layout system. It works like a spreadsheet: you define rows and columns, then place elements into that grid.

#### Example 11 — CSS Grid Method

```html
<!DOCTYPE html>
<html>
  <style>
    .grid-container {
      display: grid;
      grid-template-columns: 33% 33% 33%;
    }
  </style>
  <body>
    <div class="grid-container">

      <div>
        <h2>London</h2>
        <p>London is the capital city of England.</p>
        <p>London has over 9 million inhabitants.</p>
      </div>

      <div>
        <h2>Oslo</h2>
        <p>Oslo is the capital city of Norway.</p>
        <p>Oslo has over 700,000 inhabitants.</p>
      </div>

      <div>
        <h2>Rome</h2>
        <p>Rome is the capital city of Italy.</p>
        <p>Rome has over 4 million inhabitants.</p>
      </div>

    </div>
  </body>
</html>
```

**Expected Output:** Three columns side by side.

CSS explanation:
- `display: grid;` — Turns the container into a grid layout
- `grid-template-columns: 33% 33% 33%;` — Defines three columns, each 33% wide. The browser automatically places child elements into these columns from left to right.

Grid is excellent when you need to define **both rows and columns** in complex layouts.

---

### Summary: Choosing Your Side-by-Side Method

| Method | Best For |
|---|---|
| Float | Legacy code, simple layouts, older browser support |
| Inline-Block | Simple side-by-side with minimal setup |
| Flexbox ✅ | Most modern layouts, alignment control, responsive design |
| Grid | Complex two-dimensional layouts (rows AND columns) |

For most beginners starting today, **Flexbox is the recommended choice**.

---

## Part 3: The `<span>` Element — Styling Inside Text

### What Is `<span>`?

The `<span>` element is the **inline equivalent of `<div>`**. While `<div>` is a block-level container for large sections of a page, `<span>` is an inline container for a small piece of text or content *within* a line.

Just like `<div>`, `<span>` has no visual effect on its own. It is invisible until you give it styling.

- `<div>` = a big box for grouping sections (block)
- `<span>` = a small wrapper for words or phrases inside text (inline)

**Why does `<span>` exist?** Because sometimes you want to style just one word or one sentence differently from the rest, without breaking it onto a new line. For example: you want to make just one word in a paragraph turn blue and bold.

The `<span>` element also has no required attributes, but `style`, `class`, and `id` are commonly used.

---

### Example 12 — Your First `<span>`

```html
<!DOCTYPE html>
<html>
  <body>
    <p>My mother has <span style="color: blue; font-weight: bold;">blue</span>
    eyes and my father has <span style="color: darkgreen; font-weight: bold;">
    dark green</span> eyes.</p>
  </body>
</html>
```

**Expected Output:**
```
My mother has blue eyes and my father has dark green eyes.
```
(The word "blue" appears in blue and bold. The words "dark green" appear in dark green and bold. The rest of the sentence stays in the default colour and weight.)

CSS explanation inside `style="..."`:
- `color: blue;` — Changes the text colour to blue
- `font-weight: bold;` — Makes the text bold
- `color: darkgreen;` — Changes the text colour to dark green

Notice: Both `<span>` elements are **inside** the `<p>` tag, and neither one jumps to a new line. They stayed inline within the sentence.

---

### Example 13 — `<span>` vs. `<div>` Comparison

```html
<!DOCTYPE html>
<html>
  <body>
    <!-- Using span (inline) -->
    <p>I love <span style="color: red;">HTML</span> so much!</p>

    <!-- Using div (block) -->
    <p>I love <div style="color: red;">HTML</div> so much!</p>
  </body>
</html>
```

**Expected Output with `<span>` (correct):**
```
I love HTML so much!
```
(Everything on one line, "HTML" is red)

**Expected Output with `<div>` (incorrect usage):**
```
I love
HTML
so much!
```
("HTML" gets pushed to its own line because `<div>` is a block element)

This example clearly shows why `<span>` exists. When you want to style something *within* a sentence without breaking the flow, `<span>` is the right tool.

---

## Guided Practice Exercises

### Exercise 1: Identifying Block vs. Inline

**Objective:** Train your eye to recognise the difference between block and inline behaviour.

**Scenario:** You are building a simple webpage about your city.

**Steps:**

1. Create an HTML file called `my_city.html`
2. Add the following code and observe what happens:

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>My City</h1>
    <p>Welcome to <span style="color: green; font-weight: bold;">Lagos</span>,
    the most vibrant city in Africa!</p>
    <p>Lagos is known for its:</p>
    <ul>
      <li>Incredible music scene</li>
      <li>Delicious street food</li>
      <li>Beautiful beaches</li>
    </ul>
  </body>
</html>
```

**Expected Output:**
```
My City                         (large heading, own line)

Welcome to Lagos, the most vibrant city in Africa!
(Lagos is green and bold, but stays inline in the sentence)

Lagos is known for its:

• Incredible music scene
• Delicious street food
• Beautiful beaches
```

**Self-Check Questions:**
- Which elements started on new lines? (`<h1>`, `<p>`, `<ul>`, `<li>`)
- Which element stayed within the sentence? (`<span>`)
- What would happen if you replaced `<span>` with `<p>`?

---

### Exercise 2: Styling a `<div>` Container

**Objective:** Use `<div>` to create a styled info card.

**Scenario:** You are building a product card for a school store.

**Steps:**

1. Create the following HTML:

```html
<!DOCTYPE html>
<html>
  <body>

    <div style="background-color: #f0f8ff; border: 2px solid blue;
                padding: 15px; width: 250px; margin: auto;">
      <h2 style="color: navy;">Maths Textbook</h2>
      <p>Subject: <span style="color: green;">Mathematics</span></p>
      <p>Price: <span style="color: red; font-weight: bold;">₦2,500</span></p>
      <p>Condition: New</p>
    </div>

  </body>
</html>
```

**Expected Output:** A centred card with a light blue background, blue border, and padding. The heading "Maths Textbook" appears in navy blue. "Mathematics" appears in green, and "₦2,500" appears in red and bold.

**CSS Breakdown:**
- `background-color: #f0f8ff;` — A light sky-blue colour (using a HEX code)
- `border: 2px solid blue;` — A 2-pixel solid blue border around the div
- `padding: 15px;` — 15 pixels of space inside the box
- `width: 250px;` — The card is 250px wide
- `margin: auto;` — Centres the card on the page

**Self-Check Questions:**
- What CSS property controls the background colour?
- What property centres the div horizontally?
- What happened to the price text because of `<span>`?

**Optional Challenge:** Add a second product card below the first one for a different item.

---

### Exercise 3: Creating a Three-Column Layout

**Objective:** Place three `<div>` sections side by side using Flexbox.

**Scenario:** Build a simple weather dashboard for three cities.

**Steps:**

```html
<!DOCTYPE html>
<html>
  <style>
    .weather-container {
      display: flex;
    }
    .city-card {
      width: 33%;
      padding: 10px;
      margin: 5px;
      border: 1px solid grey;
      text-align: center;
    }
  </style>
  <body>

    <h1>Today's Weather</h1>

    <div class="weather-container">

      <div class="city-card" style="background-color: #ffe4b5;">
        <h3>Lagos</h3>
        <p>🌤 Partly Cloudy</p>
        <p><span style="font-size: 24px; font-weight: bold;">32°C</span></p>
      </div>

      <div class="city-card" style="background-color: #e0f0ff;">
        <h3>London</h3>
        <p>🌧 Rainy</p>
        <p><span style="font-size: 24px; font-weight: bold;">14°C</span></p>
      </div>

      <div class="city-card" style="background-color: #e8ffe8;">
        <h3>Tokyo</h3>
        <p>☀️ Sunny</p>
        <p><span style="font-size: 24px; font-weight: bold;">26°C</span></p>
      </div>

    </div>

  </body>
</html>
```

**Expected Output:** A heading "Today's Weather" followed by three coloured cards side by side — one for Lagos (warm yellow background), one for London (light blue background), one for Tokyo (light green background). Each card shows city name, weather condition, and temperature in large bold text.

**CSS Breakdown:**
- `.weather-container` — The outer flex container. `display: flex;` makes its children line up side by side.
- `.city-card` — Each individual city card. `width: 33%;` gives each card one-third of the space. `text-align: center;` centres all text inside.
- `font-size: 24px;` — Makes the temperature text 24 pixels tall (larger than normal)

**Self-Check Questions:**
- Which CSS property made the cards appear side by side?
- What does `text-align: center;` do?
- Why did we use `<span>` around the temperature number?

---

## Mini Project: Personal Profile Card Page

In this project, you will build a personal profile card page that combines everything from this lesson: block elements for structure, `<div>` for layout, `<span>` for text styling, and flexbox for side-by-side layout.

### Stage 1: Setup — Build the Basic Structure

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Student Profiles</h1>
  </body>
</html>
```

**Milestone Output:** A page with just the heading "Student Profiles".

---

### Stage 2: Core Logic — Add Profile Cards

Now add three profile cards, each inside its own `<div>`:

```html
<!DOCTYPE html>
<html>
  <body>

    <h1>Student Profiles</h1>

    <div style="background-color: #fff3cd; border: 1px solid #ccc;
                padding: 20px; margin: 10px;">
      <h2>Amina Okafor</h2>
      <p>Age: <span style="font-weight: bold;">17</span></p>
      <p>Subject: <span style="color: blue;">Computer Science</span></p>
      <p>Status: <span style="color: green;">Active</span></p>
    </div>

    <div style="background-color: #d4edda; border: 1px solid #ccc;
                padding: 20px; margin: 10px;">
      <h2>Chukwuemeka Eze</h2>
      <p>Age: <span style="font-weight: bold;">16</span></p>
      <p>Subject: <span style="color: blue;">Mathematics</span></p>
      <p>Status: <span style="color: green;">Active</span></p>
    </div>

    <div style="background-color: #f8d7da; border: 1px solid #ccc;
                padding: 20px; margin: 10px;">
      <h2>Fatima Bello</h2>
      <p>Age: <span style="font-weight: bold;">18</span></p>
      <p>Subject: <span style="color: blue;">Biology</span></p>
      <p>Status: <span style="color: orange;">On Leave</span></p>
    </div>

  </body>
</html>
```

**Milestone Output:** Three separate profile cards stacked vertically. Each has a different background colour, a name heading, and styled details.

---

### Stage 3: Enhancement — Place Cards Side by Side with Flexbox

Wrap all three cards in a flex container:

```html
<!DOCTYPE html>
<html>
  <style>
    .profile-container {
      display: flex;
    }
    .profile-card {
      width: 33%;
      border: 1px solid #ccc;
      padding: 20px;
      margin: 10px;
    }
  </style>
  <body>

    <h1 style="text-align: center;">Student Profiles</h1>

    <div class="profile-container">

      <div class="profile-card" style="background-color: #fff3cd;">
        <h2>Amina Okafor</h2>
        <p>Age: <span style="font-weight: bold;">17</span></p>
        <p>Subject: <span style="color: blue;">Computer Science</span></p>
        <p>Status: <span style="color: green; font-weight: bold;">Active</span></p>
      </div>

      <div class="profile-card" style="background-color: #d4edda;">
        <h2>Chukwuemeka Eze</h2>
        <p>Age: <span style="font-weight: bold;">16</span></p>
        <p>Subject: <span style="color: blue;">Mathematics</span></p>
        <p>Status: <span style="color: green; font-weight: bold;">Active</span></p>
      </div>

      <div class="profile-card" style="background-color: #f8d7da;">
        <h2>Fatima Bello</h2>
        <p>Age: <span style="font-weight: bold;">18</span></p>
        <p>Subject: <span style="color: blue;">Biology</span></p>
        <p>Status: <span style="color: orange; font-weight: bold;">On Leave</span></p>
      </div>

    </div>

  </body>
</html>
```

**Final Output:** A centred heading "Student Profiles" above three side-by-side profile cards, each with a unique background colour and styled text details.

---

### Stage 4: Reflection Questions

- Why did you need the outer `<div class="profile-container">` wrapper?
- What is the role of `<span>` in each card?
- What would happen to the layout if you removed `display: flex;` from `.profile-container`?
- Can you add a fourth profile card? What happens to the layout?

**Optional Advanced Extensions:**
- Add a profile picture using `<img>` inside each card
- Add a hover effect using CSS (you will learn this in future lessons)
- Add a footer `<div>` below all cards with "© 2026 School Management System"

---

## Common Beginner Mistakes

### Mistake 1: Putting Block Elements Inside Inline Elements

**Wrong:**
```html
<span>
  <p>This paragraph is inside a span — this is invalid!</p>
</span>
```

**Why it is wrong:** `<span>` is an inline element. Inline elements cannot contain block-level elements like `<p>`. The browser may try to fix this automatically, but the results are unpredictable.

**Correct:**
```html
<p>This paragraph is a block. <span>This span is inside the paragraph.</span></p>
```

---

### Mistake 2: Forgetting That `<div>` Is Block

**Wrong expectation:** A beginner writes two `<div>` elements expecting them to appear side by side, but they appear stacked vertically instead.

```html
<div>Box One</div>
<div>Box Two</div>
```
Both boxes appear vertically stacked — this is correct default behaviour.

**To make them side by side**, you MUST use one of the four CSS methods (float, inline-block, flex, or grid). Flex is the most recommended.

---

### Mistake 3: Confusing `<div>` and `<p>`

Beginners sometimes use `<div>` to write paragraphs of text when they should use `<p>`.

**Incorrect (semantically wrong):**
```html
<div>This is a paragraph of text about my day.</div>
```

**Correct:**
```html
<p>This is a paragraph of text about my day.</p>
```

**Why it matters:** HTML has meaning. `<p>` tells the browser (and screen readers) "this is a paragraph." `<div>` says "this is just a generic container." Use semantic elements like `<p>` for text, and save `<div>` for structural grouping.

---

### Mistake 4: Forgetting `margin: auto;` to Centre a `<div>`

**Wrong — no centering:**
```html
<div style="width: 200px;">I am not centred.</div>
```

**Correct — centred:**
```html
<div style="width: 200px; margin: auto;">I am centred!</div>
```

Remember: `margin: auto;` only works when the element has a **defined width** less than the full page. If the `<div>` is already 100% wide, there is nothing to centre.

---

### Mistake 5: Incorrect CSS Syntax Inside `style` Attribute

**Wrong:**
```html
<div style="color red padding 10px">Text</div>
```

**Correct:**
```html
<div style="color: red; padding: 10px;">Text</div>
```

CSS properties inside `style="..."` must follow this exact pattern:
- `property: value;` — notice the **colon** after the property name and the **semicolon** at the end
- Multiple properties are separated by semicolons

---

### Mistake 6: Using `<span>` When You Mean `<div>`

**Wrong — using span to group a large section:**
```html
<span>
  <h2>My Section</h2>
  <p>A paragraph here.</p>
  <p>Another paragraph.</p>
</span>
```

**Why it is wrong:** `<span>` is inline and cannot properly contain block elements like `<h2>` and `<p>`.

**Correct:**
```html
<div>
  <h2>My Section</h2>
  <p>A paragraph here.</p>
  <p>Another paragraph.</p>
</div>
```

**Simple rule to remember:** Use `<div>` for sections and groups. Use `<span>` for words and phrases within sentences.

---

## Reflection Questions

Think carefully about these questions to test your understanding:

1. What is the main difference between a block element and an inline element?
2. Why does a `<div>` always appear on its own line by default?
3. If you want to change just one word's colour in a paragraph without breaking the layout, which element would you use?
4. What does `display: flex;` do to a container's children?
5. Can you put a `<div>` inside a `<div>`? Why would you do this?
6. What CSS property centres a `<div>` that has a fixed width?
7. What is the difference between `padding` and `margin`?
8. Why should you use `<p>` for paragraph text instead of `<div>`?
9. If you have 4 `<div>` elements inside a flex container with `width: 25%;` each, how would they appear?
10. What happens if you put `<div>` inside a `<span>`?

---

## Completion Checklist

Before moving on to the next lesson, make sure you can honestly check off every item below:

- [ ] I understand what a block-level element is and how it behaves
- [ ] I understand what an inline element is and how it behaves
- [ ] I know that inline elements cannot contain block-level elements
- [ ] I can recognise at least 5 block elements and 5 inline elements
- [ ] I understand what `<div>` is and why it is used
- [ ] I can create a styled `<div>` container using the `style` attribute
- [ ] I can group multiple HTML elements inside a `<div>`
- [ ] I can centre a `<div>` using `margin: auto;`
- [ ] I can place multiple `<div>` elements side by side using at least one CSS method
- [ ] I understand what `<span>` is and can use it to style parts of text
- [ ] I know the difference between when to use `<div>` and when to use `<span>`
- [ ] I completed the mini-project and my three profile cards appear side by side

---

## Lesson Summary

In this lesson, you learned one of the most foundational concepts in web development:

**Block vs. Inline:** Every HTML element has a display value. Block elements (like `<div>`, `<p>`, `<h1>`) start on new lines and take full width. Inline elements (like `<span>`, `<a>`, `<img>`) flow within text without breaking to a new line.

**The `<div>` Element:** A block-level container with no visual appearance of its own. It is used to group and structure sections of a webpage. With CSS, you can control its background colour, border, padding, width, and position. Multiple `<div>` elements can be placed side by side using float, inline-block, flexbox, or CSS Grid — with **Flexbox being the modern recommended method**.

**The `<span>` Element:** An inline container for targeting specific text within a line. It is invisible on its own but becomes powerful when combined with CSS to change colour, size, weight, or any other text property — without breaking the sentence flow.

**HTML Tags Reference:**

| Tag | Type | Description |
|---|---|---|
| `<div>` | Block | Defines a section or container in a document |
| `<span>` | Inline | Defines an inline section within text |

These two elements — `<div>` and `<span>` — are used on virtually every professional website in the world. Mastering them prepares you for layouts, styling, classes, IDs, and JavaScript interactions in upcoming lessons.

**You are now ready for Lesson 19: HTML Classes!**
