---
render_with_liquid: false
title: "Lesson 28: HTML Semantic Elements"
nav_order: 28
---

# Lesson 28: HTML Semantic Elements

---

## Lesson Introduction

Imagine you walk into a library. Every section has a clear label: **Fiction**, **Science**, **History**, **Reference**. Without these labels, books would be piled randomly — and finding what you need would be a nightmare.

HTML pages work the same way. Before modern HTML, developers used generic "mystery boxes" called `<div>` to build every part of a page. A `<div>` tells you absolutely nothing — it could be the header, a menu, a news story, or the footer. Nobody — not you, not a browser, not a search engine — could tell the difference just by reading the tag.

**Semantic HTML** solves this problem. A **semantic element** is an HTML tag whose name tells you exactly what kind of content it holds. Instead of a plain `<div>` box labelled with nothing, you use tags like `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<aside>`, and `<footer>` — each one describing its own purpose.

This lesson will teach you:
- What "semantic" means and why it matters
- Every important semantic HTML element, explained with simple analogies
- How to use each element with code examples and expected outputs
- How to build a full, properly structured webpage using semantic elements
- Common beginner mistakes and how to avoid them

By the end, you will write HTML that is cleaner, more accessible, easier to maintain, and better understood by browsers and search engines.

---

## Prerequisite Concepts

Before we dive in, let us quickly review two things you need to understand to follow this lesson easily.

### What is an HTML Element?

An HTML element is made up of an **opening tag**, some **content**, and a **closing tag**.

```html
<p>This is a paragraph.</p>
```

- `<p>` is the **opening tag** — it starts the element
- `This is a paragraph.` is the **content** — the actual text shown on the page
- `</p>` is the **closing tag** — it ends the element

The tag name (the letter or word inside `< >`) tells the browser what kind of content it is. `<p>` means paragraph. `<h1>` means a big top-level heading.

### What is a `<div>`?

A `<div>` is a generic container. It groups things together but says nothing about what those things are. Think of it as a plain cardboard box with no label.

```html
<div>
  <h2>Welcome to my website</h2>
  <p>Hello and thanks for visiting!</p>
</div>
```

The `<div>` here just wraps two elements. A browser has no idea if this is a header, a sidebar, or an article. It is just a box. That is the problem semantic elements solve.

---

## Conceptual Understanding

### What Does "Semantic" Mean?

The word **semantic** comes from Greek and means "having meaning" or "relating to meaning."

In everyday language:
- The word **"dog"** is semantic because it means something specific — a four-legged furry animal.
- A random squiggle has no semantics — it carries no meaning.

In HTML:
- `<article>` is semantic — it tells everyone "this is a self-contained article."
- `<div>` is not semantic — it means "some kind of container." That's all.

### Why Does It Matter? Three Big Reasons

**Reason 1 — Accessibility (helping people with disabilities)**

Many people use **screen readers** — special software that reads web pages out loud for people who cannot see the screen. Screen readers understand semantic HTML. When they encounter a `<nav>` element, they announce "Navigation." When they find a `<main>` element, they can jump straight to the main content.

If everything is wrapped in `<div>`, a screen reader cannot distinguish navigation from an article from a footer. The user hears an undifferentiated wall of content.

**Reason 2 — Search Engine Optimisation (SEO)**

Search engines like Google read the HTML of your page to understand what it is about. When Google finds `<article>` tags, it knows those are important, self-contained pieces of content worth indexing. When it finds `<nav>`, it understands those are navigation links. Well-structured semantic HTML helps search engines rank your page better.

**Reason 3 — Code Readability and Maintenance**

Compare these two snippets. Both do the same visual thing:

```html
<!-- Non-semantic version -->
<div id="header">
  <div id="nav">
    <div class="nav-link">Home</div>
  </div>
</div>
<div id="main">
  <div class="article">
    <div class="article-header">Title Here</div>
    <div class="article-body">Content here...</div>
  </div>
</div>
<div id="footer">Copyright 2025</div>
```

```html
<!-- Semantic version -->
<header>
  <nav>
    <a href="#">Home</a>
  </nav>
</header>
<main>
  <article>
    <header><h1>Title Here</h1></header>
    <p>Content here...</p>
  </article>
</main>
<footer>Copyright 2025</footer>
```

The semantic version is shorter, clearer, and immediately understandable. You do not need `id="header"` because the element IS a header. Another developer reading your code six months later will understand the structure instantly.

---

### Non-Semantic vs Semantic: A Visual Comparison

Think of a newspaper. It has clear, named sections:

| Newspaper Section | HTML Semantic Element |
|---|---|
| Masthead / Front Page Title | `<header>` |
| Navigation / Table of Contents | `<nav>` |
| Main Story / Feature Article | `<main>` + `<article>` |
| Topic Chapter (Sports, Finance) | `<section>` |
| Sidebar / "Also Read" Box | `<aside>` |
| Photo with Caption | `<figure>` + `<figcaption>` |
| Bottom of Page Credits | `<footer>` |
| Publication Date | `<time>` |
| Highlighted Text | `<mark>` |

Every one of these has a matching HTML semantic element. Let us learn them one by one.

---

## The Complete Semantic Elements Map

Here is a bird's-eye view of how semantic elements typically fit together in a real page layout:

```
┌──────────────────────────────────────────────────────┐
│                      <header>                        │
│          (Logo, Site Title, Tagline)                 │
├──────────────────────────────────────────────────────┤
│                        <nav>                         │
│          (Main navigation links)                     │
├───────────────────────────────┬──────────────────────┤
│                               │                      │
│           <main>              │      <aside>         │
│                               │    (Sidebar:         │
│   ┌───────────────────────┐   │  Related Links,      │
│   │      <article>        │   │  Ads, Tips)          │
│   │  ┌─────────────────┐  │   │                      │
│   │  │   <header>      │  │   │                      │
│   │  └─────────────────┘  │   │                      │
│   │  ┌─────────────────┐  │   │                      │
│   │  │   <section>     │  │   │                      │
│   │  └─────────────────┘  │   │                      │
│   │  ┌─────────────────┐  │   │                      │
│   │  │   <figure>      │  │   │                      │
│   │  │  <figcaption>   │  │   │                      │
│   │  └─────────────────┘  │   │                      │
│   └───────────────────────┘   │                      │
│                               │                      │
├───────────────────────────────┴──────────────────────┤
│                      <footer>                        │
│          (Copyright, Contact, Links)                 │
└──────────────────────────────────────────────────────┘
```

