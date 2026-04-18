---
render_with_liquid: false
title: "Lesson 22: HTML JavaScript — Making Web Pages Come Alive"
nav_order: 22
---

# Lesson 22: HTML JavaScript — Making Web Pages Come Alive

---

## Lesson Introduction

Up until this point in your HTML journey, every page you have built has been **static** — meaning once the page loads in the browser, nothing changes. The text stays the same. The colours stay the same. Nothing moves or responds to the user.

This lesson is the moment everything changes.

In this lesson, you are going to discover **JavaScript** — the programming language that brings HTML pages to **life**. JavaScript is what makes buttons actually do things, what makes content appear and disappear, what lets you click something and watch the page respond instantly without reloading.

You will learn:
- What JavaScript is and why it matters
- How to embed JavaScript directly into your HTML page using the `<script>` tag
- How JavaScript can **find** any element on your page using `document.getElementById()`
- How JavaScript can **change the text content** of an element
- How JavaScript can **change the CSS styles** of an element
- How JavaScript can **change the attributes** (like `src` on an image) of an element
- What the `<noscript>` tag is and when to use it
- How to trigger JavaScript with a button click using the `onclick` attribute

By the end of this lesson, you will have built your first truly interactive webpage — one that responds to the user's actions.

> **Important note:** This lesson introduces JavaScript from an HTML perspective. You do not need to know JavaScript deeply yet. Think of this as your first handshake with a powerful new friend. A full JavaScript course is a separate journey — here, you are just learning how HTML and JavaScript connect.

---

## Prerequisite Concepts

Before diving in, let us make sure you are comfortable with these ideas.

### What is an HTML element?

An HTML element is content wrapped in opening and closing tags, like `<p>Hello</p>`. Every element on your page is something the browser renders and displays.

### What is an HTML attribute?

An attribute gives extra information to an HTML tag. For example, `<img src="photo.jpg">` — here `src` is an attribute that tells the image element where to find the picture file.

### What is the `id` attribute?

The `id` attribute gives a **unique name** to one specific HTML element. No two elements on the same page should share the same `id`. Think of it like a name badge — each person (element) has their own unique badge so you can find them individually.

```html
<p id="message">This is my special paragraph.</p>
```

Here, the paragraph has been given the unique ID of `"message"`. We can now use that name to find and change this exact paragraph using JavaScript.

### What is a programming language?

A programming language is a set of instructions that a computer can understand and execute. HTML is a **markup language** (it describes content). JavaScript is a true **programming language** — it can perform logic, respond to events, make decisions, and change things dynamically.

---

## Part 1: What Is JavaScript and Why Does It Exist?

### The Problem That JavaScript Solves

Imagine a webpage that shows the current time. If the page is built with only HTML, the time would be baked into the HTML when the page was built and would never update. A user visiting at 3pm would still see the time from when the developer last edited the file.

JavaScript solves this. It runs **inside the user's browser**, right at the moment the page is being viewed, and can do things in real time — fetch the current time, react to a button click, show or hide content, validate a form, animate an element, and much more.

### What is JavaScript?

JavaScript is the programming language of the web. It is:
- **Client-side** — it runs in the user's own browser, not on a server somewhere else
- **Dynamic** — it can change the page after it has already loaded
- **Event-driven** — it responds to things the user does (clicking, typing, hovering)
- **Universally supported** — every modern browser understands JavaScript natively

**Analogy:** Think of HTML as the skeleton of a body (structure), CSS as the clothing and skin (appearance), and JavaScript as the muscles and nervous system (movement and interaction).

### Real-World Uses of JavaScript

JavaScript is used everywhere in web development, data science dashboards, and software tools:

- **Buttons that do things** — clicking a button shows a popup or sends a form
- **Form validation** — checking that an email address looks correct before submitting
- **Image sliders** — the pictures that automatically scroll on a homepage
- **Live clocks and countdown timers** — a timer that counts down to an exam
- **Interactive maps** — clicking a location and seeing details appear
- **Data visualisation** — charts that update as new data comes in
- **Shopping cart totals** — updating the price when you change quantity
- **Chat applications** — messages appearing without refreshing the page

---

## Part 2: The `<script>` Tag — Where JavaScript Lives in HTML

### What Is the `<script>` Tag?

The `<script>` tag is the HTML element that tells the browser: **"What follows is JavaScript code — please run it."**

Everything written between `<script>` and `</script>` is treated as JavaScript instructions, not HTML content.

