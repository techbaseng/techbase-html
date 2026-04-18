---
render_with_liquid: false
title: "Lesson 7: HTML Styles — Making Your Web Pages Look Great"
nav_order: 7
---

# Lesson 7: HTML Styles — Making Your Web Pages Look Great

---

## Lesson Introduction

So far in this course, you have been building HTML pages that show text and content on a screen — but everything has probably looked very plain and unstyled. In this lesson, you are going to learn something really exciting: **how to add style to your HTML elements**.

Style means things like:
- Changing the **colour** of text
- Changing the **background colour** of a page or section
- Changing the **font** (the look of the letters)
- Changing the **size** of text
- Aligning text to the left, centre, or right

All of this is done using something called the **`style` attribute** in HTML, combined with instructions from a language called **CSS** (Cascading Style Sheets). You do not need to know CSS in depth right now — this lesson will teach you exactly what you need, step by step.

By the end of this lesson, you will be able to look at a plain HTML page and transform it into something that looks clean, readable, and professional.

> 💡 **Real-World Connection:** Every website you see — whether it is a news website, a social media app, a school portal, or an online shop — uses styles to make content readable and attractive. Styling is one of the most important skills in web development.

---

## Prerequisite Concepts

Before we begin, let's make sure you understand two important ideas that this lesson builds on.

### What Is an HTML Attribute?

An **attribute** is extra information you add inside an HTML opening tag. It changes how the element behaves or looks.

You have already seen attributes like this:

```html
<p class="intro">Hello World</p>
```

In the example above:
- `class` is the **attribute name**
- `"intro"` is the **attribute value**

The `style` attribute works the same way — it is just another attribute you place inside an opening tag.

### What Is CSS?

**CSS** stands for **Cascading Style Sheets**. It is a language used to describe how HTML elements should look. CSS controls colours, fonts, sizes, spacing, layout, and much more.

You will learn CSS in full detail in a later course. For now, you just need to know that CSS uses a very simple format called a **property: value** pair:

```
property: value
```

For example:
- `color: red` → makes text red
- `font-size: 20px` → makes text 20 pixels tall
- `background-color: blue` → makes the background blue

---

## Part 1: Understanding the HTML `style` Attribute

### What Is It?

The HTML `style` attribute allows you to apply CSS directly to a single HTML element. Think of it as "giving instructions about appearance" directly to one specific tag.

**The syntax (the pattern you follow) looks like this:**

```html
<tagname style="property: value;">
```

Let's break every part of this down:

| Part | What It Means |
|------|--------------|
| `tagname` | Any HTML element, like `<p>`, `<h1>`, `<body>` |
| `style=` | Tells the browser: "I want to apply a visual style" |
| `"..."` | The quote marks wrap your CSS instructions |
| `property` | What aspect you want to change (colour, size, font, etc.) |
| `:` | A colon separates the property from its value |
| `value` | What you want to set it to (red, 20px, center, etc.) |
| `;` | A semicolon ends each CSS instruction |

> 💡 **Analogy:** Think of the `style` attribute like a sticky note you attach to a piece of furniture — it tells the decorator exactly how to finish that one item.

### Your Very First Style Example

```html
<p style="color: blue;">This text is blue.</p>
```

**Expected Output:**
> <span style="color:blue">This text is blue.</span> *(the text appears in blue colour)*

That is all there is to it! You added the `style` attribute, wrote the property `color`, set its value to `blue`, and the browser turned that text blue.

---

## Part 2: Background Colour — `background-color`

### What Is It?

The `background-color` property sets the background colour of an HTML element. You can use it on any element — the whole page body, a heading, a paragraph, or a `<div>`.

### Why Does This Matter?

Background colours help:
- Separate sections of a page visually
- Create contrast so text is readable
- Highlight important information
- Make pages look polished and branded

### Example 1 — Set the Background of the Whole Page

