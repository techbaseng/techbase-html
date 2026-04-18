---
render_with_liquid: false
title: "Lesson 19 – HTML class and id Attributes"
nav_order: 19
---

# Lesson 19 – HTML `class` and `id` Attributes

---

## Lesson Introduction

Welcome to Lesson 19! In this lesson you will learn two of the most important tools that web developers use every single day: the **`class` attribute** and the **`id` attribute**.

By the end of this lesson you will be able to:

- Understand what `class` and `id` attributes are and why they exist
- Use `class` to apply the same style to many elements at once
- Assign multiple classes to a single element
- Use `id` to uniquely identify a single element
- Use `id` to create page bookmark links that let users jump to sections
- Understand the difference between `class` and `id`
- Use JavaScript's `getElementsByClassName()` and `getElementById()` methods to interact with elements

Think of this lesson like learning how to **label boxes in a warehouse**. Some boxes share the same label because they contain the same type of product — that is like `class`. Other boxes have a unique serial number that belongs to only one box — that is like `id`.

---

## Prerequisite Concepts

Before diving in, let's make sure you understand a few things from earlier lessons. If these feel familiar, great! If not, read carefully — this foundation is important.

### What is an HTML Attribute?

An **attribute** gives extra information about an HTML element. Attributes live inside the **opening tag** and always follow this pattern:

```html
<tagname attribute="value">content</tagname>
```

For example:

```html
<p style="color: red;">Hello!</p>
```

Here `style` is the attribute and `"color: red;"` is its value.

### What is CSS?

**CSS (Cascading Style Sheets)** is the language used to style HTML elements — controlling colours, sizes, spacing, fonts, and more. In this lesson, CSS styles will be written inside a `<style>` tag in the `<head>` section of the HTML page.

A CSS rule looks like this:

```css
selector {
  property: value;
}
```

For example:

```css
p {
  color: blue;
}
```

This turns all paragraph text blue. You do not need to be a CSS expert — just understand that CSS rules target elements and change how they look.

---

## Part 1 – The HTML `class` Attribute

### What is the `class` Attribute?

The `class` attribute is used to **group HTML elements together** so they can all share the same style. Think of it like giving a group of students the same uniform. You create a "uniform style" once, and every student wearing that uniform automatically looks the same.

**Why does this exist?**  
Without `class`, if you wanted ten paragraphs to all have a red background, you would have to write `style="background-color: red;"` ten times — once on each paragraph. With `class`, you write the style **once** in CSS, give it a name, and then add `class="that-name"` to every element you want styled. Done.

**What problem does it solve?**  
It removes repetition. It makes your code cleaner, easier to read, and much easier to maintain. If you later want to change the background colour, you change it in one place — not ten.

### How `class` Works — Step by Step

Here is the formula:

**Step 1:** Create a CSS rule using a `.` (dot/period) followed by your class name.

```css
.myClass {
  color: blue;
}
```

**Step 2:** Add `class="myClass"` to any HTML element you want to style.

```html
<p class="myClass">This text will be blue.</p>
```

The dot (`.`) in CSS is how you say "target elements with this class name". The class name itself (without the dot) goes inside the HTML attribute.

---

### Simple Example 1 — Styling Three Headings the Same Way

Let's say you are building a travel website. You have three city headings: London, Paris, and Tokyo. You want each one to have a tomato-red background, white text, and some padding.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .city {
      background-color: tomato;
      color: white;
      padding: 10px;
    }
  </style>
</head>
<body>

  <h2 class="city">London</h2>
  <p>London is the capital of England.</p>

  <h2 class="city">Paris</h2>
  <p>Paris is the capital of France.</p>

  <h2 class="city">Tokyo</h2>
  <p>Tokyo is the capital of Japan.</p>

</body>
</html>
```

**Expected Output (what you see in the browser):**

- "London", "Paris", and "Tokyo" each appear as headings with a **tomato-red background**, **white text**, and a small padding around the text.
- The paragraphs beneath each heading have no special styling — they are plain black text.

**Line-by-line explanation:**

- `.city { ... }` — This is the CSS rule. The `.` tells the browser "find every element with the class name `city`".
- `background-color: tomato;` — Sets the background colour to a tomato-red shade.
- `color: white;` — Sets the text colour to white.
- `padding: 10px;` — Adds 10 pixels of space inside the element, around the text.
- `<h2 class="city">London</h2>` — The `class="city"` attribute connects this heading to the `.city` CSS rule.
- All three `<h2>` elements share the class `city`, so they all get the same styling.

> 💡 **Think about it:** What would happen if you removed `class="city"` from the Paris heading? That heading would lose its red background and white text, becoming a plain heading. The other two would stay styled.

---

### Simple Example 2 — Highlighting Words Inside a Sentence

The `class` attribute is not just for big block elements. You can use it on inline elements like `<span>` to style just a few words inside a sentence.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .highlight {
      font-size: 120%;
      color: red;
    }
  </style>
</head>
<body>

  <h1>My <span class="highlight">Important</span> Heading</h1>
  <p>This is some <span class="highlight">important</span> text.</p>

</body>
</html>
```

