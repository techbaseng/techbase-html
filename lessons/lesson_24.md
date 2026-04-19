---
render_with_liquid: false
title: "The HTML Head — Metadata, Titles, Styles, Links, Scripts & More"
nav_order: 24
---

# Lesson 24: The HTML `<head>` Element — The Brain Behind Every Web Page

---

## Lesson Introduction

Have you ever noticed that when you open a website, the browser tab shows a
title like **"My Portfolio"** or **"Login – Google Accounts"**? Or that your
phone displays a website differently from a desktop computer? Or that Google
can describe a page in search results without reading its full content?

All of those things happen because of information hidden inside the **`<head>`
section** of an HTML document — code that the browser reads and uses, but that
visitors never see directly on the page.

In this lesson you will learn:

- What the `<head>` element is and why every page needs one
- Every element that belongs inside `<head>` and what each one does
- How to set a page title, add styles, link external CSS, define metadata, add
  a viewport setting, include JavaScript, and configure a base URL
- Real-world reasons each element matters
- Guided practice exercises
- A complete mini-project combining everything

By the end of this lesson you will be able to write a complete, professional
`<head>` section for any HTML page from scratch.

---

## Prerequisite Concepts

Before we dive in, make sure you are comfortable with the following ideas.
If any of them sound new, read the short explanation provided before moving on.

### What is an HTML Document?

An HTML document is a text file that a browser reads and turns into a visible
web page. It always has a structure like this:

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- Invisible setup information lives here -->
  </head>
  <body>
    <!-- Visible page content lives here -->
  </body>
</html>
```

- `<!DOCTYPE html>` — tells the browser this is a modern HTML5 document.
- `<html>` — the root (outermost) tag; everything lives inside it.
- `<head>` — the invisible setup zone. The browser reads it but does not
  display it on the page.
- `<body>` — everything here is rendered visibly on the page.

### What is a Tag?

A tag is a keyword wrapped in angle brackets, like `<title>`. Most tags come
in pairs: an opening tag `<title>` and a closing tag `</title>`. Content
goes in between.

### What is Metadata?

**Metadata** means *data about data*. On a web page, metadata is information
*about* the page itself rather than the content you can see. Examples: the
page's title, its author, its description for Google, what character encoding
it uses.

> 💡 **Analogy:** Think of a book. The chapters you read are the `<body>`.
> The cover, copyright page, and ISBN number are the `<head>` — they describe
> the book without being a chapter you read.

---

## Conceptual Understanding

### What Is the `<head>` Element?

The `<head>` element is a **container** for metadata and setup instructions.
It sits between the `<html>` tag and the `<body>` tag. The browser reads
everything inside `<head>` to learn how to set up the page — but it does **not**
display any of that content on screen.

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- All setup information goes here -->
  </head>
  <body>
    <p>Visible text goes here.</p>
  </body>
</html>
```

**What can live inside `<head>`?**

The six elements that belong inside `<head>` are:

| Element | Purpose |
|---|---|
| `<title>` | Sets the browser tab/window title |
| `<style>` | Adds CSS styling directly in the page |
| `<link>` | Links to an external CSS file (or other resource) |
| `<meta>` | Provides metadata: charset, keywords, description, viewport |
| `<script>` | Adds JavaScript code or links to a JS file |
| `<base>` | Sets a default URL/target for all links on the page |

We will study each one in depth below.

---

## Element 1 — `<title>`: The Browser Tab Title

### What is it?

The `<title>` element defines the **title of the HTML document**. It must
contain plain text only — no HTML tags inside it.

### Why does it matter?

- It appears in the **browser tab** at the top of the window.
- It appears in the **browser bookmarks** when someone saves your page.
- It is the **clickable headline** shown in Google search results.
- It is critically important for **SEO** (Search Engine Optimisation) — search
  engines use it to rank your page.

> ⚠️ The `<title>` element is **required** in every HTML document. A page
> without one is technically incomplete.

### Simple Example

```html
<!DOCTYPE html>
<html>
<head>
  <title>Welcome to My Website</title>
</head>
<body>
  <p>Hello, world!</p>
</body>
</html>
```

**What you see in the browser tab:**
```
Welcome to My Website
```

**What you see on the page:**
```
Hello, world!
```

