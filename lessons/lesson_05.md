---
render_with_liquid: false
title: "Lesson 5 — HTML Headings: Levels, Importance, SEO, Sizing & Best Practices"
nav_order: 5
---

# Lesson 5 — HTML Headings: Levels, Importance, SEO, Sizing & Best Practices

---

## Lesson Introduction

Welcome to Lesson 5! You have already used `<h1>` in every page you have written. But this lesson goes far deeper — into *why* headings matter beyond making text look big, *how* they shape the meaning and structure of your entire page, and *when* to use each of the six levels correctly.

By the end of this lesson you will be able to:

- Understand what HTML headings are and what problem they solve
- Write all six heading levels (`<h1>` through `<h6>`) with confidence
- Explain every default visual difference between heading levels
- Understand why browsers add automatic margins around headings
- Use headings to create a meaningful, logical document outline
- Explain the three critical reasons headings matter: structure, SEO, and accessibility
- Override default heading sizes using the `style` attribute and `font-size` CSS property
- Apply the golden rules of heading usage that professionals follow every day
- Distinguish correctly between using headings for *structure* versus using them for *visual size*

> **Real-world connection:** Every website you have ever read — a news article, a Wikipedia page, a product description, a government report — uses a heading hierarchy. When a screen reader announces "Heading level 2: African Wildlife", it is reading the `<h2>` tag you wrote. When Google displays your page in search results, it is largely reading your `<h1>`. Headings are not decoration — they are the skeleton of your content.

---

## Prerequisite Concepts

### Quick Recap From Previous Lessons

From **Lesson 2**, you first used `<h1>` and saw that it creates large, bold text. From **Lesson 4**, you learned that the `style` attribute can apply CSS properties like `font-size` to any element. Both of these connect directly to what you will learn here.

### What Is a Heading — Really?

Before we write code, let us understand the concept. A **heading** in everyday life is a label that introduces a section of content. In a newspaper:

- The big bold title at the top is the main heading
- Smaller section titles ("Sports", "Business", "Culture") are sub-headings
- Inside each section, individual story titles are sub-sub-headings

In HTML, we replicate this exact hierarchy with `<h1>` through `<h6>`. The number tells you the *level of importance* — 1 is most important, 6 is least.

---

## Part 1 — The Six HTML Heading Tags

### What They Are

HTML provides **six levels** of heading elements, all defined with tags from `<h1>` to `<h6>`:

```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>
```

**Expected output in browser:**

```
Heading 1     ← very large, bold, lots of space above and below
Heading 2     ← large, bold
Heading 3     ← medium-large, bold
Heading 4     ← medium, bold
Heading 5     ← small, bold (similar to normal text size)
Heading 6     ← very small, bold (often smaller than normal text)
```

Every heading is:

- Displayed in **bold** by default
- Displayed on **its own line** (block-level element — covered in a later lesson)
- Surrounded by **automatic white space** (margin) above and below it

---

### The Default Sizes

Browsers apply default font sizes to each heading level. While exact sizes vary slightly between browsers, the approximate defaults in most browsers are:

| Tag | Approximate Default Size | Relative Scale |
|-----|--------------------------|----------------|
| `<h1>` | 2em (roughly 32px) | Largest |
| `<h2>` | 1.5em (roughly 24px) | Very large |
| `<h3>` | 1.17em (roughly 18.7px) | Large |
| `<h4>` | 1em (roughly 16px) | Same as normal body text |
| `<h5>` | 0.83em (roughly 13px) | Smaller than body text |
| `<h6>` | 0.67em (roughly 10.7px) | Smallest |

> **What is "em"?** An `em` is a CSS measurement unit relative to the parent element's font size. `1em` equals the current base font size (usually 16px in browsers). `2em` is double that. You will learn measurement units fully in CSS — for now, just know that `h1` is the biggest and `h6` is the smallest.

---

### The Automatic White Space (Margin)

A key characteristic of all heading elements: **browsers automatically add margin (white space) before and after every heading**. You do not need to add blank lines in your code — the browser does it for you.

```html
<p>This is a paragraph of text.</p>
<h2>A New Section</h2>
<p>This is another paragraph.</p>
```

**Expected output:**

```
This is a paragraph of text.

A New Section        ← automatic space above and below

This is another paragraph.
```

The spaces you see above and below `A New Section` were added entirely by the browser's default stylesheet. No extra code was needed.

> **Thinking prompt:** What would your page look like if headings had no automatic margin at all? Text, heading, text would all run together with no visual breathing room — the page would feel cramped and very hard to read.

---

### Simple Example — All Six Levels in Action

```html
<!DOCTYPE html>
<html lang="en">
<body>

<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>

</body>
</html>
```

**Expected output in browser (from top to bottom, each smaller than the last):**

```
Heading 1          ← biggest
Heading 2
Heading 3
Heading 4
Heading 5
Heading 6          ← smallest
```

Try this in your browser and notice:

- Each heading is on its own line with space above and below
- Each successive heading is visually smaller and less prominent
- All are bold
- The visual weight communicates importance — bigger means more important

---

## Part 2 — Why Headings Are Important

This is the heart of the lesson. Headings are not just about making text look big. They serve **three deeply important purposes** that affect whether your page works, ranks, and reaches real people.

