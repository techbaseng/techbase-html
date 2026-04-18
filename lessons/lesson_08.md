---
render_with_liquid: false
title: "Lesson 8: HTML Text Formatting"
nav_order: 8
---

# Lesson 8: HTML Text Formatting

---

## Lesson Introduction

Imagine you are reading a textbook. Some words are **bold** to show they are important. Some terms are written in *italics* because they come from another language. Some numbers appear like this: H₂O — where the "2" sits below the normal line of text. Some answers appear with a ~~strikethrough~~ because they have been corrected.

All of these are examples of **text formatting** — giving text a special visual appearance to communicate meaning.

In HTML, you can do all of these things using special **formatting tags**. These are simple HTML elements that wrap around your text and tell the browser exactly how that piece of text should look or how important it is.

In this lesson, you will learn every HTML formatting element from scratch, understand what each one does, why it exists, and practise using all of them with clear examples and a hands-on mini project.

By the end of this lesson, you will be able to:
- Use bold, italic, highlighted, small, strikethrough, inserted, subscript, and superscript text in HTML
- Understand the difference between **visual** formatting tags and **semantic** (meaning-based) formatting tags
- Apply formatting correctly in realistic web pages
- Avoid the most common beginner mistakes

---

## Prerequisite Concepts

Before we dive in, let's make sure you are comfortable with three foundational ideas from earlier lessons.

### What is an HTML Tag?

An HTML tag is a special instruction wrapped in angle brackets that tells the browser what to do with content.

```html
<p>This is a paragraph.</p>
```

- `<p>` is the **opening tag** — it starts the paragraph
- `This is a paragraph.` is the **content**
- `</p>` is the **closing tag** — it ends the paragraph

The browser reads the opening tag, applies its rules to the content, then stops when it sees the closing tag.

### What is Nesting?

Nesting means placing one tag inside another. Think of it like boxes inside boxes.

```html
<p>This is <b>bold</b> inside a paragraph.</p>
```

Here, the `<b>` tag is **nested inside** the `<p>` tag. The bold formatting applies only to the word "bold", while the paragraph wraps around everything.

### What Does "Inline" Mean?

An inline element sits **within** a line of text. It does not create a new line or new block. Formatting tags like `<b>`, `<i>`, `<mark>`, and others are all **inline elements** — they affect only the text they wrap, without breaking the flow of the surrounding sentence.

```html
<p>I love <b>HTML</b> because it is powerful.</p>
```

**Output:**
> I love **HTML** because it is powerful.

The bold applies only to "HTML". The rest of the sentence is unchanged.

---

## Conceptual Understanding: What Are Formatting Elements?

HTML **formatting elements** are tags specifically designed to give text a special appearance or special meaning.

There are **two types** of formatting, and it is very important to understand the difference.

### Type 1: Visual Formatting (Presentational)

These tags simply change how text looks. They have no deeper meaning — they just style the text visually.

Examples: `<b>` (bold), `<i>` (italic)

### Type 2: Semantic Formatting (Meaningful)

These tags not only change how text looks — they also carry **meaning**. They tell the browser (and tools like screen readers for blind users) something important about the text.

Examples: `<strong>` (important text), `<em>` (emphasized text)

> 💡 **Why does this matter?**
> Screen readers (software used by visually impaired people) will read `<strong>` text with a strong, serious voice. They will read `<em>` text with emphasis, like stress in speech. A `<b>` tag on its own just looks bold — but `<strong>` communicates that the content is truly important. This is called **accessibility**.

Think of it this way: `<b>` is like wearing a bright shirt — it's visible. `<strong>` is like saying something in a loud voice — it's meaningful.

---

## The Complete List of HTML Formatting Elements

Here is a full overview of every formatting element you will learn in this lesson.

| Tag | What it does | Visual Result |
|---|---|---|
| `<b>` | Makes text bold (no extra meaning) | **bold** |
| `<strong>` | Marks text as important (bold visually) | **important** |
| `<i>` | Makes text italic (no extra meaning) | *italic* |
| `<em>` | Emphasizes text (italic visually) | *emphasized* |
| `<mark>` | Highlights text (like a marker pen) | highlighted |
| `<small>` | Makes text smaller than normal | small |
| `<del>` | Shows deleted/removed text (strikethrough) | ~~deleted~~ |
| `<ins>` | Shows inserted/added text (underline) | inserted |
| `<sub>` | Subscript — text sits below the line | H₂O |
| `<sup>` | Superscript — text sits above the line | x² |

