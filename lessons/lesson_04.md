---
render_with_liquid: false
title: "Lesson 4 — HTML Attributes: Syntax, Key Attributes, Quoting Rules & Best Practices"
nav_order: 4
---

## Lesson Introduction

Welcome to Lesson 4! Over the last three lessons you have built a solid foundation:
- Lesson 2 — You wrote your first real HTML pages using core tags
- Lesson 3 — You understood exactly what an HTML *element* is and how nesting works

Now it is time to fully master **HTML attributes** — the extra instructions you write *inside* opening tags to give elements more power, behaviour, and meaning.

You have already *used* attributes. Every time you wrote `href="..."` in a link or `src="..."` in an image, you used an attribute. But in this lesson you will truly *understand* them — what they are, why they exist, all their rules, and how to use each major one with confidence.

By the end of this lesson you will be able to:

- Define what an HTML attribute is and explain its syntax precisely
- Write attributes correctly using the `name="value"` format
- Explain and use the seven most important HTML attributes: `href`, `src`, `width`, `height`, `alt`, `style`, `lang`, and `title`
- Understand the difference between absolute and relative URLs in the `src` attribute
- Know the quoting rules for attribute values and when each applies
- Follow professional best practices (lowercase, always quote)
- Diagnose and fix all common attribute mistakes

> **Real-world connection:** Attributes are the knobs and dials of HTML. The tag says *what* the element is — the attributes control *how* it behaves. A link without `href` goes nowhere. An image without `src` shows nothing. A page without `lang` confuses search engines and accessibility tools. Mastering attributes means mastering control.

---

## Prerequisite Concepts

### Quick Recap — What Is an Element? What Is a Tag?

From Lesson 3:
- A **tag** is just the label: `<a>` or `</a>`
- An **element** is the full package: `<a href="...">text</a>`
- Attributes live **inside the opening tag** — never in the closing tag

You have already seen attributes used. This lesson explains every rule governing them.

---

## Part 1 — What Is an HTML Attribute?

### The Definition

An **HTML attribute** is extra information added to an HTML element's **opening tag** that modifies or extends the element's behaviour, appearance, or meaning.

Think of a tag as a basic instruction and its attributes as the settings for that instruction.

> **Analogy:** Imagine ordering a coffee. The coffee type (`latte`, `espresso`) is like the tag — it names the thing. The customisations (`size: large`, `milk: oat`, `sugar: none`) are like attributes — they specify exactly *how* you want that thing to be. Without the customisations, you just get a default coffee. With them, you get exactly what you need.

---

### The Syntax — Name/Value Pairs

Every attribute follows this exact structure:

```
name="value"
```

Where:
- **`name`** — the name of the attribute (what setting you are configuring)
- **`=`** — separates the name from the value
- **`"value"`** — the value of that setting, always wrapped in quotes

Attributes are placed **inside the opening tag**, after the tag name, separated by a space:

```html
<tagname name="value">Content</tagname>
```

Here is a real example:

```html
<a href="https://www.w3schools.com">Visit W3Schools</a>
```

Breaking it down:

```
<a   href="https://www.w3schools.com"   >Visit W3Schools</a>
 │        │                      │      │
 │        attribute name         │      │
 │                               │      │
 tag name                    value      closing bracket of opening tag
```

| Part | What it is |
|------|-----------|
| `a` | The tag name (anchor / link) |
| `href` | The attribute name |
| `=` | The separator between name and value |
| `"https://www.w3schools.com"` | The attribute value (in double quotes) |
| `Visit W3Schools` | The element's content (the clickable text) |
| `</a>` | The closing tag |

---

### Multiple Attributes on One Element

An element can have **more than one attribute**. Simply separate them with spaces inside the opening tag:

```html
<img src="photo.jpg" alt="A smiling student" width="300" height="200">
```

This `<img>` element has **four attributes**:
- `src="photo.jpg"` — the image file to display
- `alt="A smiling student"` — the text description
- `width="300"` — 300 pixels wide
- `height="200"` — 200 pixels tall

> **Order does not matter.** You can write attributes in any order within the opening tag and they will work identically. However, consistency and readability matter — develop a habit of writing attributes in a logical order (e.g., `src` before `alt` before sizing attributes).

---

### Four Universal Rules for Attributes

Before learning individual attributes, memorise these four rules:

1. **Attributes always go in the opening tag** — never in the closing tag
2. **Attributes are written as name/value pairs** — `name="value"`
3. **Attribute values must always be quoted** — use `"double"` or `'single'` quotes
4. **Attribute names should always be lowercase** — `href` not `HREF`

We will look at the quoting and case rules in detail in Part 7.

---

## Part 2 — The `href` Attribute

### What Is `href`?

The `href` attribute belongs to the `<a>` (anchor) tag. It stands for **Hypertext REFerence** and holds the **URL** (web address) of the destination the link navigates to when clicked.

```html
<a href="https://www.w3schools.com">Visit W3Schools</a>
```

Without `href`, the `<a>` tag renders as styled text but does nothing when clicked. `href` is what makes a link actually *go somewhere*.

---

### Simple Example — A Basic Link

```html
<!DOCTYPE html>
<html>
<body>

<h1>My Favourite Resources</h1>
<a href="https://www.w3schools.com">Visit W3Schools</a>

</body>
</html>
```

**Expected output in browser:**

```
My Favourite Resources

Visit W3Schools    ← blue, underlined, navigates to w3schools.com when clicked
```

---

### Second Example — Links in Context

```html
<!DOCTYPE html>
<html>
<body>

<h1>Learning Resources</h1>
<p>Start with <a href="https://www.w3schools.com">W3Schools</a> for tutorials.</p>
<p>Practice projects at <a href="https://www.github.com">GitHub</a>.</p>
<p>Ask questions at <a href="https://stackoverflow.com">Stack Overflow</a>.</p>

</body>
</html>
```

**Expected output in browser:**

```
Learning Resources

Start with W3Schools for tutorials.
Practice projects at GitHub.
Ask questions at Stack Overflow.
```

(W3Schools, GitHub, and Stack Overflow each appear as clickable blue links within their sentences.)