To change the background colour of the **entire page**, you apply the style to the `<body>` tag:

```html
<!DOCTYPE html>
<html>
<body style="background-color: powderblue;">

  <h1>This is a heading</h1>
  <p>This is a paragraph.</p>

</body>
</html>
```

**Expected Output:**
> The entire webpage background turns a soft blue colour called "powderblue". The heading and paragraph sit on top of this blue background.

**Line-by-line explanation:**
- `<body style="background-color: powderblue;">` — The `<body>` tag wraps all visible content. Adding `background-color: powderblue;` makes the whole page background that colour.
- `powderblue` is a named CSS colour. CSS has over 140 built-in named colours you can use.

### Example 2 — Set Different Backgrounds on Different Elements

You can apply `background-color` to individual elements too:

```html
<!DOCTYPE html>
<html>
<body>

  <h1 style="background-color: powderblue;">This is a heading</h1>
  <p style="background-color: tomato;">This is a paragraph.</p>

</body>
</html>
```

**Expected Output:**
> The heading has a soft blue background.
> The paragraph has a tomato-red background.
> The rest of the page stays white (the default).

> 🤔 **Think About It:** What happens if you change `tomato` to `yellow`? Try it! What other colour names do you know?

### Quick List of Popular CSS Named Colours

Here are some colour names you can try right away:

`red`, `blue`, `green`, `yellow`, `orange`, `purple`, `pink`, `black`, `white`, `gray`, `tomato`, `powderblue`, `lightgreen`, `coral`, `gold`, `salmon`, `lavender`, `teal`

---

## Part 3: Text Colour — `color`

### What Is It?

The `color` property in CSS controls the **colour of the text** inside an element.

> ⚠️ **Important Spelling Note:** CSS uses the American spelling `color` (without a 'u'), **not** `colour`. If you spell it `colour`, it will not work!

### Example 1 — Simple Text Colour

```html
<h1 style="color: blue;">This is a heading</h1>
<p style="color: red;">This is a paragraph.</p>
```

**Expected Output:**
> Heading text appears in blue.
> Paragraph text appears in red.

### Example 2 — Multiple Colours Together

```html
<!DOCTYPE html>
<html>
<body>

  <h1 style="color: navy;">Welcome to My Website</h1>
  <p style="color: green;">This is an important paragraph.</p>
  <p style="color: gray;">This is a less important note.</p>

</body>
</html>
```

**Expected Output:**
> The heading is navy (dark blue).
> First paragraph is green.
> Second paragraph is gray.

> 💡 **Design Tip:** On real websites, designers carefully choose text colours to make sure there is enough **contrast** (difference) between the text colour and the background colour so that everyone can read it easily. Dark text on a light background is usually easiest to read.

---

## Part 4: Font — `font-family`

### What Is It?

The `font-family` property changes the **typeface** — the visual style of the letters. Different fonts give your text a completely different feel.

Think of fonts like handwriting styles — one person writes in neat print, another in flowing cursive. Fonts work the same way.

### Why Does Font Choice Matter?

- Fonts affect **readability** — some fonts are easier to read on screens
- Fonts affect **tone** — a fun font feels casual, a clean sans-serif font feels modern and professional
- Fonts are a core part of branding and design

### Example 1 — Changing the Font of a Heading

```html
<h1 style="font-family: verdana;">This is a heading</h1>
<p style="font-family: courier;">This is a paragraph.</p>
```

**Expected Output:**
> The heading appears in **Verdana** font — a clean, modern sans-serif typeface.
> The paragraph appears in **Courier** font — a typewriter-style monospace font.

**Line-by-line explanation:**
- `font-family: verdana;` — tells the browser to use the Verdana font for this element.
- `font-family: courier;` — tells the browser to use the Courier font (looks like old typewriter text).

### Common Web-Safe Fonts

These fonts are available on almost all computers and devices:

| Font Name | Style Description |
|-----------|------------------|
| `Arial` | Clean, modern, easy to read |
| `Verdana` | Wide letters, great on screens |
| `Helvetica` | Classic, professional |
| `Georgia` | Elegant, serif style |
| `Courier` | Typewriter / monospace style |
| `Times New Roman` | Traditional newspaper style |
| `Trebuchet MS` | Friendly and modern |

> 🤔 **Think About It:** What font does your favourite website use? How does it affect the feel of the site?

---

## Part 5: Text Size — `font-size`

### What Is It?

The `font-size` property controls **how big or small the text appears**. You can specify size in several units, but the two most common for beginners are:

- **Pixels (`px`)** — an exact size in screen pixels. Example: `font-size: 20px;`
- **Percentage (`%`)** — a size relative to the default. Example: `font-size: 150%;` means 150% of the normal size.

### Why Does Text Size Matter?

- Headings should be bigger than body text to create visual hierarchy
- Small text can be hard to read, especially on mobile devices
- Good sizing makes content easier to scan and understand

### Example 1 — Using Percentage for Font Size

```html
<h1 style="font-size: 300%;">This is a heading</h1>
<p style="font-size: 160%;">This is a paragraph.</p>
```

**Expected Output:**
> The heading is 3 times (300%) the default font size — very large.
> The paragraph is 1.6 times (160%) the default size — noticeably larger than normal.

**Understanding percentages:**
- Default text is 100% (usually 16px on most browsers)
- `200%` = twice as big
- `50%` = half as big
- `300%` = three times as big

### Example 2 — Using Pixels for Font Size

```html
<h1 style="font-size: 40px;">Big Heading</h1>
<p style="font-size: 16px;">Normal paragraph text.</p>
<p style="font-size: 12px;">Small fine print text.</p>
```

**Expected Output:**
> Heading appears large (40 pixels tall).
> First paragraph is normal size (16 pixels).
> Second paragraph is smaller (12 pixels — fine print style).

> 🤔 **Think About It:** What happens if you set `font-size: 5px;`? Can you still read it?

---

## Part 6: Text Alignment — `text-align`

### What Is It?

The `text-align` property controls where the text sits **horizontally** within its element. There are three main values:

| Value | What It Does |
|-------|-------------|
| `left` | Aligns text to the left (this is the default) |
| `center` | Centres the text in the middle |
| `right` | Aligns text to the right |

### Why Does Text Alignment Matter?

- Page titles and headings often look better **centred**
- Body paragraphs are usually **left-aligned** for readability
- Prices, dates, or labels in tables are sometimes **right-aligned**
- Alignment gives your page structure and visual balance

### Example 1 — Centre-Aligned Heading and Paragraph

```html
<h1 style="text-align: center;">Centered Heading</h1>
<p style="text-align: center;">Centered paragraph.</p>
```

**Expected Output:**
> Both the heading and the paragraph are horizontally centred on the page.

### Example 2 — All Three Alignment Values Together

```html
<!DOCTYPE html>
<html>
<body>

  <h1 style="text-align: center;">Welcome to My Page</h1>
  <p style="text-align: left;">This paragraph is aligned to the left.</p>
  <p style="text-align: right;">This paragraph is aligned to the right.</p>

</body>
</html>
```

**Expected Output:**
> Heading: appears in the centre of the page.
> First paragraph: text starts from the left.
> Second paragraph: text ends at the right.

> 💡 **Design Tip:** On professional websites, headings and banners are often centred, while article body text is left-aligned. This combination makes pages very readable.

---

## Part 7: Combining Multiple Style Properties

So far you have used one style property at a time. In real web development, you will almost always combine multiple properties together. You can do this by separating each property-value pair with a semicolon (`;`).

### The Pattern

```html
<tagname style="property1: value1; property2: value2; property3: value3;">
```

### Example 1 — Heading with Colour, Font, and Size

