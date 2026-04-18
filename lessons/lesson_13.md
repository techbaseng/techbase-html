---
render_with_liquid: false
title: "Lesson 13: HTML Links – Hyperlinks, Colors, Bookmarks & Challenges"
nav_order: 13
---

# Lesson 13: HTML Links – Hyperlinks, Colors, Bookmarks & Challenges

---

## Lesson Introduction

Have you ever clicked on a piece of underlined text on a website and been taken to a completely different page? That clickable text is called a **hyperlink** — and it is one of the most important things in all of web development.

Links are what make the web a *web*. Without links, every page would be an island — completely cut off from everywhere else. With links, billions of pages connect to each other, creating the huge network we call the internet.

In this lesson, you will learn:
- What HTML links are and how to create them
- How to control where a link opens
- The difference between absolute and relative URLs
- How to use images, buttons, and emails as links
- How to style links with different colours using CSS
- How to create bookmarks so users can jump to sections on the same page
- Common beginner mistakes and how to avoid them

By the end of this lesson, you will be able to add professional, well-styled navigation links to any webpage.

---

## Prerequisite Concepts

Before we dive in, let us make sure you understand two ideas that this lesson builds on.

### What is an HTML Tag?

An HTML tag is a special instruction wrapped in angle brackets (`<` and `>`). It tells the browser how to display content. Most tags come in pairs: an **opening tag** and a **closing tag**.

```html
<p>This is a paragraph.</p>
```

- `<p>` is the opening tag (it starts the paragraph)
- `</p>` is the closing tag (it ends the paragraph)
- The `/` in the closing tag tells the browser the element is finished

### What is an HTML Attribute?

An attribute gives extra information to an HTML tag. It is always written **inside** the opening tag and follows the pattern `name="value"`.

```html
<p style="color: blue;">This paragraph is blue.</p>
```

Here, `style` is the **attribute name** and `"color: blue;"` is the **attribute value**.

You will use attributes a lot in this lesson — especially `href`, `target`, `title`, and `id`.

---

## Part 1: Understanding HTML Links (Hyperlinks)

### What Is a Hyperlink?

A **hyperlink** (or just "link") is clickable content on a webpage that takes you somewhere else when clicked. That "somewhere else" could be:

- Another webpage on the internet
- Another page on the same website
- A specific section lower down on the same page
- An email address
- A downloadable file

Think of a hyperlink like a door in a building. You open the door and step into a different room — or a completely different building. Links are the "doors" of the web.

When you move your mouse cursor over a link on most websites, the cursor changes from an arrow into a pointing hand. That is the browser telling you: "Click me, I go somewhere!"

### The `<a>` Tag — The Anchor Element

In HTML, links are created using the `<a>` tag. The letter "a" stands for **anchor**. The most important part of any link is the `href` attribute, which stands for **Hypertext REFerence**. This is where you put the address of the destination.

**Basic syntax:**

```html
<a href="URL">Link Text</a>
```

Let us break this down piece by piece:

| Part | What It Is | Example |
|---|---|---|
| `<a` | Opens the anchor tag | `<a` |
| `href="URL"` | The destination address | `href="https://www.google.com"` |
| `>` | Closes the opening tag | `>` |
| `Link Text` | What the user sees and clicks | `Visit Google` |
| `</a>` | Closes the anchor tag | `</a>` |

### Your First Link — A Simple Example

```html
<a href="https://www.w3schools.com/">Visit W3Schools.com!</a>
```