---

### Reason 1 — Document Structure (Readability)

Headings help users understand the organisation of your content at a glance.

Think about reading a long article without any headings — just block after block of text. It would be exhausting. Users would have to read every word to find what they need.

With headings, a user can **skim** the page in seconds: they read only the headings to find the section they want, then dive in. Studies consistently show that most web users do not read pages word for word — they scan. Headings are what they are scanning.

**Good document structure using headings:**

```html
<h1>Travel Guide: West Africa</h1>

<h2>Nigeria</h2>
<h3>Lagos</h3>
<h3>Abuja</h3>

<h2>Ghana</h2>
<h3>Accra</h3>
<h3>Kumasi</h3>

<h2>Senegal</h2>
<h3>Dakar</h3>
```

**Expected output:**

```
Travel Guide: West Africa     ← page title (h1)

Nigeria                       ← major section (h2)
  Lagos                       ← subsection (h3)
  Abuja

Ghana
  Accra
  Kumasi

Senegal
  Dakar
```

A user looking for information about Accra can scan this heading structure in under two seconds and jump straight to the right section.

---

### Reason 2 — Search Engine Optimisation (SEO)

**SEO** (Search Engine Optimisation) is the practice of structuring your content so that search engines like Google rank your page higher in search results.

Search engine crawlers — automated programs that read web pages — pay close attention to heading tags when they index your content. Here is how Google uses headings:

- The `<h1>` heading is treated as the **primary topic** of the page. Google uses it to understand what the page is fundamentally about.
- `<h2>` and `<h3>` headings tell Google about the **sub-topics** and sections within the page.
- Keywords that appear in headings are weighted more heavily than the same keywords in body text.

**A concrete example:** If you are writing a page about "how to make jollof rice", your heading structure should look like this:

```html
<h1>How to Make Perfect Jollof Rice</h1>
<h2>Ingredients You Will Need</h2>
<h2>Step-by-Step Instructions</h2>
<h3>Preparing the Tomato Base</h3>
<h3>Cooking the Rice</h3>
<h2>Tips for Getting Smoky Flavour</h2>
```

Google reads this structure and clearly understands: this page is about making jollof rice (from `<h1>`), and it covers ingredients, instructions, and tips (from `<h2>` tags). This helps the page rank when someone searches "how to make jollof rice".

> **Real-world connection:** Content creators, marketers, bloggers, and web developers are paid significant salaries specifically to research and craft the right heading structure for pages. It directly affects how much traffic a website receives from Google.

---

### Reason 3 — Accessibility (Screen Readers)

A **screen reader** is assistive software used by people with visual impairments. It reads the content of a web page aloud through a speaker or braille display.

Screen reader users have a special feature: they can navigate a page **by headings only**, jumping from one heading to the next without hearing all the body text in between. This allows them to skim a page just like sighted users scan it visually.

For this to work, your headings must be:

1. Correctly marked up with actual `<h1>`–`<h6>` tags (not just visually large text made with CSS)
2. In a logical, sequential order that makes sense when read aloud
3. Descriptive enough that the heading alone conveys what the section contains

**What a screen reader announces:** When a user's screen reader reaches `<h2>Nigeria</h2>`, it says: *"Heading level 2: Nigeria."* The user immediately knows: this is a major section heading, and it is about Nigeria.

If you made text look big using CSS but did not use a heading tag, the screen reader would just read it as ordinary text with no level announcement — the user would not know it was a section heading.

> **Analogy:** Imagine navigating a city without road signs. You could still travel, but it would take dramatically longer and require much more effort. Headings are the road signs of your web page. Screen reader users depend on them completely.

---

## Part 3 — The Heading Hierarchy Rule

### How to Use h1 Through h6 in Order

The most important practical rule for headings is to use them in **logical, sequential order** — like an outline.

Think of a heading hierarchy like the contents page of a textbook:

```
Chapter 1: The Solar System             ← h1 (page title)
  1.1 The Sun                           ← h2 (major section)
  1.2 The Planets                       ← h2
    1.2.1 Inner Planets                 ← h3 (subsection)
      Mercury                          ← h4 (sub-subsection)
      Venus                            ← h4
    1.2.2 Outer Planets                 ← h3
      Jupiter                          ← h4
      Saturn                           ← h4
  1.3 Moons and Asteroids               ← h2
```

In HTML, this would translate to:

```html
<h1>The Solar System</h1>

<h2>The Sun</h2>

<h2>The Planets</h2>
<h3>Inner Planets</h3>
<h4>Mercury</h4>
<h4>Venus</h4>
<h3>Outer Planets</h3>
<h4>Jupiter</h4>
<h4>Saturn</h4>

<h2>Moons and Asteroids</h2>
```

**Expected output:**

```
The Solar System           ← large, prominent page title

The Sun                    ← major section heading

The Planets
  Inner Planets            ← subsection
    Mercury                ← sub-subsection, small
    Venus
  Outer Planets
    Jupiter
    Saturn

Moons and Asteroids
```

---

### The Travel Guide Example (from W3Schools)

Here is the exact real-world example from the source:

```html
<h1>Travel Guide</h1>

<h2>Europe</h2>
<h3>France</h3>
<h3>Italy</h3>

<h2>Asia</h2>
<h3>India</h3>
<h3>Thailand</h3>
```

