---
render_with_liquid: false
title: "HTML Layout Elements and Techniques"
nav_order: 25
---

# Lesson 25: HTML Layout Elements and Techniques

---

## Lesson Introduction

Have you ever looked at a website like a newspaper or a magazine? You notice that the page is divided into neat zones — a big title at the top, a navigation menu on the side, articles in the middle, and a bar at the bottom. That organised arrangement is called a **page layout**.

In this lesson, you will learn:

- What HTML layout elements are and why they exist
- The eight key semantic layout elements used by every professional web developer
- Four different techniques to create multi-column page layouts
- How to build a complete structured web page from scratch

By the end of this lesson, you will be able to look at any website and immediately identify its layout structure — and you will be able to build one yourself.

> **Real-World Connection:** Every website you visit — Google, BBC, Amazon, Facebook — uses HTML layout elements. Understanding layout is the skill that transforms a simple webpage into a professional-looking website.

---

## Prerequisite Concepts

Before we dive in, let's make sure you understand a few foundational ideas. If you already know these, you can skim this section quickly.

### What is HTML?

HTML stands for **HyperText Markup Language**. It is the language we use to describe the structure of a webpage. Think of HTML as the skeleton of your website — it tells the browser "here is a heading, here is a paragraph, here is an image."

### What is a Tag?

A **tag** is a special keyword wrapped inside angle brackets `< >`. Most HTML tags come in pairs: an **opening tag** and a **closing tag**.

```html
<p>This is a paragraph.</p>
```

- `<p>` → opening tag (start of the paragraph)
- `This is a paragraph.` → the content
- `</p>` → closing tag (end of the paragraph, note the forward slash `/`)

### What is an Element?

An **element** is the complete combination of opening tag + content + closing tag.

```html
<h1>Welcome to My Website</h1>
```

This entire line is one element.

### What is CSS?

**CSS** stands for **Cascading Style Sheets**. While HTML creates the structure of your page, CSS controls how it *looks* — colours, sizes, positions, and spacing. In this lesson, we will use a little CSS to arrange our layout elements side by side.

### What is a Semantic Element?

A **semantic element** is an HTML tag that clearly *describes its own meaning*. For example, `<nav>` tells both the browser and any human reading the code: "this is the navigation area." This is different from a `<div>`, which says nothing about what is inside it.

Semantic elements make your code easier to read, easier to maintain, and better for accessibility (for example, screen readers used by visually impaired users can understand the structure better).

---

## Part 1: Conceptual Understanding — What Is a Web Page Layout?

### The Newspaper Analogy

Imagine a printed newspaper. It has:

- A **masthead** at the top with the newspaper's name
- A **navigation** strip showing section names (Sports, Finance, World)
- **Main articles** in the centre
- **Sidebar** content on the side (advertisements, related stories)
- A **footer** at the bottom with contact information

A webpage is exactly the same idea, just on a screen. Instead of cutting paper into sections, we use HTML elements to define those zones.

### Visual Representation of a Web Layout

```
+------------------------------------------+
|            <header>                      |
|      Website Name / Logo / Banner        |
+------------------------------------------+
|   <nav>                                  |
|   Home | About | Services | Contact      |
+------------------------------------------+
|   <section> or <article>  |  <aside>    |
|                            |             |
|   Main content goes here   |  Sidebar   |
|   Articles, text, images   |  Extra     |
|   go in this larger area   |  content   |
|                            |             |
+------------------------------------------+
|            <footer>                      |
|      Copyright | Contact | Links         |
+------------------------------------------+
```

This is the standard layout you will see on most professional websites.

---

## Part 2: The Eight HTML Semantic Layout Elements

HTML5 introduced a set of **semantic layout elements** — special tags that each represent a different zone of a webpage. Let's study each one individually.

---

### 2.1 `<header>` — The Top Section

**What is it?**
The `<header>` element defines the top area of a page or section. It usually contains the website's name (logo), a tagline, and sometimes navigation links.

**Why does it exist?**
Before HTML5, developers used `<div id="header">` and had to guess what was inside. The `<header>` tag makes it instantly obvious.

**Simple Example:**

```html
<!DOCTYPE html>
<html>
<body>

  <header>
    <h1>My Awesome Website</h1>
    <p>Your daily source of awesome content</p>
  </header>

</body>
</html>
```

**Expected Output in browser:**

```
My Awesome Website
Your daily source of awesome content
```

The text appears at the top of the page in a heading style.

> **Tip:** You can have multiple `<header>` elements on a page — one for the whole page AND one inside each `<article>` or `<section>`.

---

### 2.2 `<nav>` — The Navigation Menu

**What is it?**
The `<nav>` element contains a set of navigation links — buttons or links that help the user move around the website.

**Why does it exist?**
Screen readers and search engines use `<nav>` to understand "these links are for navigating the site." This improves accessibility and SEO (Search Engine Optimisation).

**Simple Example:**

```html
<nav>
  <a href="/home">Home</a>
  <a href="/about">About</a>
  <a href="/contact">Contact</a>
</nav>
```

**Expected Output in browser:**

```
Home   About   Contact
```

Three clickable links appear side by side (browsers render links inline by default).

---

### 2.3 `<section>` — A Thematic Group of Content

**What is it?**
The `<section>` element defines a standalone thematic grouping of content. Think of it as a "chapter" in a book.