> **Thinking prompt:** What happens if you write `href=""` (an empty value)? The browser treats it as a link to the current page — clicking it just reloads the same page.

---

### Common Beginner Mistakes with `href`

```html
<!-- WRONG 1: Missing https:// — browser looks for a local file -->
<a href="www.google.com">Google</a>

<!-- WRONG 2: href in the closing tag — attributes only go in opening tags -->
<a>Visit Google</a href="https://www.google.com">

<!-- WRONG 3: Space between attribute name and = sign -->
<a href ="https://www.google.com">Google</a>

<!-- CORRECT: href in opening tag, no spaces around =, full URL -->
<a href="https://www.google.com">Google</a>
```

---

## Part 3 — The `src` Attribute

### What Is `src`?

The `src` attribute belongs to the `<img>` tag. It stands for **source** and holds the **path** (file location or URL) of the image to display.

```html
<img src="img_girl.jpg">
```

Without `src`, the browser has no idea which image to show. The result is a broken image icon.

---

### Absolute URLs vs Relative URLs

There are two ways to specify the path in `src` (and also in `href`). Understanding this is critical for all web development.

#### Absolute URL

An **absolute URL** is a complete, full web address — it includes the protocol (`https://`), the domain name, and the full path to the file.

```html
<img src="https://www.w3schools.com/images/img_girl.jpg" alt="Girl with a jacket">
```

Absolute URLs point to files on **other websites** (external). They always begin with `https://` or `http://`.

**Important warnings about external images:**
- The image may be under **copyright** — you need permission to use it
- You have no control over external images — the owner can delete or change the image at any time, breaking your page
- Loading external images can be slower than loading local ones

#### Relative URL

A **relative URL** points to a file on **your own website**. It does not include the domain name — it is described relative to the current file's location.

**Type 1 — Same folder as the HTML file:**
```html
<img src="img_girl.jpg" alt="Girl with a jacket">
```

If your HTML file is at `mysite.com/index.html` and the image is also in the root folder, the browser looks for `mysite.com/img_girl.jpg`.

**Type 2 — File is in a subfolder:**
```html
<img src="images/img_girl.jpg" alt="Girl with a jacket">
```

The browser looks one level deeper into an `images` folder.

**Type 3 — URL starts with a slash (relative to domain root):**
```html
<img src="/images/img_girl.jpg" alt="Girl with a jacket">
```

The `/` at the start means "start from the root of the domain". Regardless of which folder the HTML file is in, the browser looks for `images/img_girl.jpg` at the root of the website.

> **Best practice tip:** Almost always use **relative URLs** for images and files on your own website. If you ever move your site to a different domain name, relative URLs keep working — absolute URLs to your old domain would break.

---

### Simple Example — Relative URL Image

Imagine your project folder looks like this:

```
my-website/
├── index.html
├── photo.jpg
└── images/
    └── logo.png
```

```html
<!DOCTYPE html>
<html>
<body>

<!-- Image in the same folder -->
<img src="photo.jpg" alt="My profile photo" width="200" height="200">

<!-- Image in the images subfolder -->
<img src="images/logo.png" alt="My website logo" width="150" height="50">

</body>
</html>
```

**Expected output:** Both images display, because the browser finds them by following the relative paths from the HTML file's location.

---

### Second Example — Absolute URL Image (from the web)

```html
<!DOCTYPE html>
<html>
<body>

<h1>Planet Earth</h1>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/97/The_Earth_seen_from_Apollo_17.jpg/320px-The_Earth_seen_from_Apollo_17.jpg"
     alt="Earth seen from space"
     width="320"
     height="320">
<p>This image is hosted on Wikipedia's servers.</p>

</body>
</html>
```

**Expected output:**

```
Planet Earth

[Photo of Earth from space — 320×320 pixels]

This image is hosted on Wikipedia's servers.
```

> **Thinking prompt:** What would happen to this page if Wikipedia deleted or renamed that image file? The image would show a broken icon, and your page would look incomplete. This is why hosting your own images and using relative URLs is safer.

---

## Part 4 — The `width` and `height` Attributes

### What Are They?

The `width` and `height` attributes on `<img>` tags set the **dimensions** of an image in **pixels** (px).

```html
<img src="img_girl.jpg" width="500" height="600">
```

This displays the image at 500 pixels wide and 600 pixels tall.

---

### Why Should You Always Include Them?

Beyond just controlling image size, specifying `width` and `height` serves a crucial technical purpose: **it reserves space on the page before the image loads**.

When a browser loads a page, it first reads the HTML and builds the page layout. If image dimensions are not specified, the browser does not know how much space to leave for the image. When the image eventually loads, the entire page layout suddenly shifts — text jumps, buttons move, users lose their place. This jarring experience is called **layout shift** and is considered a major web performance problem.

By specifying `width` and `height`, the browser pre-allocates the correct space, so nothing jumps when the image loads.

---

### Simple Example — Image with Fixed Dimensions

```html
<!DOCTYPE html>
<html>
<body>

<h2>With width and height specified:</h2>
<img src="cat.jpg" alt="A tabby cat" width="300" height="200">

<h2>Same image, no dimensions — risk of layout shift:</h2>
<img src="cat.jpg" alt="A tabby cat">

</body>
</html>
```

**Expected output for first image:** Displays at exactly 300×200 pixels.

**Expected output for second image:** Displays at whatever the image's natural size is (could be enormous or tiny).

> **Thinking prompt:** If you set `width="600"` but keep `height="200"` on an image that is naturally square (e.g., 400×400), what would happen? The image would appear stretched horizontally and squashed vertically. To avoid distortion when resizing, set only `width` — the browser will automatically scale `height` proportionally. Or set only `height` and let `width` scale.

---

### Example — Resizing Without Distortion

```html
<!-- Set only width — height scales automatically, no distortion -->
<img src="profile.jpg" alt="My profile photo" width="250">

<!-- Set only height — width scales automatically, no distortion -->
<img src="banner.jpg" alt="Website banner" height="80">
```

---

## Part 5 — The `alt` Attribute

### What Is `alt`?

The `alt` attribute on `<img>` provides **alternative text** — a written description of the image. It is displayed when:

1. The image file cannot be found (broken link, wrong filename)
2. The internet connection is too slow to load the image
3. The user is using a **screen reader** (assistive software for visually impaired users)

```html
<img src="img_girl.jpg" alt="Girl with a jacket">
```

The `alt` attribute is described as **required** — while it is technically optional in the code, omitting it is considered a serious accessibility and quality failure.

---

### Why Is `alt` Text One of the Most Important Attributes in HTML?

**Reason 1 — Accessibility.** Over 250 million people worldwide have significant visual impairments. Screen reader software reads web pages aloud to them. When the screen reader reaches an image, it reads the `alt` text. Without `alt`, the user hears nothing — the image is completely invisible to them.

**Reason 2 — Broken images.** When an image fails to load (wrong filename, slow connection, offline), the browser displays the `alt` text in the image's place. A good `alt` text ensures the user still understands what was supposed to be there.

**Reason 3 — Search engine optimisation (SEO).** Search engines like Google are essentially blind to images — they cannot "see" them. They read the `alt` text to understand what an image depicts. Good `alt` text helps your pages rank better for relevant searches.

**Reason 4 — Professional standards.** Web accessibility is required by law in many countries (e.g., Section 508 in the USA, the Equality Act in the UK, and equivalent laws in Nigeria and across Africa). Missing `alt` text can make your website legally non-compliant.

---

### How to Write Good `alt` Text

A good `alt` attribute:
- Describes what is in the image specifically and concisely
- Does not start with "Image of..." or "Picture of..." — screen readers already announce it is an image
- Is meaningful to someone who cannot see the image

```html
<!-- POOR alt text — too vague -->
<img src="product.jpg" alt="image">
<img src="team.jpg" alt="photo">

<!-- GOOD alt text — specific and meaningful -->
<img src="product.jpg" alt="Nike Air Max 270 running shoe in black and white">
<img src="team.jpg" alt="Our five-person development team at the Lagos Tech Hub">
```

For **decorative images** (images that are purely visual decoration with no informational value), use an empty `alt=""`:

```html
<!-- Empty alt tells screen readers to skip this decorative image entirely -->
<img src="divider-line.png" alt="">
```

---

### Simple Example — Demonstrating alt in Action

```html
<!DOCTYPE html>
<html>
<body>

<h1>Correct image (alt shown only if image fails):</h1>
<img src="img_girl.jpg" alt="Girl with a jacket" width="500" height="600">

<h1>Wrong filename (alt text displayed instead):</h1>
<img src="wrong_filename.jpg" alt="Girl with a jacket" width="500" height="600">

</body>
</html>
```

**Expected output — first image:** The photo displays normally (alt text is invisible unless you inspect with a screen reader).

**Expected output — second image:** A broken image icon and the text `Girl with a jacket` appears in its place — because the file `wrong_filename.jpg` does not exist.

---

### Second Example — Real-World Alt Text in a News Article

```html
<!DOCTYPE html>
<html>
<body>

<h1>Lagos Tech Week 2025</h1>

<img src="keynote.jpg"
     alt="Tech entrepreneur speaking on stage at Lagos Tech Week 2025, with a large screen showing a rocket launch behind them"
     width="800"
     height="450">

<p>Over 3,000 developers attended this year's Lagos Tech Week.</p>

</body>
</html>
```

This `alt` text is excellent because it:
- Describes the scene specifically
- Gives context (the event name)
- Describes what is visible on the background screen
- Would be genuinely useful to a visually impaired person

---

## Part 6 — The `style` Attribute

### What Is `style`?

The `style` attribute is used to add **inline CSS styling** directly to an individual HTML element. It controls visual properties like text colour, font size, background colour, margins, and much more.

```html
<p style="color:red;">This is a red paragraph.</p>
```

**Expected output:**

```
This is a red paragraph.    ← displayed in red text
```

---

### How the `style` Attribute Works

The value of the `style` attribute is written as one or more **CSS property:value** pairs, separated by semicolons (`;`):

```
style="property:value;"
style="property1:value1; property2:value2;"
```

For example:

```html
<p style="color:blue; font-size:20px; background-color:yellow;">
  Styled paragraph
</p>
```

**Expected output:** Blue text, 20px font size, on a yellow background.

---

### Simple Example — Styling Different Elements

```html
<!DOCTYPE html>
<html>
<body>

<h1 style="color:navy;">My Web Page</h1>
<p style="color:green;">This paragraph is green.</p>
<p style="color:red; font-size:18px;">This paragraph is red and larger.</p>
<p style="background-color:lightblue;">This paragraph has a blue background.</p>

</body>
</html>
```

**Expected output in browser:**

```
My Web Page          ← heading in navy blue
This paragraph is green.   ← green text
This paragraph is red and larger.   ← red text, bigger font
This paragraph has a blue background.  ← text on light blue background
```

---

### Second Example — Styling a Heading and an Image

```html
<!DOCTYPE html>
<html>
<body>

<h1 style="color:purple; text-align:center;">Welcome to My Website</h1>

<img src="photo.jpg"
     alt="My profile photo"
     width="200"
     height="200"
     style="border:3px solid black;">

<p style="font-family:Arial; color:grey;">
  This text uses a sans-serif font in grey.
</p>

</body>
</html>
```

**Expected output:** Purple centred heading, image with a black border, grey Arial paragraph text.

---

### A Note on Inline Styles vs External CSS

While `style` attributes work perfectly and are great for learning, professional developers use **external CSS files** for styling rather than inline `style` attributes on every element.

The reason: imagine you have 100 paragraphs and you want them all green. With `style` attributes, you must add `style="color:green;"` to all 100. With an external CSS file, you write one rule that applies to all paragraphs at once.

You will learn CSS in full in a separate course. For now, `style` attributes are the perfect way to see styling take effect immediately and understand how CSS properties work.

---

## Part 7 — The `lang` Attribute

### What Is `lang`?

The `lang` attribute is placed on the `<html>` element and declares the **natural language** of the web page's content.

```html
<html lang="en">
```

This tells search engines, browsers, and accessibility tools: "The content of this page is written in English."

---

### Why Is `lang` Important?

**For search engines:** Google and other search engines use `lang` to serve your page to users searching in the right language.

