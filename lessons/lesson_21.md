---
render_with_liquid: false
title: "HTML Iframes — Embedding Web Pages Inside Web Pages"
nav_order: 21
---

# Lesson 21 — HTML Iframes: Embedding Web Pages Inside Web Pages

---

## Lesson Introduction

Have you ever visited a website and noticed a **map embedded right on the page**, or a **YouTube video playing without leaving the site**, or a **live weather widget** tucked into a corner? These are all powered by something called an **iframe**.

In this lesson, you will learn exactly what an iframe is, how to create one, how to control its size and appearance, and how to use it as a target for links. By the end, you will be able to embed another web page — or even a live website — directly inside your own HTML page.

Think of it this way: imagine you are reading a textbook, and one of the pages has a clear plastic window that shows another book underneath. You can read both at the same time, without leaving your textbook. That plastic window is your iframe.

---

## What You Will Learn

- What an iframe is and why it exists
- The basic `<iframe>` syntax and required attributes
- How to set the height and width of an iframe
- How to remove or customise the iframe border using CSS
- How to use an iframe as a **link target** — so clicking a link loads a page inside the iframe
- Common beginner mistakes and how to avoid them
- Hands-on practice exercises
- A realistic mini-project: a simple "Resource Hub" page

---

## Prerequisite Concepts

> Before we begin, let us quickly review two concepts you already know from earlier lessons that will make iframes easier to understand.

### What is an HTML attribute?

An **attribute** gives extra information to an HTML tag. It is written **inside the opening tag**, like this:

```html
<img src="photo.jpg" alt="A cat">
```

Here, `src` and `alt` are attributes. They tell the `<img>` tag where the image file is and what it describes.

Iframes also use attributes — most importantly `src`, `title`, `height`, `width`, and `name`.

### What is CSS `style`?

CSS (Cascading Style Sheets) controls the **visual appearance** of HTML elements — their size, colour, border, spacing, and more. You can apply CSS directly to an HTML element using the `style` attribute:

```html
<p style="color: red;">This text is red.</p>
```

You will use the `style` attribute throughout this lesson to control how your iframe looks.

---

## Section 1 — What Is an iframe?

### What does "iframe" mean?

The word **iframe** stands for **inline frame**.

Let's break that down:

- **Inline** means "placed inside the normal flow of the page content," right alongside other text, images, and elements.
- **Frame** refers to a bordered container — like a picture frame — that holds something inside it.

So an **inline frame is a bordered container embedded directly inside your web page that can display another web page (or document) inside it.**

### Why does the iframe exist?

Before iframes, if you wanted to show content from another website on your page, you had to copy and paste it manually — and keep updating it. That was tedious and broke easily.

The iframe solves this problem. It creates a live window into another URL. The browser fetches and renders that other page **inside your page**, automatically and in real time.

### Real-world uses of iframes

Iframes are everywhere in modern web development. Here are common places you will see them:

- **Google Maps** embedded on a business website
- **YouTube videos** playing on a blog or news article
- **Social media posts** (tweets, Instagram posts) shown inside another site
- **Payment forms** from Stripe or PayPal embedded on an e-commerce page
- **Live weather widgets** on travel websites
- **PDF document viewers** embedded in educational platforms

---

## Section 2 — The Basic `<iframe>` Tag

### Syntax

The most basic iframe looks like this:

```html
<iframe src="URL" title="description"></iframe>
```

Let's understand every single part of this:

| Part | What it is | What it does |
|---|---|---|
| `<iframe` | Opening of the iframe tag | Tells the browser "start an inline frame here" |
| `src="URL"` | The `src` attribute | Stands for **source** — the web address of the page you want to show inside the frame |
| `title="description"` | The `title` attribute | A short text description of what the iframe contains |
| `></iframe>` | Closing of the tag | Ends the iframe element |

> 💡 **Why is `title` important?**
> Screen readers (tools used by visually impaired people) read the `title` attribute aloud so the user knows what the iframe contains. Always include it — it is a best practice for **accessibility**.

### Your First iframe Example

```html
<!DOCTYPE html>
<html>
  <body>

    <h1>My First Iframe</h1>

    <iframe src="https://www.example.com" title="Example Website"></iframe>

  </body>
</html>
```

**What happens when a browser runs this code:**

The browser loads your HTML page normally, displays the heading "My First Iframe", and then inside a small rectangular box — the iframe — it loads and displays the website at `https://www.example.com`.