```html
<script>
  /* Your JavaScript code goes here */
</script>
```

The `<script>` tag has **no required attributes** when you are writing JavaScript directly inside it. However, it can optionally point to an external JavaScript file using the `src` attribute (you will learn this in your dedicated JavaScript course).

### Where Do You Put `<script>` Tags?

You can place `<script>` tags in two places in an HTML document:

1. **Inside the `<head>` section** — the script loads before the page body is shown
2. **Inside the `<body>` section** — the script runs as the browser reads that part of the page (most commonly placed at the **bottom** of `<body>` for best performance)

For this lesson, we will keep all our `<script>` tags inside `<body>` right where they are needed, so you can clearly see the connection between the HTML and the JavaScript.

---

## Part 3: `document.getElementById()` — Finding Elements on Your Page

### The Most Important JavaScript Method for HTML

Before JavaScript can change anything on your page, it first needs to **find** the element it wants to change. The most common way to do this is:

```javascript
document.getElementById("someId")
```

Let us break this apart word by word:

- `document` — This refers to the entire HTML page. In JavaScript, `document` is a built-in object that represents your whole webpage. It is your gateway to everything on the page.
- `.` — The dot is used to access something that belongs to the `document`. Think of it like saying "the document's..."
- `getElementById` — This is a **method** (a built-in action/function) that searches the document for an element with a specific `id`. "Get element by ID" — find me the element that has this ID.
- `("someId")` — The parentheses `()` contain the argument — the specific `id` name you are searching for. It must be written in quotes because it is a text string.

**Analogy:** Imagine `document` is a huge school register. `getElementById("demo")` is like saying "look up the student named 'demo' in the register and bring me their file." Once you have the file, you can read it or change what is written in it.

### Example 1 — Finding an Element by ID (Visualising the Connection)

```html
<!DOCTYPE html>
<html>
  <body>

    <p id="demo">I am the original text.</p>

    <script>
      document.getElementById("demo").innerHTML = "Hello JavaScript!";
    </script>

  </body>
</html>
```

**Expected Output (in browser):**
```
Hello JavaScript!
```

Even though the `<p>` tag originally said "I am the original text.", by the time the browser finishes loading the page, the JavaScript has already changed it to "Hello JavaScript!".

**Line by line breakdown:**

`<p id="demo">I am the original text.</p>`
- A paragraph element is created with the unique ID of `"demo"`
- It starts with the text "I am the original text."

`document.getElementById("demo")`
- JavaScript searches the whole document for an element whose `id` is `"demo"`
- It finds our `<p>` tag and returns it as an object JavaScript can now control

`.innerHTML`
- `innerHTML` is a property of every HTML element
- It represents the content inside the element's tags
- Reading it gives you the current content; setting it with `=` replaces the content

`= "Hello JavaScript!";`
- The `=` sign assigns a new value
- `"Hello JavaScript!"` is the new text content that replaces whatever was there before
- The `;` at the end of a JavaScript statement signals the end of that instruction (like a full stop in a sentence)

> **Thinking Prompt:** What would happen if you changed `"demo"` in `getElementById("demo")` to an ID that does not exist on the page? Try it — what does the browser do?

---

## Part 4: Three Things JavaScript Can Change on Your Page

JavaScript can interact with your HTML in three major ways. Let us explore each one with clear, isolated examples.

---

### 4A: Changing Content (`innerHTML`)

`innerHTML` controls what text or HTML is **inside** an element. You can completely replace the content of any element.

#### Example 2 — Change Text Content with a Button

This is your first truly interactive example. A button, when clicked, will change the text in a paragraph.

```html
<!DOCTYPE html>
<html>
  <body>

    <h2>My First JavaScript</h2>

    <p id="demo">This text will change when you click the button.</p>

    <button onclick="document.getElementById('demo').innerHTML = 'Text has been changed!'">
      Click Me
    </button>

  </body>
</html>
```

**Before clicking the button:**
```
My First JavaScript

This text will change when you click the button.

[Click Me]
```

**After clicking the button:**
```
My First JavaScript

Text has been changed!

[Click Me]
```

**Line by line breakdown:**

`<p id="demo">This text will change when you click the button.</p>`
- A paragraph with the ID `"demo"`. This is our target.

`<button onclick="...">`
- A clickable button
- `onclick` is an **HTML event attribute** — it tells the browser: "When this button is clicked, run the JavaScript code written here"
- The JavaScript inside `onclick="..."` runs the moment the user clicks