**Expected Output:**

- The heading reads "My **Important** Heading", but the word "Important" is **larger** and **red**.
- The paragraph reads "This is some **important** text.", with "important" appearing larger and red.

**Line-by-line explanation:**

- `<span>` is an inline element — it wraps around text without starting a new line.
- `class="highlight"` connects the `<span>` to the `.highlight` CSS rule.
- `font-size: 120%;` makes the text 20% bigger than the surrounding text.
- `color: red;` turns the text red.
- Both `<span>` elements in the heading and in the paragraph share the same class, so they both get the same styling.

> 💡 **Key insight:** The `class` attribute can be placed on **any** HTML element — headings, paragraphs, divs, spans, lists, images, links, and more.

> ⚠️ **Important note:** Class names are **case sensitive**. `class="City"` and `class="city"` are two completely different classes. Always be consistent with your capitalisation.

---

### The CSS Syntax for a Class Rule

Here is the exact syntax again, clearly broken down:

```css
.className {
  property: value;
  property: value;
}
```

- The `.` (dot) at the front is mandatory — it tells CSS this is a class selector.
- `className` is your chosen name. You can call it anything, but it should describe what the class does (e.g., `.warning`, `.highlight`, `.city`).
- Inside `{ }`, you write as many CSS properties and values as you need, each ending with a `;`.

---

### Assigning Multiple Classes to One Element

An HTML element can belong to **more than one class at the same time**. You simply separate the class names with a **space** inside the attribute value.

```html
<h2 class="city main">London</h2>
```

This heading belongs to both the `city` class and the `main` class. It will receive the styling from **both** CSS rules.

**Full example:**

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .city {
      background-color: tomato;
      color: white;
      padding: 10px;
    }
    .main {
      font-size: 30px;
      text-decoration: underline;
    }
  </style>
</head>
<body>

  <h2 class="city main">London</h2>
  <h2 class="city">Paris</h2>
  <h2 class="city">Tokyo</h2>

</body>
</html>
```

**Expected Output:**

- "London" has a tomato-red background, white text, padding, is larger (30px), and is underlined.
- "Paris" and "Tokyo" have the tomato-red background, white text, and padding — but are not larger or underlined.

**Why is this useful?**  
Imagine building a news website. Most article cards look the same (`class="card"`), but the top featured article also needs to be larger (`class="card featured"`). Multiple classes let you layer styles without duplicating code.

---

### Different Elements Can Share the Same Class

One class can be used by completely different types of elements. A `<h2>` and a `<p>` can both use `class="city"` and receive identical styling.

```html
<h2 class="city">Paris</h2>
<p class="city">Paris is the capital of France.</p>
```

**Expected Output:**

Both the heading and the paragraph will have the same background colour, text colour, and padding — because they share the same class. The browser does not care that one is a heading and one is a paragraph; both match the `.city` CSS rule.

---

### Using `class` with JavaScript

The `class` attribute is not only useful for CSS styling. JavaScript can also **find and manipulate** all elements that share a class name using the `getElementsByClassName()` method.

**What is `getElementsByClassName()`?**  
This is a JavaScript function (a built-in tool) that searches the HTML document and returns a list of every element with a given class name.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .city {
      background-color: tomato;
      color: white;
      padding: 10px;
      margin: 5px;
    }
  </style>
</head>
<body>

  <button onclick="hideCities()">Hide all cities</button>

  <div class="city"><h2>London</h2><p>London is the capital of England.</p></div>
  <div class="city"><h2>Paris</h2><p>Paris is the capital of France.</p></div>
  <div class="city"><h2>Tokyo</h2><p>Tokyo is the capital of Japan.</p></div>

  <script>
    function hideCities() {
      var x = document.getElementsByClassName("city");
      for (var i = 0; i < x.length; i++) {
        x[i].style.display = "none";
      }
    }
  </script>

</body>
</html>
```

**Expected Output:**

When the page loads, all three city boxes are visible. When you click "Hide all cities", all three boxes disappear.

**What the JavaScript code does — line by line:**

- `function hideCities() { ... }` — Defines a reusable block of code called `hideCities`.
- `document.getElementsByClassName("city")` — Searches the page and returns all elements with `class="city"` as a list (called a collection).
- `for (var i = 0; i < x.length; i++)` — Loops through every item in that list. `x.length` is the total number of items (3 in this case).
- `x[i].style.display = "none";` — Hides the current element by setting its `display` CSS property to `"none"`.

> 💡 Don't worry if JavaScript feels confusing right now. The key takeaway is: **class names are used not just for CSS, but also as targets for JavaScript actions**.

---

## Part 2 – The HTML `id` Attribute

