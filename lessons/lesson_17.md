---
render_with_liquid: false
title: "HTML Lists — Unordered, Ordered, Description, and Nested Lists"
nav_order: 17
---

# Lesson 17 — HTML Lists

## Lesson Introduction

Imagine you are writing a recipe. You have a shopping list of ingredients (where order does not matter), and a set of cooking steps (where order absolutely matters). In HTML, we have exactly those two types of lists — plus a third special type called a **description list** for defining terms. Together, these three list types are among the most frequently used structures in every website, app, and document on the web.

By the end of this lesson you will be able to:

- Create **unordered lists** (bullet lists) for items where order does not matter.
- Create **ordered lists** (numbered lists) for items where sequence matters.
- Customise bullet markers and numbering styles.
- Create **description lists** to pair terms with their definitions.
- **Nest** lists inside other lists.
- Build a **horizontal navigation menu** from an unordered list using CSS.
- Complete a **mini project** that combines all three list types in one realistic webpage.

---

## Prerequisite Concepts

Before we begin, you need to feel comfortable with the following ideas. If any of these feel unfamiliar, re-read the relevant earlier lesson before continuing.

**HTML tags** — An HTML tag is a keyword wrapped in angle brackets. Tags normally come in pairs: an **opening tag** like `<p>` and a **closing tag** like `</p>`. Everything between the two tags is the content that tag controls.

**HTML elements** — An HTML element is the complete unit of opening tag + content + closing tag:

```html
<p>This is a paragraph element.</p>
```

**Parent and child elements** — When one element sits inside another element, the outer one is called the **parent** and the inner one is called the **child**. Lists use this relationship constantly: the list container (`<ul>` or `<ol>`) is the parent, and each list item (`<li>`) is a child.

**The `style` attribute** — You can add CSS styling directly to any HTML tag using the `style` attribute, like this:

```html
<p style="color: red;">This text is red.</p>
```

We will use this technique in a few list examples to change bullet styles.

---

## Part 1 — What Is an HTML List?

### Why Do Lists Exist?

Think of any real-world situation where you group related items together:

- A shopping list
- The steps to install an app
- A glossary of terms
- A navigation menu on a website
- A table of contents

All of these are lists. Without proper list elements in HTML, you would have to fake a list with paragraphs or line breaks — and that would make your HTML harder to read, harder to style, and harder for screen readers (used by people with visual impairments) to understand.

HTML provides **dedicated list elements** so that both browsers and assistive technology can correctly identify and present your content.

### The Three Types of HTML Lists

HTML supports exactly three list types. Here is a plain-English summary before we dive into the code:

| List Type | HTML Tag | When to Use |
|---|---|---|
| **Unordered list** | `<ul>` | Items where order does NOT matter (shopping items, features, options) |
| **Ordered list** | `<ol>` | Items where order DOES matter (steps, rankings, sequences) |
| **Description list** | `<dl>` | Term-and-definition pairs (glossaries, metadata, FAQ answers) |

### The List Item Tag

All three list types share the same child tag for their items: **`<li>`** (which stands for "list item"). Think of `<li>` as one line in your list.

> **Analogy:** If `<ul>` or `<ol>` is a shopping bag, then each `<li>` is one product inside the bag.

---

## Part 2 — Unordered Lists (`<ul>`)

### What Is an Unordered List?

An **unordered list** is a collection of items where the order does not matter. Each item is typically displayed with a small bullet marker beside it. By default, the marker is a solid black circle (•).

**Real-world examples:**
- A list of features on a product page ("Free shipping • 30-day returns • 24/7 support")
- A set of ingredients in a recipe
- Navigation links in a website header

### Basic Syntax

```html
<ul>
  <li>Item one</li>
  <li>Item two</li>
  <li>Item three</li>
</ul>
```

**Let's read this line by line:**

