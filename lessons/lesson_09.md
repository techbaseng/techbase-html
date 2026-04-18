---
render_with_liquid: false
title: "Lesson 9: HTML Quotation and Citation Elements"
nav_order: 9
---

# Lesson 9: HTML Quotation and Citation Elements

---

## Lesson Introduction

Have you ever read a webpage that shows a famous quote from a scientist, a message from a company, or a title of a book? Web developers use special HTML tags to mark up that kind of content correctly.

In this lesson, you will learn **six important HTML elements** that let you handle quotations, abbreviations, contact information, work titles, and text direction — all in a meaningful, structured way.

These six elements are:

- `<blockquote>` — for long quotes from another source
- `<q>` — for short inline quotes
- `<abbr>` — for abbreviations and acronyms
- `<address>` — for contact information
- `<cite>` — for titles of creative works
- `<bdo>` — for changing text direction

By the end of this lesson, you will understand what each tag does, why it exists, how to write it, and how to use them all together in a real webpage.

---

## Prerequisite Concepts

Before diving in, let us quickly review two things you already know:

**HTML Tags** — Every HTML element is written with an opening tag and a closing tag, like this:

```html
<p>This is a paragraph.</p>
```

- `<p>` is the **opening tag** — it tells the browser "start a paragraph here"
- `</p>` is the **closing tag** — notice the forward slash `/` which means "end the paragraph here"
- Everything in between is the **content** that appears on the page

**HTML Attributes** — Some tags can carry extra information called *attributes*, written inside the opening tag:

```html
<p title="I am a tooltip">Hover over me!</p>
```

- `title` is the **attribute name**
- `"I am a tooltip"` is the **attribute value**
- Attributes always go inside the opening tag and always use quotation marks around the value

You will use both of these ideas throughout this lesson.

---

## Conceptual Understanding

### Why Do We Need Special Quotation Tags?

Think about a newspaper article. When a journalist quotes someone, they use specific formatting — quotation marks, indentation, or a special block of text — so readers know "these are not the journalist's own words."

HTML works the same way. When you quote someone else's content on a webpage, you need to **tell the browser** (and search engines, and screen readers) that this text came from somewhere else. That is exactly what the quotation and citation elements do.

> **Analogy:** Think of these tags like different types of labels you put on different items in a kitchen. A label that says "borrowed from neighbour" means something different from a label that says "short note." Each tag is a specific label for a specific type of content.

There is another important reason too: **accessibility**. Screen readers (software used by visually impaired people) read HTML tags and use them to understand the meaning of content. When you use `<blockquote>` for a long quote, the screen reader knows to announce it as a quotation. When you use `<abbr>`, the screen reader can speak out the full word.

---

## Part 1 — The `<blockquote>` Element (Long Quotations)

### What Is It?

The `<blockquote>` element is used when you want to show a **long quotation** taken from another source — like a paragraph from a book, a statement from a company's website, or a passage from a research article.

**What problem does it solve?** Without it, readers cannot easily tell which text belongs to you and which text was copied from somewhere else. `<blockquote>` makes that separation clear.

### How Does the Browser Display It?

Browsers automatically **indent** (push inward from the left) the content inside `<blockquote>`. This visual indentation is the traditional way books and articles show long quotes.

### The `cite` Attribute

You can add a `cite` attribute inside `<blockquote>` to specify the **URL (web address) of the original source**. This does NOT display anything visible to the user — it is purely information for browsers and search engines. It is good practice to always include it when you know the source.

```html
<blockquote cite="https://www.example.com/source">
  The quoted text goes here.
</blockquote>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>

  <p>Here is a quote from WWF's website:</p>

  <blockquote cite="http://www.worldwildlife.org/who/index.html">
    For 60 years, WWF has worked to help people and nature thrive.
    As the world's leading conservation organization, WWF works in
    nearly 100 countries.
  </blockquote>

</body>
</html>
```

**Expected Output (in browser):**

```
Here is a quote from WWF's website:

      For 60 years, WWF has worked to help people and nature thrive.
      As the world's leading conservation organization, WWF works in
      nearly 100 countries.
```

*(Notice that the quoted text is indented — pushed inward — compared to the paragraph above it.)*

### Breaking Down This Code Line by Line

