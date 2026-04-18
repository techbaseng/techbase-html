---
render_with_liquid: false
title: "HTML Buttons — Creating, Typing, Styling, Disabling, and Using Buttons"
nav_order: 20
---

# Lesson 20 — HTML Buttons

## Lesson Introduction

Every website you have ever used is full of buttons. The "Sign Up" button on a registration page. The "Add to Cart" button on a shopping site. The "Submit" button on a contact form. The "Reset" button that clears all your typed information. Even a simple "Click Me" button that says hello.

Buttons are the primary way users **interact** with a web page. Without them, a visitor can only read — they cannot act. Buttons are what turn a passive page into an interactive experience.

In this lesson, you will learn everything about the HTML `<button>` element — what it is, how it works, the different types it can be, how to style it, how to disable it, and how to make it respond to a user's click. You will then practise with guided exercises and build a mini project that puts buttons to real use.

By the end of this lesson you will be able to:

- Create a basic clickable button using the `<button>` element.
- Style a button with CSS to change its colour, size, and appearance.
- Use the `disabled` attribute to make a button unclickable.
- Understand and use the three button `type` values: `button`, `submit`, and `reset`.
- Use the `onclick` attribute to trigger a simple JavaScript action when a button is clicked.
- Use buttons correctly inside HTML forms.

---

## Prerequisite Concepts

Before starting this lesson, you should be comfortable with the following ideas. If anything here feels unfamiliar, revisit the earlier lessons before continuing.

**HTML tags and elements** — An HTML element is made of an opening tag, content, and a closing tag. For example: `<p>Hello</p>`. The `<button>` tag works exactly the same way.

**HTML attributes** — An attribute gives extra information to an HTML tag. Attributes are written inside the opening tag. For example: `<button disabled>`. Here, `disabled` is an attribute that modifies how the button behaves.

**CSS styling** — CSS lets you change the appearance of HTML elements. You can apply CSS to a `<button>` tag using the `style` attribute directly on the element, or with a `<style>` block in the `<head>`. We will see both approaches.

**HTML forms (brief preview)** — A form is an HTML structure that collects information from the user and can send it somewhere (like to a server). Buttons play an important role inside forms. We will introduce forms here just enough to understand button types — a dedicated Forms lesson will cover forms fully later.

---

## Part 1 — What Is the HTML Button?

### Why Do Buttons Exist?

Imagine a web page as a wall poster. You can look at it, read it, admire it — but you cannot interact with it. Now imagine that same poster had a button you could press to do something useful: show more information, send a message, confirm a purchase. That is what the HTML `<button>` element does.

> **Analogy:** A button in HTML is like a physical button on an ATM or a microwave. By itself it looks like a button and can be pressed, but it needs to be connected to some action to do anything useful. In HTML, that connection comes from the button's `type` attribute or a JavaScript `onclick` handler.

### The `<button>` Element

The HTML `<button>` element defines a clickable button on a web page. The text you put between the opening `<button>` and closing `</button>` tags becomes the visible label on the button that the user sees and clicks.

**Basic syntax:**

```html
<button>Click Me</button>
```

**Expected output in the browser:**

```
[ Click Me ]
```

A raised, clickable box with the text "Click Me" inside it appears. The exact visual style depends on the browser, but it always looks like a button.

> **Important:** By itself, this button does **nothing** when clicked. A bare `<button>` element has no built-in action. You must give it a `type` attribute, an `onclick` handler, or place it inside a form to make it actually do something. We will cover all three approaches in this lesson.

### Line-by-Line Anatomy

```html
<button>Click Me</button>
```

- `<button>` — The opening tag. This tells the browser to create a clickable button element.
- `Click Me` — The content. This is the text that appears as the button's label. It is what the user reads and clicks.
- `</button>` — The closing tag. This marks the end of the button element.

---

## Part 2 — Styling HTML Buttons with CSS

### Why Style Buttons?