### What is the `id` Attribute?

The `id` attribute gives an HTML element a **unique identity**. Think of it like a national ID number or a passport number — only **one person in the entire country** can have that exact number.

In the same way, only **one element in an entire HTML document** can have a specific `id` value. If you try to use the same `id` on two elements, the browser will not crash, but your code will be incorrect — CSS and JavaScript will behave unpredictably.

**Why does it exist?**  
Sometimes you need to target one exact element — not a group, not a type, just one single specific element. The `id` attribute makes that possible.

**What problem does it solve?**

- Styling one specific element differently from everything else on the page.
- Creating bookmarks that let users jump to sections on long pages.
- Giving JavaScript a precise target to update, modify, or respond to.

---

### How `id` Works — Step by Step

Here is the formula:

**Step 1:** Create a CSS rule using a `#` (hash symbol) followed by your id name.

```css
#myHeader {
  background-color: lightblue;
}
```

**Step 2:** Add `id="myHeader"` to the one HTML element you want to style.

```html
<h1 id="myHeader">Welcome!</h1>
```

The `#` in CSS is how you say "target the element with this exact id". The id name itself (without the `#`) goes inside the HTML attribute.

---

### Simple Example 1 — Styling a Single Unique Header

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    #myHeader {
      background-color: lightblue;
      color: black;
      padding: 40px;
      text-align: center;
    }
  </style>
</head>
<body>

  <h1 id="myHeader">My Header</h1>

</body>
</html>
```

**Expected Output:**

A centred heading "My Header" with a light-blue background, black text, and generous padding around it.

**Line-by-line explanation:**

- `#myHeader { ... }` — The `#` tells CSS to look for the element with `id="myHeader"`.
- `background-color: lightblue;` — Sets a light blue background.
- `color: black;` — Black text.
- `padding: 40px;` — 40 pixels of space all around the text inside the element.
- `text-align: center;` — Centres the text horizontally.
- `<h1 id="myHeader">My Header</h1>` — This heading is connected to the `#myHeader` CSS rule.

---

### Simple Example 2 — Class and ID Side by Side

This example shows both `class` (for many elements) and `id` (for one element) working together in the same page:

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* Style the ONE element with id="myHeader" */
    #myHeader {
      background-color: lightblue;
      color: black;
      padding: 40px;
      text-align: center;
    }

    /* Style ALL elements with class="city" */
    .city {
      background-color: tomato;
      color: white;
      padding: 10px;
    }
  </style>
</head>
<body>

  <!-- One unique element -->
  <h1 id="myHeader">My Cities</h1>

  <!-- Multiple elements sharing a class -->
  <h2 class="city">London</h2>
  <p>London is the capital of England.</p>

  <h2 class="city">Paris</h2>
  <p>Paris is the capital of France.</p>

  <h2 class="city">Tokyo</h2>
  <p>Tokyo is the capital of Japan.</p>

</body>
</html>
```

**Expected Output:**

- "My Cities" appears as a large centred heading with a light-blue background.
- Each of the city names (London, Paris, Tokyo) appears in a tomato-red heading with white text.
- The city description paragraphs remain plain black text.

---

### The `id` Naming Rules

Unlike `class`, which is quite flexible, the `id` attribute has strict rules:

- The `id` value must be **unique** — no two elements on the same page can share the same `id`.
- The `id` name is **case sensitive** — `id="myHeader"` and `id="myheader"` are different.
- The `id` name must contain **at least one character**.
- The `id` name **cannot start with a number**.
- The `id` name must **not contain spaces** (no spaces, tabs, or line breaks).

**Valid id examples:**

```html
<div id="mainContent">...</div>
<p id="intro-paragraph">...</div>
<h1 id="pageTitle">...</h1>
```

**Invalid id examples (these will cause problems):**

```html
<div id="main content">...</div>   <!-- NO: contains a space -->
<p id="1stParagraph">...</p>       <!-- NO: starts with a number -->
<h1 id="">...</h1>                  <!-- NO: empty value -->
```

---

## Part 3 – The Difference Between `class` and `id`

This is one of the most commonly confused topics for beginners. Here is a simple table:

| Feature | `class` | `id` |
|---|---|---|
| Can be used on multiple elements? | ✅ Yes | ❌ No — unique only |
| CSS selector symbol | `.` (dot) | `#` (hash) |
| Can one element have several? | ✅ Yes (`class="a b c"`) | ❌ No — only one id per element |
| Used for | Grouping similar elements | Identifying one specific element |
| JavaScript method | `getElementsByClassName()` | `getElementById()` |

**Analogy:**  
Think of a school. A `class` is like the school uniform — hundreds of students wear the same uniform. An `id` is like a student's unique admission number — only one student in the entire school has that number.

---

## Part 4 – HTML Bookmarks Using `id`

### What is a Bookmark Link?