Now let us learn each one deeply, one at a time.

---

## Section 1: `<b>` — Bold Text (Visual Only)

### What is it?

The `<b>` element makes text appear **bold** — that is, thicker and darker than normal text.

### Why does it exist?

Sometimes you want a word to stand out visually. Bold text draws the reader's eye to something important on a page — like a keyword, a name, or a product title.

### What does it NOT do?

The `<b>` tag has **no semantic meaning**. It does not tell search engines, screen readers, or assistive technologies that the text is important. It is purely a visual styling tool.

### Syntax

```html
<b>Your bold text here</b>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>My favourite programming language is <b>HTML</b>.</p>
</body>
</html>
```

**Expected Output:**
> My favourite programming language is **HTML**.

Only the word "HTML" appears bold. The rest of the sentence looks normal.

### Second Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>The store sells <b>apples</b>, <b>oranges</b>, and <b>bananas</b>.</p>
</body>
</html>
```

**Expected Output:**
> The store sells **apples**, **oranges**, and **bananas**.

> 🤔 **Thinking Prompt:** What would happen if you accidentally wrote `<b>apples<b>` instead of `<b>apples</b>`? Try to guess before reading on.
> (Answer: Without the closing `/`, the browser might bold everything after that point, or it might behave unpredictably.)

---

## Section 2: `<strong>` — Important Text (Semantic Bold)

### What is it?

The `<strong>` element marks text as **important**. Like `<b>`, it visually displays text in bold. But unlike `<b>`, it communicates genuine importance to tools that read HTML.

### Why does it exist?

When you want to warn someone, highlight a critical rule, or emphasize a safety instruction, you should use `<strong>` — not just `<b>`. Screen readers will announce the text with greater emphasis when they encounter `<strong>`.

### Syntax

```html
<strong>Your important text here</strong>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>
  <p><strong>Warning:</strong> Do not touch hot surfaces.</p>
</body>
</html>
```

**Expected Output:**
> **Warning:** Do not touch hot surfaces.

### Second Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>To save your work, press <strong>Ctrl + S</strong> on your keyboard.</p>
</body>
</html>
```

**Expected Output:**
> To save your work, press **Ctrl + S** on your keyboard.

### `<b>` vs `<strong>` — Side-by-Side Comparison

```html
<p>This is <b>visually bold</b> but not marked as important.</p>
<p>This is <strong>semantically important</strong> and visually bold.</p>
```

**Expected Output:**
> This is **visually bold** but not marked as important.
> This is **semantically important** and visually bold.

Both look the same in a normal browser — but `<strong>` carries extra meaning for accessibility tools.

> 💡 **Best Practice:** Use `<strong>` when the text is genuinely critical, like warnings, rules, key terms, or safety information. Use `<b>` only for decorative styling.

---

## Section 3: `<i>` — Italic Text (Visual Only)

### What is it?

The `<i>` element makes text appear in **italics** — a slanted style of writing.

### Why does it exist?

Italics have many traditional uses in writing: titles of books or films, technical terms, phrases from foreign languages, ship names, and scientific species names. The `<i>` tag was created to handle these purely visual use cases.

### Syntax

```html
<i>Your italic text here</i>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>The ship was named <i>The Golden Star</i>.</p>
</body>
</html>
```

**Expected Output:**
> The ship was named *The Golden Star*.

### Second Example — Technical Term

```html
<!DOCTYPE html>
<html>
<body>
  <p>In Latin, the phrase <i>et cetera</i> means "and the rest".</p>
</body>
</html>
```

**Expected Output:**
> In Latin, the phrase *et cetera* means "and the rest".

---

## Section 4: `<em>` — Emphasized Text (Semantic Italic)

### What is it?