**For browsers:** Some browsers use `lang` to decide whether to offer a translation option.

**For screen readers:** Screen readers use `lang` to apply the correct language pronunciation rules. If `lang` is missing or wrong, a screen reader might try to read English text with French pronunciation rules — making it completely incomprehensible for the listener.

**For accessibility compliance:** Including `lang` is a requirement of the WCAG (Web Content Accessibility Guidelines), which many countries' accessibility laws are based on.

---

### Language Codes

Language codes follow an international standard called **BCP 47**. The most common format is:

- **Two-letter language code alone:** `"en"` (English), `"fr"` (French), `"ar"` (Arabic), `"yo"` (Yoruba), `"ha"` (Hausa)
- **Language code + country code:** `"en-US"` (English, United States), `"en-GB"` (English, United Kingdom), `"en-NG"` (English, Nigeria), `"pt-BR"` (Portuguese, Brazil)

The country code helps when the same language has regional variations (e.g., American English vs British English spellings).

---

### Simple Example — Setting Language to English (UK)

```html
<!DOCTYPE html>
<html lang="en-GB">
<body>

<h1>Welcome to My Website</h1>
<p>This page is written in British English.</p>

</body>
</html>
```

**Expected output:** Page looks identical to any other page — but browsers, screen readers, and search engines now know the language is British English.

---

### Second Example — A Multilingual Note

```html
<!DOCTYPE html>
<html lang="en-NG">
<body>

<h1>My Nigerian Tech Blog</h1>
<p>This page is in English as used in Nigeria.</p>

<!-- A section in Yoruba would ideally use a span with lang attribute -->
<p><span lang="yo">E kaaro</span> — that means "Good morning" in Yoruba.</p>

</body>
</html>
```

> **New concept shown above:** The `lang` attribute is not just for `<html>` — it can also be placed on any individual element to declare a different language for that specific piece of content. This helps screen readers switch pronunciation correctly mid-sentence.

---

### Language Code Quick Reference

| Language | Code | With Region |
|----------|------|-------------|
| English | `en` | `en-US`, `en-GB`, `en-NG` |
| French | `fr` | `fr-FR`, `fr-CA` |
| Spanish | `es` | `es-ES`, `es-MX` |
| Arabic | `ar` | `ar-EG`, `ar-SA` |
| Portuguese | `pt` | `pt-BR`, `pt-PT` |
| Yoruba | `yo` | — |
| Hausa | `ha` | — |
| Igbo | `ig` | — |
| Swahili | `sw` | — |

---

## Part 8 — The `title` Attribute

### What Is `title`?

The `title` attribute adds **extra descriptive information** about an element. When a user hovers their mouse cursor over the element, the browser displays this text as a small pop-up tooltip.

```html
<p title="I'm a tooltip">This is a paragraph.</p>
```

**Expected output:** The paragraph text displays normally. When you hover the mouse over it, a small grey tooltip box appears showing `I'm a tooltip`.

---

### Why Use `title`?

The `title` attribute is used to provide supplementary context that does not need to be visible on the page at all times, but is helpful when the user wants more information.

Common uses:
- Explaining what an abbreviated term means
- Providing extra detail about a link's destination
- Adding a description to an image that already has `alt` text

---

### Simple Example — Tooltip on a Link

```html
<!DOCTYPE html>
<html>
<body>

<a href="https://www.w3schools.com"
   title="Go to W3Schools — the world's largest web development learning site">
  Visit W3Schools
</a>

</body>
</html>
```

**Expected output:** "Visit W3Schools" appears as a clickable link. Hovering the mouse over it shows the tooltip text.

---

### Second Example — Tooltip on an Abbreviation

```html
<!DOCTYPE html>
<html>
<body>

<p>
  The <abbr title="World Wide Web Consortium">W3C</abbr> maintains the
  standards for HTML, CSS, and many other web technologies.
</p>

<p title="Last updated: April 2026">
  This article was recently updated.
</p>

</body>
</html>
```

**Expected output:** Normal paragraph text. Hovering over `W3C` shows `World Wide Web Consortium`. Hovering over the second paragraph shows `Last updated: April 2026`.

> **Note:** The `<abbr>` tag (abbreviation element) is specifically designed to work with `title` for expanding abbreviations. You will learn more about semantic HTML elements in a later lesson.

---

### `title` vs `alt` — Know the Difference

These two attributes are frequently confused by beginners:

| Attribute | Element | Purpose | When shown |
|-----------|---------|---------|-----------|
| `alt` | `<img>` only | Describes the image — **required** for accessibility | When image fails to load; read by screen readers |
| `title` | Any element | Provides supplementary information — **optional** | On mouse hover as a tooltip |

```html
<!-- This is correct: alt for accessibility, title for tooltip info -->
<img src="chart.png"
     alt="Bar chart showing Q3 revenue by region"
     title="Data source: 2025 Annual Report, page 14"
     width="600"
     height="400">
```

The `alt` here helps visually impaired users understand the chart. The `title` provides a source citation that sighted users can see on hover.

---

## Part 9 — Always Use Lowercase Attribute Names

### The Rule

Just as with HTML tag names (Lesson 3), **attribute names should always be written in lowercase**.

The HTML5 standard does not technically require it — `HREF`, `Href`, and `href` all work identically in a browser. But professional standards and the W3C recommendation require lowercase, and for the same reasons as with tags:

- **Readability:** All-lowercase code is much easier to scan
- **Compatibility:** Some stricter document types (XHTML) require lowercase
- **Consistency:** When mixed with CSS and JavaScript (which are case-sensitive), lowercase-everywhere prevents hard-to-spot bugs

```html
<!-- WRONG: uppercase attribute names -->
<a HREF="https://www.google.com">Google</a>
<img SRC="photo.jpg" ALT="My photo" WIDTH="200" HEIGHT="200">

<!-- WRONG: mixed case -->
<a Href="https://www.google.com">Google</a>

<!-- CORRECT: all lowercase -->
<a href="https://www.google.com">Google</a>
<img src="photo.jpg" alt="My photo" width="200" height="200">
```

**Expected output:** Identical for all three — the browser does not care. But your code quality is far superior with the lowercase version.

---

