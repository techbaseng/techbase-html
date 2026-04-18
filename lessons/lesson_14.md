---
render_with_liquid: false
title: "Lesson 14 – HTML Images: From Basics to Responsive Pictures"
nav_order: 14
---

# Lesson 14 – HTML Images: From Basics to Responsive Pictures

---

## Lesson Introduction

Images are one of the most powerful tools in web design. A single photograph can tell a story, a diagram can explain a complex concept, and a well-placed logo can make a website feel professional and trustworthy.

In this lesson, you will learn **everything** about using images in HTML — from placing your first photo on a page, to creating clickable image maps, setting background images, and using the modern `<picture>` element to serve the right image to every device.

By the end of this lesson, you will be able to:
- Add images to any web page using the `<img>` tag
- Control image size, position, and floating behaviour
- Build interactive image maps with clickable regions
- Set background images on elements and the whole page
- Use the `<picture>` element for responsive images that adapt to different screen sizes

> **Real-world relevance:** Every website you visit — news sites, social media, e-commerce stores, portfolios — uses HTML images. Mastering this topic is essential for any front-end web developer, designer, or digital creator.

---

## Prerequisite Concepts

Before we start, let's make sure you understand a few ideas that this lesson builds on.

### What is an HTML Tag?

An HTML tag is a special keyword wrapped in angle brackets that tells the browser how to display content. For example:

```html
<p>This is a paragraph.</p>
```

- `<p>` is the **opening tag**
- `</p>` is the **closing tag**
- Some tags are **self-closing** — they have no content inside them and no closing tag. The `<img>` tag is one of these.

### What is an Attribute?

An attribute gives extra information about a tag. It lives inside the opening tag and follows a `name="value"` pattern.

```html
<img src="photo.jpg" alt="A lovely photo">
```

Here, `src` and `alt` are **attributes** of the `<img>` tag.

### What is a URL / File Path?

A **URL** (Uniform Resource Locator) is the address of a file on the internet or on your computer. For example:
- `photo.jpg` — a file in the **same folder** as your HTML file
- `images/photo.jpg` — a file inside a sub-folder called `images`
- `https://example.com/photo.jpg` — an image on a **different website**

---

## Part 1 – HTML Images: The Basics

### What Is the `<img>` Tag?

The `<img>` tag is how you embed (place) an image inside a web page. It is a **self-closing tag** — meaning it has no closing `</img>` tag. It only contains attributes.

Think of it like this: the `<img>` tag doesn't actually put an image *inside* the HTML code. Instead, it creates a **reserved space** on the page and tells the browser: "Go fetch the image from this location and display it here."

**Syntax:**

```html
<img src="url" alt="alternate text">
```

Let's break down each part:

| Part | Meaning |
|------|---------|
| `<img` | Opens the image tag |
| `src="url"` | **Source** — the path or URL to the image file |
| `alt="text"` | **Alternate text** — displayed if the image can't be shown |
| `>` | Closes the self-closing tag |

---

### The `src` Attribute — Where Is Your Image?

The `src` attribute tells the browser **where to find** the image. It is **required** — without it, there is no image to show.

> **Important:** When a browser loads a web page, it separately goes out and fetches each image. If the image file has been moved, renamed, or deleted, the browser cannot find it and will show a broken image icon instead.

**Example 1 – Image in the same folder:**

```html
<img src="cat.jpg" alt="A cute cat">
```

**Expected result:** A photo of a cat appears on the page.

**Example 2 – Image in a sub-folder:**

```html
<img src="images/cat.jpg" alt="A cute cat">
```

**Expected result:** The browser looks inside a folder named `images` to find `cat.jpg`.

**Example 3 – Image from another website (absolute URL):**

```html
<img src="https://www.example.com/photos/cat.jpg" alt="A cat from the internet">
```

**Expected result:** The browser fetches the image from the other website.

> **Warning about external images:** External images may be protected by copyright. Also, you have no control over them — they could be removed or changed at any time. Use external images only when you have permission.

---

### The `alt` Attribute — Always Include It!

The `alt` attribute provides a **text description** of the image. It serves two critical purposes:

1. **If the image fails to load** (wrong path, slow internet, etc.), the `alt` text is shown instead.
2. **For screen readers** — people who are visually impaired use software that reads web pages aloud. The screen reader reads the `alt` text so those users know what the image shows.

> **Screen Reader:** A screen reader is a program that converts web page content into spoken audio. It reads the HTML code, including `alt` text, so that visually impaired users can "hear" the content of a page. This makes `alt` attributes essential for web accessibility.

**Example — Image loads correctly:**

```html
<img src="sunset.jpg" alt="A beautiful orange and purple sunset over the ocean">
```

**Expected result:** The sunset photo appears on screen.

**Example — Image fails to load (wrong filename):**

```html
<img src="sunse.jpg" alt="A beautiful orange and purple sunset over the ocean">
```

**Expected result on screen:**
```
A beautiful orange and purple sunset over the ocean
```
The browser cannot find `sunse.jpg`, so it displays the alt text instead.

> **Thinking prompt:** What would happen if you left the `alt` attribute empty, like `alt=""`? Screen reader users would hear nothing — the image would be invisible to them. Always write a meaningful description!

---

### Controlling Image Size: `width` and `height`