The `<em>` element stands for **emphasis**. Like `<i>`, it displays text in italic. But it also tells screen readers and search engines that the word carries stress — the same way we raise our voice to emphasize a word when speaking.

### Why does it exist?

Read these two sentences aloud:

- *I* did not say he stole the money.
- I did not say *he* stole the money.

The emphasis changes the entire meaning of the sentence! The `<em>` tag is for this kind of meaningful stress in language.

### Syntax

```html
<em>Your emphasized text here</em>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>You must <em>always</em> save your work before closing.</p>
</body>
</html>
```

**Expected Output:**
> You must *always* save your work before closing.

### Second Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>She is <em>not</em> responsible for this mistake.</p>
</body>
</html>
```

**Expected Output:**
> She is *not* responsible for this mistake.

### `<i>` vs `<em>` — Quick Comparison

| Situation | Use |
|---|---|
| Styling a ship name, book title, foreign phrase | `<i>` |
| Stressing a word to change meaning (like speech) | `<em>` |

---

## Section 5: `<small>` — Smaller Text

### What is it?

The `<small>` element makes text appear **smaller** than the surrounding text. It is typically used for fine print, disclaimers, copyright notices, and supplementary notes.

### Analogy

Think of the tiny text at the bottom of an advertisement that says "Terms and conditions apply." That is the kind of content `<small>` is perfect for.

### Syntax

```html
<small>Your small text here</small>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>This product costs $9.99 <small>(plus taxes and shipping)</small>.</p>
</body>
</html>
```

**Expected Output:**
> This product costs $9.99 (plus taxes and shipping). ← The bracketed part appears smaller

### Second Example — Copyright Notice

```html
<!DOCTYPE html>
<html>
<body>
  <p>MyWebsite.com</p>
  <small>Copyright &copy; 2024. All rights reserved.</small>
</body>
</html>
```

**Expected Output:**
> MyWebsite.com
> *(smaller)* Copyright © 2024. All rights reserved.

> 💡 **Note:** `&copy;` is an HTML entity that displays the copyright symbol ©. You will learn more about entities in a later lesson.

---

## Section 6: `<mark>` — Highlighted Text

### What is it?

The `<mark>` element highlights text with a **yellow background** (like using a physical highlighter pen on paper). It draws attention to a specific part of the text.

### Why does it exist?

In study guides, search results, and important notices, highlighting specific words helps readers find key information quickly. For example, when you search on Google, the matching word is often highlighted in the results.

### Syntax

```html
<mark>Your highlighted text here</mark>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>Do not forget to buy <mark>milk</mark> today.</p>
</body>
</html>
```

**Expected Output:**
> Do not forget to buy ==milk== today. ← "milk" appears with a yellow background

### Second Example — Highlighting a Search Term

```html
<!DOCTYPE html>
<html>
<body>
  <p>Search results for "HTML": Learn <mark>HTML</mark> from scratch.
     <mark>HTML</mark> is the language of the web.</p>
</body>
</html>
```

**Expected Output:**
> Search results for "HTML": Learn ==HTML== from scratch. ==HTML== is the language of the web.

> 🤔 **Thinking Prompt:** Where else in real life do you see highlighted or marked text? Think of product labels, warning notices, and textbooks.

---

## Section 7: `<del>` — Deleted (Strikethrough) Text

### What is it?

The `<del>` element shows text that has been **deleted or removed**. Browsers display it with a horizontal line through the middle — called a **strikethrough**.

### Why does it exist?

When you update a document, it can be useful to show what the original text was and what replaced it. This is common in legal documents, price tags (showing old vs. new price), and tracked document changes.

### Syntax

```html
<del>Your deleted text here</del>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>My favourite colour is <del>blue</del> red.</p>
</body>
</html>
```

**Expected Output:**
> My favourite colour is ~~blue~~ red.

The word "blue" appears with a line through it, showing it was removed.

### Second Example — Price Update

```html
<!DOCTYPE html>
<html>
<body>
  <p>Original Price: <del>$50.00</del> Now only $35.00!</p>