**Expected output:**

```
Travel Guide            ← page title

Europe                  ← continent section
  France                ← country subsection
  Italy

Asia
  India
  Thailand
```

This structure is immediately clear. A user can grasp the entire content outline just by reading the headings.

---

### The One `<h1>` Rule

**Use only one `<h1>` per page.**

The `<h1>` tag represents the single most important heading on the page — the main topic. Just like a book has one title (not five), each web page should have one primary `<h1>`.

Multiple `<h1>` tags confuse both search engines (which one is the real topic?) and screen reader users (which heading is the true title of this page?).

```html
<!-- WRONG: Multiple h1 tags -->
<h1>My Blog</h1>
<h1>About Me</h1>
<h1>Contact</h1>

<!-- CORRECT: One h1, followed by h2 sections -->
<h1>My Personal Blog</h1>
<h2>About Me</h2>
<h2>Contact</h2>
```

**Expected output for the correct version:**

```
My Personal Blog     ← clearly the page title (large)

About Me             ← sections (medium)
Contact
```

---

### Do Not Skip Heading Levels

Go through heading levels in order. Do not jump from `<h1>` directly to `<h4>`.

```html
<!-- WRONG: Skipping from h1 to h4 -->
<h1>My Website</h1>
<h4>Introduction</h4>
<h4>Features</h4>

<!-- CORRECT: Follow the natural order -->
<h1>My Website</h1>
<h2>Introduction</h2>
<h2>Features</h2>
```

Skipping levels breaks the semantic outline and confuses assistive technologies that rely on a logical heading progression.

---

## Part 4 — Bigger Headings: Custom Sizes with `font-size`

### The Problem

The browser's default heading sizes are fixed. Sometimes `<h1>` is not quite big enough for your design, or you want `<h3>` to be a specific size that fits your layout.

### The Solution — `font-size` in the `style` Attribute

You can override any heading's default size using the `style` attribute with the CSS `font-size` property (introduced in Lesson 4):

```html
<h1 style="font-size:60px;">Heading 1</h1>
```

**Expected output:** A massive heading displayed at 60 pixels tall — significantly larger than the default `<h1>` size of approximately 32px.

You can set `font-size` using several units:

| Unit | What it means | Example |
|------|--------------|---------|
| `px` | Pixels — fixed, exact size | `font-size:48px;` |
| `em` | Relative to parent font size | `font-size:3em;` |
| `%` | Percentage of parent font size | `font-size:200%;` |

For now, **pixels (`px`)** are the easiest to understand and control.

---

### Simple Example — Custom Heading Sizes

```html
<!DOCTYPE html>
<html lang="en">
<body>

<h1 style="font-size:60px;">Very Large Heading</h1>
<h2 style="font-size:40px;">Large Heading</h2>
<h3 style="font-size:28px;">Medium Heading</h3>
<h4 style="font-size:20px;">Small Heading</h4>

</body>
</html>
```

**Expected output:** Four headings at exactly 60px, 40px, 28px, and 20px respectively — all bold, each progressively smaller.

---

### Second Example — Overriding a Smaller Heading to Be Larger

```html
<!DOCTYPE html>
<html lang="en">
<body>

<h1>This is the standard h1 (about 32px)</h1>

<h1 style="font-size:80px;">This h1 is 80px — much bigger!</h1>

<h3 style="font-size:36px;">
  This h3 is styled to be bigger than the default h1.
</h3>

</body>
</html>
```

**Expected output:** The default `<h1>` at normal size, then a huge `<h1>` at 80px, then an `<h3>` that appears visually larger than the default `<h1>` due to the `font-size:36px` style.

> **Thinking prompt:** If you can make `<h3>` look bigger than `<h1>` using `font-size`, does that mean `<h3>` is now more important? **No!** The tag still determines the semantic importance. The `<h3>` is still treated by search engines and screen readers as a level-3 heading — less important than the `<h1>`. Visual size and semantic importance are separate concerns.

---

### Combining `font-size` with Other Style Properties

You can combine `font-size` with other CSS properties in the same `style` attribute:

```html
<h1 style="font-size:50px; color:darkblue; text-align:center;">
  Welcome to My Website
</h1>

<h2 style="font-size:28px; color:grey; font-style:italic;">
  A space for ideas and technology
</h2>
```

**Expected output:** A large, centred, dark-blue main heading, followed by a smaller grey italic subheading.

---

## Part 5 — The Critical Warning: Headings Are for Structure, Not Size

This is one of the most important rules in all of HTML, stated directly in the W3Schools source and reinforced by every professional HTML standard.

> **Do not use headings to make text BIG or bold.**

### Why This Matters

Many beginners look at headings and think: "Oh, `<h1>` is just how I make text big and bold." This is wrong — and it causes real problems.

**What headings actually are:** Semantic labels that describe the *importance and role* of a piece of text within the document's structure.

**What headings are not:** A visual formatting tool for making text appear large.

---

### The Problem With Using Headings for Visual Size

```html
<!-- WRONG: Using h1 to make a subtitle look big -->
<h1>Welcome to My Restaurant</h1>
<h1>Serving the best food in Lagos</h1>
<h1>Open Monday to Sunday, 9am to 10pm</h1>
```