`document.getElementById('demo').innerHTML = 'Text has been changed!'`
- Notice that inside `onclick="..."`, we use **single quotes** `'` around the ID and text, because the `onclick` value itself is wrapped in double quotes `"`. Using single quotes inside prevents confusion.
- This finds the element with ID `demo` and sets its inner text to `'Text has been changed!'`

> **Thinking Prompt:** What happens if you click the button a second time? Does it do anything different? Why or why not?

---

#### Example 3 — Showing the Date and Time

A classic JavaScript example — displaying the current date and time.

```html
<!DOCTYPE html>
<html>
  <body>

    <h2>What Is the Date and Time Right Now?</h2>

    <p id="dateDisplay">Click the button to find out!</p>

    <button onclick="document.getElementById('dateDisplay').innerHTML = Date()">
      Show Date & Time
    </button>

  </body>
</html>
```

**Before clicking:**
```
What Is the Date and Time Right Now?

Click the button to find out!

[Show Date & Time]
```

**After clicking:**
```
What Is the Date and Time Right Now?

Sat Apr 18 2026 14:32:07 GMT+0100 (West Africa Standard Time)

[Show Date & Time]
```

(The exact date and time will be whatever time it is when **you** click the button.)

**New concept — `Date()`:**
- `Date()` is a built-in JavaScript function that returns the current date and time as text
- Notice there are no quotes around `Date()` — it is not a string, it is a function call that produces a string

---

### 4B: Changing Styles (`style.property`)

JavaScript can also change the **CSS styling** of any element — its colour, font size, background colour, visibility, and much more.

The pattern is:

```javascript
document.getElementById("someId").style.cssProperty = "value";
```

- `.style` — accesses the style object of the element
- `.cssProperty` — the specific CSS property you want to change. In JavaScript, CSS property names that use hyphens in CSS (like `font-size`) are written in **camelCase** in JavaScript (like `fontSize`). The hyphen is removed and the next word is capitalised.
- `= "value"` — the new value to set, always as a string in quotes

#### Example 4 — Changing Font Size and Colour

```html
<!DOCTYPE html>
<html>
  <body>

    <p id="styleDemo">Watch me change my style!</p>

    <button onclick="makeBig()">Make Text Big and Red</button>

    <script>
      function makeBig() {
        document.getElementById("styleDemo").style.fontSize = "36px";
        document.getElementById("styleDemo").style.color = "red";
        document.getElementById("styleDemo").style.backgroundColor = "yellow";
      }
    </script>

  </body>
</html>
```

**Before clicking:**
```
Watch me change my style!

[Make Text Big and Red]
```

**After clicking:**
The paragraph text becomes 36px tall, turns red, and gets a yellow background.

**New concept — `function`:**

In this example, instead of writing JavaScript directly in `onclick`, we wrote a **function**. A function is a reusable block of named JavaScript code.

```javascript
function makeBig() {
    // code here
}
```

- `function` — the keyword that tells JavaScript "I am defining a reusable set of instructions"
- `makeBig` — the name we chose for this function (you can name it anything)
- `()` — the parentheses after the name (can hold inputs, but here we have none)
- `{ ... }` — the curly braces wrap all the code that belongs to this function

Then in the button: `onclick="makeBig()"` — "when clicked, run the function called `makeBig`".

**CSS Property Name Comparison:**

| In CSS | In JavaScript |
|---|---|
| `font-size` | `fontSize` |
| `background-color` | `backgroundColor` |
| `color` | `color` (no change needed — single word) |
| `font-weight` | `fontWeight` |
| `text-align` | `textAlign` |
| `border-radius` | `borderRadius` |

Notice the pattern: **remove the hyphen and capitalise the next letter**.

#### Example 5 — Changing Styles with Multiple Lines in a Function

```html
<!DOCTYPE html>
<html>
  <body>

    <p id="demo">I am a normal-looking paragraph right now.</p>

    <button onclick="changeStyles()">Transform Me!</button>

    <script>
      function changeStyles() {
        document.getElementById("demo").style.fontSize = "25px";
        document.getElementById("demo").style.color = "red";
        document.getElementById("demo").style.backgroundColor = "yellow";
      }
    </script>

  </body>
</html>
```

**Expected Output after clicking:**
The paragraph text becomes 25px, red, with a yellow background.

Breaking down each style change line:

`document.getElementById("demo").style.fontSize = "25px";`
- Finds the element with ID `"demo"`
- Accesses its `.style` object
- Sets the `fontSize` property to `"25px"` (25 pixels tall)