</body>
</html>
```

**Expected Output:**
> Original Price: ~~$50.00~~ Now only $35.00!

This is a classic use case you see on e-commerce websites showing discounted prices.

---

## Section 8: `<ins>` — Inserted Text (Underline)

### What is it?

The `<ins>` element marks text that has been **inserted** or added to a document. Browsers display it with an **underline**.

### Why does it exist?

`<ins>` is the counterpart to `<del>`. Together they show what was removed and what was added in its place — like tracking changes in a Word document.

### Syntax

```html
<ins>Your inserted text here</ins>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>My favourite colour is <del>blue</del> <ins>red</ins>.</p>
</body>
</html>
```

**Expected Output:**
> My favourite colour is ~~blue~~ <u>red</u>.

This clearly shows: "blue" was deleted, and "red" was inserted in its place.

### Second Example — Document Revision

```html
<!DOCTYPE html>
<html>
<body>
  <p>The meeting is on <del>Monday</del> <ins>Wednesday</ins> at 3pm.</p>
</body>
</html>
```

**Expected Output:**
> The meeting is on ~~Monday~~ <u>Wednesday</u> at 3pm.

> 💡 **Real-World Connection:** This combination of `<del>` and `<ins>` is exactly what Git (a version control system used by software developers) uses visually when showing code changes — red for deleted lines, green for inserted lines.

---

## Section 9: `<sub>` — Subscript Text

### What is it?

The `<sub>` element creates **subscript** text — text that appears **below** the normal line of text and is usually rendered in a smaller font size.

### Why does it exist?

In science, mathematics, and chemistry, subscript numbers are used constantly. For example:
- Water is written as H₂O (the 2 is subscript)
- Carbon dioxide is CO₂ (the 2 is subscript)
- Glucose is C₆H₁₂O₆

Without `<sub>`, you cannot correctly write these formulas in HTML.

### Syntax

```html
<sub>Your subscript text here</sub>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>Water is represented as H<sub>2</sub>O.</p>
</body>
</html>
```

**Expected Output:**
> Water is represented as H₂O.

The "2" appears slightly below and smaller than the "H" and "O".

### Second Example — Chemistry Formula

```html
<!DOCTYPE html>
<html>
<body>
  <p>Carbon dioxide is CO<sub>2</sub>.</p>
  <p>Sulphuric acid is H<sub>2</sub>SO<sub>4</sub>.</p>
</body>
</html>
```

**Expected Output:**
> Carbon dioxide is CO₂.
> Sulphuric acid is H₂SO₄.

> 🤔 **Thinking Prompt:** Can you write the chemical formula for glucose (C6H12O6) using `<sub>` tags? Try it on your own before checking the next section.

---

## Section 10: `<sup>` — Superscript Text

### What is it?

The `<sup>` element creates **superscript** text — text that appears **above** the normal line of text and is usually rendered in a smaller font size.

### Why does it exist?

Superscript is used in:
- Mathematical exponents (x², y³, 10⁴)
- Footnote references (like "See note[1]")
- Ordinal numbers in some languages (1st, 2nd, 3rd)
- Trademark symbols (sometimes)

### Syntax

```html
<sup>Your superscript text here</sup>
```

### Simple Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>The area of a square with side 5 is 5<sup>2</sup> = 25.</p>
</body>
</html>
```

**Expected Output:**
> The area of a square with side 5 is 5² = 25.

### Second Example — Footnote Reference

```html
<!DOCTYPE html>
<html>
<body>
  <p>According to the study<sup>1</sup>, HTML is the most widely used markup language.</p>
  <p><small><sup>1</sup> Smith, J. (2023). Web Languages Report.</small></p>
</body>
</html>
```

**Expected Output:**
> According to the study¹, HTML is the most widely used markup language.
> *(smaller)* ¹ Smith, J. (2023). Web Languages Report.

### `<sub>` vs `<sup>` — Visual Comparison

```html
<p>Normal text with <sub>subscript below</sub> and <sup>superscript above</sup>.</p>
```

**Expected Output:**
> Normal text with ₛᵤᵦₛcᵣᵢₚₜ ᵦₑₗₒw and ˢᵘᵖᵉʳˢᶜʳⁱᵖᵗ ᵃᵇᵒᵛᵉ.
> (subscript dips below, superscript rises above the baseline)

