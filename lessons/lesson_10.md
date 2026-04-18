---
render_with_liquid: false
title: "HTML Comments – Lesson 10"
nav_order: 10
---

# Lesson 10 — HTML Comments

---

## Lesson Introduction

Welcome to Lesson 10! 🎉

You have already learned how to write headings, paragraphs, styles, formatting,
quotations, and more. Now you are going to learn about something that might seem
small but is **incredibly useful** in real web development work:

> **HTML Comments** — secret notes you leave inside your code that the browser
> completely ignores and never shows to the visitor.

Think of comments like sticky notes written directly on the blueprint of a
building. The architect (you) can see the notes and understand what each part
means, but the people who visit the building never see those notes at all.

By the end of this lesson you will be able to:

- Write a basic HTML comment
- Add helpful notes and reminders inside your code
- Temporarily hide content without deleting it
- Use comments to help find and fix errors (called "debugging")
- Hide a small piece of content that is in the middle of a line

---

## Prerequisite Concepts

Before we dive in, let us quickly review two things you already know, because
they connect directly to this lesson.

### What Is an HTML Tag?

An HTML tag is a special instruction wrapped inside angle brackets `< >`.
Most tags come in pairs — an **opening tag** and a **closing tag**.

```html
<p>This is a paragraph.</p>
```

- `<p>` → opening tag (tells the browser "start a paragraph here")
- `This is a paragraph.` → the content the visitor sees
- `</p>` → closing tag (tells the browser "end the paragraph here")

### What Does the Browser Do?

When you open an HTML file in a browser (like Chrome, Firefox, or Edge), the
browser reads your HTML code from top to bottom and **renders** it — meaning
it converts your code into a visible web page.

The browser only shows content that is meant to be displayed. Any code or
instructions that are not meant to be shown are **ignored**.

---

## Conceptual Understanding

### What Is an HTML Comment?

An HTML comment is a special piece of text you add to your HTML code that:

- **You can read** when you look at the source code
- **The browser ignores completely** — it never shows up on the web page

**Real-life analogy:**
Imagine you are writing a recipe. You might write the recipe steps for the
cook, but also scribble a small pencil note saying "Remember: Aunty Janet is
allergic to nuts." That pencil note is only for you. The guests at dinner
never see it. HTML comments work exactly the same way.

---

### The Comment Syntax — How to Write It

The comment tag in HTML looks like this:

```html
<!-- Write your comment here -->
```

Let us break this down, character by character:

| Part | What it means |
|------|--------------|
| `<` | Opens the tag, just like all HTML tags |
| `!` | Special signal that says "this is NOT a regular tag" |
| `--` | Two dashes that mark the beginning of the comment content |
| ` Write your comment here ` | The comment text (only you can see this) |
| `--` | Two dashes that mark the END of the comment |
| `>` | Closes the tag |

> ⚠️ **Very Important:** Notice that the **opening** part is `<!--` (with an
> exclamation mark `!`), but the **closing** part is `-->` (no exclamation mark).
> Beginners often forget this. The `!` only appears at the start, never at the end.

---

### The Golden Rule of Comments

> **Comments are NOT displayed by the browser.**

No matter what you write inside `<!-- ... -->`, it will NEVER appear on the
visible web page. Only someone who opens your HTML source code will be able
to read it.

---

## Simple Standalone Examples

### Example 1 — Your Very First Comment

```html
<!DOCTYPE html>
<html>
<body>

<!-- This is a comment -->

<p>This is a paragraph.</p>

<!-- Remember to add more information here -->

</body>
</html>
```

**What the browser shows on the page:**

```
This is a paragraph.
```

**What happened?** The browser found two comments. It read them and immediately
skipped over them. They were never displayed. Only the `<p>` paragraph was shown.

> 💡 **Think about it:** Why is the second comment useful? It is a reminder note
> left by the developer (you!) to go back and add more content later.

---

### Example 2 — A Second Look at Comments

Let us try adding a comment ABOVE a heading too, to show that comments can go
anywhere in the code:

```html
<!DOCTYPE html>
<html>
<body>

<!-- Page header section starts here -->
<h1>Welcome to My Website</h1>

<!-- Main content below -->
<p>This is my first web page.</p>

</body>
</html>
```

**What the browser shows on the page:**

```
Welcome to My Website
This is my first web page.
```

The comments acted as invisible section labels for the developer, but the
visitor sees absolutely nothing from those comments.