The default browser style for a button — a plain grey raised box — looks acceptable but very basic. In real professional websites, buttons are styled to match the brand, draw attention to actions, and make the page look polished and modern.

You can apply CSS to a `<button>` element the same way you apply it to any other HTML element. You can use the `style` attribute for quick inline styles, or a CSS class in a `<style>` block for reusable, cleaner code.

### Example 1 — Inline Style (Quick Method)

```html
<button style="background-color: green; color: white; padding: 10px 20px; font-size: 16px;">
  Green Button
</button>
```

**Expected output:**
A green button with white text, some padding around the label, and a readable font size.

**CSS property-by-property explanation:**

- `background-color: green` — Sets the button's background fill colour to green.
- `color: white` — Sets the text colour inside the button to white (so it's readable on the green background).
- `padding: 10px 20px` — Adds 10px of space above and below the text, and 20px on the left and right. This makes the button larger and more comfortable to click.
- `font-size: 16px` — Sets the size of the button label text to 16 pixels, making it easy to read.

### Example 2 — CSS Class (Reusable Method)

When you have multiple buttons on a page, it is much cleaner to define a CSS class once and apply it to each button, rather than typing inline styles repeatedly.

```html
<!DOCTYPE html>
<html>
<head>
<style>
  .mybutton {
    background-color: #4CAF50;  /* A medium green */
    color: white;
    padding: 12px 24px;
    border: none;
    font-size: 16px;
    cursor: pointer;
    border-radius: 5px;
  }

  .mybutton:hover {
    background-color: #45a049;  /* Slightly darker green on hover */
  }
</style>
</head>
<body>

  <button class="mybutton">Save</button>
  <button class="mybutton">Submit</button>
  <button class="mybutton">Continue</button>

</body>
</html>
```

**Expected output:**
Three identical green buttons labelled "Save", "Submit", and "Continue". When you hover your mouse over any of them, the colour gets slightly darker, giving visual feedback that the button is interactive.

**New CSS properties explained:**

- `border: none` — Removes the default grey border/outline that browsers draw around buttons.
- `cursor: pointer` — Changes the mouse cursor to a hand (👆) when hovering over the button, which signals to users that it is clickable.
- `border-radius: 5px` — Rounds the corners of the button slightly, giving it a modern, friendly appearance.
- `.mybutton:hover` — The `:hover` part is a CSS "pseudo-class". It applies styles only when the user's mouse is hovering over the element. This creates an interactive visual response without any JavaScript.

> **Real-world connection:** The "hover effect" (button darkens on mouse-over) is one of the most universally used UI patterns on every website and app. Always include it when styling buttons, because it signals to users that the button is interactive.

---

## Part 3 — The `disabled` Attribute

### What Does "Disabled" Mean?

Sometimes you want a button to exist visually on the page but you do **not** want users to be able to click it. Common real-world situations for this:

- A "Submit" button that should only be active after a user fills in a required field.
- A "Pay Now" button that is locked until the user agrees to terms and conditions.
- A feature that is not yet available (e.g., "Download — Coming Soon").

The `disabled` attribute achieves this. When applied to a `<button>`, it makes the button visually faded (greyed out) and completely unresponsive to clicks.

### Syntax

```html
<button disabled>Disabled Button</button>
```

**Expected output:**
A greyed-out button labelled "Disabled Button". Clicking it does nothing — no action fires, no page changes.

> **Note:** The `disabled` attribute is a **boolean attribute** — it has no value. You simply write the word `disabled` inside the opening tag. The browser reads its presence as "this button is disabled".

### Side-by-Side Comparison

```html
<!-- Normal clickable button -->
<button>Active Button</button>

<!-- Disabled, unclickable button -->
<button disabled>Disabled Button</button>
```

**Expected output:**
- "Active Button" appears in the normal button style and responds to clicks.
- "Disabled Button" appears faded/greyed out and does not respond to clicks.

> **Thinking prompt:** If you inspect a disabled button with browser developer tools, you will see its colour is typically a lighter grey. This is the browser's built-in visual cue to tell the user "this button is not available right now." Browsers do this automatically — you do not need to set the colour yourself.

---

## Part 4 — Buttons with JavaScript (`onclick`)

### What Is `onclick`?

`onclick` is an **HTML event attribute**. It lets you define a small piece of JavaScript that should run when the user clicks the button.

> **Analogy:** Think of `onclick` as a set of instructions you tape to the button before handing it to someone. "When you press this button, do the following: show an alert message."

You do not need to know JavaScript to use this in a basic way — you just need to know one simple JavaScript function: `alert()`.

### What Is `alert()`?

`alert()` is a built-in JavaScript function that pops up a small dialogue box in the browser with a message inside it. It is perfect for beginners learning buttons because it gives instant, visible feedback when a button is clicked.

### Syntax

```html
<button onclick="alert('Hello!')">Click Me</button>
```

**Expected output:**
When you click the "Click Me" button, a pop-up dialogue box appears with the message "Hello!" inside it. There is an "OK" button in the dialogue to dismiss it.

### Line-by-Line Explanation

- `<button` — Opens the button element.
- `onclick="alert('Hello!')"` — This is the event attribute. The value `"alert('Hello!')"` is JavaScript code that will execute when the button is clicked. `alert()` shows a pop-up message, and `'Hello!'` is the text to display inside it.
- `>Click Me</button>` — The button label and the closing tag.

> **Notice the quotes:** The `onclick` value uses double quotes on the outside (`onclick="..."`) and single quotes inside the JavaScript (`alert('Hello!')`). This is necessary because if you used double quotes inside, the browser would get confused about where the attribute value ends. Always use single quotes inside `onclick` when you have text.

### More Examples

```html
<!-- Alert with a custom message -->
<button onclick="alert('Welcome to my website!')">Say Hello</button>

<!-- Alert using a variable-like expression -->
<button onclick="alert('You clicked the button!')">Click Me</button>
```

**Expected outputs:**
- Clicking "Say Hello" opens a pop-up saying: "Welcome to my website!"
- Clicking "Click Me" opens a pop-up saying: "You clicked the button!"

> **A note on JavaScript:** `onclick` and `alert()` are just a small taste of JavaScript. In a full JavaScript course you will learn to do far more powerful things when buttons are clicked — things like changing the content of a page, validating form data, fetching data from a server, and much more. For now, mastering the HTML button structure and attributes is the goal.

---

## Part 5 — Button Types

### Why Does Type Matter?

The `type` attribute tells the browser exactly **what role** the button plays. This is especially important when buttons are placed inside HTML forms, because without the correct `type`, the browser may behave in unexpected ways — for example, accidentally submitting a form when you only intended to run a script.

There are exactly **three** valid values for the `type` attribute on a button:

| `type` value | What it does |
|---|---|
| `type="button"` | A normal clickable button. Does nothing by default. Used when you want to attach JavaScript or a custom action. |
| `type="submit"` | Submits the form it is inside. Sends all the form's input data to the server (or the URL defined in `action`). |
| `type="reset"` | Resets all form fields back to their original (empty or default) values. |

### Example — All Three Button Types

```html
<button type="button">Normal Button</button>
<button type="submit">Submit</button>
<button type="reset">Reset</button>
```

**Expected output:**
Three buttons side by side. Clicking "Normal Button" does nothing (unless `onclick` is added). "Submit" and "Reset" work as described when placed inside a form.

### Deep Dive: Buttons Inside a Form

This is where `type` matters most. Here is a working form example:

```html
<form action="/action_page.php">
  First name: <input type="text" name="fname">
  <button type="submit">Submit</button>
  <button type="reset">Reset Form</button>
</form>
```

**What each part does:**

- `<form action="/action_page.php">` — Opens a form. The `action` attribute specifies where the data goes when submitted (a server-side script at `/action_page.php`). You will learn forms fully in a later lesson.
- `<input type="text" name="fname">` — A text box where the user types their first name.
- `<button type="submit">Submit</button>` — When clicked, takes all the data typed into the form and sends it to `/action_page.php`. The page will then navigate to that URL with the form data attached.
- `<button type="reset">Reset Form</button>` — When clicked, clears the text box back to empty, as if the user had not typed anything.

> **Important rule:** Always specify `type` on your buttons. If a button is inside a form and you forget to set `type`, most browsers will default it to `type="submit"`, which means clicking any button in the form will accidentally submit it. This is a very common beginner bug.

### Why Use `type="button"` Outside a Form?

When a button is **not** inside a form, using `type="button"` is still best practice for clarity. It signals to anyone reading your code — including your future self — that this button is meant to trigger a JavaScript action rather than submit any data.

```html
<!-- Best practice: explicit type even outside a form -->
<button type="button" onclick="alert('Saved!')">Save Progress</button>
```

---

## Part 6 — Putting It All Together: Button Attribute Summary

Here is a complete summary of every `<button>` attribute covered in this lesson:

| Attribute | What It Does | Example |
|---|---|---|
| *(none)* | Creates a basic button with a label | `<button>Click</button>` |
| `type="button"` | Normal button — does nothing by default | `<button type="button">Click</button>` |
| `type="submit"` | Submits the surrounding form | `<button type="submit">Submit</button>` |
| `type="reset"` | Resets all form fields in the surrounding form | `<button type="reset">Reset</button>` |
| `disabled` | Makes the button unclickable and visually greyed out | `<button disabled>Locked</button>` |
| `onclick="..."` | Runs JavaScript when the button is clicked | `<button onclick="alert('Hi')">Hi</button>` |
| `class="..."` | Assigns a CSS class name for styling | `<button class="mybtn">Click</button>` |

---

## Part 7 — Guided Practice Exercises

### Exercise 1 — Your First Button

**Objective:** Create a basic button and understand its default appearance.

**Steps:**
1. Create a new file called `button_test.html`.
2. Set up the basic HTML structure with `<!DOCTYPE html>`, `<html>`, `<head>`, and `<body>`.
3. Inside `<body>`, add a button with the label "Click Me".
4. Save and open in a browser.

**Code:**
```html
<!DOCTYPE html>
<html>
<body>

  <button>Click Me</button>

</body>
</html>
```

**Expected output:**
A plain grey button labelled "Click Me" appears. Clicking it does nothing yet.

**Self-check questions:**
- Does the button appear?
- What happens when you click it?
- What does it look like if you change "Click Me" to "Hello World"?

---

### Exercise 2 — Add an Alert on Click

**Objective:** Use `onclick` to make a button show a message.

**Scenario:** You are building a greeting card webpage. Add a button that, when clicked, says "Happy Birthday!" in a pop-up.

**Code:**
```html
<!DOCTYPE html>
<html>
<body>

  <h2>Birthday Card</h2>
  <p>Click the button to reveal your message!</p>
  <button type="button" onclick="alert('Happy Birthday! Wishing you all the best!')">
    Reveal Message
  </button>

</body>
</html>
```

**Expected output:**
A page with a heading, a paragraph, and a "Reveal Message" button. Clicking the button opens a pop-up alert with the birthday message.

**What-if challenge:** Change the alert message to say your own name. What do you need to change in the code?

---

### Exercise 3 — Styled Button Set

**Objective:** Apply CSS to create three visually distinct buttons.

**Scenario:** You are building a simple dashboard. Create three buttons: one for confirming an action (green), one for cancelling (red), and one that is currently unavailable (disabled/grey).

**Code:**
```html
<!DOCTYPE html>
<html>
<head>
<style>
  .btn-confirm {
    background-color: #28a745;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    font-size: 15px;
    cursor: pointer;
  }

  .btn-cancel {
    background-color: #dc3545;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    font-size: 15px;
    cursor: pointer;
  }

  .btn-confirm:hover { background-color: #218838; }
  .btn-cancel:hover  { background-color: #c82333; }
</style>
</head>
<body>

  <h2>Order Confirmation</h2>
  <button class="btn-confirm" type="button" onclick="alert('Order confirmed!')">Confirm Order</button>
  <button class="btn-cancel"  type="button" onclick="alert('Order cancelled.')">Cancel Order</button>
  <button disabled>Processing...</button>

</body>
</html>
```

**Expected output:**
- A green "Confirm Order" button. Clicking it shows "Order confirmed!"
- A red "Cancel Order" button. Clicking it shows "Order cancelled."
- A greyed-out "Processing..." button that cannot be clicked.

**Self-check questions:**
- What does `cursor: pointer` do and why is it important?
- Why is the "Processing..." button disabled?
- Can you change the green to blue (`#007bff`)?

---

### Exercise 4 — Submit and Reset Buttons in a Form

**Objective:** Use button types correctly inside an HTML form.

**Scenario:** Create a simple feedback form with a name field, a "Submit" button, and a "Reset" button.

**Code:**
```html
<!DOCTYPE html>
<html>
<body>

  <h2>Feedback Form</h2>

  <form action="#">
    <label for="name">Your Name:</label><br>
    <input type="text" id="name" name="name" placeholder="Enter your name"><br><br>

    <label for="feedback">Your Feedback:</label><br>
    <textarea id="feedback" name="feedback" rows="4" cols="40"
      placeholder="Type your feedback here..."></textarea><br><br>

    <button type="submit">Submit Feedback</button>
    <button type="reset">Clear Form</button>
  </form>

</body>
</html>
```

**Expected output:**
A form with a name field and a feedback text area. Clicking "Submit Feedback" submits the form (in this case to `#`, which means the same page). Clicking "Clear Form" erases everything the user typed.

**Self-check questions:**
- What does `type="reset"` actually do when you click it? Try typing something and then clicking it.
- What would happen if you removed `type="submit"` from the submit button?
- Why is `action="#"` used here instead of a real URL?

---

## Part 8 — Mini Project: Interactive Quiz Button Panel

In this mini project, you will build a single-question quiz page that uses buttons to let the user select an answer. The project combines styled buttons, `onclick` alerts, and a disabled button to simulate a real quiz interface.

### Stage 1 — Page Structure

Create a new file called `quiz.html` and build the basic page:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Quick Quiz</title>
<style>
  body {
    font-family: Arial, sans-serif;
    max-width: 500px;
    margin: 40px auto;
    padding: 20px;
  }

  h1 { color: #333; }

  .question {
    background-color: #f4f4f4;
    padding: 20px;
    border-radius: 8px;
    margin-bottom: 20px;
  }

  .answer-btn {
    display: block;
    width: 100%;
    padding: 12px;
    margin: 8px 0;
    font-size: 15px;
    border: 2px solid #ccc;
    border-radius: 6px;
    background-color: white;
    cursor: pointer;
    text-align: left;
  }

  .answer-btn:hover {
    background-color: #e8f0fe;
    border-color: #4285f4;
  }

  .btn-submit {
    background-color: #4285f4;
    color: white;
    padding: 12px 30px;
    border: none;
    border-radius: 6px;
    font-size: 16px;
    cursor: pointer;
    margin-top: 10px;
  }

  .btn-submit:hover { background-color: #3367d6; }

  .btn-restart {
    background-color: #f1f1f1;
    padding: 10px 20px;
    border: 1px solid #ccc;
    border-radius: 6px;
    font-size: 14px;
    cursor: pointer;
    margin-top: 5px;
  }
</style>
</head>
<body>

  <h1>Quick Quiz 🧠</h1>

</body>
</html>
```

**Milestone output:** A clean, centred white page with the heading "Quick Quiz 🧠".

---

### Stage 2 — Add the Question and Answer Buttons

Inside `<body>`, after the `<h1>`, add the quiz question and four answer buttons:

```html
  <div class="question">
    <p><strong>Question:</strong> What does HTML stand for?</p>
  </div>

  <button class="answer-btn" type="button"
    onclick="alert('❌ Not quite! That stands for Hyper Transfer Protocol.')">
    A) Hyper Transfer Protocol Language
  </button>

  <button class="answer-btn" type="button"
    onclick="alert('✅ Correct! HTML = HyperText Markup Language. Well done!')">
    B) HyperText Markup Language
  </button>

  <button class="answer-btn" type="button"
    onclick="alert('❌ Not quite! Markup is not the same as Markdown.')">
    C) HyperText Markdown Language
  </button>

  <button class="answer-btn" type="button"
    onclick="alert('❌ Not quite! Home Tool Markup Language is not a real thing.')">
    D) Home Tool Markup Language
  </button>
