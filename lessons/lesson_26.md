---
render_with_liquid: false
title: "Lesson 26: HTML Responsive Web Design"
nav_order: 26
---

# Lesson 26: HTML Responsive Web Design

---

## Lesson Introduction

Have you ever visited a website on your phone and everything looked tiny, crowded, or broken — and you had to zoom in and scroll sideways just to read it? That is what happens when a website is **not responsive**.

In this lesson, you will learn how to build web pages that **automatically look great on every device** — whether someone is using a giant desktop monitor, a laptop, a tablet, or a small smartphone screen.

This skill is one of the most important things a web developer can learn today. Think about it: most people in Nigeria and across the world now browse the internet mostly on their phones. If your website only looks good on a computer, you are losing a huge number of visitors.

By the end of this lesson, you will understand exactly what Responsive Web Design means, the tools and techniques used to achieve it, and you will build a complete responsive webpage yourself.

---

## Prerequisite Concepts

Before we dive in, let's make sure we understand a few words and ideas that will appear throughout this lesson. Do not worry — they are all very simple once explained.

### What is a "Screen" or "Viewport"?

A **viewport** is the visible area of a webpage inside your browser window. Think of it like a picture frame — the frame size changes depending on what device you are using.

- On a desktop computer, the viewport might be 1400 pixels wide.
- On a tablet, it might be 768 pixels wide.
- On a phone, it might be 375 pixels wide.

**Pixel** — A pixel (shortened to `px`) is one tiny dot of colour on your screen. Your screen is made up of millions of these tiny dots. When we say a screen is "1920 x 1080 pixels," we mean it is 1920 dots wide and 1080 dots tall.

### What is CSS?

CSS stands for **Cascading Style Sheets**. It is the language we use to style HTML — controlling colours, sizes, fonts, spacing, and layout. In this lesson, we will use a small amount of CSS to make things responsive. Do not worry; every CSS line will be explained carefully.

### What is a `<meta>` tag?

A `<meta>` tag goes inside the `<head>` section of your HTML and gives the browser **invisible instructions** about the page. You do not see `<meta>` tags on the page — they work behind the scenes. We will use one special `<meta>` tag in this lesson to tell the browser how to handle screen sizes.

---

## Conceptual Understanding

### What is Responsive Web Design?

**Responsive Web Design (RWD)** is the practice of writing HTML and CSS so that a webpage automatically adjusts — resizing, reorganising, hiding, or enlarging its content — to look good on any screen size.

Think of it like water in a container. Water takes the shape of whatever container it is poured into. A responsive webpage does the same — it flows and reshapes itself to fit the size of the device displaying it.

The three main things we make responsive are:

1. **Layout** — How columns and sections are arranged (side by side on a big screen, stacked on a small screen)
2. **Images** — Images should resize and never overflow outside the page
3. **Text** — Text size should scale nicely so it is always readable

### Why Does Responsive Design Matter?

In the real world, this matters enormously. Consider:

- A business website that is not responsive will look terrible on mobile phones. Customers will leave immediately.
- A school portal that is not responsive will frustrate students trying to submit assignments on their phones.
- A news website that is not responsive will have tiny, unreadable text on tablets.

According to global web traffic data, over 60% of all web visits happen on mobile devices. Responsive design is not optional — it is essential.

---

## Part 1: Setting the Viewport

### The Problem Without a Viewport Meta Tag

When you open an ordinary HTML file on a phone, the phone's browser tries to pretend it is a full desktop screen. It zooms out to fit the entire page into the small screen, making everything look tiny.

This is the wrong behaviour. We want the page to adapt naturally — not zoom out.

### The Solution: The Viewport Meta Tag

We fix this by adding one very important `<meta>` tag inside the `<head>` section of every webpage we want to be responsive.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Let's break this line down word by word:

| Part | Meaning |
|---|---|
| `<meta` | Opens a meta tag |
| `name="viewport"` | This meta tag is about the viewport (the visible screen area) |
| `content="..."` | The instructions we are giving the browser |
| `width=device-width` | Make the page width equal to the width of the device's screen |
| `initial-scale=1.0` | Start zoomed in at 100% (no zoom in or out at the beginning) |
| `>` | Closes the meta tag |

**Analogy:** Imagine you are printing a poster. Without the viewport tag, the printer shrinks a huge poster to fit onto a tiny page. With the viewport tag, you are telling the printer: "This page is for a small screen — format it for that size from the start."

### Example 1 — A Minimal Page With the Viewport Tag

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Responsive Page</title>
</head>
<body>
  <h1>Hello, World!</h1>
  <p>This page is set up to be responsive.</p>