---

## The Four Ways to Use HTML Comments

Now let us go through all four major uses of HTML comments one by one.

---

### Use 1 — Adding Notes and Reminders

This is the most basic and common use. You add plain text notes inside your
code to explain what a section does or to leave a reminder.

**Why is this useful?**

Imagine you built a website six months ago. You come back to update it, but you
have completely forgotten what each part of the code does. Comments are your
personal notes that explain it to your future self — and to any other developer
who reads your code.

#### Example — Explaining Sections

```html
<!DOCTYPE html>
<html>
<body>

<!-- Navigation menu -->
<p>Home | About | Contact</p>

<!-- Welcome message for new visitors -->
<h1>Hello and Welcome!</h1>

<!-- Footer with copyright info -->
<p>Copyright 2025 My Website</p>

</body>
</html>
```

**What the browser shows:**

```
Home | About | Contact
Hello and Welcome!
Copyright 2025 My Website
```

The comments act like section labels in a filing cabinet. The developer sees
them. The visitor does not.

---

#### Example — Leaving Yourself a Reminder

```html
<!DOCTYPE html>
<html>
<body>

<h2>Our Team</h2>

<p>John Smith - Lead Developer</p>

<!-- TODO: Add Sarah's bio here when she sends it -->

<p>David Brown - Designer</p>

</body>
</html>
```

**What the browser shows:**

```
Our Team
John Smith - Lead Developer
David Brown - Designer
```

The "TODO" note is a very common developer habit — leaving yourself a reminder
of something that still needs to be done.

---

### Use 2 — Hiding Content Temporarily

Sometimes you want to **hide** some HTML temporarily — maybe you do not want
it on the page right now, but you do not want to delete it either because you
might need it again soon.

You can wrap any HTML code in comment tags and it instantly disappears from the
page.

> 💡 **Real-world analogy:** Think of it like crossing out a sentence in pencil
> in a draft. The sentence is still there, you can still read it, but it does not
> count as part of the final text.

#### Example — Hiding a Single Element

```html
<!DOCTYPE html>
<html>
<body>

<p>This is a paragraph.</p>

<!-- <p>This is another paragraph</p> -->

<p>This is a paragraph too.</p>

</body>
</html>
```

**What the browser shows:**

```
This is a paragraph.
This is a paragraph too.
```

The middle paragraph is completely hidden. It still exists in your code, but
the browser skips it entirely.

> 🤔 **Think about it:** What happens if you remove the comment tags from around
> the middle paragraph? Try it and see!

---

#### Example — Hiding Multiple Lines of Code

Comments are not limited to a single line. Everything between `<!--` and `-->`
is hidden, even if it spans many lines.

```html
<!DOCTYPE html>
<html>
<body>

<p>This is a paragraph.</p>

<!--
<p>Look at this cool image:</p>
<img border="0" src="pic_trulli.jpg" alt="Trulli">
-->

<p>This is a paragraph too.</p>

</body>
</html>
```

**What the browser shows:**

```
This is a paragraph.
This is a paragraph too.
```

Both the paragraph AND the image inside the comment are completely hidden.
The browser sees the opening `<!--` and immediately starts ignoring everything
until it finds the closing `-->`.

> 💡 **Tip:** This technique of hiding multiple lines is extremely common when
> building websites. Developers often temporarily hide entire sections while
> they are working on something else.

---

### Use 3 — Debugging (Finding Errors in Your Code)

**What is debugging?**

Debugging means finding and fixing mistakes in your code. The word "bug" is a
programmer's slang word for an error or problem.

**How do comments help with debugging?**

Imagine your page is not displaying correctly. Something looks wrong, but you
are not sure which part of the code is causing the problem. You can use comments
to **switch off** sections of code one by one, until you find the section that
is causing the issue.

#### Example — Commenting Out Code to Find a Bug

Suppose you have this page with three paragraphs and something is wrong:

```html
<!DOCTYPE html>
<html>
<body>

<p>Paragraph 1 - This is fine.</p>
<p>Paragraph 2 - This is fine.</p>
<p>Paragraph 3 - This might have a problem.</p>

</body>
</html>
```

You suspect Paragraph 3 might be causing issues. You can **comment it out** to
test:

```html
<!DOCTYPE html>
<html>
<body>

<p>Paragraph 1 - This is fine.</p>
<p>Paragraph 2 - This is fine.</p>
<!-- <p>Paragraph 3 - This might have a problem.</p> -->

</body>
</html>
```