> Notice: "Welcome to My Website" is NOT shown on the page itself. It only
> appears in the browser tab and bookmarks.

### Second Example — A More Meaningful Title

```html
<!DOCTYPE html>
<html>
<head>
  <title>David's Photography Portfolio – Landscape & Nature</title>
</head>
<body>
  <h1>My Photos</h1>
</body>
</html>
```

**Browser tab shows:**
```
David's Photography Portfolio – Landscape & Nature
```

> 💡 **Real-world tip:** A good page title is between 50–60 characters long,
> includes the most important keyword first, and accurately describes the page.
> Example: `"HTML Tutorial for Beginners | W3Schools"` — not just `"Home"`.

### 🤔 Thinking Prompt
What would happen if you wrote `<title>My Page | Contact Us | Blog | Gallery</title>`?
Would that be a good title? Why or why not?

---

## Element 2 — `<style>`: Adding CSS Directly to the Page

### What is it?

The `<style>` element lets you write **CSS (Cascading Style Sheets)** rules
directly inside your HTML file. CSS is the language that controls how elements
look — colours, sizes, fonts, spacing, and more.

### Why does it matter?

Without CSS, every page looks plain and identical: black text on a white
background in the browser's default font. The `<style>` element lets you
change that for a single page.

> 💡 **Analogy:** If HTML is the structure of a house (walls, roof, doors),
> then CSS is the interior design — the paint colour, the furniture, the
> lighting.

### Simple Example

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background-color: powderblue;
    }
    h1 {
      color: red;
    }
    p {
      color: blue;
    }
  </style>
</head>
<body>
  <h1>Hello, World!</h1>
  <p>This paragraph is blue.</p>
</body>
</html>
```

**Visual output on the page:**
- The entire page background is powder blue.
- The heading "Hello, World!" is red.
- The paragraph text is blue.

### Breaking Down the CSS Syntax

```css
body {
  background-color: powderblue;
}
```

- `body` — the **selector**: which element to style.
- `{ }` — curly braces contain the rules.
- `background-color` — the **property**: what aspect to change.
- `powderblue` — the **value**: what to change it to.
- `;` — ends the rule (like a full stop in a sentence).

### Second Example — Styling Multiple Elements

```html
<style>
  h1 {
    font-size: 40px;
    color: darkgreen;
  }
  p {
    font-family: Arial, sans-serif;
    color: #333333;
  }
</style>
```

**Output:** All `<h1>` headings will be 40 pixels tall and dark green. All
paragraphs will use the Arial font and appear in dark grey.

> ⚠️ **When to use `<style>` vs a separate CSS file?**
> The `<style>` element is useful for small, single-page designs or quick
> tests. For real websites with multiple pages, you should use the `<link>`
> element to connect a separate `.css` file (explained next). That way all
> pages share the same styling without copy-pasting.

---

## Element 3 — `<link>`: Connecting an External CSS File

### What is it?

The `<link>` element defines the **relationship between the current HTML
document and an external file**. It is most commonly used to load a CSS file.

### Why does it matter?

Imagine you have a website with 20 pages. If you use `<style>` in every file,
you must update all 20 files whenever you change a colour. With `<link>`, you
connect all 20 pages to ONE CSS file. Change that file once — all pages update
instantly. This is how every professional website works.

### The `<link>` Element Attributes

```html
<link rel="stylesheet" href="mystyle.css">
```

- `rel="stylesheet"` — tells the browser the relationship: this external file
  is a **stylesheet** (CSS file).
- `href="mystyle.css"` — the path to the external CSS file.

> ⚠️ The `<link>` element is **self-closing** — it has no closing `</link>`
> tag.

### Simple Example

Imagine you have two files in the same folder:

**`index.html`:**
```html
<!DOCTYPE html>
<html>
<head>
  <title>My Styled Page</title>
  <link rel="stylesheet" href="mystyle.css">
</head>
<body>
  <h1>Welcome</h1>
  <p>This page uses an external CSS file.</p>