To a sighted user, this might look fine — three large pieces of text. But:

- **Screen reader:** Announces "Heading level 1: Welcome to My Restaurant", then "Heading level 1: Serving the best food in Lagos", then "Heading level 1: Open Monday to Sunday..." — completely confused, no hierarchy
- **Search engine:** Sees three competing `<h1>` tags and cannot determine the primary topic of the page
- **HTML validator:** Flags multiple `<h1>` elements as a structural error

**The correct approach:**

```html
<!-- CORRECT: h1 for the page title, h2 for sections, <p> for supporting text -->
<h1>Welcome to My Restaurant</h1>
<p>Serving the best food in Lagos</p>
<p>Open Monday to Sunday, 9am to 10pm</p>
```

If you want the subtitle to look bigger, use CSS — not a heading tag:

```html
<h1>Welcome to My Restaurant</h1>
<p style="font-size:20px; color:grey;">Serving the best food in Lagos</p>
<p>Open Monday to Sunday, 9am to 10pm</p>
```

---

### Another Common Mistake — Using Bold Tags Instead of Headings

Some beginners do the opposite mistake: they want a section title to appear but use `<b>` (bold) or `<p style="font-weight:bold;">` instead of a proper heading tag. This makes text look like a heading visually, but it carries none of the semantic weight.

```html
<!-- WRONG: Bold paragraph pretending to be a heading -->
<p><b>Introduction</b></p>
<p>This is the introduction text...</p>

<!-- CORRECT: Actual heading tag carries semantic meaning -->
<h2>Introduction</h2>
<p>This is the introduction text...</p>
```

Screen readers skip over `<b>` tags as headings — they do not announce them as section titles. Use the correct heading tag when something is genuinely a section heading.

---

### The Simple Test

Before using a heading tag, ask yourself two questions:

1. **Is this text a title or section label for the content that follows?** If yes → use a heading tag.
2. **Do I just want this text to look bigger or bolder?** If yes → use CSS (`font-size`, `font-weight`) on a `<p>` tag instead.

| Situation | Use |
|-----------|-----|
| Main page title | `<h1>` |
| Section title | `<h2>` |
| Subsection title | `<h3>` or deeper |
| Supporting text that happens to be large | `<p style="font-size:20px;">` |
| Text that needs to stand out but is not a heading | `<p style="font-weight:bold;">` |

---

## Part 6 — Complete Heading Tag Reference

| Tag | Name | Default Visual Weight | Typical Use |
|-----|------|-----------------------|-------------|
| `<h1>` | Heading 1 | Largest | Page title — use **once per page** |
| `<h2>` | Heading 2 | Large | Major sections of the page |
| `<h3>` | Heading 3 | Medium-large | Subsections within an `<h2>` section |
| `<h4>` | Heading 4 | Medium (≈ body text) | Sub-subsections within an `<h3>` |
| `<h5>` | Heading 5 | Small | Rarely needed — deeply nested sections |
| `<h6>` | Heading 6 | Smallest | Rarely needed — deepest level of detail |

> **In practice:** Most web pages only need `<h1>`, `<h2>`, and `<h3>`. Using `<h4>` through `<h6>` is appropriate for very complex, deeply structured documents like technical manuals, legal documents, or long-form research articles.

---

## Guided Practice Exercises

---

### Exercise 1 — Read the Heading Structure

Study the following HTML. Without running it, describe the visual output and the document structure it creates. Then run it in your browser to verify.

```html
<!DOCTYPE html>
<html lang="en">
<body>

<h1>My Coding Journey</h1>

<h2>Languages I Have Learned</h2>
<h3>HTML</h3>
<h3>CSS</h3>
<h3>JavaScript</h3>

<h2>Projects I Have Built</h2>
<h3>Personal Website</h3>
<h3>Calculator App</h3>

<h2>Goals for Next Year</h2>

</body>
</html>
```

**Expected output:**

```
My Coding Journey                ← large page title (h1)

Languages I Have Learned         ← major section (h2)
  HTML                           ← subsection (h3)
  CSS
  JavaScript

Projects I Have Built
  Personal Website
  Calculator App

Goals for Next Year
```

**Self-check questions:**

- How many `<h1>` elements are on this page? (1 — correct)
- Are any heading levels skipped? (No — h1, then h2, then h3)
- Does each `<h3>` belong logically inside its parent `<h2>`? (Yes)

---

### Exercise 2 — Fix the Broken Heading Structure

The following page has **four heading structure errors**. Find and fix them all.

**Broken code:**

```html
<!DOCTYPE html>
<html lang="en">
<body>

<h2>My Photography Blog</h2>

<h1>Landscape Photography</h1>
<h5>Mountains</h5>
<h5>Oceans</h5>

<h1>Portrait Photography</h1>
<h5>Studio Shots</h5>
<h5>Outdoor Portraits</h5>

</body>
</html>
```

**Four errors:**

1. The page title uses `<h2>` instead of `<h1>`
2. The major section headings use `<h1>` when they should be `<h2>` (there are two `<h1>` tags)
3. The subsections jump directly from `<h2>` to `<h5>` — skipping `<h3>` and `<h4>`
4. Having two `<h1>` tags violates the one-`<h1>`-per-page rule

