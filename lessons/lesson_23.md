---
render_with_liquid: false
title: "Lesson 23 – HTML File Paths"
nav_order: 23
---

# Lesson 23 – HTML File Paths

---

## Lesson Introduction

Welcome to Lesson 23! In this lesson you will learn about one of the most practically important concepts in web development: **file paths**.

Every time you add an image, link to another page, attach a stylesheet, or include a JavaScript file, you have to tell the browser **where that file lives**. That address is called a **file path**. If you get it wrong, the image won't load, the link will break, or the style won't apply — and the page will look completely wrong.

By the end of this lesson you will be able to:

- Understand what a file path is and why it is needed
- Describe the difference between absolute and relative file paths
- Write correct relative file paths for files in the same folder, inside subfolders, and in parent folders
- Know when to use absolute vs relative file paths
- Understand why relative file paths are best practice
- Apply file paths confidently to images, links, stylesheets, and scripts
- Build and navigate a realistic website folder structure

Think of file paths like a **postal address**. When you send a letter, you write the full address on the envelope. On a website, when you want to show an image, you write the file path — the "address" of that image — so the browser knows exactly where to find it.

---

## Prerequisite Concepts

Before we begin, let's make sure you understand a few foundational ideas.

### What is a File and a Folder?

A **file** is a document stored on a computer. Examples: `index.html`, `photo.jpg`, `style.css`.

A **folder** (also called a **directory**) is a container that holds files and other folders. You use folders to organise files, just like a filing cabinet holds documents in labelled drawers.

### What is a Website Folder Structure?

A website is made of many files — HTML pages, images, CSS stylesheets, JavaScript files, and more. These files are organised into folders. The arrangement of those folders and files is called the **folder structure** (or **directory structure**).

Here is a simple example of what a website's folder structure might look like:

```
my-website/
│
├── index.html
├── about.html
├── contact.html
│
├── images/
│   ├── logo.png
│   ├── banner.jpg
│   └── team-photo.jpg
│
├── css/
│   └── style.css
│
└── js/
    └── script.js
```

- `my-website/` is the **root folder** — the main container for everything.
- `index.html`, `about.html`, `contact.html` are HTML page files stored directly in the root.
- `images/` is a **subfolder** containing image files.
- `css/` is a subfolder containing stylesheet files.
- `js/` is a subfolder containing JavaScript files.

Understanding this structure is essential because file paths describe how to navigate from one file to another within it.

### What is an HTML Attribute Value?

A file path is always written as the **value** of an HTML attribute. For example, the `src` attribute of the `<img>` tag tells the browser where to find the image:

```html
<img src="images/logo.png" alt="Logo">
```

Here, `"images/logo.png"` is the file path. It is the value of `src`.

---

## What is a File Path?

A **file path** is the text that describes the **location of a file** within a website's folder structure. It is like a set of directions — it tells the browser how to navigate from where it currently is to where the file it needs is stored.

### Where are file paths used in HTML?

File paths appear as attribute values in many places:

- **Images:** `<img src="path/to/image.jpg">`
- **Links:** `<a href="path/to/page.html">`
- **Stylesheets:** `<link rel="stylesheet" href="path/to/style.css">`
- **Scripts:** `<script src="path/to/script.js"></script>`

The path goes inside the quotes of the attribute value.

---

## The Two Types of File Paths

There are two completely different ways to write a file path: **absolute** and **relative**.

Think of it this way. Imagine you want to give someone directions to a restaurant:

- **Absolute path:** "The restaurant is at 14 Market Street, Lagos, Nigeria." — This is the full, complete address. Anyone in the world can find it.
- **Relative path:** "From where you are now, walk two blocks north and turn left." — These directions only work if you know where the person is starting from.

Both approaches have a time and place. Let's explore each one.

---

## Part 1 – Absolute File Paths

### What is an Absolute File Path?

An **absolute file path** is the **complete, full URL** to a file. It includes everything needed to locate the file from anywhere on the internet — the protocol (`https://`), the domain name, and the full path to the file.

**Format:**

```
https://www.example.com/folder/filename.ext
```

### Example — Absolute Path to an Image

```html
<img src="https://www.w3schools.com/images/picture.jpg" alt="Mountain">
```

**Breaking this down piece by piece:**