**Expected visual output:**
```
[ My First Iframe ]

+------------------------------------+
|  Example Domain                    |
|  This domain is for use in...      |
|  ...                               |
+------------------------------------+
```

> 🤔 **Thinking prompt:** What do you think would happen if you changed the `src` value to a different website? Try imagining the result before you test it!

---

## Section 3 — Setting Height and Width

By default, a browser assigns a small default size to an iframe. In practice, you almost always want to control the exact size yourself.

### Method 1 — Using `height` and `width` attributes (in pixels)

```html
<iframe 
  src="https://www.example.com" 
  height="200" 
  width="300" 
  title="Example Website">
</iframe>
```

**Line-by-line explanation:**

- `src="https://www.example.com"` — loads this URL inside the frame
- `height="200"` — makes the iframe **200 pixels tall**
- `width="300"` — makes the iframe **300 pixels wide**
- `title="Example Website"` — describes the content for screen readers

> 📏 **What is a pixel?** A pixel (px) is one tiny dot on your screen. Your screen is made up of millions of these tiny dots. 200px tall and 300px wide creates a medium-sized box.

**Expected visual output:**
```
+----------------------------------+  ← 300px wide
|                                  |  ↑
|   [Content of example.com]       |  | 200px tall
|                                  |  ↓
+----------------------------------+
```

### Method 2 — Using the `style` attribute with CSS

You can also use CSS inside the `style` attribute to set size. This approach is more flexible and consistent with how professional developers write code today.

```html
<iframe 
  src="https://www.example.com" 
  style="height:200px; width:300px;" 
  title="Example Website">
</iframe>
```

**Line-by-line explanation:**

- `style="..."` — opens an inline CSS style block
- `height:200px;` — CSS property setting the height to 200 pixels (note the colon `:` and semicolon `;`)
- `width:300px;` — CSS property setting the width to 300 pixels

**Expected visual output:** Identical to Method 1 — a 300×200px frame.

> 💡 **Which method is better?** Both work. Professional developers generally prefer the `style` attribute (or a separate CSS file) because it keeps all styling in one consistent place. For learning, either is fine.

### Comparison of Both Methods

```html
<!-- Method 1: HTML attributes -->
<iframe src="page.html" height="200" width="300" title="My Frame"></iframe>

<!-- Method 2: CSS via style attribute -->
<iframe src="page.html" style="height:200px; width:300px;" title="My Frame"></iframe>
```

Both produce the exact same-sized iframe. The difference is **where you define the size** — as HTML attributes or as CSS properties.

> 🤔 **Thinking prompt:** What would happen if you changed `width:300px` to `width:600px`? The iframe would become twice as wide!

---

## Section 4 — Removing the Iframe Border

### Why does a border appear?

By default, every browser draws a **visible rectangular border** around an iframe. This border is a visual indicator showing the boundaries of the embedded frame.

However, in many real projects, the border looks unprofessional or does not match the website's design. You will often want to remove it.

### How to remove the border using CSS

Use the CSS `border` property with the value `none`:

```html
<iframe 
  src="https://www.example.com" 
  style="border:none;" 
  title="Example Website">
</iframe>
```

**Line-by-line explanation:**

- `style="border:none;"` — CSS instruction that says "draw no border around this iframe"
- `border` — the CSS property that controls the border appearance
- `none` — the value meaning "no border at all"

**Expected visual output:**

Without this style:
```
+----------------------------------+   ← visible border line
|   [Content of example.com]       |
+----------------------------------+   ← visible border line
```

With `border:none;`:
```
   [Content of example.com]           ← no border visible
```

### How to add a custom border

You can also give the iframe a custom border instead of removing it entirely. CSS borders follow this pattern:

```
border: [thickness] [style] [color];
```

Example — a 2-pixel-thick solid red border:

```html
<iframe 
  src="https://www.example.com" 
  style="border:2px solid red;" 
  title="Example Website">
</iframe>
```

**Line-by-line explanation:**

- `border:2px solid red;` — draw a border that is...
  - `2px` — 2 pixels thick
  - `solid` — a continuous solid line (other options: `dashed`, `dotted`, `double`)
  - `red` — the colour of the border line

**Expected visual output:**
```
🟥🟥🟥🟥🟥🟥🟥🟥🟥🟥🟥🟥   ← 2px red border
🟥 [Content of example.com] 🟥
🟥🟥🟥🟥🟥🟥🟥🟥🟥🟥🟥🟥   ← 2px red border
```

### More Custom Border Examples