</body>
</html>
```

**Expected Result:** When viewed on a phone, the text will appear at a normal, readable size — not zoomed out tiny.

> **Tip:** Always include the viewport meta tag on every single page you build. It is the first and most important step in making a page responsive. Without it, none of the other responsive techniques will work correctly on mobile devices.

### What Happens Without This Tag?

Without the viewport tag:
- The browser assumes the page is 980 pixels wide (a typical desktop width).
- It shrinks everything down to fit the phone's small screen.
- Text becomes tiny and unreadable.
- Users must pinch-zoom and scroll sideways.

With the viewport tag:
- The browser knows: "This page is designed for this device's actual screen width."
- Text, images, and layout all start at the right size.
- No horizontal scrolling needed.

---

## Part 2: Responsive Images

Images are one of the trickiest parts of responsive design. If you put a large image on your page without thinking about responsiveness, it might:
- Overflow outside the page on small screens (causing an ugly horizontal scrollbar), or
- Stay very small even on large screens.

We have two main ways to handle this.

### Method 1: Using `width: 100%`

If you set an image's width to `100%`, it will always stretch to fill whatever container it is inside. This means on a phone it fills the phone's width, and on a large monitor it fills the monitor's width.

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Image Example</title>
</head>
<body>
  <h2>This image always fills the full width:</h2>
  <img src="photo.jpg" style="width:100%;">
</body>
</html>
```

**Expected Result:** The image stretches to fill the full width of the screen on any device. On a tiny phone it fills the phone width. On a large monitor it fills the monitor width — and if the image is smaller than the monitor, it will get stretched and may look blurry.

**⚠️ Warning:** The problem with `width: 100%` is that it can stretch an image **larger than its original size**, which makes it look blurry and pixelated. For example, if you have a small 300px image and the screen is 1200px wide, the image will be stretched to 1200px — 4 times bigger. It will look bad.

### Method 2: Using `max-width: 100%` (Better Solution)

`max-width: 100%` is usually a better choice. It says: "The image can shrink down as small as needed (so it never overflows), but it will never grow larger than its original size."

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Image - max-width</title>
</head>
<body>
  <h2>This image scales down but never scales up beyond its original size:</h2>
  <img src="photo.jpg" style="max-width:100%; height:auto;">
</body>
</html>
```

**Expected Result:**
- On a screen smaller than the image: the image shrinks to fit.
- On a screen larger than the image: the image stays at its original size (it does not get stretched and blurry).

Let's understand the two CSS properties:

| CSS Property | Meaning |
|---|---|
| `max-width: 100%` | The image's width can be at most 100% of its container — but no more. It will shrink if needed, but never grow bigger than 100%. |
| `height: auto` | Automatically calculate the height to keep the original proportions (so the image does not look squished) |

**Thinking Prompt:** What would happen if you used `height: auto` but forgot `max-width: 100%`? The image would overflow on small screens and cause a horizontal scrollbar. Try it mentally!

### Quick Comparison

```
width:100%       → Image ALWAYS fills full width (can get blurry on large screens)
max-width:100%   → Image NEVER overflows, but stays original size on large screens
```

---

## Part 3: Showing Different Images for Different Screen Sizes

Sometimes you want to show a **completely different image** depending on the device. For example:
- On a phone: a small, close-up image that fits the small screen clearly.
- On a big desktop: a wide landscape image that looks great on the large screen.

HTML has a special element for this: `<picture>`.

### The `<picture>` Element

The `<picture>` element is a container that holds multiple `<source>` elements, each pointing to a different image for different screen sizes. The browser picks the best one automatically.

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Picture Element Example</title>
</head>
<body>

  <picture>
    <source srcset="small-image.jpg" media="(max-width: 600px)">
    <source srcset="medium-image.jpg" media="(max-width: 1500px)">
    <source srcset="large-image.jpg">
    <img src="small-image.jpg" alt="A beautiful scene">
  </picture>

</body>
</html>
```

**Expected Result:** 
- On a phone (screen ≤ 600px wide): `small-image.jpg` is displayed.
- On a tablet (600px–1500px wide): `medium-image.jpg` is displayed.
- On a large desktop (>1500px wide): `large-image.jpg` is displayed.

Let's break down the HTML carefully:

```html
<picture>
```
Opens the picture container. Everything inside is a set of options for the browser.

```html
<source srcset="small-image.jpg" media="(max-width: 600px)">
```
- `<source>` — Defines one image option.
- `srcset="small-image.jpg"` — The path to the image file to use.
- `media="(max-width: 600px)"` — Use this image **only when the screen is 600px wide or smaller**.