```

**Milestone output:** A question block followed by four full-width answer buttons. Clicking each button shows a message telling the user whether they were correct or not.

---

### Stage 3 — Add Submit and Restart Buttons

Below the answer buttons, add a disabled "Submit Answer" button and a "Restart Quiz" button:

```html
  <br>
  <button class="btn-submit" type="button" disabled>Submit Answer</button>
  <br>
  <button class="btn-restart" type="button"
    onclick="alert('Restarting! (In a real quiz, the page would reload here.)')">
    🔄 Restart Quiz
  </button>
```

**Milestone output:** A blue "Submit Answer" button (greyed out and disabled) and a "Restart Quiz" button. Clicking Restart shows an alert.

---

### Complete Final Code

```html
<!DOCTYPE html>
<html>
<head>
  <title>Quick Quiz</title>
<style>
  body {
    font-family: Arial, sans-serif;
    max-width: 500px;
    margin: 40px auto;
    padding: 20px;
  }
  h1 { color: #333; }
  .question {
    background-color: #f4f4f4;
    padding: 20px;
    border-radius: 8px;
    margin-bottom: 20px;
  }
  .answer-btn {
    display: block;
    width: 100%;
    padding: 12px;
    margin: 8px 0;
    font-size: 15px;
    border: 2px solid #ccc;
    border-radius: 6px;
    background-color: white;
    cursor: pointer;
    text-align: left;
  }
  .answer-btn:hover {
    background-color: #e8f0fe;
    border-color: #4285f4;
  }
  .btn-submit {
    background-color: #4285f4;
    color: white;
    padding: 12px 30px;
    border: none;
    border-radius: 6px;
    font-size: 16px;
    cursor: pointer;
    margin-top: 10px;
  }
  .btn-submit:hover { background-color: #3367d6; }
  .btn-restart {
    background-color: #f1f1f1;
    padding: 10px 20px;
    border: 1px solid #ccc;
    border-radius: 6px;
    font-size: 14px;
    cursor: pointer;
    margin-top: 5px;
  }
</style>
</head>
<body>

  <h1>Quick Quiz 🧠</h1>

  <div class="question">
    <p><strong>Question:</strong> What does HTML stand for?</p>
  </div>

  <button class="answer-btn" type="button"
    onclick="alert('❌ Not quite! That stands for Hyper Transfer Protocol.')">
    A) Hyper Transfer Protocol Language
  </button>

  <button class="answer-btn" type="button"
    onclick="alert('✅ Correct! HTML = HyperText Markup Language. Well done!')">
    B) HyperText Markup Language
  </button>

  <button class="answer-btn" type="button"
    onclick="alert('❌ Not quite! Markup is not the same as Markdown.')">
    C) HyperText Markdown Language
  </button>

  <button class="answer-btn" type="button"
    onclick="alert('❌ Not quite! Home Tool Markup Language is not a real thing.')">
    D) Home Tool Markup Language
  </button>

  <br>
  <button class="btn-submit" type="button" disabled>Submit Answer</button>
  <br>
  <button class="btn-restart" type="button"
    onclick="alert('Restarting! (In a real quiz, the page would reload here.)')">
    🔄 Restart Quiz
  </button>