**Why does it exist?**
When your page has multiple topics, you can wrap each topic in a `<section>` to keep them organised and separated.

**Simple Example:**

```html
<section>
  <h2>About Us</h2>
  <p>We are a company that builds amazing websites.</p>
</section>

<section>
  <h2>Our Services</h2>
  <p>We offer design, development, and hosting.</p>
</section>
```

**Expected Output in browser:**

```
About Us
We are a company that builds amazing websites.

Our Services
We offer design, development, and hosting.
```

Two clearly separated sections of content.

> **Thinking Prompt:** What happens if you put both sections inside a single `<div>` instead? The content would look the same visually, but the meaning would be lost to machines reading the code.

---

### 2.4 `<article>` — Independent, Self-Contained Content

**What is it?**
The `<article>` element defines content that is complete and self-contained — meaning you could take it out of the page, and it would still make sense on its own.

**Why does it exist?**
Think about a blog post, a news story, or a product review. These can stand alone. If you copied a blog post and sent it in an email, it still makes sense. That's an `<article>`.

**Key Difference from `<section>`:**

| `<section>` | `<article>` |
|-------------|-------------|
| Groups related content | Contains self-contained content |
| Part of a bigger whole | Makes sense on its own |
| Like a chapter | Like a newspaper story |

**Simple Example:**

```html
<article>
  <h2>10 Tips for Better HTML</h2>
  <p>Published on April 19, 2026</p>
  <p>HTML is the backbone of the web. Here are ten tips to write it better...</p>
</article>
```

**Expected Output in browser:**

```
10 Tips for Better HTML
Published on April 19, 2026
HTML is the backbone of the web. Here are ten tips to write it better...
```

---

### 2.5 `<aside>` — Sidebar Content

**What is it?**
The `<aside>` element contains content that is related to, but not part of, the main content. It is typically displayed as a sidebar.

**Why does it exist?**
On a news website, the main area has the article, while the sidebar has "related articles," "trending topics," or advertisements. The `<aside>` element holds that sidebar content.

**Simple Example:**

```html
<article>
  <h2>The History of HTML</h2>
  <p>HTML was created by Tim Berners-Lee in 1991...</p>
</article>

<aside>
  <h3>Related Articles</h3>
  <ul>
    <li>What is CSS?</li>
    <li>Introduction to JavaScript</li>
  </ul>
</aside>
```

**Expected Output in browser:**

```
The History of HTML
HTML was created by Tim Berners-Lee in 1991...

Related Articles
• What is CSS?
• Introduction to JavaScript
```