`document.getElementById("demo").style.color = "red";`
- Changes the text colour to red

`document.getElementById("demo").style.backgroundColor = "yellow";`
- Changes the background colour to yellow

> **Thinking Prompt:** What would happen if you added a second button that resets the text back to its original style? What values would you set for `fontSize`, `color`, and `backgroundColor` to undo the changes?

---

### 4C: Changing Attributes (`attribute`)

JavaScript can also change **HTML attributes** of elements. For example, you can swap out the `src` attribute of an `<img>` element to make the image change. You can change the `href` of a link, the `value` of an input, and much more.

The pattern is:

```javascript
document.getElementById("someId").attributeName = "new value";
```

#### Example 6 — Changing an Image's Source

```html
<!DOCTYPE html>
<html>
  <body>

    <img id="myImage" src="smiley.gif" width="100">

    <br><br>

    <button onclick="document.getElementById('myImage').src = 'landscape.jpg'">
      Change Image
    </button>

  </body>
</html>
```

**Before clicking:**
An image called `smiley.gif` is displayed.

**After clicking:**
The same `<img>` element now shows `landscape.jpg` instead — the image has changed on the page without any page reload.

**Line by line breakdown:**

`<img id="myImage" src="smiley.gif" width="100">`
- An image element with ID `"myImage"`
- Currently showing the file `smiley.gif`
- Width of 100 pixels

`document.getElementById('myImage').src = 'landscape.jpg'`
- Finds the element with ID `"myImage"` (our image)
- Directly sets the `.src` property to the new file `'landscape.jpg'`
- The browser immediately loads and displays the new image

> **Thinking Prompt:** Can you add a second button that changes the image **back** to `smiley.gif`? What would the JavaScript look like?

---

## Part 5: The `<noscript>` Tag — A Safety Net for Users Without JavaScript

### What Is `<noscript>`?

The `<noscript>` tag defines **alternative content** that is shown to users who have:
- Disabled JavaScript in their browser settings
- A very old or unusual browser that does not support JavaScript at all

This is extremely rare today — virtually all browsers support JavaScript — but it is good professional practice to include a fallback message for accessibility and robustness.

### How `<noscript>` Works

When a browser that supports and has JavaScript enabled encounters `<noscript>`, it **ignores** everything inside it. The `<noscript>` content is invisible.

When a browser **without** JavaScript encounters `<noscript>`, it shows the content inside as a fallback message.

### Example 7 — `<script>` with `<noscript>` Fallback

```html
<!DOCTYPE html>
<html>
  <body>

    <p id="demo">JavaScript will replace this text.</p>

    <script>
      document.getElementById("demo").innerHTML = "Hello JavaScript!";
    </script>

    <noscript>
      Sorry, your browser does not support JavaScript! Please enable JavaScript
      or use a modern browser to see this page correctly.
    </noscript>

  </body>
</html>
```

**Expected Output (in a normal browser with JavaScript enabled):**
```
Hello JavaScript!
```
(The `<noscript>` message is hidden entirely.)

**Expected Output (in a browser with JavaScript disabled):**
```
JavaScript will replace this text.
Sorry, your browser does not support JavaScript! Please enable JavaScript
or use a modern browser to see this page correctly.
```
(The script does not run, so the original paragraph text stays. The `<noscript>` message appears.)

**Line by line breakdown:**

`<script>` ... `</script>`
- Contains JavaScript that changes the paragraph text
- Runs only if JavaScript is enabled

`<noscript>` ... `</noscript>`
- Contains a plain message for users without JavaScript
- The browser only shows this when scripts are disabled or unavailable

---

## Part 6: Putting It All Together — Full Working Examples

Now let us combine everything into complete, realistic mini-pages.

### Example 8 — A Complete Interactive Page with All Three Types of Changes

