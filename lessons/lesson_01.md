---
render_with_liquid: false
title: "Lesson 01 — Introduction to HTML & Setting Up Your Editor"
nav_order: 1
---

## Lesson Introduction

Welcome! This is your very first step into the world of web development. By the end of this lesson you will know:

- What HTML is and why it exists
- What problems HTML solves
- How the web uses HTML to show content in a browser
- What an HTML element, tag, and document look like
- How to set up a free text editor and write your very first web page
- How to open that web page in a browser and see your work come to life

You do **not** need any prior coding knowledge. Everything is explained from scratch. Whenever a new technical word appears, it is defined immediately in plain language.

> **Think of it this way:** Imagine you are writing a letter. The words you write are the *content*. But you also need to tell the post office how to handle it — envelope, address, stamps. HTML is that envelope system for web content. It wraps your text in instructions so the browser knows exactly how to display it.

---

## Prerequisite Concepts

Before you read the main lesson, make sure you understand these three ideas. They are not hard — each takes less than two minutes.

### What is a Web Browser?

A **web browser** is the program you use to visit websites. Examples: Google Chrome, Mozilla Firefox, Microsoft Edge, Apple Safari. The browser's job is to read files and display them as nice-looking pages. It does *not* show the code — it reads the code and turns it into what you see on screen.

### What is a File?

A **file** is a collection of data saved on your computer with a name. Files have *extensions* (the letters after the dot in the name) that tell your computer what kind of file it is. For example:
- `photo.jpg` → a photo image
- `song.mp3` → an audio file
- `index.html` → a web page file

### What is Plain Text?

**Plain text** is text with absolutely no formatting — no bold, no colour, no font. Programs like Notepad (Windows) or TextEdit (Mac) can produce plain text. This is important because HTML files must be saved as plain text, not as a Word document or rich-text file.

---

## Part 1 — What is HTML?

### 1.1 The Big Picture: HTML in One Sentence

> **HTML** stands for **H**yper **T**ext **M**arkup **L**anguage. It is the standard language used to create and structure web pages.

Let's break that definition word by word:

| Word | Meaning |
|---|---|
| **Hyper** | Beyond normal — it can link to other documents (hyperlinks) |
| **Text** | It is written as readable text in a file |
| **Markup** | It uses special labels (called *tags*) to mark up (annotate) your content |
| **Language** | It is a set of rules that both humans and browsers follow |

### 1.2 What Problem Does HTML Solve?

Imagine you want to share a document on the internet. You type:

```
My First Heading
My first paragraph.
```

A browser would have no idea whether "My First Heading" is a title, a subtitle, a caption, or ordinary text. It would just display it all as one flat blob. HTML solves this by letting you *label* every piece of content so the browser knows how to display it.

With HTML, you tell the browser:
- "This line is a **big heading**"
- "This line is a **paragraph**"
- "This word is a **clickable link**"
- "This item belongs to a **list**"

### 1.3 What HTML Is NOT

HTML is not a *programming language* — it does not run calculations or make decisions. It is purely a *description language*. It tells the browser **what things are**, not what to *do*.

> **Analogy:** HTML is like the blueprint of a building. It says "this room is the kitchen, this room is the bedroom." The actual construction (making things interactive and beautiful) is done later by CSS (styling) and JavaScript (behaviour).

### 1.4 A Brief History of HTML

HTML has evolved over 30+ years. Here is a quick timeline:

| Year | Event |
|---|---|
| 1989 | Tim Berners-Lee invents the World Wide Web concept |
| 1991 | Tim Berners-Lee creates HTML — the first version |
| 1993 | Dave Raggett drafts HTML+ with more features |
| 1995 | HTML Working Group defines HTML 2.0 |
| 1997 | W3C releases HTML 3.2 |
| 1999 | W3C releases HTML 4.01 |
| 2000 | XHTML 1.0 released (stricter version) |
| 2008 | HTML5 first public draft released |
| 2014 | HTML5 becomes an official W3C Recommendation |
| 2017 | HTML5.2 released |
| Today | HTML5 is the current living standard |

This tutorial follows **HTML5**, the modern standard used by all websites today.

---

## Part 2 — Understanding HTML Elements and Tags

This is the most important section. Take your time here.

### 2.1 What is an HTML Tag?

A **tag** is a special label you write in your HTML file. Tags are always enclosed in **angle brackets** `< >`. They look like this:

```html
<h1>
```

