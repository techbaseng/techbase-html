---
render_with_liquid: false
title: "Lesson 2 — HTML Basic Examples: Documents, Headings, Paragraphs, Links & Images"
nav_order: 2
---

## Lesson Introduction

Welcome to Lesson 2! In the previous lesson you learned what HTML is and how to set up your editor. Now it is time to write your **very first real HTML code**.

By the end of this lesson you will be able to:

- Understand the skeleton of every HTML document
- Use the `<!DOCTYPE>` declaration and know exactly why it exists
- Create headings of different sizes using `<h1>` through `<h6>`
- Write paragraphs using the `<p>` tag
- Build clickable links using the `<a>` tag and the `href` attribute
- Display images using the `<img>` tag and its key attributes
- View the hidden HTML source code of any website in your browser

Think of this lesson as learning to read a recipe card before cooking. Every web page you will ever build follows the same basic structure you will learn right here.

> **Real-world connection:** Every website you use every day — news sites, social media, school portals, e-commerce stores — is built on exactly the foundation you are about to learn.

---

## Prerequisite Concepts

Before we dive into examples, let us make sure you understand two ideas that are used throughout this lesson.

### What is an HTML Tag?

An **HTML tag** is a special keyword wrapped inside angle brackets `< >`. Tags tell the browser *what kind of content* is coming.

Most tags come in **pairs**:

- An **opening tag** starts the content: `<tagname>`
- A **closing tag** ends the content: `</tagname>` ← notice the forward slash `/`

```html
<p>This is a paragraph.</p>
```

Here:
- `<p>` is the opening tag — it says "a paragraph starts here"
- `This is a paragraph.` is the content
- `</p>` is the closing tag — it says "the paragraph ends here"

Think of tags like a sandwich: the opening and closing tags are the two slices of bread, and the content is the filling in between.

### What is an HTML Attribute?

An **attribute** gives extra information to a tag. It always goes inside the **opening tag**, written as `name="value"`.

```html
<a href="https://www.google.com">Visit Google</a>
```

Here:
- `<a>` is the tag (used for links)
- `href="https://www.google.com"` is an **attribute** — it tells the browser *where* the link goes
- `Visit Google` is the clickable text the user sees
- `</a>` closes the link

> You do not need to memorise all attributes right now. You will learn the most important ones naturally as you work through each concept.

---

## Part 1 — The HTML Document Structure

### What Is an HTML Document?

An HTML document is just a plain text file that follows a specific set of rules. When your browser opens it, it reads those rules and draws the web page on your screen.

Think of it like this: a book has a cover, a table of contents, and chapters. An HTML document has its own required parts too.

Every complete HTML document must have these three things:

1. A **document type declaration** at the very top
2. An opening and closing `<html>` tag that wraps everything
3. A `<body>` tag that holds all the content the user sees

---

### The `<!DOCTYPE html>` Declaration

#### What is it?

`<!DOCTYPE html>` is a special instruction at the very top of every HTML file. It is **not** an HTML tag — it is a declaration.

#### Why does it exist?

In the early days of the web, there were many different versions of HTML, and browsers sometimes displayed them differently. The `<!DOCTYPE>` tells the browser: **"This file uses the modern HTML5 standard. Please display it correctly."**

Without it, some older browsers might go into a strange mode called "quirks mode" and display your page incorrectly — things might look broken or misaligned.

#### Rules to remember

- It must appear **once only**, at the very top of the file — before everything else
- It is **not case sensitive** — `<!DOCTYPE html>`, `<!doctype html>`, and `<!Doctype HTML>` all work
- For modern HTML5 (which is what everyone uses today), it is simply: `<!DOCTYPE html>`

#### Simple example

```html
<!DOCTYPE html>
```

**Expected output:** Nothing visible on the page — it is purely an instruction for the browser, not content for the user.

> **Thinking prompt:** What do you think would happen if you put `<!DOCTYPE html>` in the middle of your file instead of the top?
> Answer: Browsers would likely still work, but it is bad practice. Other tools and validators would reject your code as invalid.

---

### The Full HTML Document Skeleton

Now let us look at the complete, minimum structure every valid HTML document must have:

```html
<!DOCTYPE html>
<html>
<body>

<h1>My First Heading</h1>
<p>My first paragraph.</p>

</body>
</html>
```

Let us go through every single line:

| Line | Code | What it does |
|------|------|--------------|
| 1 | `<!DOCTYPE html>` | Tells the browser this is HTML5 |
| 2 | `<html>` | Opens the HTML document — everything lives inside here |
| 3 | `<body>` | Opens the body — all visible content goes here |
| 4 | `<h1>My First Heading</h1>` | A large heading (you will learn more in the next section) |
| 5 | `<p>My first paragraph.</p>` | A paragraph of text |
| 6 | `</body>` | Closes the body section |
| 7 | `</html>` | Closes the entire HTML document |

**Expected output in browser:**

```
My First Heading        ← displayed large and bold
My first paragraph.     ← displayed as normal-sized text below
```

> **Analogy:** The `<html>` tag is like the walls of a house — everything must be inside them. The `<body>` tag is like the living room — it holds everything the visitor sees when they walk in.

#### Why is the `<body>` tag needed?

HTML documents actually have two main sections:

- **`<head>`** — Contains invisible information about the page (title, settings, links to style files). The user does not see this directly.
- **`<body>`** — Contains everything the user **sees and interacts with** on the page.

In this lesson we are focusing entirely on what goes inside `<body>`. The `<head>` section will be covered in a later lesson.

---

## Part 2 — HTML Headings

### What are Headings?

**Headings** are titles and subtitles. Just like a newspaper has a big bold headline at the top, then smaller sub-headlines for each section, HTML gives you six levels of headings.

HTML headings use the tags `<h1>` through `<h6>`:

- `<h1>` = the biggest, most important heading (like the title of the whole page)
- `<h2>` = a major section heading
- `<h3>` = a subsection under h2
- `<h4>`, `<h5>`, `<h6>` = progressively smaller and less important headings

#### Why do headings matter?

Headings are not just for making text big. They serve two critical purposes:

1. **Readability** — They help users quickly scan and understand the structure of a page.
2. **SEO (Search Engine Optimisation)** — Search engines like Google read your headings to understand what your page is about. A good `<h1>` helps Google rank your page correctly.

---

### Simple Example — All Six Heading Levels

```html
<!DOCTYPE html>
<html>
<body>

<h1>This is heading 1</h1>
<h2>This is heading 2</h2>
<h3>This is heading 3</h3>
<h4>This is heading 4</h4>
<h5>This is heading 5</h5>
<h6>This is heading 6</h6>

</body>
</html>
```

**Expected output in browser:**

```
This is heading 1    ← very large, bold
This is heading 2    ← slightly smaller, bold
This is heading 3    ← medium size, bold
This is heading 4    ← smaller, bold
This is heading 5    ← even smaller, bold
This is heading 6    ← smallest, bold
```

Each heading automatically appears on its own line, and the browser adds space above and below it.

---

### Second Example — Using Headings Like a Real Web Page

Here is how headings work in a real-world context — imagine a science article:

```html
<!DOCTYPE html>
<html>
<body>

<h1>The Solar System</h1>

<h2>Inner Planets</h2>
<h3>Mercury</h3>
<h3>Venus</h3>
<h3>Earth</h3>

<h2>Outer Planets</h2>
<h3>Jupiter</h3>
<h3>Saturn</h3>

</body>
</html>
```

**Expected output in browser:**

```
The Solar System              ← biggest heading (page title)

  Inner Planets               ← medium heading (section)
    Mercury                   ← smaller heading (subsection)
    Venus
    Earth

  Outer Planets
    Jupiter
    Saturn
```

> **Thinking prompt:** Why should there only be ONE `<h1>` per page? Think about the title of a book — a book has one title, not five.

---

### Common Beginner Mistake with Headings

**Mistake:** Using `<h1>` just because you want big text, not because it is the page title.

```html
<!-- WRONG: Using h1 just to make text big -->
<h1>Welcome!</h1>
<h1>About Us</h1>
<h1>Contact</h1>
```

**Why this is wrong:** Every section is now equally the "most important thing" on the page, which confuses both users and search engines.

```html
<!-- CORRECT: One h1 for the title, then h2 for sections -->
<h1>My Business Website</h1>
<h2>Welcome!</h2>
<h2>About Us</h2>
<h2>Contact</h2>
```

**Expected output:** `My Business Website` appears as the largest heading, with `Welcome!`, `About Us`, and `Contact` appearing slightly smaller beneath it.

---

## Part 3 — HTML Paragraphs

### What is the `<p>` Tag?

The `<p>` tag defines a **paragraph** of text. Every time you use `<p>...</p>`, the browser automatically:

- Puts the content on a new line
- Adds space above and below it (called a margin)

This means paragraphs are automatically separated from each other, even without you pressing Enter multiple times.

---

### Simple Example — Two Paragraphs

```html
<!DOCTYPE html>
<html>
<body>

<p>This is a paragraph.</p>
<p>This is another paragraph.</p>

</body>
</html>
```