| Part | What it means |
|---|---|
| `https://` | The protocol — how data is transferred securely |
| `www.w3schools.com` | The domain name — which website/server to go to |
| `/images/` | The folder on that server |
| `picture.jpg` | The actual file name |

**Expected behaviour:** The browser goes to `www.w3schools.com`, navigates into the `images` folder there, and loads `picture.jpg`.

### When would you use an absolute path?

Use an absolute path when you want to link to or display a file that lives on **a different website entirely** — a file you do not own or host yourself.

**Real-world examples:**
- Embedding an image hosted on a company's CDN (content delivery network)
- Linking to a resource on Wikipedia, Google, or a third-party API
- Using a font from Google Fonts: `<link href="https://fonts.googleapis.com/css?family=Roboto">`

### The Problem with Absolute Paths for Your Own Files

If you use absolute paths for files within your **own website**, you create a big problem:

Imagine your website is currently at `https://mysite.com`. You hard-code this path:

```html
<img src="https://mysite.com/images/logo.png">
```

Now imagine:
- You are testing your website on your **own computer** (localhost). The absolute URL `https://mysite.com` won't work there.
- You move your website to **a different domain** (e.g., `https://mynewsite.com`). Every single absolute path in every file would be broken and would need to be updated manually.

This is why **relative file paths** are strongly preferred for files within your own website.

---

## Part 2 – Relative File Paths

### What is a Relative File Path?

A **relative file path** points to a file **relative to the location of the current HTML page**. In other words, it gives directions based on where you currently are — not a full address from the start of the internet.

When you use a relative path, you are essentially saying: "Starting from the folder where this HTML file lives, here is how to find the other file."

There are three key patterns:

1. The file is in the **same folder** as the current page
2. The file is in a **subfolder** (one level down)
3. The file is in the **root** of the website (using `/`)
4. The file is in a folder **one level up** from the current page (using `../`)

Let's explore each pattern in depth with folder structure diagrams and examples.

---

### Pattern 1 – File in the Same Folder

**When to use:** The file you need is sitting right beside your HTML file in the same folder.

**Syntax:** Just write the filename directly.

```html
<img src="picture.jpg" alt="A picture">
```

**Folder structure:**

```
my-website/
├── index.html        ← you are here
└── picture.jpg       ← file you want
```

**How it works:** The browser looks in the same folder as `index.html` and finds `picture.jpg` right there.

**Full example:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Same Folder Example</title>
</head>
<body>

  <h1>My Photo</h1>
  <img src="picture.jpg" alt="A beautiful mountain">

</body>
</html>
```

**Expected Output:** The image `picture.jpg` (which is in the same folder as this HTML file) is displayed on the page below the heading.

> 💡 **Analogy:** Imagine you are standing in your bedroom. A book on your desk is in the "same folder". You just reach out and grab it — no directions needed.

---

### Pattern 2 – File in a Subfolder

**When to use:** The file is stored inside a folder that is inside your current folder. This is the most common pattern in real websites — images almost always live in an `images/` folder.

**Syntax:** Write the folder name, then a forward slash `/`, then the filename.

```html
<img src="images/picture.jpg" alt="A picture">
```

**Folder structure:**

```
my-website/
├── index.html           ← you are here
└── images/
    └── picture.jpg      ← file you want
```

**How it works:** From the folder where `index.html` lives, go **into** the `images` subfolder, then find `picture.jpg`.

**Full example:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Subfolder Example</title>
</head>
<body>

  <h1>Gallery</h1>
  <img src="images/photo1.jpg" alt="Photo 1">
  <img src="images/photo2.jpg" alt="Photo 2">
  <img src="images/photo3.jpg" alt="Photo 3">

</body>
</html>
```

**Expected Output:** Three images are displayed, each loaded from the `images/` subfolder.

**Nesting deeper — multiple levels down:**

If your images are inside a subfolder inside another subfolder, you chain the folder names with `/`:

```
my-website/
├── index.html
└── assets/
    └── images/
        └── hero.jpg
```

Path to `hero.jpg` from `index.html`:

```html
<img src="assets/images/hero.jpg" alt="Hero image">
```

You simply keep adding folder names separated by `/` for each level you go deeper.

> 💡 **Analogy:** Imagine navigating a filing cabinet. The `images/` folder is like opening the second drawer, and `picture.jpg` is a document inside it. You open the drawer, then grab the document.