**What the browser shows:**

```
Paragraph 1 - This is fine.
Paragraph 2 - This is fine.
```

If the problem disappears now, you know Paragraph 3 was the cause. You then
go and fix Paragraph 3 without losing it — because it is still in your code,
just commented out.

---

### Use 4 — Hiding Inline Content

So far, all our comments have been on their own line. But comments can also
be placed **in the middle of a line**, hiding just a small piece of text.

This is called **inline commenting**.

#### Example — Hiding Part of a Paragraph

```html
<!DOCTYPE html>
<html>
<body>

<p>This <!-- great text --> is a paragraph.</p>

</body>
</html>
```

**What the browser shows:**

```
This  is a paragraph.
```

The words "great text" were hidden right in the middle of the sentence. The
browser only shows "This" and "is a paragraph." as if the comment was never
there.

> 🤔 **Think about it:** Why might a developer want to hide a word or phrase
> in the middle of a line rather than on its own line? Can you think of a
> situation where this would be useful?

---

#### Second Example — Hiding a Word Mid-Sentence

```html
<!DOCTYPE html>
<html>
<body>

<p>My favourite <!-- old --> colour is blue.</p>

</body>
</html>
```

**What the browser shows:**

```
My favourite  colour is blue.
```

The word "old" was hidden. Maybe the developer wrote "old" first, then decided
to remove the word temporarily without deleting it.

---

## Guided Practice Exercises

Let us now practise each concept step by step with clear exercises.

---

### 🟡 Exercise 1 — Write Your First Comment

**Objective:** Add a comment to an HTML page.

**Scenario:** You are building a personal web page. You want to leave yourself
a note reminding you to write a proper introduction later.

**Starting code:**

```html
<!DOCTYPE html>
<html>
<body>

<h1>My Personal Page</h1>

<p>Hello, my name is Alex.</p>

</body>
</html>
```

**Your task:**
Add a comment ABOVE the `<h1>` tag that says: `Page header starts here`

**Expected Result:**
Your page should still show exactly:
```
My Personal Page
Hello, my name is Alex.
```
And your source code should now contain the comment `<!-- Page header starts here -->`.

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>

<!-- Page header starts here -->
<h1>My Personal Page</h1>

<p>Hello, my name is Alex.</p>

</body>
</html>
```

**Output on page:**
```
My Personal Page
Hello, my name is Alex.
```

✅ The comment is invisible on the page, but it is there in your code!

---

### 🟡 Exercise 2 — Hide a Paragraph Temporarily

**Objective:** Use a comment to hide an HTML element.

**Scenario:** You are working on a school project website. You have written
three paragraphs but the second one is not ready yet. You want to hide it
without deleting it.

**Starting code:**

```html
<!DOCTYPE html>
<html>
<body>

<p>Chapter 1: The Journey Begins</p>
<p>Chapter 2: The Big Discovery (COMING SOON - not ready yet)</p>
<p>Chapter 3: The Happy Ending</p>

</body>
</html>
```

**Your task:**
Comment out the second paragraph so it does not appear on the page.

**Expected output:**
```
Chapter 1: The Journey Begins
Chapter 3: The Happy Ending
```

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>

<p>Chapter 1: The Journey Begins</p>
<!-- <p>Chapter 2: The Big Discovery (COMING SOON - not ready yet)</p> -->
<p>Chapter 3: The Happy Ending</p>

</body>
</html>
```

**Output on page:**
```
Chapter 1: The Journey Begins
Chapter 3: The Happy Ending
```

✅ Chapter 2 is safely stored in the code but hidden from visitors!

---

### 🟡 Exercise 3 — Hide Multiple Lines

**Objective:** Use a multi-line comment to hide an entire block of HTML.

**Scenario:** You are building a product page for a shop. There is a special
promotion section that should be hidden until the sale begins next week.

**Starting code:**

```html
<!DOCTYPE html>
<html>
<body>

<h1>Welcome to TechStore</h1>
<p>Quality products at great prices.</p>

<h2>FLASH SALE THIS WEEKEND!</h2>
<p>Get 50% off all laptops!</p>
<p>Limited stock available. Order now!</p>

<p>Contact us at info@techstore.com</p>

</body>
</html>
```

**Your task:**
Hide the entire flash sale section (the `<h2>` and both `<p>` tags about the
sale) using a multi-line comment.