There are two kinds of tags:

- **Opening tag** — signals the *start* of something: `<h1>`
- **Closing tag** — signals the *end* of something: `</h1>` (notice the forward slash `/`)

### 2.2 What is an HTML Element?

An **element** is the complete unit: opening tag + content + closing tag together.

```
<tagname>Content goes here</tagname>
```

**Simple example — a heading:**

```html
<h1>My First Heading</h1>
```

- `<h1>` → **Opening tag** — "start a big heading"
- `My First Heading` → **Content** — the actual text shown on screen
- `</h1>` → **Closing tag** — "end the heading"

**Simple example — a paragraph:**

```html
<p>My first paragraph.</p>
```

- `<p>` → Opening tag for a paragraph
- `My first paragraph.` → The text that will appear
- `</p>` → Closing tag

> **Thinking prompt:** What do you think would happen if you forgot the closing tag `</p>`? Try to guess before reading the "Common Mistakes" section later!

### 2.3 The Element Table — Input → Process → Output

| Input (what you write) | Process (what the browser does) | Output (what you see) |
|---|---|---|
| `<h1>Hello</h1>` | Browser reads the `h1` tag, applies large bold font | **Hello** (displayed as a large heading) |
| `<p>Nice day</p>` | Browser reads the `p` tag, adds spacing around text | Nice day (as a paragraph) |
| `<br>` | Browser inserts a line break | A blank line (no visible text) |

### 2.4 Empty Elements (Self-Closing Tags)

Some HTML elements have **no content** and no closing tag. They are called **empty elements** or **void elements**. The most common example is `<br>`, which creates a line break.

```html
<p>Line one.<br>Line two.</p>
```

**Expected output in the browser:**
```
Line one.
Line two.
```

Notice: `<br>` has no closing tag `</br>`. It stands alone. Other common empty elements you will meet later: `<img>` (images), `<input>` (form fields), `<hr>` (horizontal rule).

---

## Part 3 — The Structure of an HTML Document

Every valid HTML page follows a specific structure. Think of it as the *skeleton* every web page must have. Let's examine it piece by piece.

### 3.1 The Complete Minimal HTML Document

```html
<!DOCTYPE html>
<html>
<head>
  <title>Page Title</title>
</head>
<body>

  <h1>My First Heading</h1>
  <p>My first paragraph.</p>

</body>
</html>
```

**Expected output in the browser:**
- The browser tab shows: `Page Title`
- The page displays a large heading: **My First Heading**
- Below it, a paragraph: My first paragraph.

### 3.2 Line-by-Line Explanation

**Line 1: `<!DOCTYPE html>`**

This is a **declaration** (not a tag — notice it starts with `!`). It tells the browser: "This file uses HTML5." Every single HTML page should start with this. Without it, older browsers may display your page incorrectly.

```html
<!DOCTYPE html>
```

> It is not case-sensitive — `<!doctype html>` also works — but the capitalised form `<!DOCTYPE html>` is the standard convention.

---

**Line 2: `<html>`**

This is the **root element**. Everything on your page goes inside `<html>...</html>`. Think of it as the outer container that holds everything else.

```html
<html>
  ... everything goes in here ...
</html>
```

---

**Lines 3–5: `<head>...</head>`**

The `<head>` section holds **information about the page** that is NOT displayed on screen. It is invisible to visitors but important for the browser.

```html
<head>
  <title>Page Title</title>
</head>
```

The `<title>` tag inside `<head>` sets the text shown in:
- The browser's title bar (the top bar of the window)
- The browser tab (the small clickable tab)
- Search engine results (e.g. Google shows this as the clickable link title)

---

**Lines 6–11: `<body>...</body>`**

The `<body>` section holds **all the visible content** — everything the visitor actually sees on the page.

```html
<body>
  <h1>My First Heading</h1>
  <p>My first paragraph.</p>
</body>
```

- `<h1>` — Defines the largest (most important) heading. There are 6 heading sizes: `<h1>` through `<h6>`, where `<h1>` is biggest and `<h6>` is smallest.
- `<p>` — Defines a paragraph of text.

### 3.3 Visual Page Structure

Here is a visual map of how the sections relate:

```
┌─────────────────────────────────────────┐
│  <html>                                 │
│  ┌───────────────────────────────────┐  │
│  │  <head>                           │  │
│  │    <title>Page Title</title>      │  │  ← NOT shown on page
│  │  </head>                          │  │
│  ├───────────────────────────────────┤  │
│  │  <body>                           │  │
│  │    <h1>This is a heading</h1>     │  │  ← SHOWN on page
│  │    <p>This is a paragraph.</p>    │  │  ← SHOWN on page
│  │    <p>Another paragraph.</p>      │  │  ← SHOWN on page
│  │  </body>                          │  │
│  └───────────────────────────────────┘  │
│  </html>                                │
└─────────────────────────────────────────┘
```

### 3.4 How a Browser Reads Your HTML

Here is the simple journey of your HTML file to the screen:

1. You write HTML code in a text editor and save it as a `.html` file.
2. You open the file in a browser.
3. The browser reads the file from top to bottom.
4. It sees the tags and understands what each piece of content is.
5. It renders (draws) the page according to those instructions.
6. You see the finished, formatted page — **without** seeing any of the HTML code.

> **Key insight:** The browser never *shows* the tags. It only uses the tags to decide how to display the content.

---

## Part 4 — HTML Editors: Setting Up Your Workspace

Now that you understand what HTML is, you need a place to *write* it. That place is a **text editor**.

### 4.1 What is a Text Editor?

A **text editor** is a program that lets you write and save plain text files. This is different from a word processor like Microsoft Word, which adds hidden formatting. HTML files must be plain text — no hidden formatting.

> **Analogy:** A word processor (like Word) is like a fancy restaurant — it adds decorations automatically. A plain text editor is like a blank notebook — you write exactly what you want, nothing more.

### 4.2 Two Approaches: Simple Editor vs Code Editor

**Option A — Simple Text Editor (Beginner-Friendly, Free, Already on Your Computer)**

| Editor | Operating System | How to Open |
|---|---|---|
| **Notepad** | Windows | Start menu → type "Notepad" |
| **TextEdit** | Mac | Finder → Applications → TextEdit |

These are already installed on your computer and require zero setup. They are perfect for learning because you see exactly what you type.

**Option B — Code Editor (More Powerful, Free Download)**

As you progress, many developers use dedicated code editors that offer features like:
- **Syntax highlighting** (colours your HTML tags so they are easier to read)
- **Auto-complete** (suggests tag names as you type)
- **Error detection** (helps you spot unclosed tags)

Popular free code editors: **Visual Studio Code** (VS Code), **Sublime Text**, **Atom**, **Brackets**.

For this lesson, we will use **Notepad or TextEdit** — they are the best tools for learning because there is nothing hiding from you.

### 4.3 Step-by-Step: Writing Your First HTML File (Windows — Notepad)

Follow these steps exactly:

**Step 1: Open Notepad**

- **Windows 8 or later:** Press the Windows key, type `Notepad`, press Enter.
- **Windows 7 or earlier:** Click Start → Programs → Accessories → Notepad.

**Step 2: Type the HTML Code**

In Notepad, type the following HTML code exactly as shown (or copy-paste it):

```html
<!DOCTYPE html>
<html>
<body>

<h1>My First Heading</h1>

<p>My first paragraph.</p>

</body>
</html>
```

> **Important:** Type everything yourself at least once. Your fingers will remember it faster than your eyes.

**Step 3: Save the File**

- Click **File** → **Save As**
- In the "File name" box, type: `index.htm`
- In the "Encoding" dropdown, select: `UTF-8`
- Choose a location (e.g. your Desktop)
- Click **Save**

> **Why UTF-8?** UTF-8 is a character encoding standard. It ensures all special characters (accents, symbols, foreign letters) display correctly. Always use UTF-8 for HTML files.

> **Why .htm or .html?** Both `.htm` and `.html` are valid file extensions for HTML files. They work identically. `.html` is more common today.

**Step 4: Open the File in Your Browser**

- Go to where you saved the file (e.g. your Desktop)
- Double-click the file `index.htm`
- Your default browser will open and display the page

**Expected output in the browser:**

```
My First Heading     ← displayed as a large bold heading

My first paragraph.  ← displayed as normal paragraph text
```

Congratulations — you have created your first web page! 🎉

---

### 4.4 Step-by-Step: Writing Your First HTML File (Mac — TextEdit)

**Step 1: Open TextEdit**

- Click **Finder** → **Applications** → **TextEdit**

**Step 2: Configure TextEdit for Plain Text (VERY IMPORTANT)**

By default, TextEdit saves in "rich text" format (like a word processor). You must switch it to plain text mode:

- Click **TextEdit** (top menu) → **Preferences**
- Under "Format", select **Plain Text**
- Click "Open and Save" tab
- Check the box: **"Display HTML files as HTML code instead of formatted text"**
- Close the Preferences window
- Open a **new document** (File → New)

**Step 3: Type the HTML Code**

Type the same HTML code from above into the new document.

**Step 4: Save the File**

- Click **File** → **Save As**
- Name the file: `index.html`
- Make sure "Plain Text Encoding" is set to **Unicode (UTF-8)**
- If prompted to use `.txt` extension, click **"Use .html"**

**Step 5: Open in Browser**

Double-click the saved file to open it in your browser.

---

### 4.5 The W3Schools Online Editor — "Try it Yourself"

W3Schools also provides a free online editor at [w3schools.com/tryit](https://www.w3schools.com/tryit/default.asp). This is extremely useful because:
- No installation needed — works in any browser
- Type code on the left → instantly see the result on the right
- Saves you from creating files on your computer while experimenting

The online editor has two panels:
- **Left panel:** You type your HTML code
- **Right panel:** The browser output is shown live

> **Tip:** Use the online editor when you want to quickly test a small idea. Use Notepad/TextEdit when building a full project you want to save on your computer.

---

## Part 5 — Simple Standalone Examples

Now let's practise the concepts with fully explained examples.

### Example 1 — The Simplest Possible Web Page

```html
<!DOCTYPE html>
<html>
<body>

<p>Hello, World!</p>

</body>
</html>
```

**What each line does:**
- `<!DOCTYPE html>` — Tells the browser this is HTML5
- `<html>` — Opens the HTML document
- `<body>` — Opens the visible content area
- `<p>Hello, World!</p>` — Creates a paragraph containing "Hello, World!"
- `</body>` — Closes the body
- `</html>` — Closes the HTML document

**Expected browser output:**
```
Hello, World!
```

> **Thinking prompt:** What happens if you remove the `<p>` tags? The text would still appear, but it would lose the paragraph spacing. Try it!

---

### Example 2 — A Page with a Title and a Heading

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Learning Page</title>
</head>
<body>

  <h1>Welcome to HTML!</h1>
  <p>I am learning how to build web pages.</p>

</body>
</html>
```

**What changed from Example 1:**
- We added a `<head>` section with a `<title>` — the browser tab now shows "My Learning Page"
- We added an `<h1>` heading — a big, bold title on the page

**Expected browser output:**
- Browser tab label: `My Learning Page`
- Page content:
  ```
  Welcome to HTML!         ← large bold heading

  I am learning how to build web pages.   ← paragraph below it
  ```

---

### Example 3 — Multiple Headings and Paragraphs

```html
<!DOCTYPE html>
<html>
<head>
  <title>My First Full Page</title>
</head>
<body>

  <h1>My Favourite Subject</h1>
  <p>I love learning about computers and the web.</p>

  <h2>Why I Like It</h2>
  <p>Building websites lets me create things that anyone in the world can see.</p>

  <h3>My Goal</h3>
  <p>One day I want to build my own app.</p>

</body>
</html>
```

**New concepts introduced:**
- `<h2>` — A second-level heading (smaller than `<h1>`, but still a heading)
- `<h3>` — A third-level heading (smaller than `<h2>`)

**Expected browser output:**
```
My Favourite Subject         ← largest heading (h1)

I love learning about computers and the web.

Why I Like It                ← medium heading (h2)

Building websites lets me create things that anyone in the world can see.

My Goal                      ← smaller heading (h3)

One day I want to build my own app.
```

> **Thinking prompt:** There are headings `<h1>` through `<h6>`. What do you think `<h6>` looks like compared to `<h1>`? Add both to your page and see.

---

### Example 4 — Using a Line Break Inside a Paragraph

```html
<!DOCTYPE html>
<html>
<body>

<p>Line one of the poem.<br>Line two of the poem.<br>Line three of the poem.</p>

</body>
</html>
```

**`<br>` explained:**  
The `<br>` tag inserts a **line break** inside a paragraph. Without it, all the text would appear on one line. It is an empty element — no closing tag needed.

**Expected browser output:**
```
Line one of the poem.
Line two of the poem.
Line three of the poem.
```

---

## Part 6 — Guided Practice Exercises

### Exercise 1: Build a Simple "About Me" Page

**Objective:** Create your first personalised web page using a title, headings, and paragraphs.

**Scenario:** You are building a simple personal profile page that you could show to a friend.

**Steps:**

1. Open Notepad (Windows) or TextEdit (Mac).
2. Type the complete HTML structure: `<!DOCTYPE html>`, `<html>`, `<head>`, `<title>`, `<body>`.
3. Set the `<title>` to your own name, e.g. `<title>About Amara</title>`.
4. Inside `<body>`, add:
   - An `<h1>` tag with your full name.
   - A `<p>` tag introducing who you are (1–2 sentences).
   - An `<h2>` tag titled "My Hobbies".
   - A `<p>` tag listing 2–3 hobbies.
   - An `<h2>` tag titled "My Goal".
   - A `<p>` tag describing one goal you have.
5. Save the file as `about.html` (encoding: UTF-8).
6. Open it in your browser.

**Hints:**
- Every opening tag `<tagname>` needs a matching closing tag `</tagname>`.
- The `<body>` section is where all your visible content goes.
- Use `<h2>` for section headings (not as big as `<h1>`).

**Expected output (example):**
```
Amara Chukwu                  ← h1 heading

I am a student from Lagos who loves technology.

My Hobbies                    ← h2 heading

I enjoy reading, coding, and playing football.

My Goal                       ← h2 heading

I want to become a web developer and build useful apps for Africa.
```

**Self-check questions:**
- Does your browser tab show your name?
- Is your `<h1>` larger than your `<h2>` headings?
- Is all your text inside the `<body>` tag?
- Did you close every tag you opened?

**What-if challenge:** Add an `<h3>` heading called "A Fun Fact About Me" with a paragraph below it. What happens to the heading size?

---

### Exercise 2: Write a Page with the 6 Heading Levels

**Objective:** Observe how all 6 HTML heading sizes look and feel different.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Heading Sizes</title>
</head>
<body>

  <h1>Heading Level 1</h1>
  <h2>Heading Level 2</h2>
  <h3>Heading Level 3</h3>
  <h4>Heading Level 4</h4>
  <h5>Heading Level 5</h5>
  <h6>Heading Level 6</h6>

</body>
</html>
```

**Expected output:**
```
Heading Level 1    ← very large, bold
Heading Level 2    ← large, bold
Heading Level 3    ← medium-large, bold
Heading Level 4    ← medium, bold
Heading Level 5    ← small, bold
Heading Level 6    ← smallest, bold
```

**Self-check:** Notice that `<h1>` is noticeably larger than `<h6>`. In real websites, `<h1>` is used for the page's main title, `<h2>` for main sections, `<h3>` for sub-sections, and so on.

---

## Part 7 — Mini Project: Build a Class Notes Web Page

This project combines everything you have learned in this lesson.

**Project Goal:** Build a real-looking single-page class notes document for one of your subjects (e.g. Mathematics, Biology, History, or Technology).

---

### Stage 1: Setup — Create the File

Create a new file called `class-notes.html`.

Add the required HTML skeleton:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Class Notes — Mathematics</title>
</head>
<body>

  <!-- All your content goes here -->

</body>
</html>
```

**New concept — HTML comments:**  
The `<!-- ... -->` syntax is a **comment**. Comments are notes for the developer — the browser completely ignores them. They are invisible on the finished page. They are very useful for organising your code.

**Milestone output:** Opening this file in the browser should show a blank white page with the tab title "Class Notes — Mathematics". ✅

---

### Stage 2: Core Logic — Add Subject Content

Now fill in the body with your notes content:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Class Notes — Mathematics</title>
</head>
<body>

  <h1>Mathematics Class Notes</h1>
  <p>Subject: Mathematics. Term: Second Term. Year: 2025.</p>

  <h2>Topic 1: Number Systems</h2>
  <p>A number system is a way of representing numbers. The most common system we use daily is the decimal system (base 10).</p>

  <h3>Types of Numbers</h3>
  <p>Natural numbers are used for counting: 1, 2, 3, 4...</p>
  <p>Integers include zero and negative numbers: ...-2, -1, 0, 1, 2...</p>
  <p>Real numbers include decimals and fractions.</p>

  <h2>Topic 2: Basic Algebra</h2>
  <p>Algebra uses letters (variables) to represent unknown values. For example, in the equation x + 5 = 10, the variable x represents the number 5.</p>

  <h3>Key Algebra Terms</h3>
  <p>A variable is a letter representing an unknown value.</p>
  <p>An expression is a combination of numbers and variables, like 3x + 2.</p>
  <p>An equation is two expressions set equal to each other, like 3x + 2 = 11.</p>

</body>
</html>
```

**Milestone output:**
```
Mathematics Class Notes        ← large h1

Subject: Mathematics. Term: Second Term. Year: 2025.

Topic 1: Number Systems        ← medium h2

A number system is a way of representing numbers...

Types of Numbers               ← smaller h3

Natural numbers are used for counting: 1, 2, 3, 4...

... (rest of content)
```

---

### Stage 3: Enhancements — Add a Page Header and Closing Note

Now improve the page by adding an introductory note and a closing line:

```html
<body>

  <h1>Mathematics Class Notes</h1>
  <p><strong>Student:</strong> Your Name Here</p>
  <p><strong>Subject:</strong> Mathematics &nbsp; | &nbsp; <strong>Term:</strong> Second Term &nbsp; | &nbsp; <strong>Year:</strong> 2025</p>

  <!-- ... rest of your notes ... -->

  <h2>End of Notes</h2>
  <p>These notes were created using HTML. Last updated: April 2025.</p>

</body>
```

**New concept — `<strong>`:**  
The `<strong>` tag makes text **bold**. The text between `<strong>` and `</strong>` appears heavier and more important.

**Expected output for the header section:**
```
Mathematics Class Notes

Student: Your Name Here
Subject: Mathematics | Term: Second Term | Year: 2025
```

---

### Stage 4: Reflection Questions

After completing the project, ask yourself:

1. Could you build this same document in Microsoft Word? How is the HTML version different?
2. What would happen if someone in another country opened your HTML file in their browser? Would it look the same?
3. Can you think of a real website that uses headings and paragraphs exactly like this? (Hint: any news article or Wikipedia page.)
4. What other information could you add to your class notes using only the tags you've learned today?

**Optional Advanced Feature:** Add a second page called `class-notes-science.html` for another subject. Can you make both pages using the same structure?

---

## Part 8 — Common Beginner Mistakes

Study these carefully. Every beginner makes these mistakes at least once.

---

### Mistake 1: Forgetting the Closing Tag

❌ **Wrong:**
```html
<p>This paragraph has no closing tag.
<p>This is the next paragraph.</p>
```

✅ **Correct:**
```html
<p>This paragraph is properly closed.</p>
<p>This is the next paragraph.</p>
```

**Why this matters:** Browsers are forgiving and may still display the page, but missing closing tags can cause unpredictable layout problems, especially when you add more content later.

---

### Mistake 2: Using a Forward Slash in the Opening Tag

❌ **Wrong:**
```html
</p>My paragraph text.</p>
```

✅ **Correct:**
```html
<p>My paragraph text.</p>
```

**Rule:** The opening tag has NO slash: `<p>`. The closing tag has a slash: `</p>`.

---

### Mistake 3: Saving the File with the Wrong Extension

❌ **Wrong:** Saving as `index.txt` (it saves as plain text, browser won't recognise it as HTML)

✅ **Correct:** Save as `index.html` or `index.htm`

**In Notepad:** Always choose "All Files (*.*)" in the "Save as type" dropdown before typing the filename with `.html`, otherwise Windows adds `.txt` to the end.

---

### Mistake 4: Forgetting `<!DOCTYPE html>`

❌ **Wrong:**
```html
<html>
<body>
<p>My page.</p>
</body>
</html>
```

✅ **Correct:**
```html
<!DOCTYPE html>
<html>
<body>
<p>My page.</p>
</body>
</html>
```

**Why this matters:** Without `<!DOCTYPE html>`, older browsers may switch into "quirks mode" and display your page incorrectly.

---

### Mistake 5: Putting Visible Content in the `<head>`

❌ **Wrong:**
```html
<head>
  <title>My Page</title>
  <p>This text is in the wrong place!</p>  <!-- ← This belongs in <body> -->
</head>
```

✅ **Correct:**
```html
<head>
  <title>My Page</title>
</head>
<body>
  <p>This text is in the right place.</p>
</body>
```

**Rule:** All visible content goes inside `<body>`. The `<head>` section is only for metadata (information *about* the page, not the page content itself).

---

### Mistake 6: Using TextEdit in "Rich Text" Mode on Mac

❌ **Wrong:** Saving an HTML file from TextEdit without switching to Plain Text mode — the file will contain hidden formatting codes that will break your HTML.

✅ **Correct:** Go to TextEdit Preferences → Format → Plain Text. Then create a new document before writing HTML.

---

### Mistake 7: Wrong Tag Nesting Order

❌ **Wrong:**
```html
<h1><p>Mixed up tags</h1></p>
```

✅ **Correct:**
```html
<h1>Heading text</h1>
<p>Paragraph text</p>
```

**Rule:** Tags must be properly nested — the last tag opened must be the first tag closed. Think of it like opening and closing brackets: `( [ ] )` not `( [ ) ]`.

---

## Part 9 — Reflection Questions

Think about these before moving to the next lesson:

1. In your own words, what is the difference between an HTML *tag* and an HTML *element*?
2. Why does the `<title>` tag go inside `<head>` instead of `<body>`?
3. If a browser sees `<h1>Hello</h1>`, what does it do with the `<h1>` and `</h1>` parts?
4. You want to display the text "Welcome!" on a web page in a very large, prominent style. Which HTML tag would you use?
5. What is the purpose of `<!DOCTYPE html>`?
6. Why should you save your HTML file as UTF-8 encoding?
7. Can you use a regular Microsoft Word document as a website? Why or why not?
8. What is the difference between Notepad and Visual Studio Code as tools for writing HTML?

---

## Part 10 — Completion Checklist

Before moving to the next lesson, make sure you can check off every item:

- [ ] I can explain what HTML stands for and what it does
- [ ] I understand what a tag, an element, and an attribute are (concept of attributes to be expanded in Lesson 2)
- [ ] I know the required structure of every HTML page: `<!DOCTYPE html>`, `<html>`, `<head>`, `<title>`, `<body>`
- [ ] I can explain the difference between `<head>` and `<body>`
- [ ] I know what `<h1>` through `<h6>` do
- [ ] I know what `<p>` does
- [ ] I know what `<br>` does and why it has no closing tag
- [ ] I have successfully opened Notepad (or TextEdit) and written an HTML file
- [ ] I have saved the file as `.html` with UTF-8 encoding
- [ ] I have opened my HTML file in a browser and seen the output
- [ ] I understand and can avoid the 7 common beginner mistakes listed above
- [ ] I have completed the "About Me" exercise
- [ ] I have completed the Mini Project (Class Notes page)

---

## Lesson Summary

Here is everything covered in this lesson in a compact reference:

**What HTML Is:**
HTML (HyperText Markup Language) is the standard language for creating web pages. It uses *tags* to label and structure content so browsers know how to display it.

**Core Structure of Every HTML Page:**
```html
<!DOCTYPE html>       <!-- Required: tells browser it's HTML5 -->
<html>                <!-- Root container for the whole page -->
<head>                <!-- Invisible metadata section -->
  <title>...</title>  <!-- Sets the browser tab title -->
</head>
<body>                <!-- All VISIBLE content goes here -->
  ...
</body>
</html>
```

**Tags Learned in This Lesson:**

| Tag | Purpose | Empty? |
|---|---|---|
| `<!DOCTYPE html>` | Declares HTML5 document | Yes (declaration) |
| `<html>` | Root element | No |
| `<head>` | Metadata container | No |
| `<title>` | Browser tab title | No |
| `<body>` | Visible page content | No |
| `<h1>` to `<h6>` | Headings (largest to smallest) | No |
| `<p>` | Paragraph | No |
| `<br>` | Line break | Yes (no closing tag) |
| `<!-- comment -->` | Developer note (invisible) | Yes |
| `<strong>` | Bold text | No |

**Editor Setup:**
- Windows: Use Notepad, save as `.html`, encoding UTF-8
- Mac: Use TextEdit in Plain Text mode, save as `.html`, encoding UTF-8
- Online: Use the W3Schools "Try it Yourself" editor at w3schools.com

**Real-World Connection:**
Every website you visit — from news portals and social media to government services and educational platforms — is built on a foundation of HTML. The skills in this lesson are the first step toward building anything on the web, whether it is a personal portfolio, a small business website, a data dashboard, or a full web application.

---

> **Next Up — Lesson 02:** In the next lesson you will learn about HTML Elements in depth, HTML Attributes (extra information you can add to tags), and how to create links, images, and formatted text. You will begin seeing how real web pages are assembled.

---

*Sources: W3Schools HTML Tutorial — https://www.w3schools.com/html/*