---

## Deep Dive: Every Semantic Element Explained

### 1. `<section>` — Thematic Grouping of Content

**What is it?**
A `<section>` groups related content together under a theme. According to the HTML standard, a section is "a thematic grouping of content, typically with a heading."

**Real-world analogy:** A chapter in a book. Chapter 1 covers one topic. Chapter 2 covers another. Each chapter is a section.

**When to use `<section>`:**
- Chapters of a long article
- Introduction, Body, and Conclusion parts of an essay
- Different topics on a single page (e.g., "About Us", "Our Services", "Contact")
- News categories (Sports, Finance, Technology)

**Simple Example:**

```html
<section>
  <h2>Introduction to Photosynthesis</h2>
  <p>Photosynthesis is the process by which plants make food using sunlight.</p>
</section>
```

**Expected output on the page:**
```
Introduction to Photosynthesis
Photosynthesis is the process by which plants make food using sunlight.
```

**Two sections example (like on a real page):**

```html
<section>
  <h1>WWF</h1>
  <p>The World Wide Fund for Nature (WWF) is an international organization
  working on issues regarding the conservation, research and restoration of
  the environment, formerly named the World Wildlife Fund. WWF was founded
  in 1961.</p>
</section>

<section>
  <h1>WWF's Panda Symbol</h1>
  <p>The Panda has become the symbol of WWF. The well-known panda logo of
  WWF originated from a panda named Chi Chi that was transferred from the
  Beijing Zoo to the London Zoo in the same year of the establishment of WWF.</p>
</section>
```

**Expected output on the page:**
```
WWF
The World Wide Fund for Nature (WWF) is an international organization working
on issues regarding the conservation, research and restoration of the environment,
formerly named the World Wildlife Fund. WWF was founded in 1961.

WWF's Panda Symbol
The Panda has become the symbol of WWF. The well-known panda logo of WWF
originated from a panda named Chi Chi that was transferred from the Beijing Zoo
to the London Zoo in the same year of the establishment of WWF.
```

> **Thinking Prompt:** What would happen to readability if we put both of these sections in plain `<div>` containers instead? The content would look the same visually — but the meaning would be lost to browsers and screen readers.

---

### 2. `<article>` — Independent, Self-Contained Content

**What is it?**
An `<article>` contains content that could stand alone and still make perfect sense, even if you removed it from the rest of the page. It is independent.

**Real-world analogy:** A newspaper article. You can clip a single article from a newspaper and read it anywhere. It makes sense on its own. You do not need the rest of the paper.

**When to use `<article>`:**
- Blog posts
- News stories
- Forum posts
- Product cards in a shop
- User comments
- Any piece of content that could be shared or syndicated independently

**Simple Example — One blog post:**

```html
<article>
  <h2>How to Grow Tomatoes at Home</h2>
  <p>Growing tomatoes is easier than you think. All you need is a sunny spot,
  good soil, and regular watering. Here are the basic steps...</p>
</article>
```

**Expected output:**
```
How to Grow Tomatoes at Home
Growing tomatoes is easier than you think. All you need is a sunny spot, good
soil, and regular watering. Here are the basic steps...
```

**Multiple articles example — Browser comparison page:**

```html
<article>
  <h2>Google Chrome</h2>
  <p>Google Chrome is a web browser developed by Google, released in 2008.
  Chrome is the world's most popular web browser today!</p>
</article>

<article>
  <h2>Mozilla Firefox</h2>
  <p>Mozilla Firefox is an open-source web browser developed by Mozilla.
  Firefox has been the second most popular web browser since January, 2018.</p>
</article>

<article>
  <h2>Microsoft Edge</h2>
  <p>Microsoft Edge is a web browser developed by Microsoft, released in 2015.
  Microsoft Edge replaced Internet Explorer.</p>
</article>
```

**Expected output:**
```
Google Chrome
Google Chrome is a web browser developed by Google, released in 2008. Chrome is
the world's most popular web browser today!

Mozilla Firefox
Mozilla Firefox is an open-source web browser developed by Mozilla. Firefox has
been the second most popular web browser since January, 2018.

Microsoft Edge
Microsoft Edge is a web browser developed by Microsoft, released in 2015.
Microsoft Edge replaced Internet Explorer.
```

**Styled articles example with CSS:**

You can style `<article>` with CSS to make each one look like a card. Here is the full code:

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .all-browsers {
      margin: 0;
      padding: 5px;
      background-color: lightgray;
    }

    .all-browsers > h1,
    .browser {
      margin: 10px;
      padding: 5px;
    }

    .browser {
      background: white;
    }

    .browser > h2, p {
      margin: 4px;
      font-size: 90%;
    }
  </style>
</head>
<body>

  <article class="all-browsers">
    <h1>Most Popular Browsers</h1>

    <article class="browser">
      <h2>Google Chrome</h2>
      <p>Google Chrome is a web browser developed by Google, released in 2008.
      Chrome is the world's most popular web browser today!</p>
    </article>

    <article class="browser">
      <h2>Mozilla Firefox</h2>
      <p>Mozilla Firefox is an open-source web browser developed by Mozilla.
      Firefox has been the second most popular web browser since January, 2018.</p>
    </article>

    <article class="browser">
      <h2>Microsoft Edge</h2>
      <p>Microsoft Edge is a web browser developed by Microsoft, released in 2015.
      Microsoft Edge replaced Internet Explorer.</p>
    </article>
  </article>

</body>
</html>
```

**What you will see in the browser:**
A light gray card labelled "Most Popular Browsers" containing three white inner cards — one for each browser.

> **Important Note:** Notice that `<article>` elements can be **nested inside each other**. The outer `<article>` represents the whole comparison page. The inner `<article>` elements each represent one independent browser entry. This is perfectly valid.

---

### Can `<article>` and `<section>` Be Nested Inside Each Other?

Yes! And this often confuses beginners. Let us clarify:

- A `<section>` can contain multiple `<article>` elements (e.g., a "News" section with multiple news articles)
- An `<article>` can contain `<section>` elements (e.g., a long blog post divided into sections: Introduction, Body, Conclusion)

There is no strict rule about which one goes "outside." The choice depends on whether the content is independent (use `<article>`) or just thematically grouped (use `<section>`).

---

### 3. `<header>` — Introductory Content

**What is it?**
A `<header>` represents introductory content or a group of navigational links. It typically appears at the top of a page or at the top of a section/article.

**Real-world analogy:** The cover page of a book or the top of a letter. It introduces what follows.

**What goes inside `<header>`:**
- Site logo and brand name
- One or more headings (`<h1>` through `<h6>`)
- Navigation links (`<nav>`)
- Author information
- Publication date

**Key rule:** You can have **multiple `<header>` elements** on one page — one for the overall page, and one inside each `<article>` to introduce that article. However, you **cannot** place a `<header>` inside a `<footer>`, an `<address>`, or another `<header>`.

**Simple page header example:**

```html
<header>
  <h1>My Cooking Blog</h1>
  <p>Recipes, tips, and stories from my kitchen</p>
