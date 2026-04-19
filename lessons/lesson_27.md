---
render_with_liquid: false
title: "HTML Computer Code Elements"
nav_order: 27
---

# Lesson 27: HTML Computer Code Elements

---

## Lesson Introduction

Have you ever visited a website that shows programming instructions, keyboard shortcuts, or computer error messages — and they look different from normal text? They appear in a special font that resembles what you might see in a text editor or terminal. That special look is not an accident. HTML has a dedicated set of elements specifically designed to mark up **technical and computer-related content**.

In this lesson, you will learn five powerful HTML elements: `<kbd>`, `<samp>`, `<code>`, `<pre>`, and `<var>`. Together, they give you everything you need to properly communicate technical ideas on a web page — whether you're building a programming tutorial, a science textbook, a software manual, or a tech blog.

By the end of this lesson, you will be able to:

- Understand what each computer code element does and why it exists
- Use each element correctly in a real HTML page
- Combine elements to display multi-line code blocks cleanly
- Build a complete mini technical documentation page using all five elements

---

## Prerequisite Concepts

Before we dive in, let's quickly cover a few foundational ideas. If you already know these, treat this as a helpful reminder!

### What is an HTML Element?

An **HTML element** is a building block of a web page. It is written with an **opening tag**, some **content**, and a **closing tag**.

```html
<p>This is a paragraph.</p>
```

- `<p>` → opening tag (tells the browser "start a paragraph here")
- `This is a paragraph.` → the content the user will see
- `</p>` → closing tag (tells the browser "end the paragraph here")

### What is a Monospace Font?

A **monospace font** (also called a fixed-width font) is a font where every single letter takes up exactly the same amount of horizontal space. This is the font style used by most code editors, terminals, and command prompts.

For example, in a regular font:

```
iii   → narrow letters, takes less space
WWW   → wide letters, takes more space
```

In a monospace font:

```
iii   → every letter is the same width
WWW   → every letter is the same width
```

This makes code easier to read because columns line up neatly. When you use the HTML computer code elements in this lesson, the browser automatically switches to this monospace style.

### What is Inline vs Block Content?

- **Inline elements** sit inside a line of regular text — they don't force a new line. Examples: `<strong>`, `<em>`, `<code>`, `<kbd>`, `<var>`, `<samp>`.
- **Block elements** take up their own full row on the page. Examples: `<p>`, `<div>`, `<pre>`, `<h1>`.

Most of the elements in this lesson are **inline**, except `<pre>`, which is a **block** element. We'll explain each one in detail below.

---

## Conceptual Understanding

### Why Do These Elements Exist?

Think about a technology documentation website — like a setup guide for software. It might include:

- A keyboard shortcut like **Ctrl + S** (save the file)
- A terminal error message like **File not found**
- A snippet of actual code like `x = 5;`
- A variable name like *b* in a math formula

Without special HTML elements, all of these would look exactly the same as ordinary paragraph text. A reader would have no visual cue about what is a command, what is output, and what is a variable. That would be confusing!

HTML's computer code elements solve this problem by giving technical content its own distinctive look and semantic meaning. **Semantic** means that the element tells the browser (and search engines, and screen readers) *what kind of content this is*, not just *how it should look*.

---

## Part 1 — The `<kbd>` Element (Keyboard Input)

### What Is It?

The `<kbd>` element stands for **keyboard**. You use it to show text that the user is supposed to **type or press** on their keyboard. Think of it as a label that says: "Hey reader, press this key!"

### What It Looks Like

The browser renders `<kbd>` content in the **default monospace font** — the same kind of font you see in code editors.

### Simple Example

```html
<p>To save your file, press <kbd>Ctrl + S</kbd></p>
```

**Expected Output in the Browser:**

> To save your file, press `Ctrl + S`

The text `Ctrl + S` appears in a monospace font, visually distinct from the rest of the sentence.

### Another Example