```html
<!-- Blue dotted border, 3px thick -->
<iframe src="page.html" style="border:3px dotted blue;" title="My Frame"></iframe>

<!-- Green dashed border, 1px thick -->
<iframe src="page.html" style="border:1px dashed green;" title="My Frame"></iframe>

<!-- No border (clean look) -->
<iframe src="page.html" style="border:none;" title="My Frame"></iframe>
```

---

## Section 5 — Using an iframe as a Link Target

This is one of the most powerful and interesting things you can do with an iframe. You can make a link **load its destination inside the iframe** instead of navigating away from the page.

### What does "link target" mean?

Normally, when you click a link (`<a href="...">`) it opens the new page in the **same tab**, replacing your current page.

But you can tell the link **where** to open — and one option is: inside a specific named iframe on the same page.

Think of it like having a TV screen (the iframe) and a set of channel buttons (the links). When you click a button, the TV screen changes — but you never leave the room (the current page).

### How it works — step by step

**Step 1:** Give the iframe a `name` attribute.
**Step 2:** On each link, set `target` equal to that name.
**Step 3:** When the user clicks the link, the linked page loads inside the iframe.

### Full Example — iframe as Link Target

```html
<!DOCTYPE html>
<html>
  <body>

    <h2>My Resource Viewer</h2>

    <!-- The iframe that will display linked pages -->
    <iframe 
      src="https://www.example.com" 
      name="iframe_a" 
      title="Resource Viewer"
      style="height:400px; width:600px; border:2px solid grey;">
    </iframe>

    <!-- Links that load inside the iframe above -->
    <p>
      <a href="https://www.w3schools.com" target="iframe_a">
        Open W3Schools
      </a>
    </p>

    <p>
      <a href="https://www.wikipedia.org" target="iframe_a">
        Open Wikipedia
      </a>
    </p>

  </body>
</html>
```

**Line-by-line explanation:**

**The iframe:**
- `src="https://www.example.com"` — shows this page initially when the page first loads
- `name="iframe_a"` — gives this iframe the identifier "iframe\_a" (this is like giving it a name tag)
- `title="Resource Viewer"` — describes the frame for screen readers
- `style="height:400px; width:600px; border:2px solid grey;"` — makes it 400×600px with a grey border

**The links:**
- `href="https://www.w3schools.com"` — the URL to open when clicked
- `target="iframe_a"` — instead of opening in a new tab, load this URL inside the iframe named "iframe\_a"

**How it behaves:**

When the page first loads → `example.com` appears in the iframe.
User clicks "Open W3Schools" → `w3schools.com` loads inside the **same iframe**.
User clicks "Open Wikipedia" → `wikipedia.org` loads inside the **same iframe**.
The rest of the page (heading, links) never changes!

**Expected visual output flow:**

```
[ My Resource Viewer ]

+------------------------------------+
|  [Initially shows example.com]     |  ← iframe starts here
+------------------------------------+

Open W3Schools   ← click this
Open Wikipedia   ← click this

--- After clicking "Open W3Schools": ---

+------------------------------------+
|  [Now shows w3schools.com]         |  ← same iframe, new content!
+------------------------------------+

Open W3Schools
Open Wikipedia
```

> 🤔 **Thinking prompt:** Can you imagine how this could be used on a real website? For example, a sidebar with links that load different sections into a main reading area — all without leaving the page.

---

## Section 6 — Combining Everything Together

Now let us see all the iframe features combined in one real example:

```html
<!DOCTYPE html>
<html>
  <body>

    <h1>Web Resource Centre</h1>
    <p>Click a link below to view the resource in the frame.</p>

    <!-- Navigation links -->
    <p>
      <a href="https://www.w3schools.com" target="viewer">W3Schools</a> |
      <a href="https://www.wikipedia.org" target="viewer">Wikipedia</a> |
      <a href="https://www.bbc.com" target="viewer">BBC News</a>
    </p>

    <!-- The viewing iframe -->
    <iframe 
      src="https://www.w3schools.com" 
      name="viewer"
      title="Resource Viewer"
      style="height:500px; width:100%; border:3px solid #333;">
    </iframe>

  </body>
</html>
```

**What is new here?**

- `width:100%` — instead of a fixed number of pixels, `100%` means the iframe stretches to fill the **full width of its container** (the browser window). This is great for responsive layouts.
- `border:3px solid #333;` — `#333` is a dark grey colour written in **hex code** (a 6-character colour code used in CSS)
- Multiple links all using the **same** `target="viewer"` — they all load into the same iframe