```html
<!DOCTYPE html>
<html>
  <body>

    <h1>JavaScript Demonstration Page</h1>

    <!-- Section 1: Change Content -->
    <h2>1. Change Content</h2>
    <p id="contentDemo">Original paragraph text.</p>
    <button onclick="changeContent()">Change the Text</button>

    <br><br>

    <!-- Section 2: Change Styles -->
    <h2>2. Change Styles</h2>
    <p id="styleDemo">Watch my style change!</p>
    <button onclick="changeStyle()">Change the Style</button>

    <br><br>

    <!-- Section 3: Change Attribute -->
    <h2>3. Change Attribute</h2>
    <p>Current button label: <span id="labelDemo">Submit</span></p>
    <button onclick="changeAttribute()">Change Button Label</button>

    <script>
      function changeContent() {
        document.getElementById("contentDemo").innerHTML =
          "The content has been changed by JavaScript!";
      }

      function changeStyle() {
        document.getElementById("styleDemo").style.color = "blue";
        document.getElementById("styleDemo").style.fontSize = "28px";
        document.getElementById("styleDemo").style.fontWeight = "bold";
      }

      function changeAttribute() {
        document.getElementById("labelDemo").innerHTML = "Send Message";
      }
    </script>

    <noscript>
      This page requires JavaScript to function. Please enable JavaScript.
    </noscript>

  </body>
</html>
```

**Expected Behaviour:**
- Clicking "Change the Text" → The paragraph under Section 1 changes to "The content has been changed by JavaScript!"
- Clicking "Change the Style" → The paragraph under Section 2 becomes blue, 28px, and bold
- Clicking "Change Button Label" → The word "Submit" in Section 3 changes to "Send Message"

---

## HTML Tags Reference for This Lesson

| Tag | Description |
|---|---|
| `<script>` | Defines a client-side script (JavaScript) embedded in or linked from the HTML page |
| `<noscript>` | Defines alternative content to display when a browser does not support or has disabled JavaScript |

---

## Guided Practice Exercises

### Exercise 1: Your First Click-to-Change

**Objective:** Practice connecting a button click to a content change.

**Scenario:** You are building a greeting card webpage that shows a hidden message when the user clicks a button.

**Steps:**

1. Create an HTML file called `greeting.html`
2. Write the following code:

```html
<!DOCTYPE html>
<html>
  <body>

    <h1>🎉 Happy Birthday!</h1>

    <p id="message">Click the button to reveal your birthday message!</p>

    <button onclick="revealMessage()">Reveal Message 🎁</button>

    <script>
      function revealMessage() {
        document.getElementById("message").innerHTML =
          "Wishing you joy, laughter, and endless success. You deserve it all! 🎂";
      }
    </script>

  </body>
</html>
```

**Expected Output before clicking:**
```
🎉 Happy Birthday!

Click the button to reveal your birthday message!

[Reveal Message 🎁]
```

**Expected Output after clicking:**
```
🎉 Happy Birthday!

Wishing you joy, laughter, and endless success. You deserve it all! 🎂

[Reveal Message 🎁]
```

**Self-Check Questions:**
- What is the `id` of the paragraph being changed?
- What does `onclick` do?
- What does `.innerHTML` do?
- Could you add a second button that resets the message back to the original?

---

### Exercise 2: Style Switcher

**Objective:** Use JavaScript to toggle the visual appearance of text.

**Scenario:** You are building a simple "Night Mode" toggle for a webpage.

```html
<!DOCTYPE html>
<html>
  <body id="pageBody" style="background-color: white; color: black; padding: 30px;">

    <h1 id="title">Welcome to My Page</h1>
    <p id="content">This page supports a dark mode. Try clicking the button below!</p>

    <button onclick="enableDarkMode()">🌙 Enable Dark Mode</button>
    <button onclick="enableLightMode()">☀️ Enable Light Mode</button>

    <script>
      function enableDarkMode() {
        document.getElementById("pageBody").style.backgroundColor = "black";
        document.getElementById("pageBody").style.color = "white";
      }

      function enableLightMode() {
        document.getElementById("pageBody").style.backgroundColor = "white";
        document.getElementById("pageBody").style.color = "black";
      }
    </script>

  </body>
</html>
```

**Expected Behaviour:**
- Clicking "🌙 Enable Dark Mode" → The page background turns black and text turns white
- Clicking "☀️ Enable Light Mode" → The page background returns to white and text returns to black

**CSS Breakdown:**
- `style="background-color: white; color: black; padding: 30px;"` — sets the initial default styles on the `<body>` element itself
- `document.getElementById("pageBody").style.backgroundColor = "black";` — JavaScript changes the `backgroundColor` property at runtime

**Self-Check Questions:**
- Why does the `<body>` tag have an `id="pageBody"` attribute?
- What CSS property controls the background colour in JavaScript?
- Can you add a third button that makes the background navy blue with white text?

---

### Exercise 3: Interactive Quiz Question

**Objective:** Build a simple question-and-answer interaction using JavaScript.