- `<ul>` — Opens the unordered list container. This tells the browser "a bullet list starts here."
- `<li>Item one</li>` — A single list item. Everything between `<li>` and `</li>` is the text that appears beside the bullet.
- The second and third `<li>` lines follow the same pattern.
- `</ul>` — Closes the unordered list container. This tells the browser "the bullet list ends here."

### Simple Example — A Fruit List

```html
<ul>
  <li>Apple</li>
  <li>Banana</li>
  <li>Mango</li>
</ul>
```

**Expected output in the browser:**

```
• Apple
• Banana
• Mango
```

> **Thinking prompt:** What if you swapped Banana and Mango — would the meaning of the list change? No! That is exactly why this is an *unordered* list. The sequence does not matter.

---

### Choosing a Bullet Marker Style

By default the bullet is a solid disc. You can change the marker shape using the CSS property `list-style-type` on the `<ul>` tag. There are four options:

| `list-style-type` value | What it looks like |
|---|---|
| `disc` | ● (solid filled circle — the default) |
| `circle` | ○ (hollow circle) |
| `square` | ■ (solid square) |
| `none` | No marker at all (invisible bullets) |

#### Example 1 — Disc (default)

```html
<ul style="list-style-type: disc;">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
```

**Expected output:**
```
● Coffee
● Tea
● Milk
```

#### Example 2 — Circle

```html
<ul style="list-style-type: circle;">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
```

**Expected output:**
```
○ Coffee
○ Tea
○ Milk
```

#### Example 3 — Square

```html
<ul style="list-style-type: square;">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
```

**Expected output:**
```
■ Coffee
■ Tea
■ Milk
```

#### Example 4 — None (no marker)

```html
<ul style="list-style-type: none;">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
```

**Expected output:**
```
Coffee
Tea
Milk
```

> **Why would you use `none`?** When you want to build a navigation menu from a list but hide the bullets, or when you are creating a custom-styled list where you add your own icons in CSS.

> **Thinking prompt:** What happens if you remove the `style` attribute entirely? The browser will use `disc` as the default.

---

### Nested Unordered Lists

You can place one list **inside** another list item. This creates a sub-list — also called a **nested list**.

```html
<ul>
  <li>Coffee</li>
  <li>Tea
    <ul>
      <li>Black tea</li>
      <li>Green tea</li>
    </ul>
  </li>
  <li>Milk</li>
</ul>
```

**Expected output:**
```
● Coffee
● Tea
    ○ Black tea
    ○ Green tea
● Milk
```

**Line-by-line explanation:**

- The outer `<ul>` holds the main list: Coffee, Tea, Milk.
- The `<li>Tea` item does **not** have a closing `</li>` right away. Instead, it opens a second `<ul>` inside itself.
- That inner `<ul>` contains "Black tea" and "Green tea" as its own `<li>` items.
- The inner `</ul>` closes the sub-list, and then `</li>` closes the "Tea" list item.

Notice that the browser automatically changes the bullet style for the inner list (from `disc` to `circle`) to help show the difference in levels visually.

> **Important rule:** A `<li>` element can contain anything that a normal block of content can — other lists, images, links, paragraphs, etc.

---

### Horizontal List — Building a Navigation Menu

One very practical use of `<ul>` is building a website **navigation bar** (the row of links at the top of a website). By default, list items stack vertically. But with a little CSS, you can make them float side by side horizontally.

```html
<!DOCTYPE html>
<html>
<head>
<style>
  ul {
    list-style-type: none;   /* Remove bullets */
    margin: 0;               /* Remove default spacing */
    padding: 0;              /* Remove default indent */
    overflow: hidden;        /* Contain the floated items */
    background-color: #333;  /* Dark background */
  }

  li {
    float: left;             /* Put each item side-by-side */
  }

  li a {
    display: block;          /* Make the whole box clickable */
    color: white;            /* White text */
    text-align: center;
    padding: 16px;
    text-decoration: none;   /* Remove underline */
  }

  li a:hover {
    background-color: #111;  /* Darken on hover */
  }
</style>
</head>
<body>

<ul>
  <li><a href="#home">Home</a></li>
  <li><a href="#news">News</a></li>
  <li><a href="#contact">Contact</a></li>
  <li><a href="#about">About</a></li>
</ul>

</body>
</html>
```