</body>
</html>
```

**`mystyle.css`:**
```css
body {
  background-color: lightyellow;
}
h1 {
  color: navy;
}
p {
  font-size: 18px;
}
```

**Output:** When you open `index.html`, the browser reads the `<link>` tag,
finds `mystyle.css`, and applies the styles. The background becomes light
yellow, the heading is navy blue, and the paragraph text is 18 pixels.

### Second Example — Linking from a Subfolder

If your CSS file is inside a folder called `css/`:

```html
<link rel="stylesheet" href="css/mystyle.css">
```

> 💡 **Real-world use:** Every major website links to one or more external CSS
> files. The `<link>` tag can also be used to link to a website icon (favicon):
> `<link rel="icon" href="favicon.ico">`.

---

## Element 4 — `<meta>`: Metadata for the Browser, Search Engines & More

### What is it?

The `<meta>` element provides **information about the HTML document** to
browsers, search engines, and other web services. It is a self-closing element
(no closing tag needed) and uses attributes to define what kind of information
it carries.

> 💡 **Analogy:** A `<meta>` tag is like a label on the back of a product. The
> product itself (the page content) is what you show visitors. The label
> (metadata) tells behind-the-scenes systems everything they need to know:
> what language it's in, what it's about, who made it.

### The Most Important `<meta>` Tags

#### 1. Character Set (`charset`)

```html
<meta charset="UTF-8">
```

**What is `charset`?** A character set is the system a computer uses to turn
numbers into letters and symbols. `UTF-8` is the universal standard that
supports almost every language in the world — English, Arabic, Chinese,
Yoruba, French accents, emojis, and more.

**Why is it important?** Without this declaration, some characters (like
accented letters or non-Latin scripts) may display as garbled symbols (e.g.,
`Ã©` instead of `é`).

> ⚠️ Always put `<meta charset="UTF-8">` as the **very first thing** inside
> `<head>`. It must come before `<title>` so the browser knows how to read
> the title correctly.

#### 2. Page Description

```html
<meta name="description" content="Free web tutorials for beginners and experts.">
```

- `name="description"` — tells the browser this is a page description.
- `content="..."` — the actual description text.

**Why is it important?** Search engines (Google, Bing) read this description
and often display it as the grey text below the blue link in search results.
A good description can significantly increase how many people click your page.

#### 3. Keywords

```html
<meta name="keywords" content="HTML, CSS, JavaScript, tutorial">
```

**Why does it exist?** This was historically used to tell search engines what
topics the page covers. Modern search engines largely ignore it, but it is
still part of the standard.

#### 4. Author

```html
<meta name="author" content="Jane Okafor">
```

**Why is it useful?** Documents the person or organisation that created the
page. Useful for CMS (Content Management Systems) and documentation sites.

#### 5. Auto-Refresh

```html
<meta http-equiv="refresh" content="30">
```

**What does this do?** Tells the browser to automatically reload the page
every 30 seconds. Useful for dashboards showing live data (stock prices,
sports scores, server status) that need to update regularly.

You can also use it to redirect after a delay:
```html
<meta http-equiv="refresh" content="5; url=https://www.example.com">
```
This redirects the user to `example.com` after 5 seconds.

#### 6. Viewport (Mobile-Responsive Setting)

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

This is one of the **most important** meta tags for modern websites. Let's
break it down word by word:

- `name="viewport"` — targets the viewport (the visible area of a web page in
  the browser window).
- `width=device-width` — sets the page width to match the screen width of
  the device (phone, tablet, laptop). Without this, a mobile phone would try
  to show the page at desktop width and zoom it out, making text tiny.
- `initial-scale=1.0` — sets the zoom level to 100% when the page first loads.

> 💡 **Real-world importance:** If you do not include the viewport meta tag,
> your page will look bad on mobile phones. It will appear zoomed out with
> tiny text. Include this in **every** HTML page you create.

### Full `<meta>` Example Together

```html
<head>
  <meta charset="UTF-8">
  <meta name="description" content="A beginner's guide to growing tomatoes at home.">
  <meta name="keywords" content="tomatoes, gardening, how to grow, vegetables">
  <meta name="author" content="Amara Diallo">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>How to Grow Tomatoes at Home</title>