| Line | Code | What It Does |
|------|------|--------------|
| 1 | `<p>Here is a quote from WWF's website:</p>` | A regular paragraph introducing the quote |
| 2 | `<blockquote cite="http://...">` | Opens the blockquote; `cite` attribute holds the source URL |
| 3 | `For 60 years...` | The actual quoted text |
| 4 | `</blockquote>` | Closes the blockquote element |

### Second Example — A Science Quote

```html
<p>Albert Einstein once said:</p>

<blockquote cite="https://www.brainyquote.com">
  Imagination is more important than knowledge.
  For knowledge is limited, whereas imagination
  embraces the entire world.
</blockquote>
```

**Expected Output:**

```
Albert Einstein once said:

      Imagination is more important than knowledge.
      For knowledge is limited, whereas imagination
      embraces the entire world.
```

> 💡 **Thinking Prompt:** What happens if you remove the `<blockquote>` tags and just leave the text as a regular paragraph? Would the reader be able to tell it is a quote? This is why semantic tags matter.

### Real-World Use Case

On news websites, research portals, and educational platforms, `<blockquote>` is used everywhere — quoting experts, scientific papers, official statements, and more.

---

## Part 2 — The `<q>` Element (Short Inline Quotations)

### What Is It?

The `<q>` element is used for **short quotations** that appear *within* (inline with) normal text. It is the difference between quoting an entire paragraph from a book versus quoting a short phrase mid-sentence.

**What problem does it solve?** Sometimes you just want to quote a short phrase inside a sentence without creating a big indented block. `<q>` is the right tool for that.

### How Does the Browser Display It?

Browsers automatically add **quotation marks** (`"..."`) around the content inside `<q>`. You do NOT need to type the quotation marks yourself — the browser adds them for you.

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>

  <p>WWF's goal is to: <q>Build a future where people live in harmony with nature.</q></p>

</body>
</html>
```

**Expected Output:**

```
WWF's goal is to: "Build a future where people live in harmony with nature."
```

*(The browser automatically adds the quotation marks around the text inside `<q>`.)*

### Breaking Down This Code

- `<p>` — opens a paragraph
- `WWF's goal is to:` — regular text before the quote
- `<q>` — opens the inline quotation; browser will add opening `"`
- `Build a future where people live in harmony with nature.` — the quoted text
- `</q>` — closes the inline quotation; browser will add closing `"`
- `</p>` — closes the paragraph

### Second Example — A Scientist's Short Quote

```html
<p>Marie Curie believed that <q>nothing in life is to be feared, it is only to be understood.</q></p>
```

**Expected Output:**

```
Marie Curie believed that "nothing in life is to be feared, it is only to be understood."
```

### `<blockquote>` vs `<q>` — Quick Comparison

| Feature | `<blockquote>` | `<q>` |
|---------|----------------|-------|
| Quote length | Long (multiple sentences) | Short (a phrase or sentence) |
| Displayed as | Indented block | Inline with surrounding text |
| Quotation marks | Not added automatically | Added automatically by browser |
| Typical use | Paragraphs from articles, speeches | Short phrases inside sentences |

> 💡 **Thinking Prompt:** If someone said: "The scientist wrote an entire paragraph about climate change," would you use `<q>` or `<blockquote>`? Why?

---

## Part 3 — The `<abbr>` Element (Abbreviations and Acronyms)

### What Is It?

The `<abbr>` element marks text that is an **abbreviation** or an **acronym**.

- An **abbreviation** is a shortened form of a word, like "Dr." for "Doctor" or "Mr." for "Mister"
- An **acronym** is formed from the first letters of a phrase, like "HTML" for "HyperText Markup Language" or "WHO" for "World Health Organization"

**What problem does it solve?** When a reader encounters an abbreviation they don't know, they have no way to find out what it means just by looking at it. The `<abbr>` element lets you attach the full meaning as a tooltip — when the user hovers their mouse over the abbreviation, the full form pops up.

### The `title` Attribute

The `title` attribute is used with `<abbr>` to provide the full expanded form of the abbreviation. This is what shows up as a tooltip on hover.

```html
<abbr title="World Health Organization">WHO</abbr>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>

  <p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>

</body>
</html>
```

**Expected Output (what you see in browser):**

```
The WHO was founded in 1948.
```

*(When you hover your mouse over "WHO", a small tooltip pops up showing: "World Health Organization")*