```html
<h1 style="color: white; background-color: navy; font-family: verdana; font-size: 200%; text-align: center;">
  My Styled Heading
</h1>
```

**Expected Output:**
> A large centred heading with white text, a navy blue background, and Verdana font — at double the default size.

**Line-by-line breakdown:**
- `color: white;` — text is white
- `background-color: navy;` — background is dark blue
- `font-family: verdana;` — uses the Verdana font
- `font-size: 200%;` — twice the normal size
- `text-align: center;` — text is centred

### Example 2 — A Full Styled Page

```html
<!DOCTYPE html>
<html>
<body style="background-color: lightyellow;">

  <h1 style="color: darkgreen; text-align: center; font-family: verdana;">
    Student Report Card
  </h1>

  <p style="color: navy; font-size: 120%; font-family: arial;">
    Student: Amara Obi
  </p>

  <p style="color: navy; font-size: 120%; font-family: arial;">
    Grade: JSS 2
  </p>

  <p style="color: red; font-size: 110%;">
    Result: Outstanding — top of the class!
  </p>

</body>
</html>
```

**Expected Output:**
> - Page background: light yellow
> - Heading: dark green, centred, Verdana font
> - Student name and grade: navy text, slightly larger than normal, Arial font
> - Result line: red text

---

## Part 8: Quick Reference — The Five Core Style Properties

Here is a summary table of everything you have learned:

| CSS Property | What It Controls | Example Value |
|---|---|---|
| `background-color` | Background colour of an element | `powderblue`, `tomato`, `#ff0000` |
| `color` | Colour of the text | `blue`, `red`, `green` |
| `font-family` | The font/typeface used | `verdana`, `arial`, `courier` |
| `font-size` | The size of the text | `16px`, `200%`, `2em` |
| `text-align` | Horizontal alignment of text | `left`, `center`, `right` |

---

## Guided Practice Exercises

Now it is time to practise what you have learned. These exercises follow a progressive path: warm-up → structured task → challenge.

---

### Exercise 1: Warm-Up — Your First Styled Page

**Objective:** Apply one style property to three different elements.

**Instructions:**
1. Open a new HTML file
2. Create a `<body>` tag with a light background colour
3. Inside the body, add an `<h1>` tag with blue text
4. Add a `<p>` tag with red text

**Starter template:**

```html
<!DOCTYPE html>
<html>
<body style="___: lightblue;">

  <h1 style="___: blue;">Hello, World!</h1>
  <p style="___: red;">This is my first styled paragraph.</p>

</body>
</html>
```

**Fill in the blanks with the correct CSS property names.**

**Expected Output:**
> Light blue page background. Blue heading text. Red paragraph text.

**Answer:**

```html
<!DOCTYPE html>
<html>
<body style="background-color: lightblue;">

  <h1 style="color: blue;">Hello, World!</h1>
  <p style="color: red;">This is my first styled paragraph.</p>

</body>
</html>
```

**Self-Check Questions:**
- What is the name of the property that changes text colour?
- What is the name of the property that changes background colour?
- Where exactly does the `style` attribute go in the HTML tag?

---

### Exercise 2: Structured Task — Style a School Notice

**Scenario:** You are creating a digital school notice for your school's website. The notice must be easy to read and look professional.

**Requirements:**
- Page background: `lightyellow`
- Notice title (`<h1>`): text colour `darkred`, centred, font `verdana`
- Date (`<p>`): text colour `gray`, font size `90%`
- Body text (`<p>`): text colour `black`, font `arial`, font size `110%`
- Footer note (`<p>`): text colour `green`, right-aligned

**Your Task — Write the complete HTML:**