</head>
```

**Expected output (what the browser/search engine sees):**
- Character encoding: UTF-8 (supports all languages)
- Search snippet description: "A beginner's guide to growing tomatoes at home."
- Author documented: Amara Diallo
- Mobile-friendly: Yes
- Browser tab title: "How to Grow Tomatoes at Home"

Nothing is visually displayed on the page from these tags — they all work
behind the scenes.

---

## Element 5 — `<script>`: Adding JavaScript Behaviour

### What is it?

The `<script>` element is used to add **JavaScript** — the programming
language that makes web pages interactive. JavaScript can respond to button
clicks, validate forms, animate elements, fetch data, and much more.

### Simple Example

```html
<!DOCTYPE html>
<html>
<head>
  <title>My JavaScript Demo</title>
  <script>
    function greetUser() {
      document.getElementById("message").innerHTML = "Hello, JavaScript!";
    }
  </script>
</head>
<body>
  <p id="message">Click the button below.</p>
  <button onclick="greetUser()">Click Me</button>
</body>
</html>
```

**Before clicking the button:**
```
Click the button below.
[Click Me]
```

**After clicking the button:**
```
Hello, JavaScript!
[Click Me]
```

### Breaking Down the Script

```javascript
function greetUser() {
```
- `function` — defines a reusable block of code called a function.
- `greetUser` — the name we give this function.
- `()` — parentheses hold any data passed to the function (none here).
- `{` — opens the function body.

```javascript
  document.getElementById("message").innerHTML = "Hello, JavaScript!";
```
- `document` — refers to the entire HTML page.
- `getElementById("message")` — finds the element with `id="message"`.
- `.innerHTML` — the content inside that element.
- `= "Hello, JavaScript!"` — replaces that content with new text.

```javascript
}
```
- Closes the function body.

> 💡 **Real-world note:** In professional practice, JavaScript is usually
> stored in a separate `.js` file and linked with `<script src="myscript.js">`,
> similar to how CSS is kept in an external file. You will learn more about
> JavaScript in a dedicated lesson.

---

## Element 6 — `<base>`: Setting a Default URL for All Links

### What is it?

The `<base>` element specifies the **base URL** for all relative links and/or
a **default target** for all links and forms on the page.

> ⚠️ There can be **only one** `<base>` element in any HTML document, and it
> must have either `href`, `target`, or both.

### Why does it exist?

Imagine your website is hosted at `https://www.mysite.com/blog/`, and you have
20 images and 15 links all written as relative paths. Without `<base>`, you
might have to type the full URL every time. With `<base>`, you set it once.

### Simple Example

```html
<head>
  <base href="https://www.w3schools.com/" target="_blank">
</head>
<body>
  <img src="images/stickman.gif" width="24" height="39" alt="Stickman">
  <a href="tags/tag_base.asp">HTML base Tag</a>
</body>
```

**What happens:**
- The image `src="images/stickman.gif"` actually resolves to
  `https://www.w3schools.com/images/stickman.gif`
- The link `href="tags/tag_base.asp"` resolves to
  `https://www.w3schools.com/tags/tag_base.asp`
- `target="_blank"` means every link on the page opens in a **new browser tab**

### Breaking Down the Attributes

- `href="https://www.w3schools.com/"` — sets the base URL. All relative
  links are appended to this.
- `target="_blank"` — opens linked pages in a new tab. Other values:
  - `_self` — same tab (default behaviour)
  - `_parent` — parent frame
  - `_top` — full window

> 💡 **Real-world use:** `<base>` is commonly used in single-page applications
> and Content Management Systems where a consistent root URL needs to be
> established for asset loading.

---

## Complete `<head>` Structure Reference

Here is what a fully set-up `<head>` section looks like with all elements:

```html
<!DOCTYPE html>
<html>
<head>

  <!-- 1. Character set — always first -->
  <meta charset="UTF-8">

  <!-- 2. Viewport for mobile responsiveness -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- 3. Page title — required -->
  <title>Recipe Blog – Easy Nigerian Dishes</title>

  <!-- 4. SEO meta tags -->
  <meta name="description" content="Simple and delicious Nigerian recipes for every home cook.">
  <meta name="keywords" content="Nigerian food, recipes, jollof rice, egusi, suya">
  <meta name="author" content="Ngozi Eze">

  <!-- 5. Link to external CSS -->
  <link rel="stylesheet" href="styles/main.css">

  <!-- 6. JavaScript -->
  <script>
    function showWelcome() {
      alert("Welcome to our recipe blog!");
    }
  </script>

  <!-- 7. Base URL (optional) -->
  <base href="https://www.recipelove.com/" target="_self">

</head>
<body>
  <h1>Easy Nigerian Dishes</h1>
</body>
</html>
```

**What the browser does with each line:**
1. Sets character encoding to UTF-8
2. Makes the page mobile-friendly
3. Shows "Recipe Blog – Easy Nigerian Dishes" in the tab
4. Gives Google a description to show in search results
5. Loads styling from `styles/main.css`
6. Defines a function the page can call
7. Prefixes all relative links with the base URL

---

## Quick Summary Table of All `<head>` Elements

| Tag | Type | Visible on Page? | Primary Purpose |
|---|---|---|---|
| `<title>` | Paired | ❌ (tab only) | Browser tab title, SEO |
| `<style>` | Paired | ❌ | Internal CSS for this page |
| `<link>` | Self-closing | ❌ | Link to external CSS/resources |
| `<meta charset>` | Self-closing | ❌ | Character encoding |
| `<meta name="description">` | Self-closing | ❌ | Search engine description |
| `<meta name="keywords">` | Self-closing | ❌ | SEO keywords |
| `<meta name="author">` | Self-closing | ❌ | Page author |
| `<meta name="viewport">` | Self-closing | ❌ | Mobile responsiveness |
| `<meta http-equiv="refresh">` | Self-closing | ❌ | Auto-refresh / redirect |
| `<script>` | Paired | ❌ | JavaScript code or link |
| `<base>` | Self-closing | ❌ | Default URL prefix / target |

---

## Guided Practice Exercises

### ✅ Exercise 1 — Write a Basic `<head>` Section

**Objective:** Build a minimal but complete `<head>` for a simple web page.

**Scenario:** You are creating a simple personal web page about yourself.

**Steps:**

1. Open your text editor and create a new file called `about.html`.
2. Write the full HTML structure with `<!DOCTYPE html>`, `<html>`, `<head>`,
   and `<body>`.
3. Inside `<head>`, add:
   - A `<meta charset="UTF-8">` tag
   - A `<meta name="viewport">` tag with `content="width=device-width, initial-scale=1.0"`
   - A `<title>` with text: `About Me – [Your Name]`

**Your code should look like this:**

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>About Me – Fatima Hassan</title>
</head>
<body>
  <h1>Hello! I'm Fatima.</h1>
  <p>I'm learning HTML and loving it!</p>
</body>
</html>
```

**Expected browser tab title:**
```
About Me – Fatima Hassan
```

**Self-check questions:**
- Is `<meta charset="UTF-8">` the first thing inside `<head>`?
- Does your `<title>` contain only plain text (no HTML tags)?
- Is the viewport meta tag present?

---

### ✅ Exercise 2 — Add Internal Styling with `<style>`

**Objective:** Use the `<style>` element to change how the page looks.

**Scenario:** Style the personal page from Exercise 1.

**Steps:**

1. Add a `<style>` block inside `<head>` (after the meta tags).
2. Set the body background colour to `#f0f8ff` (Alice Blue).
3. Make the `h1` heading colour `#2c3e50` (dark blue).
4. Make the paragraph text colour `#555555` (medium grey) and font size `16px`.

**Expected code (head section only):**

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>About Me – Fatima Hassan</title>
  <style>
    body {
      background-color: #f0f8ff;
    }
    h1 {
      color: #2c3e50;
    }
    p {
      color: #555555;
      font-size: 16px;
    }
  </style>
</head>
```

**Visual output on page:**
- Light blue-tinted background
- Dark blue heading
- Medium grey paragraph text at 16px size

**What-if experiment:** Change `background-color: #f0f8ff` to
`background-color: tomato` and reload. What changes?

---

### ✅ Exercise 3 — Adding SEO Metadata

**Objective:** Add useful metadata for search engines.

**Scenario:** Imagine your page is a blog post about learning to code. Make
it search-engine friendly.

**Steps:**

Add these three `<meta>` tags inside `<head>`:

1. A `description` — something like: `"A beginner's journey through HTML, CSS, and JavaScript."`
2. `keywords` — include: `HTML, CSS, beginner, coding, learn to code`
3. `author` — your name

**Code to add:**

```html
<meta name="description" content="A beginner's journey through HTML, CSS, and JavaScript.">
<meta name="keywords" content="HTML, CSS, beginner, coding, learn to code">
<meta name="author" content="Fatima Hassan">
```

**Expected result:** While nothing extra shows on the page, if you were to
submit this page to Google, it would read the description and show it in
search results beneath your page title.

**Self-check questions:**
- Are all meta tags self-closing (no `</meta>` at the end)?
- Is the description between 50–160 characters?

---

### ✅ Exercise 4 — Link an External CSS File

**Objective:** Replace the `<style>` block with an external CSS link.

**Steps:**

1. Create a new file called `style.css` in the same folder.
2. Move all your CSS rules from `<style>` into `style.css`.
3. In your HTML file, replace the entire `<style>` block with:
   ```html
   <link rel="stylesheet" href="style.css">
   ```

**`style.css` should contain:**

```css
body {
  background-color: #f0f8ff;
}

h1 {
  color: #2c3e50;
}

p {
  color: #555555;
  font-size: 16px;
}
```

**`about.html` head section should now be:**

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="A beginner's journey through HTML, CSS, and JavaScript.">
  <meta name="keywords" content="HTML, CSS, beginner, coding, learn to code">
  <meta name="author" content="Fatima Hassan">
  <title>About Me – Fatima Hassan</title>
  <link rel="stylesheet" href="style.css">
</head>
```

**Expected result:** The page looks identical to Exercise 2, but the styling
now comes from the external file.

**What-if experiment:** What happens if you misspell the filename as
`href="styles.css"` instead of `href="style.css"`? (Answer: The styles
won't load, and the page reverts to plain/unstyled appearance.)

---

### ✅ Exercise 5 — The Viewport Challenge (Metadata Elements)

**Objective:** Understand and use the viewport meta tag correctly.

**Scenario:** You are building a page for a small business. It must look
correct on both desktop and mobile.

**Task:** Write the complete `<head>` section for a page called
"Bright Smiles Dental Clinic – Appointments" that:

1. Uses UTF-8 character encoding
2. Is mobile-responsive
3. Has a meaningful title
4. Has a description for Google
5. Links to `clinic.css`
6. Has the author set to "Dr. Emeka Adeyemi"

**Solution:**

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Book your dental appointment at Bright Smiles Clinic. Caring for your teeth since 2005.">
  <meta name="author" content="Dr. Emeka Adeyemi">
  <title>Bright Smiles Dental Clinic – Book an Appointment</title>
  <link rel="stylesheet" href="clinic.css">
</head>
```

**Self-check:** Does your `<meta name="viewport">` have both `width=device-width`
AND `initial-scale=1.0`?

---

## Mini Project: The Complete Professional Web Page Head

### Project Description

You will build the complete `<head>` section for a professional personal
portfolio website from scratch. This project brings together every element
you have learned in this lesson.

### Project Goal

Build a file called `portfolio.html` with a fully professional `<head>` section
and a simple body, ready to be styled and expanded.

---

### Stage 1 — Setup

Create `portfolio.html`. Start with the required skeleton:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- Your work goes here -->
</head>
<body>
  <h1>My Portfolio</h1>
  <p id="intro">Welcome to my personal portfolio website.</p>
  <button onclick="showMessage()">Say Hello</button>
</body>
</html>
```

**Milestone output:** A blank page with the heading "My Portfolio", a
paragraph, and a button that does nothing yet.

---

### Stage 2 — Add Core Metadata

Add the following inside `<head>`:

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Personal portfolio of Chidi Nwosu – Frontend Developer from Lagos, Nigeria.">
<meta name="keywords" content="portfolio, frontend developer, HTML, CSS, JavaScript, Lagos">
<meta name="author" content="Chidi Nwosu">
```

**Milestone:** Your page now works on all screen sizes and is search-engine
ready.

---

### Stage 3 — Add the Title

```html
<title>Chidi Nwosu | Frontend Developer Portfolio</title>
```

**Milestone output (browser tab):**
```
Chidi Nwosu | Frontend Developer Portfolio
```

---

### Stage 4 — Add Styling

Create `portfolio.css` with the following content:

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Segoe UI', Arial, sans-serif;
  background-color: #1a1a2e;
  color: #eaeaea;
  padding: 40px;
}