By default, an image is displayed at its original size. You can resize it using:

**Method 1 – The `style` attribute (recommended):**

```html
<img src="dog.jpg" alt="A golden retriever" style="width:300px; height:200px;">
```

**Method 2 – The `width` and `height` attributes:**

```html
<img src="dog.jpg" alt="A golden retriever" width="300" height="200">
```

Both methods display the same result — an image that is 300 pixels wide and 200 pixels tall.

> **What is a pixel?** A pixel (px) is the smallest unit of display on a screen. A typical laptop screen is about 1920 pixels wide and 1080 pixels tall. When you set `width:300px`, the image occupies 300 of those tiny units across.

**Why use `style` instead of `width`/`height` attributes?**

If you use a CSS stylesheet that says `img { width: 100%; }`, it will **override** your `width` and `height` attributes, making your images stretch unexpectedly. The `style` attribute is more specific and **will not be overridden** by external stylesheets.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    img {
      width: 100%;  <!-- This affects BOTH images below -->
    }
  </style>
</head>
<body>
  <!-- This image WILL be stretched to 100% because the stylesheet overrides width attribute -->
  <img src="logo.gif" alt="Logo" width="128" height="128">

  <!-- This image WON'T be stretched because inline style takes priority -->
  <img src="logo.gif" alt="Logo" style="width:128px; height:128px;">
</body>
</html>
```

**Expected result:** The first image stretches to fill the page width. The second image stays exactly 128×128 pixels.

---

### Images in Sub-Folders

If your images are stored in a separate folder (good practice for keeping projects organised), you include the folder name in the path:

```html
<img src="/images/header.gif" alt="Website Header" style="width:128px; height:128px;">
```

Here `/images/` is the folder name and `header.gif` is the file name.

---

### Animated Images (GIFs)

HTML supports animated GIF files — images that play like short looping animations. You use them the same way as any other image:

```html
<img src="loading-spinner.gif" alt="Loading animation" style="width:48px; height:48px;">
```

**Expected result:** A spinning animation appears on screen.

> GIFs are commonly used for loading indicators, simple animations, and internet memes!

---

### Using an Image as a Link

You can wrap an `<img>` tag inside an `<a>` tag to make an image clickable — clicking it takes the user to another page:

```html
<a href="https://www.example.com">
  <img src="banner.jpg" alt="Click here to visit Example.com" style="width:200px; height:80px;">
</a>
```

**Expected result:** The banner image is displayed, and clicking on it navigates to `example.com`.

> **Analogy:** Think of this like a clickable picture in a magazine. Instead of just looking at the image, you can tap it to go somewhere new.

---

### Image Floating — Wrapping Text Around an Image

The CSS `float` property lets you position an image to the **left** or **right** of a text block, so the text flows around it — like you see in newspaper layouts.

**Float image to the right:**

```html
<p>
  <img src="smiley.gif" alt="Smiley face" style="float:right; width:60px; height:60px;">
  This is a paragraph of text. The image floats to the right side of this paragraph,
  and the text wraps around it on the left side.
</p>
```

**Expected result:** The smiley icon appears on the right side of the paragraph, and the text sits to its left.

**Float image to the left:**

```html
<p>
  <img src="smiley.gif" alt="Smiley face" style="float:left; width:60px; height:60px;">
  This paragraph has an image floating to its left side. The text wraps on the right.
</p>
```

**Expected result:** The smiley icon appears on the left, and the text flows to its right.

---

### Common Image File Formats

Different image formats are suited for different purposes. All modern browsers support these:

| Format | Best Used For | File Extension |
|--------|--------------|----------------|
| **JPEG** | Photographs and complex images | `.jpg`, `.jpeg` |
| **PNG** | Images needing transparency, logos, diagrams | `.png` |
| **GIF** | Simple animations, small icons | `.gif` |
| **SVG** | Vector graphics (logos, icons that scale perfectly) | `.svg` |
| **WebP** | Modern format — great quality at small file sizes | `.webp` |
| **APNG** | Animated PNG — like GIF but better quality | `.apng` |
| **ICO** | Browser tab icons (favicons) | `.ico` |

> **Practical tip:** For web pages, JPEG is great for photos (smaller file size), PNG is great for logos or anything with a transparent background, and SVG is ideal for icons that need to look sharp at any size.

> **Note:** Loading large images takes time and can slow down your web page. Always use appropriately sized images!

---

### Image Tags Quick Reference

| Tag | Purpose |
|-----|---------|
| `<img>` | Embeds an image on the page |
| `<map>` | Defines an image map (clickable regions on an image) |
| `<area>` | Defines a clickable area inside an image map |
| `<picture>` | Container for multiple image sources (responsive images) |

---

## Part 2 – HTML Image Maps

### What Is an Image Map?

An **image map** is an image with **multiple clickable zones**. Each zone takes the user to a different destination — or triggers a different action — when clicked.

**Real-world example:** Imagine a map of Africa. You click on Nigeria and go to a page about Nigeria. You click on Ghana and go to a page about Ghana. Each country is a different clickable zone on the same image.

---

### The Three Tags You Need

To build an image map, you need three things working together:

1. **`<img>`** — the image itself, with a special `usemap` attribute
2. **`<map>`** — a container that defines the clickable zones
3. **`<area>`** — one or more elements that define each clickable zone

---

### Step 1: The Image with `usemap`

```html
<img src="workplace.jpg" alt="Workplace" usemap="#workmap">
```

- `src="workplace.jpg"` — loads the image as usual
- `usemap="#workmap"` — **connects this image to a map** named `workmap`
  - The `#` sign means "look for something with this name on the same page"