```html
<!DOCTYPE html>
<html>
<body style="background-color: lightyellow;">

  <h1 style="color: ___; text-align: ___; font-family: ___ ;">
    IMPORTANT SCHOOL NOTICE
  </h1>

  <p style="color: ___; font-size: ___ ;">
    Date: Monday, 14th April 2025
  </p>

  <p style="color: ___; font-family: ___; font-size: ___ ;">
    All students are reminded that the end-of-term examination 
    begins next Monday. Please come prepared with your stationery 
    and school ID card.
  </p>

  <p style="color: ___; text-align: ___ ;">
    — School Administration
  </p>

</body>
</html>
```

**Expected Output:**
> A styled notice with a yellow page background, dark red centred heading, grey small date, black body text in Arial, and a right-aligned green footer.

**Full Answer:**

```html
<!DOCTYPE html>
<html>
<body style="background-color: lightyellow;">

  <h1 style="color: darkred; text-align: center; font-family: verdana;">
    IMPORTANT SCHOOL NOTICE
  </h1>

  <p style="color: gray; font-size: 90%;">
    Date: Monday, 14th April 2025
  </p>

  <p style="color: black; font-family: arial; font-size: 110%;">
    All students are reminded that the end-of-term examination 
    begins next Monday. Please come prepared with your stationery 
    and school ID card.
  </p>

  <p style="color: green; text-align: right;">
    — School Administration
  </p>

</body>
</html>
```

**Self-Check Questions:**
- How do you apply multiple CSS properties inside one `style` attribute?
- What separates individual property-value pairs?
- What would happen if you forgot the semicolon between two properties?

---

### Exercise 3: Challenge — What-If Experimentation

Take the school notice from Exercise 2 and make these changes one at a time. After each change, observe what happens:

1. Change the heading `color` to `purple` — what changes?
2. Change `font-size: 90%` to `font-size: 200%` on the date — what happens?
3. Change the body text `text-align` to `center` — does it look better or worse?
4. Change the footer `color` to `tomato` — can you still read it on a yellow background?
5. Remove the `background-color` from `<body>` entirely — what does the page look like now?

> 🤔 **Reflection:** Which combination of background and text colours was easiest to read? Which was hardest?

---

## Mini-Project: Build a Styled Personal Profile Page

Now you will bring together everything from this lesson to build a **personal profile page** — like the "About Me" section of a website or social media profile.

### Stage 1: Setup — Create the Page Skeleton

Start with a basic HTML page:

```html
<!DOCTYPE html>
<html>
<body>

  <h1>My Name</h1>
  <h2>About Me</h2>
  <p>Bio text goes here.</p>

  <h2>My Favourite Things</h2>
  <p>Favourites go here.</p>

  <h2>My Goal</h2>
  <p>Goal text goes here.</p>

</body>
</html>
```

**Milestone 1 Output:** A plain white page with unstyled text. Ugly, but functional!

---

### Stage 2: Core Logic — Add Styles

Now enhance the page by applying the five CSS properties you have learned.

**Requirements:**
- Body: background colour of your choice (pick something you like!)
- `<h1>` (your name): large, centred, coloured text, nice font
- `<h2>` headings: a colour that works well with your background
- Paragraph text: readable font, comfortable size

```html
<!DOCTYPE html>
<html>
<body style="background-color: lightcyan;">

  <h1 style="color: darkblue; text-align: center; font-family: verdana; font-size: 250%;">
    Amara Obi
  </h1>

  <h2 style="color: teal; font-family: verdana;">About Me</h2>
  <p style="color: black; font-family: arial; font-size: 110%;">
    Hi! I am a JSS 2 student who loves science, mathematics, and football.
    I enjoy coding and hope to build websites and apps in the future.
  </p>

  <h2 style="color: teal; font-family: verdana;">My Favourite Things</h2>
  <p style="color: black; font-family: arial; font-size: 110%;">
    Football, reading science books, music, and spending time with family.
  </p>

  <h2 style="color: teal; font-family: verdana;">My Goal</h2>
  <p style="color: darkgreen; font-family: arial; font-size: 110%; font-style: italic;">
    To become a software engineer and build solutions that help people in Nigeria and across Africa.
  </p>

</body>
</html>
```