h1 {
  font-size: 48px;
  color: #e94560;
  margin-bottom: 16px;
}

p {
  font-size: 18px;
  line-height: 1.6;
  margin-bottom: 24px;
}

button {
  background-color: #e94560;
  color: white;
  padding: 12px 28px;
  border: none;
  border-radius: 6px;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background-color: #c73652;
}
```

Now link it in `<head>`:

```html
<link rel="stylesheet" href="portfolio.css">
```

**Milestone output:**
- Dark navy background
- Red heading "My Portfolio"
- White text paragraph
- Styled red button

---

### Stage 5 — Add JavaScript

Add this `<script>` block inside `<head>`:

```html
<script>
  function showMessage() {
    document.getElementById("intro").innerHTML =
      "Hello! I build beautiful websites with HTML, CSS, and JavaScript.";
  }
</script>
```

**Before clicking the button:**
```
Welcome to my personal portfolio website.
[Say Hello]
```

**After clicking "Say Hello":**
```
Hello! I build beautiful websites with HTML, CSS, and JavaScript.
[Say Hello]
```

---

### Stage 6 — Final Complete File

Here is the complete `portfolio.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>

  <!-- Core metadata -->
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- SEO metadata -->
  <meta name="description" content="Personal portfolio of Chidi Nwosu – Frontend Developer from Lagos, Nigeria.">
  <meta name="keywords" content="portfolio, frontend developer, HTML, CSS, JavaScript, Lagos">
  <meta name="author" content="Chidi Nwosu">

  <!-- Page title -->
  <title>Chidi Nwosu | Frontend Developer Portfolio</title>

  <!-- External CSS -->
  <link rel="stylesheet" href="portfolio.css">

  <!-- JavaScript -->
  <script>
    function showMessage() {
      document.getElementById("intro").innerHTML =
        "Hello! I build beautiful websites with HTML, CSS, and JavaScript.";
    }
  </script>