**What the browser displays:**
> [Visit W3Schools.com!](#) ← (This would appear as a clickable blue underlined link)

**What happens when clicked:** The browser navigates to `https://www.w3schools.com/`

> 💡 **Tip:** The text between `<a>` and `</a>` is what the user reads and clicks. Make it descriptive! Instead of "Click here", use "Read our HTML Tutorial" so users know exactly where they are going.

### Default Link Appearance in Browsers

By default, every browser displays links with the same colour system:

| Link State | Colour | Style |
|---|---|---|
| **Unvisited** (never clicked before) | Blue | Underlined |
| **Visited** (already clicked before) | Purple | Underlined |
| **Active** (being clicked right now) | Red | Underlined |

These are the browser defaults. You can change all of these with CSS — and you will learn exactly how to do that in Part 3 of this lesson.

---

## Part 2: The `target` Attribute — Controlling Where the Link Opens

### The Problem

By default, when a user clicks a link, the new page opens in the **same browser tab**, replacing the page they were on. Sometimes that is fine. But sometimes you want the link to open in a **new tab** — for example, if you are linking to an external website and you want users to stay on your website too.

### The Solution: `target`

The `target` attribute tells the browser **where** to open the linked document.

**Syntax:**

```html
<a href="URL" target="value">Link Text</a>
```

### The Four Target Values

| Value | What It Does |
|---|---|
| `_self` | Opens in the **same** tab (this is the default — you do not need to write it) |
| `_blank` | Opens in a **new** tab or window |
| `_parent` | Opens in the parent frame (used with frames, which are rarely used today) |
| `_top` | Opens in the full body of the window, breaking out of any frames |

### The Most Useful One: `_blank`

The `_blank` value is the one you will use most often.

```html
<a href="https://www.w3schools.com/" target="_blank">Visit W3Schools in a new tab!</a>
```

**What happens:** Clicking this link opens W3Schools in a brand new browser tab, while your original page stays open in the old tab.

**Real-world use:** Travel booking sites, news websites, and online stores often use `target="_blank"` when linking to external partners so that users never fully leave their site.

> ⚠️ **Beginner Mistake:** Forgetting the underscore! It is `_blank` (with an underscore), NOT `blank`. Without the underscore, the browser treats it as a named window, not a special instruction.

---

## Part 3: Absolute URLs vs Relative URLs

### What Is a URL?

A **URL** (Uniform Resource Locator) is simply an address on the internet — like a postal address, but for webpages. For example: `https://www.w3schools.com/html/default.asp`

### Absolute URLs

An **absolute URL** is the full, complete web address — including the protocol (`https://`), the domain name (`www.w3schools.com`), and the path to the specific page (`/html/default.asp`).

Think of it like writing a full home address: "123 Main Street, Lagos, Nigeria."

```html
<a href="https://www.w3.org/">W3C</a>
<a href="https://www.google.com/">Google</a>
```

Use absolute URLs when linking to **external websites** — websites different from your own.

### Relative URLs

A **relative URL** is a short address that does NOT include the full domain. It is a path *relative to* the current page — like saying "go to the room next door" instead of giving the full building address.

```html
<!-- Link to a page in the html folder of the same website -->
<a href="/html/default.asp">HTML Tutorial</a>

<!-- Link to a page in the same folder as the current page -->
<a href="default.asp">HTML Tutorial</a>
```

Use relative URLs when linking to **pages within your own website**.

### Side-by-Side Comparison Example

```html
<h2>Absolute URLs</h2>
<p><a href="https://www.w3.org/">W3C</a></p>
<p><a href="https://www.google.com/">Google</a></p>

<h2>Relative URLs</h2>
<p><a href="html_images.asp">HTML Images</a></p>
<p><a href="/css/default.asp">CSS Tutorial</a></p>
```

**Expected output:**
> **Absolute URLs**
> [W3C](#) — links to an external website
> [Google](#) — links to an external website
>
> **Relative URLs**
> [HTML Images](#) — links to a page in the same website
> [CSS Tutorial](#) — links to a CSS page in the same website

> 🤔 **Thinking Prompt:** What would happen if you used a relative URL to link to Google? Try writing `<a href="google.com">Google</a>` and imagine where it would go. It would try to find a folder called "google.com" on your *own* website — and fail! This is why external links always need the full `https://` prefix.

---

## Part 4: Special Types of Links

### 4.1 Using an Image as a Link

A link does not have to be text! You can wrap any HTML element — including images — inside an `<a>` tag to make it clickable.

The trick is simple: put the `<img>` tag *inside* the `<a>` tag.

**Syntax:**

```html
<a href="destination-page.html">
  <img src="image-file.gif" alt="Description of image" style="width:42px;height:42px;">
</a>
```

**Example:**

```html
<a href="default.asp">
  <img src="smiley.gif" alt="HTML tutorial" style="width:42px;height:42px;">
</a>
```

**What happens:** The smiley face image becomes clickable. When clicked, the browser goes to `default.asp`.

> 💡 **Real-world use:** Logos at the top-left of most websites are image links that take you back to the homepage when you click them. That is one of the most common uses of image links in the real world.

### 4.2 Linking to an Email Address

You can create a link that opens the user's email application automatically, with a new email ready to be written. Use the special `mailto:` scheme inside the `href` attribute.

```html
<a href="mailto:someone@example.com">Send email</a>
```

**What happens:** When clicked, the browser opens the default email app (like Outlook, Gmail, or Apple Mail) with `someone@example.com` already filled in as the recipient.

**Real-world use:** Contact pages on business websites often use this so customers can email the company with one click.

### 4.3 Using a Button as a Link

HTML buttons look more professional than plain text links in some situations. However, buttons need a small amount of JavaScript to behave as links. Here is how it works:

```html
<button onclick="document.location='default.asp'">HTML Tutorial</button>
```

**What happens:** When the button is clicked, the `onclick` event triggers. The JavaScript inside `onclick` sets the browser's location to `default.asp`, navigating to that page.

> 💡 **Note:** `onclick` is a JavaScript event. You do not need to understand JavaScript deeply right now — just know that `document.location='URL'` is what makes the button navigate to a page.

### 4.4 The `title` Attribute — Tooltip Text

The `title` attribute adds a small pop-up tooltip that appears when the user hovers their mouse over the link for a moment.

```html
<a href="https://www.w3schools.com/html/" title="Go to W3Schools HTML section">
  Visit our HTML Tutorial
</a>
```

**What happens:** When you hover over the link text "Visit our HTML Tutorial", a small tooltip box appears showing: "Go to W3Schools HTML section".

**Real-world use:** Titles help with accessibility and give users extra context about where a link leads, especially useful for screen reader software.

---

## Part 5: HTML Link Colors — Styling Links with CSS

### Why Change Link Colors?

The default browser colours for links (blue for unvisited, purple for visited, red for active) are well-known but often clash with a website's design. Professional websites style their links to match their branding.

In CSS, you target links using special selectors called **pseudo-classes**. A pseudo-class describes a *state* of an element — in this case, the different states a link can be in.

### The Four Link Pseudo-Classes

| CSS Selector | When It Applies |
|---|---|
| `a:link` | A link that has **NOT** been visited yet |
| `a:visited` | A link the user has **already visited** |
| `a:hover` | A link the user is **currently hovering over** with the mouse |
| `a:active` | A link that is **being clicked** right now |

> ⚠️ **Important Rule:** CSS link pseudo-classes must be declared in this exact order: `link`, `visited`, `hover`, `active`. Remember it with the phrase **"L V H A"** or the silly sentence **"Lord Vader Hates Apples."** If you put them in the wrong order, some states may not work correctly!

### Simple Example — Changing Link Colors

```html
<style>
  a:link {
    color: green;
    background-color: transparent;
    text-decoration: none;
  }

  a:visited {
    color: pink;
    background-color: transparent;
    text-decoration: none;
  }

  a:hover {
    color: red;
    background-color: transparent;
    text-decoration: underline;
  }

  a:active {
    color: yellow;
    background-color: transparent;
    text-decoration: underline;
  }
</style>

<p><a href="https://www.w3schools.com/">Visit W3Schools</a></p>
```

**What the browser does:**
- The link appears **green** with no underline when you first see it
- When you hover over it, it turns **red** and gets an underline
- When you actively click it, it turns **yellow**
- After you visit it and come back, it appears **pink**

Let us break down each CSS property used:

| Property | What It Does |
|---|---|
| `color: green;` | Sets the text colour to green |
| `background-color: transparent;` | Makes the background see-through (no coloured box behind the text) |
| `text-decoration: none;` | Removes the underline from the link |
| `text-decoration: underline;` | Adds an underline to the link |

> 🤔 **Thinking Prompt:** What would happen if you set `a:link { color: red; }` and `a:visited { color: red; }` to the same colour? The user would not be able to tell which links they have already visited! This is bad for user experience. Always make `a:link` and `a:visited` different colours.

### Styling Links as Buttons

You can go much further and style a link to look exactly like a button. This is very common on websites for call-to-action links like "Sign Up" or "Learn More".

```html
<style>
  a:link, a:visited {
    background-color: #f44336;
    color: white;
    padding: 15px 25px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
  }

  a:hover, a:active {
    background-color: red;
  }
</style>

<a href="https://www.w3schools.com/">This is a link styled as a button</a>
```

**What the browser displays:**
A red rectangular button with white text that reads "This is a link styled as a button". When you hover over it, the red gets slightly darker.

Let us understand each property:

- `background-color: #f44336;` — Sets the button background to a red colour (`#f44336` is a red HEX colour code)
- `color: white;` — Makes the text white so it is readable against red
- `padding: 15px 25px;` — Adds 15px of space above/below the text and 25px left/right, making the button bigger
- `text-align: center;` — Centres the text inside the button
- `text-decoration: none;` — Removes the underline
- `display: inline-block;` — Makes the link behave like a block element (so padding works properly) while still sitting inline with other content

> 💡 **Real-world use:** The "Buy Now", "Get Started", and "Learn More" buttons you see on websites are almost always styled `<a>` tags like this one, not actual `<button>` elements.

---

## Part 6: HTML Bookmarks — Jumping to a Section on the Same Page

### What Is a Bookmark?

A **bookmark** (also called an **anchor link** or **jump link**) is a special type of link that does NOT take you to a different page. Instead, it scrolls the current page up or down to a specific section.

Imagine reading a very long article. At the top there is a "Table of Contents" with items like "Chapter 1", "Chapter 2", "Chapter 3". Clicking "Chapter 3" instantly jumps you down the page to where Chapter 3 starts. That is a bookmark in action.

**Real-world uses:**
- Wikipedia uses bookmarks in its "Contents" sections at the top of every article
- Long FAQ pages use bookmarks so users can jump to the question they need
- Legal documents and privacy policies use bookmarks to navigate between sections

### How Bookmarks Work — Two Steps

Creating a bookmark requires two things:

**Step 1: Mark the target location** using the `id` attribute on any HTML element. This is like planting a flag at the destination.

**Step 2: Create a link that points to that `id`**, using `#` followed by the id value.

### Step 1 — Creating the Bookmark Target (Planting the Flag)

Add an `id` attribute to the heading or element where you want people to land when they click the link.

```html
<h2 id="C4">Chapter 4</h2>
```

**What this does:** It labels this `<h2>` element with the unique name "C4". The `id` must be **unique** — no other element on the same page should have the same `id`.

> 💡 **Analogy:** Think of the `id` like a house number. Just as every house on a street has a unique number, every element on a page should have a unique `id`.

### Step 2 — Linking to the Bookmark (Following the Flag)

Create a link using `href="#id-name"`. The `#` symbol tells the browser: "I am not going to a different page — I am jumping to an element with this id on the **current** page."

```html
<a href="#C4">Jump to Chapter 4</a>
```

**What happens when clicked:** The page scrolls smoothly down to the `<h2 id="C4">Chapter 4</h2>` element.

### Complete Bookmark Example

```html
<!DOCTYPE html>
<html>
<body>

  <!-- Navigation at the top -->
  <p><a href="#section1">Jump to Section 1</a></p>
  <p><a href="#section2">Jump to Section 2</a></p>
  <p><a href="#section3">Jump to Section 3</a></p>

  <!-- Lots of content in between... -->
  <br><br><br><br><br><br><br><br><br><br>
  <br><br><br><br><br><br><br><br><br><br>

  <!-- Target sections with id attributes -->
  <h2 id="section1">Section 1: Introduction</h2>
  <p>This is Section 1 content.</p>
  <br><br><br><br><br><br><br><br><br><br>

  <h2 id="section2">Section 2: Main Content</h2>
  <p>This is Section 2 content.</p>
  <br><br><br><br><br><br><br><br><br><br>

  <h2 id="section3">Section 3: Conclusion</h2>
  <p>This is Section 3 content.</p>

</body>
</html>
```

**Expected output:** Three clickable links at the top of the page. Clicking each one jumps the page to the corresponding section heading.

### Linking to a Bookmark on a DIFFERENT Page

You can also link to a bookmark on a completely different page. Just combine the page URL with the `#id`:

```html
<a href="html_demo.html#C4">Jump to Chapter 4 on the demo page</a>
```

**What this does:**
1. Navigates to `html_demo.html`
2. Once the page loads, automatically scrolls to the element with `id="C4"`

---

## Guided Practice Exercises

### Exercise 1 — Your First Link

**Objective:** Create a simple link to an external website that opens in a new tab.

**Scenario:** You are building a personal webpage and want to add a link to your favourite news site.

**Steps:**

1. Open your text editor and create a new file called `exercise1.html`
2. Type the basic HTML structure:

```html
<!DOCTYPE html>
<html>
<head>
  <title>My First Link</title>
</head>
<body>
  <h1>My Favourite Website</h1>
  <!-- Add your link here -->
</body>
</html>
```

3. Add this link inside the `<body>`:

```html
<a href="https://www.bbc.com/news" target="_blank" title="Visit BBC News">
  Read today's news on BBC
</a>
```

**Expected output in browser:**
> A clickable link that reads: "Read today's news on BBC"
> Hovering shows a tooltip: "Visit BBC News"
> Clicking opens BBC News in a new tab

**Self-check questions:**
- What would happen if you removed `target="_blank"`?
- What does the `title` attribute add to the user experience?
- Try changing the link text to something more descriptive. Does it still work?

---

### Exercise 2 — Relative and Absolute Links Together

**Objective:** Build a simple two-page mini website and link the pages together using relative URLs.

**Steps:**

**Page 1 — Create `index.html`:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Website - Home</title>
</head>
<body>
  <h1>Welcome to My Website</h1>
  <p>This is the home page.</p>

  <!-- Relative link to another page in the same folder -->
  <a href="about.html">Go to the About page</a>

  <!-- Absolute link to an external website -->
  <p><a href="https://www.google.com" target="_blank">Search on Google</a></p>
</body>
</html>
```

**Page 2 — Create `about.html` in the same folder:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Website - About</title>
</head>
<body>
  <h1>About Me</h1>
  <p>This is the about page.</p>

  <!-- Relative link back to home -->
  <a href="index.html">Back to Home</a>
</body>
</html>
```

**Expected output:**
- Opening `index.html` shows the home page with two links
- Clicking "Go to the About page" loads `about.html`
- On `about.html`, clicking "Back to Home" returns to `index.html`
- Clicking "Search on Google" opens Google in a new tab

**What-if challenge:** What happens if you rename `about.html` to `about-me.html` but forget to update the link in `index.html`? Try it and see the broken link!

---

### Exercise 3 — Styling Links with CSS

**Objective:** Apply custom CSS colours and styles to links in all four states.

**Scenario:** You are designing a navigation menu for a tech company. The company colour is dark blue (`#003366`) with an orange highlight (`#ff6600`).

```html
<!DOCTYPE html>
<html>
<head>
  <title>Styled Links</title>
  <style>
    /* Unvisited links */
    a:link {
      color: #003366;
      text-decoration: none;
      font-weight: bold;
    }

    /* Visited links */
    a:visited {
      color: #666666;
      text-decoration: none;
    }

    /* Hovered links */
    a:hover {
      color: #ff6600;
      text-decoration: underline;
    }

    /* Active (clicking) links */
    a:active {
      color: #ff0000;
    }
  </style>
</head>
<body>
  <h2>Company Navigation</h2>
  <p><a href="https://www.w3schools.com">HTML Tutorials</a></p>
  <p><a href="https://www.w3schools.com/css/">CSS Tutorials</a></p>
  <p><a href="https://www.w3schools.com/js/">JavaScript Tutorials</a></p>
</body>
</html>
```

**Expected output:**
- Links appear in dark blue with no underline
- Hovering turns them orange with an underline
- After visiting them, they appear grey
- Clicking turns them red for a split second

**Self-check questions:**
- Why did we put `a:hover` AFTER `a:visited` in the CSS?
- What happens if you swap the order of `a:hover` and `a:visited`?
- Try changing `text-decoration: none;` to `text-decoration: underline;` on `a:link`. What changes?

---

### Exercise 4 — Building a Page with Bookmarks

**Objective:** Create a long page with a table of contents using bookmark links.

**Scenario:** You are creating an HTML reference guide page with multiple sections.

```html
<!DOCTYPE html>
<html>
<head>
  <title>HTML Quick Reference Guide</title>
  <style>
    body { font-family: Arial, sans-serif; max-width: 700px; margin: 0 auto; padding: 20px; }
    .toc { background-color: #f0f0f0; padding: 20px; border-radius: 8px; margin-bottom: 30px; }
    .toc h2 { margin-top: 0; }
    .section { margin-top: 60px; border-top: 2px solid #cccccc; padding-top: 20px; }
    a { color: #0066cc; }
  </style>
</head>
<body>

  <!-- TABLE OF CONTENTS -->
  <div class="toc">
    <h2>Table of Contents</h2>
    <p><a href="#headings">1. HTML Headings</a></p>
    <p><a href="#paragraphs">2. HTML Paragraphs</a></p>
    <p><a href="#links">3. HTML Links</a></p>
    <p><a href="#images">4. HTML Images</a></p>
  </div>

  <!-- SECTION 1 -->
  <div class="section">
    <h2 id="headings">1. HTML Headings</h2>
    <p>HTML headings use tags from &lt;h1&gt; to &lt;h6&gt;. The h1 tag is the biggest and most important. The h6 tag is the smallest.</p>
    <p><a href="#top">↑ Back to top</a></p>
  </div>

  <!-- SECTION 2 -->
  <div class="section">
    <h2 id="paragraphs">2. HTML Paragraphs</h2>
    <p>Paragraphs are created with the &lt;p&gt; tag. Each paragraph starts on a new line and has space above and below it.</p>
    <p><a href="#top">↑ Back to top</a></p>
  </div>

  <!-- SECTION 3 -->
  <div class="section">
    <h2 id="links">3. HTML Links</h2>
    <p>Links are created with the &lt;a&gt; tag and the href attribute. Use target="_blank" to open in a new tab.</p>
    <p><a href="#top">↑ Back to top</a></p>
  </div>

  <!-- SECTION 4 -->
  <div class="section">
    <h2 id="images">4. HTML Images</h2>
    <p>Images use the &lt;img&gt; tag with src and alt attributes. Always include an alt attribute for accessibility.</p>
    <p><a href="#top">↑ Back to top</a></p>
  </div>

</body>
</html>
```

**Expected output:**
- A table of contents box at the top with four clickable items
- Clicking each item jumps to its section
- "↑ Back to top" links at the end of each section (Note: for "Back to top" to work, add `id="top"` to the `<body>` tag or the very first element on the page)

**What-if challenge:** Add a fifth section about "HTML Lists" with its own bookmark. Make sure the table of contents links to it!

---

## Mini Project: Personal Link Hub Page

Let us combine everything from this lesson into one real mini project — a **Personal Link Hub** page. This is similar to websites like Linktree that hold all your important links in one place.

### Project Overview

You will build a single page with:
- A profile header section
- A styled navigation with bookmark links
- Multiple sections (one per category of links)
- Styled link buttons

### Stage 1 — HTML Structure Setup

Create a file called `linkhub.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My Link Hub</title>
</head>
<body>

  <!-- PROFILE HEADER -->
  <div id="top">
    <h1>My Personal Link Hub</h1>
    <p>Welcome! Find all my important links below.</p>
  </div>

  <!-- NAVIGATION BOOKMARKS -->
  <nav>
    <a href="#learning">Learning</a> |
    <a href="#social">Social</a> |
    <a href="#tools">Tools</a>
  </nav>

  <!-- SECTION: LEARNING -->
  <section id="learning">
    <h2>Learning Resources</h2>
    <p><a href="https://www.w3schools.com" target="_blank" title="Learn web development">W3Schools</a></p>
    <p><a href="https://developer.mozilla.org" target="_blank" title="Mozilla web docs">MDN Web Docs</a></p>
  </section>

  <!-- SECTION: SOCIAL -->
  <section id="social">
    <h2>Social Media</h2>
    <p><a href="https://www.linkedin.com" target="_blank">LinkedIn</a></p>
    <p><a href="https://github.com" target="_blank">GitHub</a></p>
  </section>

  <!-- SECTION: TOOLS -->
  <section id="tools">
    <h2>Useful Tools</h2>
    <p><a href="https://www.google.com" target="_blank">Google Search</a></p>
    <p><a href="mailto:youremail@example.com" title="Send me an email">Contact Me by Email</a></p>
  </section>

  <!-- BACK TO TOP -->
  <p><a href="#top">↑ Back to the top</a></p>

</body>
</html>
```

**Milestone output:** A working page with three sections you can jump between using the navigation links.

### Stage 2 — Add CSS Styling

Add this `<style>` block inside the `<head>` tag, just before `</head>`:

```html
<style>
  body {
    font-family: Arial, sans-serif;
    max-width: 600px;
    margin: 0 auto;
    padding: 30px;
    background-color: #f5f5f5;
  }

  #top {
    text-align: center;
    background-color: #1a1a2e;
    color: white;
    padding: 30px;
    border-radius: 12px;
    margin-bottom: 20px;
  }

  nav {
    text-align: center;
    margin: 15px 0;
    font-size: 1.1em;
  }

  section {
    background-color: white;
    padding: 20px;
    border-radius: 10px;
    margin: 20px 0;
    box-shadow: 0 2px 6px rgba(0,0,0,0.1);
  }

  section h2 {
    color: #1a1a2e;
    border-bottom: 2px solid #e0e0e0;
    padding-bottom: 8px;
  }

  /* Unvisited */
  a:link {
    color: #0066cc;
    text-decoration: none;
    font-size: 1.05em;
  }

  /* Visited */
  a:visited {
    color: #6633cc;
    text-decoration: none;
  }

  /* Hover */
  a:hover {
    color: #cc3300;
    text-decoration: underline;
  }

  /* Active */
  a:active {
    color: #ff6600;
  }
</style>
```

**Milestone output:** The page now looks polished and professional with a dark header, white sections, and styled links.

### Stage 3 — Style Some Links as Buttons

Replace the plain text links in the Learning section with button-styled links:

```html
<!-- SECTION: LEARNING -->
<section id="learning">
  <h2>Learning Resources</h2>

  <a href="https://www.w3schools.com" target="_blank"
     style="display:inline-block; background-color:#0066cc; color:white;
            padding:10px 20px; border-radius:6px; text-decoration:none;
            margin: 5px;">
    W3Schools
  </a>

  <a href="https://developer.mozilla.org" target="_blank"
     style="display:inline-block; background-color:#ff6600; color:white;
            padding:10px 20px; border-radius:6px; text-decoration:none;
            margin: 5px;">
    MDN Web Docs
  </a>
</section>
```

**Milestone output:** Two button-styled links that look like professional action buttons.

### Stage 4 — Final Output and Reflection

Your finished Link Hub page should have:
- A dark-coloured header with your name
- A navigation bar with bookmark links
- Three sections: Learning, Social, and Tools
- Mixed link styles (regular links and button-styled links)
- A "Back to top" bookmark link at the bottom
- Custom CSS colours for all four link states

**Reflection questions:**
- Which link type (text link vs button link) looks more clickable to you? Why?
- How would you add a fourth section called "Entertainment"?
- If a friend asked "how does clicking 'Back to top' jump me to the top of the page?", how would you explain it using the concept of `id` and `href`?

**Optional extension:** Add a `title` attribute to every link on the page with a descriptive tooltip.

---

## Common Beginner Mistakes

### Mistake 1 — Forgetting the `https://` in Absolute URLs

**Wrong:**
```html
<a href="www.google.com">Google</a>
```

**Why it fails:** The browser does not recognise this as a web address. It will try to find a file called `www.google.com` in your own website's folders.

**Correct:**
```html
<a href="https://www.google.com">Google</a>
```

---

### Mistake 2 — Forgetting the Closing `</a>` Tag

**Wrong:**
```html
<a href="https://www.google.com">Google
<p>This paragraph will also become part of the link!</p>
```

**Why it fails:** Everything after the unclosed `<a>` tag becomes part of the clickable link area, including other elements.

**Correct:**
```html
<a href="https://www.google.com">Google</a>
<p>This paragraph is separate and not a link.</p>
```

---

### Mistake 3 — Using `_blank` Without the Underscore

**Wrong:**
```html
<a href="https://www.google.com" target="blank">Google</a>
```

**Why it fails:** `blank` (without underscore) is treated as a *window name*, not a special instruction. The browser may open a new window named "blank" once, then reuse that same window for all future `target="blank"` clicks on your page.

**Correct:**
```html
<a href="https://www.google.com" target="_blank">Google</a>
```

---

### Mistake 4 — Writing Bookmark Links Without the `#` Symbol

**Wrong:**
```html
<a href="C4">Jump to Chapter 4</a>
```

**Why it fails:** The browser looks for a *file* called `C4`, not an element with `id="C4"` on the current page.

**Correct:**
```html
<a href="#C4">Jump to Chapter 4</a>
```

---

### Mistake 5 — Using the Wrong Order for CSS Link Pseudo-Classes

**Wrong order:**
```css
a:hover { color: orange; }
a:link { color: blue; }
a:active { color: red; }
a:visited { color: purple; }
```

**Why it fails:** CSS applies styles in the order they appear. If `a:link` comes *after* `a:hover`, the hover style may be overridden by the link style.

**Correct order (always use LVHA):**
```css
a:link    { color: blue; }
a:visited { color: purple; }
a:hover   { color: orange; }
a:active  { color: red; }
```

---

### Mistake 6 — Duplicate `id` Values on the Same Page

**Wrong:**
```html
<h2 id="section">Introduction</h2>
<h2 id="section">Conclusion</h2>
```

**Why it fails:** The browser will only jump to the *first* element it finds with that `id`. The second `id="section"` bookmark will never work correctly.

**Correct:**
```html
<h2 id="introduction">Introduction</h2>
<h2 id="conclusion">Conclusion</h2>
```

---

## Reflection Questions

Take a moment to think through these questions to check your understanding:

1. What is the purpose of the `href` attribute in an `<a>` tag? What happens if you leave it out?
2. If you were building a company website and linking to a partner's site, would you use `target="_blank"` or `target="_self"`? Why?
3. What is the difference between `href="https://www.example.com"` and `href="about.html"`?
4. A colleague says: "I want to make a link that opens the user's email app." What HTML would you write for them?
5. Why is the order `a:link`, `a:visited`, `a:hover`, `a:active` important in CSS?
6. You have a very long Terms and Conditions page. How would you use bookmarks to improve the user experience?
7. Can a link contain an image? If yes, how would you write the code?
8. What is the `title` attribute on a link used for? Who benefits most from it?

---

## Completion Checklist

Review this checklist before moving to the next lesson. You should be able to tick every item:

- [ ] I understand what a hyperlink is and why it is important
- [ ] I can create a basic link using `<a href="URL">text</a>`
- [ ] I know the difference between `target="_self"` and `target="_blank"`
- [ ] I understand absolute URLs (full web addresses) vs relative URLs (local paths)
- [ ] I can make an image into a clickable link
- [ ] I can create a `mailto:` link that opens an email app
- [ ] I can use a button as a link with the `onclick` attribute
- [ ] I know what the `title` attribute does on a link
- [ ] I understand the four CSS link pseudo-classes: `a:link`, `a:visited`, `a:hover`, `a:active`
- [ ] I know the correct order for CSS link pseudo-classes (LVHA)
- [ ] I can style links as buttons using CSS
- [ ] I understand what a bookmark is and why it is useful
- [ ] I can create a bookmark using `id` on a target element
- [ ] I can link to a bookmark using `href="#id-name"`
- [ ] I can link to a bookmark on a different page using `href="page.html#id-name"`
- [ ] I can identify and fix the six common beginner mistakes from this lesson

---

## Lesson Summary

In this lesson, you covered one of the most fundamental building blocks of the web: **HTML Links**.

You started by learning that the `<a>` tag (the anchor element) combined with the `href` attribute is how all links are made in HTML. You explored the `target` attribute and its most useful value `_blank` for opening links in new tabs.

You then understood the important distinction between **absolute URLs** (full web addresses used for external sites) and **relative URLs** (shorter paths used for pages within your own website).

You discovered that links are not limited to text — images, buttons, and even email addresses can all be turned into clickable links.

In the styling section, you learned about **CSS link pseudo-classes** (`a:link`, `a:visited`, `a:hover`, `a:active`) and the critical LVHA rule for ordering them. You also saw how to style links to look like professional button components.

Finally, you mastered **bookmarks** — using the `id` attribute to mark destinations and the `#` prefix in `href` to create jump-links within the same page (or to sections on other pages).

All of these skills come together in real-world websites every day — from navigation menus to table of contents pages, from contact buttons to styled call-to-action links. You now have the tools to use them all confidently.

---

> **Next Up — Lesson 14: HTML Images**
> Now that you can navigate between pages with links, you will learn how to add and control images on your webpages, including background images, image maps, and the `<picture>` element.