**Expected output in browser:**

```
This is a paragraph.

This is another paragraph.
```

Notice the gap between the two paragraphs — the browser added that automatically.

---

### Second Example — Paragraphs in a Real Context

```html
<!DOCTYPE html>
<html>
<body>

<h1>About Lagos</h1>

<p>Lagos is the largest city in Nigeria and one of the most populous cities in Africa.</p>

<p>It is a major financial centre and home to a vibrant culture, with world-class music, art, and cuisine.</p>

<p>The city sits on the Atlantic Ocean and is known for its bustling markets and creative industries.</p>

</body>
</html>
```

**Expected output in browser:**

```
About Lagos

Lagos is the largest city in Nigeria and one of the most
populous cities in Africa.

It is a major financial centre and home to a vibrant culture,
with world-class music, art, and cuisine.

The city sits on the Atlantic Ocean and is known for its
bustling markets and creative industries.
```

---

### Common Beginner Mistake with Paragraphs

**Mistake 1:** Trying to create space by pressing Enter inside HTML code.

```html
<!-- WRONG: Pressing Enter does NOT create a new paragraph -->
<p>First line
Second line</p>
```

**What the browser actually shows:**

```
First line Second line
```

The browser ignores extra line breaks inside HTML code. You must use a new `<p>` tag.

```html
<!-- CORRECT: Use separate p tags for separate paragraphs -->
<p>First paragraph.</p>
<p>Second paragraph.</p>
```

**Mistake 2:** Forgetting to close the `<p>` tag.

```html
<!-- RISKY: Missing closing tag -->
<p>This paragraph has no closing tag.
<p>This is the second paragraph.
```

While browsers are forgiving and may still display this, it is bad practice and can cause layout problems on complex pages. Always close your tags.

---

## Part 4 — HTML Links

### What is the `<a>` Tag?

The `<a>` tag creates a **hyperlink** — a piece of clickable text (or image) that takes the user to another page or website.

`<a>` stands for **anchor**. Think of a ship's anchor: it connects the ship to a fixed point. An HTML anchor connects your page to another destination.

### The `href` Attribute

The `href` attribute (short for **Hypertext REFerence**) holds the **URL** (the web address) that the link goes to.

```html
<a href="https://www.w3schools.com">This is a link</a>
```

Breaking this down word by word:

| Part | Meaning |
|------|---------|
| `<a` | Opens the anchor tag |
| `href=` | Says "the destination of this link is..." |
| `"https://www.w3schools.com"` | The URL — where the link goes when clicked |
| `>` | Closes the opening tag |
| `This is a link` | The clickable text the user sees |
| `</a>` | Closes the anchor tag |

**Expected output in browser:**

```
This is a link    ← shown in blue with an underline (default browser style)
```

When you click it, the browser navigates to `https://www.w3schools.com`.

> **Real-world connection:** Every "Click here", "Read more", "Buy now", or "Download" button you have ever clicked on any website is built with the `<a>` tag.

---

### Simple Example — A Basic Link

```html
<!DOCTYPE html>
<html>
<body>

<p>Visit my favourite website:</p>
<a href="https://www.google.com">Go to Google</a>

</body>
</html>
```

**Expected output:**

```
Visit my favourite website:
Go to Google    ← blue, underlined, clickable
```

---

### Second Example — Multiple Links

```html
<!DOCTYPE html>
<html>
<body>

<h1>Useful Websites</h1>

<p><a href="https://www.google.com">Google</a> - Search engine</p>
<p><a href="https://www.wikipedia.org">Wikipedia</a> - Free encyclopedia</p>
<p><a href="https://www.w3schools.com">W3Schools</a> - Learn web development</p>

</body>
</html>
```

**Expected output:**

```
Useful Websites

Google - Search engine
Wikipedia - Free encyclopedia
W3Schools - Learn web development
```

(Google, Wikipedia, and W3Schools each appear as clickable blue links.)

> **Thinking prompt:** What do you think happens if you leave out the `href` attribute? Try it! You will get a link that looks like normal text — it is not clickable because there is no destination.

---

### Common Beginner Mistakes with Links

**Mistake 1:** Forgetting `https://` at the start of the URL.

```html
<!-- WRONG -->
<a href="www.google.com">Google</a>

<!-- CORRECT -->
<a href="https://www.google.com">Google</a>
```

Without `https://`, the browser treats it as a **relative path** — it looks for a file called `www.google.com` in the same folder as your HTML file, not on the internet.

**Mistake 2:** Putting the URL outside the quotes.