## Part 10 — Always Quote Attribute Values

### The Rule

Attribute values should **always** be wrapped in quotes. The HTML5 standard technically allows some attribute values without quotes, but W3C strongly recommends always quoting, and demands quotes for XHTML.

```html
<!-- "Bad" (technically works in some cases, but discouraged) -->
<a href=https://www.w3schools.com>Visit W3Schools</a>

<!-- "Good" (always correct) -->
<a href="https://www.w3schools.com">Visit W3Schools</a>
```

**Expected output:** Both display identically as a clickable link in most cases. But quoting is always safer.

---

### Why Quoting Is Mandatory — Not Just Recommended

There is one case where missing quotes **always** breaks the code: when the attribute value contains a **space**.

```html
<!-- BROKEN: The title value has a space — browser only reads "Description" -->
<p title=Description of W3Schools>

<!-- CORRECT: Quotes allow the full phrase including spaces -->
<p title="Description of W3Schools">
```

Without quotes, the browser reads `title=Description` and then treats `of` and `W3Schools` as separate broken attributes — completely wrong. This is not a maybe-it-works situation: it **always fails** without quotes.

This is the core reason the rule exists: quoting handles all values safely, including those with spaces, so you never have to think about whether this particular value needs quotes.

---

### Double Quotes vs Single Quotes

HTML supports both `"double"` and `'single'` quotes for attribute values. They are completely equivalent in the browser's eyes.

```html
<!-- Both of these are valid and produce identical results -->
<a href="https://www.google.com">Google</a>
<a href='https://www.google.com'>Google</a>
```

**When to use single quotes:** When the attribute value itself **contains double quotes**, you must use single quotes as the outer wrapper to avoid confusion:

```html
<!-- WRONG: double quotes inside double quotes breaks the attribute -->
<p title="John "ShotGun" Nelson">

<!-- CORRECT: use single quotes when value contains double quotes -->
<p title='John "ShotGun" Nelson'>
```

**The reverse also applies:** If your value contains single quotes, use double quotes as the outer wrapper:

```html
<!-- CORRECT: double quotes when value contains single quotes/apostrophe -->
<p title="Nigeria's largest city is Lagos">
```

> **Best practice:** Default to **double quotes** for all attribute values (it is the overwhelming convention in HTML). Only switch to single quotes when the value itself contains double quotes.

---

### Summary Table — Quoting Rules

| Situation | Use | Example |
|-----------|-----|---------|
| Normal value (no special characters) | `"double"` | `href="https://google.com"` |
| Value contains double quotes | `'single'` | `title='He said "Hello"'` |
| Value contains single quote/apostrophe | `"double"` | `title="Nigeria's capital"` |
| Value contains spaces | Either — but **must use one** | `alt="A blue car"` |
| Value contains no spaces or special chars | `"double"` (preferred) | `width="300"` |

---

## Part 11 — All Key Attributes Quick Reference

Here is a consolidated reference table for every attribute covered in this lesson:

| Attribute | Which Tag(s) | What It Does | Example |
|-----------|-------------|-------------|---------|
| `href` | `<a>` | URL the link navigates to | `href="https://google.com"` |
| `src` | `<img>` | Path or URL of image to display | `src="photo.jpg"` |
| `width` | `<img>` | Image width in pixels | `width="300"` |
| `height` | `<img>` | Image height in pixels | `height="200"` |
| `alt` | `<img>` | Text description of image | `alt="A smiling student"` |
| `style` | Any element | Inline CSS styling | `style="color:red;"` |
| `lang` | `<html>` | Language of the page | `lang="en-NG"` |
| `title` | Any element | Tooltip text on hover | `title="More info here"` |

---

## Guided Practice Exercises

Work through these in order. Each one builds confidence with a specific attribute concept.

---

### Exercise 1 — Label Every Attribute

For each HTML line below, identify the element name, all attribute names, and all attribute values.

**Line 1:**
```html
<a href="https://www.bbc.com" title="Visit BBC News website">BBC News</a>
```

**Answers:**
- Element: `<a>` (anchor/link)
- Attribute 1 name: `href` | value: `"https://www.bbc.com"`
- Attribute 2 name: `title` | value: `"Visit BBC News website"`
- Content: `BBC News`

---

**Line 2:**
```html
<img src="team.jpg" alt="Our five-person team at the office" width="600" height="400">
```

**Answers:**
- Element: `<img>` (image, empty element)
- Attribute 1 name: `src` | value: `"team.jpg"`
- Attribute 2 name: `alt` | value: `"Our five-person team at the office"`
- Attribute 3 name: `width` | value: `"600"`
- Attribute 4 name: `height` | value: `"400"`
- Content: *none (empty element)*

---

**Line 3:**
```html
<p style="color:purple; font-size:16px;" title="Introduction paragraph">
  Welcome to my website.
</p>
```

**Answers:**
- Element: `<p>` (paragraph)
- Attribute 1 name: `style` | value: `"color:purple; font-size:16px;"`
- Attribute 2 name: `title` | value: `"Introduction paragraph"`
- Content: `Welcome to my website.`

---

### Exercise 2 — Fix Five Attribute Errors

The following code contains **five separate attribute mistakes**. Find them all and write the corrected version.

**Broken code:**

```html
<!DOCTYPE html>
<HTML lang=en>
<body>

<h1 STYLE="color:blue">My Technology Blog</h1>
<p>Read the latest at <a HREF=https://www.techcrunch.com title='TechCrunch'>TechCrunch</a>.</p>
<img src="laptop.jpg" ALT=A laptop on a desk width="400" height=300>

</body>
</html>
```

**Five errors:**
1. `<HTML>` — tag name not lowercase (covered in Lesson 3)
2. `lang=en` — attribute value not quoted
3. `STYLE=` — attribute name not lowercase
4. `HREF=` — attribute name not lowercase, and value not quoted
5. `ALT=A laptop on a desk` — attribute name not lowercase AND value with spaces is not quoted, AND `height=300` is not quoted

**Corrected code:**