</head>
<body>

  <h1>My Portfolio</h1>
  <p id="intro">Welcome to my personal portfolio website.</p>
  <button onclick="showMessage()">Say Hello</button>

</body>
</html>
```

---

### Stage 7 — Optional Enhancements

Try adding these improvements:

1. Add a favicon link: `<link rel="icon" href="favicon.ico">`
2. Add an auto-refresh (for testing): `<meta http-equiv="refresh" content="60">`
3. Add a `<base>` tag with your domain: `<base href="https://chidinwosu.dev/">`
4. Add a second button that changes the page background colour using JavaScript

---

### Reflection Questions

1. Why do we put `<meta charset="UTF-8">` before `<title>`?
2. What is the difference between using `<style>` inside the HTML file and
   using `<link>` to an external CSS file? When would you choose each?
3. If you have a website with 50 pages and you change the navigation menu
   style, why is it better to use an external CSS file linked with `<link>`?
4. What would happen to your page on a mobile phone if you forgot the viewport
   meta tag?
5. Can you put more than one `<base>` element in a page? What happens if you try?

---

## Common Beginner Mistakes

### Mistake 1 — Forgetting `<meta charset="UTF-8">`

❌ **Wrong:**
```html
<head>
  <title>My Page</title>
</head>
```

✅ **Correct:**
```html
<head>
  <meta charset="UTF-8">
  <title>My Page</title>