---

### Pattern 3 – File at the Website Root (Starting with `/`)

**When to use:** You want to reference a file from the very **root** of your website — the top-most folder — regardless of where your current page is.

**Syntax:** Start the path with a `/` (forward slash).

```html
<img src="/images/picture.jpg" alt="A picture">
```

**Folder structure:**

```
my-website/           ← ROOT of the website
├── index.html
├── about/
│   └── about.html    ← you are here (inside a subfolder)
└── images/
    └── picture.jpg   ← file you want (back at root level)
```

**How it works:** The `/` at the start means "start from the root of the website". The browser goes to the top-level folder of the site, then navigates into `images/`, then finds `picture.jpg`.

**Full example — used from a page inside a subfolder:**

```html
<!-- This is about/about.html -->
<!DOCTYPE html>
<html>
<head>
  <title>About Us</title>
</head>
<body>

  <h1>About Our Company</h1>
  <!-- The /images/ path works from ANY page, anywhere on the site -->
  <img src="/images/logo.png" alt="Company Logo">

</body>
</html>
```

**Expected Output:** The logo loads correctly even though `about.html` is inside the `about/` subfolder, because `/images/logo.png` starts from the root.

**Why is this useful?**  
If you have a logo or navigation image that appears on every page of your site — including pages inside subfolders — using a root-relative path (`/images/logo.png`) means you write the same path on every page and it always works.

> ⚠️ **Important note:** Root-relative paths starting with `/` work when your site is running on a web server (or localhost). They do NOT work when you simply double-click an HTML file and open it from your desktop as a local file. For local file testing, use the subfolder pattern (no leading `/`).

---

### Pattern 4 – File One Level Up (Using `../`)

**When to use:** The file you need is in the **parent folder** — the folder one level above your current location.

**Syntax:** Use `../` to go one folder up, then navigate from there.

```html
<img src="../picture.jpg" alt="A picture">
```

**Folder structure:**

```
my-website/
├── picture.jpg          ← file you want (one level up)
└── pages/
    └── about.html       ← you are here
```

**How it works:** `../` means "go up one folder level". So from `pages/`, going `../` takes you back to `my-website/`, where `picture.jpg` lives.

**Full example:**

```html
<!-- This is pages/about.html -->
<!DOCTYPE html>
<html>
<head>
  <title>About</title>
</head>
<body>

  <h1>About Page</h1>
  <!-- Go up one level (out of pages/), then find picture.jpg -->
  <img src="../picture.jpg" alt="A picture">

</body>
</html>
```

**Expected Output:** The image `picture.jpg` from the `my-website/` folder is displayed on the about page.

**Going up and into another folder:**

You can combine `../` with a folder name to go up one level and then into a different subfolder:

```
my-website/
├── images/
│   └── logo.png        ← file you want
└── pages/
    └── about.html      ← you are here
```

Path: `../images/logo.png`

```html
<img src="../images/logo.png" alt="Logo">
```

**Step-by-step navigation:**
1. `../` — Go up one level: from `pages/` to `my-website/`
2. `images/` — Go into the `images/` folder
3. `logo.png` — Find the file

**Going up two levels — `../../`:**

If you are two folders deep and need to go all the way up to the root:

```
my-website/
├── banner.jpg            ← file you want
└── sections/
    └── blog/
        └── post.html     ← you are here
```

Path: `../../banner.jpg`

```html
<img src="../../banner.jpg" alt="Banner">
```

Each `../` goes up exactly one folder level.

> 💡 **Analogy:** Imagine you are in a room inside a house, and you need something from the street outside. `../` is like walking out of the room into the hallway. `../../` is like walking out of the hallway through the front door. Each `../` is one door you walk through to get further out.

---

## Complete File Path Summary Table

| Path | Meaning | Example |
|---|---|---|
| `filename.jpg` | Same folder as current page | `<img src="photo.jpg">` |
| `folder/filename.jpg` | File is inside a subfolder | `<img src="images/photo.jpg">` |
| `/folder/filename.jpg` | File at website root, then into folder | `<img src="/images/photo.jpg">` |
| `../filename.jpg` | File is one folder level up | `<img src="../photo.jpg">` |
| `../folder/filename.jpg` | Up one level, then into a subfolder | `<img src="../images/photo.jpg">` |
| `https://example.com/img.jpg` | Full URL — file on a different website | `<img src="https://site.com/img.jpg">` |