```html
<img src="small-image.jpg" alt="A beautiful scene">
```
This is the **fallback** — the image shown if the browser does not support `<picture>`, or if none of the `<source>` conditions are met. Always include this `<img>` inside `<picture>`.

> **Real-world use case:** An e-commerce website might show a product close-up on mobile (where detail matters) and a lifestyle photo showing the product in use on a wide desktop screen. This makes the site feel more natural and professional on every device.

**Thinking Prompt:** Why would we want different images for different devices, instead of just one image that scales? Because a wide landscape photo looks great on a big screen, but when shrunk to phone size, important details might become too small to see. A close-up photo works better on a small screen.

---

## Part 4: Responsive Text Size with `vw` Units

We know we can set text size using `px` (pixels) or `em` or `%`. But there is a special unit called `vw` that is perfect for responsive text.

### What is `vw`?

`vw` stands for **viewport width**. One `vw` equals **1% of the browser window's current width**.

So if your browser window is 1000px wide, then `1vw = 10px`. If the browser is 500px wide, then `1vw = 5px`.

This means text set in `vw` automatically scales up on big screens and scales down on small screens — without you writing any extra code!

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Text</title>
</head>
<body>

  <h1 style="font-size: 10vw;">Hello World</h1>
  <p style="font-size: 3vw;">This text also scales with the screen.</p>

</body>
</html>
```

**Expected Result:**
- On a wide 1000px screen: `10vw = 100px` for the heading (very large).
- On a narrow 400px phone: `10vw = 40px` for the heading (smaller, but still proportional).
- The text always looks balanced relative to the screen size.

**Analogy:** Think of `vw` like a percentage of the window. If the window is a room, `10vw` is "10% of the room's width." Whether the room is a tiny cupboard or a large hall, the text always takes up 10% of the room's width and scales automatically.

### Comparing Size Units

| Unit | What it means | Responsive? |
|---|---|---|
| `px` | Fixed number of pixels | No — stays the same on every screen |
| `%` | Percentage of parent element | Partly — depends on parent's size |
| `vw` | Percentage of viewport (browser window) width | Yes — scales with screen width |
| `em` | Relative to parent font size | Partly |

> **Tip:** Use `vw` for big display headings and banners. For body text (regular paragraphs), `px` or `em` is usually fine since paragraphs wrap naturally anyway.

---

## Part 5: Media Queries — The Heart of Responsive Design

So far we have seen individual responsive techniques. But what if you want to **completely change the layout** of a page depending on the screen size? For example, display 3 columns side by side on a large screen, but stack them one on top of the other on a small screen?

This is done with **CSS Media Queries**.

### What is a Media Query?

A media query is a CSS rule that says: **"Apply these styles ONLY when the screen matches this condition."**

Think of it like an if-statement in coding: *"IF the screen is small, THEN use this layout."*

### Basic Media Query Syntax

```css
@media screen and (max-width: 800px) {
  /* CSS rules here only apply when screen width is 800px or less */
}
```

Breaking it down:
- `@media` — Starts a media query block.
- `screen` — We are targeting screens (as opposed to printers, etc.).
- `and` — Combines conditions.
- `(max-width: 800px)` — The condition: only apply these styles when the screen is 800px wide or narrower.
- `{ ... }` — The CSS styles to apply when the condition is true.

The `800px` value is called a **breakpoint** — the point at which the layout "breaks" and changes to a different design.

### Example: Three Columns That Stack on Small Screens

This is one of the most classic and useful patterns in responsive design.

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Columns</title>
  <style>
    /* Default layout: three columns side by side */
    .left {
      float: left;
      width: 20%;
      background-color: lightblue;
      padding: 10px;
    }

    .main {
      float: left;
      width: 60%;
      background-color: lightyellow;
      padding: 10px;
    }

    .right {
      float: left;
      width: 20%;
      background-color: lightgreen;
      padding: 10px;
    }

    /* Media query: when screen is 800px or smaller, stack everything */
    @media screen and (max-width: 800px) {
      .left, .main, .right {
        width: 100%;  /* Each column takes full width - stacks vertically */
        float: none;  /* Remove the side-by-side floating */
      }
    }
  </style>
</head>
<body>

  <div class="left">Left Sidebar</div>
  <div class="main">Main Content</div>
  <div class="right">Right Sidebar</div>

</body>
</html>
```

**Expected Result:**
- On a large screen (>800px): Three columns appear side by side. Left column is 20% wide, main content is 60% wide, right column is 20% wide.
- On a small screen (≤800px): All three sections stack one on top of the other, each taking the full 100% width. No horizontal scrolling needed.

Let's trace through the CSS carefully:

**Default styles (always apply):**
```css
float: left;    /* Makes elements float next to each other (side by side) */
width: 20%;     /* The left and right columns take 20% of the screen each */
width: 60%;     /* The main column takes 60% (total: 20+60+20 = 100%) */
```

**Inside the media query (only when screen ≤ 800px):**
```css
width: 100%;    /* Each column now takes the full width */
float: none;    /* Remove the floating so they stack top to bottom */
```

> **Tip:** The most common breakpoints used by professional web developers are around 480px (phones), 768px (tablets), and 1024px (small laptops). You can use as many `@media` breakpoints as you need.

### Example 2: Different Background Colours Per Screen Size

Here is a simpler example to help you see exactly how media queries switch styles on and off:

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      background-color: lightgreen;  /* Default: green background */
    }

    @media screen and (max-width: 600px) {
      body {
        background-color: lightcoral;  /* On small screens: red background */
      }
    }
  </style>
</head>
<body>
  <h1>Resize me!</h1>
  <p>The background changes colour when the window is small.</p>
</body>
</html>
```

**Expected Result:**
- On a wide screen: background is light green.
- On a screen 600px or less: background changes to light coral (pinkish-red).

**Thinking Prompt:** What happens when the screen is exactly 600px wide? The media query condition `max-width: 600px` includes 600px, so at exactly 600px the red background applies. What if you change it to `max-width: 599px`? Then at 600px the green background would still show.

---

## Part 6: Using CSS Frameworks for Responsive Design

Building responsive layouts from scratch requires writing a lot of CSS. Professional developers often speed this up by using **CSS Frameworks** — pre-written collections of CSS that handle responsiveness for you.

Two of the most popular frameworks are **W3.CSS** and **Bootstrap**.

### What is a CSS Framework?

A CSS framework is a ready-made stylesheet full of CSS classes you can apply to your HTML. Instead of writing all the responsive CSS yourself, you just add the right class names to your elements and the framework handles the rest.

**Analogy:** A CSS framework is like a set of pre-made Lego pieces. Instead of carving each brick yourself, you use the pre-made bricks and assemble them into whatever you need.

### W3.CSS Framework

W3.CSS is a lightweight, modern CSS framework. You link it to your page using a single `<link>` tag.

```html
<!DOCTYPE html>
<html>
<head>
  <title>W3.CSS Example</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
</head>
<body>

  <div class="w3-container w3-green">
    <h1>W3Schools Demo</h1>
    <p>Resize this responsive page!</p>
  </div>

  <div class="w3-row-padding">

    <div class="w3-third">
      <h2>Lagos</h2>
      <p>Lagos is the largest city in Nigeria.</p>
      <p>It is one of the fastest-growing cities in Africa.</p>
    </div>

    <div class="w3-third">
      <h2>Abuja</h2>
      <p>Abuja is the capital city of Nigeria.</p>
      <p>It is located in the centre of the country.</p>
    </div>

    <div class="w3-third">
      <h2>Kano</h2>
      <p>Kano is one of Nigeria's oldest cities.</p>
      <p>It is known for its ancient walls and trade history.</p>
    </div>

  </div>

</body>
</html>
```

**Expected Result:**
- On a large screen: Three sections (Lagos, Abuja, Kano) appear side by side in three equal columns.
- On a small screen: The sections stack vertically — one on top of the other.

All of this responsive behaviour happens automatically because of the W3.CSS classes!

Let's understand the key class names used:

| Class | What it does |
|---|---|
| `w3-container` | Adds standard horizontal padding to a section |
| `w3-green` | Sets the background colour to green |
| `w3-row-padding` | Creates a row where child elements sit side by side with padding between them |
| `w3-third` | Makes an element take up exactly one-third of the row width |

### Bootstrap Framework

Bootstrap is the world's most widely used CSS framework. It provides a powerful grid system and a huge range of responsive components.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Bootstrap 5 Example</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"></script>
</head>
<body>

  <div class="container-fluid p-5 bg-primary text-white text-center">
    <h1>My Bootstrap Page</h1>
    <p>Resize this page to see the responsive layout change!</p>
  </div>

  <div class="container mt-5">
    <div class="row">

      <div class="col-sm-4">
        <h3>Column 1</h3>
        <p>This is the first column. On small screens it stacks.</p>
      </div>

      <div class="col-sm-4">
        <h3>Column 2</h3>
        <p>This is the second column.</p>
      </div>

      <div class="col-sm-4">
        <h3>Column 3</h3>
        <p>This is the third column.</p>
      </div>

    </div>
  </div>

</body>
</html>
```