```html
<!-- WRONG -->
<a href=https://www.google.com>Google</a>

<!-- CORRECT -->
<a href="https://www.google.com">Google</a>
```

Always wrap attribute values in double quotes.

---

## Part 5 — HTML Images

### What is the `<img>` Tag?

The `<img>` tag displays an image on your web page.

**Important:** `<img>` is a **self-closing tag** — it has no closing tag. This is because it has no "content" between tags; it simply embeds a file.

```html
<img src="w3schools.jpg" alt="W3Schools Logo" width="104" height="142">
```

Let us break down every attribute:

| Attribute | What it does | Example value |
|-----------|-------------|---------------|
| `src` | The **source** — the file name or URL of the image | `"photo.jpg"` or `"https://example.com/img.png"` |
| `alt` | **Alternative text** — describes the image in words | `"A smiling dog"` |
| `width` | Sets the width of the image in pixels | `"200"` |
| `height` | Sets the height of the image in pixels | `"150"` |

---

### Why is `alt` Text So Important?

The `alt` attribute serves three critical purposes:

1. **Accessibility:** Screen readers (used by visually impaired users) read the `alt` text aloud so the user understands what the image shows.
2. **Broken images:** If the image file cannot be found (e.g. wrong file name), the browser displays the `alt` text instead so the user knows what was supposed to be there.
3. **SEO:** Search engines cannot "see" images, so they read the `alt` text to understand what the image is about.

> **Analogy:** The `alt` attribute is like a label on a jar. Even if the jar is empty (image not loading), the label tells you what was supposed to be inside.

---

### Simple Example — Displaying a Local Image

```html
<!DOCTYPE html>
<html>
<body>

<img src="cat.jpg" alt="A fluffy orange cat" width="300" height="200">

</body>
</html>
```

**Expected output:**

```
[A photo of a fluffy orange cat, 300 pixels wide and 200 pixels tall]
```

(If `cat.jpg` is saved in the same folder as your HTML file, it will appear. If not, the text `A fluffy orange cat` appears in its place.)

---

### Second Example — Image from the Internet

You can also use a full web address (URL) for the `src`:

```html
<!DOCTYPE html>
<html>
<body>

<h1>My Favourite Animal</h1>

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Cat03.jpg/320px-Cat03.jpg"
     alt="A cat sitting on a surface"
     width="320"
     height="214">

<p>Cats are one of the most popular pets in the world.</p>

</body>
</html>
```

**Expected output:**

```
My Favourite Animal

[Photo of a cat]

Cats are one of the most popular pets in the world.
```

> **Thinking prompt:** What happens if you change the `width` to `600` but keep `height` at `214`? Try it! The image will look stretched horizontally. To avoid distortion, you can set only `width` and leave `height` out — the browser will scale it proportionally.

---

### Common Beginner Mistakes with Images

**Mistake 1:** Wrong file name or wrong path.

```html
<!-- WRONG: File name is wrong -->
<img src="Cat.jpg" alt="A cat">

<!-- If the file is actually named "cat.jpg" (lowercase c), 
     it won't display on case-sensitive systems like Linux servers -->

<!-- CORRECT: Match the exact file name and capitalisation -->
<img src="cat.jpg" alt="A cat">
```

**Mistake 2:** Forgetting the `alt` attribute.

```html
<!-- WRONG: Missing alt attribute -->
<img src="logo.png" width="100" height="50">

<!-- CORRECT: Always include alt text -->
<img src="logo.png" alt="Company logo" width="100" height="50">
```

**Mistake 3:** Using a closing tag.

```html
<!-- WRONG: img does not need a closing tag -->
<img src="photo.jpg" alt="Photo"></img>

<!-- CORRECT: img is self-closing -->
<img src="photo.jpg" alt="Photo">
```

---

## Part 6 — How to View HTML Source Code

This is a powerful skill that professional web developers use every single day. You can look at the HTML code behind **any website in the world**.

### Method 1 — View Full Page Source

On any web page in your browser:

- **Windows/Linux:** Press `Ctrl + U`
- **Mac:** Press `Cmd + Option + U`
- Or: Right-click anywhere on the page → select **"View Page Source"**

A new browser tab opens showing the complete raw HTML code of the entire page.

**Why is this useful?** You can learn by studying how real websites are built. If you see something on a website you like, you can view the source to see how it was coded.

### Method 2 — Inspect a Specific Element

Right-click on any specific element on a web page (a button, an image, a heading) → select **"Inspect"** (or "Inspect Element").

A panel opens showing:
- The **HTML** of that specific element on the left
- The **CSS styling** applied to it on the right

