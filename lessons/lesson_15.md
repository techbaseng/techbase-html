---
render_with_liquid: false
title: "HTML Favicon and Page Title"
nav_order: 15
---

# Lesson 15: HTML Favicon and Page Title

---

## Lesson Introduction

Have you ever noticed that tiny little picture sitting to the left of a website's name in your browser tab? That small icon is called a **favicon**. And right next to it — or on its own — is the **page title**, the text that tells you (and the browser) what the page is about.

In this lesson, you will learn:
- What a **favicon** is, why it exists, and how to add one to your webpage
- What a **page title** is, why it matters, and how to write a good one
- How both of these work together to make your website look professional and findable
- How to use the `<link>` tag and the `<title>` tag inside the `<head>` section

Think of it like this: when someone opens many tabs in their browser, your favicon and page title are the only clues that help them find YOUR tab quickly. They're like a name tag and a photo for your webpage!

> **Real-World Relevance:** Every professional website — from Google to Amazon — uses a favicon and a carefully written page title. A good page title also helps your website rank higher in search engines like Google. This lesson teaches two small but powerful details that make a huge difference.

---

## Prerequisite Concepts

Before we dive in, let's make sure you understand a few things that this lesson builds on. Don't worry — we'll explain each one simply.

### What is the `<head>` Section?

Every HTML page has two main sections: the `<head>` and the `<body>`.

- The **`<body>`** is where everything the visitor *sees* on the page goes — text, images, buttons, etc.
- The **`<head>`** is where invisible *instructions about the page* go — things the browser needs to know but that the visitor doesn't directly see on the page content.

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- Instructions about the page go here -->
  </head>
  <body>
    <!-- The visible page content goes here -->
  </body>
</html>
```

Both the favicon and the page title live inside the `<head>` section.

### What is a File Path?

A **file path** is the address of a file on your computer or server. Think of it like a street address for a file.

- `/images/favicon.ico` means: go to the root of the website, find a folder called `images`, and inside it find the file `favicon.ico`.
- `favicon.ico` (no slash) means: look for the file in the same folder as the HTML file.

We'll use file paths when we link to our favicon image.

### What is a `<link>` Tag?

The `<link>` tag is used inside `<head>` to connect your HTML page to an external resource — like a stylesheet, an icon, or a font. It is a **self-closing tag**, meaning it does not have a separate closing tag.

```html
<link rel="stylesheet" href="style.css">
```

- `rel` — tells the browser the *relationship* between the page and the linked file
- `href` — gives the *address* (path) of the file to link to
- `type` — tells the browser the *file type* of the linked resource

---

## Part 1: HTML Favicon

### What Is a Favicon?

**Favicon** stands for **"Favourites Icon"** (also called a "tab icon" or "browser icon"). It is a **small image** that appears:

- In the **browser tab**, to the left of the page title
- In the **bookmarks bar** when you save a page
- In your **browser history**
- On the **home screen** of a phone if someone saves your site

Think of it like this: if your webpage were a shop, the favicon would be your shop's logo on the front door. It's the first tiny visual thing people use to recognise your page at a glance.

**Without a favicon:**
```
[ My Page Title ]
```
*(Just plain text in the tab — looks unfinished)*

**With a favicon:**
```
[ 🌐 My Page Title ]
```
*(A small icon appears before the title — looks professional)*

### Why Does a Favicon Exist?

People often have 10, 15, or even 30 tabs open at the same time. When tabs are too many, the page title gets cut short and becomes unreadable. The favicon becomes the only visible thing in a tab. A good favicon helps users find YOUR tab instantly without reading any text.

> **Think About This:** Open 20 browser tabs right now. How many of them can you identify just by their favicon without reading the title? Most of them, right? That's the power of the favicon!

### What Image Can You Use as a Favicon?

You can use almost any image. However, because favicons are displayed **very small** (usually 16×16 pixels or 32×32 pixels), the image should:

- Be **simple** with clear shapes (not too detailed)
- Have **high contrast** (colours that stand out against the browser tab background)
- Be square in shape (equal width and height)

You can create your own favicon for free at websites like [https://www.favicon.cc](https://www.favicon.cc).

### What File Formats Are Supported?

Favicons support multiple image formats. Here is a summary of browser support:

| Format | Edge | Chrome | Firefox | Opera | Safari |
|--------|------|--------|---------|-------|--------|
| `.ico` | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| `.png` | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| `.gif` | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| `.jpeg` | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| `.svg` | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |

All major modern browsers support all five formats! The most traditional and universally compatible format is `.ico`, which is why most developers still name their favicon file `favicon.ico`. However, `.png` is also very popular and works perfectly in all modern browsers.

### Where Do You Save the Favicon File?

You should save your favicon image either:
1. In the **root directory** of your website (the main/top-level folder), OR
2. In an **`images` folder** inside the root directory

The most common setup looks like this:

```
my-website/
│
├── index.html         ← Your HTML file
├── favicon.ico        ← Favicon in root folder (Option 1)
│
└── images/
    └── favicon.ico    ← Favicon in images folder (Option 2)