</body>
</html>
```

**Final expected output:**
A centred quiz page with a styled question box, four full-width answer buttons that each pop up a right/wrong message on click, a blue disabled "Submit Answer" button, and a "Restart Quiz" button.

### Reflection Questions

1. Why is the "Submit Answer" button disabled? In a real quiz, when would you want to enable it?
2. Why do all four answer buttons use `type="button"` even though they are not inside a `<form>` element?
3. What would happen if you removed the `cursor: pointer` CSS property? Try it!
4. Could you turn one of the answer buttons green and make it pulse when correct? What CSS would you start with?

### Optional Extension Challenges

1. Add a second question below the first with its own answer buttons.
2. Style the correct-answer button differently (e.g., a light green border when it is the right answer).
3. Add a "Score: 0/1" text below the quiz that updates when the correct answer is clicked. (Hint: this requires JavaScript — a preview of what's coming!)
4. Make the page mobile-friendly by changing `max-width: 500px` to a percentage value.

---

## Part 9 — Common Beginner Mistakes

### Mistake 1 — Forgetting the Closing `</button>` Tag

**Wrong:**
```html
<button>Click Me
```

**Why it is wrong:** Without the closing tag, the browser's HTML parser may treat everything after the button as still being inside the button, leading to bizarre visual results where your entire page appears to be one giant button.

**Correct:**
```html
<button>Click Me</button>
```

---

### Mistake 2 — Using Double Quotes Inside `onclick`

**Wrong:**
```html
<button onclick="alert("Hello!")">Click Me</button>
```

**Why it is wrong:** The double quotes around `"Hello!"` end the `onclick` attribute early. The browser reads `onclick="alert("` as the full attribute, then gets confused by `Hello!` floating in the middle of the tag. This causes a syntax error and the button will not work.

**Correct — use single quotes inside the double quotes:**
```html
<button onclick="alert('Hello!')">Click Me</button>
```

---

### Mistake 3 — Not Specifying `type` Inside a Form

**Wrong:**
```html
<form action="/submit">
  <input type="text" name="email">
  <button>Click for help</button>  <!-- No type! -->
  <button type="submit">Submit</button>