---

## Combining Formatting Tags Together

Now that you understand each tag individually, let us look at how they can be **combined** in a real paragraph.

> ⚠️ **Rule:** Always close tags in the correct order. If you open `<b>` inside `<p>`, close `<b>` before closing `<p>`.

### Combined Example 1 — Science Article Snippet

```html
<!DOCTYPE html>
<html>
<body>
  <h2>Chemistry Fact</h2>
  <p>
    <strong>Water</strong> (H<sub>2</sub>O) is a <em>vital</em> compound
    for all living organisms. The boiling point of water is
    <mark>100°C</mark> at standard pressure.
  </p>
  <p><small>Source: Chemistry Textbook, 2023</small></p>
</body>
</html>
```

**Expected Output:**
> **Chemistry Fact**
>
> **Water** (H₂O) is a *vital* compound for all living organisms. The boiling point of water is ==100°C== at standard pressure.
>
> *(smaller)* Source: Chemistry Textbook, 2023

### Combined Example 2 — Product Listing

```html
<!DOCTYPE html>
<html>
<body>
  <h2>Laptop Pro X</h2>
  <p>
    <strong>Special Offer!</strong> Was <del>$1,200</del>,
    now only <ins>$899</ins>.
  </p>
  <p><small>*Offer valid while stocks last. <em>Terms apply.</em></small></p>
</body>
</html>
```

**Expected Output:**
> **Laptop Pro X**
>
> **Special Offer!** Was ~~$1,200~~, now only <u>$899</u>.
>
> *(smaller)* *Offer valid while stocks last. Terms apply.*

---

## Guided Practice Exercises

### Exercise 1 — Formatting a Science Note

**Objective:** Use `<strong>`, `<em>`, `<sub>`, and `<mark>` to format a science sentence.

**Scenario:** You are building a chemistry revision page for students.

**Your Task:** Write HTML that produces this output:

> **Reminder:** The formula for sulphuric acid is H₂SO₄. This is an *extremely* corrosive substance. Handle with ==caution==.

**Steps:**
1. Open a new HTML file with `<!DOCTYPE html>`, `<html>`, `<body>` structure.
2. Use a `<p>` tag.
3. Use `<strong>` for "Reminder:".
4. Use `<sub>` for the subscript numbers in the formula.
5. Use `<em>` for "extremely".
6. Use `<mark>` for "caution".

**Hint:** H₂SO₄ needs two `<sub>` tags — one for the "2" and one for the "4".

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>
  <p>
    <strong>Reminder:</strong> The formula for sulphuric acid is
    H<sub>2</sub>SO<sub>4</sub>. This is an <em>extremely</em>
    corrosive substance. Handle with <mark>caution</mark>.
  </p>
</body>
</html>
```

**Expected Output:**
> **Reminder:** The formula for sulphuric acid is H₂SO₄. This is an *extremely* corrosive substance. Handle with ==caution==.

**Self-Check Questions:**
- Did you close every tag you opened?
- Does the subscript appear below the regular text line?
- Is "Reminder:" in bold?

---

### Exercise 2 — Price Update Notice

**Objective:** Use `<del>`, `<ins>`, `<strong>`, and `<small>` to build a product price update.

**Scenario:** An online shop is running a sale. You need to show old and new prices.

**Your Task:** Write HTML that produces this output:

> **SALE!** Wireless Headphones
> Was: ~~$120.00~~
> Now: <u>$79.99</u>
> *(smaller)* Limited stock available. Offer ends Sunday.

**Steps:**
1. Use `<strong>` for "SALE!".
2. Use `<del>` for the old price.
3. Use `<ins>` for the new price.
4. Use `<small>` for the disclaimer.

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>
  <p><strong>SALE!</strong> Wireless Headphones</p>
  <p>Was: <del>$120.00</del></p>
  <p>Now: <ins>$79.99</ins></p>
  <small>Limited stock available. Offer ends Sunday.</small>
</body>
</html>
```

**Expected Output:**
> **SALE!** Wireless Headphones
> Was: ~~$120.00~~
> Now: <u>$79.99</u>
> *(smaller)* Limited stock available. Offer ends Sunday.