### Breaking Down This Code

- `<p>` — opens a paragraph
- `The` — normal text
- `<abbr title="World Health Organization">` — opens the abbreviation element; `title` holds the full meaning
- `WHO` — the abbreviation as it appears on screen
- `</abbr>` — closes the abbreviation element
- `was founded in 1948.` — continues the normal paragraph text
- `</p>` — closes the paragraph

### Second Example — Using Multiple Abbreviations

```html
<p>
  The <abbr title="HyperText Markup Language">HTML</abbr> document was created by
  <abbr title="Doctor">Dr.</abbr> Smith at the university.
</p>
```

**Expected Output:**

```
The HTML document was created by Dr. Smith at the university.
```

*(Hovering over "HTML" shows "HyperText Markup Language". Hovering over "Dr." shows "Doctor".)*

### Why This Matters in the Real World

- **Search engines** (like Google) can better understand your content when they know what abbreviations mean
- **Translation tools** can more accurately translate your page
- **Screen readers** for visually impaired users can read out the full term
- **Accessibility** improves for all users, especially in technical, medical, or legal content

---

## Part 4 — The `<address>` Element (Contact Information)

### What Is It?

The `<address>` element is used to display **contact information** for the author or owner of a webpage or article. This could be an email address, a website URL, a physical address, a phone number, or a social media handle.

**What problem does it solve?** If you just write contact details as regular text, browsers and search engines treat them like any other text. The `<address>` tag tells them: "This is contact information" — which allows search engines to index it correctly and display it in local search results.

### How Does the Browser Display It?

Text inside `<address>` is usually displayed in **italic** (slanted text). The browser also automatically adds a **line break** (empty line) before and after the `<address>` element to separate it from surrounding content.

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>

  <address>
    Written by John Doe.<br>
    Visit us at:<br>
    Example.com<br>
    Box 564, Disneyland<br>
    USA
  </address>

</body>
</html>
```

**Expected Output (in browser):**

*(Displayed in italic text)*
```
Written by John Doe.
Visit us at:
Example.com
Box 564, Disneyland
USA
```

### Breaking Down This Code

- `<address>` — opens the contact information block
- `Written by John Doe.` — first line of contact info
- `<br>` — a line break tag (forces the next content to start on a new line); there is no closing `</br>` tag
- `Visit us at:` — second line
- `<br>` — another line break
- `Example.com` — the website
- `<br>` — another line break
- `Box 564, Disneyland` — physical address
- `<br>` — another line break
- `USA` — country
- `</address>` — closes the contact information block

### Second Example — Email Contact

```html
<address>
  Contact us at: admin@mywebsite.com<br>
  Phone: +234 800 123 4567<br>
  Lagos, Nigeria
</address>
```

**Expected Output:**

*(In italic)*
```
Contact us at: admin@mywebsite.com
Phone: +234 800 123 4567
Lagos, Nigeria
```

> ⚠️ **Important Note:** The `<address>` element is meant for the **contact details of the author/owner** of the page. It is NOT meant to be used for any random physical address in your content (like an address mentioned in a news story). Use it specifically for the person/organisation who wrote or owns the page.

---

## Part 5 — The `<cite>` Element (Title of a Creative Work)

### What Is It?

The `<cite>` element is used to mark the **title of a creative work** — like a book, a painting, a movie, a poem, a song, a sculpture, a TV show, or any other piece of creative content.

**What problem does it solve?** When you mention the name of a book or artwork in text, readers should be able to tell that it is a *title*, not just an ordinary word. The `<cite>` tag gives the title a distinct visual style and semantic meaning.

### An Important Rule

A **person's name is NOT the title of a work**. For example:
- ✅ Correct: `<cite>The Scream</cite>` (title of a painting)
- ❌ Wrong: `<cite>Edvard Munch</cite>` (this is a person's name, not a title)

### How Does the Browser Display It?

Text inside `<cite>` is usually displayed in **italic** (slanted text).

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>

  <p><cite>The Scream</cite> by Edvard Munch. Painted in 1893.</p>

</body>
</html>
```

**Expected Output:**

```
The Scream by Edvard Munch. Painted in 1893.
```

*(Where "The Scream" appears in italic.)*

### Second Example — Citing a Book