**Expected visual output:**
A dark horizontal bar reading: `Home  News  Contact  About`  
Hovering over any item makes it slightly darker.

**CSS explanation (each property explained):**

- `list-style-type: none` — Removes the bullet points so the menu looks clean.
- `margin: 0; padding: 0` — Removes the default browser indent/gap that appears around lists.
- `overflow: hidden` — Ensures the dark background stretches to contain all the floated items.
- `float: left` — Forces each `<li>` to sit to the right of the previous one instead of below it.
- `display: block` — Makes the link fill the entire `<li>` box, so clicking anywhere in the box works.
- `padding: 16px` — Adds comfortable click space around each link label.
- `text-decoration: none` — Removes the default blue underline from links.

> **Real-world connection:** Nearly every website navigation bar you have ever seen is built exactly this way — a `<ul>` with CSS making it horizontal.

---

## Part 3 — Ordered Lists (`<ol>`)

### What Is an Ordered List?

An **ordered list** is a list where the sequence matters. Each item is automatically numbered by the browser. You do not type the numbers yourself — HTML does it for you.

**Real-world examples:**
- Steps in a tutorial ("Step 1: Install Python, Step 2: Open the terminal…")
- A ranked top-10 list
- Cooking instructions in a recipe
- Legal terms with clause numbers

### Basic Syntax

```html
<ol>
  <li>First item</li>
  <li>Second item</li>
  <li>Third item</li>
</ol>
```

**Expected output:**
```
1. First item
2. Second item
3. Third item
```

The browser automatically adds "1.", "2.", "3." — you never type those numbers.

> **Thinking prompt:** What if you deleted the second `<li>`? The list would still number correctly: 1, 2 — not 1, 3. HTML always renumbers automatically.

---

### The `type` Attribute — Changing the Numbering Style

By default, ordered lists use Arabic numerals (1, 2, 3…). The `type` attribute on `<ol>` lets you change this:

| `type` value | Example output |
|---|---|
| `"1"` | 1. 2. 3. (default) |
| `"A"` | A. B. C. (uppercase letters) |
| `"a"` | a. b. c. (lowercase letters) |
| `"I"` | I. II. III. (uppercase Roman numerals) |
| `"i"` | i. ii. iii. (lowercase Roman numerals) |

#### Example 1 — Default Numbers

```html
<ol type="1">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```

**Expected output:**
```
1. Coffee
2. Tea
3. Milk
```

#### Example 2 — Uppercase Letters

```html
<ol type="A">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```

**Expected output:**
```
A. Coffee
B. Tea
C. Milk
```

#### Example 3 — Lowercase Letters

```html
<ol type="a">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```

**Expected output:**
```
a. Coffee
b. Tea
c. Milk
```

#### Example 4 — Uppercase Roman Numerals

```html
<ol type="I">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```

**Expected output:**
```
I.   Coffee
II.  Tea
III. Milk
```

#### Example 5 — Lowercase Roman Numerals

```html
<ol type="i">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```

**Expected output:**
```
i.   Coffee
ii.  Tea
iii. Milk
```

> **Real-world use case:** Legal documents, academic papers, and formal outlines often use Roman numerals for section headings. Homework assignments sometimes use lowercase letters (a., b., c.) for sub-questions.

---

### The `start` Attribute — Starting From a Custom Number

By default, an ordered list starts counting from 1. Sometimes you need to start from a different number — for example, when continuing a list that was split across two separate `<ol>` blocks on the page.

The `start` attribute lets you set the starting number:

```html
<ol start="50">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```

**Expected output:**
```
50. Coffee
51. Tea
52. Milk
```

> **Thinking prompt:** What would happen if you wrote `start="5"` with `type="A"`? The list would start at the 5th letter: E, F, G…

---