```

A very common and professional file name for the favicon is `favicon.ico`.

### How to Add a Favicon — The `<link>` Tag

To add a favicon to your page, you place a `<link>` tag inside the `<head>` section, **after the `<title>` tag**.

**Basic Syntax:**
```html
<link rel="icon" type="image/x-icon" href="/images/favicon.ico">
```

Let's break this down **word by word**:

| Part | What it means |
|------|---------------|
| `<link` | Start of the link tag |
| `rel="icon"` | **rel** = relationship. We're telling the browser: "This file is an *icon* for this page." |
| `type="image/x-icon"` | **type** = the kind of file. `image/x-icon` is the MIME type for `.ico` files. Think of it like telling the browser: "This is an icon image." |
| `href="/images/favicon.ico"` | **href** = the file path/address of the favicon image. The `/` at the start means "start from the root of the website." |
| `>` | End of the self-closing tag |

> **What is a MIME type?** A MIME type is like a label on a box that tells the browser what kind of content is inside. `image/x-icon` means "this is an image of the icon type." For PNG files, you would use `image/png`.

### Your First Favicon Example

**Example 1 — Favicon stored in an `images` folder:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Page Title</title>
  <link rel="icon" type="image/x-icon" href="/images/favicon.ico">
</head>
<body>

  <h1>This is a Heading</h1>
  <p>This is a paragraph.</p>

</body>
</html>
```

**What Happens:**
- The browser reads the `<head>` section
- It finds the `<link>` tag and follows the `href` path to `/images/favicon.ico`
- It loads that small image and displays it in the browser tab, to the left of "My Page Title"

**Expected Visual Output in the Browser Tab:**
```
[ 🖼️ My Page Title  |  ×  ]
```
*(A small favicon image appears before the title text in the tab)*

> **Thinking Prompt:** What do you think would happen if you typed the wrong file path in `href`? Try changing `/images/favicon.ico` to `/images/wrongname.ico` and observe. The favicon simply won't appear — no crash, no error visible to the user, just a missing icon.

### Example 2 — Using a PNG Favicon

If your favicon is a `.png` file instead of `.ico`, you change the `type` attribute accordingly:

```html
<link rel="icon" type="image/png" href="/images/favicon.png">
```

| File Type | `type` Attribute Value |
|-----------|------------------------|
| `.ico` | `type="image/x-icon"` |
| `.png` | `type="image/png"` |
| `.gif` | `type="image/gif"` |
| `.jpeg` | `type="image/jpeg"` |
| `.svg` | `type="image/svg+xml"` |

### Example 3 — Favicon in the Root Folder (No Subfolder)

If you save your favicon directly in the same folder as your `index.html` file (no `images` subfolder), the path is simply:

```html
<link rel="icon" type="image/x-icon" href="favicon.ico">
```

Notice there is **no `/` at the start** and **no folder name** — just the filename. This tells the browser: "Look for `favicon.ico` in the same place as this HTML file."

### Full Working Example with Favicon

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Awesome Website</title>
  <link rel="icon" type="image/x-icon" href="/images/favicon.ico">
</head>
<body>

  <h1>Welcome to My Website!</h1>
  <p>This page has a favicon in the browser tab.</p>