```html
<p>I just finished reading <cite>Things Fall Apart</cite> by Chinua Achebe.
It is one of the most important African novels ever written.</p>
```

**Expected Output:**

```
I just finished reading Things Fall Apart by Chinua Achebe.
It is one of the most important African novels ever written.
```

*(Where "Things Fall Apart" appears in italic.)*

### `<cite>` vs `<blockquote cite="...">`

These two look similar but are very different:

| Element | Purpose |
|---------|---------|
| `<cite>` | Displays a **title** of a creative work as italic text on the page |
| `cite` attribute in `<blockquote>` | Provides the **URL of the source** — invisible to users, used by browsers and search engines |

---

## Part 6 — The `<bdo>` Element (Bi-Directional Override)

### What Is It?

`<bdo>` stands for **Bi-Directional Override**. This element is used to **override** (change) the natural direction that text flows on screen.

Normally in English (and most Western languages), text flows **left to right** — you start reading from the left side of the page and move right. But some languages, like Arabic and Hebrew, flow **right to left**.

The `<bdo>` element lets you force text to display in a specific direction, regardless of the default direction.

### The `dir` Attribute

The `<bdo>` element uses the `dir` attribute to specify the text direction:
- `dir="ltr"` — **Left to Right** (the normal direction for English)
- `dir="rtl"` — **Right to Left** (reverses the text direction)

### Simple Example — Reversing Text Direction

```html
<!DOCTYPE html>
<html>
<body>

  <bdo dir="rtl">This text will be written from right to left</bdo>

</body>
</html>
```

**Expected Output:**

```
tfel ot thgir morf nettirw eb lliw txet sihT
```

*(The words themselves are not reversed, but the entire text is displayed starting from the right side of the page, so it appears mirrored.)*

### Breaking Down This Code

- `<bdo` — opens the bi-directional override tag
- `dir="rtl"` — the `dir` attribute; `"rtl"` means "right to left"
- `>` — closes the opening tag
- `This text will be written from right to left` — the content that will be reversed
- `</bdo>` — closes the bdo element

### Second Example — Left to Right (Normal Direction)

```html
<bdo dir="ltr">This is the normal left-to-right direction.</bdo>
```

**Expected Output:**

```
This is the normal left-to-right direction.
```

*(No change — this just confirms the default direction explicitly.)*

### Real-World Use Case

If you are building a multilingual website that includes Arabic or Hebrew text, you would use `<bdo dir="rtl">` or set the `dir` attribute on the HTML body to make those sections read correctly.

---

## Complete Reference Table

Here is a summary of all six elements covered in this lesson:

| Tag | Full Name | What It Does | Visual Style |
|-----|-----------|--------------|--------------|
| `<blockquote>` | Block Quotation | Defines a long section quoted from another source | Indented block |
| `<q>` | Inline Quotation | Defines a short inline quotation | Adds `"..."` around text |
| `<abbr>` | Abbreviation | Marks an abbreviation or acronym | Tooltip shows full meaning on hover |
| `<address>` | Address | Defines contact information | Italic + line breaks before/after |
| `<cite>` | Citation / Title | Marks the title of a creative work | Italic |
| `<bdo>` | Bi-Directional Override | Changes the direction of text | Reverses text direction |

---

## Guided Practice Exercises

### Exercise 1 — Using `<blockquote>`

**Objective:** Practice writing a long blockquote with a source citation.

**Scenario:** You are building a science education webpage and want to include a famous statement from NASA.

**Steps:**
1. Open your code editor (or a plain text file saved as `.html`)
2. Create the HTML structure with `<!DOCTYPE html>`, `<html>`, and `<body>` tags
3. Write a short introductory sentence using `<p>`
4. Add a `<blockquote>` with the `cite` attribute pointing to `https://www.nasa.gov`
5. Place the following text inside the blockquote: *"NASA leads the nation on a great journey of discovery, seeking new knowledge and understanding of Earth, the solar system, and the universe."*

**Your code should look like this:**

```html
<!DOCTYPE html>
<html>
<body>

  <p>From NASA's official mission statement:</p>

  <blockquote cite="https://www.nasa.gov">
    NASA leads the nation on a great journey of discovery, seeking new knowledge
    and understanding of Earth, the solar system, and the universe.
  </blockquote>

</body>
</html>
```