---

### Exercise 3 — Mathematics Expressions

**Objective:** Use `<sup>` to write mathematical expressions correctly.

**Scenario:** You are creating a maths revision webpage for students.

**Your Task:** Write HTML that produces this:

> The formula for the area of a circle is πr²
> Einstein's famous equation is E = mc²
> The speed of light is approximately 3 × 10⁸ metres per second.

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>
  <p>The formula for the area of a circle is &#960;r<sup>2</sup></p>
  <p>Einstein's famous equation is E = mc<sup>2</sup></p>
  <p>The speed of light is approximately 3 &times; 10<sup>8</sup> metres per second.</p>
</body>
</html>
```

> 💡 **Note:** `&#960;` is the HTML entity for the Greek letter π (pi). `&times;` is the multiplication symbol ×. You will learn more HTML entities in a later lesson.

**Expected Output:**
> The formula for the area of a circle is πr²
> Einstein's famous equation is E = mc²
> The speed of light is approximately 3 × 10⁸ metres per second.

---

## Mini Project: Build a Science Fact Card

In this project, you will combine everything you have learned to build a styled science fact card for a biology or chemistry class webpage.

### Project Brief

You are building a webpage called "Daily Science Fact." It should display a well-formatted fact using as many formatting elements as appropriate.

---

### Stage 1: Setup — Basic HTML Structure

Start with a clean, complete HTML file.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Daily Science Fact</title>
</head>
<body>

  <!-- Your content will go here -->

</body>
</html>
```

**Milestone Output:** A blank webpage with a title "Daily Science Fact" in the browser tab.

---

### Stage 2: Add the Fact Card Content

Now add the main content using formatting tags.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Daily Science Fact</title>
</head>
<body>

  <h1>Daily Science Fact</h1>

  <h2>Did You Know?</h2>

  <p>
    <strong>Photosynthesis</strong> is the process by which plants
    convert sunlight into food. The overall chemical equation is:
  </p>

  <p>
    6CO<sub>2</sub> + 6H<sub>2</sub>O + light energy →
    C<sub>6</sub>H<sub>12</sub>O<sub>6</sub> + 6O<sub>2</sub>
  </p>

  <p>
    This was <em>first described</em> in detail by Jan Ingenhousz
    in the 18<sup>th</sup> century. It is <mark>one of the most
    important biological processes</mark> on Earth.
  </p>

  <p>
    <del>Scientists once believed sunlight was the only factor.</del>
    <ins>We now know that water and carbon dioxide are equally essential.</ins>
  </p>

  <p><small>Source: Biology Foundations, 4th Edition. All content for educational use only.</small></p>

</body>
</html>
```

**Milestone Output:**

> **Daily Science Fact**
>
> **Did You Know?**
>
> **Photosynthesis** is the process by which plants convert sunlight into food. The overall chemical equation is:
>
> 6CO₂ + 6H₂O + light energy → C₆H₁₂O₆ + 6O₂
>
> This was *first described* in detail by Jan Ingenhousz in the 18ᵗʰ century. It is ==one of the most important biological processes== on Earth.
>
> ~~Scientists once believed sunlight was the only factor.~~ <u>We now know that water and carbon dioxide are equally essential.</u>
>
> *(smaller)* Source: Biology Foundations, 4th Edition. All content for educational use only.

---

### Stage 3: Reflection Questions

Think about the completed project and answer these questions to yourself:

1. Why did you use `<strong>` for "Photosynthesis" instead of just `<b>`?
2. Why is `<sub>` important for the chemical formula?
3. What would happen if you forgot to close `<sub>` after "2" in CO₂?
4. Could you have used `<i>` instead of `<em>` for "first described"? What would be different?
5. What real websites have you seen use highlighted text (`<mark>`), strikethrough (`<del>`), or fine print (`<small>`)?

---

### Stage 4: Optional Extensions

Try adding these to make your fact card even richer:

- Add a second science fact using `<b>` for a keyword (instead of `<strong>`) and notice the visual difference
- Add a footnote reference using `<sup>` and `<small>` together
- Create a price comparison section with `<del>` and `<ins>` — as if selling a textbook on your website