```html
<!DOCTYPE html>
<html lang="en">                                    <!-- Fix 1: lowercase tag; Fix 2: lang value quoted -->
<body>

<h1 style="color:blue;">My Technology Blog</h1>    <!-- Fix 3: lowercase style -->
<p>Read the latest at <a href="https://www.techcrunch.com" title="TechCrunch">TechCrunch</a>.</p>
                                                    <!-- Fix 4: lowercase href, value quoted -->
<img src="laptop.jpg"
     alt="A laptop on a desk"                       <!-- Fix 5: lowercase alt, value with spaces quoted -->
     width="400"
     height="300">                                  <!-- height value quoted -->

</body>
</html>
```

**Expected output in browser:**

```
My Technology Blog    ← blue heading

Read the latest at TechCrunch.    ← "TechCrunch" is a clickable link

[Laptop image, 400×300 pixels]
```

---

### Exercise 3 — Absolute vs Relative URLs

You are building a website with this folder structure:

```
my-portfolio/
├── index.html
├── about.html
├── images/
│   ├── profile.jpg
│   └── project1.jpg
└── projects/
    └── project-details.html
```

Write the correct `src` or `href` attribute value for each scenario:

**Scenario 1:** You are in `index.html` and want to display `images/profile.jpg`.
```html
<img src="images/profile.jpg" alt="My profile photo">
```

**Scenario 2:** You are in `project-details.html` (inside the `projects/` folder) and want to display `images/project1.jpg` (which is up one level in the parent folder).
```html
<img src="../images/project1.jpg" alt="Project 1 screenshot">
```
> `..` means "go up one folder level" — it is a standard file path convention.

**Scenario 3:** You are in `index.html` and want to link to `about.html` (same folder).
```html
<a href="about.html">About Me</a>
```

**Scenario 4:** You are in `index.html` and want to link to `project-details.html` (inside the `projects/` subfolder).
```html
<a href="projects/project-details.html">View Project Details</a>
```

**Scenario 5:** You want to display an image from an external URL.
```html
<img src="https://example.com/images/banner.jpg" alt="External banner image">
```

---

### Exercise 4 — Build a Correctly Attributed Image Gallery

**Objective:** Create a simple photo gallery page that uses all the image-related attributes correctly.

**Requirements:**
- Valid document structure with `lang` attribute on `<html>`
- A page `<h1>` title with a `style` attribute (any colour)
- Three `<img>` elements, each with `src`, `alt`, `width`, and `height`
- A brief `<p>` caption under each image, using `title` attribute for extra info
- All attributes in lowercase with values quoted

**Solution:**

```html
<!DOCTYPE html>
<html lang="en-NG">
<body>

<h1 style="color:darkgreen;">My Photography Gallery</h1>

<h2>Nature Photos</h2>

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Biome-wet-tropical.jpg/320px-Biome-wet-tropical.jpg"
     alt="Lush tropical rainforest with tall green trees"
     width="320"
     height="213">
<p title="Taken at Okomu National Park, Nigeria">
  Tropical rainforest canopy — one of Earth's most biodiverse ecosystems.
</p>

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1a/24701-nature-natural-beauty.jpg/320px-24701-nature-natural-beauty.jpg"
     alt="Calm river flowing through green hills at sunrise"
     width="320"
     height="213">
<p title="Sunrise photography requires patience and early mornings">
  A tranquil river at sunrise — stillness captured in a frame.
</p>

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/African_savanna_at_Ngorongoro.jpg/320px-African_savanna_at_Ngorongoro.jpg"
     alt="Wide open African savanna landscape with acacia trees"
     width="320"
     height="213">
<p title="The African savanna spans across multiple countries">
  African savanna — vast, open, and breathtaking.
</p>

</body>
</html>
```

**Expected output:** Three images displayed with their captions. Hovering over each caption reveals its tooltip. Page heading is in dark green.

---

## HTML Attributes Code Challenges

These challenges test everything from this lesson: attribute syntax, specific attributes, quoting rules, URL types, and best practices.

---

### Challenge 1 — Spot the Wrong Attributes

Study this element closely. There are **three attribute mistakes**. Name and fix all three.

```html
<img SRC=banner.png ALT="Promotional banner for our summer sale 2025" Width="800" height="200">
```

**Mistakes:**
1. `SRC` — should be lowercase `src`
2. `SRC=banner.png` — the value `banner.png` has no quotes
3. `Width` — should be lowercase `width`

**Corrected version:**

```html
<img src="banner.png" alt="Promotional banner for our summer sale 2025" width="800" height="200">
```

---

### Challenge 2 — Write a Complete, Correct `<html>` Opening Tag

**Task:** Write the opening `<html>` tag for a web page written in Nigerian English.

**Solution:**

```html
<html lang="en-NG">
```

**Bonus — for a French-Canadian page:**

```html
<html lang="fr-CA">
```

---

### Challenge 3 — Inline Style Practice

**Task:** Write a single `<p>` element that has ALL of the following style properties applied using the `style` attribute:
- Text colour: `navy`
- Background colour: `lightyellow`
- Font size: `18px`
- Font family: `Georgia`

**Solution:**

```html
<p style="color:navy; background-color:lightyellow; font-size:18px; font-family:Georgia;">
  This paragraph demonstrates multiple inline CSS properties applied via the style attribute.
</p>
```

**Expected output:** Navy text, on a light yellow background, in Georgia font at 18px size.

---

### Challenge 4 — Quoting Edge Cases

**Task:** Write each of the following as a valid HTML attribute value, choosing the correct quote type:

1. A `title` value that reads: `John "The Eagle" Okafor`
2. A `title` value that reads: `Nigeria's capital city is Abuja`
3. An `alt` value that reads: `Chart showing Africa's GDP growth from 2020 to 2025`
4. A `title` value that reads: He said: "It's a beautiful day in Lagos!"

**Solutions:**

```html
<!-- 1: Contains double quotes — use single quote wrapper -->
<p title='John "The Eagle" Okafor'>Player Profile</p>

<!-- 2: Contains apostrophe/single quote — use double quote wrapper -->
<p title="Nigeria's capital city is Abuja">Geography</p>

<!-- 3: Contains apostrophe — use double quote wrapper -->
<img src="chart.png" alt="Chart showing Africa's GDP growth from 2020 to 2025">

<!-- 4: Contains BOTH types — use single quotes outside (or escape characters, covered later) -->
<p title='He said: "It&apos;s a beautiful day in Lagos!"'>Quote</p>
```