---

## File Paths Applied to Different HTML Elements

File paths are not just for images — they appear in many places. Let's look at the most common ones.

### 1. Images (`<img src="">`)

```html
<!-- Same folder -->
<img src="photo.jpg" alt="A photo">

<!-- Subfolder -->
<img src="images/banner.jpg" alt="Banner">

<!-- Root-relative -->
<img src="/images/logo.png" alt="Logo">

<!-- Up one level then into a folder -->
<img src="../images/profile.jpg" alt="Profile">

<!-- Absolute (from another website) -->
<img src="https://upload.wikimedia.org/wikipedia/commons/photo.jpg" alt="Wiki photo">
```

### 2. Page Links (`<a href="">`)

```html
<!-- Link to a page in the same folder -->
<a href="about.html">About Us</a>

<!-- Link to a page in a subfolder -->
<a href="pages/contact.html">Contact</a>

<!-- Link to a page one level up -->
<a href="../index.html">Back to Home</a>

<!-- Link to an external website (absolute) -->
<a href="https://www.google.com">Google</a>
```

### 3. CSS Stylesheets (`<link href="">`)

```html
<!-- Stylesheet in the same folder -->
<link rel="stylesheet" href="style.css">

<!-- Stylesheet in a css/ subfolder -->
<link rel="stylesheet" href="css/style.css">

<!-- Stylesheet at root -->
<link rel="stylesheet" href="/css/style.css">
```

### 4. JavaScript Files (`<script src="">`)

```html
<!-- Script in same folder -->
<script src="script.js"></script>

<!-- Script in a js/ subfolder -->
<script src="js/app.js"></script>

<!-- Script one level up -->
<script src="../js/utils.js"></script>
```

---

## Best Practice: Use Relative File Paths

> **Best practice: Always use relative file paths for files within your own website.**

Here is why this rule matters so much:

**Problem with absolute paths for your own files:**

```html
<!-- BAD: Absolute path to your own file -->
<img src="https://www.mywebsite.com/images/logo.png" alt="Logo">
```

If you do this throughout your site, several problems arise:
- When testing on your **local computer**, it doesn't work — the browser tries to fetch from the internet, not your local files.
- When you **move to a new domain**, every single path breaks.
- When the site is copied or archived, nothing loads.

**Relative path — the correct approach:**

```html
<!-- GOOD: Relative path -->
<img src="images/logo.png" alt="Logo">
```

With a relative path:
- It works on your **local computer** while testing.
- It works on **any server**, regardless of the domain name.
- It works if the **entire site is moved** to a new location.
- It works if the site is **archived or cloned**.

Think of it like this: relative paths are like saying "turn left at the corner" — those directions work whether you are in Lagos or London. Absolute paths are like saying "turn left at 14 Market Street, Lagos" — those directions only work in one specific city.

---

## Guided Practice Exercises

### Exercise 1 – Warm-Up: Identify the Path Type

Look at each file path below and decide: is it **absolute** or **relative**? What does it point to?

```
1.  https://www.bbc.com/images/logo.png
2.  images/photo.jpg
3.  ../index.html
4.  /css/style.css
5.  contact.html
6.  https://fonts.googleapis.com/css?family=Roboto
7.  ../../assets/banner.jpg
8.  js/app.js
```

**Answers:**
1. Absolute — full URL to BBC's logo on their server
2. Relative — `photo.jpg` inside an `images/` subfolder
3. Relative — `index.html` one folder level up
4. Relative (root-relative) — `style.css` in a `css/` folder at the website root
5. Relative — `contact.html` in the same folder
6. Absolute — full URL to a Google Fonts stylesheet
7. Relative — `banner.jpg` two folder levels up, inside `assets/`
8. Relative — `app.js` inside a `js/` subfolder

---

### Exercise 2 – Write the Correct File Path

Given the folder structure below, write the correct `src` or `href` attribute value for each instruction. Assume the current page is `about.html`.

**Folder Structure:**

```
school-website/
│
├── index.html
├── about.html             ← CURRENT PAGE
│
├── images/
│   ├── logo.png
│   ├── team.jpg
│   └── banner.jpg
│
├── css/
│   └── style.css
│
└── pages/
    └── contact.html
```