**Scenario:** You are building a quiz page. When the user clicks an answer button, feedback appears.

```html
<!DOCTYPE html>
<html>
  <body>

    <h2>Quick Quiz!</h2>
    <p><strong>Question:</strong> What does HTML stand for?</p>

    <button onclick="checkAnswer('correct')">
      Hyper Text Markup Language
    </button>

    <button onclick="checkAnswer('wrong')">
      High Transfer Markup Language
    </button>

    <button onclick="checkAnswer('wrong')">
      Hyper Tool Main Language
    </button>

    <br><br>

    <p id="feedback" style="font-size: 20px; font-weight: bold;"></p>

    <script>
      function checkAnswer(result) {
        if (result === 'correct') {
          document.getElementById("feedback").innerHTML = "✅ Correct! Well done!";
          document.getElementById("feedback").style.color = "green";
        } else {
          document.getElementById("feedback").innerHTML = "❌ Not quite! Try again.";
          document.getElementById("feedback").style.color = "red";
        }
      }
    </script>

  </body>
</html>
```

**Expected Output — if correct answer clicked:**
```
✅ Correct! Well done!     (in green text)
```

**Expected Output — if wrong answer clicked:**
```
❌ Not quite! Try again.    (in red text)
```

**New concept — `if` statement:**
This is your first glimpse at a JavaScript decision:

```javascript
if (result === 'correct') {
    // runs if result equals 'correct'
} else {
    // runs if result does NOT equal 'correct'
}
```

- `if` — means "only do this if the condition is true"
- `result === 'correct'` — checks if the variable `result` is exactly equal to the string `'correct'`
- `===` — means "strictly equal to" (checks both value and type)
- `else` — means "otherwise, do this instead"

Notice how the three buttons all call `checkAnswer()` but with different arguments: `'correct'` or `'wrong'`. The function receives that value in its `result` parameter and acts accordingly.

**Self-Check Questions:**
- What does `===` mean in JavaScript?
- Why do the wrong-answer buttons both call the same function?
- Can you add a fourth button (another wrong answer) to the quiz?

---

## Mini Project: Interactive Student Report Card

In this project, you will build an interactive student report card page. A teacher can click buttons to reveal the student's grade, highlight their score, and display a personalised message — all without reloading the page.

### Stage 1: Setup — Build the HTML Structure

```html
<!DOCTYPE html>
<html>
  <body style="font-family: Arial, sans-serif; padding: 30px;">

    <h1>📋 Student Report Card</h1>

    <div style="border: 2px solid #ccc; padding: 20px; width: 400px;">
      <h2>Student: Amina Okafor</h2>
      <p>Subject: Mathematics</p>
      <p>Score: <span id="scoreDisplay">[ Click to reveal ]</span></p>
      <p>Grade: <span id="gradeDisplay">[ Click to reveal ]</span></p>
      <p>Remark: <span id="remarkDisplay">[ Click to reveal ]</span></p>
    </div>

    <br>
    <button onclick="revealReport()">📊 Reveal Full Report</button>

  </body>
</html>
```

**Milestone Output:** A neat card with three hidden fields and one button. All the span elements show placeholder text.

---

### Stage 2: Add the JavaScript Logic

Now add the `<script>` block with the `revealReport()` function:

```html
<!DOCTYPE html>
<html>
  <body style="font-family: Arial, sans-serif; padding: 30px;">

    <h1>📋 Student Report Card</h1>

    <div style="border: 2px solid #ccc; padding: 20px; width: 400px;">
      <h2>Student: Amina Okafor</h2>
      <p>Subject: Mathematics</p>
      <p>Score: <span id="scoreDisplay">[ Click to reveal ]</span></p>
      <p>Grade: <span id="gradeDisplay">[ Click to reveal ]</span></p>
      <p>Remark: <span id="remarkDisplay">[ Click to reveal ]</span></p>
    </div>

    <br>
    <button onclick="revealReport()">📊 Reveal Full Report</button>
    <button onclick="resetReport()">🔄 Reset</button>

    <script>
      function revealReport() {
        // Change the score
        document.getElementById("scoreDisplay").innerHTML = "87 / 100";
        document.getElementById("scoreDisplay").style.color = "blue";
        document.getElementById("scoreDisplay").style.fontWeight = "bold";

        // Change the grade
        document.getElementById("gradeDisplay").innerHTML = "A";
        document.getElementById("gradeDisplay").style.color = "green";
        document.getElementById("gradeDisplay").style.fontWeight = "bold";

        // Change the remark
        document.getElementById("remarkDisplay").innerHTML =
          "Excellent performance! Keep up the great work.";
        document.getElementById("remarkDisplay").style.color = "darkgreen";
      }

      function resetReport() {
        document.getElementById("scoreDisplay").innerHTML = "[ Click to reveal ]";
        document.getElementById("scoreDisplay").style.color = "black";
        document.getElementById("scoreDisplay").style.fontWeight = "normal";

        document.getElementById("gradeDisplay").innerHTML = "[ Click to reveal ]";
        document.getElementById("gradeDisplay").style.color = "black";
        document.getElementById("gradeDisplay").style.fontWeight = "normal";

        document.getElementById("remarkDisplay").innerHTML = "[ Click to reveal ]";
        document.getElementById("remarkDisplay").style.color = "black";
      }
    </script>

    <noscript>
      This report card requires JavaScript to display results. Please enable
      JavaScript in your browser.
    </noscript>

  </body>
</html>
```