</head>
```

**Why it matters:** Without the charset, special characters (like `é`, `ñ`,
`ü`, Arabic, or Chinese characters) may display as strange symbols.

---

### Mistake 2 — Writing Content or Closing Tags for Self-Closing Elements

❌ **Wrong:**
```html
<meta charset="UTF-8"></meta>
<link rel="stylesheet" href="style.css"></link>
```

✅ **Correct:**
```html
<meta charset="UTF-8">
<link rel="stylesheet" href="style.css">
```

**Why it matters:** `<meta>`, `<link>`, and `<base>` are self-closing (void
elements). They do not have a closing tag and do not contain content.

---

### Mistake 3 — Putting HTML Tags Inside `<title>`

❌ **Wrong:**
```html
<title><h1>My Amazing Website</h1></title>
```

✅ **Correct:**
```html
<title>My Amazing Website</title>
```

**Why it matters:** The `<title>` element only accepts plain text. Adding HTML
tags inside it will cause them to appear as literal text (including the
angle brackets) in the browser tab.

---

### Mistake 4 — Forgetting the Viewport Meta Tag

❌ **Wrong (mobile will look broken):**
```html
<head>
  <meta charset="UTF-8">
  <title>My Mobile Site</title>
</head>
```

✅ **Correct:**
```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Mobile Site</title>
</head>
```

**Why it matters:** Without the viewport tag, mobile browsers zoom out the
entire page and make everything tiny.

---

### Mistake 5 — Using More Than One `<base>` Element

❌ **Wrong:**
```html
<head>
  <base href="https://site-a.com/">
  <base href="https://site-b.com/">