</header>
```

**Expected output:**
```
My Cooking Blog
Recipes, tips, and stories from my kitchen
```

**Article header example:**

```html
<article>
  <header>
    <h1>What Does WWF Do?</h1>
    <p>WWF's mission:</p>
  </header>
  <p>WWF's mission is to stop the degradation of our planet's natural environment,
  and build a future in which humans live in harmony with nature.</p>
</article>
```

**Expected output:**
```
What Does WWF Do?
WWF's mission:
WWF's mission is to stop the degradation of our planet's natural environment, and
build a future in which humans live in harmony with nature.
```

> **Thinking Prompt:** Notice the `<header>` is inside an `<article>` here. This is the article's own header — introducing just that article. The same element can be used at page level AND inside content blocks.

---

### 4. `<footer>` — Closing Content

**What is it?**
A `<footer>` defines the end section of a document, page, or content block. It typically contains supporting information that comes after the main content.

**Real-world analogy:** The last page of a book — copyright information, "About the Author," references, and index.

**What goes inside `<footer>`:**
- Author name
- Copyright notice
- Contact information
- Links to privacy policy, terms of use
- Back-to-top links
- Related documents
- Sitemap links

**Key rule:** Like `<header>`, you can have **multiple `<footer>` elements** on one page.

**Simple footer example:**

```html
<footer>
  <p>Author: Hege Refsnes</p>
  <p><a href="mailto:hege@example.com">hege@example.com</a></p>
</footer>
```

**Expected output:**
```
Author: Hege Refsnes
hege@example.com   (clickable email link)
```

**Full page footer example:**

```html
<footer>
  <p>&copy; 2025 TechBlog Inc. All rights reserved.</p>
  <p>
    <a href="/privacy">Privacy Policy</a> |
    <a href="/terms">Terms of Use</a> |
    <a href="/contact">Contact Us</a>
  </p>
</footer>
```

**Expected output:**
```
© 2025 TechBlog Inc. All rights reserved.
Privacy Policy | Terms of Use | Contact Us   (all clickable links)
```

---

### 5. `<nav>` — Navigation Links

**What is it?**
A `<nav>` element defines a block of navigation links — links that help users move around your website.

**Real-world analogy:** The index at the front of a textbook or the menu bar at the top of a restaurant menu.

**Important rule:** NOT every group of links on your page belongs inside `<nav>`. The `<nav>` element is intended only for **major blocks of navigation links** — like your main menu, a sidebar navigation, or a table of contents. Links inside `<footer>` (like "Privacy Policy") are usually NOT put in `<nav>`.

Browsers and screen readers use `<nav>` to help users jump directly to the navigation or skip past it. This is a major accessibility benefit.

**Simple navigation example:**

```html
<nav>
  <a href="/html/">HTML</a> |
  <a href="/css/">CSS</a> |
  <a href="/js/">JavaScript</a> |
  <a href="/jquery/">jQuery</a>
</nav>
```

**Expected output (links displayed in a row):**
```
HTML | CSS | JavaScript | jQuery
```
(Each word is a clickable link)

**Navigation list example (common real-world pattern):**

```html
<nav>
  <ul>
    <li><a href="/home">Home</a></li>
    <li><a href="/about">About</a></li>
    <li><a href="/blog">Blog</a></li>
    <li><a href="/contact">Contact</a></li>
  </ul>
</nav>
```

**Expected output:**
```
• Home
• About
• Blog
• Contact
(Each item is a clickable link)
```

---

### 6. `<aside>` — Secondary / Sidebar Content

**What is it?**
An `<aside>` contains content that is related to the surrounding content but not the main point. It is content you could remove without breaking the main story, but it adds extra value.

**Real-world analogy:** The sidebar in a newspaper article — extra facts, a quote, a related photo, or a "Did You Know?" box beside the main story.

**When to use `<aside>`:**
- Biography of the author alongside an article
- Glossary definitions for terms in the main text
- Advertisements that relate to the page topic
- Related links or "You might also like" boxes
- Statistics or quick facts that supplement the main content

**Simple aside example:**

```html
<p>My family and I visited The Epcot center this summer. The weather was
nice, and Epcot was amazing! I had a great summer together with my family!</p>

<aside>
  <h4>Epcot Center</h4>
  <p>Epcot is a theme park at Walt Disney World Resort featuring exciting
  attractions, international pavilions, award-winning fireworks and seasonal
  special events.</p>
</aside>
```

**Expected output:**
```
My family and I visited The Epcot center this summer. The weather was nice, and
Epcot was amazing! I had a great summer together with my family!

Epcot Center
Epcot is a theme park at Walt Disney World Resort featuring exciting attractions,
international pavilions, award-winning fireworks and seasonal special events.
```

**Styled aside example (floated as a sidebar):**

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    aside {
      width: 30%;
      padding-left: 15px;
      margin-left: 15px;
      float: right;
      font-style: italic;
      background-color: lightgray;
    }
  </style>
</head>
<body>

  <p>My family and I visited The Epcot center this summer. The weather was
  nice, and Epcot was amazing! I had a great summer together with my family!</p>

  <aside>
    <p>The Epcot center is a theme park at Walt Disney World Resort featuring
    exciting attractions, international pavilions, award-winning fireworks and
    seasonal special events.</p>
  </aside>

  <p>My family and I visited The Epcot center this summer. The weather was
  nice, and Epcot was amazing! I had a great summer together with my family!</p>
  <p>My family and I visited The Epcot center this summer. The weather was
  nice, and Epcot was amazing! I had a great summer together with my family!</p>

</body>
</html>
```

**What you will see in the browser:**
The `<aside>` appears as a grey box floating on the right side of the page. The main paragraphs wrap around it on the left — exactly like a newspaper sidebar.