</form>
```

**Why it is wrong:** The first button has no `type`. Inside a form, the default button type is `submit`. So clicking "Click for help" will accidentally submit the form — not what you wanted at all.

**Correct:**
```html
<form action="/submit">
  <input type="text" name="email">
  <button type="button" onclick="alert('Help: Enter your email address.')">Click for help</button>
  <button type="submit">Submit</button>
</form>
```

---

### Mistake 4 — Putting Interactive Content Inside a Disabled Button

**Wrong:**
```html
<button disabled onclick="alert('Hi')">Click Me</button>
```

**Why it is confusing:** The `disabled` attribute prevents the button from firing any event, including `onclick`. Adding `onclick` to a disabled button is pointless — nothing will happen. It also misleads anyone reading your code into thinking the button does something.

**Correct:**
If a button should eventually be enabled, keep it disabled and only add `onclick` when you remove `disabled` (which is done in JavaScript).

```html
<!-- While waiting: -->
<button disabled>Please wait...</button>

<!-- After an action completes (JavaScript would remove disabled): -->
<button type="button" onclick="alert('Ready!')">Continue</button>
```

---

### Mistake 5 — Using a `<div>` or `<a>` Tag as a Fake Button

Some beginners try to style a `<div>` or `<a>` to look like a button instead of using the actual `<button>` element.

**Wrong:**
```html
<div style="background: blue; color: white; padding: 10px;" onclick="alert('Hi')">
  Click Me