**Expected Result:**
- On a screen 576px or wider: Three columns appear side by side.
- On a very small screen: All three columns stack vertically.

Key Bootstrap class names explained:

| Class | What it does |
|---|---|
| `container` | Creates a centred, fixed-width container |
| `container-fluid` | Creates a full-width container (always 100% wide) |
| `row` | Creates a horizontal row for columns |
| `col-sm-4` | Each column takes 4 out of 12 units of width (4+4+4 = 12 = full row) on small screens and above |
| `bg-primary` | Blue background colour |
| `text-white` | White text |
| `text-center` | Centred text |
| `mt-5` | Margin (space) at the top |
| `p-5` | Padding (space inside the box) |

> **Tip:** Bootstrap uses a 12-column grid system. When you say `col-sm-4`, you are saying "this element takes up 4 of the 12 available columns." Three elements each taking 4 columns fit perfectly in one row (4 + 4 + 4 = 12).

---

## Guided Practice Exercises

### Exercise 1: Add the Viewport Meta Tag

**Objective:** Understand the difference the viewport meta tag makes.

**Scenario:** You are building a simple news page. A friend tells you the page looks tiny on their phone.

**Steps:**

1. Create a new file called `news.html`.
2. Write the following code **without** the viewport meta tag first:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Daily News</title>
</head>
<body>
  <h1>Breaking News</h1>
  <p>The annual technology fair opens today in Lagos. Thousands of visitors are expected to attend over the three-day event, which showcases innovations in software, hardware, and digital services.</p>
</body>
</html>
```

3. Open it in your browser and shrink the browser window to simulate a phone (or use browser developer tools to simulate a mobile screen).
4. Notice how the text looks and if there is any scrolling.
5. Now add the viewport tag inside `<head>`:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

6. Refresh and compare.

**Expected Output (with viewport tag):** Text fills the width of the phone screen naturally. No zooming out. No horizontal scrolling.

**Self-check Questions:**
- What does `initial-scale=1.0` mean?
- What would happen if `initial-scale` was set to `2.0`?
- Why must the viewport tag go inside `<head>` and not `<body>`?

**Hint:** `initial-scale=2.0` would start the page zoomed in to 200% — text would appear very large initially.

---

### Exercise 2: Responsive Image

**Objective:** Make an image resize gracefully on different screens.

**Scenario:** You are building a portfolio page and want your profile photo to look good on any device.

**Steps:**

1. Create a file called `portfolio.html`.
2. First, try a fixed-size image:

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Portfolio</title>
</head>
<body>
  <h1>My Portfolio</h1>
  <!-- Fixed size - NOT responsive -->
  <img src="https://via.placeholder.com/800x400" style="width: 800px;">
  <p>Welcome to my portfolio website.</p>
</body>
</html>
```

3. Resize the browser window. Notice the image overflows and creates a horizontal scrollbar.
4. Now change the image to be responsive:

```html
<img src="https://via.placeholder.com/800x400" style="max-width: 100%; height: auto;">
```

**Expected Output:** The image shrinks gracefully when the window is small, and never causes a horizontal scrollbar.

**Self-check Questions:**
- What is the difference between `width: 100%` and `max-width: 100%`?
- When would `width: 100%` cause a problem?
- What does `height: auto` do?

---

### Exercise 3: Responsive Text with `vw`

**Objective:** Create a heading whose text size scales with the screen width.

**Steps:**

1. Create `text-demo.html`:

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Text</title>
</head>
<body>

  <h1 style="font-size: 8vw; color: navy;">Welcome to My Site</h1>
  <h2 style="font-size: 5vw; color: darkgreen;">Built with Responsive Design</h2>
  <p style="font-size: 2vw;">This paragraph also scales with the viewport width.</p>