```html
<p>To undo an action, press <kbd>Ctrl + Z</kbd></p>
<p>To copy selected text, press <kbd>Ctrl + C</kbd></p>
<p>To paste, press <kbd>Ctrl + V</kbd></p>
```

**Expected Output:**

> To undo an action, press `Ctrl + Z`
> To copy selected text, press `Ctrl + C`
> To paste, press `Ctrl + V`

### Why Use `<kbd>` Instead of Just Bold Text?

You could write:

```html
<p>Press <strong>Ctrl + S</strong> to save.</p>
```

But this would only make the text bold — it gives no information about *what kind* of content it is. Using `<kbd>` tells browsers, search engines, and assistive technologies (like screen readers for visually impaired users) that this is keyboard input. It carries **meaning**, not just style.

> 💡 **Analogy:** Think of `<kbd>` like a key cap on a physical keyboard — it looks distinct from surrounding text, just like a real key stands out from the desk it sits on.

### Real-World Use Cases

- Software tutorials: "Press `Enter` to confirm"
- Game documentation: "Use `WASD` to move your character"
- Spreadsheet guides: "Press `F2` to edit a cell"

---

## Part 2 — The `<samp>` Element (Sample Computer Output)

### What Is It?

The `<samp>` element stands for **sample**. You use it to show text that represents **output produced by a computer program** — like a message printed to the screen or an error from a terminal.

### The Key Difference from `<kbd>`

| Element | Represents |
|---------|-----------|
| `<kbd>` | What the **user types** (input going *in*) |
| `<samp>` | What the **computer displays** (output coming *out*) |

Think of it like a conversation: you speak (`<kbd>`), and the computer replies (`<samp>`).

### Simple Example

```html
<p>Message from my computer:</p>
<p><samp>File not found. Press F1 to continue</samp></p>
```

**Expected Output in the Browser:**

> Message from my computer:
>
> `File not found. Press F1 to continue`

The error message appears in monospace font, just like you'd see in a real terminal window.

### Another Example — A Login Attempt

```html
<p>After entering the wrong password, you might see:</p>
<p><samp>Access denied. Too many failed attempts. Try again in 30 seconds.</samp></p>
```

**Expected Output:**

> After entering the wrong password, you might see:
>
> `Access denied. Too many failed attempts. Try again in 30 seconds.`

### Real-World Use Cases

- Bug reports and technical support pages
- Command-line tutorials showing what appears after running a command
- System documentation showing expected program responses

---

## Part 3 — The `<code>` Element (Computer Code)

### What Is It?

The `<code>` element is used to mark up an actual piece of **computer code**. This could be a variable name, a function call, a command, or a short snippet from a programming language.

### Simple Example

```html
<p>In Python, you can print text using the <code>print()</code> function.</p>
```

**Expected Output:**

> In Python, you can print text using the `print()` function.

### Another Example — Inline Code in a Sentence

```html
<p>Set the variable with <code>x = 5;</code> and the result will be 5.</p>
```

**Expected Output:**

> Set the variable with `x = 5;` and the result will be 5.

### Multi-line Code Block with `<code>`

You can also put multiple lines of code inside `<code>`:

```html
<code>
x = 5;
y = 6;
z = x + y;
</code>
```

**Expected Output:**

> `x = 5; y = 6; z = x + y;`

Wait — notice something strange! The three lines collapsed into **one line**. The `<code>` element on its own **does NOT preserve line breaks or extra spaces**. This is a very important limitation to understand.

> 🤔 **Thinking Prompt:** What would happen if you added ten blank lines inside a `<code>` tag? They would all be collapsed and ignored. Why? Because HTML collapses whitespace by default.

To fix this, you need to combine `<code>` with another element — `<pre>`. We'll learn that next.

---

## Part 4 — The `<pre>` Element (Preformatted Text)

### What Is It?

The `<pre>` element stands for **preformatted**. It tells the browser: "Display this text *exactly* as I typed it — preserve every space, every blank line, every indent."