**Expected Behaviour:**
- Clicking "📊 Reveal Full Report" → All three spans fill in with score, grade, and remark in styled colours
- Clicking "🔄 Reset" → All three spans return to their placeholder text and black colour

---

### Stage 3: Reflection Questions

- Why was `<span>` used inside the `<p>` tags instead of another `<p>` tag?
- What would happen if two elements had the same `id`, like two spans both with `id="scoreDisplay"`?
- What does the `<noscript>` tag do in this project?
- Can you modify the project to show a **different remark** if the score is below 50? (Hint: you would use an `if` statement.)

**Optional Advanced Extensions:**
- Add a second student card on the same page and wire up their own reveal button
- Change the card's `border` colour to green using JavaScript when the report is revealed
- Add an animated emoji that appears (🎉) next to the grade when revealed

---

## Common Beginner Mistakes

### Mistake 1: Mismatching the `id` in HTML and JavaScript

**Wrong:**
```html
<p id="myText">Hello</p>

<script>
  document.getElementById("mytext").innerHTML = "Changed!";
  /* "mytext" is lowercase — but the id is "myText" with a capital T */
</script>
```

**Why it fails:** IDs are **case-sensitive**. `"myText"` and `"mytext"` are two completely different IDs. JavaScript will look for an element with ID `"mytext"`, not find it, and the change will silently fail.

**Correct:**
```html
<p id="myText">Hello</p>

<script>
  document.getElementById("myText").innerHTML = "Changed!";
  /* Both use exactly "myText" */
</script>
```

---

### Mistake 2: Forgetting the Quotes Around the ID

**Wrong:**
```javascript
document.getElementById(demo).innerHTML = "Hello!";
/* demo has no quotes */
```

**Why it fails:** Without quotes, JavaScript thinks `demo` is a variable name, not a text string. Since no variable called `demo` is defined, it throws an error.

**Correct:**
```javascript
document.getElementById("demo").innerHTML = "Hello!";
/* "demo" is in quotes — it is a string */
```

---

### Mistake 3: Using Hyphens in JavaScript Style Property Names

**Wrong:**
```javascript
document.getElementById("demo").style.font-size = "20px";
/* font-size uses a hyphen — invalid in JavaScript */
```

**Why it fails:** In JavaScript, the hyphen `-` is the **subtraction operator**. `style.font-size` means "style.font minus size", which is nonsense. JavaScript throws an error.

**Correct:**
```javascript
document.getElementById("demo").style.fontSize = "20px";
/* fontSize uses camelCase — correct in JavaScript */
```

---

### Mistake 4: Quote Conflicts Inside `onclick`

**Wrong:**
```html
<button onclick="document.getElementById("demo").innerHTML = "Changed!"">
  Click
</button>
```

**Why it fails:** The `onclick` attribute value starts with `"`, then the JavaScript uses `"` around `"demo"` and `"Changed!"`, which closes the `onclick` attribute prematurely. The browser gets confused.

**Correct — use single quotes inside the `onclick` attribute:**
```html
<button onclick="document.getElementById('demo').innerHTML = 'Changed!'">
  Click
</button>
```

Or move the JavaScript to a separate function:
```html
<button onclick="changeIt()">Click</button>

<script>
  function changeIt() {
    document.getElementById("demo").innerHTML = "Changed!";
  }
</script>
```

---

### Mistake 5: Placing `<script>` Before the Element It Targets