**Expected output:**
```
Welcome to TechStore
Quality products at great prices.
Contact us at info@techstore.com
```

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>

<h1>Welcome to TechStore</h1>
<p>Quality products at great prices.</p>

<!--
<h2>FLASH SALE THIS WEEKEND!</h2>
<p>Get 50% off all laptops!</p>
<p>Limited stock available. Order now!</p>
-->

<p>Contact us at info@techstore.com</p>

</body>
</html>
```

**Output on page:**
```
Welcome to TechStore
Quality products at great prices.
Contact us at info@techstore.com
```

✅ The entire sale section is hidden but ready to be "uncommented" when the
sale starts!

---

### 🟡 Exercise 4 — Inline Comment

**Objective:** Hide a word inside a sentence using an inline comment.

**Scenario:** You wrote a product description but you want to temporarily
hide the word "discounted" while you decide whether to use it.

**Starting code:**

```html
<!DOCTYPE html>
<html>
<body>

<p>Our discounted laptop bags are available now.</p>

</body>
</html>
```

**Your task:**
Use an inline comment to hide the word "discounted" from the sentence.

**Expected output:**
```
Our  laptop bags are available now.
```

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>

<p>Our <!-- discounted --> laptop bags are available now.</p>

</body>
</html>
```

**Output on page:**
```
Our  laptop bags are available now.
```

✅ The word "discounted" is hidden but still in the code for you to restore
if needed!

---

### 🟡 Exercise 5 — Code Challenge Style Practice

This exercise is modelled on the W3Schools HTML Comments Code Challenge.

**Objective:** Fix and complete commented HTML code.

**Scenario:** A fellow student wrote this HTML page but accidentally left out
some important comment tags. Your job is to add the correct comment tags.

**Starting code (with problems):**

```html
<!DOCTYPE html>
<html>
<body>

This is a note to myself about this section

<p>Welcome to my blog.</p>

<p>My hobbies are reading, coding, and cooking.</p>

This paragraph below is hidden until I'm ready:
<p>Subscribe to my newsletter for updates.</p>

</body>
</html>
```

**Your task:**
1. Wrap `This is a note to myself about this section` in proper comment tags.
2. Wrap `This paragraph below is hidden until I'm ready:` and the subscription
   paragraph in a multi-line comment.

**Expected output:**
```
Welcome to my blog.
My hobbies are reading, coding, and cooking.
```

**Solution:**

```html
<!DOCTYPE html>
<html>
<body>

<!-- This is a note to myself about this section -->

<p>Welcome to my blog.</p>

<p>My hobbies are reading, coding, and cooking.</p>

<!--
This paragraph below is hidden until I'm ready:
<p>Subscribe to my newsletter for updates.</p>
-->

</body>
</html>
```

**Output on page:**
```
Welcome to my blog.
My hobbies are reading, coding, and cooking.
```

✅ Excellent! You have now practised all four major types of HTML comments.

---

## Mini Project — Building a Blog Draft Page with Comments

Now let us combine everything you have learned into a realistic mini-project.

### Project: "My Blog Draft Page"

You are going to build a draft version of a blog page. You will use comments
to label sections, hide content that is not ready, and leave yourself useful
development reminders.

---

### Stage 1 — Setup: Basic Page Structure with Comment Labels

**Goal:** Create the page structure and use comments to label each section.

```html
<!DOCTYPE html>
<html>
<body>

<!-- ===== HEADER SECTION ===== -->
<h1>My Personal Blog</h1>
<p>Thoughts, ideas, and adventures.</p>

<!-- ===== MAIN ARTICLE SECTION ===== -->
<h2>My First Blog Post</h2>
<p>Today I started learning HTML. It is easier than I expected!</p>

<!-- ===== FOOTER SECTION ===== -->
<p>Written by: Alex | April 2025</p>

</body>
</html>
```

**Milestone Output:**
```
My Personal Blog
Thoughts, ideas, and adventures.
My First Blog Post
Today I started learning HTML. It is easier than I expected!
Written by: Alex | April 2025
```

✅ Your page is structured and labelled with invisible section comments!

---

### Stage 2 — Core Logic: Hiding Incomplete Content

**Goal:** Add more blog posts but hide the ones that are not finished yet.