You can even **edit the HTML and CSS** live in the browser to experiment — your changes only affect your own browser view and reset when you reload the page.

> **Try it now:** Open any website, right-click on the main heading, and select "Inspect". You will see the `<h1>` or `<h2>` tag highlighted. This is exactly what you are learning to write.

---

## Guided Practice Exercises

Now it is time to practice everything you have learned. Work through these exercises in order.

---

### Exercise 1 — Your First Complete HTML Document

**Objective:** Build a valid HTML document from memory using the correct structure.

**Scenario:** You are creating the home page for a school project about your favourite subject.

**Steps:**

1. Open your text editor (from Lesson 1)
2. Type the following code exactly:

```html
<!DOCTYPE html>
<html>
<body>

<h1>My Favourite Subject: Mathematics</h1>

<h2>Why I Love Maths</h2>
<p>Mathematics helps us understand the patterns in the world around us.</p>
<p>From counting money to building bridges, maths is everywhere.</p>

<h2>My Favourite Topics</h2>
<p>I enjoy algebra, geometry, and statistics the most.</p>

</body>
</html>
```

3. Save the file as `maths.html`
4. Open it in your browser by double-clicking the file

**Expected output:**

```
My Favourite Subject: Mathematics    ← large bold heading

Why I Love Maths                     ← medium heading

Mathematics helps us understand the patterns in the world around us.

From counting money to building bridges, maths is everywhere.

My Favourite Topics

I enjoy algebra, geometry, and statistics the most.
```

**Self-check questions:**
- Does `<!DOCTYPE html>` appear on the very first line?
- Is all your content inside `<body>...</body>`?
- Does every `<h2>` have a matching `</h2>`?
- Does every `<p>` have a matching `</p>`?

---

### Exercise 2 — Adding Links to Your Page

**Objective:** Add three clickable links to your page.

**Scenario:** You are adding a "Useful Resources" section to your maths page.

Add the following code just before `</body>`:

```html
<h2>Useful Resources</h2>
<p><a href="https://www.khanacademy.org">Khan Academy</a> - Free maths lessons</p>
<p><a href="https://www.mathisfun.com">Math is Fun</a> - Explanations and games</p>
<p><a href="https://www.wolframalpha.com">Wolfram Alpha</a> - Solve any maths problem</p>
```

**Expected output:**

```
Useful Resources

Khan Academy - Free maths lessons
Math is Fun - Explanations and games
Wolfram Alpha - Solve any maths problem
```

(Each of the three names is a clickable blue link.)

**Self-check questions:**
- Does each link have `href="..."` with a complete URL including `https://`?
- Is the clickable text between `<a>` and `</a>`?
- Did you close each `<a>` tag with `</a>`?

---

### Exercise 3 — Adding an Image

**Objective:** Display an image on your page.

**Scenario:** You want to add a visual to make your page more engaging.

**Option A — Use a local image:**
1. Find any image on your computer (e.g., `photo.jpg`)
2. Copy it into the same folder as your `maths.html` file
3. Add this code after your `<h1>` heading:

```html
<img src="photo.jpg" alt="A descriptive label for the image" width="400" height="250">
```

**Option B — Use an online image:**

```html
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/21/Simple_algebra_-_unknown_quantities.svg/320px-Simple_algebra_-_unknown_quantities.svg.png"
     alt="An algebra equation diagram"
     width="320"
     height="240">
```

**Expected output:**

```
[Your image appears on the page at 320 × 240 pixels]
```

**Self-check questions:**
- Does your `<img>` tag have a `src` attribute?
- Does it have an `alt` attribute with a meaningful description?
- Does it have `width` and `height` attributes?
- Is there NO closing `</img>` tag?

**Optional what-if challenge:** What happens if you remove the `width` attribute entirely? Try it and observe how the browser behaves.

---

### Exercise 4 — The Complete Profile Page

**Objective:** Combine everything you have learned into one page.

**Scenario:** Build a simple "About Me" page that uses all five elements from this lesson: document structure, headings, paragraphs, a link, and an image.

```html
<!DOCTYPE html>
<html>
<body>

<h1>About Me</h1>

<img src="https://via.placeholder.com/150" alt="My profile photo" width="150" height="150">

<h2>Who I Am</h2>
<p>My name is [your name]. I am a student learning web development.</p>
<p>I live in [your city] and I am passionate about technology and problem-solving.</p>

<h2>My Hobbies</h2>
<p>I enjoy reading, coding, football, and listening to music.</p>

<h2>My Goal</h2>
<p>I want to build websites and applications that help people in my community.</p>

<h2>Find Me Online</h2>
<p><a href="https://www.linkedin.com">Visit LinkedIn</a> to connect professionally.</p>

</body>
</html>
```