**Questions — write the path for each:**

1. Display `logo.png` from the `images/` folder
2. Display `banner.jpg` from the `images/` folder
3. Link to `contact.html` inside the `pages/` folder
4. Link to `index.html` (same folder as `about.html`)
5. Attach `style.css` from the `css/` folder

**Answers:**

```html
<!-- 1. -->
<img src="images/logo.png" alt="Logo">

<!-- 2. -->
<img src="images/banner.jpg" alt="Banner">

<!-- 3. -->
<a href="pages/contact.html">Contact</a>

<!-- 4. -->
<a href="index.html">Home</a>

<!-- 5. -->
<link rel="stylesheet" href="css/style.css">
```

**Why are all of these correct?** Because `about.html` is in the root of `school-website/`. All subfolders (`images/`, `css/`, `pages/`) are one level below it, so you simply write `foldername/filename`.

---

### Exercise 3 – Navigating Up with `../`

Now the current page has moved. Assume you are working inside `pages/contact.html`.

**Folder Structure:**

```
school-website/
│
├── index.html
├── about.html
│
├── images/
│   ├── logo.png
│   └── team.jpg
│
└── pages/
    └── contact.html      ← CURRENT PAGE
```

**Questions:**

1. Display `logo.png` from the `images/` folder (which is one level up)
2. Link back to `index.html` (one level up)
3. Link to `about.html` (one level up)
4. Display `team.jpg` from `images/` (one level up, then into `images/`)

**Answers:**

```html
<!-- 1. -->
<img src="../images/logo.png" alt="Logo">

<!-- 2. -->
<a href="../index.html">Home</a>

<!-- 3. -->
<a href="../about.html">About</a>

<!-- 4. -->
<img src="../images/team.jpg" alt="Team Photo">
```

**Step-by-step for answer 1:**
- `../` → go up from `pages/` to `school-website/`
- `images/` → go into the `images/` folder
- `logo.png` → find the file

---

### Exercise 4 – Build the Full HTML Page with Correct Paths

Using the folder structure from Exercise 3, write a complete `contact.html` page that:
- Has a heading "Contact Us"
- Displays the `logo.png` image at the top
- Has a link back to `index.html` labelled "Home"
- Has a link to `about.html` labelled "About"
- Attaches a stylesheet from `/css/style.css` (root-relative)

**Solution:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Contact Us</title>
  <!-- Root-relative path to stylesheet -->
  <link rel="stylesheet" href="/css/style.css">
</head>
<body>

  <!-- Logo: go up one level, then into images/ -->
  <img src="../images/logo.png" alt="School Logo">

  <h1>Contact Us</h1>
  <p>Reach us at: info@school.edu</p>

  <!-- Navigation: go up one level to find these pages -->
  <nav>
    <a href="../index.html">Home</a> |
    <a href="../about.html">About</a>
  </nav>

</body>
</html>
```

**Expected Output:** A page with the school logo at the top, a "Contact Us" heading, a contact email, and navigation links back to the home and about pages.

**Self-check questions:**
- Why do the image and link paths start with `../`?
- Why does the stylesheet use `/css/style.css` (root-relative) instead of `../css/style.css`? (Both would work — root-relative is more reliable across deeper nesting levels.)

---

## Mini Project – Build a Simple School Website Folder Structure

### Project Overview

You will create a small multi-page school website with a proper folder structure. This project pulls together everything from this lesson: same-folder paths, subfolder paths, parent-folder paths (`../`), and root-relative paths.

The project simulates how a real website is actually organised and shows you why correct file paths are essential.

---

### Stage 1 – Plan the Folder Structure

First, decide on the structure. Here is what you will build:

```
school-site/
│
├── index.html           ← Home page (root)
│
├── images/
│   ├── logo.png         ← (imagine this file exists)
│   ├── hero.jpg         ← (imagine this file exists)
│   └── science-lab.jpg  ← (imagine this file exists)
│
├── css/
│   └── style.css        ← Stylesheet
│
└── pages/
    ├── about.html       ← About page (inside subfolder)
    └── contact.html     ← Contact page (inside subfolder)