When a webpage is very long — like a long tutorial, a legal document, or a recipe with many sections — it can be frustrating to scroll down manually to find the section you want. **Bookmark links** solve this.

A bookmark link is a clickable link that, when clicked, **jumps the page** directly to a specific section, rather than loading a new page.

**How bookmarks work:**

1. You give a target element an `id`.
2. You create a link with `href="#idName"` that points to that element.
3. When the user clicks the link, the browser scrolls to the element with that `id`.

### Example — Bookmarks on the Same Page

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body { font-family: Arial; }
    h2   { margin-top: 80px; }
  </style>
</head>
<body>

  <!-- Navigation links at the top of the page -->
  <p>Jump to a chapter:</p>
  <a href="#chapter1">Chapter 1 – Introduction</a><br>
  <a href="#chapter2">Chapter 2 – The Basics</a><br>
  <a href="#chapter3">Chapter 3 – Advanced Topics</a>

  <!-- Chapter sections far down the page -->
  <h2 id="chapter1">Chapter 1 – Introduction</h2>
  <p>This chapter introduces the topic with a broad overview...</p>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit...</p>

  <h2 id="chapter2">Chapter 2 – The Basics</h2>
  <p>Now we cover the foundational concepts in detail...</p>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit...</p>

  <h2 id="chapter3">Chapter 3 – Advanced Topics</h2>
  <p>Here we explore more complex ideas for experienced readers...</p>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit...</p>

</body>
</html>
```

**Expected Output:**

At the top of the page, there are three clickable links. Clicking "Chapter 1 – Introduction" scrolls the page instantly to the `<h2>` with `id="chapter1"`. Clicking Chapter 2 jumps to that heading, and so on.

**Breaking down the bookmark syntax:**

- `<h2 id="chapter1">Chapter 1 – Introduction</h2>` — The `id="chapter1"` marks this heading as the destination.
- `<a href="#chapter1">Chapter 1 – Introduction</a>` — The `#` before the id name in the `href` tells the browser "scroll to the element with id `chapter1`".

---

### Linking to a Bookmark on a Different Page

You can also link to a specific section **on a completely different page**. The syntax combines the page URL with the id:

```html
<a href="page2.html#chapter4">Go to Chapter 4 on Page 2</a>
```

When this link is clicked, the browser opens `page2.html` and automatically scrolls to the element with `id="chapter4"` on that page.

**Real-world use case:** Wikipedia uses this constantly. When you click a reference number at the bottom of a Wikipedia article, it jumps to that reference in the footnotes section — that is a bookmark link using `id`.

---

## Part 5 – Using `id` with JavaScript

Just like `class` works with `getElementsByClassName()`, the `id` attribute works with JavaScript's `getElementById()` method.

**What is `getElementById()`?**  
It is a JavaScript function that finds the **one exact element** with a given `id` and returns it, so you can then change it, read it, or interact with it.

### Example — Changing Text with JavaScript

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    #myHeader {
      background-color: lightblue;
      padding: 20px;
      text-align: center;
    }
  </style>
</head>
<body>

  <h1 id="myHeader">Original Heading Text</h1>
  <button onclick="changeText()">Click me to change the heading</button>

  <script>
    function changeText() {
      document.getElementById("myHeader").innerHTML = "Have a nice day!";
    }
  </script>

</body>
</html>
```

**Expected Output:**

- When the page loads, the heading reads "Original Heading Text" with a light-blue background.
- When the button is clicked, the heading text changes to "Have a nice day!".

**What the JavaScript does — line by line:**

- `function changeText() { ... }` — Defines a function called `changeText`.
- `document.getElementById("myHeader")` — Searches the page for the element with `id="myHeader"` and returns it. There is only one such element, so this is always a precise target.
- `.innerHTML = "Have a nice day!";` — Changes the text inside that element to the new text.

**Why is `id` important here?**  
Because `getElementById()` grabs exactly one element. If you used a class, you would get a list and have to loop through it. With `id`, it is instant and precise.

---

## Part 6 – Guided Practice Exercises

### Exercise 1 – Warm-Up: Style a Group with Class

**Objective:** Practice creating a CSS class and applying it to multiple elements.

**Scenario:** You are building a simple menu for a restaurant. You want all menu items to have the same card-like appearance.

**Steps:**

1. Open a new HTML file.
2. Create a CSS class called `.menu-item` with these styles:
   - `background-color: lightyellow`
   - `border: 2px solid orange`
   - `padding: 15px`
   - `margin: 10px`
3. Create four `<div>` elements, each with `class="menu-item"`, containing dish names such as: Jollof Rice, Pounded Yam, Egusi Soup, Fried Plantain.

**Expected Output:**

Four yellow boxes, each with an orange border and padding, displaying one dish name each.

**Hints:**
- Remember the `.` before the class name in CSS.
- The `margin` property adds space *outside* the element.
- The `border` property draws a visible border line.

**Solution:**

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .menu-item {
      background-color: lightyellow;
      border: 2px solid orange;
      padding: 15px;
      margin: 10px;
    }
  </style>
</head>
<body>

  <div class="menu-item">Jollof Rice</div>
  <div class="menu-item">Pounded Yam</div>
  <div class="menu-item">Egusi Soup</div>
  <div class="menu-item">Fried Plantain</div>

</body>
</html>
```