> **Thinking Prompt:** What if you put the aside content in a plain `<div>`? Visually it might look the same with the CSS, but a screen reader would not know it is supplemental content — it would read it as if it were part of the main story.

---

### 7. `<figure>` and `<figcaption>` — Illustrated Content

**What is `<figure>`?**
The `<figure>` element wraps self-contained content that is referenced from the main text, such as:
- Photographs
- Diagrams
- Illustrations
- Code listings
- Charts and graphs

**What is `<figcaption>`?**
The `<figcaption>` element goes inside `<figure>` and provides a visible caption or description for the figure. It can be placed at the very start or very end of the `<figure>` element.

**Real-world analogy:** In a science textbook, figures have numbered captions: *"Figure 3: The water cycle showing evaporation, condensation, and precipitation."* The `<figure>` is the image + caption block, and `<figcaption>` is the caption text.

**Simple figure example:**

```html
<figure>
  <img src="pic_trulli.jpg" alt="Trulli">
  <figcaption>Fig1. - Trulli, Puglia, Italy.</figcaption>
</figure>
```

**Expected output:**
```
[An image of Trulli stone houses is displayed]
Fig1. - Trulli, Puglia, Italy.
```
(The caption appears below the image)

**Caption at the top example:**

```html
<figure>
  <figcaption>The Human Heart — anterior view</figcaption>
  <img src="heart.jpg" alt="Human heart diagram">
</figure>
```

**Expected output:**
```
The Human Heart — anterior view
[Heart diagram image displayed below]
```

**Why use `<figure>` instead of just `<img>`?**

- It groups image and caption together as one semantic unit
- Screen readers understand that the caption describes the image
- If the figure is removed or moved (e.g., on mobile), it stays intact as a unit
- It is the proper HTML5 way to display captioned images

---

### 8. `<main>` — The Main Content of the Page

**What is it?**
The `<main>` element contains the dominant, unique content of the page — the content that is specific to this page and not repeated across your website (unlike headers, footers, and navigation which are shared).

**Real-world analogy:** The main body text of a book page — not the page numbers, chapter headings, or margins, just the actual story content.

**Rules:**
- There should be **only ONE `<main>` element** per page
- It should NOT contain `<header>`, `<footer>`, `<nav>`, or `<aside>` elements
- It wraps the core, unique content of the current page

```html
<main>
  <h1>Today's Top Stories</h1>

  <article>
    <h2>New Study Shows Exercise Improves Memory</h2>
    <p>Researchers at Harvard found that 30 minutes of daily exercise...</p>
  </article>

  <article>
    <h2>Tech Giant Launches New Phone</h2>
    <p>The new model includes an improved camera and longer battery life...</p>
  </article>
</main>
```

---

### 9. `<mark>` — Highlighted Text

**What is it?**
The `<mark>` element highlights text — typically shown in yellow by browsers, like a yellow highlighter pen on paper.

**Real-world analogy:** Highlighting a sentence in a textbook to draw attention to it.

**When to use `<mark>`:**
- Showing search results (highlighting the matched search term)
- Drawing attention to important definitions
- Pointing out key passages in a document

**Simple example:**

```html
<p>Do not forget to <mark>buy milk</mark> on the way home.</p>
```

**Expected output:**
```
Do not forget to [buy milk] on the way home.
```
(The words "buy milk" appear with a yellow background highlight)

**Search result example:**

```html
<p>The results for your search for <mark>HTML5</mark> are shown below.</p>
```

**Expected output:**
```
The results for your search for [HTML5] are shown below.
(HTML5 is highlighted in yellow)
```

---

### 10. `<time>` — Date and Time

**What is it?**
The `<time>` element represents a specific time or date in a machine-readable format. This helps search engines, calendar apps, and assistive technologies understand date/time information.

**Real-world analogy:** Writing a date on a letter — both the human-friendly format ("Monday, April 15th") and the machine-readable format ("2025-04-15") communicate the same date.

**The `datetime` attribute:** This attribute holds the machine-readable version of the date/time. Browsers show the text inside the `<time>` tags (human-friendly), while software reads the `datetime` attribute.

**Simple time example:**

```html
<p>The concert is on <time datetime="2025-07-14">July 14th</time>.</p>
```

**Expected output:**
```
The concert is on July 14th.
```
(Visually looks normal, but the machine knows "2025-07-14")

**More examples:**

```html
<!-- Just a date -->
<time datetime="2025-12-25">Christmas Day</time>

<!-- Date and time -->
<time datetime="2025-12-25T09:00">Christmas morning at 9 AM</time>

<!-- Time only -->
<time datetime="19:30">7:30 in the evening</time>
```

---

### 11. `<details>` and `<summary>` — Expandable Content

**What is `<details>`?**
The `<details>` element creates a disclosure widget — content that is hidden by default and can be expanded or collapsed by the user with a click. No JavaScript needed!

**What is `<summary>`?**
The `<summary>` element goes inside `<details>` and provides the visible clickable label that the user sees even when the content is collapsed.

**Real-world analogy:** An FAQ section where you see the question and click to reveal the answer.

**Simple example:**

```html
<details>
  <summary>What is HTML?</summary>
  <p>HTML stands for HyperText Markup Language. It is the standard language
  for creating web pages and web applications.</p>
</details>
```

**Expected output (before clicking):**
```
▶ What is HTML?
```

**Expected output (after clicking the triangle):**
```
▼ What is HTML?
HTML stands for HyperText Markup Language. It is the standard language
for creating web pages and web applications.
```

---

## Complete Semantic Elements Reference Table

Here is a summary of all the semantic elements covered in this lesson and a few additional ones:

| Element | What it means | Real-world equivalent |
|---|---|---|
| `<header>` | Introductory content for a page or section | Book cover page / letter heading |
| `<nav>` | Major navigation links | Restaurant menu / book index |
| `<main>` | The main unique content of the page | Main body text of a book page |
| `<article>` | Independent, self-contained content | A newspaper article |
| `<section>` | Thematic grouping of related content | A chapter in a book |
| `<aside>` | Secondary, related but non-essential content | Newspaper sidebar / footnote |
| `<figure>` | Self-contained illustration, diagram, or photo | Captioned figure in a textbook |
| `<figcaption>` | Caption for a `<figure>` | Figure caption in a textbook |
| `<footer>` | Closing content for a page or section | Back matter of a book |
| `<mark>` | Highlighted text | Yellow highlighter pen on paper |
| `<time>` | A date or time value | Date stamp on a letter |
| `<details>` | Expandable/collapsible content block | FAQ accordion |
| `<summary>` | Visible label for a `<details>` block | FAQ question visible before expanding |