> The `&apos;` in example 4 is an HTML **entity** — a special code for the apostrophe character. You will learn HTML entities in a later lesson. For now, the best approach when a value has both types of quotes is to use `&apos;` for the apostrophe.

---

### Challenge 5 — Build a Complete, Correct Attributes Showcase Page

**Task:** Build a single HTML page that demonstrates **every attribute from this lesson at least once**. The page should be a "Tech Tools" resource page.

**Requirements:** `lang`, `href`, `src`, `alt`, `width`, `height`, `style`, `title`

**Solution:**

```html
<!DOCTYPE html>
<html lang="en">
<body>

<h1 style="color:darkblue; text-align:center;">Essential Developer Tools</h1>

<p style="font-size:16px;" title="Last reviewed: April 2026">
  Below are some of the most useful tools for web developers at all levels.
</p>

<h2>Documentation &amp; Learning</h2>

<img src="https://www.w3schools.com/images/w3schools_logo_436_2.png"
     alt="W3Schools logo — free web development tutorials"
     width="150"
     height="48"
     style="border:1px solid #cccccc;">

<p>
  <a href="https://www.w3schools.com" title="Visit W3Schools for free HTML, CSS, and JavaScript tutorials">
    W3Schools
  </a>
  — the world's largest web development learning platform.
</p>

<h2>Code &amp; Version Control</h2>

<img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png"
     alt="GitHub logo — a circle with a cat silhouette inside"
     width="80"
     height="80">

<p>
  <a href="https://www.github.com" title="GitHub: host your code and collaborate with developers worldwide">
    GitHub
  </a>
  — store, share, and collaborate on code projects.
</p>

<h2>Community &amp; Support</h2>

<p>
  <a href="https://stackoverflow.com"
     title="Stack Overflow: ask programming questions and get answers from experts">
    Stack Overflow
  </a>
  — the largest Q&amp;A community for developers.
</p>

</body>
</html>
```

> The `&amp;` you see above is the HTML entity for the `&` character. Because `&` has a special meaning in HTML, you must write it as `&amp;` to display it literally. You will learn this fully in the HTML Entities lesson.

**Expected output:**

```
         Essential Developer Tools        ← centred, dark blue

Below are some of the most useful tools...    ← normal text with tooltip on hover

Documentation & Learning

[W3Schools logo]

W3Schools — the world's largest web development learning platform.

Code & Version Control

[GitHub logo]

GitHub — store, share, and collaborate on code projects.

Community & Support

Stack Overflow — the largest Q&A community for developers.
```

---

## Mini Project — Build a Professional Team Profile Page

Combine every concept from Lessons 2, 3, and 4 into one polished, complete, professionally structured team profile page.

---

### Project Overview

**Project name:** Our Team  
**Goal:** A multi-section team profile page using all key attributes from this lesson alongside correct document structure and element nesting from previous lessons.

---

### Stage 1 — Skeleton with Language

```html
<!DOCTYPE html>
<html lang="en-NG">
<body>

<!-- Content coming in next stages -->

</body>
</html>
```

**Milestone:** Open in browser → blank page, no errors.

---

### Stage 2 — Page Header with Inline Styling

```html
<h1 style="color:darkblue; text-align:center; font-family:Arial;">
  Meet Our Team
</h1>

<p style="text-align:center; color:grey; font-size:15px;"
   title="Updated April 2026">
  We are a passionate team of developers, designers, and strategists based in Lagos, Nigeria.
</p>
```

---

### Stage 3 — Team Member Cards (Headings, Images, Links, Attributes)

```html
<!-- Team Member 1 -->
<h2 style="color:darkgreen;">Amara Okafor — Lead Developer</h2>

<img src="https://via.placeholder.com/150x150.png?text=Amara"
     alt="Amara Okafor, Lead Developer, smiling at the camera"
     width="150"
     height="150"
     style="border-radius:50%; border:3px solid darkgreen;">

<p>Amara specialises in front-end development and has 5 years of experience building web applications.</p>

<p>
  <a href="https://www.linkedin.com"
     title="View Amara's LinkedIn profile">
    Connect on LinkedIn
  </a>
</p>

<!-- Team Member 2 -->
<h2 style="color:darkblue;">Chidi Eze — UI/UX Designer</h2>

<img src="https://via.placeholder.com/150x150.png?text=Chidi"
     alt="Chidi Eze, UI/UX Designer, professional headshot"
     width="150"
     height="150"
     style="border-radius:50%; border:3px solid darkblue;">

<p>Chidi creates intuitive, beautiful user interfaces with a focus on accessibility and mobile-first design.</p>

<p>
  <a href="https://www.behance.net"
     title="View Chidi's design portfolio on Behance">
    View Portfolio
  </a>
</p>

<!-- Team Member 3 -->
<h2 style="color:maroon;">Ngozi Adeyemi — Project Manager</h2>

<img src="https://via.placeholder.com/150x150.png?text=Ngozi"
     alt="Ngozi Adeyemi, Project Manager, in a professional setting"
     width="150"
     height="150"
     style="border-radius:50%; border:3px solid maroon;">

<p>Ngozi leads project planning and delivery, ensuring every product ships on time and exceeds client expectations.</p>

<p>
  <a href="mailto:ngozi@example.com"
     title="Send Ngozi an email directly">
    Email Ngozi
  </a>
</p>
```

---

### Stage 4 — Final Complete Page

Assemble all stages together and open the file in your browser. Your finished page should display:
- A centred dark-blue page title
- A grey subtitle with a tooltip
- Three team member sections, each with a circular image, styled heading, description paragraph, and a styled link
- All attributes in lowercase with quoted values
- `lang="en-NG"` on the `<html>` tag

---

### Stage 5 — Attribute Audit

Go through your completed page and audit every single attribute:

- [ ] Is every attribute name in lowercase?
- [ ] Is every attribute value in double quotes?
- [ ] Does every `<img>` have `src`, `alt`, `width`, and `height`?
- [ ] Is the `alt` text on each image descriptive and specific?
- [ ] Does each `<a>` have a complete `href` with `https://` (or `mailto:`)?
- [ ] Does the `<html>` tag have `lang="en-NG"`?
- [ ] Does every `style` attribute value end each CSS property with a semicolon?