**Corrected code:**

```html
<!DOCTYPE html>
<html lang="en">
<body>

<h1>My Photography Blog</h1>        <!-- Fix 1: page title should be h1 -->

<h2>Landscape Photography</h2>      <!-- Fix 2 & 4: section title → h2 -->
<h3>Mountains</h3>                  <!-- Fix 3: subsection → h3, not h5 -->
<h3>Oceans</h3>

<h2>Portrait Photography</h2>       <!-- Fix 2 & 4: section title → h2 -->
<h3>Studio Shots</h3>               <!-- Fix 3: subsection → h3 -->
<h3>Outdoor Portraits</h3>

</body>
</html>
```

**Expected output:**

```
My Photography Blog         ← clear page title (large)

Landscape Photography       ← section (medium-large)
  Mountains                 ← subsection (medium)
  Oceans

Portrait Photography
  Studio Shots
  Outdoor Portraits
```

---

### Exercise 3 — Build a Heading Hierarchy from an Outline

You are given this text outline. Write the correct HTML heading tags for each item:

```
Tech News Today                          ← page title
  Artificial Intelligence                ← major section
    Large Language Models                ← subsection
    Computer Vision                      ← subsection
  Cybersecurity                          ← major section
    Ransomware Threats                   ← subsection
    Best Practices for Companies         ← subsection
  Blockchain                             ← major section
```

**Solution:**

```html
<!DOCTYPE html>
<html lang="en">
<body>

<h1>Tech News Today</h1>

<h2>Artificial Intelligence</h2>
<h3>Large Language Models</h3>
<h3>Computer Vision</h3>

<h2>Cybersecurity</h2>
<h3>Ransomware Threats</h3>
<h3>Best Practices for Companies</h3>

<h2>Blockchain</h2>

</body>
</html>
```

---

### Exercise 4 — Custom Heading Sizes

**Objective:** Build a page with three headings, each with a custom `font-size` applied via the `style` attribute. Use a different colour for each heading as well.

**Requirements:**

- `<h1>` at `font-size:70px` in `darkblue`
- `<h2>` at `font-size:36px` in `darkgreen`
- `<h3>` at `font-size:22px` in `maroon`

**Solution:**

```html
<!DOCTYPE html>
<html lang="en">
<body>

<h1 style="font-size:70px; color:darkblue;">Welcome to AfriTech Blog</h1>

<h2 style="font-size:36px; color:darkgreen;">Latest in African Technology</h2>

<h3 style="font-size:22px; color:maroon;">Startup Spotlights</h3>

<p>Here are this week's most exciting African tech startups to watch...</p>

</body>
</html>
```

**Expected output:** A very large dark-blue page title (70px), a medium dark-green section heading (36px), and a small maroon subheading (22px), followed by body text.

---

## HTML Headings Code Challenges

---

### Challenge 1 — Heading or Not?

For each scenario below, decide: should it use a heading tag, and if so which level? Or should it use something else?

**Scenario A:** The main title of a recipe page for "Egusi Soup"

- **Answer:** `<h1>Egusi Soup</h1>` — this is the primary page title

**Scenario B:** The word "Ingredients" introducing a list of ingredients on the same recipe page

- **Answer:** `<h2>Ingredients</h2>` — a major section of the recipe

**Scenario C:** A note at the bottom saying "Recipe serves 4 people"

- **Answer:** `<p>Recipe serves 4 people</p>` — supporting detail, not a section heading

**Scenario D:** The word "Preparation" introducing the cooking steps

- **Answer:** `<h2>Preparation</h2>` — another major section

**Scenario E:** "Step 1: Toast the egusi" inside the Preparation section

- **Answer:** `<h3>Step 1: Toast the egusi</h3>` — a sub-step within the Preparation section

**Scenario F:** The author's name "By Chef Adaeze" displayed large at the top of the page

- **Answer:** `<p style="font-size:18px;">By Chef Adaeze</p>` — it is not a section heading, just a large-styled detail

---

### Challenge 2 — Build a Recipe Page with Correct Heading Structure

**Task:** Build a complete recipe page for any dish you like, using a correct heading hierarchy with at least `<h1>`, two `<h2>` sections, and at least two `<h3>` sub-items. Include paragraphs and the `lang` attribute on `<html>`.

**Solution (example — Jollof Rice):**

```html
<!DOCTYPE html>
<html lang="en-NG">
<body>

<h1>Nigerian Jollof Rice</h1>
<p>A classic, smoky, flavour-packed West African staple loved across the continent.</p>

<h2>Ingredients</h2>

<h3>For the Tomato Base</h3>
<p>5 large tomatoes, 3 red peppers, 2 onions, scotch bonnet peppers to taste.</p>

<h3>For the Rice</h3>
<p>3 cups long-grain parboiled rice, 2 cups chicken stock, salt, curry powder, thyme.</p>

<h2>Method</h2>

<h3>Preparing the Tomato Base</h3>
<p>Blend all tomato base ingredients until smooth. Fry in hot oil for 20–30 minutes until the raw smell disappears and the mixture darkens.</p>

<h3>Cooking the Rice</h3>
<p>Add the rice to the tomato base, pour in chicken stock, season with salt and spices, cover tightly and cook on low heat for 30 minutes until the rice is cooked and slightly smoky.</p>

<h2>Tips</h2>
<p>For the signature smoky "party jollof" flavour, allow the bottom of the pot to catch slightly at the end of cooking.</p>

</body>
</html>
```