**Milestone 2 Output:**
> A colourful, styled profile page with a cyan background, dark blue large name at the top, teal section headings, and readable black paragraph text.

---

### Stage 3: Enhancement — Style the Footer

Add a footer at the bottom with your contact info (or a made-up contact for practice):

```html
  <p style="color: gray; font-size: 85%; text-align: center;">
    Contact: amara@myschool.edu.ng | Lagos, Nigeria
  </p>
```

**Milestone 3 Output:**
> A small, grey, centred footer at the bottom of the page.

---

### Stage 4: Final Output — Complete Profile Page

Here is the full completed project:

```html
<!DOCTYPE html>
<html>
<body style="background-color: lightcyan;">

  <h1 style="color: darkblue; text-align: center; font-family: verdana; font-size: 250%;">
    Amara Obi
  </h1>

  <h2 style="color: teal; font-family: verdana;">About Me</h2>
  <p style="color: black; font-family: arial; font-size: 110%;">
    Hi! I am a JSS 2 student who loves science, mathematics, and football.
    I enjoy coding and hope to build websites and apps in the future.
  </p>

  <h2 style="color: teal; font-family: verdana;">My Favourite Things</h2>
  <p style="color: black; font-family: arial; font-size: 110%;">
    Football, reading science books, music, and spending time with family.
  </p>

  <h2 style="color: teal; font-family: verdana;">My Goal</h2>
  <p style="color: darkgreen; font-family: arial; font-size: 110%;">
    To become a software engineer and build solutions that help people
    in Nigeria and across Africa.
  </p>

  <p style="color: gray; font-size: 85%; text-align: center;">
    Contact: amara@myschool.edu.ng | Lagos, Nigeria
  </p>

</body>
</html>
```

**Final Project Reflection Questions:**
1. Which part of styling did you find most interesting?
2. What would you change about the colours or fonts you chose?
3. How could you use what you learned here to improve a real project?

**Optional Extensions:**
- Can you add a second background colour for just one `<h2>`?
- Can you make one paragraph bigger than all the others using `font-size`?
- Can you find and use two CSS colour names that you had never heard of before?

---

## Common Beginner Mistakes

These are the most frequent errors beginners make when using the `style` attribute. Study each one carefully!

---

### Mistake 1: Spelling `color` as `colour`

```html
<!-- WRONG -->
<p style="colour: red;">This is red.</p>

<!-- CORRECT -->
<p style="color: red;">This is red.</p>
```

CSS uses American English. `colour` will be ignored by the browser. No error message will appear — the text just won't change colour.

---

### Mistake 2: Forgetting the Colon Between Property and Value

```html
<!-- WRONG -->
<p style="color red;">This is wrong.</p>

<!-- CORRECT -->
<p style="color: red;">This is correct.</p>
```

The colon `:` is mandatory. Without it, the browser cannot understand your instruction and will ignore the whole style.

---

### Mistake 3: Forgetting the Semicolon Between Multiple Properties

```html
<!-- WRONG -->
<p style="color: red font-size: 20px;">Text</p>

<!-- CORRECT -->
<p style="color: red; font-size: 20px;">Text</p>
```

When you write more than one CSS property, each one must end with a semicolon `;`. Without it, the browser may apply only the first property and ignore the rest.

---

### Mistake 4: Forgetting to Close the Quotes Around the Style Value

```html
<!-- WRONG -->
<p style="color: red>This is wrong.</p>

<!-- CORRECT -->
<p style="color: red;">This is correct.</p>
```

The `style` attribute value must always be inside matching quotation marks. An unclosed quote can break not just this element but the entire page layout.

---

### Mistake 5: Using `font-family` Names That Don't Exist or Aren't Installed

```html
<!-- RISKY — font might not be installed on all devices -->
<p style="font-family: MyFancyFont;">Text</p>

<!-- SAFER — use well-known web-safe fonts -->
<p style="font-family: arial;">Text</p>
```