```html
<!DOCTYPE html>
<html>
<body>

<!-- ===== HEADER SECTION ===== -->
<h1>My Personal Blog</h1>
<p>Thoughts, ideas, and adventures.</p>

<!-- ===== POST 1: PUBLISHED ===== -->
<h2>Post 1: My First Day Learning HTML</h2>
<p>Today I started learning HTML. It is easier than I expected!</p>

<!-- ===== POST 2: HIDDEN - STILL DRAFTING ===== -->
<!--
<h2>Post 2: Learning About CSS</h2>
<p>CSS controls how your page looks. I will write more when I understand it better.</p>
-->

<!-- ===== POST 3: HIDDEN - NOT STARTED ===== -->
<!--
<h2>Post 3: My JavaScript Journey</h2>
<p>TODO: Write this post after I finish the JavaScript lessons.</p>
-->

<!-- ===== FOOTER SECTION ===== -->
<p>Written by: Alex | April 2025</p>

</body>
</html>
```

**Milestone Output:**
```
My Personal Blog
Thoughts, ideas, and adventures.
Post 1: My First Day Learning HTML
Today I started learning HTML. It is easier than I expected!
Written by: Alex | April 2025
```

✅ Posts 2 and 3 are ready in the code but invisible on the page!

---

### Stage 3 — Enhancement: Adding Reminders and Inline Notes

**Goal:** Add development reminder comments and use inline commenting to hide
draft phrases.

```html
<!DOCTYPE html>
<html>
<body>

<!-- ===== HEADER SECTION ===== -->
<!-- TODO: Add a logo image here once it is designed -->
<h1>My Personal Blog</h1>
<p>Thoughts, ideas, and <!-- very very --> adventures.</p>

<!-- ===== POST 1: PUBLISHED ===== -->
<h2>Post 1: My First Day Learning HTML</h2>
<p>Today I started learning HTML. It is <!-- surprisingly --> easier than I expected!</p>

<!-- ===== POST 2: HIDDEN - STILL DRAFTING ===== -->
<!--
<h2>Post 2: Learning About CSS</h2>
<p>CSS controls how your page looks. I will write more when I understand it better.</p>
-->

<!-- ===== POST 3: HIDDEN - NOT STARTED ===== -->
<!--
<h2>Post 3: My JavaScript Journey</h2>
<p>TODO: Write this post after I finish the JavaScript lessons.</p>
-->

<!-- ===== FOOTER SECTION ===== -->
<!-- TODO: Add social media links below -->
<p>Written by: Alex | April 2025</p>

</body>
</html>
```

**Milestone Output:**
```
My Personal Blog
Thoughts, ideas, and  adventures.
Post 1: My First Day Learning HTML
Today I started learning HTML. It is  easier than I expected!
Written by: Alex | April 2025
```

✅ Notice how "very very" and "surprisingly" are hidden inline, while the
TODO reminders are invisible labels for your future work.

---

### Stage 4 — Final Output

Your complete blog draft page uses EVERY type of HTML comment:

- ✅ Section-labelling comments
- ✅ Multi-line hidden content (unpublished blog posts)
- ✅ Reminder / TODO comments
- ✅ Inline comments hiding draft words

**Reflection Questions for Stage 4:**

1. How would you "publish" Post 2? What would you need to change in the code?
2. Why is it better to comment out incomplete content rather than delete it?
3. If someone visits your website, can they see your hidden comments? Can they
   ever find them? (Hint: think about "View Source" in a browser!)

> 🔍 **Advanced extension:** Try right-clicking on any web page in your browser
> and choosing "View Page Source." You might discover that real professional
> websites also use comments in their HTML code!

---

## Common Beginner Mistakes

### ❌ Mistake 1 — Putting `!` in the Closing Tag

**Wrong:**
```html
<!-- This is a comment --!>
```

**Right:**
```html
<!-- This is a comment -->
```

**Why:** The exclamation mark `!` only belongs in the OPENING part `<!--`.
The closing part is simply `-->` with no exclamation mark.

---

### ❌ Mistake 2 — Forgetting Both Dashes

**Wrong:**
```html
<! This is a comment >
```

**Right:**
```html
<!-- This is a comment -->
```

**Why:** The `<!--` opening requires two dashes after the `!`. Without both
dashes, the browser will not recognise it as a comment and may display it as
broken code.

---

### ❌ Mistake 3 — Only Closing With One Dash

**Wrong:**
```html
<!-- This is a comment ->
```

**Right:**
```html
<!-- This is a comment -->
```