</body>
</html>
```

2. Open in your browser. Slowly resize the window from very wide to very narrow.

**Expected Output:** All three text sizes shrink and grow proportionally as you resize the window. Nothing overflows. Nothing becomes unreadably small or excessively large.

**Self-check Questions:**
- If the screen is 500px wide, what will `8vw` equal in pixels?
- Why might `2vw` be too small for body text on a mobile phone?
- What unit might be safer for body paragraph text?

**Hint Answer:** 8vw on a 500px screen = 0.08 × 500 = 40px. And 2vw on a 375px phone = 7.5px — yes, that is quite small! For body text, `px` or `em` units are safer.

---

### Exercise 4: Media Query Layout Change

**Objective:** Build a two-column layout that stacks on small screens.

**Scenario:** You are building a blog. On desktop, the blog post is on the left and a sidebar is on the right. On phones, they should stack vertically.

**Steps:**

1. Create `blog.html`:

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Blog</title>
  <style>

    /* Default (large screen): two columns side by side */
    .blog-post {
      float: left;
      width: 70%;
      background-color: #f9f9f9;
      padding: 20px;
    }

    .sidebar {
      float: left;
      width: 30%;
      background-color: #e0f0ff;
      padding: 20px;
    }

    /* Small screen (700px or less): stack them */
    @media screen and (max-width: 700px) {
      .blog-post, .sidebar {
        width: 100%;
        float: none;
      }
    }

  </style>
</head>
<body>

  <h1>My Blog</h1>

  <div class="blog-post">
    <h2>My First Blog Post</h2>
    <p>Today I learned about responsive web design. It is amazing how a few lines of CSS can make a website work beautifully on every device.</p>
    <p>I used the viewport meta tag, max-width for images, and media queries for layout changes.</p>
  </div>

  <div class="sidebar">
    <h3>About Me</h3>
    <p>I am learning HTML and building my first website.</p>
    <h3>Categories</h3>
    <p>HTML, CSS, Web Design</p>
  </div>

</body>
</html>
```

2. Open in your browser.
3. Slowly shrink the window width.
4. At 700px, watch the layout change from two columns to stacked.

**Expected Output:**
- Wide window: Blog post (70% width) and sidebar (30% width) side by side.
- Narrow window (≤700px): Blog post above, sidebar below, both 100% width.

**What-if Challenge:** What would happen if you changed `max-width: 700px` to `min-width: 700px`? The logic would flip — the stacked layout would apply on large screens, and the two-column layout on small screens! Try it.

---

## Mini Project: Build a Responsive Profile Page

Now let's put everything together and build a complete, real-world responsive profile page.

### Project Description

You will build a personal profile page that:
- Looks great on both desktop and mobile.
- Has a header banner.
- Has a two-column section (profile info on the left, description on the right) that stacks on small screens.
- Has a responsive profile photo.
- Has a footer.

---

### Stage 1: Setup — HTML Structure

Start with the basic structure and viewport tag.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Profile Page</title>
  <style>
    /* We will add styles here in the next stages */
  </style>
</head>
<body>

  <!-- Stage 1 Milestone: Check that the page opens with a title -->
  <p>Building my responsive profile page...</p>

</body>
</html>
```

**Milestone Output:** Page opens in browser with the text "Building my responsive profile page..." visible.

---

### Stage 2: Core Layout — Header, Columns, Footer

Now add the real content and layout styles.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Profile Page</title>
  <style>

    /* Reset default margins */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      color: #333;
    }

    /* ===== HEADER ===== */
    .header {
      background-color: #2c3e50;
      color: white;
      text-align: center;
      padding: 30px 20px;
    }

    .header h1 {
      font-size: 8vw;  /* Responsive heading! */
    }

    .header p {
      font-size: 3vw;
      margin-top: 8px;
    }

    /* ===== MAIN CONTENT AREA ===== */
    .content-wrapper {
      max-width: 1000px;
      margin: 30px auto;
      padding: 0 20px;
    }

    /* ===== PROFILE SECTION - TWO COLUMNS ===== */
    .profile-left {
      float: left;
      width: 35%;
      background-color: white;
      padding: 20px;
      text-align: center;
    }

    .profile-right {
      float: left;
      width: 65%;
      background-color: white;
      padding: 20px;
    }

    /* Responsive image inside left column */
    .profile-left img {
      max-width: 100%;
      height: auto;
      border-radius: 50%;  /* Makes it circular */
      border: 4px solid #2c3e50;
    }

    /* ===== FOOTER ===== */
    .footer {
      background-color: #2c3e50;
      color: white;
      text-align: center;
      padding: 20px;
      margin-top: 40px;
      clear: both;  /* Ensures footer appears below the floated columns */
    }

    /* ===== MEDIA QUERY - SMALL SCREENS ===== */
    @media screen and (max-width: 600px) {

      /* Stack the columns */
      .profile-left, .profile-right {
        width: 100%;
        float: none;
      }

      /* Reduce image size on mobile */
      .profile-left img {
        width: 150px;
      }

      /* Adjust header text on very small screens */
      .header h1 {
        font-size: 10vw;
      }

      .header p {
        font-size: 4vw;
      }

    }

  </style>
</head>
<body>

  <!-- HEADER -->
  <div class="header">
    <h1>Chidi Okafor</h1>
    <p>Web Developer | Lagos, Nigeria</p>
  </div>

  <!-- MAIN CONTENT -->
  <div class="content-wrapper">

    <!-- LEFT COLUMN: Photo and quick info -->
    <div class="profile-left">
      <img src="https://via.placeholder.com/200" alt="Profile Photo">
      <h3 style="margin-top: 15px;">Chidi Okafor</h3>
      <p style="color: #666;">Front-End Developer</p>
      <p style="margin-top: 10px;">📍 Lagos, Nigeria</p>
      <p>📧 chidi@example.com</p>
    </div>

    <!-- RIGHT COLUMN: About and skills -->
    <div class="profile-right">
      <h2>About Me</h2>
      <p style="margin-top: 10px; line-height: 1.7;">
        Hello! I am a passionate web developer based in Lagos, Nigeria.
        I love building websites that are both beautiful and functional.
        I am currently learning HTML, CSS, and JavaScript.
      </p>

      <h2 style="margin-top: 20px;">My Skills</h2>
      <p style="margin-top: 10px;">✅ HTML</p>
      <p>✅ CSS</p>
      <p>✅ Responsive Web Design</p>
      <p>✅ Bootstrap</p>

      <h2 style="margin-top: 20px;">Projects</h2>
      <p style="margin-top: 10px;">🔗 Personal Blog</p>
      <p>🔗 Portfolio Website</p>
      <p>🔗 Restaurant Landing Page</p>
    </div>

  </div>

  <!-- FOOTER -->
  <div class="footer">
    <p>© 2026 Chidi Okafor. Built with HTML and CSS.</p>
    <p style="margin-top: 8px; color: #aaa;">This page is fully responsive!</p>
  </div>

</body>
</html>
```