</body>
</html>
```

**Expected Tab Output:**
```
[ 🏠 My Awesome Website ]
```
*(Your favicon icon appears to the left of the title in the tab)*

---

## Part 2: HTML Page Title

### What Is a Page Title?

The **page title** is the text you write inside the `<title>` tag in your HTML `<head>`. It is NOT the heading visible on the webpage itself — it is the text shown:

1. In the **browser tab** (at the top of the browser window)
2. In the **bookmarks bar** when someone saves your page as a bookmark
3. In **Google search results** as the clickable blue headline
4. In the **browser history** list
5. When someone **shares** your page link on social media (it often shows the title)

> **Analogy:** The page title is like the label on a folder in a filing cabinet. Even though you can't see the label when the folder is open, you need it to find and identify the folder quickly.

### How to Add a Page Title — The `<title>` Tag

The `<title>` tag goes inside the `<head>` section:

```html
<title>Your Page Title Here</title>
```

Let's look at a simple example:

**Example 1 — Basic page title:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>HTML Tutorial</title>
</head>
<body>
  The content of the document......
</body>
</html>
```

**What the Browser Shows:**
- In the tab: `HTML Tutorial`
- In the title bar (top of the browser window): `HTML Tutorial`

**Example 2 — A more descriptive page title:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Learn HTML for Beginners - Free Tutorial</title>
</head>
<body>
  <h1>Welcome to the HTML Tutorial</h1>
  <p>This is where you learn HTML.</p>
</body>
</html>
```

**Browser Tab Output:**
```
[ Learn HTML for Beginners - Free Tutorial ]
```

Notice how the `<h1>` heading inside `<body>` says "Welcome to the HTML Tutorial" — that's what visitors see ON the page. But the `<title>` says "Learn HTML for Beginners - Free Tutorial" — that's what appears IN the tab and in search results. They don't have to be identical, but they should both accurately describe the page.

> **Thinking Prompt:** Why might you want the page title and the `<h1>` heading to be slightly different? Think about search results. In Google, you see the title in blue — it needs to be appealing to click. On the page itself, the heading can be more welcoming. They serve different audiences at different moments.

### What Makes a Good Page Title?

Every web page should have a page title that **describes the content and meaning of the page**. Here is what to keep in mind:

**The page title is important for SEO (Search Engine Optimisation).** SEO is the practice of making your website easier for search engines like Google to find and rank. Search engine algorithms use the text in your `<title>` tag to decide:
- What your page is about
- How relevant it is to a user's search query
- Where to rank it in search results

**The `<title>` element:**
- Defines the title shown in the browser toolbar/tab
- Provides a title for the page when it is saved to browser favourites/bookmarks
- Displays the title for the page in search engine result pages (SERPs)

**Good page title examples:**

| Scenario | Good Page Title |
|----------|----------------|
| A recipe page | `Chocolate Chip Cookies Recipe - Easy 30-Minute Bake` |
| A business homepage | `Lagos Plumbing Services - Fast & Affordable Repairs` |
| A blog post | `How to Learn Python in 30 Days - Beginner's Guide` |
| A product page | `Sony WH-1000XM5 Wireless Headphones - Best Price` |

**Bad page title examples (avoid these):**

| Bad Example | Why It's Bad |
|-------------|-------------|
| `Page 1` | Tells nobody anything about the page |
| `Untitled Document` | Default title — tells search engines you didn't care |
| (empty — no title tag) | Very bad for SEO; browser just shows the URL |
| `Home` | Too vague — every website has a "Home" page |
| `asdfghjkl` | Makes no sense; hurts search rankings |

> **Try to make the title as accurate and meaningful as possible!**

### Example 3 — Comparing a Page Title vs a Page Heading

This is very important — beginners often confuse the `<title>` tag with the `<h1>` tag. They are completely different things:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Free Python Courses Online - LearnCode.com</title>  <!-- Page Title: shown in tab & search results -->
</head>
<body>
  <h1>Welcome to Our Free Python Learning Centre!</h1>  <!-- Page Heading: shown ON the page -->
  <p>Start learning Python today with our beginner-friendly lessons.</p>