### Nested Ordered Lists

Just like unordered lists, ordered lists can be nested:

```html
<ol>
  <li>Coffee</li>
  <li>Tea
    <ol>
      <li>Black tea</li>
      <li>Green tea</li>
    </ol>
  </li>
  <li>Milk</li>
</ol>
```

**Expected output:**
```
1. Coffee
2. Tea
    1. Black tea
    2. Green tea
3. Milk
```

The inner ordered list restarts numbering from 1 automatically.

---

## Part 4 — Description Lists (`<dl>`)

### What Is a Description List?

A **description list** is a specialised list designed for term-and-definition pairs — like a dictionary or a glossary. Instead of bullet points or numbers, each entry has two parts: a **term** and its **description** (or definition).

**Real-world examples:**
- A glossary of technical terms on a documentation page
- A product specification sheet ("Weight: 1.2kg, Battery: 4000mAh")
- An FAQ section ("Question: ... Answer: ...")
- A recipe's metadata ("Servings: 4, Cook time: 30 min")

### The Three Tags Used in Description Lists

| Tag | Full name | What it does |
|---|---|---|
| `<dl>` | Description List | The container for the entire list |
| `<dt>` | Description Term | The word or phrase being defined |
| `<dd>` | Description Details | The definition or description of the term |

### Basic Syntax

```html
<dl>
  <dt>Term 1</dt>
  <dd>Definition of term 1</dd>
  <dt>Term 2</dt>
  <dd>Definition of term 2</dd>
</dl>
```

**Line-by-line explanation:**

- `<dl>` — Opens the description list container.
- `<dt>Term 1</dt>` — Defines the first **term** (displayed left-aligned, not indented).
- `<dd>Definition of term 1</dd>` — Provides the **description** for that term (displayed indented below the term).
- The pattern repeats for each term-description pair.
- `</dl>` — Closes the description list.

### Simple Example — Drinks Glossary

```html
<dl>
  <dt>Coffee</dt>
  <dd>- black hot drink</dd>

  <dt>Milk</dt>
  <dd>- white cold drink</dd>
</dl>
```

**Expected output:**
```
Coffee
    - black hot drink
Milk
    - white cold drink
```

Notice that `<dd>` automatically indents its content. The browser does this by default to visually connect the description to its term.

### Practical Example — Programming Glossary

```html
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language — used to structure web content.</dd>

  <dt>CSS</dt>
  <dd>Cascading Style Sheets — used to style and layout web pages.</dd>

  <dt>JavaScript</dt>
  <dd>A programming language that makes web pages interactive.</dd>
</dl>
```

**Expected output:**
```
HTML
    HyperText Markup Language — used to structure web content.
CSS
    Cascading Style Sheets — used to style and layout web pages.
JavaScript
    A programming language that makes web pages interactive.
```

> **Thinking prompt:** Could you use a `<ul>` or `<ol>` for this same content? Technically yes, but `<dl>` is semantically better — it clearly communicates to browsers and screen readers that these are paired term-definition relationships, not just a simple list of items.

---

## Part 5 — Mixing List Types (Nested Combinations)

You can nest different list types inside each other. For example, you could have an ordered list of steps where each step has an unordered list of notes.

### Example — Study Plan

```html
<ol>
  <li>Morning Study
    <ul>
      <li>Read Chapter 3</li>
      <li>Make notes</li>
    </ul>
  </li>
  <li>Afternoon Practice
    <ul>
      <li>Complete exercises 1–5</li>
      <li>Review answers</li>
    </ul>
  </li>
  <li>Evening Review
    <ul>
      <li>Re-read notes</li>
      <li>Summarise key points</li>
    </ul>
  </li>
</ol>
```

**Expected output:**
```
1. Morning Study
     • Read Chapter 3
     • Make notes
2. Afternoon Practice
     • Complete exercises 1–5
     • Review answers
3. Evening Review
     • Re-read notes
     • Summarise key points
```