(Without CSS, these will stack vertically. We'll position them side by side later with CSS.)

---

### 2.6 `<footer>` — The Bottom Section

**What is it?**
The `<footer>` element defines the bottom area of a page or section. It usually contains copyright information, contact details, and links to privacy policies.

**Why does it exist?**
Just like `<header>`, `<footer>` makes the bottom section of your page clearly labelled and easy to style.

**Simple Example:**

```html
<footer>
  <p>&copy; 2026 My Awesome Website. All rights reserved.</p>
  <p>Contact: info@mywebsite.com</p>
</footer>
```

**Expected Output in browser:**

```
© 2026 My Awesome Website. All rights reserved.
Contact: info@mywebsite.com
```

> **Note:** `&copy;` is the HTML entity for the copyright symbol ©.

---

### 2.7 `<details>` — Collapsible Content

**What is it?**
The `<details>` element creates a collapsible widget — a block of content that is hidden by default and can be shown when the user clicks on it.

**Why does it exist?**
When you have a FAQ (Frequently Asked Questions) section, you don't want to show all answers at once. `<details>` lets users click to expand only the answer they need.

**Simple Example:**

```html
<details>
  <summary>What is HTML?</summary>
  <p>HTML stands for HyperText Markup Language. It is the standard language for creating webpages.</p>
</details>
```

**Expected Output in browser (before click):**

```
▶ What is HTML?
```

**Expected Output in browser (after clicking):**

```
▼ What is HTML?
  HTML stands for HyperText Markup Language. It is the standard language for creating webpages.
```

The browser automatically adds a triangle (▶/▼) to show the toggle state.

---

### 2.8 `<summary>` — The Visible Label for `<details>`

**What is it?**
The `<summary>` element works inside `<details>`. It defines the clickable label that the user sees before expanding.

**Why does it exist?**
Without `<summary>`, the browser shows a default label like "Details". Using `<summary>` lets you write your own custom label.

**Simple Example:**

```html
<details>
  <summary>Click to see the answer</summary>
  <p>The answer is: 42.</p>
</details>
```

**Expected Output (before click):**

```
▶ Click to see the answer
```

**Expected Output (after click):**

```
▼ Click to see the answer
  The answer is: 42.
```

---

### Quick Reference — All 8 Layout Elements

| Element | Purpose | Real-World Example |
|---------|----------|--------------------|
| `<header>` | Top zone of page/section | Website logo and tagline |
| `<nav>` | Navigation links | Menu bar with Home, About, Contact |
| `<section>` | Grouped thematic content | "Our Services" section |
| `<article>` | Self-contained content | A blog post or news story |
| `<aside>` | Sidebar / related content | Trending topics sidebar |
| `<footer>` | Bottom zone of page/section | Copyright and contact info |
| `<details>` | Collapsible hidden content | FAQ accordion |
| `<summary>` | Label for `<details>` | "Click to expand" text |

---

## Part 3: HTML Layout Techniques

Now that you know what the semantic elements are, the next question is: **How do we arrange them visually on the screen?**

Without any CSS, all HTML elements stack vertically — one on top of another, like a stack of boxes. But websites show content side by side (like a main article column next to a sidebar). To achieve this, we need CSS layout techniques.

There are **four main techniques** for creating multi-column HTML layouts:

1. CSS Frameworks
2. CSS Float Layout
3. CSS Flexbox Layout
4. CSS Grid Layout

Let's study each one.

---

### Technique 1: CSS Frameworks

**What is it?**
A CSS Framework is a pre-written collection of CSS code that someone else has already built. Instead of writing all your layout CSS from scratch, you include the framework and use its ready-made classes.

**Why use it?**
If you want to create a professional layout quickly — without deep CSS knowledge — a framework lets you do it in minutes.

**Popular frameworks include:**
- **Bootstrap** — the most widely used; great for responsive designs
- **W3.CSS** — a lightweight framework by W3Schools; simple and clean
- **Tailwind CSS** — a utility-first framework popular with modern developers

**Simple Example using W3.CSS:**

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
</head>
<body>

  <div class="w3-container w3-blue">
    <h1>Header</h1>
  </div>

  <div class="w3-row">
    <div class="w3-col m8">
      <p>Main Content Area (8/12 width)</p>
    </div>
    <div class="w3-col m4">
      <p>Sidebar (4/12 width)</p>
    </div>
  </div>

  <div class="w3-container w3-dark-grey">
    <p>Footer</p>
  </div>

</body>
</html>
```

**Expected Output:**

```
[Blue Header Bar]
[Main Content (wide)] [Sidebar (narrow)]
[Dark Grey Footer]
```

The `w3-row` class creates a horizontal row. `w3-col m8` means "take 8 out of 12 columns of width." This is the 12-column grid system most frameworks use.

**Pros:**
- Very fast to build layouts
- Looks professional with little effort
- Built-in responsive design (adapts to mobile)

**Cons:**
- You depend on someone else's CSS
- May include features you don't need (larger file size)
- Less control over fine details

---

### Technique 2: CSS Float Layout

**What is it?**
The `float` CSS property was originally designed to wrap text around images (like in a magazine). Web developers discovered they could also use it to create side-by-side columns.

**How does it work?**
When you `float` an element to the left or right, it is removed from the normal document flow and moved to that side. Other content wraps around it.

**Key CSS Properties:**
- `float: left;` — moves the element to the left
- `float: right;` — moves the element to the right
- `clear: both;` — stops the floating effect (used on the footer to prevent it from wrapping around floated columns)

**Simple Example — Two Columns:**

```html
<!DOCTYPE html>
<html>
<head>
<style>
  * {
    box-sizing: border-box; /* Makes width calculations easier */
  }

  nav {
    float: left;
    width: 25%;
    background-color: #f0f0f0;
    padding: 10px;
  }

  article {
    float: left;
    width: 75%;
    padding: 10px;
  }

  footer {
    clear: both; /* Stop the float — footer goes below both columns */
    background-color: #333;
    color: white;
    text-align: center;
    padding: 10px;
  }
</style>
</head>
<body>

  <header>
    <h1>My City Blog</h1>
  </header>

  <nav>
    <ul>
      <li>London</li>
      <li>Paris</li>
      <li>Tokyo</li>
    </ul>
  </nav>

  <article>
    <h2>London</h2>
    <p>London is the capital city of England. It is the most populous city
       in the United Kingdom, with a metropolitan area of over 13 million inhabitants.</p>
  </article>

  <footer>
    <p>Footer — Copyright 2026</p>
  </footer>

</body>
</html>
```

**Expected Output in browser:**

```
My City Blog
+------------------+----------------------------------+
| • London         | London                           |
| • Paris          | London is the capital city of    |
| • Tokyo          | England. It is the most          |
|                  | populous city in the UK...       |
+------------------+----------------------------------+
           Footer — Copyright 2026
```

**Line-by-line CSS explanation:**

- `* { box-sizing: border-box; }` — The `*` targets ALL elements. `box-sizing: border-box` means the padding is included inside the element's width, so `25% + 75% = 100%` exactly (without this, padding would push them to 100%+, breaking the layout).
- `float: left;` — moves the element to the left side
- `width: 25%;` — nav takes 25% of the page width
- `width: 75%;` — article takes 75% (25% + 75% = 100%)
- `clear: both;` — the footer clears the float, forcing it below both columns

**Pros:**
- Works in all browsers, even very old ones
- Simple to understand for beginners

**Cons:**
- Floated elements are "out of flow" — positioning can be unpredictable
- You must manually clear floats or the layout breaks
- Less flexible than modern techniques

---

### Technique 3: CSS Flexbox Layout

**What is it?**
**Flexbox** (short for "Flexible Box Layout") is a modern CSS layout system that makes it easy to arrange elements in a row or column, distribute space between them, and align them precisely.

**Why is it better than Float?**
Flexbox was designed specifically for layout. It handles equal-height columns, centring, and distribution automatically — things that Float struggles with.

**Key CSS Properties:**

| Property | What it does |
|----------|-------------|
| `display: flex;` | Activates Flexbox on a container |
| `flex-direction: row;` | Children go left to right (default) |
| `flex-direction: column;` | Children go top to bottom |
| `flex: 1;` | This child takes equal share of remaining space |
| `flex: 3;` | This child takes 3x more space than flex: 1 |

**Simple Example — Two Columns with Flexbox:**

```html
<!DOCTYPE html>
<html>
<head>
<style>
  body {
    font-family: Arial, sans-serif;
  }

  header {
    background-color: #2c3e50;
    color: white;
    padding: 15px;
  }

  nav {
    background-color: #ecf0f1;
    padding: 15px;
  }

  .content-wrapper {
    display: flex; /* Activate Flexbox on this container */
  }

  article {
    flex: 3; /* Takes 3 parts of available space */
    padding: 15px;
  }

  aside {
    flex: 1; /* Takes 1 part of available space */
    background-color: #f9f9f9;
    padding: 15px;
  }

  footer {
    background-color: #2c3e50;
    color: white;
    text-align: center;
    padding: 10px;
  }
</style>
</head>
<body>

  <header>
    <h1>My City Blog</h1>
  </header>

  <nav>
    <a href="#">London</a> |
    <a href="#">Paris</a> |
    <a href="#">Tokyo</a>
  </nav>

  <div class="content-wrapper">

    <article>
      <h2>London</h2>
      <p>London is the capital city of England, home to over 9 million people.
         It sits along the River Thames and has been settled for over 2,000 years.</p>
    </article>

    <aside>
      <h3>Quick Facts</h3>
      <p>Country: England</p>
      <p>Founded: 43 AD</p>
    </aside>

  </div>

  <footer>
    <p>&copy; 2026 City Blog</p>
  </footer>

</body>
</html>
```

**Expected Output in browser:**

```
My City Blog (dark header)
London | Paris | Tokyo  (nav bar)
+------------------------------+----------+
|  London                      | Quick    |
|  London is the capital city  | Facts    |
|  of England, home to over    | Country: |
|  9 million people...         | England  |
+------------------------------+----------+
       © 2026 City Blog (dark footer)
```

**Line-by-line explanation:**

- `display: flex;` on `.content-wrapper` — tells the browser: "arrange the children of this div using Flexbox rules"
- `flex: 3;` on `article` — the article takes 3 "shares" of the available horizontal space
- `flex: 1;` on `aside` — the aside takes 1 "share"; so article:aside = 3:1 (article is 3× wider)

> **Thinking Prompt:** What would happen if you changed `flex: 3` to `flex: 1`? Both columns would become equal width. Try it!

**Pros:**
- Elements behave predictably
- Equal-height columns happen automatically
- Centring is easy
- Great for one-dimensional layouts (either row OR column)

**Cons:**
- Slightly more to learn than float
- Not ideal for complex two-dimensional grid designs

---

### Technique 4: CSS Grid Layout

**What is it?**
CSS Grid is the most powerful layout system in CSS. It lets you define a **two-dimensional grid** — with both rows AND columns — and place elements precisely within that grid.

**Analogy:** Think of CSS Grid like a spreadsheet. You define the rows and columns, then place your content into specific cells.

**Key CSS Properties:**

| Property | What it does |
|----------|-------------|
| `display: grid;` | Activates Grid on a container |
| `grid-template-columns: ...` | Defines column widths |
| `grid-template-rows: ...` | Defines row heights |
| `grid-column: span 2;` | This element spans 2 columns |
| `fr` | "fraction" unit — divides remaining space |

**Simple Example — Full Page Grid:**

```html
<!DOCTYPE html>
<html>
<head>
<style>
  .page-container {
    display: grid; /* Activate Grid */
    grid-template-columns: 1fr 3fr; /* 2 columns: sidebar (1 part), main (3 parts) */
    grid-template-rows: auto auto auto; /* 3 rows: header, content, footer */
    gap: 10px; /* Space between grid cells */
    min-height: 100vh;
  }

  header {
    grid-column: 1 / 3; /* Header spans BOTH columns (column 1 to column 3) */
    background-color: #3498db;
    color: white;
    padding: 15px;
  }

  nav {
    background-color: #ecf0f1;
    padding: 15px;
  }

  article {
    padding: 15px;
  }

  footer {
    grid-column: 1 / 3; /* Footer also spans both columns */
    background-color: #2c3e50;
    color: white;
    text-align: center;
    padding: 10px;
  }
</style>
</head>
<body>

  <div class="page-container">

    <header>
      <h1>My City Blog</h1>
    </header>

    <nav>
      <ul>
        <li><a href="#">London</a></li>
        <li><a href="#">Paris</a></li>
        <li><a href="#">Tokyo</a></li>
      </ul>
    </nav>

    <article>
      <h2>London</h2>
      <p>London is the capital city of England. Standing on the River Thames,
         London has been a major settlement for two millennia, going back to
         its founding by the Romans, who named it Londinium.</p>
    </article>

    <footer>
      <p>&copy; 2026 City Blog. All Rights Reserved.</p>
    </footer>

  </div>

</body>
</html>
```

**Expected Output in browser:**

```
+-----------------------------------------------+
|  My City Blog (blue header — full width)      |
+---------------+-------------------------------+
|  • London     |  London                       |
|  • Paris      |  London is the capital city   |
|  • Tokyo      |  of England. Standing on the  |
|               |  River Thames...              |
+---------------+-------------------------------+
|  © 2026 City Blog (dark footer — full width)  |
+-----------------------------------------------+
```

**Line-by-line explanation:**

- `display: grid;` — activates the Grid system
- `grid-template-columns: 1fr 3fr;` — creates 2 columns. `1fr` means 1 fraction of the space, `3fr` means 3 fractions. So the nav is 1/4 the width, the article is 3/4.
- `gap: 10px;` — adds 10 pixels of space between grid cells
- `grid-column: 1 / 3;` — makes the header start at column line 1 and end at column line 3 (i.e., span both columns)

**Pros:**
- Most powerful and flexible layout tool
- Perfect for complex two-dimensional layouts
- Clean, readable code
- Modern browsers support it fully

**Cons:**
- More to learn upfront than Float or Flexbox
- Slightly newer (very old browsers may not fully support it)

---

### Comparison Table: Which Technique to Use?

| Technique | Best For | Difficulty | Browser Support |
|-----------|----------|------------|-----------------|
| CSS Framework | Quick prototypes, beginners | Easy | Excellent |
| CSS Float | Simple two-column layouts | Easy | Excellent (including old browsers) |
| CSS Flexbox | One-direction layouts, nav bars | Medium | Excellent |
| CSS Grid | Complex page layouts | Medium–Advanced | Very good |

> **Real-World Note:** Modern professional projects almost always use **Flexbox for components** (like navigation bars and card rows) and **CSS Grid for full page layout**. CSS Frameworks like Bootstrap are common in business applications. Float is considered "old school" and is used less in new projects.

---

## Part 4: Guided Practice Exercises

Now let's practice what we've learned with structured exercises. Start each one, complete the steps, then check your output.

---

### Exercise 1 — Identify the Layout Elements

**Objective:** Recognise semantic layout elements in existing code.

**Scenario:** Your friend sent you this HTML. Identify what each layout element does.

```html
<!DOCTYPE html>
<html>
<body>

  <header>
    <h1>Fresh Food Blog</h1>
  </header>

  <nav>
    <a href="#">Recipes</a>
    <a href="#">Tips</a>
    <a href="#">About</a>
  </nav>

  <section>
    <article>
      <h2>How to Make Perfect Rice</h2>
      <p>Rice is a staple in millions of households worldwide...</p>
    </article>

    <aside>
      <h3>Most Popular</h3>
      <p>1. Jollof Rice</p>
      <p>2. Fried Rice</p>
    </aside>
  </section>

  <footer>
    <p>Fresh Food Blog &copy; 2026</p>
  </footer>

</body>
</html>
```

**Steps:**

1. Copy this code into a `.html` file on your computer.
2. Open it in a browser.
3. Answer these questions:

**Self-Check Questions:**

- Which element contains "Fresh Food Blog"? _______________
- Which element contains the links "Recipes | Tips | About"? _______________
- Which element wraps both the `<article>` and `<aside>`? _______________
- Which element contains "How to Make Perfect Rice"? _______________
- Which element contains "Most Popular"? _______________
- Which element contains the copyright notice? _______________

**Answers:** header, nav, section, article, aside, footer.

---

### Exercise 2 — Build a Two-Column Layout with Flexbox

**Objective:** Create a simple two-column layout using Flexbox.

**Scenario:** You are building a simple personal portfolio page. It needs a left sidebar with your name and links, and a right main area with your content.

**Steps:**

1. Create a new file called `portfolio.html`
2. Add the structure below
3. Add the CSS styles
4. Open in browser and verify the output

**Starter Code:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Portfolio</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }

    header {
      background-color: #1a1a2e;
      color: white;
      padding: 20px;
      text-align: center;
    }

    .main-content {
      display: flex;           /* Step 1: Activate Flexbox */
    }

    nav {
      flex: 1;                 /* Step 2: Sidebar takes 1 share */
      background-color: #16213e;
      color: white;
      padding: 20px;
      min-height: 400px;
    }

    nav a {
      display: block;          /* Each link on its own line */
      color: #a8dadc;
      margin-bottom: 10px;
      text-decoration: none;
    }

    section {
      flex: 3;                 /* Step 3: Main area takes 3 shares */
      padding: 20px;
    }

    footer {
      background-color: #1a1a2e;
      color: white;
      text-align: center;
      padding: 15px;
    }
  </style>
</head>
<body>

  <header>
    <h1>Jane Doe — Web Developer</h1>
  </header>

  <div class="main-content">

    <nav>
      <h3>Menu</h3>
      <a href="#">About Me</a>
      <a href="#">Projects</a>
      <a href="#">Skills</a>
      <a href="#">Contact</a>
    </nav>

    <section>
      <h2>About Me</h2>
      <p>Hello! I am Jane, a passionate web developer from Lagos, Nigeria.
         I love building clean, fast websites that help businesses grow online.</p>

      <h2>Featured Project</h2>
      <p>I recently built a school management system for a local secondary school,
         helping them digitise their student records.</p>
    </section>

  </div>

  <footer>
    <p>&copy; 2026 Jane Doe. Built with HTML and CSS.</p>
  </footer>

</body>
</html>
```

**Expected Output:**

```
+--------------------------------------------------+
|    Jane Doe — Web Developer (dark blue header)   |
+------------------+-------------------------------+
|  Menu            |  About Me                     |
|  About Me        |  Hello! I am Jane, a          |
|  Projects        |  passionate web developer...  |
|  Skills          |                               |
|  Contact         |  Featured Project             |
|                  |  I recently built a school... |
+------------------+-------------------------------+
|  © 2026 Jane Doe. Built with HTML and CSS.       |
+--------------------------------------------------+
```

**Self-Check Questions:**

- What does `display: flex;` on `.main-content` do?
- Why is `flex: 3;` on `section` and `flex: 1;` on `nav`? What ratio does that create?
- What would happen if you removed `display: block;` from `nav a`?

**What-If Challenges:**

- Change `flex: 3` on section to `flex: 1`. What happens to the layout?
- Add a second `<nav>` link for "Blog." Where does it appear?
- Change the header background to `#e63946`. What colour appears?

---

### Exercise 3 — Add a `<details>` FAQ Section

**Objective:** Use `<details>` and `<summary>` to create a collapsible FAQ.

**Scenario:** Add a Frequently Asked Questions section to a webpage.

**Code:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>FAQ Page</title>
  <style>
    body { font-family: Arial; padding: 20px; }
    details {
      margin-bottom: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      padding: 10px;
    }
    summary {
      font-weight: bold;
      cursor: pointer;    /* Changes mouse cursor to hand on hover */
      color: #2c3e50;
    }
    details p {
      margin-top: 10px;
      color: #555;
    }
  </style>
</head>
<body>

  <h1>Frequently Asked Questions</h1>

  <details>
    <summary>What is HTML?</summary>
    <p>HTML stands for HyperText Markup Language. It is the standard
       language for creating the structure of web pages.</p>
  </details>

  <details>
    <summary>What is CSS?</summary>
    <p>CSS stands for Cascading Style Sheets. It controls how HTML
       elements look — their colours, sizes, and positions.</p>
  </details>

  <details>
    <summary>Do I need to buy software to code HTML?</summary>
    <p>No! You only need a free text editor (like VS Code or Notepad++)
       and a web browser. Both are free to download.</p>
  </details>

</body>
</html>
```

**Expected Output (before clicking):**

```
Frequently Asked Questions
▶ What is HTML?
▶ What is CSS?
▶ Do I need to buy software to code HTML?
```

**Expected Output (after clicking "What is HTML?"):**

```
Frequently Asked Questions
▼ What is HTML?
  HTML stands for HyperText Markup Language. It is the standard
  language for creating the structure of web pages.
▶ What is CSS?
▶ Do I need to buy software to code HTML?
```

**Self-Check Questions:**

- What tag creates the clickable label?
- What happens to the triangle (▶) when you click to expand?
- Can you have multiple `<details>` elements on the same page?

---

## Part 5: Mini Project — Build a Complete City Guide Page

Now let's bring everything together! You will build a complete, real-world style webpage from scratch.

**Project Title:** Lagos City Guide

**Final Result:** A complete webpage with header, navigation, main article, sidebar, footer, and a collapsible fun facts section.

---

### Stage 1 — Setup the HTML Structure

Create a file called `lagos-guide.html` and type this skeleton:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Lagos City Guide</title>
</head>
<body>

  <!-- HEADER -->
  <header>
    <h1>Lagos City Guide</h1>
    <p>Your complete guide to the heart of Nigeria</p>
  </header>

  <!-- NAVIGATION -->
  <nav>
    <a href="#">About Lagos</a>
    <a href="#">Things to Do</a>
    <a href="#">Food</a>
    <a href="#">Transport</a>
  </nav>

  <!-- MAIN CONTENT AREA -->
  <div class="content-area">

    <!-- ARTICLE -->
    <article>
      <h2>About Lagos</h2>
      <p>Lagos is the largest city in Nigeria and one of the most populous cities
         in Africa. It is a vibrant, fast-moving metropolis known for its music,
         food, fashion, and entrepreneurial spirit.</p>

      <h3>History</h3>
      <p>Lagos was originally a collection of islands settled by the Awori people.
         The Portuguese arrived in the 15th century, naming it "Lagos" after a city
         in Portugal. It later became a major centre during the colonial era.</p>

      <h3>Fun Facts</h3>
      <details>
        <summary>Click to reveal Lagos facts</summary>
        <ul>
          <li>Lagos has a population of over 15 million people.</li>
          <li>It was Nigeria's capital until 1991 when Abuja took over.</li>
          <li>Lagos State has the largest economy of any Nigerian state.</li>
          <li>Nollywood, Nigeria's film industry, is based in Lagos.</li>
        </ul>
      </details>
    </article>

    <!-- SIDEBAR -->
    <aside>
      <h3>Quick Info</h3>
      <p><strong>Country:</strong> Nigeria</p>
      <p><strong>State:</strong> Lagos State</p>
      <p><strong>Language:</strong> Yoruba, English</p>
      <p><strong>Currency:</strong> Naira (₦)</p>
      <p><strong>Climate:</strong> Tropical</p>

      <h3>Must Visit</h3>
      <ul>
        <li>Lekki Conservation Centre</li>
        <li>National Museum Lagos</li>
        <li>Tarkwa Bay Beach</li>
        <li>Nike Art Gallery</li>
      </ul>
    </aside>

  </div>

  <!-- FOOTER -->
  <footer>
    <p>&copy; 2026 Lagos City Guide. Made with HTML &amp; CSS.</p>
  </footer>

</body>
</html>
```

**Milestone 1 Output (no CSS yet):** Everything stacks vertically. You will see all the content but it won't look like a two-column layout yet. That's fine — structure first!

---

### Stage 2 — Add CSS Styling

Now add CSS inside the `<head>` section, right before `</head>`:

```html
<style>
  /* Reset default browser spacing */
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
    color: #333;
  }

  /* ========== HEADER ========== */
  header {
    background-color: #009900;   /* Nigerian green */
    color: white;
    padding: 20px 30px;
  }

  header h1 {
    font-size: 2em;
  }

  header p {
    font-size: 1.1em;
    margin-top: 5px;
    opacity: 0.85;
  }

  /* ========== NAVIGATION ========== */
  nav {
    background-color: #006600;
    padding: 12px 30px;
  }

  nav a {
    color: white;
    text-decoration: none;
    margin-right: 20px;
    font-weight: bold;
    font-size: 0.95em;
  }

  nav a:hover {
    text-decoration: underline;
  }

  /* ========== CONTENT AREA — Flexbox Layout ========== */
  .content-area {
    display: flex;          /* Activate Flexbox */
    gap: 20px;              /* 20px space between columns */
    padding: 20px 30px;
    max-width: 1100px;
    margin: 0 auto;         /* Centre the content area */
  }

  /* ========== ARTICLE (Main Column) ========== */
  article {
    flex: 3;                /* Takes 3/4 of the space */
    background-color: white;
    padding: 25px;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  }

  article h2 {
    color: #009900;
    border-bottom: 2px solid #009900;
    padding-bottom: 8px;
    margin-bottom: 15px;
  }

  article h3 {
    color: #006600;
    margin-top: 20px;
    margin-bottom: 10px;
  }

  article p {
    line-height: 1.7;
    margin-bottom: 15px;
  }

  /* ========== DETAILS / SUMMARY ========== */
  details {
    background-color: #f0fff0;
    border: 1px solid #009900;
    border-radius: 5px;
    padding: 12px;
    margin-top: 10px;
  }

  summary {
    font-weight: bold;
    cursor: pointer;
    color: #006600;
  }

  details ul {
    margin-top: 10px;
    padding-left: 20px;
  }

  details li {
    margin-bottom: 6px;
    line-height: 1.5;
  }

  /* ========== ASIDE (Sidebar) ========== */
  aside {
    flex: 1;                /* Takes 1/4 of the space */
    background-color: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    height: fit-content;    /* Don't stretch taller than content */
  }

  aside h3 {
    color: #009900;
    border-bottom: 1px solid #009900;
    padding-bottom: 6px;
    margin-bottom: 12px;
  }

  aside p {
    font-size: 0.95em;
    margin-bottom: 8px;
    line-height: 1.5;
  }

  aside ul {
    padding-left: 18px;
  }

  aside li {
    margin-bottom: 6px;
    font-size: 0.95em;
  }

  /* ========== FOOTER ========== */
  footer {
    background-color: #006600;
    color: white;
    text-align: center;
    padding: 18px;
    margin-top: 20px;
  }
</style>
```

**Milestone 2 Output:**

```
+--------------------------------------------------------+
|  Lagos City Guide (green header)                       |
|  Your complete guide to the heart of Nigeria           |
+--------------------------------------------------------+
|  About Lagos | Things to Do | Food | Transport (dark nav)|
+----------------------------------+-----------+
|  About Lagos                     | Quick Info|
|  Lagos is the largest city...    | Country:  |
|                                  | Nigeria   |
|  History                         | State:    |
|  Lagos was originally...         | Lagos     |
|                                  | ...       |
|  Fun Facts                       | Must Visit|
|  ▶ Click to reveal Lagos facts   | • Lekki   |
|                                  | • Museum  |
+----------------------------------+-----------+
|  © 2026 Lagos City Guide. Made with HTML & CSS. (green)|
+--------------------------------------------------------+
```

---

### Stage 3 — Test and Enhance

Now try these enhancements:

1. **Click "Click to reveal Lagos facts"** — the list should expand with 4 facts.
2. **Add a second `<article>`** below the first one with a "Things to Do in Lagos" section.
3. **Change the green colour** (`#009900`) to match a colour you prefer.
4. **Add one more Quick Info item** to the `<aside>`.

**Optional Advanced Extension:**
Convert the layout from Flexbox to CSS Grid:

```css
/* Replace .content-area styles with: */
.content-area {
  display: grid;
  grid-template-columns: 3fr 1fr;  /* 3/4 for article, 1/4 for aside */
  gap: 20px;
  padding: 20px 30px;
  max-width: 1100px;
  margin: 0 auto;
}
```

This produces the same visual result using Grid instead of Flexbox — notice how the code changes slightly but the output looks the same!

---

## Part 6: Common Beginner Mistakes

Here are the most common mistakes beginners make with HTML layout — and how to fix them.

---

### Mistake 1 — Forgetting `clear: both` When Using Float

**Broken Code:**

```html
<style>
  nav   { float: left; width: 30%; }
  article { float: left; width: 70%; }
  /* No clear on footer! */
</style>

<nav>Sidebar</nav>
<article>Main Content</article>
<footer>Footer</footer>  <!-- Footer tries to wrap alongside floated elements! -->
```

**Problem:** The footer floats up next to the sidebar instead of appearing below both columns.

**Fixed Code:**

```html
<style>
  nav     { float: left; width: 30%; }
  article { float: left; width: 70%; }
  footer  { clear: both; }  /* ← This fixes it! */
</style>
```

---

### Mistake 2 — Forgetting `display: flex` on the Container

**Broken Code:**

```html
<style>
  nav     { flex: 1; }   /* This has no effect! */
  article { flex: 3; }   /* This has no effect! */
</style>

<div class="wrapper">
  <nav>Sidebar</nav>
  <article>Main Content</article>
</div>
```

**Problem:** The `flex` property on children has NO effect unless the *parent container* has `display: flex`.

**Fixed Code:**

```html
<style>
  .wrapper { display: flex; }   /* ← Add this to the PARENT */
  nav      { flex: 1; }
  article  { flex: 3; }
</style>
```

---

### Mistake 3 — Float Percentages Adding Up to More Than 100%

**Broken Code:**

```html
<style>
  nav     { float: left; width: 30%; padding: 20px; }
  article { float: left; width: 70%; padding: 20px; }
</style>
```

**Problem:** With `padding: 20px`, the actual total width becomes more than 100%, so `article` wraps below `nav`.

**Fixed Code:**

```html
<style>
  * { box-sizing: border-box; }  /* ← Padding is now included in width */
  nav     { float: left; width: 30%; padding: 20px; }
  article { float: left; width: 70%; padding: 20px; }
</style>
```

---

### Mistake 4 — Using `<div>` When a Semantic Element Exists

**Incorrect (but works visually):**

```html
<div id="header">
  <h1>My Website</h1>
</div>

<div id="nav">
  <a href="#">Home</a>
</div>
```

**Better (semantic):**

```html
<header>
  <h1>My Website</h1>
</header>

<nav>
  <a href="#">Home</a>
</nav>
```

Both look the same in the browser, but the semantic version is better for accessibility, SEO, and code readability.

---

### Mistake 5 — Putting `<summary>` Outside `<details>`

**Broken Code:**

```html
<summary>Click Me</summary>   <!-- WRONG — summary must be inside details -->
<details>
  <p>Hidden content here.</p>
</details>
```

**Fixed Code:**

```html
<details>
  <summary>Click Me</summary>   <!-- CORRECT — summary is the FIRST child of details -->
  <p>Hidden content here.</p>
</details>
```

---

## Part 7: Reflection Questions

Take a few minutes to think through these questions. Answering them helps cement your understanding.

1. **Why did HTML5 introduce semantic layout elements like `<header>`, `<nav>`, and `<footer>`?** What was wrong with just using `<div>` for everything?

2. **What is the difference between `<section>` and `<article>`?** Give a real-world example of when you would use each.

3. **If you were building a recipe website**, which layout elements would you use and where? Sketch out a structure (use text boxes like the ones in this lesson).

4. **Float was the original layout technique for columns.** Why did developers create Flexbox and Grid if Float already worked?

5. **CSS Grid uses `grid-column: 1 / 3;` to span columns.** In your own words, what does this mean?

6. **When would you choose a CSS Framework** (like Bootstrap) over writing your own CSS? What are the trade-offs?

7. **The `<details>` element creates collapsible content without any JavaScript.** Can you think of three situations where this would be useful on a real website?

---

## Completion Checklist

Go through this checklist before you consider this lesson complete:

- [ ] I can name all 8 HTML5 semantic layout elements and explain what each one does
- [ ] I understand the difference between `<section>` and `<article>`
- [ ] I understand when to use `<aside>` vs `<article>`
- [ ] I can use `<details>` and `<summary>` to create collapsible content
- [ ] I understand what CSS Float is and how `clear: both` fixes layout issues
- [ ] I can create a two-column layout using Flexbox (`display: flex`, `flex: 1`, `flex: 3`)
- [ ] I understand how CSS Grid uses `grid-template-columns` to define column widths
- [ ] I understand what `fr` units are in CSS Grid
- [ ] I completed Exercise 1 (identifying layout elements)
- [ ] I completed Exercise 2 (Flexbox portfolio layout)
- [ ] I completed Exercise 3 (FAQ with `<details>`)
- [ ] I built the Lagos City Guide mini-project
- [ ] I understand the 5 common beginner mistakes and how to avoid them
- [ ] I answered the reflection questions

---

## Lesson Summary

In this lesson, you learned how to structure and layout a complete webpage like a professional web developer.

**HTML5 Semantic Layout Elements** tell both the browser and human readers what each section of a webpage means. The eight elements are `<header>` (top zone), `<nav>` (navigation links), `<section>` (thematic content group), `<article>` (self-contained content), `<aside>` (sidebar content), `<footer>` (bottom zone), `<details>` (collapsible content), and `<summary>` (the label for `<details>`).

**Four Layout Techniques** let you arrange elements side by side on screen. CSS Frameworks like Bootstrap give you ready-made layout classes. CSS Float was the original column technique — you float elements left and use `clear: both` on footers. CSS Flexbox is a modern, reliable method — you apply `display: flex` to a parent and use `flex` values on children to control width ratios. CSS Grid is the most powerful — you define rows and columns with `grid-template-columns` and place elements precisely using `grid-column`.

**The most important takeaway:** always use semantic elements to give your HTML structure meaning, and choose your layout technique based on your project's needs — Flexbox for components, Grid for full-page layouts, frameworks for speed.

In the next lesson, you will learn about **Responsive Web Design** — how to make your layouts automatically adapt to different screen sizes, from large desktop monitors to small mobile phones.

---

*Sources: W3Schools HTML Layout Tutorial — https://www.w3schools.com/html/html_layout.asp*