---

## HTML Formatting Elements — Code Challenge

The second source page for this lesson (the W3Schools Code Challenge page) challenges you to test your understanding of formatting elements. Here are equivalent challenge tasks you can practise right now:

### Challenge 1
**Task:** Make the word "important" appear in bold using the semantic tag.

```html
<p>This is <___>important</___ > information.</p>
```

**Answer:**
```html
<p>This is <strong>important</strong> information.</p>
```

---

### Challenge 2
**Task:** Make the word "science" appear in italic using the visual-only tag.

```html
<p>I love <___>science</___ >.</p>
```

**Answer:**
```html
<p>I love <i>science</i>.</p>
```

---

### Challenge 3
**Task:** Show that the word "bad" has been deleted and "good" has been inserted.

```html
<p>This is a <___>bad</___ > <___>good</___ > idea.</p>
```

**Answer:**
```html
<p>This is a <del>bad</del> <ins>good</ins> idea.</p>
```

---

### Challenge 4
**Task:** Write the chemical formula for carbon dioxide using the correct subscript tag.

**Answer:**
```html
<p>CO<sub>2</sub></p>
```

---

### Challenge 5
**Task:** Write x to the power of 3 (x³) using the correct superscript tag.

**Answer:**
```html
<p>x<sup>3</sup></p>
```

---

### Challenge 6
**Task:** Highlight the word "deadline" in a sentence.

**Answer:**
```html
<p>The project <mark>deadline</mark> is this Friday.</p>
```

---

## Common Beginner Mistakes

Here are the most frequent errors beginners make with formatting tags, and how to fix them.

---

### Mistake 1: Forgetting to Close the Tag

**Wrong:**
```html
<p>This word is <b>bold and so is everything after it.</p>
```

**What happens:** The bold formatting never ends. Everything after `<b>` will appear bold, even outside the intended word.

**Correct:**
```html
<p>This word is <b>bold</b> and the rest is normal.</p>
```

---

### Mistake 2: Using `<b>` When `<strong>` Is More Appropriate

**Wrong (for a critical warning):**
```html
<p><b>Do not run</b> near the swimming pool.</p>
```

**Better:**
```html
<p><strong>Do not run</strong> near the swimming pool.</p>
```

Use `<strong>` for genuine warnings, safety rules, and critical content so screen readers announce it properly.

---

### Mistake 3: Incorrect Nesting Order

**Wrong:**
```html
<p>This is <b><em>bold and italic</b></em>.</p>
```

**What happens:** The closing tags do not match the opening order. This is invalid HTML and browsers may render it incorrectly.

**Correct:**
```html
<p>This is <b><em>bold and italic</em></b>.</p>
```

**Rule:** The last tag you open must be the first tag you close. Think of it like closing brackets: `( [ ] )` — you cannot do `( [ ) ]`.

---

### Mistake 4: Using `<sub>` and `<sup>` for the Wrong Content

**Wrong — using `<sup>` just to make text smaller:**
```html
<p>See the disclaimer<sup>*</sup> below.</p>
<!-- This is actually correct, but beginners sometimes use <sup> to just shrink text -->
```

**Wrong — using `<sup>` for a chemical formula subscript:**
```html
<p>H<sup>2</sup>O</p>  <!-- WRONG: the 2 should be below, not above! -->
```

**Correct:**
```html
<p>H<sub>2</sub>O</p>  <!-- The 2 is subscript (below the line) -->
```

**Memory trick:** **Sub**script = below ground (like a **sub**marine). **Super**script = above (like a **super**hero flying up).

---

### Mistake 5: Confusing `<del>` With Just Styling

Some beginners try to use CSS `text-decoration: line-through` instead of `<del>`. While CSS can visually create a strikethrough, only `<del>` communicates to browsers, search engines, and screen readers that the content has been **deleted**. Always use the right semantic tag for the right purpose.

---

### Mistake 6: Using `<ins>` Without `<del>` (in revision context)

When showing document changes, always pair `<del>` (removed text) with `<ins>` (added text). Using `<ins>` alone to underline normal text can confuse readers into thinking something was changed.