**Expected output:**

```
Nigerian Jollof Rice                  ← large h1 title
A classic, smoky, flavour-packed...   ← intro paragraph

Ingredients                           ← h2 section
  For the Tomato Base                 ← h3 subsection
  5 large tomatoes...                 ← paragraph
  For the Rice                        ← h3 subsection
  3 cups long-grain...

Method
  Preparing the Tomato Base
  Blend all tomato base...
  Cooking the Rice
  Add the rice to the tomato...

Tips
For the signature smoky...
```

---

### Challenge 3 — Identify What Is Wrong

A student wrote the following heading structure for a blog page. List every problem you can find and write the corrected version.

**Student's code:**

```html
<h3>My Tech Blog</h3>
<h2 style="font-size:8px;">Welcome!</h2>
<h1>About Coding</h1>
<h1>About Design</h1>
<h6>What I Write About</h6>
```

**Problems:**

1. `<h3>` is used as the page title — it should be `<h1>`
2. `<h2>` is styled with `font-size:8px` — making it invisible/tiny. Using CSS to make a heading invisible is bad practice; if it needs to be hidden, rethink the structure entirely
3. There are **two** `<h1>` tags — only one is allowed per page
4. Heading levels jump from `<h1>` directly to `<h6>` — skipping four levels
5. The headings are not in a logical, sequential order (h3, h2, h1, h1, h6 makes no structural sense)

**Corrected version:**

```html
<h1>My Tech Blog</h1>
<p>Welcome!</p>
<h2>About Coding</h2>
<h2>About Design</h2>
<h3>What I Write About</h3>
```

---

### Challenge 4 — Heading Size Challenge

**Task:** Write a page where ALL of the following are true simultaneously:

- The `<h1>` appears visually **smaller** than the `<h2>` (achieved through custom `font-size`)
- The `<h3>` appears the same size as the `<h1>`
- The semantic hierarchy is still h1 → h2 → h3 (correct nesting order)

This challenge tests whether you understand that **visual size and semantic level are independent**.

**Solution:**

```html
<!DOCTYPE html>
<html lang="en">
<body>

<!-- h1 styled small — still semantically the most important heading -->
<h1 style="font-size:16px;">Page Title (h1, styled small — 16px)</h1>

<!-- h2 styled very large — still semantically a section heading -->
<h2 style="font-size:60px;">Big Section (h2, styled large — 60px)</h2>

<!-- h3 styled same as h1 visually — still semantically a subsection -->
<h3 style="font-size:16px;">Sub-section (h3, styled same as h1 — 16px)</h3>

</body>
</html>
```

**Expected visual output:**

```
Page Title (h1, styled small — 16px)    ← looks small despite being h1
BIG SECTION (h2, styled large — 60px)  ← looks massive despite being h2
Sub-section (h3, styled same as h1)    ← looks identical to h1 visually
```

**Key insight:** A screen reader reads this as: "Heading level 1: Page Title. Heading level 2: Big Section. Heading level 3: Sub-section." The semantic hierarchy is perfectly correct even though the visual sizes are unusual. This demonstrates that heading tags carry structural meaning independent of their appearance.

---

### Challenge 5 — Full News Website Heading Structure

**Task:** Build the heading structure for a news website homepage. It must include:

- One `<h1>` for the site name
- At least three `<h2>` sections (e.g., Top Stories, Business, Sport)
- At least two `<h3>` article titles under each `<h2>` section
- A custom `font-size` on the `<h1>` (make it impressive)
- The `lang="en"` attribute on `<html>`
- At least one paragraph per `<h2>` section

**Solution:**

```html
<!DOCTYPE html>
<html lang="en">
<body>

<h1 style="font-size:64px; color:darkred;">The Daily Tribune</h1>
<p style="color:grey;">Your trusted source for news across Africa and beyond.</p>

<h2>Top Stories</h2>
<h3>Nigeria Launches New Space Agency Initiative</h3>
<p>The federal government announced plans to establish a national space programme with funding from the 2026 budget.</p>
<h3>Pan-African Free Trade Zone Reaches New Milestone</h3>
<p>Trade volumes across AFCFTA member states have risen by 23% in the first quarter of this year.</p>

<h2>Business &amp; Technology</h2>
<h3>Lagos Startup Raises $12M Series A Funding</h3>
<p>A Lagos-based fintech company has secured significant investment to expand its mobile payment platform across West Africa.</p>
<h3>Renewable Energy Investment in Africa Hits Record High</h3>
<p>Solar and wind energy projects across the continent attracted over $6 billion in foreign investment last year.</p>

<h2>Sport</h2>
<h3>Super Eagles Qualify for AFCON Quarter-Finals</h3>
<p>Nigeria's national football team booked their place in the knockout rounds with a convincing 3–1 victory.</p>
<h3>African Athletes Shine at World Athletics Championships</h3>
<p>Athletes from Kenya, Ethiopia, and Nigeria claimed a combined eight medals at this year's championships.</p>

</body>
</html>
```