```

**Milestone:** Draw or write out this structure before writing any code. Understanding the structure first is the most important step.

---

### Stage 2 – Create the Stylesheet

**File:** `css/style.css`

```css
/* css/style.css */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  background-color: #f9f9f9;
  color: #333;
}

header {
  background-color: #003366;
  color: white;
  padding: 15px 20px;
  display: flex;
  align-items: center;
  gap: 15px;
}

header img {
  height: 50px;
}

header h1 {
  margin: 0;
  font-size: 22px;
}

nav {
  background-color: #0055aa;
  padding: 10px 20px;
}

nav a {
  color: white;
  text-decoration: none;
  margin-right: 20px;
  font-weight: bold;
}

nav a:hover {
  text-decoration: underline;
}

main {
  padding: 30px 20px;
}

.hero-image {
  width: 100%;
  max-width: 800px;
  border-radius: 6px;
  margin: 20px 0;
}

footer {
  background-color: #003366;
  color: white;
  text-align: center;
  padding: 15px;
  margin-top: 40px;
}
```

**Milestone Output:** The stylesheet is ready. No visual output yet — it will be applied when linked to HTML files.

---

### Stage 3 – Create the Home Page

**File:** `index.html` (in the root)

Since `index.html` is in the root folder, all paths are straightforward: subfolders are reached by going **down** (`images/`, `css/`, `pages/`).

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Greenfield Academy – Home</title>

  <!-- CSS is in the css/ subfolder — go down into it -->
  <link rel="stylesheet" href="css/style.css">
</head>
<body>

  <header>
    <!-- Logo is in images/ subfolder -->
    <img src="images/logo.png" alt="Greenfield Academy Logo">
    <h1>Greenfield Academy</h1>
  </header>

  <nav>
    <!-- These pages are in the same folder (index.html) or in pages/ -->
    <a href="index.html">Home</a>
    <a href="pages/about.html">About</a>
    <a href="pages/contact.html">Contact</a>
  </nav>

  <main>
    <h2>Welcome to Greenfield Academy</h2>
    <p>We are committed to nurturing the leaders of tomorrow through
       excellent education, science, and the arts.</p>

    <!-- Hero image in images/ subfolder -->
    <img src="images/hero.jpg" alt="Students in class" class="hero-image">

    <h3>Why Choose Us?</h3>
    <p>Our school offers world-class facilities, dedicated teachers,
       and a safe environment for every child to thrive.</p>
  </main>

  <footer>
    <p>&copy; 2025 Greenfield Academy. All rights reserved.</p>
  </footer>

</body>
</html>
```

**Milestone Output:** A styled home page with a navy header, navigation bar, hero image, and footer.

**Path analysis for `index.html`:**
- `css/style.css` → go into `css/` subfolder ✅
- `images/logo.png` → go into `images/` subfolder ✅
- `pages/about.html` → go into `pages/` subfolder ✅
- `images/hero.jpg` → go into `images/` subfolder ✅

---

### Stage 4 – Create the About Page

**File:** `pages/about.html` (inside the `pages/` subfolder)

Since this file is inside `pages/`, to reach files in the root or sibling folders (`images/`, `css/`), you must go **up one level** using `../`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Greenfield Academy – About</title>

  <!-- CSS is in ../css/ — go up one level, then into css/ -->
  <link rel="stylesheet" href="../css/style.css">
</head>
<body>

  <header>
    <!-- Logo: go up one level, then into images/ -->
    <img src="../images/logo.png" alt="Greenfield Academy Logo">
    <h1>Greenfield Academy</h1>
  </header>

  <nav>
    <!-- Home is one level up -->
    <a href="../index.html">Home</a>
    <!-- About is in the same folder (pages/) -->
    <a href="about.html">About</a>
    <!-- Contact is also in the same folder (pages/) -->
    <a href="contact.html">Contact</a>
  </nav>

  <main>
    <h2>About Our School</h2>
    <p>Founded in 1995, Greenfield Academy has educated over 10,000
       students across Lagos, Nigeria.</p>

    <!-- Science lab image: go up one level, then into images/ -->
    <img src="../images/science-lab.jpg" alt="Our science lab" class="hero-image">

    <h3>Our Mission</h3>
    <p>To provide every student with the tools, knowledge, and confidence
       they need to succeed in a rapidly changing world.</p>

    <h3>Our Values</h3>
    <p>Excellence, integrity, curiosity, and community are the four
       pillars that guide everything we do at Greenfield Academy.</p>
  </main>

  <footer>
    <p>&copy; 2025 Greenfield Academy. All rights reserved.</p>
  </footer>