---

## Guided Practice Exercises

### Exercise 1: Identify the Right Element

**Objective:** Choose the correct semantic element for each scenario.

**Scenario A:** You are writing a travel blog. You have a block of text about your trip to Lagos, Nigeria. This block makes complete sense if read anywhere — on social media, in an email, or on your blog. What element wraps it?

> **Answer:** `<article>` — because it is independent and self-contained.

**Scenario B:** Your webpage has a long "Services" page split into three parts: Web Design, Mobile Apps, and SEO. Each part covers a different topic. What element wraps each part?

> **Answer:** `<section>` — because these are thematically distinct groupings of content.

**Scenario C:** You want to add a "Did You Know?" box to the right side of your article about climate change. The box has interesting facts but is not the main point of the article. What element wraps it?

> **Answer:** `<aside>` — supplemental, indirectly related content.

**Scenario D:** Your page has links: "Home", "About", "Portfolio", "Blog", "Contact". These appear at the top of every page. What element wraps them?

> **Answer:** `<nav>` — this is a major navigation block.

---

### Exercise 2: Fix the Non-Semantic Code

**The Problem:**
The HTML below uses only `<div>` tags. Rewrite it using proper semantic elements.

```html
<!-- BEFORE: Non-semantic, hard to read -->
<div id="page-header">
  <div id="site-logo">MyNewsDaily</div>
  <div id="main-nav">
    <a href="/home">Home</a>
    <a href="/world">World</a>
    <a href="/sports">Sports</a>
  </div>
</div>

<div id="main-content">
  <div class="news-story">
    <div class="story-title">Scientists Discover New Planet</div>
    <div class="story-text">A team of astronomers announced the discovery
    of a new planet in the solar system...</div>
  </div>
</div>

<div id="sidebar">
  <div class="sidebar-title">Quick Facts</div>
  <div class="sidebar-text">The planet is estimated to be 3x the size of Earth.</div>
</div>

<div id="page-footer">
  <div>Copyright 2025 MyNewsDaily</div>
</div>
```

**Your Task:** Rewrite this using `<header>`, `<nav>`, `<main>`, `<article>`, `<aside>`, and `<footer>`.

**Solution:**

```html
<!-- AFTER: Semantic and clear -->
<header>
  <h1>MyNewsDaily</h1>
  <nav>
    <a href="/home">Home</a>
    <a href="/world">World</a>
    <a href="/sports">Sports</a>
  </nav>
</header>

<main>
  <article>
    <h2>Scientists Discover New Planet</h2>
    <p>A team of astronomers announced the discovery of a new planet in
    the solar system...</p>
  </article>
</main>

<aside>
  <h4>Quick Facts</h4>
  <p>The planet is estimated to be 3x the size of Earth.</p>
</aside>

<footer>
  <p>Copyright 2025 MyNewsDaily</p>
</footer>
```

**Expected output on the page:**
```
MyNewsDaily
Home  World  Sports

Scientists Discover New Planet
A team of astronomers announced the discovery of a new planet in the solar system...

[Sidebar]
Quick Facts
The planet is estimated to be 3x the size of Earth.

Copyright 2025 MyNewsDaily
```

> **Self-check Questions:**
> - Did you wrap the site name and navigation together in a `<header>`?
> - Is the navigation block specifically inside a `<nav>`?
> - Is the news story inside `<article>` (not `<section>`) because it is independent content?
> - Is the sidebar in `<aside>` because it is supplemental information?
> - Is the copyright in `<footer>`?

---

### Exercise 3: Build a Blog Post Structure

**Objective:** Build a complete semantic HTML structure for a single blog post page.

**Scenario:** You are building the HTML for a single blog post page. The page has:
- A site header with the blog name "TechTalks" and navigation links: Home, Posts, About
- A main content area containing one article about Python programming
  - The article has its own header with a title "Python for Beginners" and publication date "March 10, 2025"
  - The article body has two sections: "Why Python?" and "Your First Python Program"
  - The article has a footer showing "Written by: Ada Johnson"
- A sidebar with "Related Topics" links: JavaScript, Web Design, Databases
- A page footer with copyright

**Steps:**
1. Start with the page structure: `<header>`, `<main>`, `<aside>`, `<footer>`
2. Add the `<nav>` inside the page `<header>`
3. Add the `<article>` inside `<main>`
4. Add `<header>`, `<section>` elements inside the `<article>`
5. Add the article's own `<footer>`

**Solution:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>TechTalks - Python for Beginners</title>
</head>
<body>

  <!-- Page Header -->
  <header>
    <h1>TechTalks</h1>
    <nav>
      <a href="/home">Home</a> |
      <a href="/posts">Posts</a> |
      <a href="/about">About</a>
    </nav>
  </header>

  <!-- Main Content -->
  <main>

    <!-- The Blog Post Article -->
    <article>

      <!-- Article Header -->
      <header>
        <h2>Python for Beginners</h2>
        <p>Published: <time datetime="2025-03-10">March 10, 2025</time></p>
      </header>

      <!-- Section 1 -->
      <section>
        <h3>Why Python?</h3>
        <p>Python is one of the most popular programming languages in the world.
        It is simple to read, easy to learn, and powerful enough for professional
        software development, data science, and artificial intelligence.</p>
      </section>

      <!-- Section 2 -->
      <section>
        <h3>Your First Python Program</h3>
        <p>The simplest Python program you can write prints a message to the screen:</p>
        <figure>
          <pre><code>print("Hello, World!")</code></pre>
          <figcaption>Fig 1. A Python "Hello World" program — the traditional
          starting point for every new programmer.</figcaption>
        </figure>
      </section>

      <!-- Article Footer -->
      <footer>
        <p>Written by: Ada Johnson</p>
      </footer>

    </article>

  </main>

  <!-- Sidebar -->
  <aside>
    <h4>Related Topics</h4>
    <ul>
      <li><a href="/javascript">JavaScript</a></li>
      <li><a href="/web-design">Web Design</a></li>
      <li><a href="/databases">Databases</a></li>
    </ul>
  </aside>

  <!-- Page Footer -->
  <footer>
    <p>&copy; 2025 TechTalks. All rights reserved.</p>
  </footer>