---

### Stage 6 — Reflection Questions

1. Why did you add `lang="en-NG"` to the `<html>` tag rather than the `<body>` tag?
2. The circular image borders are achieved with `style="border-radius:50%;"`. What do you think `50%` does to a square image?
3. If you gave the same `alt` text to all three team member photos (e.g., `alt="Team member photo"`), what problems would that cause?
4. Why is it better to use `src="images/amara.jpg"` (relative) rather than `src="https://mysite.com/images/amara.jpg"` (absolute) for images on your own site?
5. On the `mailto:` link — what happens on a mobile device when you click a `mailto:` link?

---

## Common Beginner Mistakes — Full Summary for This Lesson

**Syntax Mistakes:**
- Putting attributes in the **closing tag**: `</a href="#">` — never do this
- Forgetting the `=` between name and value: `<img src"photo.jpg">` — always include `=`
- Using spaces around `=`: `<a href = "url">` — no spaces around the equals sign
- Writing attribute names in uppercase: `SRC`, `ALT`, `HREF` — always lowercase

**Quoting Mistakes:**
- No quotes on values with spaces: `alt=A blue car` — always quote
- Using no quotes at all: `href=https://google.com` — always quote
- Starting with double but ending with single: `alt="My photo'` — must use the same quote type
- Using double quotes inside double-quoted values: `title="John "Big" Smith"` — use single quotes outside

**`href` Mistakes:**
- Missing `https://`: `href="www.google.com"` — browser looks for a local file named `www.google.com`
- Putting the URL as content instead of as a value: `<a>https://google.com</a>` — no `href` means no navigation

**`src` Mistakes:**
- Wrong relative path: `src="photo.jpg"` when the image is actually in `src="images/photo.jpg"`
- Using an absolute URL for your own site's images: causes domain-change breakage
- Linking to external images without permission (copyright violation)

**`alt` Mistakes:**
- Missing `alt` entirely — always include it
- Vague `alt` text: `alt="image"` — be specific and descriptive
- Starting with "Image of": `alt="Image of a cat"` — screen readers already announce it is an image

**`lang` Mistakes:**
- Forgetting `lang` entirely on `<html>` — always include it
- Using the wrong code: `lang="english"` instead of `lang="en"` — codes are standardised
- Putting `lang` on `<body>` instead of `<html>` — it belongs on `<html>`

**`style` Mistakes:**
- Missing the colon between property and value: `style="colorred"` — should be `style="color:red;"`
- Missing the semicolons between multiple properties: `style="color:red font-size:16px"` — needs `;` between them

---

## Reflection Questions

1. In your own words, what is an HTML attribute? What problem does it solve?
2. What is the difference between `src` and `href`? On which elements does each appear?
3. You have an image at `mysite.com/gallery/wedding.jpg`. Your HTML file is at `mysite.com/index.html`. What relative URL would you use in the `src` attribute?
4. You have an image at the same location, but your HTML file is at `mysite.com/blog/post.html`. Now what relative URL would you use?
5. Explain three different reasons why the `alt` attribute matters. Which reason do you think is most important and why?
6. A colleague argues: "I never bother with the `lang` attribute — the page looks the same without it." How would you respond?
7. What is the difference between the `title` attribute and the `alt` attribute? When would you use both on the same element?
8. What quote style would you use for this value — and why? `title=He said: "Hello there, it's great to see you!"`

---

## Lesson Completion Checklist

- [ ] I can define an HTML attribute and explain the `name="value"` syntax
- [ ] I know that attributes go only in the opening tag, never the closing tag
- [ ] I can use `href` correctly on `<a>` tags with a full URL
- [ ] I can use `src` correctly on `<img>` tags with both relative and absolute URLs
- [ ] I understand the difference between absolute and relative URLs and when to use each
- [ ] I can use `width` and `height` on images and understand why they matter for layout
- [ ] I understand why `alt` is required, what it does, and how to write good alt text
- [ ] I can use the `style` attribute to apply inline CSS colour and font properties
- [ ] I know what `lang` does, where it goes, and how to write language codes
- [ ] I know what the `title` attribute does and when it is useful
- [ ] I know that all attribute names must be lowercase
- [ ] I know that all attribute values must always be quoted
- [ ] I know when to use double quotes vs single quotes
- [ ] I completed all four guided exercises
- [ ] I completed all five code challenges
- [ ] I built the team profile mini-project
- [ ] I answered all eight reflection questions

---

## Lesson Summary

Lesson 4 gave you complete mastery over **HTML attributes** — the tools that control how every element looks and behaves.

**What an attribute is:** Extra information in the opening tag, always written as `name="value"`. Multiple attributes can be added to one tag, separated by spaces.

**The eight key attributes:**

| Attribute | Purpose |
|-----------|---------|
| `href` | Destination URL for links |
| `src` | Image file path or URL |
| `width` / `height` | Image dimensions in pixels |
| `alt` | Image description for accessibility and fallback |
| `style` | Inline CSS visual styling |
| `lang` | Page language (on `<html>` only) |
| `title` | Tooltip information on hover |

**Absolute vs Relative URLs:** Absolute URLs are full web addresses (with `https://`). Relative URLs describe paths relative to your own site. Use relative URLs for your own assets.

**Quoting rules:** Always quote attribute values. Use double quotes by default. Use single quotes when the value itself contains double quotes.

**Case rule:** All attribute names must be written in lowercase.

> **Coming up in Lesson 5:** You will study **HTML Headings** in depth — their six levels, why they matter for accessibility and SEO, how search engines read them, default sizes, and how to control them properly using `style`.

---

*Sources: W3Schools HTML Attributes (https://www.w3schools.com/html/html_attributes.asp) and HTML Attributes Code Challenges (https://www.w3schools.com/html/html_challenges_attributes.asp)*

> **Note:** The links provided for this lesson were identical to Lesson 3. The correct Lesson 4 source pages (HTML Attributes) were automatically loaded to maintain the curriculum sequence.