**Expected Output:**

```
From NASA's official mission statement:

      NASA leads the nation on a great journey of discovery, seeking new knowledge
      and understanding of Earth, the solar system, and the universe.
```

**Self-Check Questions:**
- Is the text visually indented compared to the paragraph above it?
- Did you include the `cite` attribute with the URL?
- Did you open AND close the `<blockquote>` tag?

---

### Exercise 2 — Using `<q>` for Short Quotes

**Objective:** Practice embedding a short inline quotation inside a paragraph.

**Scenario:** You are writing a webpage about motivational quotes for students.

**Your code:**

```html
<!DOCTYPE html>
<html>
<body>

  <p>Nelson Mandela famously said: <q>Education is the most powerful weapon which you can use to change the world.</q></p>

  <p>Albert Einstein believed: <q>A person who never made a mistake never tried anything new.</q></p>

</body>
</html>
```

**Expected Output:**

```
Nelson Mandela famously said: "Education is the most powerful weapon which you can use to change the world."

Albert Einstein believed: "A person who never made a mistake never tried anything new."
```

**Self-Check Questions:**
- Does each quote appear with quotation marks around it?
- Is the quote part of the same line as the surrounding paragraph text?

---

### Exercise 3 — Using `<abbr>`

**Objective:** Practice marking abbreviations with their full expanded forms.

**Scenario:** You are writing a webpage about technology for a general audience.

**Your code:**

```html
<!DOCTYPE html>
<html>
<body>

  <p>
    The <abbr title="HyperText Markup Language">HTML</abbr> standard is maintained by the
    <abbr title="World Wide Web Consortium">W3C</abbr>.
    It is used alongside <abbr title="Cascading Style Sheets">CSS</abbr> and
    <abbr title="JavaScript">JS</abbr> to build modern websites.
  </p>

</body>
</html>
```

**Expected Output (visible text):**

```
The HTML standard is maintained by the W3C. It is used alongside CSS and JS to build modern websites.
```

*(Hovering over "HTML" shows "HyperText Markup Language", hovering over "W3C" shows "World Wide Web Consortium", etc.)*

**Self-Check Questions:**
- Did each `<abbr>` tag have a `title` attribute?
- Is the `title` attribute value the full expanded form of the abbreviation?

---

### Exercise 4 — Using `<address>`

**Objective:** Create a contact section for a fictional school website.

**Your code:**

```html
<!DOCTYPE html>
<html>
<body>

  <h2>Contact Us</h2>

  <address>
    Lagos STEM Academy<br>
    15 Innovation Drive, Victoria Island<br>
    Lagos, Nigeria<br>
    Email: info@lagosstem.edu.ng<br>
    Phone: +234 801 234 5678
  </address>

</body>
</html>
```

**Expected Output (in italic):**

```
Lagos STEM Academy
15 Innovation Drive, Victoria Island
Lagos, Nigeria
Email: info@lagosstem.edu.ng
Phone: +234 801 234 5678
```

---

### Exercise 5 — Using `<cite>`

**Objective:** Reference the titles of several creative works correctly.

**Your code:**

```html
<!DOCTYPE html>
<html>
<body>

  <p>My favourite book is <cite>Purple Hibiscus</cite> by Chimamanda Ngozi Adichie.</p>
  <p>The painting <cite>Starry Night</cite> was created by Vincent van Gogh in 1889.</p>
  <p>The movie <cite>Black Panther</cite> was released in 2018.</p>

</body>
</html>
```

**Expected Output:**

```
My favourite book is Purple Hibiscus by Chimamanda Ngozi Adichie.
The painting Starry Night was created by Vincent van Gogh in 1889.
The movie Black Panther was released in 2018.
```

*(All three titles appear in italic.)*

---

### Exercise 6 — Using `<bdo>`

**Objective:** Experiment with text direction overrides.

**Your code:**

```html
<!DOCTYPE html>
<html>
<body>

  <p>Normal direction: <bdo dir="ltr">Hello World</bdo></p>
  <p>Reversed direction: <bdo dir="rtl">Hello World</bdo></p>

</body>
</html>
```

**Expected Output:**

```
Normal direction: Hello World
Reversed direction: dlroW olleH
```

---

## Mini Project: Author's Blog Page