</body>
</html>
```

**Expected output on the page:**
```
TechTalks
Home | Posts | About

Python for Beginners
Published: March 10, 2025

Why Python?
Python is one of the most popular programming languages in the world...

Your First Python Program
The simplest Python program you can write prints a message to the screen:

  print("Hello, World!")

  Fig 1. A Python "Hello World" program — the traditional starting point for
  every new programmer.

Written by: Ada Johnson

[Sidebar]
Related Topics
• JavaScript
• Web Design
• Databases

© 2025 TechTalks. All rights reserved.
```

> **What-if challenges:**
> - What if you wanted to add a "Quick Tip" box inside one of the sections? Which element would you use? (`<aside>`)
> - What if you wanted to add a "Table of Contents" nav inside the article? You could add a `<nav>` inside the `<article>` with links to each section!

---

## Mini Project: Semantic News Website

Now let us put everything together in a realistic project — a news-style website page built entirely with semantic HTML.

### Project Overview

**Goal:** Build a single-page news website for a fictitious site called "DailyUpdate" using only semantic HTML elements.

**The page will contain:**
- A site header with logo and main navigation
- A main content area with two news articles
- A sidebar with today's weather summary
- A figure with a captioned photo inside one article
- An expandable "More Details" section in an article
- Highlighted breaking news text using `<mark>`
- A time stamp on each article
- A full page footer

### Stage 1: The Shell

**Preview:** First, set up the outer structure.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>DailyUpdate - Your News Source</title>
</head>
<body>

  <header>
    <!-- Logo and nav will go here -->
  </header>

  <main>
    <!-- Articles will go here -->
  </main>

  <aside>
    <!-- Sidebar will go here -->
  </aside>

  <footer>
    <!-- Footer will go here -->
  </footer>

</body>
</html>
```

**Milestone output:** The page is blank but the structure is in place. No visual output yet.

---

### Stage 2: Fill the Header and Footer

```html
<header>
  <h1>DailyUpdate</h1>
  <p><em>Bringing you the news that matters</em></p>
  <nav>
    <a href="/home">Home</a> |
    <a href="/world">World</a> |
    <a href="/tech">Technology</a> |
    <a href="/sports">Sports</a> |
    <a href="/opinion">Opinion</a>
  </nav>
</header>
```

```html
<footer>
  <p>&copy; 2025 DailyUpdate Media Group. All rights reserved.</p>
  <p>
    <a href="/privacy">Privacy Policy</a> |
    <a href="/terms">Terms of Use</a> |
    <a href="/contact">Contact</a>
  </p>
</footer>
```

**Milestone output:**
```
DailyUpdate
Bringing you the news that matters
Home | World | Technology | Sports | Opinion

[Main content area still empty]

© 2025 DailyUpdate Media Group. All rights reserved.
Privacy Policy | Terms of Use | Contact
```

---

### Stage 3: Add Two Articles Inside `<main>`

```html
<main>

  <article>
    <header>
      <h2><mark>BREAKING:</mark> Renewable Energy Reaches Record High</h2>
      <p>Published: <time datetime="2025-04-19">April 19, 2025</time> | By Sarah Okonkwo</p>
    </header>

    <figure>
      <img src="solar-panels.jpg" alt="Solar panel farm at sunrise">
      <figcaption>Fig 1. A large solar panel installation in the Sahel region
      of West Africa, contributing to the continent's renewable energy goals.</figcaption>
    </figure>

    <section>
      <h3>The Record</h3>
      <p>Global renewable energy production reached an all-time high this quarter,
      with solar and wind power accounting for 45% of all electricity generated
      worldwide, according to the International Energy Agency.</p>
    </section>

    <section>
      <h3>What This Means</h3>
      <p>Experts say this milestone marks a turning point in the fight against
      climate change. "We are ahead of schedule," said Dr. Amara Diallo, director
      of the Clean Energy Institute.</p>
    </section>

    <details>
      <summary>More Statistics and Data</summary>
      <p>Solar power grew by 28% compared to the same quarter last year.
      Wind energy grew by 19%. Battery storage capacity doubled. Africa
      saw the highest percentage growth of any continent at 62%.</p>
    </details>

    <footer>
      <p>Filed under: <a href="/environment">Environment</a>, <a href="/energy">Energy</a></p>
    </footer>
  </article>


  <article>
    <header>
      <h2>Scientists Decode Ancient Nigerian Script</h2>
      <p>Published: <time datetime="2025-04-18">April 18, 2025</time> | By Dr. Emeka Eze</p>
    </header>

    <section>
      <h3>The Discovery</h3>
      <p>A team of linguists from the University of Lagos have successfully decoded
      a 500-year-old writing system discovered in artifacts from Benin City. The
      script is believed to contain trade records and royal decrees.</p>
    </section>

    <section>
      <h3>Historical Significance</h3>
      <p>The Benin Kingdom was one of the most powerful empires in West Africa.
      Historians say this discovery could rewrite parts of the region's history
      and reveal previously unknown diplomatic relationships.</p>
    </section>

    <footer>
      <p>Filed under: <a href="/history">History</a>, <a href="/science">Science</a></p>
    </footer>
  </article>

</main>
```

---

### Stage 4: Add the Sidebar

```html
<aside>
  <h3>Today's Weather — Lagos</h3>
  <p>🌤 Partly Cloudy</p>
  <p>High: 32°C | Low: 24°C</p>
  <p>Humidity: 78%</p>
  <p><time datetime="2025-04-19">April 19, 2025</time></p>

  <hr>

  <h3>Trending Today</h3>
  <ul>
    <li><a href="#">Lagos State Budget 2025</a></li>
    <li><a href="#">AFCON Qualifier Results</a></li>
    <li><a href="#">New Naira Exchange Rate</a></li>
    <li><a href="#">University Admissions Open</a></li>
  </ul>
</aside>
```

---

### Stage 5: The Complete Final Page