**Expected output:**

```
About Me

[Placeholder profile image]

Who I Am

My name is [your name]. I am a student learning web development.
I live in [your city] and I am passionate about technology and problem-solving.

My Hobbies

I enjoy reading, coding, football, and listening to music.

My Goal

I want to build websites and applications that help people in my community.

Find Me Online

Visit LinkedIn     ← clickable link
```

---

## HTML Basics Code Challenges

The following challenges test your understanding of basic HTML. Read each challenge carefully, write the code yourself first, then check the solution beneath it.

---

### Challenge 1 — Fix the Broken Document

The following HTML has **three errors**. Can you find and fix all three?

```html
<!DOCTYPE html>
<html>
<body>

<h1>My First Page
<p>Welcome to my website.</p>
<p>This page was made with HTML</p>

</html>
```

**Hints:**
- One tag is missing its closing tag
- One section is missing entirely
- One sentence is missing punctuation (though HTML won't care about this one — your reader will!)

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>                            <!-- Error 1 fixed: </body> was missing -->

<h1>My First Page</h1>           <!-- Error 2 fixed: </h1> closing tag was missing -->
<p>Welcome to my website.</p>
<p>This page was made with HTML.</p>   <!-- Error 3 fixed: missing full stop (punctuation) -->

</body>                           <!-- Added missing </body> -->
</html>
```

---

### Challenge 2 — Build a Product Page

**Task:** Write the HTML for a simple product page for a phone. It must include:

- A `<!DOCTYPE html>` declaration
- A page title using `<h1>` that says "SmartPhone Pro X"
- A `<h2>` heading saying "Description"
- A `<p>` with a short description of the phone
- A `<h2>` heading saying "Features"
- Three separate `<p>` tags listing three features
- An `<img>` tag with `src`, `alt`, `width`, and `height` attributes
- A link to `https://www.gsmarena.com` with the text "Read Reviews"

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>

<h1>SmartPhone Pro X</h1>

<img src="phone.jpg" alt="SmartPhone Pro X product photo" width="300" height="400">

<h2>Description</h2>
<p>The SmartPhone Pro X is the latest flagship device with a stunning display and all-day battery life.</p>

<h2>Features</h2>
<p>6.7-inch Super AMOLED display with 120Hz refresh rate.</p>
<p>50MP triple camera system with optical zoom.</p>
<p>5000mAh battery with 65W fast charging.</p>

<p><a href="https://www.gsmarena.com">Read Reviews</a></p>

</body>
</html>
```

---

### Challenge 3 — Heading Hierarchy

**Task:** A student wrote the following code. Identify what is wrong with the heading structure and rewrite it correctly.

```html
<!-- BROKEN: What is wrong here? -->
<h3>My Blog</h3>
<h1>Latest Post</h1>
<h5>Introduction</h5>
<h2>Main Content</h2>
```

**What is wrong:** The headings are completely out of order. `<h1>` is not the page title but a subsection. `<h5>` skips straight from `<h1>` without using `<h2>`, `<h3>`, `<h4>`.

**Corrected version:**

```html
<h1>My Blog</h1>
<h2>Latest Post</h2>
<h3>Introduction</h3>
<h3>Main Content</h3>
```

**Expected output:**

```
My Blog                ← biggest (page title)
  Latest Post          ← second biggest (section)
    Introduction       ← smaller (subsection)
    Main Content       ← smaller (subsection)
```

---

### Challenge 4 — Image and Link Together

**Task:** Create an image that is also a clickable link. When the user clicks the image, it takes them to `https://www.nasa.gov`.

**Hint:** You can nest the `<img>` tag *inside* the `<a>` tag.

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>

<h1>Space Exploration</h1>

<a href="https://www.nasa.gov">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e5/NASA_logo.svg/200px-NASA_logo.svg.png"
       alt="NASA logo - click to visit NASA website"
       width="200"
       height="200">
</a>

<p>Click the NASA logo above to visit the official NASA website.</p>

</body>
</html>
```

**Expected output:**

```
Space Exploration

[NASA logo image — clicking it opens nasa.gov]

Click the NASA logo above to visit the official NASA website.
```

---

## Mini Project — Build Your First Personal Web Page

Now you will bring everything together into one complete, polished personal web page.

### Project Overview

**Project name:** My Personal Introduction Page  
**Goal:** A complete, valid HTML page about yourself that uses all five core concepts from this lesson.

---

### Stage 1 — Setup (The Document Skeleton)

Create a new file called `index.html` and write the document structure:

```html
<!DOCTYPE html>
<html>
<body>

<!-- Your content will go here in the next stages -->

</body>
</html>
```

**Milestone output:** Open the file in a browser. It should show a completely blank white page — no errors.

> The `<!-- ... -->` syntax is an HTML comment. It is a note for the developer and is completely invisible to the user in the browser. You will learn more about comments in a later lesson.

---

### Stage 2 — Core Content (Headings and Paragraphs)

Now add your personal information using headings and paragraphs:

```html
<!DOCTYPE html>
<html>
<body>

<h1>Hello, I Am [Your Full Name]</h1>

<h2>About Me</h2>
<p>I am [your age] years old and I live in [your city], [your country].</p>
<p>I am currently studying [your course or subject] and learning to build websites.</p>

<h2>My Interests</h2>
<p>I love [interest 1], [interest 2], and [interest 3].</p>
<p>In my free time, I enjoy [hobby].</p>

<h2>My Career Goal</h2>
<p>I want to become a [your dream career] and use technology to [what you want to achieve].</p>

</body>
</html>
```

**Milestone output:**

```
Hello, I Am [Your Name]    ← large bold heading

About Me

I am [age] years old and I live in [city], [country].
I am currently studying [course] and learning to build websites.

My Interests

I love [interest 1], [interest 2], and [interest 3].
In my free time, I enjoy [hobby].

My Career Goal

I want to become a [career] and use technology to [goal].
```

---

### Stage 3 — Enhancement (Image and Links)

Now add a photo and helpful links:

```html
<!-- Add this just after your <h1> line -->
<img src="https://via.placeholder.com/180x180.png?text=My+Photo"
     alt="A placeholder for my profile photo"
     width="180"
     height="180">

<!-- Add this section just before </body> -->
<h2>Connect With Me</h2>
<p>Find me on <a href="https://www.linkedin.com">LinkedIn</a>.</p>
<p>Learn web development at <a href="https://www.w3schools.com">W3Schools</a> — where I am learning from.</p>
<p>Send me an email: <a href="mailto:youremail@example.com">youremail@example.com</a></p>
```

> **New concept — `mailto:` links:** If you use `mailto:someone@example.com` as the `href`, clicking the link opens the user's email app with that address pre-filled. This is a handy trick for contact pages.

---

### Stage 4 — Final Output

Your completed `index.html` should look like this (with your own information filled in):

```html
<!DOCTYPE html>
<html>
<body>

<h1>Hello, I Am Amara Okafor</h1>

<img src="https://via.placeholder.com/180x180.png?text=My+Photo"
     alt="Amara Okafor profile photo"
     width="180"
     height="180">

<h2>About Me</h2>
<p>I am 21 years old and I live in Lagos, Nigeria.</p>
<p>I am currently studying Computer Science and learning to build websites.</p>

<h2>My Interests</h2>
<p>I love music, football, and solving puzzles.</p>
<p>In my free time, I enjoy reading tech blogs and playing chess.</p>

<h2>My Career Goal</h2>
<p>I want to become a software developer and use technology to build tools that help small businesses in Africa grow.</p>

<h2>Connect With Me</h2>
<p>Find me on <a href="https://www.linkedin.com">LinkedIn</a>.</p>
<p>Learn web development at <a href="https://www.w3schools.com">W3Schools</a> — where I am learning from.</p>
<p>Send me an email: <a href="mailto:amara@example.com">amara@example.com</a></p>

</body>
</html>
```

**Expected final output in browser:**

```
Hello, I Am Amara Okafor

[Profile photo placeholder]

About Me

I am 21 years old and I live in Lagos, Nigeria.
I am currently studying Computer Science and learning to build websites.

My Interests

I love music, football, and solving puzzles.
In my free time, I enjoy reading tech blogs and playing chess.

My Career Goal

I want to become a software developer and use technology to
build tools that help small businesses in Africa grow.

Connect With Me

Find me on LinkedIn.
Learn web development at W3Schools — where I am learning from.
Send me an email: amara@example.com
```

---

### Stage 5 — Reflection Questions

After completing your project, ask yourself:

1. What would happen if you removed the `<!DOCTYPE html>` declaration?
2. Why is it important to use `<h1>` only once?
3. If you replace `https://` with nothing in an `href`, what do you think the browser will do?
4. How would you change the image size without distorting it?
5. What would a user with a visual impairment experience if you forgot the `alt` attribute on your image?

**Optional extensions:**

- Replace the placeholder image URL with a real photo of yourself
- Add a `<h2>` section for your favourite books or movies
- Create a second HTML file (`projects.html`) and link to it from your index page using `<a href="projects.html">My Projects</a>`

---

## Common Beginner Mistakes — Full Summary

Here is a complete list of all the mistakes beginners commonly make with the concepts in this lesson:

**Document Structure Mistakes:**
- Forgetting `<!DOCTYPE html>` — always put it on the very first line
- Writing content outside of `<body>...</body>` — all visible content must be inside body
- Not closing `</html>` at the end of the file

**Heading Mistakes:**
- Using multiple `<h1>` tags — stick to one per page
- Skipping heading levels (e.g., going from `<h1>` directly to `<h4>`) — always go in order
- Using `<h1>` just to make text big — use CSS for font size, not heading tags

**Paragraph Mistakes:**
- Pressing Enter in code expecting a new paragraph in the browser — use `<p>` tags
- Forgetting closing `</p>` tags — always close them
- Putting blank lines in code expecting blank lines in the browser — use CSS margins

**Link Mistakes:**
- Forgetting `https://` in URLs
- Not wrapping attribute values in double quotes
- Putting the URL as plain text instead of inside `href`

**Image Mistakes:**
- Wrong file name or wrong case (Cat.jpg vs cat.jpg)
- Missing `alt` attribute
- Adding a closing `</img>` tag — `<img>` is self-closing
- Using a file path that does not match where the image is actually stored

---

## Reflection Questions

Before moving to Lesson 3, take a moment to think about these questions:

1. In your own words, what does `<!DOCTYPE html>` do and why is it written at the very top?
2. What is the difference between `<h1>` and `<h2>`? When would you use each?
3. Explain the difference between `src` and `alt` in the `<img>` tag.
4. If a link has `href="about.html"`, where does the browser look for that file?
5. You want to display a large company logo that links to the company's homepage. Which two HTML tags would you combine to achieve this?
6. What shortcut do you press to view the source code of any web page?
7. Name two reasons why the `alt` attribute on images is important even if everything is working perfectly.

---

## Lesson Completion Checklist

Use this checklist to confirm you have fully mastered this lesson before moving forward:

- [ ] I can explain what `<!DOCTYPE html>` is and why it must appear first
- [ ] I can write a complete HTML document with `<html>`, `<body>`, and content tags
- [ ] I can create headings from `<h1>` to `<h6>` and know when to use each
- [ ] I understand why there should only be one `<h1>` per page
- [ ] I can write paragraphs using the `<p>` tag
- [ ] I understand why pressing Enter in code does not create paragraph breaks
- [ ] I can create a clickable link using `<a href="...">...</a>`
- [ ] I know that `href` holds the URL and that it must include `https://`
- [ ] I can display an image using `<img src="..." alt="..." width="..." height="...">`
- [ ] I understand that `<img>` is self-closing (no `</img>` needed)
- [ ] I understand why `alt` text is important for images
- [ ] I can view the source code of any web page using `Ctrl + U`
- [ ] I can right-click and Inspect any element on a web page
- [ ] I completed all four guided exercises
- [ ] I completed the personal web page mini-project
- [ ] I answered all the reflection questions

---

## Lesson Summary

Congratulations — you have completed Lesson 2! Here is what you now know:

**The HTML Document Structure:**
Every valid HTML document begins with `<!DOCTYPE html>`, is wrapped in `<html>...</html>`, and all visible content lives inside `<body>...</body>`.

**Headings:**
Use `<h1>` through `<h6>` to create titles and subtitles. `<h1>` is the biggest and most important — use it once per page as your main title.

**Paragraphs:**
Use `<p>...</p>` to create blocks of text. The browser automatically adds spacing between paragraphs. Pressing Enter in your code does not create paragraph breaks.

**Links:**
Use `<a href="URL">Clickable text</a>` to create hyperlinks. The `href` attribute holds the destination URL, which must include `https://`.

**Images:**
Use `<img src="file" alt="description" width="w" height="h">` to display images. The `alt` attribute is required for accessibility and broken image fallbacks. `<img>` is self-closing.

**Viewing Source Code:**
Press `Ctrl + U` to view full page source, or right-click → Inspect to examine specific elements.

> **Coming up in Lesson 3:** You will learn about HTML Elements in detail — what makes up an HTML element, nesting elements inside each other, and how to think about the structure of a web page as a tree of connected elements.

---

*Sources: W3Schools HTML Basic Examples (https://www.w3schools.com/html/html_basic.asp) and HTML Basic Code Challenges (https://www.w3schools.com/html/html_challenges_basic.asp)*