</body>
</html>
```

**What the Visitor Sees:**
- In the browser tab: `Free Python Courses Online - LearnCode.com`
- On the actual webpage: `Welcome to Our Free Python Learning Centre!`

Both describe the same page but from different angles — the title is optimised for search engines and bookmarks, while the heading is written to welcome visitors warmly.

---

## Part 3: Combining Favicon and Page Title Together

Now let's put both concepts together in one complete, professional-looking HTML page:

### Full Example — Favicon + Page Title + Content

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Portfolio - Web Developer</title>
  <link rel="icon" type="image/x-icon" href="/images/favicon.ico">
</head>
<body>

  <h1>Welcome to My Portfolio</h1>
  <p>Hello! I am a web developer based in Lagos, Nigeria.</p>
  <p>Browse my projects below.</p>

</body>
</html>
```

**What Happens When You Open This Page:**
1. The browser reads the `<head>` section first
2. It sets the tab title to: `My Portfolio - Web Developer`
3. It loads the favicon from `/images/favicon.ico` and shows it in the tab
4. It renders the `<body>` content — the heading and paragraphs — in the main page area

**Expected Tab Appearance:**
```
[ 🖼️ My Portfolio - Web Developer ]
```

> **Note:** The `<link>` tag always goes AFTER the `<title>` tag. This is the standard convention followed by professional developers.

---

## Guided Practice Exercises

### Exercise 1 — Your First Favicon

**Objective:** Add a favicon to a simple webpage.

**Scenario:** You are building a basic website for a school project. You want it to look professional with a favicon in the tab.

**Steps:**
1. Create a new file called `index.html`
2. Write the basic HTML structure (`<!DOCTYPE html>`, `<html>`, `<head>`, `<body>`)
3. Add a `<title>` tag inside `<head>` with the text: `My School Project`
4. Add a `<link>` tag to link a favicon called `favicon.ico` stored in an `images` folder
5. Add a heading `<h1>` and a paragraph `<p>` inside `<body>`

**Your Code Should Look Like This:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>My School Project</title>
  <link rel="icon" type="image/x-icon" href="/images/favicon.ico">
</head>
<body>

  <h1>Science Fair 2025</h1>
  <p>This project explores the effect of sunlight on plant growth.</p>

</body>
</html>
```

**Expected Output:**
- Browser tab shows: `[ 🖼️ My School Project ]`
- Page displays: `Science Fair 2025` as a large heading and the paragraph below it

**Self-Check Questions:**
- Did you put the `<link>` tag inside `<head>`, not inside `<body>`?
- Does your `href` path point to the correct folder and filename?
- Is your `rel` attribute set to `"icon"`?

---

### Exercise 2 — Write Better Page Titles

**Objective:** Practise writing meaningful page titles for different scenarios.

**Scenario:** Below are five webpages with poor titles. Rewrite each one to be better.

| Poor Title | Improved Title (your answer) |
|------------|------------------------------|
| `Page1` | ??? |
| `Untitled` | ??? |
| `Home` | ??? |
| `Products` | ??? |
| `Blog` | ??? |

**Sample Improved Answers:**

| Poor Title | Improved Title |
|------------|----------------|
| `Page1` | `Getting Started with HTML - Beginner's Guide` |
| `Untitled` | `Adaeze's Photography Portfolio - Lagos, Nigeria` |
| `Home` | `TechFix Repairs - Fast & Affordable Phone Repairs` |
| `Products` | `Handmade African Jewellery - Shop Unique Pieces` |
| `Blog` | `Coding Tips for Beginners - Weekly Articles` |

**Self-Check Questions:**
- Does each improved title describe what the page is specifically about?
- Would someone clicking the title in a Google search feel they are on the right page?
- Is the title between 50–60 characters long? (This is the ideal length for Google search results.)

---

### Exercise 3 — Combining Favicon and Page Title

**Objective:** Build a complete webpage with both a favicon and a meaningful title.