**Self-check questions:**
- What happens if you add a fifth `<div>` with `class="menu-item"`? Does it automatically get the styling? (Yes — that is the power of class!)
- What would you change if you wanted a green border instead of orange?

---

### Exercise 2 – Multiple Classes

**Objective:** Practice applying more than one class to a single element.

**Scenario:** A school website has student profile cards. Most cards look the same, but the top student's card should also have a gold background and larger text.

**Steps:**

1. Create a CSS class `.card` with a light-grey background, padding, and a border.
2. Create a second CSS class `.top-student` with a gold background colour (`goldenrod`) and a larger font size (20px).
3. Create four student `<div>` elements. The first one should have `class="card top-student"`, the rest should just have `class="card"`.

**Expected Output:**

- First card: gold background, larger text.
- Other three cards: grey background, normal text.

**Solution:**

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .card {
      background-color: lightgrey;
      padding: 15px;
      border: 1px solid black;
      margin: 8px;
    }
    .top-student {
      background-color: goldenrod;
      font-size: 20px;
    }
  </style>
</head>
<body>

  <div class="card top-student">Amara – Top Student 🏆</div>
  <div class="card">Bola</div>
  <div class="card">Chidi</div>
  <div class="card">Dami</div>

</body>
</html>
```

**Self-check questions:**
- What order does the browser apply the two classes in?
- What happens if `.top-student` also sets `color: white`?

---

### Exercise 3 – Styling with `id`

**Objective:** Practice creating and using an `id` to style a unique element.

**Scenario:** A webpage has a special announcement banner at the top. Only one such banner exists on the page — it should have a red background, white text, and large centred text.

**Solution:**

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    #announcement {
      background-color: red;
      color: white;
      font-size: 24px;
      text-align: center;
      padding: 20px;
    }
  </style>
</head>
<body>

  <div id="announcement">⚠️ Important Announcement: School Closed Tomorrow</div>

  <p>Regular page content goes here...</p>
  <p>More content...</p>

</body>
</html>
```

**Expected Output:**

A red banner at the top with large white centred announcement text. The rest of the page below it is plain paragraph text.

**Self-check questions:**
- Can you add a second `<div id="announcement">` and get the same style? (Technically the browser shows both, but this is invalid HTML and will cause JavaScript bugs.)
- What is the CSS selector symbol for `id` vs `class`?

---

### Exercise 4 – Bookmark Navigation

**Objective:** Create an in-page navigation menu using `id` bookmarks.

**Scenario:** You are building a simple FAQ page with multiple questions. Users should be able to click on a question at the top to jump directly to the answer below.