---

### Step 2: The `<map>` Element

```html
<map name="workmap">
  <!-- clickable areas go here -->
</map>
```

- `name="workmap"` — **must exactly match** the `usemap` value (without the `#`)
- Everything inside `<map>` defines the clickable zones

---

### Step 3: The `<area>` Elements — Defining Clickable Zones

Each `<area>` element defines one clickable zone. You must specify:
- **`shape`** — what shape the clickable zone is
- **`coords`** — the coordinates (pixel positions) that define where the zone is
- **`href`** — where to go when the zone is clicked
- **`alt`** — description of the area (for accessibility)

#### Shape 1: Rectangle (`shape="rect"`)

A rectangle needs **two corner points**: the top-left corner and the bottom-right corner. Each point is given as `x,y` (horizontal pixels from the left, vertical pixels from the top).

```html
<area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
```

Breaking this down:
- `shape="rect"` — rectangular clickable zone
- `coords="34,44,270,350"` — means:
  - Top-left corner: 34px from left edge, 44px from top edge
  - Bottom-right corner: 270px from left edge, 350px from top edge
- `alt="Computer"` — description
- `href="computer.htm"` — destination when clicked

**Expected result:** A rectangular clickable zone appears over the computer part of the image.

#### Shape 2: Circle (`shape="circle"`)

A circle needs a **centre point** and a **radius** (how big the circle is).

```html
<area shape="circle" coords="337,300,44" alt="Coffee Cup" href="coffee.htm">
```

Breaking this down:
- `shape="circle"` — circular clickable zone
- `coords="337,300,44"` — means:
  - Centre point: 337px from left, 300px from top
  - Radius: 44 pixels (the circle extends 44px in all directions from the centre)
- `href="coffee.htm"` — destination when clicked

**Expected result:** A circular clickable zone appears over the coffee cup in the image.

#### Shape 3: Polygon (`shape="poly"`)

A polygon lets you define **any shape** using a series of connected points. This is useful for irregular shapes like countries on a map, or a croissant!

```html
<area shape="poly"
  coords="140,121,181,116,204,160,204,222,191,270,140,329,85,355,58,352,37,322,40,259,103,161,128,147"
  alt="Croissant" href="croissant.htm">
```

Breaking this down:
- `shape="poly"` — polygon (any shape with straight sides)
- `coords` — a list of x,y pairs that form the outline of the shape. Each pair is a corner of the polygon
  - `140,121` → first point (140px right, 121px down)
  - `181,116` → second point
  - `204,160` → third point
  - ...and so on, connecting the dots to form the shape
- `href="croissant.htm"` — destination

**Expected result:** A custom-shaped clickable zone precisely outlines the croissant.

#### Shape 4: Default (`shape="default"`)

The `default` shape makes the **entire image** clickable (as a fallback for any area not covered by other shapes):

```html
<area shape="default" href="home.htm" alt="Go to homepage">
```

---

### A Complete Image Map Example

Here is a full, working image map with three clickable zones:

```html
<!-- The image — connected to the map by usemap="#workmap" -->
<img src="workplace.jpg" alt="Workplace" usemap="#workmap">

<!-- The map — name matches usemap value (without #) -->
<map name="workmap">

  <!-- Rectangular area over the computer -->
  <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">

  <!-- Rectangular area over the phone -->
  <area shape="rect" coords="290,172,333,250" alt="Phone" href="phone.htm">

  <!-- Circular area over the coffee cup -->
  <area shape="circle" coords="337,300,44" alt="Coffee" href="coffee.htm">

</map>
```