Putting it all together:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>DailyUpdate - Your News Source</title>
</head>
<body>

  <header>
    <h1>DailyUpdate</h1>
    <p><em>Bringing you the news that matters</em></p>
    <nav>
      <a href="/home">Home</a> |
      <a href="/world">World</a> |
      <a href="/tech">Technology</a> |
      <a href="/sports">Sports</a> |
      <a href="/opinion">Opinion</a>
    </nav>
  </header>

  <main>

    <article>
      <header>
        <h2><mark>BREAKING:</mark> Renewable Energy Reaches Record High</h2>
        <p>Published: <time datetime="2025-04-19">April 19, 2025</time> | By Sarah Okonkwo</p>
      </header>

      <figure>
        <img src="solar-panels.jpg" alt="Solar panel farm at sunrise">
        <figcaption>Fig 1. A large solar panel installation in the Sahel region
        of West Africa.</figcaption>
      </figure>

      <section>
        <h3>The Record</h3>
        <p>Global renewable energy production reached an all-time high this quarter,
        with solar and wind power accounting for 45% of all electricity generated
        worldwide.</p>
      </section>

      <section>
        <h3>What This Means</h3>
        <p>Experts say this milestone marks a turning point in the fight against
        climate change. "We are ahead of schedule," said Dr. Amara Diallo.</p>
      </section>

      <details>
        <summary>More Statistics and Data</summary>
        <p>Solar power grew by 28% compared to last year. Wind grew by 19%.
        Africa saw the highest growth at 62%.</p>
      </details>

      <footer>
        <p>Filed under: <a href="/environment">Environment</a>, <a href="/energy">Energy</a></p>
      </footer>
    </article>


    <article>
      <header>
        <h2>Scientists Decode Ancient Nigerian Script</h2>
        <p>Published: <time datetime="2025-04-18">April 18, 2025</time> | By Dr. Emeka Eze</p>
      </header>

      <section>
        <h3>The Discovery</h3>
        <p>A team of linguists from the University of Lagos have successfully decoded
        a 500-year-old writing system discovered in artifacts from Benin City.</p>
      </section>

      <section>
        <h3>Historical Significance</h3>
        <p>The Benin Kingdom was one of the most powerful empires in West Africa.
        This discovery could rewrite parts of the region's history.</p>
      </section>

      <footer>
        <p>Filed under: <a href="/history">History</a>, <a href="/science">Science</a></p>
      </footer>
    </article>

  </main>

  <aside>
    <h3>Today's Weather — Lagos</h3>
    <p>🌤 Partly Cloudy</p>
    <p>High: 32°C | Low: 24°C</p>

    <h3>Trending Today</h3>
    <ul>
      <li><a href="#">Lagos State Budget 2025</a></li>
      <li><a href="#">AFCON Qualifier Results</a></li>
      <li><a href="#">New Naira Exchange Rate</a></li>
    </ul>
  </aside>

  <footer>
    <p>&copy; 2025 DailyUpdate Media Group. All rights reserved.</p>
    <p>
      <a href="/privacy">Privacy Policy</a> |
      <a href="/terms">Terms of Use</a> |
      <a href="/contact">Contact</a>
    </p>
  </footer>

</body>
</html>
```

**Final Milestone Output — what a browser renders:**
```
DailyUpdate
Bringing you the news that matters
Home | World | Technology | Sports | Opinion

[BREAKING:] Renewable Energy Reaches Record High
Published: April 19, 2025 | By Sarah Okonkwo

[Solar panel image displayed]
Fig 1. A large solar panel installation in the Sahel region of West Africa.

The Record
Global renewable energy production reached an all-time high this quarter...

What This Means
Experts say this milestone marks a turning point in the fight against climate change...

▶ More Statistics and Data

Filed under: Environment, Energy


Scientists Decode Ancient Nigerian Script
Published: April 18, 2025 | By Dr. Emeka Eze

The Discovery
A team of linguists from the University of Lagos have successfully decoded...

Historical Significance
The Benin Kingdom was one of the most powerful empires in West Africa...

Filed under: History, Science


[SIDEBAR]
Today's Weather — Lagos
🌤 Partly Cloudy
High: 32°C | Low: 24°C

Trending Today
• Lagos State Budget 2025
• AFCON Qualifier Results
• New Naira Exchange Rate


© 2025 DailyUpdate Media Group. All rights reserved.
Privacy Policy | Terms of Use | Contact
```

> **Reflection Questions:**
> - Count the semantic elements used. Did you spot at least 8 different semantic tags?
> - If a blind user uses a screen reader, how would they benefit from this structure compared to a page made entirely of `<div>` tags?
> - Which article would be better for an RSS feed reader to pick up? Why?

---

## The Semantic Layout Challenge

Based on the W3Schools code challenge for semantic layouts, here is the core practical challenge for you to solve:

**Challenge: Semantic Layout**

**Task:** You are given the following non-semantic HTML. Add the correct semantic HTML5 element names to replace the `?????` placeholders.

```html
<!DOCTYPE html>
<html>
<body>

<?????> 
  <h1>My Website</h1>
  <p>A great place to learn</p>
  <nav>
    <a href="/home">Home</a>
    <a href="/about">About</a>
  </nav>
</?????>

<?????> 
  <h2>Welcome!</h2>
  <p>This is the main content of my website.</p>
</?????>

<?????> 
  <h4>Follow Us</h4>
  <p>Connect with us on social media!</p>
</?????>

<?????>
  <p>&copy; 2025 My Website</p>
</?????>

</body>
</html>
```

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>

<header>
  <h1>My Website</h1>
  <p>A great place to learn</p>
  <nav>
    <a href="/home">Home</a>
    <a href="/about">About</a>
  </nav>
</header>

<main>
  <h2>Welcome!</h2>
  <p>This is the main content of my website.</p>
</main>

<aside>
  <h4>Follow Us</h4>
  <p>Connect with us on social media!</p>
</aside>

<footer>
  <p>&copy; 2025 My Website</p>
</footer>

</body>
</html>
```

**Expected output:**
```
My Website
A great place to learn
Home  About

Welcome!
This is the main content of my website.

[Sidebar]
Follow Us
Connect with us on social media!

© 2025 My Website
```

---

## Common Beginner Mistakes

### Mistake 1: Using `<section>` for Everything

**Wrong:**
```html
<section>
  <p>Copyright 2025</p>
</section>
```

**Right:**
```html
<footer>
  <p>Copyright 2025</p>
</footer>
```

**Why it's wrong:** A `<section>` is for a thematic grouping of content with a heading. The copyright information at the bottom belongs in a `<footer>`.

---

### Mistake 2: Using `<article>` for Everything

**Wrong:**
```html
<article>
  <h2>Our Services</h2>
  <article>Web Design</article>
  <article>SEO</article>
  <article>Hosting</article>
</article>
```