**Scenario:** You are creating a simple homepage for a fictional bakery called "Sunshine Bakery" in Abuja, Nigeria. The bakery sells fresh bread and pastries. You have a PNG file called `cake-icon.png` saved in a folder called `assets`.

**Steps:**
1. Write the full HTML boilerplate
2. Add a meaningful `<title>` tag
3. Add a `<link>` tag for the favicon using the correct path and type
4. Add a welcoming heading and description in the body

**Your Solution:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Sunshine Bakery Abuja - Fresh Bread & Pastries Daily</title>
  <link rel="icon" type="image/png" href="/assets/cake-icon.png">
</head>
<body>

  <h1>Welcome to Sunshine Bakery</h1>
  <p>We bake fresh bread, cakes, and pastries every morning in Abuja.</p>
  <p>Come visit us at 14 Wuse Market Road, Abuja.</p>

</body>
</html>
```

**Expected Tab Output:**
```
[ 🎂 Sunshine Bakery Abuja - Fresh Bread & Pastries Daily ]
```

**What-If Challenge:** What would you change if the favicon file were a `.svg` file called `logo.svg` stored in the root folder (not in any subfolder)?

```html
<!-- Answer: -->
<link rel="icon" type="image/svg+xml" href="logo.svg">
```

---

## Mini Project: Build a Multi-Page Personal Website Foundation

In this project, you will build two connected HTML pages. Each page will have its own **unique favicon and page title**, showing how professional websites identify each page separately.

### Project Overview

You are building a basic personal website with:
- **Page 1:** `index.html` — The Home page
- **Page 2:** `about.html` — The About Me page

Both pages should look connected and professional.

---

### Stage 1: Setup — Create Your Folder Structure

Your project folder should look like this:

```
my-website/
│
├── index.html
├── about.html
│
└── images/
    └── favicon.ico
```

Create this folder structure on your computer. You can download a free favicon from [https://www.favicon.cc](https://www.favicon.cc) or create a simple one.

---

### Stage 2: Build the Home Page (`index.html`)

```html
<!DOCTYPE html>
<html>
<head>
  <title>Chidi Obi - Web Developer Portfolio</title>
  <link rel="icon" type="image/x-icon" href="/images/favicon.ico">
</head>
<body>

  <h1>Hi, I'm Chidi Obi</h1>
  <p>I am a beginner web developer learning HTML and CSS.</p>
  <p>Welcome to my personal portfolio website.</p>
  <p><a href="about.html">Learn more about me →</a></p>

</body>
</html>
```

**Milestone Output:**
- Tab shows: `[ 🖼️ Chidi Obi - Web Developer Portfolio ]`
- Page shows heading and intro text
- A link to the About page works

---

### Stage 3: Build the About Page (`about.html`)

Notice this page has a **different title** — it identifies itself clearly:

```html
<!DOCTYPE html>
<html>
<head>
  <title>About Chidi Obi - Background & Skills</title>
  <link rel="icon" type="image/x-icon" href="/images/favicon.ico">
</head>
<body>

  <h1>About Me</h1>
  <p>My name is Chidi Obi. I am 19 years old and based in Lagos, Nigeria.</p>
  <p>I started learning web development 3 months ago. I love building things on the web.</p>

  <h2>My Skills</h2>
  <p>HTML, CSS (learning), JavaScript (soon!)</p>

  <p><a href="index.html">← Back to Home</a></p>

</body>
</html>
```

**Milestone Output:**
- Tab shows: `[ 🖼️ About Chidi Obi - Background & Skills ]`
- Page shows personal information and skills
- A link back to the home page works

---

### Stage 4: Enhancement — Different Titles, Same Favicon

Now you have two pages where:
- Both pages share the **same favicon** (`/images/favicon.ico`) — just like a real website where all pages show the company logo
- Each page has a **different, specific title** that accurately describes its content

This is exactly how professional websites work. For example:
- Wikipedia home: `Wikipedia, the free encyclopedia`
- Wikipedia article: `Nigeria - Wikipedia`
- Wikipedia another article: `HTML - Wikipedia`

Same look, same favicon, unique titles per page!

---

### Stage 5: Reflection Questions

1. If you open both pages in two different tabs, can you tell which tab is which just from the title (without even looking at the favicon)?
2. Why is it a bad idea to give all pages of your website the same title?
3. If Google searches show your title to potential visitors, what would make someone more likely to click on your page?
4. What would happen if you forgot to add the `<link>` tag but the favicon file exists on the server?
5. Optional: What if the favicon file is very large (e.g., a 5MB photo)? Would that cause any problems?

---

## Common Beginner Mistakes

### Mistake 1 — Putting `<link>` or `<title>` in `<body>` Instead of `<head>`

**Wrong:**
```html
<!DOCTYPE html>
<html>
<head>
  <!-- Empty head! -->