**Expected output:** A bold dark-red site title, followed by three clearly organised sections (Top Stories, Business & Technology, Sport), each with two article headlines and supporting paragraphs.

---

## Mini Project — Build a Complete Wikipedia-Style Article Page

Bring together everything from Lessons 2 through 5 to build a richly structured article page that uses headings, paragraphs, images, links, and inline styling in a professional, real-world way.

---

### Project Overview

**Project name:** My HTML Knowledge Article  
**Goal:** A polished, correctly headed article on any topic you find interesting, demonstrating a complete and logical heading hierarchy alongside all the elements and attributes you have learned.

---

### Stage 1 — Plan Your Heading Outline First

Before writing any HTML, plan your heading structure on paper. A good article outline:

```
[Your Topic]                         ← h1
  Introduction / Overview            ← h2
  [Major Section 1]                  ← h2
    [Subsection 1a]                  ← h3
    [Subsection 1b]                  ← h3
  [Major Section 2]                  ← h2
    [Subsection 2a]                  ← h3
  [Conclusion / Summary]             ← h2
```

Example outline for an article about Nigeria:

```
Nigeria                              ← h1
  Overview                           ← h2
  Geography                          ← h2
    Major Cities                     ← h3
    Climate                          ← h3
  Culture & Society                  ← h2
    Languages                        ← h3
    Music & Arts                     ← h3
  Economy                            ← h2
  External Links                     ← h2
```

---

### Stage 2 — Build the Full Page

```html
<!DOCTYPE html>
<html lang="en-NG">
<body>

<h1 style="font-size:52px; color:darkgreen;">Nigeria</h1>

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/79/Flag_of_Nigeria.svg/1920px-Flag_of_Nigeria.svg.png?_=20190924030125"
     alt="The flag of Nigeria — two equal vertical green stripes on the outside with a white stripe in the centre"
     width="320"
     height="213">

<h2>Overview</h2>
<p>Nigeria is the most populous country in Africa, with over 220 million people. It is located in West Africa, bordered by Benin to the west, Niger to the north, Chad to the north-east, and Cameroon to the east. Its coast lies on the Gulf of Guinea in the south.</p>
<p>The country gained independence from British colonial rule on <strong>1 October 1960</strong> and became a republic in 1963.</p>

<h2>Geography</h2>
<p>Nigeria covers an area of approximately 923,768 square kilometres, making it the 32nd largest country in the world.</p>

<h3>Major Cities</h3>
<p>Lagos is the largest city and the economic capital, with a population exceeding 15 million. Abuja is the federal capital, designed and built from scratch in the 1980s. Kano, Ibadan, and Port Harcourt are other major urban centres.</p>

<h3>Climate</h3>
<p>Nigeria experiences a tropical climate. The south has a humid equatorial climate with two rainy seasons, while the north has a semi-arid climate with one shorter rainy season.</p>

<h2>Culture &amp; Society</h2>
<p>Nigeria is home to over 250 ethnic groups, making it one of the most ethnically diverse countries in the world.</p>

<h3>Languages</h3>
<p>The official language is English. The three largest indigenous languages — Yoruba, Hausa, and Igbo — each have tens of millions of native speakers. Nigerian Pidgin is also widely spoken as a lingua franca across the country.</p>

<h3>Music &amp; Arts</h3>
<p>Nigeria is globally renowned for its music scene. Afrobeats — popularised by artists such as Burna Boy, Wizkid, and Davido — has achieved worldwide commercial and critical success. Nollywood, Nigeria's film industry, is the second-largest in the world by output.</p>

<h2>Economy</h2>
<p>Nigeria has the largest economy in Africa by GDP. Key sectors include oil and gas, telecommunications, banking, agriculture, and entertainment. The country is a leading producer of crude oil, which accounts for a significant share of government revenue.</p>

<h2>External Links</h2>
<p>
  <a href="https://services.gov.ng" title="Official website of the Federal Republic of Nigeria">
    Official Government of Nigeria Website
  </a>
</p>
<p>
  <a href="https://en.wikipedia.org/wiki/Nigeria" title="Nigeria article on Wikipedia">
    Nigeria on Wikipedia
  </a>
</p>

</body>
</html>
```

> The `<strong>` tag is used above — it makes text bold and also carries semantic meaning (important emphasis). You will learn it fully in the HTML Formatting lesson.

---

### Stage 3 — Heading Audit

Review your finished page and check every heading:

- [ ] Is there exactly **one** `<h1>` tag?
- [ ] Is the `<h1>` the main title of the entire page?
- [ ] Does every `<h2>` represent a major section of the article?
- [ ] Does every `<h3>` represent a subsection within the `<h2>` immediately above it?
- [ ] Are no heading levels skipped?
- [ ] Is every heading used because the text is a genuine section title (not just for visual size)?
- [ ] Does the `<html>` tag have a `lang` attribute?

---

### Stage 4 — Reflection Questions