This is a **block-level** element, meaning it creates its own section on the page (like a paragraph does).

### Why Is It Important for Code?

When you write real code, spacing matters. Indentation, line breaks, and alignment communicate structure. Without `<pre>`, all of that formatting would be lost.

### The Right Pattern: `<pre>` + `<code>` Together

The professional and correct way to display a multi-line code block in HTML is to **wrap `<code>` inside `<pre>`**:

```html
<pre>
<code>
x = 5;
y = 6;
z = x + y;
</code>
</pre>
```

**Expected Output:**

```
x = 5;
y = 6;
z = x + y;
```

Now the three lines appear on separate lines, exactly as written!

### Simple `<pre>` Example (Without `<code>`)

`<pre>` can also be used on its own for ASCII art or any preformatted text:

```html
<pre>
Name:   Amara
Age:    22
Grade:  A+
</pre>
```

**Expected Output:**

```
Name:   Amara
Age:    22
Grade:  A+
```

The columns line up perfectly because the spaces are preserved!

### Another `<pre>` + `<code>` Example — Python Code

```html
<pre>
<code>
def greet(name):
    print("Hello, " + name)

greet("Amara")
</code>
</pre>
```

**Expected Output:**

```
def greet(name):
    print("Hello, " + name)

greet("Amara")
```

The indentation is preserved exactly, which is essential for Python where indentation controls code structure.

> 💡 **Analogy:** Think of `<pre>` like a photographer's "do not crop" instruction. It tells the browser, "Show every pixel exactly as it was. Don't rearrange anything."

### Real-World Use Cases

- Programming tutorial websites (showing code samples)
- Technical documentation
- Displaying terminal output with proper formatting
- Poetry or text art where spacing matters

---

## Part 5 — The `<var>` Element (Variables)

### What Is It?

The `<var>` element is used to mark up a **variable** — in programming, this is a named container that holds a value. In mathematics, it's a letter that represents an unknown or changing quantity.

By default, most browsers display `<var>` content in **italic** text.

### Why Use `<var>`?

It gives semantic meaning to variable names so that both readers and machines understand: "this word is a variable, not ordinary text."

### Simple Example — Math Context

```html
<p>The area of a rectangle is: <var>length</var> × <var>width</var></p>
```

**Expected Output:**

> The area of a rectangle is: *length* × *width*

Both variable names appear in italics, distinguishing them from the regular words.

### The W3Schools Example — Triangle Area

```html
<p>The area of a triangle is: 1/2 x <var>b</var> x <var>h</var>, 
where <var>b</var> is the base, and <var>h</var> is the vertical height.</p>
```

**Expected Output:**

> The area of a triangle is: 1/2 x *b* x *h*, where *b* is the base, and *h* is the vertical height.

### Another Example — Programming Context

```html
<p>Declare a variable: <code>var <var>score</var> = 100;</code></p>
```

**Expected Output:**

> Declare a variable: `var score = 100;`