**Milestone Output (Large Screen):**
- Dark blue header banner with name and title at the top.
- Two-column section: photo and quick info on the left (35%), detailed bio on the right (65%).
- Dark blue footer at the bottom.

**Milestone Output (Small Screen ≤ 600px):**
- Header text scales to `10vw` for the name and `4vw` for the subtitle.
- Left column (photo) appears at full width, centred.
- Right column (bio) appears below, also at full width.
- No horizontal scrollbar anywhere.

---

### Stage 3: Enhancements — Add a Picture Element

Let's also add a decorative banner image that shows a different image on large and small screens.

Add this HTML right after the `</div>` of the header:

```html
<!-- BANNER IMAGE - different image for different screens -->
<picture>
  <source srcset="https://via.placeholder.com/400x150" media="(max-width: 600px)">
  <source srcset="https://via.placeholder.com/1000x200">
  <img src="https://via.placeholder.com/1000x200"
       alt="Banner"
       style="width:100%; display:block;">
</picture>
```

**Expected Output:** A banner image appears below the header. On a narrow screen (≤600px) a 400x150 version loads; on wide screens a 1000x200 version loads.

---

### Stage 4: Reflection Questions

After completing your profile page, think about the following:

1. What would happen if you removed the viewport meta tag and opened the page on a phone?
2. Why did we use `float: none` in the media query instead of just `float: right`?
3. Why is `clear: both` important on the footer element?
4. Why did we use `max-width: 100%` for the profile image instead of `width: 100%`?
5. How could you make this page look even better? (Think about adding a navigation bar, colours, or hover effects.)

**Optional Advanced Extension:** Try adding a second media query for medium screens (tablets, 601px–900px). In this breakpoint, make the left column 40% and right column 60%. This creates a three-tier layout: phone (stacked), tablet (40/60), desktop (35/65).

---

## Common Beginner Mistakes

### Mistake 1: Forgetting the Viewport Meta Tag

**What happens:** Even if you write perfect responsive CSS, the page will still look zoomed out on phones because the browser does not know to respect your CSS at phone size.

**Wrong:**
```html
<head>
  <title>My Page</title>
  <!-- Viewport tag missing! -->
</head>
```

**Correct:**
```html
<head>
  <title>My Page</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```

---

### Mistake 2: Using `width: 100%` Instead of `max-width: 100%` for Images

**What happens:** Images stretch larger than their original size and become blurry on big screens.

**Wrong:**
```html
<img src="small-photo.jpg" style="width: 100%;">
```

**Correct:**
```html
<img src="small-photo.jpg" style="max-width: 100%; height: auto;">
```

---

### Mistake 3: Forgetting `height: auto` with `max-width: 100%`

**What happens:** The image width shrinks responsively but the height stays fixed, making the image look squished and distorted.

**Wrong:**
```html
<img src="photo.jpg" style="max-width: 100%; height: 300px;">
```

**Correct:**
```html
<img src="photo.jpg" style="max-width: 100%; height: auto;">
```

`height: auto` tells the browser to calculate the height automatically to preserve the image's original proportions.

---

### Mistake 4: Writing Media Queries Without `screen`