1. Why did you use `<h1>` only once for your article topic, even though the country name also appears in paragraphs?
2. If Google searches for "Nigeria culture", which of your headings would help that particular page rank for that search term?
3. A screen reader user navigates your page by headings only, skipping all paragraph text. Read only your heading text aloud in order. Does it make sense as a standalone summary of the article?
4. If your article were printed as a document, how would the heading hierarchy map to a traditional outline?
5. The `font-size:52px` on your `<h1>` makes it visually larger. If you removed that style, what would the page look like? Would anything important change for SEO or accessibility?

---

## Common Beginner Mistakes — Full Summary for This Lesson

**Hierarchy Mistakes:**

- Using multiple `<h1>` tags — one page, one `<h1>`, always
- Starting the page with `<h2>` or `<h3>` instead of `<h1>`
- Skipping levels: going from `<h1>` to `<h4>` without `<h2>` and `<h3>`
- Reversing order: `<h3>` before `<h2>` before `<h1>` on the same page

**Misuse Mistakes:**

- Using `<h1>` multiple times for every section that "feels important"
- Using heading tags purely to make text look big — use CSS for visual size
- Using `<b>` or `<strong>` inside `<p>` tags to fake section titles — use actual heading tags
- Putting extremely long sentences inside heading tags — headings should be short titles, not sentences

**Styling Mistakes:**

- Using `font-size` to make a heading so small it is invisible — defeats the purpose entirely
- Forgetting the semicolon in inline style: `style="font-size:60px color:blue"` — should be `font-size:60px; color:blue;`
- Not adding the `px` unit: `style="font-size:60"` — browser may not recognise it (always include a unit)

**Accessibility Mistakes:**

- Writing bold, large text as a paragraph instead of a heading — screen readers cannot navigate it
- Incorrect heading order — assistive technology relies on predictable, sequential heading levels
- Using headings for table labels or captions — those have dedicated tags (`<th>`, `<caption>`) you will learn later

---

## Reflection Questions

1. In your own words, explain what an HTML heading is and why it is different from simply making text large with CSS.
2. You are building a five-page website. Should each page have its own `<h1>`, or should only the home page have one? Why?
3. A search engine crawler visits your page and reads only the heading tags. What would it learn about your page? Is that a good summary of your content?
4. A visually impaired user navigates your page with a screen reader, pressing the "next heading" key repeatedly. What would they hear for the Nigeria article page you built in the mini project?
5. Why does the W3Schools source specifically say "Use HTML headings for headings only. Don't use headings to make text BIG or bold"? What would go wrong if everyone ignored this rule?
6. You are hired to audit a website. You find the page starts with `<h3>`, then uses `<h1>` for sub-sections, and has no `<h2>` at all. Write a brief report explaining each problem and how to fix it.
7. What does the `font-size` CSS property control? How is it different from choosing a heading level?

---

## Lesson Completion Checklist

- [ ] I know there are six HTML heading levels: `<h1>` through `<h6>`
- [ ] I understand that `<h1>` is the most important and `<h6>` is the least important
- [ ] I know that browsers display each level with a different default size (h1 largest, h6 smallest)
- [ ] I understand that browsers automatically add white space (margin) before and after headings
- [ ] I know the three reasons headings matter: document structure, SEO, and accessibility
- [ ] I can explain how search engines use heading tags to understand page content
- [ ] I can explain how screen readers use headings to allow navigation by heading
- [ ] I understand the one-`<h1>`-per-page rule and why it exists
- [ ] I know that heading levels must be used in sequential order without skipping levels
- [ ] I can use `style="font-size:Xpx;"` to override a heading's default size
- [ ] I understand that visual size and semantic importance are independent — they can be overridden separately
- [ ] I know never to use heading tags just to make text big or bold — that is CSS's job
- [ ] I completed all four guided exercises
- [ ] I completed all five code challenges
- [ ] I built the Wikipedia-style article mini project
- [ ] I audited my project's heading structure using the Stage 3 checklist
- [ ] I answered all seven reflection questions

---

## Lesson Summary

In Lesson 5 you moved beyond just *writing* headings to truly *understanding* them — their levels, their purpose, their rules, and how to customise them.

**The six levels:** `<h1>` is the largest and most important; `<h6>` is the smallest and least important. All are bold by default and surrounded by automatic margins. Use them in sequential order without skipping.

**Why headings matter — three reasons:**

- **Structure:** Headings allow users to scan and navigate your content at a glance
- **SEO:** Search engines read your `<h1>` as your page's main topic and use all headings to understand your content's outline
- **Accessibility:** Screen readers let users jump between headings — the heading hierarchy is the skeleton of your page for millions of users with visual impairments

**Custom sizes:** Use `style="font-size:Xpx;"` to override default heading sizes. Remember that visual size and semantic importance are separate — the tag determines meaning, the `font-size` determines appearance.

**The golden rule:** Use headings for genuine section titles only. Never use heading tags just to make text look big or bold. Use CSS for visual styling; use heading tags for structural meaning.

> **Coming up in Lesson 6:** You will study **HTML Paragraphs** in depth — the `<p>` element's rules, how browsers handle whitespace, the `<pre>` element for preserving formatting, horizontal rules with `<hr>`, and the critical CSS properties that control paragraph spacing and appearance.

---

*Sources: W3Schools HTML Headings (<https://www.w3schools.com/html/html_headings.asp>) and HTML Headings Code Challenges (<https://www.w3schools.com/html/html_challenges_headings.asp>)*