**Expected output:**

```
[ Web Resource Centre ]
Click a link below to view the resource in the frame.

W3Schools | Wikipedia | BBC News

+--------------------------------------------------+
|                                                  |
|          [W3Schools website loads here]          |
|                                                  |
|  (Clicking Wikipedia will replace this content)  |
|                                                  |
+--------------------------------------------------+
```

---

## Section 7 — Guided Practice Exercises

### Exercise 1 — Basic Iframe

**Objective:** Create your first iframe that embeds a web page.

**Scenario:** You are building a simple personal webpage and want to include a Wikipedia article about your favourite city.

**Steps:**

1. Create a new HTML file called `exercise1.html`
2. Add the standard HTML structure (`<!DOCTYPE html>`, `<html>`, `<body>`)
3. Add a heading: "My Favourite City"
4. Add an iframe that loads `https://www.wikipedia.org`
5. Give the iframe a `title` of "Wikipedia"
6. Set the height to 300 and width to 500

**Your code should look like this:**

```html
<!DOCTYPE html>
<html>
  <body>

    <h1>My Favourite City</h1>

    <iframe 
      src="https://www.wikipedia.org" 
      height="300" 
      width="500" 
      title="Wikipedia">
    </iframe>

  </body>
</html>
```

**Expected output:**
```
[ My Favourite City ]

+----------------------------------------+
|  [Wikipedia homepage loads here]       |
|  500px wide, 300px tall                |
+----------------------------------------+
```

**Self-check questions:**
- Did the Wikipedia page load inside the small box?
- Can you see the border around the iframe?
- Is the rest of your heading still visible outside the iframe?

---

### Exercise 2 — Customise the Border

**Objective:** Practice removing and customising the border.

**Scenario:** Your manager asks you to show a company web page inside a page, but without the default ugly browser border.

**Steps:**

1. Take your code from Exercise 1
2. Remove the `height` and `width` attributes
3. Add a `style` attribute instead, setting height to 350px and width to 600px
4. Add `border:none;` to remove the border
5. Save and open in your browser

```html
<!DOCTYPE html>
<html>
  <body>

    <h1>My Favourite City</h1>

    <iframe 
      src="https://www.wikipedia.org" 
      style="height:350px; width:600px; border:none;" 
      title="Wikipedia">
    </iframe>

  </body>
</html>
```

**Expected output:** Wikipedia appears in a clean borderless box.

**What-if challenge:** Try changing `border:none;` to `border:4px dashed blue;`. What do you see?

---

### Exercise 3 — iframe as Link Target

**Objective:** Create a set of navigation links that load pages inside an iframe.

**Scenario:** You are building a mini "learning portal" with three resource links. Clicking each link should load the page inside a frame below — without the user leaving your portal page.

**Steps:**

1. Create a new file `portal.html`
2. Add a heading "Learning Portal"
3. Add three links (to any three websites you like)
4. Give all three links `target="content_frame"`
5. Add an iframe below the links with `name="content_frame"`
6. Set the iframe to 450px tall, 100% wide, with a 2px solid dark border

```html
<!DOCTYPE html>
<html>
  <body>

    <h1>Learning Portal</h1>

    <p>
      <a href="https://www.w3schools.com" target="content_frame">HTML Tutorials</a> | 
      <a href="https://www.wikipedia.org" target="content_frame">Wikipedia</a> | 
      <a href="https://www.bbc.com" target="content_frame">BBC News</a>
    </p>

    <iframe 
      src="https://www.w3schools.com" 
      name="content_frame" 
      title="Content Viewer"
      style="height:450px; width:100%; border:2px solid #444;">
    </iframe>

  </body>
</html>
```

**Expected output:**
```
[ Learning Portal ]
HTML Tutorials | Wikipedia | BBC News

+----------------------------------------------------------+
|  [W3Schools loads first by default]                       |
|  Clicking any link above replaces this content            |
|  without changing the rest of the page                    |
+----------------------------------------------------------+
```

**Self-check questions:**
- When you click "Wikipedia", does it load inside the frame — not in a new tab?
- Does the heading and the set of links stay visible after clicking?
- What happens if you click "BBC News" after Wikipedia is already loaded?

---

## Section 8 — Mini Project: "My Study Hub" Page

Now let us combine everything from this lesson into a complete, realistic mini-project.

### Project Overview