This is one of the most realistic patterns you will see in real web content — numbered main steps with bulleted sub-notes.

---

## Part 6 — Complete HTML List Tags Reference

Here is every tag used in HTML lists, with a clear description of each:

| Tag | Description |
|---|---|
| `<ul>` | Defines an **unordered** (bulleted) list |
| `<ol>` | Defines an **ordered** (numbered) list |
| `<li>` | Defines a **list item** inside `<ul>` or `<ol>` |
| `<dl>` | Defines a **description list** |
| `<dt>` | Defines a **term** (title) in a description list |
| `<dd>` | Defines the **description/definition** of a term in a description list |

---

## Part 7 — Guided Practice Exercises

### Exercise 1 — Your Favourite Things (Unordered List)

**Objective:** Build a simple unordered list.

**Scenario:** You are creating a personal page and want to list your three favourite subjects in school.

**Steps:**
1. Open your HTML file.
2. Add a heading: `<h2>My Favourite Subjects</h2>`
3. Below it, create a `<ul>` with three `<li>` items — your favourite subjects.
4. Save and open the file in a browser.

**Starter code:**
```html
<!DOCTYPE html>
<html>
<body>

<h2>My Favourite Subjects</h2>

<ul>
  <li>Mathematics</li>
  <li>Computer Science</li>
  <li>Physics</li>
</ul>

</body>
</html>
```

**Expected output:**
```
My Favourite Subjects

• Mathematics
• Computer Science
• Physics
```

**Self-check questions:**
- Did the bullets appear?
- Can you change the bullet style to `square`?
- What happens when you add a fourth `<li>`?

---

### Exercise 2 — Making Tea (Ordered List)

**Objective:** Use an ordered list to write step-by-step instructions.

**Scenario:** A friend asks you how to make a cup of tea. Write the steps as a numbered list.

**Steps:**
1. Create an HTML file.
2. Add an `<h2>` heading: "How to Make Tea"
3. Create an `<ol>` with at least five steps.
4. Preview in the browser.

**Example solution:**
```html
<h2>How to Make Tea</h2>

<ol>
  <li>Boil water in a kettle.</li>
  <li>Place a tea bag in your mug.</li>
  <li>Pour the hot water into the mug.</li>
  <li>Wait 3 minutes for the tea to brew.</li>
  <li>Remove the tea bag and add milk if desired.</li>
</ol>
```

**Expected output:**
```
How to Make Tea

1. Boil water in a kettle.
2. Place a tea bag in your mug.
3. Pour the hot water into the mug.
4. Wait 3 minutes for the tea to brew.
5. Remove the tea bag and add milk if desired.
```

**What-if challenge:** What happens if you change `<ol>` to `type="A"`? Try it!

---

### Exercise 3 — School Subjects and Topics (Nested List)

**Objective:** Build a nested list combining `<ul>` inside `<ul>`.

**Scenario:** Create a list of school subjects, and under each subject, list two topics covered.

**Example solution:**
```html
<h2>School Curriculum</h2>

<ul>
  <li>Mathematics
    <ul>
      <li>Algebra</li>
      <li>Geometry</li>
    </ul>
  </li>
  <li>Science
    <ul>
      <li>Physics</li>
      <li>Chemistry</li>
    </ul>
  </li>
  <li>Languages
    <ul>
      <li>English</li>
      <li>French</li>
    </ul>
  </li>
</ul>
```

**Expected output:**
```
• Mathematics
    ○ Algebra
    ○ Geometry
• Science
    ○ Physics
    ○ Chemistry
• Languages
    ○ English
    ○ French
```

**Self-check:** Notice the inner bullets automatically changed from ● to ○? That is the browser helping you see the indentation levels visually.

---

### Exercise 4 — HTML Glossary (Description List)

**Objective:** Build a description list to explain HTML terms.

**Scenario:** You are writing a beginner's HTML cheat sheet. Add four terms and their definitions.