**Expected result:**
- The `workplace.jpg` image is displayed normally
- Hovering over the computer area shows a hand cursor (indicating it's clickable)
- Clicking the computer area loads `computer.htm`
- Clicking the phone area loads `phone.htm`
- Clicking the coffee cup area loads `coffee.htm`

---

### Image Maps and JavaScript

A clickable area can also **run a JavaScript function** instead of (or in addition to) loading a new page. Use the `onclick` attribute:

```html
<map name="workmap">
  <area shape="circle" coords="337,300,44" href="coffee.htm" onclick="showCoffeeAlert()">
</map>

<script>
function showCoffeeAlert() {
  alert("You clicked the coffee cup!");
}
</script>
```

**Expected result:** When the user clicks the coffee cup area, a pop-up alert box appears with the message "You clicked the coffee cup!" before navigating to `coffee.htm`.

> **What is JavaScript?** JavaScript is a programming language that runs in the browser and makes web pages interactive. You don't need to know JavaScript to use this feature — just understand that `onclick="functionName()"` calls a function when something is clicked.

---

### How to Find Coordinates for an Image Map

How do you know what coordinates to use? Here's a simple process:

1. Open the image in an image editing tool (like Paint, Photoshop, or GIMP)
2. Hover your mouse over the area you want to make clickable
3. The software shows the current x,y position of your cursor
4. Note down the coordinates of the corners (for rectangles) or the centre + radius (for circles)

> **Online tool:** You can also search for "image map generator" online. These tools let you draw shapes on an image and automatically generate the coordinates for you.

---

## Part 3 – HTML Background Images

### What Is a Background Image?

A background image is an image placed **behind** the content of an HTML element, rather than as a visible image within the content. Think of it like the wallpaper behind the text and pictures on your computer desktop.

Background images are applied using **CSS** (specifically the `background-image` property), not with the `<img>` tag.

---

### Background Image on a Single Element

You can add a background image to any HTML element using the `style` attribute:

```html
<p style="background-image: url('forest.jpg');">
  This paragraph has a forest background image behind this text.
</p>
```

**Expected result:** The paragraph is displayed with the forest photo visible behind the text.

Or you can define it in a `<style>` block in the `<head>` of your document:

```html
<head>
  <style>
    p {
      background-image: url('forest.jpg');
    }
  </style>
</head>
<body>
  <p>This paragraph has a forest background.</p>
</body>
```

**Expected result:** All `<p>` elements on the page will have the forest background image.

---

### Background Image on the Entire Page

To give the **whole page** a background image, apply it to the `<body>` element:

```html
<style>
  body {
    background-image: url('beach.jpg');
  }
</style>
```

**Expected result:** The beach photo fills the background of the entire webpage.

---

### Background Repeat

By default, if the image is **smaller than the element**, it will automatically **tile (repeat)** — it copies itself horizontally and vertically until it fills the entire space. This is useful for textures and patterns, but can look messy with photographs.

**Default repeating behaviour:**

```html
<style>
  body {
    background-image: url('small_pattern.jpg');
  }
</style>
```

**Expected result:** The small pattern image tiles across the entire page.

**To stop repeating:**

```html
<style>
  body {
    background-image: url('photo.jpg');
    background-repeat: no-repeat;
  }
</style>
```

**Expected result:** The photo appears once in the top-left corner and does not repeat.

> **`background-repeat` values:**
> - `repeat` — default, tiles in both directions
> - `no-repeat` — shows the image only once
> - `repeat-x` — tiles only horizontally
> - `repeat-y` — tiles only vertically

---

### Background Cover — Fill the Entire Element

The most common professional technique is to make the image **cover the entire element** without repeating or distorting. Use `background-size: cover`:

```html
<style>
  body {
    background-image: url('hero.jpg');
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-size: cover;
  }
</style>
```

Let's understand each line:

| Property | Value | What it does |
|----------|-------|-------------|
| `background-image` | `url('hero.jpg')` | Loads the image |
| `background-repeat` | `no-repeat` | Stops the image from tiling |
| `background-attachment` | `fixed` | Keeps the image fixed in the viewport — it doesn't scroll with the page |
| `background-size` | `cover` | Scales the image to completely cover the element, maintaining proportions |

**Expected result:** The hero image fills the entire browser window, is fixed in place when you scroll, and maintains its proportions (no stretching or distortion).

> **Analogy:** `background-size: cover` is like fitting a photo over your phone screen — it fills the entire screen and crops any overflow, but the photo isn't distorted.

---

### Background Stretch — Stretch to Fit Exactly

If you want the image to stretch and fill the element **exactly** (including potentially distorting it), use `background-size: 100% 100%`:

```html
<style>
  body {
    background-image: url('texture.jpg');
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-size: 100% 100%;
  }
</style>
```

**Expected result:** The texture image is stretched to fill exactly 100% of the width and 100% of the height of the browser window. If you resize the browser, the image stretches with it.

> **Difference between `cover` and `100% 100%`:**
> - `cover` — keeps proportions, crops if needed
> - `100% 100%` — stretches to fit, may distort the image

---

### Background Image Summary

```html
<!-- Background on a paragraph -->
<p style="background-image: url('pattern.jpg');">Text here</p>

<!-- Background on the entire page, no repeat, covering -->
<style>
  body {
    background-image: url('page_bg.jpg');
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-size: cover;
  }
</style>
```

---

## Part 4 – The HTML `<picture>` Element

### The Problem: One Image Doesn't Fit All Screens

Think about this situation: You build a website with a beautiful wide landscape photo as your hero image — 1920 pixels wide. On a large desktop monitor, it looks stunning. But on a mobile phone, that 1920px image is:
- Far wider than the phone screen needs
- Much larger in file size than necessary (wastes mobile data)
- Possibly the wrong aspect ratio for a portrait phone screen

**The solution** is to serve different images to different devices. That's exactly what the `<picture>` element does!

---

### What Is the `<picture>` Element?

The `<picture>` element is a **container** that holds multiple image source options. The browser looks through the options and picks the **best match** for the current device or screen size — then displays that one image.

> **Analogy:** Think of a restaurant menu with a regular option and a kids' option. The waiter (browser) looks at who's asking and serves the appropriate version. The `<picture>` element is the menu; each `<source>` is a different option.

---

### Basic Structure of `<picture>`

```html
<picture>
  <source media="(min-width: 650px)" srcset="large_food.jpg">
  <source media="(min-width: 465px)" srcset="medium_car.jpg">
  <img src="small_girl.jpg" alt="A person standing outside">
</picture>
```

Let's break this down carefully:

**`<source>` element:**
- `media="(min-width: 650px)"` — a **media condition**: this source is used when the screen is at least 650 pixels wide
- `srcset="large_food.jpg"` — the image to load when the condition is true

**`<img>` element (the fallback):**
- This is the **default image** — always required
- It is used by browsers that don't support `<picture>`, or if none of the `<source>` conditions match
- Must always be the **last child** inside `<picture>`

**How the browser makes its decision:**

The browser reads through the `<source>` elements from top to bottom and uses the **first one that matches**. If nothing matches, it falls back to the `<img>` tag.

**For our example:**
- Screen is 800px wide → uses `large_food.jpg` (matches `min-width: 650px`)
- Screen is 500px wide → uses `medium_car.jpg` (matches `min-width: 465px`)
- Screen is 300px wide → uses `small_girl.jpg` (no conditions match, uses `<img>` fallback)

---

### Why Use `<picture>`? Two Main Reasons

#### Reason 1: Bandwidth (Data Saving)

Loading a 2MB image on a mobile phone wastes data and makes the page slow. With `<picture>`, you can load a small lightweight image on mobile and a high-quality large image on desktop.

**Example:**

```html
<picture>
  <!-- Desktop: load the full high-quality image -->
  <source media="(min-width: 1024px)" srcset="hero_desktop.jpg">

  <!-- Tablet: load a medium image -->
  <source media="(min-width: 600px)" srcset="hero_tablet.jpg">

  <!-- Mobile: load the smallest image (default fallback) -->
  <img src="hero_mobile.jpg" alt="Our company headquarters">
</picture>
```

**Expected result:**
- Desktop user (1024px+): sees `hero_desktop.jpg`
- Tablet user (600–1023px): sees `hero_tablet.jpg`
- Mobile user (under 600px): sees `hero_mobile.jpg`

Each user gets appropriately sized content without wasting bandwidth.

#### Reason 2: Format Support

Not every browser supports every image format. For example, some browsers may not support WebP (a modern, efficient format). With `<picture>`, you can offer the modern format first and fall back to a widely supported one:

```html
<picture>
  <!-- Try to use WebP first (smaller file, better quality) -->
  <source srcset="photo.webp">

  <!-- Fall back to PNG if WebP isn't supported -->
  <source srcset="photo.png">

  <!-- Final fallback: GIF (supported everywhere) -->
  <img src="photo.gif" alt="A scenic mountain view" style="width:auto;">
</picture>
```

**Expected result:**
- Browsers that support WebP → use `photo.webp`
- Browsers that support PNG (but not WebP) → use `photo.png`
- Other browsers → use `photo.gif`

> **Note:** The browser uses the **first `<source>` it recognises and can support**. Once a match is found, it ignores all the ones that follow.

---

### The `<picture>` Element vs. The `<img>` Element

| Feature | `<img>` | `<picture>` |
|---------|---------|------------|
| Shows one image | ✅ | ✅ |
| Adapts to screen size | ❌ | ✅ |
| Can serve different formats | ❌ | ✅ |
| Saves mobile data | ❌ | ✅ |
| Fallback for old browsers | N/A | Uses `<img>` inside it |
| Required for accessibility | `alt` on `<img>` | `alt` on inner `<img>` |

---

## Part 5 – Guided Practice Exercises

### Exercise 1: Your First Image

**Objective:** Add an image to an HTML page with proper alt text and sizing.

**Scenario:** You are building a simple web page about your favourite animal.

**Steps:**

1. Create a file called `animal.html`
2. Write the following base structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>My Favourite Animal</title>
</head>
<body>
  <h1>The African Lion</h1>

  <!-- Step 3: Add your image here -->

  <p>The African lion is one of the most majestic animals on the planet.
  Lions live in the grasslands and savannas of Africa.</p>
</body>
</html>
```

3. Add an `<img>` tag where the comment says to. Use:
   - `src="lion.jpg"` (imagine this file exists in your folder)
   - `alt="A lion resting on a rock in the African savanna"`
   - `style="width:400px; height:300px;"`

**Solution:**

```html
<img src="lion.jpg" alt="A lion resting on a rock in the African savanna" style="width:400px; height:300px;">
```

**Expected result:** A 400×300 pixel image of a lion appears on the page above the paragraph.

**Self-check questions:**
- What happens if you change `src="lion.jpg"` to `src="lions.jpg"` (wrong filename)?
- What does the `alt` text help with?
- Why might you use `style` for sizing instead of the `width` attribute?

---

### Exercise 2: Floating Image with Text

**Objective:** Make an image float next to text.

**Scenario:** You are writing a product description for a website. The product image should sit to the left, with the description text flowing to its right.

**Steps:**

1. Create a file called `product.html`
2. Add an image with `float:left` and some margin so the text doesn't crowd it:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Product Page</title>
</head>
<body>

  <h2>Premium Leather Wallet</h2>

  <img src="wallet.jpg"
       alt="A brown leather wallet with multiple card slots"
       style="float:left; width:150px; height:150px; margin-right:20px;">

  <p>This premium leather wallet features 6 card slots, a central cash compartment,
  and a sleek minimalist design. Handcrafted from genuine cowhide leather, it develops
  a beautiful patina over time. Available in brown, black, and tan.</p>

  <p>Perfect as a gift or a treat for yourself. Comes in a premium gift box.</p>

</body>
</html>
```

**Expected result:** The wallet image sits on the left side. Both paragraphs of text flow to its right.

**Self-check questions:**
- What would happen if you changed `float:left` to `float:right`?
- Why did we add `margin-right:20px` to the image?

---

### Exercise 3: Simple Image Map

**Objective:** Create an image map with two clickable regions.

**Scenario:** You have a photo of a fruit bowl with an apple and a banana. Clicking the apple takes users to an apple page; clicking the banana takes them to a banana page.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Fruit Bowl Image Map</title>
</head>
<body>

  <h2>Click on a Fruit to Learn More!</h2>

  <img src="fruit_bowl.jpg" alt="A fruit bowl with an apple and banana" usemap="#fruitmap">

  <map name="fruitmap">
    <!-- Apple is in the left area of the image: rectangle from (50,80) to (200,250) -->
    <area shape="rect"
          coords="50,80,200,250"
          alt="Apple"
          href="apple.html">

    <!-- Banana is in the right area: circle centred at (350,180) with radius 70 -->
    <area shape="circle"
          coords="350,180,70"
          alt="Banana"
          href="banana.html">
  </map>

</body>
</html>
```

**Expected result:**
- The fruit bowl image appears
- Clicking the apple region loads `apple.html`
- Clicking the banana region loads `banana.html`

**What-if challenge:** How would you add a third clickable area for a third fruit — say, a grape cluster in the upper right?

---

### Exercise 4: Background Image Page

**Objective:** Add a full-page background image.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Background Image Practice</title>
  <style>
    body {
      background-image: url('nature_bg.jpg');
      background-repeat: no-repeat;
      background-attachment: fixed;
      background-size: cover;
    }

    h1 {
      color: white;
      text-align: center;
      padding-top: 100px;
    }

    p {
      color: white;
      text-align: center;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <h1>Welcome to Nature's Paradise</h1>
  <p>Scroll down and notice how the background image stays fixed!</p>
  <p>This effect is created with background-attachment: fixed</p>
</body>
</html>
```

**Expected result:** The `nature_bg.jpg` image covers the entire page as a fixed background. White text appears over it.

**What-if challenge:** What happens if you change `background-attachment: fixed` to `background-attachment: scroll`? Try it!

---

### Exercise 5: Responsive `<picture>` Element

**Objective:** Serve different images to different screen sizes.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Responsive Image Practice</title>
</head>
<body>

  <h2>Our Headquarters</h2>

  <picture>
    <!-- Large screens: show a wide landscape photo -->
    <source media="(min-width: 800px)" srcset="hq_wide.jpg">

    <!-- Medium screens: show a portrait photo -->
    <source media="(min-width: 400px)" srcset="hq_medium.jpg">

    <!-- Small/mobile screens: show a close-up crop -->
    <img src="hq_small.jpg" alt="Our headquarters building in Lagos, Nigeria">
  </picture>

  <p>Our office is located in Victoria Island, Lagos.</p>

</body>
</html>
```

**Expected result:**
- Wide browser window (800px+): displays `hq_wide.jpg`
- Medium window (400–799px): displays `hq_medium.jpg`
- Narrow window (under 400px): displays `hq_small.jpg`

**Self-check questions:**
- Why do you always need the `<img>` element inside `<picture>`?
- What would happen if you removed all the `<source>` elements?

---

## Part 6 – Mini Project: "My City" Interactive Web Page

In this project, you will build a complete web page about your city (or any city you choose) that uses everything you've learned in this lesson.

### Project Overview

**Goal:** Build a city information page with:
- A hero background image
- A main image of the city with a float
- An interactive image map of a city landmark or map
- A responsive `<picture>` element for a gallery photo

---

### Stage 1: Setup — Create the Basic Structure

Create a file called `my_city.html`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Lagos, Nigeria - City Guide</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }
  </style>
</head>
<body>

  <!-- Content will go here -->

</body>
</html>
```

**Milestone output:** An empty page that loads without errors.

---

### Stage 2: Hero Section with Background Image

Add a hero section at the top of the page with a background image:

```html
<div style="
  background-image: url('lagos_skyline.jpg');
  background-size: cover;
  background-attachment: fixed;
  background-repeat: no-repeat;
  height: 300px;
  display: flex;
  align-items: center;
  justify-content: center;
">
  <h1 style="color: white; font-size: 48px; text-shadow: 2px 2px 4px black;">
    Welcome to Lagos
  </h1>
</div>
```

**Milestone output:** A 300px tall banner with a background photo and white "Welcome to Lagos" text overlaid.

---

### Stage 3: Floating City Image with Description

Below the hero, add a city image that floats with text around it:

```html
<div style="padding: 30px;">

  <h2>About Lagos</h2>

  <img src="lagos_market.jpg"
       alt="A bustling market scene in Lagos, Nigeria"
       style="float:left; width:250px; height:200px; margin-right:20px; margin-bottom:10px;">

  <p>Lagos is the largest city in Nigeria and one of the fastest-growing cities in the world.
  Known for its vibrant culture, incredible music scene, and entrepreneurial spirit,
  Lagos is the economic heartbeat of West Africa.</p>

  <p>From the beaches of Bar Beach to the tech hubs of Yaba, Lagos offers something
  for everyone. The city never sleeps, and neither does its ambition.</p>

  <div style="clear:both;"></div>

</div>
```

**Milestone output:** A market image floats left with the descriptive paragraphs to its right.

---

### Stage 4: Image Map of a Landmark

Add an image map of a famous Lagos location with clickable areas:

```html
<div style="padding: 30px; background-color: #f5f5f5;">
  <h2>Explore Lagos Landmarks</h2>
  <p>Click on a landmark to learn more:</p>

  <img src="lagos_map_photo.jpg"
       alt="Aerial view of central Lagos showing major landmarks"
       usemap="#lagosmap"
       style="width:600px; height:400px;">

  <map name="lagosmap">
    <area shape="rect" coords="50,50,200,180"
          alt="Lekki Conservation Centre"
          href="lekki.html"
          title="Lekki Conservation Centre">

    <area shape="circle" coords="320,200,60"
          alt="Eko Atlantic City"
          href="eko_atlantic.html"
          title="Eko Atlantic City">

    <area shape="rect" coords="400,250,550,380"
          alt="National Museum Lagos"
          href="museum.html"
          title="National Museum Lagos">
  </map>
</div>
```

**Milestone output:** An image of Lagos appears with three clickable zones — a rectangle for Lekki, a circle for Eko Atlantic, and a rectangle for the museum.

---

### Stage 5: Responsive Gallery with `<picture>`

Add a gallery section using the `<picture>` element:

```html
<div style="padding: 30px;">
  <h2>Photo of the Month</h2>

  <picture>
    <source media="(min-width: 900px)" srcset="lagos_beach_wide.jpg">
    <source media="(min-width: 500px)" srcset="lagos_beach_medium.jpg">
    <img src="lagos_beach_small.jpg"
         alt="Bar Beach in Lagos at sunset with golden light on the waves"
         style="width:100%; height:auto;">
  </picture>

  <p><em>Bar Beach at sunset — one of Lagos's most beautiful spots.</em></p>
</div>
```

**Milestone output:** A beach photo that adjusts to the screen size — wide on desktops, medium on tablets, compact on mobiles.

---

### Stage 6: Final Output Preview

Your complete page now has all five image techniques working together:
1. ✅ Background image with cover and fixed attachment
2. ✅ Floating image with text wrap
3. ✅ Image map with clickable areas
4. ✅ Responsive `<picture>` element

**Reflection questions:**
- Which technique did you find most interesting? Why?
- How would the page experience differ for a mobile user vs. a desktop user?
- What other cities or topics could you apply these techniques to?

**Optional advanced extensions:**
- Add JavaScript `onclick` alerts to your image map areas
- Add a second background image section mid-page
- Add a `default` area to your image map that links to a general overview page

---

## Part 7 – Common Beginner Mistakes

### Mistake 1: Missing the `alt` Attribute

❌ **Wrong:**
```html
<img src="photo.jpg">
```

✅ **Correct:**
```html
<img src="photo.jpg" alt="A description of what this photo shows">
```

**Why it matters:** Without `alt`, screen readers say nothing about the image. Users with slow internet who don't see the image get no information. It's also a web accessibility standard requirement.

---

### Mistake 2: Wrong File Name or Path (Case Sensitivity)

❌ **Wrong** (file is `Dog.jpg` but code says `dog.jpg`):
```html
<img src="dog.jpg" alt="A dog">
```

✅ **Correct** (exact match including capitalisation):
```html
<img src="Dog.jpg" alt="A dog">
```

**Why it matters:** File systems on web servers are often **case-sensitive** (unlike Windows). `Dog.jpg` and `dog.jpg` are treated as different files. Always match the filename exactly.

---

### Mistake 3: Forgetting `usemap="#"` Hash Symbol

❌ **Wrong:**
```html
<img src="map.jpg" usemap="mymap">
```

✅ **Correct:**
```html
<img src="map.jpg" usemap="#mymap">
```

**Why it matters:** The `#` symbol tells the browser to look for an element on the **same page**. Without it, the image map link is broken.

---

### Mistake 4: `map name` and `usemap` Value Not Matching

❌ **Wrong** (names don't match):
```html
<img src="map.jpg" usemap="#mymap">
<map name="map1">...</map>
```

✅ **Correct** (names match exactly):
```html
<img src="map.jpg" usemap="#mymap">
<map name="mymap">...</map>
```

**Why it matters:** The `usemap="#mymap"` value connects to `name="mymap"`. If they don't match exactly, the image map doesn't work at all.

---

### Mistake 5: Using `<img>` for Background Images

❌ **Wrong** (trying to use `<img>` as a background):
```html
<div>
  <img src="bg.jpg" style="position:absolute;">
  <p>Content here</p>
</div>
```

✅ **Correct** (use CSS `background-image`):
```html
<div style="background-image: url('bg.jpg'); background-size: cover;">
  <p>Content here</p>
</div>
```

**Why it matters:** `<img>` is for visible, content images. CSS `background-image` is for decorative backgrounds that sit behind content.

---

### Mistake 6: Forgetting the `<img>` Fallback Inside `<picture>`

❌ **Wrong** (no `<img>` fallback):
```html
<picture>
  <source media="(min-width: 800px)" srcset="large.jpg">
  <source media="(min-width: 400px)" srcset="medium.jpg">
</picture>
```

✅ **Correct** (always include `<img>` as the last element):
```html
<picture>
  <source media="(min-width: 800px)" srcset="large.jpg">
  <source media="(min-width: 400px)" srcset="medium.jpg">
  <img src="small.jpg" alt="A description of the image">
</picture>
```

**Why it matters:** Older browsers don't understand `<picture>` at all — they need the `<img>` element. Without it, those users see nothing.

---

### Mistake 7: Forgetting `background-repeat: no-repeat` with Background Images

❌ **Wrong** (photo tiles awkwardly):
```html
<style>
  body {
    background-image: url('sunset_photo.jpg');
    background-size: cover;
  }
</style>
```

✅ **Correct:**
```html
<style>
  body {
    background-image: url('sunset_photo.jpg');
    background-repeat: no-repeat;
    background-size: cover;
  }
</style>
```

**Why it matters:** Even with `background-size: cover`, some browsers may still show tiling artefacts in certain edge cases. Always explicitly set `background-repeat: no-repeat` when you don't want tiling.

---

### Mistake 8: Not Specifying Width and Height

❌ **Wrong** (may cause page to flicker during loading):
```html
<img src="large_photo.jpg" alt="A large photo">
```

✅ **Correct:**
```html
<img src="large_photo.jpg" alt="A large photo" style="width:800px; height:500px;">
```

**Why it matters:** If the browser doesn't know the image dimensions before it loads, the page layout can "jump" suddenly when the image finishes loading. Specifying dimensions reserves the correct space immediately.

---

## Reflection Questions

Think about these questions to deepen your understanding:

1. You have a website selling handmade jewellery. The main product photo is 5MB and loads slowly on mobile. Which technique from this lesson would you use to fix this, and how?

2. A client wants their company logo to be clickable — clicking different parts of the logo navigates to different sections of the website. Which HTML technique would you use?

3. What is the difference between using `<img>` and CSS `background-image`? When would you use each?

4. Why is the `alt` attribute not optional? Think about users with slow internet, screen readers, and search engines.

5. If you have a `<picture>` element with three `<source>` elements and one `<img>` element, in which order does the browser evaluate them? What does it do when it finds a match?

6. What would happen to your image map if you resize the image using CSS but forget to update the coordinates? Why is this a problem?

---

## Completion Checklist

Check off each item as you complete it:

- [ ] I understand what the `<img>` tag does and can write it from memory
- [ ] I know what `src` and `alt` attributes do and why both are required
- [ ] I can set image size using the `style` attribute
- [ ] I understand the difference between relative paths and absolute URLs for images
- [ ] I can make images float left or right with CSS
- [ ] I know the common HTML image file formats (JPEG, PNG, GIF, SVG, WebP)
- [ ] I understand what an image map is and can create one with `<map>` and `<area>`
- [ ] I can define rectangular, circular, and polygonal clickable areas
- [ ] I can add a background image to an element using CSS `background-image`
- [ ] I know how to prevent background image tiling with `background-repeat: no-repeat`
- [ ] I can use `background-size: cover` to make a background fill an element
- [ ] I understand what the `<picture>` element is for
- [ ] I can write a `<picture>` element with `<source>` and `<img>` fallback
- [ ] I understand the two main reasons to use `<picture>`: bandwidth and format support
- [ ] I have completed the Mini Project
- [ ] I understand and can avoid the common beginner mistakes

---

## Lesson Summary

In this lesson, you covered all four major areas of HTML images:

**Part 1 – Basic Images:** The `<img>` tag is the foundation. It uses `src` to find the image and `alt` to describe it. You can control size with `style`, float images next to text, link them with `<a>`, and use animated GIFs. Always specify width and height to prevent page flicker.

**Part 2 – Image Maps:** Using `<img usemap>`, `<map>`, and `<area>`, you can define clickable zones on a single image. Zones can be rectangles, circles, or polygons. Coordinates match pixel positions on the image. Image maps can link to pages or trigger JavaScript functions.

**Part 3 – Background Images:** CSS `background-image` places images behind content. Use `background-repeat: no-repeat` to prevent tiling, `background-size: cover` to fill the element proportionally, and `background-attachment: fixed` to keep it stationary during scroll.

**Part 4 – The `<picture>` Element:** For responsive, efficient web design, `<picture>` lets you specify multiple image sources. The browser picks the first `<source>` that matches the current conditions (screen size or format support). The `<img>` fallback is always required.

### HTML Image Tags Reference

| Tag | Description |
|-----|-------------|
| `<img>` | Embeds an image |
| `<map>` | Defines an image map |
| `<area>` | Defines a clickable area inside a map |
| `<picture>` | Container for multiple responsive image sources |

### Key CSS Background Properties

| Property | Common Values | Purpose |
|----------|--------------|---------|
| `background-image` | `url('file.jpg')` | Sets the background image |
| `background-repeat` | `no-repeat`, `repeat`, `repeat-x` | Controls tiling |
| `background-size` | `cover`, `contain`, `100% 100%` | Controls scaling |
| `background-attachment` | `fixed`, `scroll` | Controls scrolling behaviour |

---

> **You are now ready for Lesson 15!** The skills you've built here — controlling images in all their forms — form a foundation for every real-world web project you will ever create. Great work making it to the end of this lesson.