If you use a font name that doesn't exist on the user's computer, the browser will fall back to its default font. Always use well-known web-safe fonts for beginners' projects.

---

### Mistake 6: Putting the `style` Attribute on a Closing Tag

```html
<!-- WRONG -->
<p>Hello</p style="color: red;">

<!-- CORRECT -->
<p style="color: red;">Hello</p>
```

Attributes go in the **opening** tag only, never in the closing tag.

---

### Mistake 7: Writing `text-align: middle` Instead of `text-align: center`

```html
<!-- WRONG -->
<p style="text-align: middle;">Centred text</p>

<!-- CORRECT -->
<p style="text-align: center;">Centred text</p>
```

The correct value for horizontal centring is `center` (American spelling), not `middle`. The value `middle` is used in different contexts (for vertical alignment in tables).

---

## Reflection Questions

Take a moment to think about what you have learned before moving on:

1. What is the `style` attribute and where does it go?
2. Name the five CSS properties you learned in this lesson and what each one controls.
3. What symbol separates a CSS property from its value?
4. What symbol separates multiple CSS properties when you write more than one?
5. Why is it important to choose colours carefully on a web page?
6. What is the difference between `color` and `background-color`?
7. In real life, can you think of a website where the font choice makes a big difference to how it feels?
8. If a user's computer doesn't have the font you specified, what happens?

---

## Completion Checklist

Before moving to Lesson 8, check that you can confidently say yes to all of these:

- [ ] I understand what the `style` attribute is and how to write it correctly
- [ ] I can apply `background-color` to change the background of a page or element
- [ ] I can apply `color` to change text colour
- [ ] I can apply `font-family` to change the font of text
- [ ] I can apply `font-size` to make text bigger or smaller
- [ ] I can apply `text-align` to align text left, centre, or right
- [ ] I can combine multiple CSS properties in one `style` attribute
- [ ] I know the difference between `color` and `colour` in CSS
- [ ] I always use a colon after the property name and a semicolon after the value
- [ ] I completed the school notice exercise
- [ ] I completed the personal profile mini-project
- [ ] I understand at least 5 common beginner mistakes and how to avoid them

---

## Lesson Summary

In this lesson you learned how to use the **HTML `style` attribute** to control the visual appearance of individual HTML elements. Here is a recap of everything covered:

**The `style` attribute** goes inside an HTML opening tag and accepts CSS property-value pairs:

```html
<tagname style="property: value; property: value;">
```

**The five core CSS properties you learned:**

1. **`background-color`** — Sets the background colour of an element or the entire page
   ```html
   <body style="background-color: powderblue;">
   ```

2. **`color`** — Sets the text colour of an element
   ```html
   <h1 style="color: blue;">
   ```

3. **`font-family`** — Sets the font/typeface of text
   ```html
   <p style="font-family: verdana;">
   ```

4. **`font-size`** — Sets the size of text (in `px` or `%`)
   ```html
   <h1 style="font-size: 300%;">
   ```

5. **`text-align`** — Aligns text horizontally (`left`, `center`, `right`)
   ```html
   <h1 style="text-align: center;">
   ```

**Combining multiple properties:**

```html
<h1 style="color: white; background-color: navy; font-family: verdana; font-size: 200%; text-align: center;">
  My Heading
</h1>
```

**Key rules to remember:**
- Always use a **colon** (`:`) between property and value
- Always use a **semicolon** (`;`) after each property-value pair
- CSS uses **American English** spelling: `color`, not `colour`; `center`, not `centre`
- The `style` attribute always goes in the **opening** tag

---

> 🎉 **Congratulations!** You have completed Lesson 7. Your HTML pages can now come to life with colour, typography, and alignment. In the next lesson, you will learn about **HTML Text Formatting** — including how to make text bold, italic, underlined, and more!