**Example solution:**
```html
<h2>HTML Glossary</h2>

<dl>
  <dt>Tag</dt>
  <dd>A keyword wrapped in angle brackets that tells the browser what to do, e.g. &lt;p&gt;.</dd>

  <dt>Element</dt>
  <dd>An opening tag, its content, and its closing tag together.</dd>

  <dt>Attribute</dt>
  <dd>Extra information added inside an opening tag to modify its behaviour, e.g. style="color:red".</dd>

  <dt>Nesting</dt>
  <dd>Placing one HTML element inside another element.</dd>
</dl>
```

**Expected output:**
```
HTML Glossary

Tag
    A keyword wrapped in angle brackets that tells the browser what to do, e.g. <p>.
Element
    An opening tag, its content, and its closing tag together.
Attribute
    Extra information added inside an opening tag to modify its behaviour.
Nesting
    Placing one HTML element inside another element.
```

---

## Part 8 — Mini Project: "My Life" Personal Page

In this project you will build a personal profile page that uses all three list types in one realistic, combined HTML file.

### Stage 1 — Set Up the Page Structure

Create a new file called `my_life.html` and add the basic HTML structure:

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Life</title>
</head>
<body>

  <h1>About Me</h1>

</body>
</html>
```

**Milestone output:** A page that shows "About Me" as a large heading.

---

### Stage 2 — Add an Unordered List of Hobbies

Inside `<body>`, after the `<h1>`, add a section about your hobbies:

```html
<h2>My Hobbies</h2>
<ul>
  <li>Reading science fiction books</li>
  <li>Playing football</li>
  <li>Coding websites</li>
  <li>Listening to music</li>
</ul>
```

**Milestone output:** A bulleted list of hobbies appears below the heading.

---

### Stage 3 — Add an Ordered List of Goals

Below the hobbies section, add a ranked list of personal goals:

```html
<h2>My Goals This Year</h2>
<ol>
  <li>Learn HTML and CSS completely.</li>
  <li>Build my first personal website.</li>
  <li>Study for and pass my final exams.</li>
  <li>Read at least 6 books.</li>
</ol>
```

**Milestone output:** A numbered list of goals appears.

---

### Stage 4 — Add a Nested List of Favourite Music

Add a section that lists music genres and their artists using a nested list:

```html
<h2>Favourite Music</h2>
<ul>
  <li>Afrobeats
    <ul>
      <li>Burna Boy</li>
      <li>Wizkid</li>
    </ul>
  </li>
  <li>Hip-Hop
    <ul>
      <li>Kendrick Lamar</li>
      <li>J. Cole</li>
    </ul>
  </li>
</ul>
```

**Milestone output:** A two-level list where genres have artists nested beneath them.

---

### Stage 5 — Add a Description List of Key Facts

Finally, add a description list of facts about yourself:

```html
<h2>Quick Facts</h2>
<dl>
  <dt>Nationality</dt>
  <dd>Nigerian</dd>

  <dt>Favourite subject</dt>
  <dd>Computer Science</dd>

  <dt>Current skill</dt>
  <dd>Learning HTML</dd>

  <dt>Favourite food</dt>
  <dd>Jollof rice</dd>
</dl>
```

**Milestone output:** A term-definition list of personal facts.

---

### Complete Final Code

Putting all five stages together:

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Life</title>
</head>
<body>

  <h1>About Me</h1>

  <h2>My Hobbies</h2>
  <ul>
    <li>Reading science fiction books</li>
    <li>Playing football</li>
    <li>Coding websites</li>
    <li>Listening to music</li>
  </ul>

  <h2>My Goals This Year</h2>
  <ol>
    <li>Learn HTML and CSS completely.</li>
    <li>Build my first personal website.</li>
    <li>Study for and pass my final exams.</li>
    <li>Read at least 6 books.</li>
  </ol>

  <h2>Favourite Music</h2>
  <ul>
    <li>Afrobeats
      <ul>
        <li>Burna Boy</li>
        <li>Wizkid</li>
      </ul>
    </li>
    <li>Hip-Hop
      <ul>
        <li>Kendrick Lamar</li>
        <li>J. Cole</li>
      </ul>
    </li>
  </ul>

  <h2>Quick Facts</h2>
  <dl>
    <dt>Nationality</dt>
    <dd>Nigerian</dd>

    <dt>Favourite subject</dt>
    <dd>Computer Science</dd>

    <dt>Current skill</dt>
    <dd>Learning HTML</dd>

    <dt>Favourite food</dt>
    <dd>Jollof rice</dd>
  </dl>

</body>
</html>
```