Now let us combine **all six elements** into one realistic project — an author's personal blog page.

### Project Description

You will build a simple webpage for a fictional author named **Amara Osei**. The page will include a quote from her latest book, abbreviations, her contact details, and a reference to her published work.

### Stage 1: Set Up the Page Structure

```html
<!DOCTYPE html>
<html>
<head>
  <title>Amara Osei - Author's Blog</title>
</head>
<body>

  <h1>Amara Osei — Author & Educator</h1>

</body>
</html>
```

**Milestone 1 Output:** A page with just a heading.

---

### Stage 2: Add an Introduction Paragraph with Abbreviations

Add this inside the `<body>` after the heading:

```html
<p>
  Welcome to my blog. I write about <abbr title="Science, Technology, Engineering and Mathematics">STEM</abbr>
  education and storytelling in Africa. My work has been featured in
  <abbr title="The New York Times">NYT</abbr> and the
  <abbr title="British Broadcasting Corporation">BBC</abbr>.
</p>
```

**Milestone 2 Output:**

```
Amara Osei — Author & Educator

Welcome to my blog. I write about STEM education and storytelling in Africa.
My work has been featured in NYT and the BBC.
```

*(Hovering over "STEM", "NYT", or "BBC" reveals the full names.)*

---

### Stage 3: Add a Featured Long Quote

```html
<h2>Featured Quote</h2>

<p>From my latest novel:</p>

<blockquote cite="https://www.amaraosei.com/book">
  The children of tomorrow will not be remembered for how much they knew,
  but for how bravely they dared to learn in the face of uncertainty.
  Education is not the filling of a bucket, but the lighting of a fire.
</blockquote>
```

**Milestone 3 Output:** The blockquote appears indented below the heading.

---

### Stage 4: Add a Short Inline Quote

```html
<p>
  My writing philosophy is simple: <q>Every story deserves to be told with honesty and courage.</q>
  I carry this with me every time I sit down to write.
</p>
```

**Milestone 4 Output:**

```
My writing philosophy is simple: "Every story deserves to be told with honesty and courage."
I carry this with me every time I sit down to write.
```

---

### Stage 5: Cite a Published Work

```html
<h2>My Latest Book</h2>

<p>
  My debut novel, <cite>Voices from the Red Earth</cite>, was published in 2023.
  It tells the story of three generations of a Ghanaian family navigating
  tradition and modernity.
</p>
```

**Milestone 5 Output:**

```
My Latest Book

My debut novel, Voices from the Red Earth, was published in 2023.
```

*(Title appears in italic.)*

---

### Stage 6: Add Contact Information

```html
<h2>Contact Me</h2>

<address>
  Amara Osei<br>
  Literary Agent: books@amaraosei.com<br>
  Media Enquiries: press@amaraosei.com<br>
  Accra, Ghana
</address>
```

---

### Stage 7: Add a Fun Text Direction Element

```html
<p>My author signature in reverse: <bdo dir="rtl">Amara Osei</bdo></p>
```

---

### Complete Final Project Code

```html
<!DOCTYPE html>
<html>
<head>
  <title>Amara Osei - Author's Blog</title>
</head>
<body>

  <h1>Amara Osei — Author & Educator</h1>

  <p>
    Welcome to my blog. I write about
    <abbr title="Science, Technology, Engineering and Mathematics">STEM</abbr>
    education and storytelling in Africa. My work has been featured in
    <abbr title="The New York Times">NYT</abbr> and the
    <abbr title="British Broadcasting Corporation">BBC</abbr>.
  </p>

  <h2>Featured Quote</h2>

  <p>From my latest novel:</p>

  <blockquote cite="https://www.amaraosei.com/book">
    The children of tomorrow will not be remembered for how much they knew,
    but for how bravely they dared to learn in the face of uncertainty.
    Education is not the filling of a bucket, but the lighting of a fire.
  </blockquote>

  <p>
    My writing philosophy is simple: <q>Every story deserves to be told with honesty and courage.</q>
    I carry this with me every time I sit down to write.
  </p>

  <h2>My Latest Book</h2>

  <p>
    My debut novel, <cite>Voices from the Red Earth</cite>, was published in 2023.
    It tells the story of three generations of a Ghanaian family navigating
    tradition and modernity.
  </p>

  <h2>Contact Me</h2>

  <address>
    Amara Osei<br>
    Literary Agent: books@amaraosei.com<br>
    Media Enquiries: press@amaraosei.com<br>
    Accra, Ghana
  </address>

  <p>My author signature in reverse: <bdo dir="rtl">Amara Osei</bdo></p>

</body>
</html>
```