</head>
```

✅ **Correct:**
```html
<head>
  <base href="https://site-a.com/" target="_blank">
</head>
```

**Why it matters:** Only one `<base>` element is allowed per page. If you
include more than one, browsers use only the first one and ignore the rest.

---

### Mistake 6 — Misspelling `href` Attribute in `<link>`

❌ **Wrong:**
```html
<link rel="stylesheet" hraf="style.css">
```

✅ **Correct:**
```html
<link rel="stylesheet" href="style.css">
```

**Why it matters:** Misspelling `href` means the browser cannot find the CSS
file, and your page will have no styling.

---

### Mistake 7 — Placing `<head>` Content Inside `<body>`

❌ **Wrong:**
```html
<body>
  <meta charset="UTF-8">
  <title>Oops</title>
  <h1>Hello</h1>
</body>
```

✅ **Correct:**
```html
<head>
  <meta charset="UTF-8">
  <title>Correct</title>
</head>
<body>
  <h1>Hello</h1>
</body>
```

**Why it matters:** Metadata elements belong in `<head>`, not `<body>`. If
placed in `<body>`, browsers may partially ignore them or behave
unpredictably.

---

## Completion Checklist

Before you finish this lesson, make sure you can tick every box:

- [ ] I understand what the `<head>` element is and that its content is not
      displayed on the page
- [ ] I can write a `<title>` element with a meaningful, descriptive title
- [ ] I know why `<meta charset="UTF-8">` must come first in `<head>`
- [ ] I can write the viewport `<meta>` tag from memory
- [ ] I can add a page description, keywords, and author using `<meta>` tags
- [ ] I understand the difference between `<style>` (internal) and
      `<link rel="stylesheet">` (external) CSS
- [ ] I can write a `<link>` tag to connect an external CSS file
- [ ] I can write a simple `<script>` block that changes page content
- [ ] I understand what `<base>` does and know only one is allowed per page
- [ ] I know and can avoid the common mistakes from this lesson
- [ ] I have completed the mini project portfolio page

---

## Lesson Summary

The `<head>` element is the invisible control centre of every HTML page. It
sits between `<html>` and `<body>` and holds setup instructions that the
browser, search engines, and other services read before displaying your page.

Here is what each `<head>` element does at a glance:

**`<title>`** — sets the browser tab title; required on every page; critical
for SEO. Write it accurately and meaningfully.

**`<style>`** — lets you add CSS directly inside the HTML file; useful for
single-page projects or quick prototypes.

**`<link>`** — connects to an external CSS file; best practice for multi-page
websites because one CSS file styles all pages at once.

**`<meta>`** — provides metadata in many forms:
- `charset="UTF-8"` — universal character encoding
- `name="viewport"` — makes pages look good on mobile
- `name="description"` — controls your Google search snippet
- `name="keywords"` — SEO topic tags
- `name="author"` — documents page authorship
- `http-equiv="refresh"` — auto-refreshes or redirects the page

**`<script>`** — adds JavaScript that makes the page interactive; can be
inline or linked via `src`.

**`<base>`** — sets a default URL prefix for all relative links; only one
allowed per page.

A properly written `<head>` section is the foundation of every professional,
accessible, SEO-friendly, and mobile-ready web page. Take time to write it
correctly every single time.

---

> 🎓 **What's next?** In Lesson 25 you will learn about **HTML Layout** —
> how to use semantic elements like `<header>`, `<nav>`, `<main>`, `<aside>`,
> `<footer>`, and `<section>` to structure a full web page layout in a way
> that is clear, accessible, and professional.