**Expected final output:**

The browser displays a personal page with four separate sections, each using a different list structure:
- An unordered bullet list of hobbies
- A numbered list of goals
- A nested bullet list showing music genres and their artists
- An indented description list of quick personal facts

---

### Optional Extension Challenges

1. Change the hobbies list bullet style to `square`.
2. Change the goals list to use uppercase Roman numerals (`type="I"`).
3. Add a fifth hobby and watch the list automatically expand.
4. Add a navigation bar at the top of the page using a horizontal `<ul>` menu with CSS.

---

## Part 9 — Common Beginner Mistakes

### Mistake 1 — Putting `<li>` Outside a List Container

**Wrong:**
```html
<li>Item one</li>
<li>Item two</li>
```

**Why it is wrong:** `<li>` items must always live inside a `<ul>` or `<ol>` parent. Without the container, the browser may still try to display them, but the HTML is invalid and will behave unpredictably.

**Correct:**
```html
<ul>
  <li>Item one</li>
  <li>Item two</li>
</ul>
```

---

### Mistake 2 — Forgetting to Close `</li>` Before the Next Item

**Wrong:**
```html
<ul>
  <li>Apple
  <li>Banana
  <li>Mango
</ul>
```

**Why it is risky:** Modern browsers are forgiving and often guess what you meant, but this is technically invalid HTML. When you add nested lists, missing `</li>` tags cause the nesting to break completely.

**Correct:**
```html
<ul>
  <li>Apple</li>
  <li>Banana</li>
  <li>Mango</li>
</ul>
```

---

### Mistake 3 — Using `<br>` Tags Instead of List Items

**Wrong:**
```html
<p>
  Apple<br>
  Banana<br>
  Mango
</p>
```

**Why it is wrong:** This looks like a list visually, but it is not semantically a list. Browsers, search engines, and screen readers cannot identify this as a list. Users relying on screen readers will not hear it announced as a list.

**Correct:**
```html
<ul>
  <li>Apple</li>
  <li>Banana</li>
  <li>Mango</li>
</ul>
```

---

### Mistake 4 — Confusing `<ul>` and `<ol>`

**Wrong example:** Using `<ul>` for cooking steps where order matters.

```html
<!-- Wrong! Steps must be in order -->
<ul>
  <li>Serve the food</li>
  <li>Cook the food</li>
  <li>Prepare the ingredients</li>
</ul>
```

**Correct:**
```html
<!-- Right! Use <ol> when sequence matters -->
<ol>
  <li>Prepare the ingredients</li>
  <li>Cook the food</li>
  <li>Serve the food</li>
</ol>
```

**Rule of thumb:** Ask yourself: "Does the order of these items matter?" If yes → `<ol>`. If no → `<ul>`.

---

### Mistake 5 — Putting Block Content Directly Inside `<dl>` Without `<dt>` or `<dd>`

**Wrong:**
```html
<dl>
  Coffee
  A hot black drink
</dl>
```

**Why it is wrong:** Content must be wrapped in `<dt>` or `<dd>` tags. Bare text inside `<dl>` is invalid HTML.

**Correct:**
```html
<dl>
  <dt>Coffee</dt>
  <dd>A hot black drink</dd>
</dl>
```

---

### Mistake 6 — Closing the Outer List Too Early When Nesting

**Wrong:**
```html
<ul>
  <li>Tea</li>
</ul>
  <ul>  <!-- This starts a SECOND separate list, not a nested one! -->
    <li>Black tea</li>
    <li>Green tea</li>
  </ul>
```