You will build a **"My Study Hub"** page — a simple one-page study tool that:
- Has a title and a short description
- Has a navigation bar of 4 study resource links
- Has an iframe that shows each resource when clicked
- Has a styled, borderless (or minimal border) iframe that fills most of the screen

---

### Stage 1 — Setup the HTML Structure

Start with the basic page skeleton:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>My Study Hub</title>
  </head>
  <body>

    <h1>📚 My Study Hub</h1>
    <p>Click any resource below to study it in the viewer.</p>

  </body>
</html>
```

**Milestone output:**
```
📚 My Study Hub
Click any resource below to study it in the viewer.
```

---

### Stage 2 — Add the Navigation Links

Add four resource links, all targeting the same iframe:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>My Study Hub</title>
  </head>
  <body>

    <h1>📚 My Study Hub</h1>
    <p>Click any resource below to study it in the viewer.</p>

    <nav>
      <a href="https://www.w3schools.com/html/" target="study_frame">HTML</a> |
      <a href="https://www.w3schools.com/css/" target="study_frame">CSS</a> |
      <a href="https://www.wikipedia.org" target="study_frame">Wikipedia</a> |
      <a href="https://www.bbc.com" target="study_frame">BBC News</a>
    </nav>

  </body>
</html>
```

**Milestone output:**
```
📚 My Study Hub
Click any resource below to study it in the viewer.

HTML | CSS | Wikipedia | BBC News
```

---

### Stage 3 — Add the iframe Viewer

Now add the iframe below the navigation:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>My Study Hub</title>
  </head>
  <body>

    <h1>📚 My Study Hub</h1>
    <p>Click any resource below to load it in the viewer below.</p>

    <nav>
      <a href="https://www.w3schools.com/html/" target="study_frame">HTML</a> |
      <a href="https://www.w3schools.com/css/" target="study_frame">CSS</a> |
      <a href="https://www.wikipedia.org" target="study_frame">Wikipedia</a> |
      <a href="https://www.bbc.com" target="study_frame">BBC News</a>
    </nav>

    <br>

    <iframe
      src="https://www.w3schools.com/html/"
      name="study_frame"
      title="Study Viewer"
      style="height:550px; width:100%; border:2px solid #2c3e50;">
    </iframe>

  </body>
</html>
```

**Milestone output:**
```
📚 My Study Hub
Click any resource below to load it in the viewer below.

HTML | CSS | Wikipedia | BBC News