</div>
```

**Why it is wrong:** A `<div>` is not semantically a button. It is not keyboard-accessible (you cannot Tab to it and press Enter), it is not announced as a button to screen readers, and it does not behave like a button in all browsers.

**Correct:**
```html
<button type="button" style="background: blue; color: white; padding: 10px;"
  onclick="alert('Hi')">
  Click Me
</button>
```

Always use `<button>` for clickable actions. Use `<a>` only for navigation to a URL.

---

### Mistake 6 — Adding `type="submit"` to a Button Outside a Form

**Wrong (conceptually confusing):**
```html
<!-- There is no form here -->
<button type="submit" onclick="alert('Done!')">Save</button>
```

**Why it is confusing:** `type="submit"` is only meaningful inside a `<form>`. Outside a form, it is equivalent to `type="button"` in most browsers, but it misleads anyone reading the code into thinking there is a form being submitted.

**Correct:**
```html
<button type="button" onclick="alert('Done!')">Save</button>
```

---

## Part 10 — Reflection Questions

Think through these questions to confirm your understanding has solidified:

1. What HTML tag do you use to create a button?

2. What is the difference between `type="button"` and `type="submit"`?

3. You add `disabled` to a button. What changes visually and functionally?

4. A button has `onclick="alert('test')"` but is also `disabled`. What happens when you click it?

5. Inside a form, what is the default `type` of a button if you do not specify one? Why is this dangerous?

6. You want a button to clear all the text a user has typed into a form. Which `type` value achieves this?

7. What CSS property changes the mouse cursor to a hand pointer when hovering over a button?

8. Why should you use `<button>` rather than styling a `<div>` to look like a button?

9. You write `onclick="alert("Welcome")"` — why does this cause a bug, and how do you fix it?

10. What does the CSS `:hover` pseudo-class on a button do?

---

## Part 11 — Completion Checklist

Use this to confirm you have fully mastered Lesson 20:

- [ ] I can create a basic `<button>` element with a label
- [ ] I understand that a bare button does nothing without a `type`, `onclick`, or form context
- [ ] I can style a button with CSS using both inline `style` and a CSS class
- [ ] I can apply a `hover` effect to make a button darken on mouse-over
- [ ] I can use the `disabled` attribute to make a button unclickable
- [ ] I can use `onclick` to show an `alert()` message when a button is clicked
- [ ] I understand the three `type` values: `button`, `submit`, and `reset`
- [ ] I know why specifying `type` inside a form is important
- [ ] I can correctly place `submit` and `reset` buttons inside a form
- [ ] I completed all four guided exercises
- [ ] I built the quiz mini project
- [ ] I can identify and fix the six common button mistakes

---

## Lesson Summary

The HTML `<button>` element is the primary tool for user interaction on a webpage. You create a button by writing `<button>Label</button>` — the text between the tags becomes the clickable label.

By itself, a `<button>` does nothing when clicked. You must connect it to an action by: giving it a `type` attribute for form-related behaviour (`submit` sends the form, `reset` clears it), or adding an `onclick` attribute to run JavaScript (like `alert()`) when clicked.

The `disabled` attribute greyed out and locks the button completely — no clicks will register. It is used to prevent actions that are not yet available to the user.

Buttons are styled with CSS just like any other HTML element. The `background-color`, `color`, `padding`, `border`, `border-radius`, and `cursor: pointer` properties are the most commonly used. A `:hover` rule adds a visual response when the user's mouse is over the button.

Always specify `type` on buttons that live inside forms. Without it, browsers default to `type="submit"`, which can accidentally submit your form when the user clicks any button. Use `type="button"` for buttons that run JavaScript actions, `type="submit"` to send form data, and `type="reset"` to clear form fields.

Finally, always use the `<button>` element for clickable actions — not `<div>` or `<a>` — because `<button>` is semantically correct, accessible to keyboard users, and understood by screen readers.

---

*Sources: W3Schools HTML Buttons Tutorial — https://www.w3schools.com/html/html_buttons.asp*