</body>
</html>
```

**Milestone Output:** A styled About page matching the Home page layout, with correct navigation and images.

**Path analysis for `pages/about.html`:**
- `../css/style.css` → up to root, then into `css/` ✅
- `../images/logo.png` → up to root, then into `images/` ✅
- `../index.html` → up to root, find `index.html` ✅
- `about.html` → same folder (`pages/`) ✅
- `contact.html` → same folder (`pages/`) ✅
- `../images/science-lab.jpg` → up to root, then into `images/` ✅

---

### Stage 5 – Create the Contact Page

**File:** `pages/contact.html`

This page follows the same pattern as `about.html` since it is in the same `pages/` folder.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Greenfield Academy – Contact</title>

  <link rel="stylesheet" href="../css/style.css">
</head>
<body>

  <header>
    <img src="../images/logo.png" alt="Greenfield Academy Logo">
    <h1>Greenfield Academy</h1>
  </header>

  <nav>
    <a href="../index.html">Home</a>
    <a href="about.html">About</a>
    <a href="contact.html">Contact</a>
  </nav>

  <main>
    <h2>Contact Us</h2>
    <p>We would love to hear from you. Reach us through any of the
       channels below.</p>

    <h3>📍 Address</h3>
    <p>14 Academy Road, Lekki Phase 1, Lagos, Nigeria</p>

    <h3>📞 Phone</h3>
    <p>+234 801 234 5678</p>

    <h3>✉️ Email</h3>
    <p>info@greenfieldacademy.edu.ng</p>

    <h3>🕐 Office Hours</h3>
    <p>Monday – Friday: 8:00am – 4:00pm</p>
  </main>

  <footer>
    <p>&copy; 2025 Greenfield Academy. All rights reserved.</p>
  </footer>

</body>
</html>
```

**Final Project Output:**

A complete three-page school website where:
- All pages share the same header, navigation, and footer layout
- The CSS stylesheet is loaded correctly from `css/style.css` on every page
- The logo loads correctly from `images/logo.png` on every page
- Navigation links work correctly between all three pages
- Images on the about page load from the shared `images/` folder

**Reflection Questions:**
- Why do `about.html` and `contact.html` use `../` to reach the stylesheet but `index.html` does not?
- What would break if you used `images/logo.png` (without `../`) in `about.html`?
- How would you add a fourth page inside a new `blog/` subfolder? What would its paths look like?

**Optional Challenge:** Add a fourth page: `pages/gallery.html`. Include three images from the `images/` folder and a link back to all other pages.

---

## Common Beginner Mistakes

### Mistake 1 – Using Absolute Paths for Your Own Files

**Wrong:**

```html
<img src="https://www.mysite.com/images/logo.png" alt="Logo">
```

**Why it's wrong:** If you move to a new domain, change server, or test locally, all these paths break instantly.

**Correct:**

```html
<img src="images/logo.png" alt="Logo">
```

---

### Mistake 2 – Forgetting `../` When the File is Up One Level

**Wrong** (from `pages/about.html`):

```html
<img src="images/logo.png" alt="Logo">
```

**Why it's wrong:** The browser looks for an `images/` folder inside `pages/`, but it doesn't exist there. The image won't load.

**Correct:**

```html
<img src="../images/logo.png" alt="Logo">
```

---

### Mistake 3 – Using Backslashes Instead of Forward Slashes

**Wrong:**

```html
<img src="images\logo.png" alt="Logo">
```

**Why it's wrong:** Backslashes (`\`) are used in Windows file paths on your computer, but HTML **always** uses forward slashes (`/`). Using backslashes will cause the file not to load in the browser.

**Correct:**

```html
<img src="images/logo.png" alt="Logo">
```

---

### Mistake 4 – Wrong Capitalisation in File Names

**Wrong:**

```html
<img src="images/Logo.png" alt="Logo">
```

**Why it's wrong (on most servers):** Web servers — especially Linux-based ones — are **case sensitive**. If the file is named `logo.png` (lowercase) but you write `Logo.png` (capital L), the server cannot find it and the image won't load. This often works on Windows (which is not case sensitive) but breaks when the site is deployed to a Linux server.