**Final Complete Output:**

```
Amara Osei — Author & Educator

Welcome to my blog. I write about STEM education and storytelling in Africa.
My work has been featured in NYT and the BBC.

Featured Quote

From my latest novel:

      The children of tomorrow will not be remembered for how much they knew,
      but for how bravely they dared to learn in the face of uncertainty.
      Education is not the filling of a bucket, but the lighting of a fire.

My writing philosophy is simple: "Every story deserves to be told with honesty and courage."
I carry this with me every time I sit down to write.

My Latest Book

My debut novel, Voices from the Red Earth, was published in 2023.
It tells the story of three generations of a Ghanaian family navigating
tradition and modernity.

Contact Me

Amara Osei
Literary Agent: books@amaraosei.com
Media Enquiries: press@amaraosei.com
Accra, Ghana

My author signature in reverse: iesO amarA
```

> 💡 **Reflection Questions:**
> - Which element makes the long quote stand out visually from the rest of the text?
> - Why did we use `<abbr>` for STEM, NYT, and BBC?
> - What would happen if you wrapped Amara's name in `<cite>` instead of `<address>`? Would that be correct?

### Optional Extensions

- Add more books using `<cite>` and write short reviews for each
- Add a second `<blockquote>` from a different author
- Try changing `<bdo dir="rtl">` on a longer sentence and observe the result
- Look up the `lang` attribute and try `<bdo dir="rtl" lang="ar">` to experiment with Arabic

---

## Code Challenge — Quotations

Based on the W3Schools code challenge for quotations, here are the types of tasks you should be able to complete confidently after this lesson:

**Challenge 1:** Given a paragraph with a long quote from an external source, wrap the quoted text in the correct tag that visually indents it.

*Answer: Use `<blockquote>`*

**Challenge 2:** Given a paragraph containing the phrase `"Build a future where people live in harmony with nature"` as a short inline quote, use the correct tag so the browser automatically adds quotation marks.

*Answer: Use `<q>`*

**Challenge 3:** On a page showing "The WHO was founded in 1948", mark the abbreviation "WHO" so that hovering over it shows "World Health Organization".

*Answer: Use `<abbr title="World Health Organization">WHO</abbr>`*

**Challenge 4:** Add contact information to a webpage so it renders in italic with line breaks.

*Answer: Use `<address>` with `<br>` tags between lines*

**Challenge 5:** Mark the title of a book in a sentence so it appears in italic.

*Answer: Wrap the title in `<cite>`*

**Challenge 6:** Force a line of text to display from right to left.

*Answer: Use `<bdo dir="rtl">text here</bdo>`*

---

## Common Beginner Mistakes

### Mistake 1 — Adding quotation marks manually inside `<q>`

❌ **Wrong:**
```html
<p>She said: <q>"Come and see the stars."</q></p>
```

**Output:**
```
She said: ""Come and see the stars.""
```

*(Double quotation marks appear because the browser adds them AND you typed them.)*

✅ **Correct:**
```html
<p>She said: <q>Come and see the stars.</q></p>
```

**Output:**
```
She said: "Come and see the stars."
```

---

### Mistake 2 — Using `<cite>` for a Person's Name

❌ **Wrong:**
```html
<p>The painting was created by <cite>Leonardo da Vinci</cite>.</p>
```