Notice how `<code>` wraps the whole snippet (it's code), but `<var>` is used specifically around the variable name `score`.

### Real-World Use Cases

- Mathematics textbooks and STEM educational websites
- Programming documentation explaining what a variable does
- Physics or chemistry pages explaining formulas with variable components

---

## Combining All Five Elements

Now that you know each element separately, let's see how they work together in a realistic scenario: a simple troubleshooting guide.

```html
<h2>How to Check Your Python Version</h2>

<p>Open your terminal and type the following command:</p>
<p><kbd>python --version</kbd></p>

<p>Your computer should display something like:</p>
<p><samp>Python 3.11.2</samp></p>

<p>If you want to use this in a script, the relevant code is:</p>
<pre>
<code>
import sys
print(sys.version)
</code>
</pre>

<p>In this code, <var>sys</var> is a built-in module that contains 
system-specific information, and <code>sys.version</code> is 
the attribute that holds the version string.</p>
```

**Expected Rendered Output:**

---

**How to Check Your Python Version**

Open your terminal and type the following command:

`python --version`

Your computer should display something like:

`Python 3.11.2`

If you want to use this in a script, the relevant code is:

```
import sys
print(sys.version)
```

In this code, *sys* is a built-in module that contains system-specific information, and `sys.version` is the attribute that holds the version string.

---

Notice how each element plays its own clear role in that example. The overall result is professional, semantic, and easy to understand.

---

## Quick Reference: All Five Elements at a Glance

| Tag | Full Name | Purpose | Visual Style |
|-----|-----------|---------|-------------|
| `<kbd>` | Keyboard Input | Text the user types/presses | Monospace font |
| `<samp>` | Sample Output | Text the computer displays | Monospace font |
| `<code>` | Computer Code | A piece of actual code | Monospace font |
| `<pre>` | Preformatted Text | Preserves spaces and line breaks | Monospace font, block |
| `<var>` | Variable | A variable in code or math | Italic text |

---

## Guided Practice Exercises

### Exercise 1 — Keyboard Shortcut Guide

**Objective:** Use `<kbd>` to build a keyboard shortcut reference.

**Scenario:** You are creating a help page for a simple text editor. Users need to know the keyboard shortcuts.

**Steps:**

1. Create a new `.html` file.
2. Add a heading: "Keyboard Shortcuts"
3. Write three paragraphs, each describing one shortcut using `<kbd>`.

**Starter Code:**

```html
<!DOCTYPE html>
<html>
<body>

<h2>Keyboard Shortcuts</h2>

<p>To open a new document, press <kbd>Ctrl + N</kbd></p>
<p>To find text, press <kbd>Ctrl + F</kbd></p>
<p>To close the editor, press <kbd>Alt + F4</kbd></p>

</body>
</html>
```

**Expected Output:**

> **Keyboard Shortcuts**
>
> To open a new document, press `Ctrl + N`
> To find text, press `Ctrl + F`
> To close the editor, press `Alt + F4`

**Self-Check Questions:**
- Does each shortcut appear in a different font from the regular text?
- What would happen if you used `<strong>` instead of `<kbd>`?
- Can you add two more shortcuts to this guide?

**What-If Challenge:** What if the user is on a Mac? Change `Ctrl` to `Cmd` for Mac shortcuts.

---

### Exercise 2 — Program Output Display

**Objective:** Use `<samp>` to show error messages and program outputs.

**Scenario:** You are writing a troubleshooting page for a database application.

**Steps:**

1. Write a paragraph explaining the situation.
2. Show the error message using `<samp>`.
3. Add a second scenario with a success message.

**Starter Code:**

```html
<!DOCTYPE html>
<html>
<body>

<h2>Common Database Messages</h2>

<p>When the database cannot connect, you will see:</p>
<p><samp>ERROR 2002 (HY000): Can't connect to local MySQL server</samp></p>

<p>When the connection succeeds, you will see:</p>
<p><samp>Welcome to the MySQL monitor. Connection established.</samp></p>

</body>
</html>
```

**Expected Output:**

> **Common Database Messages**
>
> When the database cannot connect, you will see:
>
> `ERROR 2002 (HY000): Can't connect to local MySQL server`
>
> When the connection succeeds, you will see:
>
> `Welcome to the MySQL monitor. Connection established.`

**Self-Check Questions:**
- What is the visual difference between the `<samp>` text and the regular paragraph text?
- Could you use `<kbd>` instead of `<samp>` here? Why or why not?

---

### Exercise 3 — Code Block with Line Preservation

**Objective:** Use `<pre>` + `<code>` to display a properly formatted code snippet.

**Scenario:** You are writing a tutorial about JavaScript.

**Steps:**

1. Write a heading.
2. Write a brief explanation paragraph.
3. Place the code inside `<pre><code>...</code></pre>`.

**Starter Code:**

```html
<!DOCTYPE html>
<html>
<body>

<h2>Simple JavaScript Example</h2>

<p>This code calculates the sum of two numbers and prints the result:</p>

<pre>
<code>
let x = 10;
let y = 20;
let sum = x + y;
console.log("The sum is: " + sum);
</code>
</pre>

</body>
</html>
```

**Expected Output:**

> **Simple JavaScript Example**
>
> This code calculates the sum of two numbers and prints the result:
>
> ```
> let x = 10;
> let y = 20;
> let sum = x + y;
> console.log("The sum is: " + sum);
> ```

**Self-Check Questions:**
- What happens if you remove `<pre>` and only keep `<code>`? Try it!
- Are the line breaks preserved when you use just `<code>` without `<pre>`?

---

### Exercise 4 — Math Formula with Variables

**Objective:** Use `<var>` to mark up variables in a physics formula.

**Scenario:** You are building a science education page about Newton's Second Law of Motion.

**Steps:**

1. Write the formula as a paragraph using `<var>` for each variable.
2. Explain what each variable means.

**Starter Code:**

```html
<!DOCTYPE html>
<html>
<body>

<h2>Newton's Second Law of Motion</h2>

<p>The formula is: <var>F</var> = <var>m</var> × <var>a</var></p>

<p>Where:</p>
<p><var>F</var> is the force (in Newtons)</p>
<p><var>m</var> is the mass (in kilograms)</p>
<p><var>a</var> is the acceleration (in m/s²)</p>

</body>
</html>
```

**Expected Output:**

> **Newton's Second Law of Motion**
>
> The formula is: *F* = *m* × *a*
>
> Where:
> *F* is the force (in Newtons)
> *m* is the mass (in kilograms)
> *a* is the acceleration (in m/s²)

**Self-Check Questions:**
- Do the variable letters appear in italic?
- What is the visual and semantic difference between using `<var>` vs `<em>` for variable names?

---

### Exercise 5 — Challenge: Combining All Elements

**Objective:** Build a small HTML snippet that uses ALL five elements together.

**Scenario:** You're writing a quick-start guide for a command-line tool called "DataCalc".

```html
<!DOCTYPE html>
<html>
<body>

<h2>DataCalc Quick Start Guide</h2>

<p>To launch DataCalc, open your terminal and press <kbd>Enter</kbd> after typing:</p>
<p><kbd>datacalc --start</kbd></p>

<p>If DataCalc starts successfully, you will see:</p>
<p><samp>DataCalc v2.0 loaded. Ready for input.</samp></p>

<p>The main calculation function uses the formula:</p>
<p>Result = <var>a</var> + <var>b</var> * <var>c</var></p>

<p>Here is an example script:</p>
<pre>
<code>
a = 5
b = 3
c = 2
result = a + (b * c)
print(result)
</code>
</pre>

<p>The function <code>print()</code> displays the final output to the screen.</p>

</body>
</html>
```

**Expected Output:**

> **DataCalc Quick Start Guide**
>
> To launch DataCalc, open your terminal and press `Enter` after typing:
> `datacalc --start`
>
> If DataCalc starts successfully, you will see:
> `DataCalc v2.0 loaded. Ready for input.`
>
> The main calculation function uses the formula:
> Result = *a* + *b* * *c*
>
> Here is an example script:
> ```
> a = 5
> b = 3
> c = 2
> result = a + (b * c)
> print(result)
> ```
>
> The function `print()` displays the final output to the screen.

---

## Mini Project: Technical Documentation Page

Now you will build a complete, realistic mini project using everything you've learned.

### Project: "Python Basics Reference Card"

**Goal:** Create a single-page HTML reference card for a beginner learning Python. It should include keyboard tips, code examples, sample output, and variable explanations.

---

### Stage 1 — Page Setup

Create the HTML skeleton and a main heading.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Python Basics Reference Card</title>
</head>
<body>

<h1>Python Basics Reference Card</h1>
<p>A beginner's guide to running Python programs and understanding basic syntax.</p>

</body>
</html>
```

**Milestone Output:** A page with a title and introductory sentence.

---

### Stage 2 — Running Python (Using `<kbd>` and `<samp>`)

Add a section explaining how to run Python from the terminal.

```html
<h2>Running Python</h2>

<p>To check if Python is installed on your computer, open the terminal and type:</p>
<p><kbd>python --version</kbd></p>

<p>If Python is installed, you will see something like:</p>
<p><samp>Python 3.11.2</samp></p>

<p>To run a Python script named <code>hello.py</code>, type:</p>
<p><kbd>python hello.py</kbd></p>

<p>If your script runs successfully, any print statements will appear in the terminal:</p>
<p><samp>Hello, World!</samp></p>
```

**Milestone Output:** A section showing terminal commands and expected responses.

---

### Stage 3 — Core Code Examples (Using `<pre>` + `<code>`)

Add a section with actual Python code snippets.

```html
<h2>Your First Python Program</h2>

<p>Type the following code into a file called <code>hello.py</code>:</p>

<pre>
<code>
# This is a comment
print("Hello, World!")
</code>
</pre>

<h2>Variables and Arithmetic</h2>

<p>You can store numbers in variables and perform calculations:</p>

<pre>
<code>
x = 10
y = 5
total = x + y
print(total)
</code>
</pre>

<p>The expected output after running this code is:</p>
<p><samp>15</samp></p>

<h2>Getting User Input</h2>

<p>To ask the user to type something, use the <code>input()</code> function:</p>

<pre>
<code>
name = input("What is your name? ")
print("Hello, " + name)
</code>
</pre>

<p>When you run this, the terminal will display:</p>
<p><samp>What is your name?</samp></p>
<p>After the user types their name and presses <kbd>Enter</kbd>, it will show:</p>
<p><samp>Hello, Amara</samp></p>
```

**Milestone Output:** Multiple formatted code blocks with correct line breaks and indentation.

---

### Stage 4 — Formulas and Variables (Using `<var>`)

Add a maths section connecting Python to STEM concepts.

```html
<h2>Using Python for Maths</h2>

<p>Python can calculate formulas just like a scientific calculator. For example, 
the formula for the area of a circle is:</p>

<p>Area = π × <var>r</var> × <var>r</var></p>

<p>Where <var>r</var> is the radius. In Python, you would write this as:</p>

<pre>
<code>
import math
r = 7
area = math.pi * r * r
print("Area:", area)
</code>
</pre>

<p>The expected output is:</p>
<p><samp>Area: 153.93804002589985</samp></p>

<p>Here, <var>r</var> is the variable that holds the radius value, 
and <code>math.pi</code> is Python's built-in approximation of π (pi).</p>
```

**Milestone Output:** A formula displayed with italic variables, followed by the code that implements it, and the sample output.

---

### Stage 5 — Complete Final Page

Putting all stages together, your final page will look like this:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Python Basics Reference Card</title>
</head>
<body>

<h1>Python Basics Reference Card</h1>
<p>A beginner's guide to running Python programs and understanding basic syntax.</p>

<!-- ===== SECTION 1: Running Python ===== -->
<h2>Running Python</h2>

<p>To check if Python is installed, open the terminal and type:</p>
<p><kbd>python --version</kbd></p>

<p>If Python is installed, you will see:</p>
<p><samp>Python 3.11.2</samp></p>

<p>To run a Python script named <code>hello.py</code>, type:</p>
<p><kbd>python hello.py</kbd></p>

<p>A successful run of a print statement produces:</p>
<p><samp>Hello, World!</samp></p>

<!-- ===== SECTION 2: Your First Program ===== -->
<h2>Your First Python Program</h2>

<p>Type the following code into a file called <code>hello.py</code>:</p>

<pre>
<code>
# This is a comment
print("Hello, World!")
</code>
</pre>

<!-- ===== SECTION 3: Variables and Arithmetic ===== -->
<h2>Variables and Arithmetic</h2>

<p>You can store numbers in variables and perform calculations:</p>

<pre>
<code>
x = 10
y = 5
total = x + y
print(total)
</code>
</pre>

<p>Expected output:</p>
<p><samp>15</samp></p>

<!-- ===== SECTION 4: Getting User Input ===== -->
<h2>Getting User Input</h2>

<p>To ask the user to type something, use the <code>input()</code> function:</p>

<pre>
<code>
name = input("What is your name? ")
print("Hello, " + name)
</code>
</pre>

<p>The terminal will show:</p>
<p><samp>What is your name?</samp></p>
<p>After the user types their name and presses <kbd>Enter</kbd>:</p>
<p><samp>Hello, Amara</samp></p>

<!-- ===== SECTION 5: Maths with Variables ===== -->
<h2>Using Python for Maths</h2>

<p>The formula for the area of a circle is:</p>
<p>Area = π × <var>r</var> × <var>r</var></p>
<p>Where <var>r</var> is the radius. In Python:</p>

<pre>
<code>
import math
r = 7
area = math.pi * r * r
print("Area:", area)
</code>
</pre>

<p>Expected output:</p>
<p><samp>Area: 153.93804002589985</samp></p>

<p>Here, <var>r</var> is the variable holding the radius, and 
<code>math.pi</code> is Python's built-in value of π.</p>

</body>
</html>
```

**Reflection Questions:**
1. Which of the five elements did you use the most? Why do you think that is?
2. What would happen if you removed all the `<pre>` tags from the code blocks?
3. Could you use `<samp>` to show the user's own input? Or would `<kbd>` be more appropriate?
4. How would this page be useful to a real person learning Python?

**Optional Advanced Extension:** Add CSS styling to make the page look more professional. For example, give `<pre>` blocks a grey background, a border, and some padding using an inline `<style>` block.

---

## Common Beginner Mistakes

### Mistake 1: Using `<code>` Without `<pre>` for Multi-Line Code

**Wrong:**

```html
<code>
x = 5;
y = 6;
z = x + y;
</code>
```

**What Actually Happens:** All three lines collapse into a single line: `x = 5; y = 6; z = x + y;`

**Correct:**

```html
<pre>
<code>
x = 5;
y = 6;
z = x + y;
</code>
</pre>
```

**Why:** `<code>` does not preserve whitespace. `<pre>` does. Always use them together for multi-line code.

---

### Mistake 2: Using `<kbd>` for Computer Output

**Wrong:**

```html
<p>The computer printed: <kbd>File not found</kbd></p>
```

**Why It's Wrong:** `<kbd>` means "keyboard input" — something the user types. Computer output should use `<samp>`.

**Correct:**

```html
<p>The computer printed: <samp>File not found</samp></p>
```

---

### Mistake 3: Using `<pre>` for Regular Paragraphs

**Wrong:**

```html
<pre>Welcome to my website. This is a great place to learn HTML.</pre>
```

**What Actually Happens:** The text appears in monospace font, which looks strange for regular readable text.

**Correct:**

```html
<p>Welcome to my website. This is a great place to learn HTML.</p>
```

**Why:** `<pre>` is designed for code and technical content. Use `<p>` for normal text.

---

### Mistake 4: Forgetting the Closing Tag

**Wrong:**

```html
<p>Press <kbd>Ctrl + S to save your work</p>
```

The `<kbd>` tag was never closed! The browser will try to fix this, but results can be unpredictable.

**Correct:**

```html
<p>Press <kbd>Ctrl + S</kbd> to save your work</p>
```

**Rule:** Every opening tag needs a matching closing tag.

---

### Mistake 5: Mixing Up `<var>` and `<em>` for Variables

`<em>` is for **emphasis** in human language (like stressing a word in a sentence).

`<var>` is for **variables** in code or mathematics.

Both display as italic by default, but they have different semantic meanings. Screen readers and search engines interpret them differently.

**Wrong for a variable:**

```html
<p>The value of <em>x</em> is unknown.</p>
```

**Correct:**

```html
<p>The value of <var>x</var> is unknown.</p>
```

---

## Reflection Questions

Take a few minutes to think about these questions before moving on. Writing down your answers helps you remember better!

1. **What is the difference between `<kbd>` and `<samp>`?** Give a real-life scenario where you would use each one.

2. **Why is the combination `<pre><code>...</code></pre>` better than just `<code>` alone** when displaying multi-line code?

3. **Can you think of a website you use regularly** (a tutorial site, a school portal, a banking app) where any of these elements might be used? Which elements and where?

4. **What does "semantic HTML" mean?** Why should you use `<kbd>` instead of just making text bold when showing keyboard shortcuts?

5. **In the mini project**, you built a Python reference card. What other programming language or topic could you make a reference card for using these same elements?

6. **What would happen** if a screen reader (used by blind or visually impaired users) reads a page that uses `<kbd>` properly vs one that just uses bold text? Why does it matter?

---

## Completion Checklist

Go through this list and tick off each item before you consider this lesson complete:

- [ ] I understand what the `<kbd>` element is and when to use it
- [ ] I understand what the `<samp>` element is and when to use it
- [ ] I understand what the `<code>` element is and when to use it
- [ ] I understand what the `<pre>` element is and when to use it
- [ ] I know why `<pre>` and `<code>` are used together for multi-line code blocks
- [ ] I understand what the `<var>` element is and when to use it
- [ ] I know the visual difference between all five elements (monospace vs italic)
- [ ] I know the difference between `<kbd>` (user input) and `<samp>` (computer output)
- [ ] I have completed all five guided exercises
- [ ] I have built the mini project (Python Basics Reference Card)
- [ ] I can name at least three common beginner mistakes and how to fix them
- [ ] I understand what "semantic HTML" means in the context of these elements
- [ ] I can explain these concepts to someone else in simple language

---

## Lesson Summary

In this lesson, you learned that HTML has five dedicated elements for displaying **computer-related and technical content**. Each one serves a different, specific purpose:

- **`<kbd>`** marks text that the user is expected to **type or press** on a keyboard. It renders in monospace font. Use it for keyboard shortcuts and commands.

- **`<samp>`** marks text that represents **output from a computer program** — like error messages or terminal responses. It also renders in monospace font.

- **`<code>`** marks **actual computer code** — commands, snippets, function names, etc. It renders in monospace font. Works well inline inside sentences.

- **`<pre>`** is a block element that **preserves all whitespace** (spaces, tabs, line breaks) exactly as typed. It is always used together with `<code>` to display properly formatted multi-line code blocks.

- **`<var>`** marks **variables** in programming or mathematical expressions. It typically renders in italic and carries semantic meaning different from plain emphasis.

These elements are used everywhere in the real world — on documentation sites like MDN Web Docs, programming tutorial platforms, textbook websites, and any technical tool that needs to communicate clearly with its users.

Mastering these elements will immediately make your web pages more professional, accessible, and meaningful to both users and search engines.

---

## HTML Computer Code Elements — Quick Reference Table

| Tag | Description | Typical Use |
|-----|-------------|-------------|
| `<kbd>` | Keyboard input | Keyboard shortcuts, commands to type |
| `<samp>` | Sample computer output | Error messages, program responses |
| `<code>` | Computer code | Inline code, function names, commands |
| `<pre>` | Preformatted text | Multi-line code blocks, preserving whitespace |
| `<var>` | Variable | Variable names in code or math formulas |

---

*End of Lesson 27 — You're ready for Lesson 28: HTML Semantic Elements!*