**Correct:**
```html
<ul>
  <li>Tea
    <ul>   <!-- Inner list is INSIDE the <li>, before </li> -->
      <li>Black tea</li>
      <li>Green tea</li>
    </ul>
  </li>
</ul>
```

The inner `<ul>` must be placed **inside** the `<li>` tag of its parent item, before that `<li>` is closed.

---

## Part 10 — Reflection Questions

Take a moment to answer these questions in your head or write them down. They help you confirm that the concepts have landed:

1. What is the difference between `<ul>` and `<ol>`? Give a real-world example of when you would use each one.

2. If you have a list of the top 5 richest people in the world, should you use `<ul>` or `<ol>`? Why?

3. What does the `type="A"` attribute do on an `<ol>` tag?

4. You want to start a numbered list from 10 instead of 1. Which attribute do you use, and how?

5. What are the three tags used in a description list, and what does each one do?

6. A friend says: "I can just use `<br>` to create a list." What is wrong with this approach?

7. What CSS property changes the bullet shape on a `<ul>` list? Name all four valid values.

8. When building a website navigation bar from a `<ul>`, why do you set `list-style-type: none`?

9. Look at the nested list below. Where exactly should the inner `<ul>` be placed?

   ```html
   <ul>
     <li>Fruit ___</li>  ← where does the inner list go?
   </ul>
   ```

10. What is one advantage of using a `<dl>` description list for a FAQ section instead of using regular paragraphs?

---

## Part 11 — Completion Checklist

Use this checklist to confirm you have fully mastered Lesson 17:

- [ ] I can create a basic `<ul>` unordered list with `<li>` items
- [ ] I can change the bullet marker style using `list-style-type` in CSS
- [ ] I can create a basic `<ol>` ordered list with `<li>` items
- [ ] I understand the five `type` attribute values for `<ol>`
- [ ] I can use the `start` attribute to begin counting from a custom number
- [ ] I can nest a list inside another list correctly
- [ ] I can create a `<dl>` description list using `<dt>` and `<dd>` tags
- [ ] I can build a horizontal navigation menu using `<ul>` and CSS
- [ ] I know which common mistakes to avoid when writing list HTML
- [ ] I completed the mini-project "My Life" personal page
- [ ] I can explain when to use `<ul>` vs `<ol>` vs `<dl>`

---

## Lesson Summary

In this lesson you learned that HTML provides three powerful list types to organise content clearly and semantically:

**Unordered lists (`<ul>`)** are used when the order of items does not matter. Items appear with bullet markers by default. You can change the marker to `disc`, `circle`, `square`, or `none` using the CSS `list-style-type` property. Setting it to `none` combined with `float: left` allows you to build horizontal navigation menus.

**Ordered lists (`<ol>`)** are used when sequence matters. The browser automatically numbers items. You can change the numbering format with the `type` attribute (numbers, uppercase/lowercase letters, uppercase/lowercase Roman numerals) and start at any number using the `start` attribute.

**Description lists (`<dl>`)** are used for term-and-definition pairs. Each entry uses `<dt>` for the term and `<dd>` for the description. Browsers indent `<dd>` content automatically.

**All list types support nesting** — you can place a list inside a `<li>` to create sub-lists. Mixed nesting (e.g., `<ul>` inside `<ol>`) is perfectly valid and very common in real websites.

The single tag shared by all list types is `<li>` — it marks one list item. Always wrap `<li>` inside a `<ul>` or `<ol>` container, and always wrap `<dt>` and `<dd>` inside a `<dl>` container.

Lists are not just visual formatting tools — they are **semantic** structures that tell browsers, search engines, and screen readers exactly how your content is organised. Using the right list type makes your web pages more accessible, more professional, and easier to maintain.

---

*Sources: W3Schools HTML Lists Tutorial — https://www.w3schools.com/html/html_lists.asp*