---

## Reflection Questions

Take a few minutes to think through these questions. They will help you confirm you truly understood the lesson.

1. What is the difference between `<b>` and `<strong>`? When should you choose one over the other?

2. You are writing an HTML page about the history of science. You want to write: *"Charles Darwin published 'On the Origin of Species' in 1859."* Which formatting tag would you use for the book title, and why?

3. A classmate writes `<em>` to make a ship name italic in their story. Is this the best choice? What would you suggest instead?

4. Look at this code. What is wrong, and how would you fix it?
   ```html
   <p>Price: <del>$50 <ins></del>$30</ins></p>
   ```

5. You are writing a physics equation for kinetic energy: KE = ½mv². How do you write the "2" correctly in HTML?

6. Where in a real website have you seen `<small>` text used? (Think: footers, disclaimers, social media post timestamps.)

7. If a screen reader is reading your page to a visually impaired user, how does `<em>` help them compared to `<i>`?

---

## Completion Checklist

Go through each item below. If you can confidently check it off, you have mastered this lesson!

- [ ] I understand what HTML formatting elements are and why they exist
- [ ] I can explain the difference between visual formatting tags and semantic formatting tags
- [ ] I can use `<b>` to make text bold (visual only)
- [ ] I can use `<strong>` to mark text as important (semantic bold)
- [ ] I can use `<i>` to make text italic (visual only)
- [ ] I can use `<em>` to emphasize text (semantic italic)
- [ ] I can use `<small>` to display smaller text (fine print, disclaimers)
- [ ] I can use `<mark>` to highlight text with a background colour
- [ ] I can use `<del>` to show deleted/removed text with a strikethrough
- [ ] I can use `<ins>` to show inserted/added text with an underline
- [ ] I can use `<sub>` to write subscript text (below the line, e.g. H₂O)
- [ ] I can use `<sup>` to write superscript text (above the line, e.g. x²)
- [ ] I can combine multiple formatting tags correctly in one paragraph
- [ ] I know how to close tags in the correct nesting order
- [ ] I completed the exercises and the mini project
- [ ] I understand why proper nesting matters

---

## Lesson Summary

In this lesson, you explored the full set of HTML text formatting elements. Here is a final summary of everything you learned:

**HTML gives us 10 core formatting elements:**

| Tag | Purpose | Visual Result |
|---|---|---|
| `<b>` | Bold — visual only | **text** |
| `<strong>` | Bold — semantically important | **text** |
| `<i>` | Italic — visual only | *text* |
| `<em>` | Italic — semantically emphasized | *text* |
| `<small>` | Smaller text for fine print | small text |
| `<mark>` | Highlighted text | highlighted |
| `<del>` | Strikethrough — deleted text | ~~text~~ |
| `<ins>` | Underlined — inserted text | <u>text</u> |
| `<sub>` | Subscript — below the line | H₂O |
| `<sup>` | Superscript — above the line | x² |

**Key Principles to Remember:**

- Prefer **semantic tags** (`<strong>`, `<em>`) over purely visual ones (`<b>`, `<i>`) when the text truly carries importance or stress — this supports accessibility.
- Always **close your tags** in the reverse order you opened them.
- `<del>` and `<ins>` are a natural pair — use them together when tracking document changes.
- `<sub>` and `<sup>` are essential for science, mathematics, and footnotes — not just decoration.
- `<small>` is for **supplementary** information (fine print, copyright), not for making unimportant text disappear.
- `<mark>` is great for highlighting key terms in study materials and search result displays.

**Real-World Applications of Formatting Tags:**
- Science & Chemistry websites: `<sub>` for formulas, `<sup>` for exponents
- E-commerce stores: `<del>` and `<ins>` for price comparisons
- Legal and medical documents: `<strong>` for warnings, `<small>` for disclaimers
- Academic pages: `<sup>` for footnote references, `<em>` for key terms
- News and study tools: `<mark>` to highlight search terms or key facts

You are now ready to move on to the next lesson: **HTML Quotations** — where you will learn how to add quotes, citations, and abbreviations to your web pages.

---

*End of Lesson 8 — HTML Text Formatting*