+--------------------------------------------------------------+
|                                                              |
|         [W3Schools HTML Tutorial loads here by default]      |
|                                                              |
|  Clicking any nav link replaces this content instantly       |
|                                                              |
+--------------------------------------------------------------+
```

---

### Stage 4 — Final Output Review

Open your file in a browser. You should see:

1. A heading at the top
2. Four clickable links in a row
3. A large iframe below, initially showing the W3Schools HTML tutorial
4. When you click "CSS", the CSS tutorial appears in the iframe
5. When you click "Wikipedia", Wikipedia appears — all without leaving your page!

**Reflection questions:**
- What happens to the heading and the navigation when you click a link?
- Why is it useful to load resources inside an iframe instead of opening a new tab?
- What kind of website could benefit most from this kind of layout?

**Optional advanced extensions:**
- Add a 5th link to a Google Maps location
- Add a `<footer>` below the iframe with your name
- Try changing the border colour to match your favourite colour using a hex code

---

## Section 9 — Common Beginner Mistakes

### Mistake 1 — Forgetting the `title` attribute

**Wrong:**
```html
<iframe src="https://www.example.com"></iframe>
```

**Problem:** Screen readers cannot describe the iframe's content to visually impaired users. This is a basic accessibility error.

**Correct:**
```html
<iframe src="https://www.example.com" title="Example website"></iframe>
```

---

### Mistake 2 — Using `name` instead of `target` on the link (or vice versa)

**Wrong:**
```html
<iframe src="page.html" target="frame1" title="My Frame"></iframe>
<a href="other.html" name="frame1">Click me</a>
```

**Problem:** `name` goes on the **iframe**, not the link. `target` goes on the **link**, not the iframe.

**Correct:**
```html
<iframe src="page.html" name="frame1" title="My Frame"></iframe>
<a href="other.html" target="frame1">Click me</a>
```

---

### Mistake 3 — Mixing px syntax with and without the "px" unit

**Wrong (HTML attribute style):**
```html
<iframe src="page.html" style="height:200; width:300;" title="Frame"></iframe>
```

**Problem:** In CSS, you must include the unit. `200` alone means nothing in CSS — it needs to be `200px`.

**Correct:**
```html
<iframe src="page.html" style="height:200px; width:300px;" title="Frame"></iframe>
```

> **Note:** When using the HTML `height` and `width` attributes (not CSS), you write just the number: `height="200"`. The unit (pixels) is assumed. But in CSS (inside `style=""`), you must always write `200px`.

---

### Mistake 4 — Embedding a site that blocks iframes

**Example:**
```html
<iframe src="https://www.google.com" title="Google"></iframe>
```

**Problem:** Many websites — including Google, Facebook, and most major platforms — use security settings (`X-Frame-Options` header) that **prevent** their pages from being embedded in iframes. When you try, the iframe will appear blank or show an error message.

**Solution:** Only embed pages that allow iframe embedding. Many websites provide official embed codes (like YouTube, Google Maps) that are specifically designed to work in iframes.

---

### Mistake 5 — Writing the border shorthand in the wrong order

**Wrong:**
```html
<iframe style="border: red solid 2px;" ...></iframe>
```

**Problem:** While browsers may sometimes accept different orders, the **correct and reliable order** for the CSS border shorthand is: `thickness style color`.

**Correct:**
```html
<iframe style="border: 2px solid red;" ...></iframe>
```

---

## Section 10 — Chapter Summary

Here is everything you learned in this lesson, summarised clearly:

The **HTML `<iframe>` tag** creates an **inline frame** — a container that displays another web page inside your current page.

The **`src` attribute** specifies the URL of the page to embed inside the iframe.

The **`title` attribute** is always recommended for accessibility (screen readers).

The **`height` and `width` attributes** control the size of the iframe in pixels. You can also use the CSS `style` attribute with `height:Xpx;` and `width:Xpx;` for the same result.

To **remove the default border**, use `style="border:none;"`. To add a **custom border**, use `style="border: 2px solid red;"` (or any thickness, style, and colour you choose).

To use an **iframe as a link target**:
- Give the iframe a `name` attribute (e.g., `name="viewer"`)
- Give your links a `target` attribute that matches (e.g., `target="viewer"`)
- Clicking the link loads the destination page inside the iframe instead of navigating away

---

## Completion Checklist

Before moving on, make sure you can answer "yes" to every item:

- [ ] I understand what an iframe is and why it is useful
- [ ] I can write a basic `<iframe>` tag with `src` and `title`
- [ ] I can set the size using HTML attributes (`height`, `width`)
- [ ] I can set the size using CSS (`style="height:Xpx; width:Xpx;"`)
- [ ] I can remove the iframe border using `style="border:none;"`
- [ ] I can add a custom coloured border using `style="border: 2px solid red;"`
- [ ] I understand the difference between `name` (on the iframe) and `target` (on the link)
- [ ] I can set up a link-to-iframe target relationship
- [ ] I know that some websites block being embedded in iframes
- [ ] I completed at least one of the practice exercises
- [ ] I built or understood the mini-project Study Hub

---

## Reflection Questions

Think about these before you move to the next lesson:

1. What is the difference between opening a link in a new tab and opening it in a named iframe?
2. Can you think of a website you use regularly that likely uses iframes somewhere?
3. Why is it important to include the `title` attribute on an iframe?
4. If you wanted the iframe to fill the full width of the screen regardless of screen size, what CSS value would you use for `width`?
5. What do you think would happen if two different iframes had the same `name` attribute?

---

## HTML iframe Quick Reference

| Attribute / Style | What it does | Example |
|---|---|---|
| `src="URL"` | Sets the page to embed | `src="https://www.example.com"` |
| `title="text"` | Describes the iframe for accessibility | `title="My Viewer"` |
| `height="200"` | Height in pixels (HTML attribute) | `height="400"` |
| `width="300"` | Width in pixels (HTML attribute) | `width="600"` |
| `style="height:200px;"` | Height using CSS | `style="height:400px;"` |
| `style="width:300px;"` | Width using CSS | `style="width:100%;"` |
| `style="border:none;"` | Removes the border | `style="border:none;"` |
| `style="border:2px solid red;"` | Adds a custom border | `style="border:3px dashed blue;"` |
| `name="framename"` | Names the iframe for link targeting | `name="viewer"` |
| `target="framename"` | (on `<a>` tag) Opens link inside named iframe | `target="viewer"` |

---

*End of Lesson 21 — HTML Iframes*