**What happens:** Usually still works, but is not best practice. It is better to specify `screen` to target screen displays explicitly.

**Less precise:**
```css
@media (max-width: 600px) {
  /* works, but not explicit */
}
```

**Best practice:**
```css
@media screen and (max-width: 600px) {
  /* explicitly targeting screens */
}
```

---

### Mistake 5: Mixing Up `max-width` and `min-width` in Media Queries

**What happens:** The layout applies on the wrong screens — exactly the opposite of what you wanted.

- `max-width: 600px` means: "Apply this CSS when the screen is **600px or smaller** (i.e., small/phone screens)."
- `min-width: 600px` means: "Apply this CSS when the screen is **600px or larger** (i.e., larger screens)."

**Wrong (applying phone styles to desktops):**
```css
@media screen and (min-width: 600px) {
  .columns { width: 100%; float: none; }  /* This wrongly stacks on desktop! */
}
```

**Correct (applying phone styles to phones):**
```css
@media screen and (max-width: 600px) {
  .columns { width: 100%; float: none; }  /* Correctly stacks on small screens */
}
```

---

### Mistake 6: Not Using `clear: both` After Floated Elements

**What happens:** The footer or next section "climbs up" and overlaps with your floated columns, causing a messy, broken layout.

**Wrong:**
```html
<div class="left-col">...</div>
<div class="right-col">...</div>
<footer>...</footer>  <!-- Footer overlaps with columns! -->
```

**Correct — add `clear: both` to the footer:**
```html
<div class="left-col">...</div>
<div class="right-col">...</div>
<footer style="clear: both;">...</footer>  <!-- Footer correctly appears below columns -->
```

---

## Reflection Questions

1. In your own words, explain what "Responsive Web Design" means to someone who has never heard the term.
2. Why is the viewport meta tag the very first thing you must add to make a page responsive?
3. What is the difference between `width: 100%` and `max-width: 100%` when applied to an image?
4. Explain in simple language what a CSS Media Query does.
5. What is a "breakpoint" in responsive design?
6. What does `vw` stand for, and why is it useful for responsive text?
7. Why would a developer choose to use the `<picture>` element instead of a simple `<img>` tag?
8. Name one advantage and one disadvantage of using a CSS framework like Bootstrap instead of writing your own responsive CSS.
9. When would you use `max-width` in a media query versus `min-width`?
10. Look at the three-column layout example. If the viewport width is 750px, which CSS rules apply — the default rules or the media query rules?

---

## Completion Checklist

Before moving on to the next lesson, confirm that you can do all of the following:

- [ ] I understand what Responsive Web Design is and why it matters.
- [ ] I know what a viewport is and can explain it in simple terms.
- [ ] I can write the viewport meta tag correctly from memory.
- [ ] I understand the difference between `width: 100%` and `max-width: 100%` for images.
- [ ] I know how to use the `<picture>` element to show different images on different screen sizes.
- [ ] I understand what `vw` units are and how they make text responsive.
- [ ] I can write a basic CSS media query with a breakpoint.
- [ ] I understand what a "breakpoint" is.
- [ ] I know what `max-width` and `min-width` mean in media queries.
- [ ] I know what `float: none` and `clear: both` do in a responsive layout.
- [ ] I know what W3.CSS and Bootstrap are, and how to link them to a page.
- [ ] I have completed all four guided exercises.
- [ ] I have built the complete responsive profile page mini project.
- [ ] I can list at least four common beginner mistakes in responsive design.

---

## Lesson Summary

In this lesson, you have learned everything you need to start building websites that look great on every device — from large desktop monitors to tiny smartphone screens.

Here is a quick recap of what you learned:

**Viewport Meta Tag** — The most important first step. Always add this to the `<head>` of every page:
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**Responsive Images** — Use `max-width: 100%; height: auto;` to make images shrink on small screens without ever becoming blurry by overgrowing on large screens.

**The `<picture>` Element** — Use this to show completely different image files on different screen sizes, giving you full control over visual quality on every device.

**Responsive Text with `vw`** — Use `vw` units for headings and banners so text scales naturally with the viewport width.

**CSS Media Queries** — The core tool of responsive design. Write different CSS rules for different screen sizes using the `@media` rule:
```css
@media screen and (max-width: 600px) {
  /* CSS rules for small screens */
}
```

**CSS Frameworks (W3.CSS and Bootstrap)** — Pre-made, free CSS libraries that handle responsive behaviour for you, helping you build professional-looking responsive pages faster.

Responsive Web Design is a fundamental, non-negotiable skill for any modern web developer. With what you have learned in this lesson, you are ready to build websites that work beautifully for every visitor — no matter what device they use to reach you.