**Solution:**

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body { font-family: Arial; }
    nav  { background-color: #f0f0f0; padding: 15px; margin-bottom: 20px; }
    h2   { margin-top: 100px; color: navy; }
    a    { display: block; margin-bottom: 8px; }
  </style>
</head>
<body>

  <nav>
    <strong>Frequently Asked Questions</strong><br><br>
    <a href="#q1">1. What is HTML?</a>
    <a href="#q2">2. What is CSS?</a>
    <a href="#q3">3. What is JavaScript?</a>
  </nav>

  <h2 id="q1">1. What is HTML?</h2>
  <p>HTML stands for HyperText Markup Language. It is the standard language
  for building the structure of web pages. Every website you visit is built
  with HTML at its foundation.</p>

  <h2 id="q2">2. What is CSS?</h2>
  <p>CSS stands for Cascading Style Sheets. It is the language used to control
  the appearance of HTML elements — including colours, fonts, spacing, and layout.</p>

  <h2 id="q3">3. What is JavaScript?</h2>
  <p>JavaScript is a programming language that adds interactivity to web pages.
  It can respond to user actions, update content dynamically, and communicate
  with servers.</p>

</body>
</html>
```

**Expected Output:**

A grey navigation panel at the top with three clickable links. Clicking each link scrolls the page directly to that question's heading and answer.

**Self-check questions:**
- What is the `href` value pattern for a bookmark link?
- What would happen if you used `href="q1"` without the `#`?

---

## Part 7 – Mini Project: Student Grade Report Card Page

### Project Overview

You will build a simple student grade report card webpage that uses both `class` and `id` attributes together. The page will have a unique page header (using `id`), styled grade cards for each subject (using `class`), highlighted failing and passing grades (using multiple classes), and a quick navigation menu (using `id` bookmarks).

This simulates what a real school system interface might look like.

---

### Stage 1 – Setup the Page Structure

Start with a basic HTML page:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Student Report Card</title>
</head>
<body>

  <h1>Student Report Card</h1>

</body>
</html>
```

**Milestone output:** A plain page with the heading "Student Report Card".

---

### Stage 2 – Add the Unique Page Header Using `id`

Add a styled header at the top using `id`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Student Report Card</title>
  <style>
    #report-header {
      background-color: navy;
      color: white;
      text-align: center;
      padding: 30px;
      font-family: Arial, sans-serif;
    }
    #report-header p {
      margin: 4px 0;
      font-size: 14px;
    }
  </style>
</head>
<body>

  <div id="report-header">
    <h1>📋 Student Report Card</h1>
    <p>Student: Amara Okafor</p>
    <p>Class: Year 10B &nbsp;|&nbsp; Term: Second Term &nbsp;|&nbsp; Year: 2025</p>
  </div>

</body>
</html>
```

**Milestone output:** A navy-blue banner header with white text showing the student's name, class, term, and year.

---

### Stage 3 – Add Subject Cards Using `class`

Add styled subject grade cards. Passing grades get one class, failing grades get an additional class:

```html
  <style>
    /* ... previous styles ... */

    body {
      font-family: Arial, sans-serif;
      background-color: #f5f5f5;
    }

    .subject-card {
      background-color: white;
      border: 1px solid #ccc;
      border-left: 5px solid navy;
      padding: 15px 20px;
      margin: 10px 20px;
      border-radius: 4px;
    }
    .subject-card h3 {
      margin: 0 0 5px 0;
      color: navy;
    }
    .subject-card p {
      margin: 2px 0;
    }

    .grade-pass {
      border-left-color: green;
    }
    .grade-fail {
      border-left-color: red;
      background-color: #fff0f0;
    }
  </style>
```

Now add the subject cards to the `<body>`:

```html
  <div class="subject-card grade-pass">
    <h3>Mathematics</h3>
    <p>Score: 85 / 100</p>
    <p>Grade: A</p>
    <p>Remark: Excellent performance</p>
  </div>

  <div class="subject-card grade-pass">
    <h3>English Language</h3>
    <p>Score: 72 / 100</p>
    <p>Grade: B</p>
    <p>Remark: Good work, keep it up</p>
  </div>

  <div class="subject-card grade-fail">
    <h3>Chemistry</h3>
    <p>Score: 38 / 100</p>
    <p>Grade: F</p>
    <p>Remark: Needs significant improvement</p>
  </div>

  <div class="subject-card grade-pass">
    <h3>Geography</h3>
    <p>Score: 68 / 100</p>
    <p>Grade: B</p>
    <p>Remark: Satisfactory</p>
  </div>

  <div class="subject-card grade-fail">
    <h3>Biology</h3>
    <p>Score: 45 / 100</p>
    <p>Grade: D</p>
    <p>Remark: Below average, extra study needed</p>
  </div>
```

**Milestone output:**

Five subject cards. Passing subjects (Maths, English, Geography) have a green left border. Failing subjects (Chemistry, Biology) have a red left border and a pinkish background.

---

### Stage 4 – Add a Navigation Bookmark Menu and Summary Section

Add a quick-links navigation at the top and a unique summary section at the bottom:

```html
  <style>
    /* ... previous styles ... */

    #quick-nav {
      background-color: #e8e8e8;
      padding: 12px 20px;
      margin: 10px 20px;
    }
    #quick-nav a {
      margin-right: 15px;
      color: navy;
      text-decoration: none;
      font-weight: bold;
    }
    #summary-section {
      background-color: #fffbcc;
      border: 2px solid goldenrod;
      padding: 20px;
      margin: 10px 20px;
      border-radius: 4px;
    }
  </style>
```

Add the navigation just after the header and add the summary at the bottom:

```html
  <!-- Quick Navigation -->
  <div id="quick-nav">
    <strong>Quick Jump:</strong>
    <a href="#subjects">Subject Grades</a>
    <a href="#summary">Summary</a>
  </div>

  <!-- Subjects Section -->
  <h2 id="subjects">Subject Grades</h2>

  <!-- ... your subject cards here ... -->

  <!-- Summary Section -->
  <div id="summary-section">
    <h2 id="summary">📊 Term Summary</h2>
    <p><strong>Total Subjects:</strong> 5</p>
    <p><strong>Subjects Passed:</strong> 3</p>
    <p><strong>Subjects Failed:</strong> 2</p>
    <p><strong>Overall Average:</strong> 61.6%</p>
    <p><strong>Position in Class:</strong> 14 out of 35</p>
    <p><strong>Principal's Remark:</strong> A fair result. Amara must improve in Sciences next term.</p>
  </div>
```

---

### Final Complete Project Code

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Student Report Card</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f5f5f5;
      margin: 0;
    }

    /* Unique page header */
    #report-header {
      background-color: navy;
      color: white;
      text-align: center;
      padding: 30px;
    }
    #report-header p {
      margin: 4px 0;
      font-size: 14px;
    }

    /* Navigation bookmark bar */
    #quick-nav {
      background-color: #e8e8e8;
      padding: 12px 20px;
      margin: 10px 20px;
    }
    #quick-nav a {
      margin-right: 15px;
      color: navy;
      text-decoration: none;
      font-weight: bold;
    }

    /* Subject cards - shared class */
    .subject-card {
      background-color: white;
      border: 1px solid #ccc;
      border-left: 5px solid navy;
      padding: 15px 20px;
      margin: 10px 20px;
      border-radius: 4px;
    }
    .subject-card h3 {
      margin: 0 0 5px 0;
      color: navy;
    }

    /* Additional classes for grade outcome */
    .grade-pass {
      border-left-color: green;
    }
    .grade-fail {
      border-left-color: red;
      background-color: #fff0f0;
    }

    /* Unique summary section */
    #summary-section {
      background-color: #fffbcc;
      border: 2px solid goldenrod;
      padding: 20px;
      margin: 10px 20px;
      border-radius: 4px;
    }
  </style>