</head>
<body>
  <title>My Page</title>               <!-- ❌ WRONG — title is in body -->
  <link rel="icon" href="favicon.ico"> <!-- ❌ WRONG — link is in body -->
  <h1>Hello World</h1>
</body>
</html>
```

**Correct:**
```html
<!DOCTYPE html>
<html>
<head>
  <title>My Page</title>               <!-- ✅ CORRECT — title is in head -->
  <link rel="icon" type="image/x-icon" href="/images/favicon.ico"> <!-- ✅ CORRECT -->
</head>
<body>
  <h1>Hello World</h1>
</body>
</html>
```

**Why it matters:** Although browsers might sometimes partially forgive misplaced tags, putting metadata outside `<head>` is invalid HTML and can cause unpredictable behaviour in different browsers.

---

### Mistake 2 — Wrong File Path for the Favicon

**Wrong:**
```html
<link rel="icon" type="image/x-icon" href="images/favicon.ico">
<!-- ❌ If your HTML file is not in the root, this path may be wrong -->
```

**Correct (absolute path from root):**
```html
<link rel="icon" type="image/x-icon" href="/images/favicon.ico">
<!-- ✅ The leading / means: start from the root of the website -->
```

**Why it matters:** If the path is wrong, the browser cannot find the favicon file. It will simply display no favicon icon (or the browser's default icon). No error will be shown to the user, making this a sneaky bug.

---

### Mistake 3 — Using the Wrong `type` for the File Format

**Wrong:**
```html
<link rel="icon" type="image/x-icon" href="/images/favicon.png">
<!-- ❌ The file is .png but the type says x-icon (for .ico files) -->
```

**Correct:**
```html
<link rel="icon" type="image/png" href="/images/favicon.png">
<!-- ✅ The type matches the actual file format -->
```

**Why it matters:** Some browsers may not display the favicon correctly if the `type` doesn't match the actual file format.

---

### Mistake 4 — Leaving the `<title>` Tag Empty

**Wrong:**
```html
<title></title>  <!-- ❌ Empty title -->
```

**Correct:**
```html
<title>My Awesome Page - Learn Something New Today</title>  <!-- ✅ Meaningful title -->
```

**Why it matters:** An empty title means your page appears blank in browser tabs, search results show nothing, and search engines don't know what your page is about — hurting your SEO ranking severely.

---

### Mistake 5 — Confusing `<title>` with `<h1>`

**Wrong Understanding:**
```
"I already have a big heading on my page, so I don't need a <title> tag."
```

**Correct Understanding:**
- `<h1>` is the **visible heading** on the page — it's what the visitor reads
- `<title>` is the **invisible tab/bookmark/search label** — it's what the browser and search engines read
- Both are needed, and both should describe your page (but they can be worded differently)

---

### Mistake 6 — Using a Complex or Blurry Image as a Favicon

**Wrong:**
Using a detailed photograph or a complex logo as a favicon. At 16×16 pixels, it becomes an unrecognisable blur.

**Correct:**
Use a simple icon — a single letter, a symbol, a simple shape — with strong contrast. Favicon generators like [favicon.cc](https://www.favicon.cc) help you design icons specifically for this tiny size.

---

## Reflection Questions

Think about these questions to test and deepen your understanding:

1. You visit a website and see a small coffee cup icon in the browser tab before the page title. What is that icon called, and what HTML tag produces it?

2. You search "learn HTML" on Google and see several results with blue clickable titles. What HTML tag inside the webpage's `<head>` section produces those titles?

3. What is the difference between `href="favicon.ico"` and `href="/favicon.ico"`? When would you use each?

4. A developer creates 10 pages on their website but gives all of them the exact same `<title>`: "Welcome". What problems might this cause for visitors and search engines?

5. Why should a favicon be a simple image with high contrast rather than a detailed photograph?

6. If you use a `.png` file as your favicon instead of a `.ico` file, what needs to change in your `<link>` tag?

7. Where in an HTML file must both the `<title>` tag and the favicon `<link>` tag be placed?

8. Write out from memory the complete `<link>` tag for a favicon called `logo.svg` stored in a folder called `icons`. The favicon format is SVG.

---

## Completion Checklist

Use this checklist to make sure you have fully understood and practised this lesson:

- [ ] I understand what a favicon is and where it appears in the browser
- [ ] I know why favicons should be simple, high-contrast images
- [ ] I can correctly write the `<link>` tag to add a favicon using `.ico`, `.png`, `.gif`, `.jpeg`, and `.svg` formats
- [ ] I understand what the `rel`, `type`, and `href` attributes do in the `<link>` tag
- [ ] I know that the favicon `<link>` tag goes inside `<head>`, after the `<title>` tag
- [ ] I understand what the `<title>` tag does and where it appears (tab, bookmarks, search results)
- [ ] I know the difference between `<title>` (invisible metadata) and `<h1>` (visible heading)
- [ ] I understand why a good page title matters for SEO
- [ ] I can write a meaningful, descriptive page title for different types of web pages
- [ ] I completed Exercise 1 (adding a favicon), Exercise 2 (improving titles), and Exercise 3 (combining both)
- [ ] I completed the mini project with two connected pages, each with correct favicon and page title
- [ ] I understand and can avoid all six common beginner mistakes listed in this lesson

---

## Lesson Summary

In this lesson, you learned two small but very powerful tools that make a website look and behave professionally:

**Favicon (`<link rel="icon" ...>`):**
- A favicon is a tiny image displayed in browser tabs, bookmarks, and history
- It goes inside `<head>` using a `<link>` tag placed after `<title>`
- You must match the `type` attribute to the image file format (`.ico` → `image/x-icon`, `.png` → `image/png`, etc.)
- The `href` attribute holds the file path to the favicon image
- The image should be simple and high-contrast since it is displayed very small
- All major browsers support `.ico`, `.png`, `.gif`, `.jpeg`, and `.svg` favicons

**Page Title (`<title>`):**
- The page title is defined using the `<title>` tag inside `<head>`
- It is NOT visible on the page itself — it appears in the browser tab, bookmarks, and search engine results
- It is very important for SEO (Search Engine Optimisation)
- A good title describes the page content accurately and meaningfully
- Each page on a website should have its own unique, specific title
- Never leave the `<title>` tag empty or use meaningless titles like "Page 1" or "Untitled"

**Both together:**
- A favicon and a well-written page title are among the first things a browser reads about your webpage
- They work together to make your site identifiable, professional, and searchable
- Every serious, professional website uses both — and now you know exactly how to add them too!

---

### Quick Reference Card

```html
<!DOCTYPE html>
<html>
<head>
  <!-- Page Title: shown in tab, bookmarks, and search results -->
  <title>Your Meaningful Page Title Here</title>

  <!-- Favicon: small icon shown in browser tab -->
  <link rel="icon" type="image/x-icon" href="/images/favicon.ico">
</head>
<body>
  <!-- Your visible page content goes here -->
</body>
</html>
```

### HTML Tags Covered in This Lesson

| Tag | Description |
|-----|-------------|
| `<title>` | Defines the title of the document (shown in tab, bookmarks, search results) |
| `<link>` | Links an external resource to the document (used here for the favicon) |

**Key `<link>` Attributes for Favicons:**

| Attribute | Value | Purpose |
|-----------|-------|---------|
| `rel` | `"icon"` | Tells the browser this is a page icon |
| `type` | `"image/x-icon"` / `"image/png"` etc. | Specifies the file format of the icon |
| `href` | `/images/favicon.ico` | The file path to the favicon image |