**Right:**
```html
<section>
  <h2>Our Services</h2>
  <article>
    <h3>Web Design</h3>
    <p>We build beautiful, responsive websites.</p>
  </article>
  <article>
    <h3>SEO</h3>
    <p>We help your site rank higher in search results.</p>
  </article>
  <article>
    <h3>Hosting</h3>
    <p>Reliable, fast hosting for your projects.</p>
  </article>
</section>
```

**Why it's wrong:** "Our Services" is a section (a themed page area). Each individual service description is an article if it is self-contained, but plain labels like just "Web Design" as one-word articles are too minimal.

---

### Mistake 3: Putting Multiple `<main>` Elements on One Page

**Wrong:**
```html
<main>
  <h1>Homepage Content</h1>
</main>

<main>
  <h2>Secondary Content</h2>
</main>
```

**Right:**
```html
<main>
  <h1>Homepage Content</h1>
  <section>
    <h2>Secondary Content</h2>
  </section>
</main>
```

**Why it's wrong:** There should only be **one** `<main>` element per page. Use `<section>` to divide content within `<main>`.

---

### Mistake 4: Forgetting `<figcaption>` or Using It Outside `<figure>`

**Wrong:**
```html
<img src="chart.png" alt="Sales chart">
<p>Fig 1. Quarterly sales data.</p>
```

**Right:**
```html
<figure>
  <img src="chart.png" alt="Sales chart">
  <figcaption>Fig 1. Quarterly sales data.</figcaption>
</figure>
```

**Why it's wrong:** A plain `<p>` tag after an `<img>` has no semantic connection to the image. `<figcaption>` inside `<figure>` creates a meaningful, structured link between the image and its description.

---

### Mistake 5: Using `<nav>` for Every Group of Links

**Wrong:**
```html
<footer>
  <nav>
    <a href="/privacy">Privacy Policy</a>
    <a href="/terms">Terms</a>
  </nav>
</footer>
```

**Right:**
```html
<footer>
  <p>
    <a href="/privacy">Privacy Policy</a> |
    <a href="/terms">Terms</a>
  </p>
</footer>
```

**Why it's wrong:** `<nav>` is reserved for **major** navigation blocks. Small groups of links in a footer do not usually need `<nav>`. Overusing `<nav>` reduces its semantic value for screen readers.

---

### Mistake 6: Nesting `<header>` Inside `<footer>` (Forbidden)

**Wrong:**
```html
<footer>
  <header>
    <h3>Footer Title</h3>
  </header>
  <p>Copyright info here</p>
</footer>
```

**Right:**
```html
<footer>
  <h3>Footer Title</h3>
  <p>Copyright info here</p>
</footer>
```

**Why it's wrong:** The HTML specification explicitly states that `<header>` cannot be placed inside a `<footer>` element. Use a plain heading element like `<h3>` instead.

---

## Reflection Questions

Test your understanding by thinking through these questions:

1. **Why is `<div>` considered "non-semantic"?** What information does it fail to convey that `<article>` or `<section>` would provide?

2. **Can a page have two `<footer>` elements?** If yes, what would be a valid reason?

3. **What is the difference between `<article>` and `<section>`?** Give a real-world example where you would choose one over the other.

4. **Why do screen readers care about `<nav>` elements?** What can they do with that information that they cannot do with a `<div>`?

5. **You are building an e-commerce product page.** It has: a site header, product name, description, customer reviews (5 separate reviews), a "You may also like" panel, and a footer. Which semantic elements would you use for each part? Write out your plan.

6. **What does the `datetime` attribute in `<time>` allow that the visible text does not?** Give an example where the visible text and `datetime` value would be different.

7. **Why does the W3C say semantic HTML allows data to be "shared and reused across applications"?** Think about how a recipe sharing website or a news aggregator might use semantic HTML to extract content automatically.

---

## Completion Checklist

Go through this checklist to confirm you have mastered this lesson:

- [ ] I can explain what "semantic" means in plain language
- [ ] I know why semantic HTML matters (accessibility, SEO, readability)
- [ ] I can explain the difference between `<article>` and `<section>` with examples
- [ ] I know when to use `<header>` and when to use `<footer>`
- [ ] I know that `<nav>` is only for major navigation blocks
- [ ] I understand that `<aside>` is for supplemental, not essential content
- [ ] I can correctly use `<figure>` and `<figcaption>` together
- [ ] I know when to use `<mark>` and `<time>`
- [ ] I know how `<details>` and `<summary>` create expandable content
- [ ] I can identify non-semantic HTML and rewrite it using semantic elements
- [ ] I have completed Exercise 2 (rewriting the non-semantic HTML)
- [ ] I have completed Exercise 3 (building the blog post structure)
- [ ] I have completed the mini project (DailyUpdate news page)
- [ ] I can name at least 5 common beginner mistakes with semantic HTML

---

## Lesson Summary

HTML5 introduced **semantic elements** — tags whose names describe the role and meaning of their content. This was a major step forward from the older pattern of using generic `<div>` containers for everything.

The key semantic elements you learned in this lesson are:

**Structural elements** that define the major zones of a webpage:
`<header>`, `<nav>`, `<main>`, `<aside>`, and `<footer>`

**Content elements** that describe the nature of the content:
`<article>` (independent, self-contained content) and `<section>` (thematically grouped content)

**Media elements** for captioned illustrations:
`<figure>` and `<figcaption>`

**Inline and interactive elements**:
`<mark>` (highlighted text), `<time>` (dates and times), `<details>` and `<summary>` (expandable content blocks)

The benefits of using semantic HTML are:
- **Accessibility** — screen readers use semantic elements to help users navigate and understand content
- **SEO** — search engines rank well-structured semantic pages more effectively
- **Maintainability** — code is easier to read, understand, and modify
- **Interoperability** — content can be shared and reused across applications, as the W3C intended

The golden rule: ask yourself **"What IS this content?"** — not just "How should this look?" The element name should answer that question. If it is a navigation block, use `<nav>`. If it is a standalone article, use `<article>`. If it is a page footer, use `<footer>`. Reserve `<div>` for when no semantic element fits.

In the next lesson, you will explore the HTML Style Guide — best practices and conventions for writing clean, consistent HTML code.

---

*Sources: W3Schools HTML Semantic Elements (https://www.w3schools.com/html/html5_semantic_elements.asp) and HTML Semantics Code Challenge (https://www.w3schools.com/html/html_challenges_semantics.asp)*