</head>
<body>

  <!-- Unique Page Header (id) -->
  <div id="report-header">
    <h1>📋 Student Report Card</h1>
    <p>Student: Amara Okafor</p>
    <p>Class: Year 10B &nbsp;|&nbsp; Term: Second Term &nbsp;|&nbsp; Year: 2025</p>
  </div>

  <!-- Bookmark Navigation (id) -->
  <div id="quick-nav">
    <strong>Quick Jump:</strong>
    <a href="#subjects">Subject Grades</a>
    <a href="#summary">Summary</a>
  </div>

  <!-- Subjects Section -->
  <h2 id="subjects" style="margin-left:20px;">Subject Grades</h2>

  <!-- Subject Cards (class + multiple classes) -->
  <div class="subject-card grade-pass">
    <h3>Mathematics</h3>
    <p>Score: 85 / 100 &nbsp;|&nbsp; Grade: A</p>
    <p>Remark: Excellent performance</p>
  </div>

  <div class="subject-card grade-pass">
    <h3>English Language</h3>
    <p>Score: 72 / 100 &nbsp;|&nbsp; Grade: B</p>
    <p>Remark: Good work, keep it up</p>
  </div>

  <div class="subject-card grade-fail">
    <h3>Chemistry</h3>
    <p>Score: 38 / 100 &nbsp;|&nbsp; Grade: F</p>
    <p>Remark: Needs significant improvement</p>
  </div>

  <div class="subject-card grade-pass">
    <h3>Geography</h3>
    <p>Score: 68 / 100 &nbsp;|&nbsp; Grade: B</p>
    <p>Remark: Satisfactory</p>
  </div>

  <div class="subject-card grade-fail">
    <h3>Biology</h3>
    <p>Score: 45 / 100 &nbsp;|&nbsp; Grade: D</p>
    <p>Remark: Below average, extra study needed</p>
  </div>

  <!-- Unique Summary Section (id) -->
  <div id="summary-section">
    <h2 id="summary">📊 Term Summary</h2>
    <p><strong>Total Subjects:</strong> 5</p>
    <p><strong>Subjects Passed:</strong> 3</p>
    <p><strong>Subjects Failed:</strong> 2</p>
    <p><strong>Overall Average:</strong> 61.6%</p>
    <p><strong>Position in Class:</strong> 14 out of 35</p>
    <p><strong>Principal's Remark:</strong> A fair result. Amara must improve in Sciences next term.</p>
  </div>

</body>
</html>
```

**Final Output:**

A fully styled student report card page with:
- A navy header banner (styled with `id`)
- Bookmark links that jump to sections
- Five subject cards sharing the `.subject-card` class
- Passing cards with a green border
- Failing cards with a red border and pink background
- A golden summary panel at the bottom (styled with `id`)

**Reflection questions:**
- Why did you use `id` for the header and summary, but `class` for the subject cards?
- What would you need to change to add a sixth subject?
- How would you add another class `.grade-top` for subjects scoring above 80?

**Optional challenge:** Add a JavaScript button that hides all failing subject cards using `getElementsByClassName("grade-fail")`.

---

## Part 8 – Common Beginner Mistakes

### Mistake 1 — Using `id` for Multiple Elements

**Wrong:**

```html
<h2 id="city">London</h2>
<h2 id="city">Paris</h2>
<h2 id="city">Tokyo</h2>
```

**Why it's wrong:** An `id` must be **unique** on a page. Using the same `id` on multiple elements breaks HTML validity and causes JavaScript's `getElementById()` to only find the first one.

**Correct:**

```html
<h2 class="city">London</h2>
<h2 class="city">Paris</h2>
<h2 class="city">Tokyo</h2>
```

Use `class` when multiple elements need the same style.

---

### Mistake 2 — Wrong Selector Symbol in CSS

**Wrong:**

```css
/* Trying to style a class but using # */
#city {
  background-color: tomato;
}
```

This would look for an element with `id="city"`, not `class="city"`.

**Correct:**

```css
/* Dot for class */
.city {
  background-color: tomato;
}