*(Leonardo da Vinci is a person's name, not a work title.)*

✅ **Correct:**
```html
<p>The painting <cite>Mona Lisa</cite> was created by Leonardo da Vinci.</p>
```

---

### Mistake 3 — Forgetting to Close Tags

❌ **Wrong:**
```html
<blockquote cite="https://example.com">
  This is a long quote from a source.
```

*(The `</blockquote>` closing tag is missing — this causes browser rendering problems.)*

✅ **Correct:**
```html
<blockquote cite="https://example.com">
  This is a long quote from a source.
</blockquote>
```

---

### Mistake 4 — Forgetting the `title` Attribute on `<abbr>`

❌ **Wrong:**
```html
<p>The <abbr>WHO</abbr> was founded in 1948.</p>
```

*(Without `title`, the `<abbr>` tag does nothing visible or useful.)*

✅ **Correct:**
```html
<p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>
```

---

### Mistake 5 — Using `<address>` for Any Address (Not the Author's)

❌ **Wrong:**
```html
<p>The conference took place at:
<address>
  15 Central Park, New York, NY
</address>
</p>
```

*(This is the address of an event, not the author of the page.)*

✅ **Correct usage of `<address>`:**
```html
<address>
  Written by John Smith.<br>
  Contact: john@example.com
</address>
```

For a random address in content, just use a `<p>` tag instead.

---

### Mistake 6 — Confusing the `cite` Attribute with the `<cite>` Element

❌ **Confused thinking:** "They are both 'cite' so they must do the same thing."

✅ **Clear distinction:**
- `<cite>` is an **element** — it wraps the *title* of a creative work and displays it in italic on the screen
- `cite="..."` is an **attribute** used inside `<blockquote>` or `<q>` — it holds a URL pointing to the source; it is invisible to users

---

## Reflection Questions

Think carefully about each of these after completing the lesson:

1. **Why does `<blockquote>` exist when you could just indent text using CSS?**
   *(Hint: Think about meaning vs appearance — semantic HTML vs visual styling.)*

2. **If you are quoting a sentence from a research paper in the middle of your paragraph, would you use `<q>` or `<blockquote>`? Why?**

3. **What benefit does `<abbr title="...">` provide to a reader who is using a screen reader?**

4. **Is it ever appropriate to put a URL (like `https://example.com`) inside `<address>`? Why or why not?**

5. **If someone builds a website in Arabic, which attribute or element would be most relevant to them from today's lesson?**

6. **What is the difference between `<cite>The Scream</cite>` and writing "The Scream" in bold using `<b>`?**
   *(Hint: One is *semantic* — it tells the browser what the text *means*; the other is purely *visual*.)*

---

## Completion Checklist

Before moving on to the next lesson, make sure you can confidently say YES to each of these:

- [ ] I know what `<blockquote>` is for and how the `cite` attribute works with it
- [ ] I understand the difference between `<blockquote>` (long quotes) and `<q>` (short inline quotes)
- [ ] I know that `<q>` automatically adds quotation marks — I do not need to type them
- [ ] I can use `<abbr title="...">` to mark an abbreviation and provide its full meaning
- [ ] I understand that `<address>` is for contact details of the page's author, displayed in italic
- [ ] I know that `<cite>` marks the *title* of a creative work (not a person's name), displayed in italic
- [ ] I can use `<bdo dir="rtl">` to reverse text direction
- [ ] I know the difference between the `<cite>` element and the `cite` attribute
- [ ] I completed at least 4 of the 6 practice exercises
- [ ] I built the mini-project Author's Blog page
- [ ] I can identify and correct the 6 common beginner mistakes

---

## Lesson Summary

In this lesson, you learned six powerful HTML elements that go beyond just displaying text — they give your content **meaning and structure**:

**`<blockquote cite="URL">`** — For long quotations taken from another source. Browsers indent the text automatically. Use the `cite` attribute to record the URL of the source (not visible to users).

**`<q>`** — For short inline quotations within a sentence. Browsers automatically add quotation marks. Never type the quotes yourself when using this tag.

**`<abbr title="Full Form">`** — For abbreviations and acronyms. The `title` attribute holds the expanded meaning. It appears as a tooltip when the user hovers their mouse over the text.

**`<address>`** — For contact information belonging to the author or owner of the page. Text is styled in italic and separated from surrounding content with line breaks.

**`<cite>`** — For marking the titles of creative works such as books, paintings, movies, and songs. The text displays in italic. Remember: do NOT use it for a person's name.

**`<bdo dir="rtl|ltr">`** — For overriding the natural direction of text. Use `dir="rtl"` to force text to display from right to left. Useful for multilingual pages.

These elements are part of what makes HTML **semantic** — meaning-rich. They do not just change how things look; they communicate *what* things are, which matters for search engines, screen readers, translation tools, and the long-term quality of your web pages.

> **What's next:** In Lesson 10, you will learn about HTML Comments — how to leave notes in your code that are invisible to users but helpful to developers.