**Correct:**

```html
<img src="images/logo.png" alt="Logo">
```

**Best practice:** Always use **lowercase** for all file and folder names in your website to avoid this problem entirely.

---

### Mistake 5 – Missing the File Extension

**Wrong:**

```html
<img src="images/logo" alt="Logo">
```

**Why it's wrong:** The browser needs the full filename including its extension (`.png`, `.jpg`, `.css`, `.html`) to know what type of file it is and where to find it.

**Correct:**

```html
<img src="images/logo.png" alt="Logo">
```

---

### Mistake 6 – Using Spaces in File or Folder Names

**Wrong:**

```html
<img src="my images/team photo.jpg" alt="Team">
```

**Why it's wrong:** Spaces in URLs and file paths cause broken links. Browsers may encode spaces as `%20`, which can be confusing and error-prone.

**Correct:**

```html
<img src="my-images/team-photo.jpg" alt="Team">
```

Use **hyphens** (`-`) or **underscores** (`_`) instead of spaces in all file and folder names.

---

### Mistake 7 – Confusing `/` (Root-relative) with `./` (Current folder)

**Confusing to beginners:**

- `/images/logo.png` → starts from the **root** of the website
- `./images/logo.png` → starts from the **current folder** (the `./` is optional and means "here")
- `images/logo.png` → same as `./images/logo.png` — also the current folder

All three work when you are in the root folder. The difference matters when you are inside a subfolder. `/images/logo.png` always goes to the root's `images/` folder no matter where you are, while `images/logo.png` looks for an `images/` folder in the current folder.

---

## Reflection Questions

Think through these questions carefully before moving on:

1. What is a file path? Why does a browser need one?
2. What is the difference between an absolute file path and a relative file path?
3. When should you use an absolute file path? Give a real-world example.
4. Why is it best practice to use relative file paths for your own website's files?
5. If your current page is `pages/blog/post.html` and you want to load `images/photo.jpg` from the root, what would the path be?
6. What does `../` mean in a file path? What does `../../` mean?
7. A friend says their image works when testing on their laptop but breaks when they upload the site to a server. What is the most likely mistake they made?
8. What is wrong with a path like `images\banner.jpg`?
9. Why is it recommended to use lowercase letters for all file and folder names?
10. What path would you use to link to `contact.html` from a page in the same folder? What path would you use to link to `contact.html` if it is inside a `pages/` subfolder?

---

## Completion Checklist

Before moving on to Lesson 24, confirm you can do all of the following:

- [ ] I can explain what a file path is in simple language
- [ ] I understand what an absolute file path is and when to use it
- [ ] I can write a relative path to a file in the same folder
- [ ] I can write a relative path to a file in a subfolder (`folder/file.ext`)
- [ ] I can write a root-relative path starting with `/`
- [ ] I can write a relative path using `../` to go one level up
- [ ] I can chain paths: `../images/photo.jpg` means go up then into a folder
- [ ] I understand why relative paths are best practice
- [ ] I know that HTML uses forward slashes `/`, not backslashes `\`
- [ ] I completed at least two of the guided practice exercises
- [ ] I understand the common mistakes and how to avoid them
- [ ] I completed the mini-project (or fully understood each stage)

---

## Lesson Summary

A **file path** tells the browser where to find a file — whether that is an image, another HTML page, a stylesheet, or a JavaScript file. It appears as the value inside attributes like `src`, `href`, and so on.

There are two types of file paths. An **absolute file path** is the full URL, starting with `https://`. It is used to link to files on external websites. A **relative file path** describes the location of a file relative to where the current HTML page lives.

Relative paths use three key patterns: writing just the filename (same folder), writing `foldername/filename` (going into a subfolder), and writing `../filename` (going up one folder level). You can chain these patterns — for example, `../../images/photo.jpg` means go up two levels, then into `images/`.

The most important rule to remember is: **always use relative file paths for files within your own website.** This keeps your site portable, testable, and future-proof — it will work on your local machine, on any server, and under any domain name.

Other important habits: always use forward slashes `/`, always include the file extension, always use lowercase filenames, and never put spaces in file or folder names.

---

*End of Lesson 23 – HTML File Paths*