/* Hash for id */
#myHeader {
  background-color: lightblue;
}
```

---

### Mistake 3 — Space in Class or ID Names

**Wrong:**

```html
<div class="main content">...</div>
```

Wait — this is actually valid! A space between class names means the element has **two classes**: `main` and `content`. This is intentional for multiple classes.

But in `id`:

```html
<h1 id="my header">Wrong!</h1>
```

This is invalid. `id` values cannot contain spaces. The browser may interpret this as broken HTML.

**Correct:**

```html
<h1 id="my-header">Correct!</h1>
<h1 id="myHeader">Also correct!</h1>
```

---

### Mistake 4 — Forgetting the `#` in Bookmark `href`

**Wrong:**

```html
<a href="chapter1">Jump to Chapter 1</a>
```

Without the `#`, the browser thinks you are linking to a file named `chapter1`, not a bookmark on the current page.

**Correct:**

```html
<a href="#chapter1">Jump to Chapter 1</a>
```

---

### Mistake 5 — Case Sensitivity

**Wrong:**

```html
<style>
  .City { background-color: tomato; }
</style>

<h2 class="city">London</h2>
```

The CSS rule `.City` will not match `class="city"` because CSS class names are case sensitive.

**Correct:**

```html
<style>
  .city { background-color: tomato; }
</style>

<h2 class="city">London</h2>
```

Always use consistent capitalisation throughout your code.

---

### Mistake 6 — Starting an `id` with a Number

**Wrong:**

```html
<div id="1stSection">...</div>
```

**Correct:**

```html
<div id="firstSection">...</div>
<div id="section1">...</div>
```

`id` values must not start with a number. You can include numbers in the middle or end.

---

## Part 9 – Reflection Questions

Take a moment and think through these questions before moving on:

1. What is the main purpose of the `class` attribute? What problem does it solve?
2. What is the main purpose of the `id` attribute? How is it different from `class`?
3. If you have a webpage with 20 blog post cards, all looking identical, would you use `class` or `id`? Why?
4. If you have a single navigation bar at the top of the page, would you use `class` or `id`? Why?
5. What CSS selector symbol is used for `class`? What symbol is used for `id`?
6. Can an element have both a `class` and an `id` at the same time? What would that look like?
7. How do you create a bookmark link that jumps to a section of the same page?
8. What JavaScript method finds elements by class name? What method finds an element by `id`?
9. If a CSS rule for `class` and a CSS rule for `id` both target the same element, which one is more specific (takes priority)?
10. Why is it bad practice to use the same `id` on multiple elements?

---

## Completion Checklist

Before moving on to the next lesson, confirm you can do all of the following:

- [ ] I understand what the `class` attribute is and why it exists
- [ ] I can write a CSS rule using `.className { }` syntax
- [ ] I can add `class="name"` to an HTML element
- [ ] I can apply the same class to multiple elements
- [ ] I can assign multiple classes to one element using a space
- [ ] I understand that class is for groups; id is for unique single elements
- [ ] I can write a CSS rule using `#idName { }` syntax
- [ ] I can add `id="name"` to a single HTML element
- [ ] I understand the naming rules for `id` (unique, no spaces, no starting with a number)
- [ ] I can create a bookmark link using `href="#idName"`
- [ ] I understand how `getElementsByClassName()` works in JavaScript
- [ ] I understand how `getElementById()` works in JavaScript
- [ ] I can explain the difference between `class` and `id` clearly
- [ ] I completed at least two of the practice exercises
- [ ] I completed the mini-project

---

## Lesson Summary

In this lesson you learned two of HTML's most powerful organisational tools.

The **`class` attribute** allows you to group HTML elements together and apply the same CSS styles to all of them at once. You create a CSS rule with a `.` (dot) prefix, and then add `class="name"` to every element you want to style that way. Multiple elements can share the same class, and one element can have multiple classes (separated by spaces). JavaScript can target all elements of a class using `getElementsByClassName()`.

The **`id` attribute** gives a single HTML element a **unique identity** on the page. You create a CSS rule with a `#` (hash) prefix, and then add `id="name"` to the one element you want to target. No two elements on the same page should share the same `id`. IDs are also used to create **bookmark links** that scroll the page to a specific section, and JavaScript can find one exact element using `getElementById()`.

The core rule to remember:
- Use **`class`** → when you want to style **many elements** the same way.
- Use **`id`** → when you want to style or target **exactly one unique element**.

These two attributes form the backbone of how professional websites are structured, styled, and controlled with JavaScript. Mastering them now will make every future lesson easier.

---

*End of Lesson 19 – HTML `class` and `id` Attributes*