**Wrong:**
```html
<script>
  document.getElementById("demo").innerHTML = "Hello!";
  /* The paragraph below doesn't exist yet when this script runs! */
</script>

<p id="demo">Original text.</p>
```

**Why it fails:** The browser reads HTML from top to bottom. When the `<script>` runs, it tries to find `id="demo"`, but the `<p>` element hasn't been read yet — so it does not exist. JavaScript finds nothing, and the change fails silently or throws an error.

**Correct — put `<script>` after the element it targets:**
```html
<p id="demo">Original text.</p>

<script>
  document.getElementById("demo").innerHTML = "Hello!";
  /* The paragraph exists now — JavaScript can find it */
</script>
```

---

### Mistake 6: Forgetting the Semicolon at the End of JavaScript Statements

**Technically not always an error, but bad practice:**
```javascript
document.getElementById("demo").innerHTML = "Hello!"
/* Missing semicolon */
```

**Better practice:**
```javascript
document.getElementById("demo").innerHTML = "Hello!";
/* Semicolon marks the end of this statement clearly */
```

JavaScript is forgiving enough to often work without semicolons, but professional developers always include them. It prevents subtle bugs and makes code easier to read.

---

## Reflection Questions

Think carefully about these questions to test your understanding:

1. What is the purpose of the `<script>` tag in HTML?
2. What does `document` refer to in `document.getElementById()`?
3. Why is the `id` attribute important when using JavaScript?
4. What does `innerHTML` allow you to do to an HTML element?
5. How is `style.fontSize` different from the CSS property `font-size`? Why?
6. What is the `<noscript>` tag used for, and when would a user see its content?
7. What does `onclick` do on a button element?
8. What happens if you use `getElementById()` with an ID that does not exist on the page?
9. Why should you put `<script>` tags after the HTML elements they target?
10. What is the difference between changing `innerHTML` and changing `style.color`?

---

## Completion Checklist

Before moving on to the next lesson, confirm you can check off every item:

- [ ] I understand what JavaScript is and what makes it different from HTML
- [ ] I know what the `<script>` tag does and where to place it in an HTML document
- [ ] I understand what `document.getElementById()` does and how it works
- [ ] I can use `innerHTML` to change the text content of an HTML element
- [ ] I understand why CSS hyphenated names (like `font-size`) become camelCase in JavaScript (like `fontSize`)
- [ ] I can use `.style.property` to change the CSS styling of an HTML element from JavaScript
- [ ] I can use JavaScript to change an HTML attribute (like changing an image's `src`)
- [ ] I know what the `<noscript>` tag is for
- [ ] I understand how `onclick` connects a button click to a JavaScript function
- [ ] I know why placing `<script>` before the target element causes errors
- [ ] I completed the mini-project and both buttons work correctly
- [ ] I understand why IDs must match exactly (case-sensitive) between HTML and JavaScript

---

## Lesson Summary

In this lesson, you took your first major step from static HTML into the world of interactive, dynamic web pages.

**JavaScript** is the programming language that runs inside the browser and makes web pages respond to user actions. It is client-side (runs on the user's machine), event-driven (responds to clicks, typing, and more), and universally supported in all modern browsers.

**The `<script>` tag** is how you embed JavaScript into an HTML document. Everything between `<script>` and `</script>` is treated as JavaScript code and executed by the browser.

**`document.getElementById("id")`** is the foundational JavaScript method for finding a specific HTML element on the page by its unique `id` attribute. Once found, you can control the element completely.

**Three types of changes JavaScript can make:**
- **Content changes** — via `.innerHTML = "new text"` (replaces what is inside the element's tags)
- **Style changes** — via `.style.cssProperty = "value"` (modifies the element's CSS in real time, using camelCase property names)
- **Attribute changes** — via `.attributeName = "value"` (modifies HTML attributes like `src`, `href`, `value`)

**The `onclick` attribute** on any HTML element (especially buttons) runs JavaScript the moment the user clicks it.

**The `<noscript>` tag** provides a fallback message for the rare cases where a user's browser has JavaScript disabled or does not support it.

**HTML Script Tags Reference:**

| Tag | Description |
|---|---|
| `<script>` | Embeds or links a client-side JavaScript script |
| `<noscript>` | Fallback content for browsers without JavaScript support |

This lesson is just your introduction. JavaScript is an enormous language with its own dedicated courses. You now know how HTML and JavaScript connect — which prepares you perfectly for your future JavaScript journey.

**You are now ready for Lesson 23: HTML File Paths!**