**Why:** The closing marker needs **two** dashes: `-->`. One dash is not enough.

---

### ❌ Mistake 4 — Trying to Nest Comments Inside Each Other

**Wrong:**
```html
<!-- Outer comment <!-- inner comment --> -->
```

**Why it fails:** HTML does not support nested (comments inside comments). As
soon as the browser finds the first `-->`, it ends the comment. Everything
after that is treated as normal HTML again, which causes unexpected problems.

**Right approach:** Keep your comments simple and non-nested.

---

### ❌ Mistake 5 — Thinking Comments Are Truly Invisible to Everyone

This is a very common misunderstanding! Comments are invisible on the
**rendered page**, but they are NOT secret. Anyone who right-clicks on your
web page and chooses "View Page Source" will be able to read ALL your comments.

**Important rule:** Never put passwords, private information, or sensitive
business details inside HTML comments. They are not secure.

---

### ❌ Mistake 6 — Forgetting to Close a Multi-Line Comment

**Wrong:**
```html
<p>This is visible.</p>

<!--
<p>This should be hidden.</p>

<p>This is also visible... or is it?</p>
```

**Why it fails:** When you forget the closing `-->`, the browser treats
everything from the opening `<!--` onwards as a comment, potentially hiding
large sections of your page accidentally.

**Right:**
```html
<p>This is visible.</p>

<!--
<p>This should be hidden.</p>
-->

<p>This is also visible.</p>
```

---

## Reflection Questions

Take a moment to think through these questions. They will help you understand
the lesson deeply.

1. **What is the main purpose of HTML comments?**
   Think about: Are they for the visitor or for the developer?

2. **Name three real-world situations where hiding content with a comment is
   more useful than deleting it.**

3. **You are working in a team of three developers on the same HTML file.
   How could comments help everyone understand the code better?**

4. **A friend says: "I put my secret password in an HTML comment so nobody
   will find it." What would you tell them?**

5. **Look at the comment syntax: `<!-- comment -->`. Which part is different
   from normal HTML tags, and why do you think HTML was designed that way?**

6. **If you comment out a paragraph that contains a heading and an image,
   what happens to both elements?**

7. **What does the term "debugging" mean, and how do HTML comments help with
   the debugging process?**

---

## Completion Checklist

Before moving to the next lesson, confirm that you can do all of the following:

- [ ] Write a basic HTML comment using `<!-- -->`
- [ ] Explain what an HTML comment is and why it is used
- [ ] Add a comment as a note or reminder in HTML code
- [ ] Comment out a single HTML element to hide it temporarily
- [ ] Comment out multiple lines of HTML to hide a block of content
- [ ] Use an inline comment to hide content in the middle of a line
- [ ] Explain the difference between the opening `<!--` and closing `-->`
- [ ] List at least three common beginner mistakes with comments
- [ ] Explain why HTML comments are NOT a safe place for sensitive information
- [ ] Describe how comments help with debugging HTML code
- [ ] Complete the mini-project blog draft page with all four comment types

---

## Lesson Summary

HTML comments are a simple but powerful tool that every web developer uses
daily. Here is a quick recap of everything you learned:

**The comment syntax:**
```html
<!-- This is an HTML comment -->
```

**The four key uses of HTML comments:**

1. **Adding notes and reminders** — Document your code for yourself and others
2. **Hiding content temporarily** — Switch off code without deleting it
3. **Debugging** — Comment out sections to find and fix errors
4. **Inline commenting** — Hide a small piece of content mid-sentence

**The golden rules:**
- Comments are NEVER displayed on the visible page
- The opening tag is `<!--` (with `!` and two dashes)
- The closing tag is `-->` (just two dashes and `>`, no `!`)
- Multi-line comments hide everything between `<!--` and `-->`
- Comments are NOT secret — anyone can see them in View Source
- Never store passwords or sensitive data in HTML comments

**Real-world connection:**

In professional web development, comments are used to organise large HTML
files with thousands of lines of code. Team members leave comments to explain
complex sections, mark work-in-progress areas, and help new developers
understand the codebase quickly. Comments also play an important role in
front-end debugging, where developers comment out sections one by one to
isolate and fix problems.

---

> 🚀 **Up Next:** Lesson 11 — HTML Colors! You will learn how to apply
> beautiful colours to text, backgrounds, and borders using colour names,
> HEX codes, RGB values, and HSL values.
