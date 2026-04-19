---
render_with_liquid: false
title: "Lesson 31: HTML Forms — Collecting Input from Users"
nav_order: 31
---

# Lesson 31: HTML Forms — Collecting Input from Users

---

## Lesson Introduction

Almost every useful website in the world has a form. When you log in to your email, you fill in a form. When you sign up for a new account, you fill in a form. When you search on Google, you type into a form. When you place an online order, you fill in your address in a form.

**Forms are how websites collect information from users.**

Without forms, websites can only show information — they cannot receive any. Forms are what turn a one-way display page into a two-way interactive experience.

In this lesson, you will learn everything about HTML forms from the ground up. You will learn how to create text boxes, password fields, checkboxes, radio buttons, drop-down menus, file uploaders, submit buttons, and much more. You will also learn how to use form attributes and input attributes to control exactly how forms behave.

By the end of this lesson, you will be able to build real, complete, professional-looking forms for any purpose — registration, login, surveys, contact pages, and more.

---

## Prerequisite Concepts

Before we start, let's make sure you understand a few important ideas that will appear throughout this lesson.

### What is a "Server"?

When a form is submitted, where does the data go? It goes to a **server** — a computer that is always running and waiting to receive data. The server is usually running a programming language like PHP, Python, or Node.js that processes the form data (for example, saving it to a database or sending an email).

In this lesson, we focus on the **HTML side** of forms — building the form itself. You do not need a server to practise. You can simply observe how forms work in the browser.

### What Does "Submit" Mean?

Submitting a form means sending the form data somewhere. When you click a "Submit" or "Send" button on a form, the browser collects all the data the user typed or selected and sends it to a destination (usually a server).

### What is an "Attribute"?

An attribute is extra information added inside an HTML opening tag to control how the element behaves. For example:

```html
<input type="text" name="username" placeholder="Enter your name">
```

Here, `type`, `name`, and `placeholder` are all attributes of the `<input>` element. Each one changes how the input field works.

---

## Part 1: The `<form>` Element — The Container for Everything

### What is the `<form>` Element?

The `<form>` element is the container that wraps around all the inputs, labels, and buttons in your form. Just like `<ul>` contains list items, `<form>` contains all the fields the user will interact with.

**Analogy:** Think of the `<form>` element as an envelope. The envelope itself does not contain any message yet — but it is the container that will hold everything and be addressed (to a server) before being sent.

### The Basic `<form>` Structure

```html
<form action="/submit-page.php" method="post">
  <!-- Form fields go here -->
</form>
```

Every important detail is in the opening tag. Let's look at the two most important attributes:

### The `action` Attribute

The `action` attribute tells the browser **where to send the form data** when the form is submitted.

```html
<form action="/submit-page.php">
```

- The value is a URL or a file path.
- When the user clicks Submit, the browser navigates to `/submit-page.php` and sends all the form data there.
- If you leave `action` out or set it to `""`, the form data is sent to the **same page** the form is on.

```html
<!-- Sends data to a specific page -->
<form action="/register.php">

<!-- Sends data to itself (same page) -->
<form action="">
```

### The `method` Attribute

The `method` attribute tells the browser **how to send the data**. There are two options: `GET` and `POST`.

| Method | What it does | When to use it |
|---|---|---|
| `GET` | Sends data as part of the URL (visible in the browser address bar) | For search forms, filters, anything non-sensitive |
| `POST` | Sends data hidden inside the request body (not visible in the URL) | For passwords, personal info, registrations, anything sensitive |

**Example of GET — data visible in URL:**
```html
<form action="/search" method="get">
  <input type="text" name="query">
  <button type="submit">Search</button>
</form>
```
After submitting with the word "cats", the URL becomes: `/search?query=cats`

**Example of POST — data hidden:**
```html
<form action="/login" method="post">
  <input type="password" name="password">
  <button type="submit">Login</button>
</form>
```
The password is NOT visible in the URL. It is sent securely inside the request.

> **Rule of thumb:** Always use `method="post"` for anything that involves personal information, passwords, or financial data. Use `method="get"` only for non-sensitive things like search queries.

### The `target` Attribute

The `target` attribute controls where the response page (the page after the form is submitted) opens.

| Value | What it does |
|---|---|
| `_self` | Opens in the same tab (default behaviour) |
| `_blank` | Opens in a new tab |
| `_parent` | Opens in the parent frame |
| `_top` | Opens in the full body of the window |

```html
<form action="/result.php" method="post" target="_blank">
  <!-- Opens the result in a new tab -->
</form>
```

### The `autocomplete` Attribute

The `autocomplete` attribute controls whether the browser should suggest previously typed values when a user starts typing in a field.

```html
<form action="/register.php" method="post" autocomplete="on">
  <!-- Browser may suggest saved names, emails, etc. -->
</form>

<form action="/login.php" method="post" autocomplete="off">
  <!-- Browser will NOT suggest saved values (useful for security) -->
</form>
```

### The `novalidate` Attribute

By default, the browser will check form inputs before submitting (for example, making sure an email field contains `@`). The `novalidate` attribute turns off this automatic checking.

```html
<form action="/process.php" method="post" novalidate>
  <!-- Browser skips built-in validation -->
</form>
```

### Simple Example 1 — A Minimal Form

```html
<!DOCTYPE html>
<html>
<head>
  <title>My First Form</title>
</head>
<body>

  <h2>Contact Us</h2>

  <form action="/send-message.php" method="post">
    <!-- Inputs will go here -->
    <p>Form fields will appear here.</p>
    <button type="submit">Send</button>
  </form>

</body>
</html>
```

**Expected Output:** A heading "Contact Us", a paragraph of text, and a "Send" button visible on the page.

---

## Part 2: The `<input>` Element — The Most Important Form Element

### What is `<input>`?

`<input>` is the most versatile HTML element. It can create many different types of form fields — text boxes, password fields, checkboxes, radio buttons, file uploaders, date pickers, colour pickers, and more — all depending on the value of its `type` attribute.

`<input>` is a **self-closing** element — it has no closing tag:

```html
<input type="text" name="username">
```

The `type` attribute determines what kind of input field is displayed.

---

## Part 3: The `<label>` Element — Naming Your Fields

Before we look at all the input types, you must understand the `<label>` element. Every input field should have a label — a visible text description that tells the user what to type.

### Why Use `<label>`?

- It makes forms accessible (screen readers can read labels aloud for visually impaired users).
- Clicking a label automatically focuses (activates) its associated input field — great for usability.
- It makes the form readable and understandable.

### How to Connect a `<label>` to an `<input>`

Use the `for` attribute on the label and the `id` attribute on the input. They must match:

```html
<label for="username">Username:</label>
<input type="text" id="username" name="username">
```

- `for="username"` — This label belongs to the input with `id="username"`.
- `id="username"` — The unique ID of this input field.
- `name="username"` — The name used when sending data to the server (the "key" in the key-value pair).

**Expected Output:** The text "Username:" appears next to a text input box. Clicking the word "Username:" moves the cursor into the input box.

> **Important difference — `id` vs `name`:**
> - `id` is used to connect the label to the input inside the HTML page.
> - `name` is the key sent to the server. For example, if `name="username"` and the user types "Chidi", the server receives `username=Chidi`.

---

## Part 4: All Input Types

Now let's go through every input type systematically.

### `type="text"` — Single-line Text Input

The most basic input. Creates a single-line text box.

```html
<form>
  <label for="fname">First Name:</label><br>
  <input type="text" id="fname" name="firstname"><br>

  <label for="lname">Last Name:</label><br>
  <input type="text" id="lname" name="lastname">
</form>
```

**Expected Output:** Two text boxes with labels above each one. The user can type freely into each box.

**Key attributes often used with `type="text"`:**

| Attribute | What it does | Example |
|---|---|---|
| `value` | Pre-fills the field with a default value | `value="John"` |
| `placeholder` | Shows greyed-out hint text inside the field | `placeholder="Enter your name"` |
| `maxlength` | Limits how many characters the user can type | `maxlength="50"` |
| `size` | Sets the visible width of the input (in characters) | `size="30"` |
| `readonly` | User can see but not edit the value | `readonly` |
| `disabled` | Field is greyed out and unusable | `disabled` |
| `required` | Form cannot be submitted if this field is empty | `required` |

**Example with common attributes:**
```html
<label for="city">City:</label>
<input type="text" id="city" name="city"
       placeholder="Enter your city"
       maxlength="100"
       required>
```

**Expected Output:** A text box with greyed-out hint text "Enter your city". If the user tries to submit the form without filling this field, the browser shows an error.

---

### `type="password"` — Password Input

Creates a text box where typed characters are hidden (shown as dots or asterisks).

```html
<form>
  <label for="pwd">Password:</label><br>
  <input type="password" id="pwd" name="password">
</form>
```

**Expected Output:** A text box where everything the user types appears as `●●●●●` (dots). This protects passwords from being seen by onlookers.

> **Security Note:** `type="password"` only hides characters visually. To truly protect passwords, you must use `method="post"` on the form AND use HTTPS on your server. Never use `method="get"` with passwords.

---

### `type="submit"` — The Submit Button

Creates a button that submits the form.

```html
<form action="/process.php" method="post">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name"><br><br>
  <input type="submit" value="Register Now">
</form>
```

**Expected Output:** A clickable button with the text "Register Now". Clicking it sends the form data to `/process.php`.

- The `value` attribute sets the text on the button.
- If you leave out `value`, the button shows the default text "Submit".

---

### `type="reset"` — The Reset Button

Creates a button that clears all fields in the form back to their default values.

```html
<input type="reset" value="Clear Form">
```

**Expected Output:** A button labelled "Clear Form". Clicking it erases everything the user has typed.

> **Tip:** Use reset buttons carefully — users accidentally click them and lose all their work. Many modern forms leave out the reset button for this reason.

---

### `type="button"` — A General-Purpose Button

Creates a clickable button that does nothing by default. You need JavaScript to make it do something. (We will not use JavaScript here, but knowing it exists is important.)

```html
<input type="button" value="Click Me">
```

**Expected Output:** A button labelled "Click Me" that appears but does nothing unless JavaScript handles the click.

---

### `type="checkbox"` — Tick Boxes

Creates a small square box the user can tick or untick. Used when the user can select **multiple options at once**.

```html
<form>
  <p>Select your interests:</p>

  <input type="checkbox" id="coding" name="interest" value="coding">
  <label for="coding">Coding</label><br>

  <input type="checkbox" id="music" name="interest" value="music">
  <label for="music">Music</label><br>

  <input type="checkbox" id="sports" name="interest" value="sports">
  <label for="sports">Sports</label><br>

  <input type="submit" value="Submit">
</form>
```

**Expected Output:** Three tick-box options (Coding, Music, Sports). The user can tick any combination — none, some, or all.

**Key attribute:**
- `checked` — Pre-selects the checkbox when the page loads:

```html
<input type="checkbox" id="newsletter" name="newsletter" value="yes" checked>
<label for="newsletter">Subscribe to newsletter</label>
```

**Thinking Prompt:** What is the difference between `type="checkbox"` and `type="radio"`? With checkboxes, users can pick multiple options. With radio buttons (coming next), users can only pick one.

---

### `type="radio"` — Radio Buttons

Creates circular buttons where the user can only **select one option from a group**. All radio buttons in the same group must share the same `name` attribute.

```html
<form>
  <p>What is your gender?</p>

  <input type="radio" id="male" name="gender" value="male">
  <label for="male">Male</label><br>

  <input type="radio" id="female" name="gender" value="female">
  <label for="female">Female</label><br>

  <input type="radio" id="other" name="gender" value="other">
  <label for="other">Prefer not to say</label>
</form>
```

**Expected Output:** Three circular radio buttons. Selecting one automatically deselects any other. The user can only have one selected at a time.

**Why same `name`?** The browser groups radio buttons by their `name` attribute. All radio buttons with `name="gender"` form one group. Only one can be selected within a group.

**Pre-select one with `checked`:**
```html
<input type="radio" id="male" name="gender" value="male" checked>
```

---

### `type="email"` — Email Address Field

Creates a text box specifically for email addresses. The browser validates that the input contains an `@` symbol before allowing the form to submit.

```html
<label for="email">Email Address:</label>
<input type="email" id="email" name="email" placeholder="you@example.com" required>
```

**Expected Output:** A text box. If the user types "hello" (no `@`) and clicks Submit, the browser shows: "Please include an '@' in the email address."

On mobile devices, `type="email"` also shows a keyboard that includes `@` and `.com` for easier typing.

---

### `type="number"` — Number Input

Creates a number field with up/down arrow buttons (spinner). Only numbers can be entered.

```html
<label for="age">Your Age:</label>
<input type="number" id="age" name="age" min="1" max="120" value="18">
```

**Expected Output:** A field containing "18" with small up/down arrows. Users can only type numbers. The `min` and `max` attributes limit the range.

| Attribute | Meaning | Example |
|---|---|---|
| `min` | Minimum allowed value | `min="0"` |
| `max` | Maximum allowed value | `max="100"` |
| `step` | How much the value jumps when using the arrows | `step="5"` means jumps by 5 |
| `value` | Default value shown on load | `value="18"` |

---

### `type="range"` — Slider

Creates a sliding scale control. Good for ratings, volume, or any value within a range.

```html
<label for="rating">Rate our service (1-10):</label>
<input type="range" id="rating" name="rating" min="1" max="10" value="5">
```

**Expected Output:** A horizontal slider bar. The user drags it left or right to pick a value between 1 and 10. The slider starts in the middle (value 5).

---

### `type="date"` — Date Picker

Creates a date picker. The browser shows a calendar popup for selecting a date.

```html
<label for="birthday">Date of Birth:</label>
<input type="date" id="birthday" name="birthday">
```

**Expected Output:** A field that opens a calendar when clicked. The user selects a day, month, and year. The date is stored in `YYYY-MM-DD` format.

```html
<!-- With min and max dates -->
<input type="date" id="appt" name="appointment" min="2024-01-01" max="2025-12-31">
```

---

### `type="time"` — Time Picker

Creates a field for entering a time (hours and minutes).

```html
<label for="appttime">Appointment Time:</label>
<input type="time" id="appttime" name="appttime">
```

**Expected Output:** A field showing HH:MM with up/down controls for hours and minutes.

---

### `type="color"` — Colour Picker

Creates a colour picker control. The user clicks to open a colour selection panel.

```html
<label for="favcolor">Choose your favourite colour:</label>
<input type="color" id="favcolor" name="favcolor" value="#ff0000">
```

**Expected Output:** A small coloured square (default red). Clicking it opens a full colour picker panel. The value is always a hex colour code like `#ff0000`.

---

### `type="url"` — URL / Website Address Field

Creates a field for entering a URL. The browser validates that it starts with `http://` or `https://`.

```html
<label for="website">Your Website:</label>
<input type="url" id="website" name="website" placeholder="https://example.com">
```

**Expected Output:** A text field. If the user enters "google" (without `https://`) and submits, the browser shows an error asking for a valid URL.

---

### `type="tel"` — Telephone Number Field

Creates a field for phone numbers. Unlike `type="number"`, it allows dashes, spaces, and brackets — all common in phone numbers.

```html
<label for="phone">Phone Number:</label>
<input type="tel" id="phone" name="phone" placeholder="+234 800 000 0000">
```

**Expected Output:** A text box optimised for phone numbers. On mobile devices, it shows the numeric keyboard automatically.

---

### `type="search"` — Search Field

Creates a field specifically for search inputs. In some browsers it shows a small 'X' to clear the field.

```html
<label for="search">Search:</label>
<input type="search" id="search" name="search" placeholder="Search the site...">
```

---

### `type="file"` — File Upload Field

Creates a field that lets the user upload a file from their computer.

```html
<label for="cv">Upload Your CV:</label>
<input type="file" id="cv" name="cv">
```

**Expected Output:** A "Choose File" button. Clicking it opens the computer's file browser. The user selects a file.

**Important:** When using `type="file"`, the `<form>` must also have `enctype="multipart/form-data"`:

```html
<form action="/upload.php" method="post" enctype="multipart/form-data">
  <label for="photo">Upload Profile Photo:</label>
  <input type="file" id="photo" name="photo" accept="image/*">
  <input type="submit" value="Upload">
</form>
```

- `enctype="multipart/form-data"` — Required for file uploads. Without it, only the file name (not the actual file) gets sent.
- `accept="image/*"` — Filters the file browser to show only image files.

---

### `type="hidden"` — Hidden Field

Creates an invisible field. The user cannot see or change it, but the value is sent to the server when the form is submitted. Used to pass background data.

```html
<input type="hidden" name="user_id" value="12345">
```

**Expected Output:** Nothing visible on the page. But when the form is submitted, `user_id=12345` is sent along with the other form data.

**Real-world use:** Hidden fields are used to pass a session token, a product ID, or a page reference that the user should not be able to change but that the server needs to process the form correctly.

---

### `type="image"` — Image Submit Button

Creates an image that acts as a submit button.

```html
<input type="image" src="submit-btn.png" alt="Submit" width="100" height="40">
```

**Expected Output:** Your image appears. Clicking it submits the form.

---

### Summary Table of All Input Types

| Type | What it creates |
|---|---|
| `text` | Single-line text box |
| `password` | Text box where characters are hidden |
| `email` | Text box with email format validation |
| `number` | Number field with spinner arrows |
| `range` | Sliding scale |
| `date` | Date picker (calendar popup) |
| `time` | Time input |
| `color` | Colour picker |
| `url` | URL/website address field |
| `tel` | Telephone number field |
| `search` | Search box |
| `checkbox` | Tick box (multiple can be selected) |
| `radio` | Circle button (only one per group can be selected) |
| `file` | File upload button |
| `submit` | Button that submits the form |
| `reset` | Button that clears the form |
| `button` | Generic clickable button |
| `hidden` | Invisible field (not seen by user) |
| `image` | Image that acts as a submit button |

---

## Part 5: Other Important Form Elements

Beyond `<input>`, there are several other elements that create form controls.

### `<textarea>` — Multi-line Text Box

`<input type="text">` creates a single line. But what if you want the user to write a full paragraph? Use `<textarea>`.

```html
<label for="message">Your Message:</label><br>
<textarea id="message" name="message" rows="5" cols="40" placeholder="Type your message here..."></textarea>
```

**Expected Output:** A resizable multi-line text box, 5 rows tall and 40 columns wide. The user can type as much as they want, with line breaks.

Key attributes:

| Attribute | What it does |
|---|---|
| `rows` | Number of visible lines (height) |
| `cols` | Number of visible characters per line (width) |
| `placeholder` | Hint text inside the box |
| `maxlength` | Maximum number of characters allowed |
| `readonly` | User can read but not edit |
| `required` | Must not be empty before submitting |

> **Note:** Unlike `<input>`, `<textarea>` has a **closing tag** `</textarea>`. The default text content goes between the tags:
> ```html
> <textarea>This is default text inside the textarea</textarea>
> ```

---

### `<select>` — Drop-Down List

Creates a drop-down menu. The user clicks to open it and selects one option.

```html
<label for="country">Country:</label>
<select id="country" name="country">
  <option value="ng">Nigeria</option>
  <option value="gh">Ghana</option>
  <option value="ke">Kenya</option>
  <option value="za">South Africa</option>
</select>
```

**Expected Output:** A drop-down showing "Nigeria" (first option) by default. Clicking opens the list with all four countries. Selecting one closes the list.

**Key attributes on `<select>`:**

| Attribute | What it does |
|---|---|
| `name` | The name sent to the server |
| `size` | Shows multiple options as a list (not drop-down) |
| `multiple` | Allows selecting multiple options |
| `required` | Must have a selection before submitting |

**Making a pre-selected option:**
```html
<option value="ng" selected>Nigeria</option>
```
The `selected` attribute on an `<option>` makes it the default choice.

**Showing multiple visible options (not a dropdown):**
```html
<select name="languages" size="4" multiple>
  <option value="html">HTML</option>
  <option value="css">CSS</option>
  <option value="js">JavaScript</option>
  <option value="python">Python</option>
</select>
```

**Expected Output:** A list box showing all 4 options at once. Holding Ctrl (Windows) or Cmd (Mac) lets the user select multiple items.

---

### `<option>` and `<optgroup>` — Options and Groups

`<option>` defines each item inside a `<select>`. `<optgroup>` groups related options with a label.

```html
<select name="car">
  <optgroup label="African Cars">
    <option value="innoson">Innoson IVM</option>
    <option value="kiira">Kiira EV</option>
  </optgroup>
  <optgroup label="Japanese Cars">
    <option value="toyota">Toyota</option>
    <option value="honda">Honda</option>
  </optgroup>
</select>
```

**Expected Output:** A drop-down with options grouped under bolded, non-selectable headers "African Cars" and "Japanese Cars".

---

### `<datalist>` — Autocomplete Suggestions

`<datalist>` creates a list of suggested values for an `<input>` field. It is like a drop-down that also allows free typing.

```html
<label for="browser">Favourite Browser:</label>
<input list="browsers" id="browser" name="browser" placeholder="Type or choose...">

<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Safari">
  <option value="Edge">
  <option value="Opera">
</datalist>
```

**Expected Output:** A text field. When the user starts typing, a dropdown of matching suggestions appears. The user can also type something not in the list.

**Key connection:** The `list` attribute on `<input>` must match the `id` on `<datalist>`.

**Difference between `<select>` and `<datalist>`:**
- `<select>` forces the user to pick only from the given options.
- `<datalist>` suggests options but allows the user to type anything.

---

### `<button>` Element

The `<button>` element creates a clickable button. Unlike `<input type="button">`, the `<button>` element can contain HTML content (text, icons, images).

```html
<!-- A submit button using <button> -->
<button type="submit">Submit Form</button>

<!-- A reset button -->
<button type="reset">Clear</button>

<!-- A button with an icon (text emoji here) -->
<button type="submit">🚀 Launch</button>
```

**Expected Output:** A clickable button. The `type` attribute determines what it does:
- `type="submit"` — Submits the form (default if `type` is omitted inside a form).
- `type="reset"` — Resets all form fields.
- `type="button"` — Does nothing (for JavaScript).

> **Always specify `type` on `<button>` inside a form.** If you forget, the default is `type="submit"`, which might submit your form when you did not intend to.

---

### `<fieldset>` and `<legend>` — Grouping and Labelling Sections

`<fieldset>` groups related inputs together, drawing a visible box around them. `<legend>` gives the group a title that appears at the top of the box.

```html
<form action="/register.php" method="post">

  <fieldset>
    <legend>Personal Information</legend>
    <label for="fname">First Name:</label>
    <input type="text" id="fname" name="firstname"><br><br>
    <label for="email">Email:</label>
    <input type="email" id="email" name="email">
  </fieldset>

  <fieldset>
    <legend>Account Details</legend>
    <label for="username">Username:</label>
    <input type="text" id="username" name="username"><br><br>
    <label for="pwd">Password:</label>
    <input type="password" id="pwd" name="password">
  </fieldset>

  <button type="submit">Create Account</button>

</form>
```

**Expected Output:** Two visually separated sections, each inside a labelled box. "Personal Information" section contains name and email. "Account Details" section contains username and password.

**Why use `<fieldset>` and `<legend>`?**
- Makes long forms easier to navigate.
- Helps screen readers understand the form's structure.
- Groups logically related fields visually.

---

### `<output>` — Displaying Calculation Results

`<output>` displays the result of a calculation or user action. It updates dynamically with JavaScript.

```html
<form oninput="result.value = parseInt(a.value) + parseInt(b.value)">
  <input type="number" id="a" name="a" value="0"> +
  <input type="number" id="b" name="b" value="0"> =
  <output name="result" for="a b">0</output>
</form>
```

**Expected Output:** Two number fields and a result that updates live as you type. If you type 5 and 3, the output shows 8 immediately.

---

## Part 6: Important Input Attributes (The Full Set)

Input attributes give you precise control over how each field behaves. Here is a comprehensive reference.

### `name` — The Key Sent to the Server

Every input that needs to send data to the server **must have a `name` attribute**. Without `name`, the field's value will not be sent.

```html
<!-- This value WILL be sent: name="username" -->
<input type="text" name="username" value="Chidi">

<!-- This value will NOT be sent: no name attribute -->
<input type="text" value="Chidi">
```

When submitted, the server receives: `username=Chidi`

---

### `value` — Pre-filled Default Value

The `value` attribute sets what the field shows when the page first loads.

```html
<input type="text" name="country" value="Nigeria">
```

**Expected Output:** The text box already contains "Nigeria". The user can change it.

For checkboxes and radio buttons, `value` is the data sent to the server when the option is selected:
```html
<input type="checkbox" name="agree" value="yes"> I agree to the terms
```
If checked: sends `agree=yes`. If unchecked: sends nothing.

---

### `placeholder` — Hint Text Inside the Field

Shows light greyed-out text inside an empty field as a hint to the user. It disappears as soon as the user starts typing.

```html
<input type="email" name="email" placeholder="your.email@example.com">
```

**Expected Output:** The field shows `your.email@example.com` in grey. When the user clicks and types, the hint disappears.

> **Do not use `placeholder` as a replacement for `<label>`.** Placeholder text disappears when the user starts typing, leaving them with no reminder of what the field is for. Always use a visible `<label>` alongside your placeholder.

---

### `required` — Must Be Filled

When `required` is present, the browser will not allow the form to be submitted until this field has a value.

```html
<input type="text" name="name" required>
<input type="email" name="email" required>
```

**Expected Output:** If the user clicks Submit without filling in these fields, the browser highlights them and shows a message like "Please fill in this field."

---

### `readonly` — Can See But Cannot Edit

The user can read the value but cannot change it.

```html
<input type="text" name="userid" value="USER-00123" readonly>
```

**Expected Output:** A field showing "USER-00123" that the user cannot type into. The value IS still sent to the server when the form is submitted.

---

### `disabled` — Greyed Out and Unusable

The field is visible but completely non-interactive. The user cannot click, type, or select it. Unlike `readonly`, **disabled fields are NOT sent to the server**.

```html
<input type="text" name="offer_code" value="SUMMER2024" disabled>
```

**Expected Output:** A greyed-out field showing "SUMMER2024". The user cannot change it, and this value is NOT included when the form is submitted.

> **Key difference between `readonly` and `disabled`:**
> - `readonly` — User cannot edit, but value IS sent to server.
> - `disabled` — User cannot interact, and value is NOT sent to server.

---

### `maxlength` and `minlength` — Character Limits

```html
<!-- No more than 50 characters -->
<input type="text" name="title" maxlength="50">

<!-- Must have at least 8 characters -->
<input type="password" name="pwd" minlength="8" required>
```

`maxlength` silently stops the user from typing more than the limit. `minlength` triggers a browser error at submit time if the input is too short.

---

### `min` and `max` — Number/Date Range Limits

Used with `type="number"`, `type="date"`, `type="range"`, `type="time"`.

```html
<input type="number" name="quantity" min="1" max="99">
<input type="date" name="checkIn" min="2025-01-01">
```

---

### `step` — Jump Interval for Numbers and Ranges

Defines the legal interval between values.

```html
<!-- Only allows 0, 5, 10, 15, 20... -->
<input type="number" name="score" min="0" max="100" step="5">

<!-- Only allows even numbers -->
<input type="number" name="even" min="0" step="2">
```

---

### `autofocus` — Automatically Focus This Field

Moves the cursor into this field immediately when the page loads.

```html
<input type="text" name="search" autofocus placeholder="Start searching...">
```

**Expected Output:** When the page opens, the cursor is already inside the search box — the user can start typing immediately without clicking.

> Only one field per page should have `autofocus`.

---

### `autocomplete` — Browser Auto-fill Control

Controls whether the browser offers to auto-complete this specific field (independent of the `<form>` level `autocomplete`).

```html
<!-- Allow browser to suggest saved addresses -->
<input type="text" name="address" autocomplete="on">

<!-- Do NOT suggest anything for this field -->
<input type="password" name="newpassword" autocomplete="new-password">
```

---

### `multiple` — Allow Multiple Values

For `type="email"` and `type="file"`, allows entering multiple values separated by commas.

```html
<!-- User can type multiple emails separated by commas -->
<input type="email" name="recipients" multiple>

<!-- User can select multiple files at once -->
<input type="file" name="photos" multiple accept="image/*">
```

---

### `pattern` — Custom Validation with Regular Expressions

Specifies a pattern (regular expression) that the field's value must match.

```html
<!-- Must be exactly 11 digits (like a Nigerian phone number) -->
<input type="tel" name="phone" pattern="[0-9]{11}" 
       title="Please enter an 11-digit phone number">

<!-- Must be 6 uppercase letters or digits (like a postcode) -->
<input type="text" name="postcode" pattern="[A-Z0-9]{6}"
       title="Please enter a 6-character postcode (uppercase letters and numbers)">
```

- `pattern` takes a regular expression (a pattern-matching formula).
- `title` provides the error message hint shown to the user.
- If the input does not match the pattern, the form cannot be submitted.

---

### `list` — Connect Input to a `<datalist>`

Links an `<input>` to a `<datalist>` for autocomplete suggestions.

```html
<input type="text" name="city" list="nigerian-cities" placeholder="Choose a city">
<datalist id="nigerian-cities">
  <option value="Lagos">
  <option value="Abuja">
  <option value="Kano">
  <option value="Port Harcourt">
  <option value="Ibadan">
</datalist>
```

---

### `size` — Visible Width of the Input Box

Sets how wide the input box appears (measured in number of characters visible at once).

```html
<input type="text" name="shortcode" size="5">   <!-- Very narrow box -->
<input type="text" name="fullname" size="40">   <!-- Wide box -->
```

> `size` only affects the visual width. It does not limit how much text the user can type (use `maxlength` for that).

---

## Part 7: Form Attributes That Work on Input Elements

Some attributes can be added directly to `<input>` or `<button>` elements **to override** the `<form>`-level settings for that specific element. These are called **form override attributes**.

### `formaction` — Override the Form's `action`

Allows a specific submit button to send the form to a different URL than the form's `action`.

```html
<form action="/save-draft.php" method="post">
  <input type="text" name="title" placeholder="Post title">
  <textarea name="content" placeholder="Write your post..."></textarea>

  <!-- This button uses the form's action (/save-draft.php) -->
  <button type="submit">Save Draft</button>

  <!-- This button overrides and sends to /publish.php instead -->
  <button type="submit" formaction="/publish.php">Publish Now</button>
</form>
```

**Expected Output:** Two submit buttons. "Save Draft" sends to `/save-draft.php`. "Publish Now" sends to `/publish.php`. Both buttons submit the same form data.

**Real-world use:** A blog editor form with both a "Save Draft" button and a "Publish" button — same form, different destinations.

---

### `formmethod` — Override the Form's `method`

Allows a specific button to use a different HTTP method (GET or POST) than the rest of the form.

```html
<form action="/search.php" method="post">
  <input type="text" name="query">

  <!-- Normal submit: POST to /search.php -->
  <button type="submit">Search</button>

  <!-- This button overrides to use GET instead -->
  <button type="submit" formmethod="get">Search (Shareable Link)</button>
</form>
```

---

### `formenctype` — Override the Form's `enctype`

Overrides the encoding type for a specific submit button. Most useful when one button needs to upload a file while another does not.

---

### `formtarget` — Override the Form's `target`

Makes a specific button open the result in a different window/tab.

```html
<form action="/result.php" method="post">
  <input type="text" name="data">

  <!-- Opens result in same tab (uses form's default) -->
  <button type="submit">Submit Here</button>

  <!-- Opens result in a new tab -->
  <button type="submit" formtarget="_blank">Preview in New Tab</button>
</form>
```

---

### `formnovalidate` — Skip Validation for This Button

Lets a specific submit button bypass browser validation.

```html
<form action="/process.php" method="post">
  <input type="email" name="email" required>

  <!-- Normal submit: validates email format -->
  <button type="submit">Submit</button>

  <!-- Save without validating: useful for "Save Draft" -->
  <button type="submit" formaction="/save-draft.php" formnovalidate>
    Save Draft (Skip Validation)
  </button>
</form>
```

**Expected Output:** Clicking "Submit" validates the email. Clicking "Save Draft" skips validation and saves immediately, even if the email is incomplete.

---

## Guided Practice Exercises

### Exercise 1: Build a Basic Login Form

**Objective:** Create a working login form with all essential fields.

**Scenario:** You are building the login page for a school management system.

**Steps:**

1. Create `login.html`.
2. Build the complete form:

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>School Login</title>
  <style>
    body { font-family: Arial, sans-serif; max-width: 400px; margin: 50px auto; padding: 20px; }
    label { display: block; margin-top: 15px; font-weight: bold; }
    input[type="text"], input[type="password"] {
      width: 100%; padding: 8px; margin-top: 5px; box-sizing: border-box;
      border: 1px solid #ccc; border-radius: 4px;
    }
    button { margin-top: 20px; padding: 10px 25px; background-color: #2c3e50; color: white;
             border: none; border-radius: 4px; cursor: pointer; font-size: 16px; }
  </style>
</head>
<body>

  <h2>Student Login</h2>

  <form action="/login.php" method="post" autocomplete="off">

    <label for="student_id">Student ID:</label>
    <input type="text" id="student_id" name="student_id"
           placeholder="e.g. STU-2024-001"
           maxlength="15"
           required
           autofocus>

    <label for="password">Password:</label>
    <input type="password" id="password" name="password"
           placeholder="Enter your password"
           minlength="6"
           required>

    <input type="hidden" name="portal" value="student">

    <button type="submit">Log In</button>

  </form>

</body>
</html>
```

**Expected Output:** A clean login form with a Student ID field (autofocused), a Password field (hidden characters), and a "Log In" button.

**Self-check Questions:**
- Why did we use `method="post"` instead of `method="get"`?
- What does `autocomplete="off"` do on this form?
- Why is the hidden field `portal` useful here?
- What does `minlength="6"` do on the password field?
- What would happen if we added `autofocus` to the password field instead of the student ID field?

---

### Exercise 2: Build a Student Registration Form

**Objective:** Create a comprehensive multi-section registration form.

**Scenario:** A university needs a new student registration form.

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Student Registration</title>
  <style>
    body { font-family: Arial, sans-serif; max-width: 600px; margin: 30px auto; padding: 20px; }
    fieldset { border: 2px solid #2c3e50; border-radius: 8px; margin-bottom: 20px; padding: 15px; }
    legend { font-weight: bold; color: #2c3e50; padding: 0 10px; }
    label { display: block; margin-top: 12px; font-weight: bold; }
    input[type="text"], input[type="email"], input[type="date"], input[type="tel"],
    select, textarea {
      width: 100%; padding: 8px; margin-top: 5px; box-sizing: border-box;
      border: 1px solid #ccc; border-radius: 4px;
    }
    .radio-group label, .checkbox-group label { display: inline; font-weight: normal; margin-left: 5px; }
    .radio-group, .checkbox-group { margin-top: 8px; }
    button { margin-top: 20px; padding: 12px 30px; background-color: #27ae60; color: white;
             border: none; border-radius: 4px; cursor: pointer; font-size: 16px; width: 100%; }
  </style>
</head>
<body>

  <h2>New Student Registration</h2>

  <form action="/register.php" method="post">

    <!-- SECTION 1: Personal Details -->
    <fieldset>
      <legend>Personal Information</legend>

      <label for="fname">First Name: *</label>
      <input type="text" id="fname" name="firstname" placeholder="Your first name" required>

      <label for="lname">Last Name: *</label>
      <input type="text" id="lname" name="lastname" placeholder="Your last name" required>

      <label for="dob">Date of Birth: *</label>
      <input type="date" id="dob" name="dob" max="2010-01-01" required>

      <label>Gender: *</label>
      <div class="radio-group">
        <input type="radio" id="male" name="gender" value="male" required>
        <label for="male">Male</label>
        &nbsp;&nbsp;
        <input type="radio" id="female" name="gender" value="female">
        <label for="female">Female</label>
        &nbsp;&nbsp;
        <input type="radio" id="other_gender" name="gender" value="other">
        <label for="other_gender">Other</label>
      </div>

    </fieldset>

    <!-- SECTION 2: Contact Details -->
    <fieldset>
      <legend>Contact Information</legend>

      <label for="email">Email Address: *</label>
      <input type="email" id="email" name="email" placeholder="student@university.edu" required>

      <label for="phone">Phone Number: *</label>
      <input type="tel" id="phone" name="phone"
             placeholder="08012345678"
             pattern="[0-9]{11}"
             title="Please enter an 11-digit phone number"
             required>

      <label for="state">State of Origin: *</label>
      <select id="state" name="state" required>
        <option value="">-- Select State --</option>
        <option value="abia">Abia</option>
        <option value="abuja">Abuja (FCT)</option>
        <option value="anambra">Anambra</option>
        <option value="lagos" selected>Lagos</option>
        <option value="kano">Kano</option>
        <option value="rivers">Rivers</option>
      </select>

    </fieldset>

    <!-- SECTION 3: Academic Details -->
    <fieldset>
      <legend>Academic Information</legend>

      <label for="faculty">Faculty: *</label>
      <select id="faculty" name="faculty" required>
        <optgroup label="Science & Technology">
          <option value="cs">Computer Science</option>
          <option value="eng">Engineering</option>
          <option value="math">Mathematics</option>
        </optgroup>
        <optgroup label="Arts & Social Sciences">
          <option value="econ">Economics</option>
          <option value="law">Law</option>
          <option value="polsci">Political Science</option>
        </optgroup>
      </select>

      <label for="about">Tell us about yourself:</label>
      <textarea id="about" name="about" rows="4"
                placeholder="Write a short paragraph about yourself, your goals, and why you chose this university..."
                maxlength="500"></textarea>

      <label>Preferred Study Mode: *</label>
      <div class="radio-group">
        <input type="radio" id="full_time" name="study_mode" value="fulltime" checked required>
        <label for="full_time">Full-time</label>
        &nbsp;&nbsp;
        <input type="radio" id="part_time" name="study_mode" value="parttime">
        <label for="part_time">Part-time</label>
      </div>

      <label>Subjects of Interest:</label>
      <div class="checkbox-group">
        <input type="checkbox" id="prog" name="interest" value="programming">
        <label for="prog">Programming</label><br>
        <input type="checkbox" id="data" name="interest" value="data_science">
        <label for="data">Data Science</label><br>
        <input type="checkbox" id="design" name="interest" value="design">
        <label for="design">Web Design</label><br>
        <input type="checkbox" id="ai" name="interest" value="ai">
        <label for="ai">Artificial Intelligence</label>
      </div>

    </fieldset>

    <!-- SECTION 4: Documents -->
    <fieldset>
      <legend>Upload Documents</legend>

      <label for="photo">Passport Photo:</label>
      <input type="file" id="photo" name="passport_photo" accept="image/*">

      <label for="cert">O'Level Certificate (PDF):</label>
      <input type="file" id="cert" name="olevel_cert" accept=".pdf">

    </fieldset>

    <!-- Terms and Submit -->
    <div class="checkbox-group">
      <input type="checkbox" id="terms" name="agree_terms" value="yes" required>
      <label for="terms"> I agree to the <a href="/terms.html">Terms and Conditions</a></label>
    </div>

    <button type="submit">Submit Registration</button>

  </form>

</body>
</html>
```

**Expected Output:** A fully styled, multi-section registration form with four fieldset groups covering personal information, contact details, academic choices, and document uploads.

**Self-check Questions:**
- Why is `enctype="multipart/form-data"` missing from this form? What should you add to properly support file uploads?
- What does the `max="2010-01-01"` on the date field achieve?
- Why do all the radio buttons for "gender" share the same `name="gender"`?
- What happens if a user selects multiple checkboxes for "interest"? How does the server receive that data?
- What is the `optgroup` element doing inside the faculty dropdown?

**Hint for file uploads:** Add `enctype="multipart/form-data"` to the `<form>` opening tag.

---

### Exercise 3: Build a Course Feedback Form with Form-Override Buttons

**Objective:** Create a form with two different submit buttons that send data to different places.

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Course Feedback</title>
  <style>
    body { font-family: Arial, sans-serif; max-width: 500px; margin: 30px auto; padding: 20px; }
    label { display: block; margin-top: 15px; font-weight: bold; }
    input[type="text"], select, textarea { width: 100%; padding: 8px; margin-top: 5px; box-sizing: border-box; }
    .btn-row { margin-top: 20px; display: flex; gap: 10px; }
    button { padding: 10px 20px; border: none; border-radius: 4px; cursor: pointer; font-size: 15px; }
    .btn-draft { background-color: #7f8c8d; color: white; }
    .btn-submit { background-color: #2c3e50; color: white; }
  </style>
</head>
<body>

  <h2>Course Feedback Form</h2>

  <form action="/submit-feedback.php" method="post">

    <label for="course">Course Name:</label>
    <select id="course" name="course" required>
      <option value="">-- Select Course --</option>
      <option value="html_css">HTML & CSS</option>
      <option value="javascript">JavaScript</option>
      <option value="python">Python</option>
    </select>

    <label for="rating">Overall Rating:</label>
    <input type="range" id="rating" name="rating" min="1" max="5" value="3">
    <p>Selected: <output for="rating" id="ratingOutput">3</output> / 5</p>

    <script>
      document.getElementById('rating').addEventListener('input', function() {
        document.getElementById('ratingOutput').textContent = this.value;
      });
    </script>

    <label for="comments">Comments:</label>
    <textarea id="comments" name="comments" rows="5"
              placeholder="Share your experience with this course..."></textarea>

    <label for="recommend">Would you recommend this course?</label>
    <select id="recommend" name="recommend">
      <option value="yes">Yes, definitely!</option>
      <option value="maybe">Maybe</option>
      <option value="no">No</option>
    </select>

    <div class="btn-row">
      <!-- Save as draft: goes to different URL, skips validation -->
      <button type="submit"
              class="btn-draft"
              formaction="/save-draft.php"
              formnovalidate>
        Save Draft
      </button>

      <!-- Full submit: goes to main action URL, validates everything -->
      <button type="submit" class="btn-submit">
        Submit Feedback
      </button>
    </div>

  </form>

</body>
</html>
```

**Expected Output:** A feedback form with a course selector, a live rating slider, a comments textarea, and two buttons. "Save Draft" saves without validation to `/save-draft.php`. "Submit Feedback" validates and sends to `/submit-feedback.php`.

---

## Mini Project: Build a Complete Job Application Form

You will now build a real-world job application form that a company could actually use on their website.

### Project Overview

A tech company called **InnovateTech** needs an online job application form. It must collect:
- Applicant's personal information
- Contact information
- Work experience and skills
- Education
- A cover letter
- A CV file upload
- Agreement to terms

---

### Stage 1: Setup

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>InnovateTech — Job Application</title>
  <style>

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      font-family: 'Segoe UI', Arial, sans-serif;
      background-color: #f0f2f5;
      color: #2c3e50;
      padding: 30px 20px;
    }

    .page-header {
      background-color: #2c3e50;
      color: white;
      padding: 25px 30px;
      border-radius: 8px 8px 0 0;
      max-width: 700px;
      margin: 0 auto;
    }

    .page-header h1 { font-size: 24px; }
    .page-header p { margin-top: 5px; opacity: 0.8; }

    form {
      background-color: white;
      max-width: 700px;
      margin: 0 auto;
      padding: 30px;
      border-radius: 0 0 8px 8px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }

    fieldset {
      border: 2px solid #ecf0f1;
      border-radius: 6px;
      padding: 20px;
      margin-bottom: 25px;
    }

    legend {
      background-color: #2c3e50;
      color: white;
      padding: 5px 15px;
      border-radius: 4px;
      font-weight: bold;
    }

    label {
      display: block;
      margin-top: 15px;
      font-weight: bold;
      font-size: 14px;
    }

    input[type="text"],
    input[type="email"],
    input[type="tel"],
    input[type="url"],
    input[type="number"],
    input[type="date"],
    select,
    textarea {
      width: 100%;
      padding: 10px 12px;
      margin-top: 6px;
      border: 1px solid #bdc3c7;
      border-radius: 4px;
      font-size: 15px;
    }

    input[type="file"] { margin-top: 8px; }

    .radio-inline input, .checkbox-inline input { width: auto; margin-right: 6px; }
    .radio-inline label, .checkbox-inline label { display: inline; font-weight: normal; }
    .option-group { margin-top: 10px; line-height: 2; }

    .btn-row { margin-top: 25px; display: flex; gap: 15px; flex-wrap: wrap; }

    button {
      padding: 12px 28px;
      font-size: 16px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    .btn-draft { background-color: #95a5a6; color: white; }
    .btn-submit { background-color: #27ae60; color: white; flex: 1; }

    .required-note { font-size: 13px; color: #7f8c8d; margin-bottom: 15px; }

    .char-count { font-size: 12px; color: #7f8c8d; text-align: right; margin-top: 3px; }

  </style>
</head>
<body>

  <div class="page-header">
    <h1>InnovateTech — Job Application</h1>
    <p>Complete all sections. Fields marked * are required.</p>
  </div>
```

---

### Stage 2: Personal & Contact Information

Add this inside the `<body>` after the header div, opening the `<form>`:

```html
  <form action="/apply.php" method="post" enctype="multipart/form-data">

    <p class="required-note">* = required field</p>

    <!-- ── PERSONAL INFO ── -->
    <fieldset>
      <legend>👤 Personal Information</legend>

      <label for="app_fname">First Name: *</label>
      <input type="text" id="app_fname" name="firstname"
             placeholder="Your first name" required autofocus>

      <label for="app_lname">Last Name: *</label>
      <input type="text" id="app_lname" name="lastname"
             placeholder="Your last name" required>

      <label for="app_dob">Date of Birth: *</label>
      <input type="date" id="app_dob" name="dob"
             max="2005-12-31" required>

      <label>Gender:</label>
      <div class="option-group">
        <span class="radio-inline">
          <input type="radio" id="g_male" name="gender" value="male">
          <label for="g_male">Male</label>
        </span>
        &nbsp;&nbsp;
        <span class="radio-inline">
          <input type="radio" id="g_female" name="gender" value="female">
          <label for="g_female">Female</label>
        </span>
        &nbsp;&nbsp;
        <span class="radio-inline">
          <input type="radio" id="g_other" name="gender" value="other">
          <label for="g_other">Prefer not to say</label>
        </span>
      </div>

    </fieldset>

    <!-- ── CONTACT INFO ── -->
    <fieldset>
      <legend>📞 Contact Information</legend>

      <label for="app_email">Email Address: *</label>
      <input type="email" id="app_email" name="email"
             placeholder="you@example.com" required>

      <label for="app_phone">Phone Number: *</label>
      <input type="tel" id="app_phone" name="phone"
             placeholder="08012345678"
             pattern="[0-9]{11}"
             title="Enter an 11-digit phone number"
             required>

      <label for="app_linkedin">LinkedIn Profile URL:</label>
      <input type="url" id="app_linkedin" name="linkedin"
             placeholder="https://linkedin.com/in/yourname">

      <label for="app_city">City: *</label>
      <input type="text" id="app_city" name="city"
             list="nigerian-cities" required>
      <datalist id="nigerian-cities">
        <option value="Lagos">
        <option value="Abuja">
        <option value="Port Harcourt">
        <option value="Kano">
        <option value="Ibadan">
        <option value="Enugu">
        <option value="Benin City">
      </datalist>

    </fieldset>
```

---

### Stage 3: Role, Skills & Experience

```html
    <!-- ── ROLE & SKILLS ── -->
    <fieldset>
      <legend>💼 Role & Skills</legend>

      <label for="app_role">Position Applying For: *</label>
      <select id="app_role" name="role" required>
        <option value="">-- Select a Position --</option>
        <optgroup label="Engineering">
          <option value="frontend">Frontend Developer</option>
          <option value="backend">Backend Developer</option>
          <option value="fullstack">Full-Stack Developer</option>
        </optgroup>
        <optgroup label="Design & Product">
          <option value="ux">UX Designer</option>
          <option value="pm">Product Manager</option>
        </optgroup>
        <optgroup label="Data">
          <option value="data_analyst">Data Analyst</option>
          <option value="ml_engineer">Machine Learning Engineer</option>
        </optgroup>
      </select>

      <label for="app_exp">Years of Experience: *</label>
      <input type="number" id="app_exp" name="years_exp"
             min="0" max="50" step="1" value="0" required>

      <label>Employment Type Preference: *</label>
      <div class="option-group">
        <span class="radio-inline">
          <input type="radio" id="emp_full" name="emp_type" value="fulltime" required checked>
          <label for="emp_full">Full-time</label>
        </span>
        &nbsp;&nbsp;
        <span class="radio-inline">
          <input type="radio" id="emp_part" name="emp_type" value="parttime">
          <label for="emp_part">Part-time</label>
        </span>
        &nbsp;&nbsp;
        <span class="radio-inline">
          <input type="radio" id="emp_remote" name="emp_type" value="remote">
          <label for="emp_remote">Remote</label>
        </span>
      </div>

      <label>Core Skills (select all that apply):</label>
      <div class="option-group checkbox-inline">
        <input type="checkbox" id="sk_html" name="skills" value="HTML_CSS">
        <label for="sk_html">HTML/CSS</label><br>
        <input type="checkbox" id="sk_js" name="skills" value="JavaScript">
        <label for="sk_js">JavaScript</label><br>
        <input type="checkbox" id="sk_python" name="skills" value="Python">
        <label for="sk_python">Python</label><br>
        <input type="checkbox" id="sk_sql" name="skills" value="SQL">
        <label for="sk_sql">SQL / Databases</label><br>
        <input type="checkbox" id="sk_react" name="skills" value="React">
        <label for="sk_react">React / Vue</label><br>
        <input type="checkbox" id="sk_cloud" name="skills" value="Cloud">
        <label for="sk_cloud">Cloud (AWS / GCP)</label>
      </div>

      <label for="app_salary">Expected Monthly Salary (₦):</label>
      <input type="number" id="app_salary" name="salary_expectation"
             min="50000" step="5000" placeholder="e.g. 300000">

      <label for="app_start">Earliest Start Date:</label>
      <input type="date" id="app_start" name="start_date">

    </fieldset>
```

---

### Stage 4: Cover Letter, CV Upload & Submit

```html
    <!-- ── COVER LETTER ── -->
    <fieldset>
      <legend>📝 Cover Letter</legend>

      <label for="app_cover">Write Your Cover Letter: *</label>
      <textarea id="app_cover" name="cover_letter" rows="8"
                placeholder="Dear Hiring Manager, I am writing to express my interest in..."
                maxlength="2000"
                required
                oninput="document.getElementById('cover_count').textContent = this.value.length"></textarea>
      <p class="char-count"><span id="cover_count">0</span> / 2000 characters</p>

    </fieldset>

    <!-- ── DOCUMENTS ── -->
    <fieldset>
      <legend>📎 Upload Documents</legend>

      <label for="app_cv">Upload Your CV/Resume (PDF only): *</label>
      <input type="file" id="app_cv" name="cv_file"
             accept=".pdf" required>

      <label for="app_portfolio">Upload Portfolio / Work Samples (optional):</label>
      <input type="file" id="app_portfolio" name="portfolio"
             accept=".pdf,.zip,.docx" multiple>

    </fieldset>

    <!-- ── AGREEMENT ── -->
    <fieldset>
      <legend>✅ Declaration</legend>

      <div class="checkbox-inline" style="margin-top:10px; line-height:1.8;">
        <input type="checkbox" id="accurate" name="accuracy_declaration" value="yes" required>
        <label for="accurate">I confirm that all information provided is accurate and truthful.</label><br>

        <input type="checkbox" id="terms_agree" name="terms" value="agreed" required>
        <label for="terms_agree">I have read and agree to the <a href="/privacy.html">Privacy Policy</a>.</label>
      </div>

    </fieldset>

    <!-- Hidden fields -->
    <input type="hidden" name="form_version" value="2025-v1">
    <input type="hidden" name="source" value="careers_page">

    <!-- Submit Buttons -->
    <div class="btn-row">
      <button type="submit"
              class="btn-draft"
              formaction="/save-application-draft.php"
              formnovalidate>
        💾 Save Draft
      </button>
      <button type="submit" class="btn-submit">
        🚀 Submit Application
      </button>
    </div>

  </form>

</body>
</html>
```

**Final Milestone Output:**
- A professional-looking two-toned form with a dark header and white form body.
- Five clearly labelled fieldset sections: Personal, Contact, Role & Skills, Cover Letter, Documents.
- Two submit buttons: "Save Draft" (skips validation, goes to draft endpoint) and "Submit Application" (full validation).
- Live character counter on the cover letter textarea.
- City autocomplete with Nigerian cities via `<datalist>`.
- Proper `enctype="multipart/form-data"` for file uploads.

**Reflection Questions:**
1. Why must the `<form>` have `enctype="multipart/form-data"` for the file uploads to work?
2. Why did we give the hidden fields `name="form_version"` and `name="source"`?
3. How does `formnovalidate` on the "Save Draft" button help the user experience?
4. Why did we use `<optgroup>` in the role `<select>`?
5. What would happen if two different `<select>` elements both had `name="role"`? Which value would the server receive?

---

## Common Beginner Mistakes

### Mistake 1: Forgetting `name` on Input Fields

**What happens:** The field value is NOT sent to the server. The server receives nothing from that field.

**Wrong:**
```html
<input type="text" id="city" placeholder="Enter city">
```

**Correct:**
```html
<input type="text" id="city" name="city" placeholder="Enter city">
```

---

### Mistake 2: Using `method="get"` for Passwords

**What happens:** The password appears in the URL like `/login?password=abc123` — visible in the browser bar, browser history, server logs, and to anyone watching over the user's shoulder.

**Wrong:**
```html
<form action="/login.php" method="get">
  <input type="password" name="pwd">
</form>
```

**Correct:**
```html
<form action="/login.php" method="post">
  <input type="password" name="pwd">
</form>
```

---

### Mistake 3: Confusing `id` and `name`

`id` connects the label to the input in the HTML page. `name` is the key sent to the server. They can have the same value (which is common and recommended), but they serve different purposes.

**Wrong thinking:** "They are the same thing."

**Correct understanding:**
```html
<label for="email">Email:</label>         <!-- uses id to link -->
<input type="email" id="email" name="email">
<!--                 ↑ for label  ↑ for server -->
```

---

### Mistake 4: Radio Buttons With Different `name` Values

**What happens:** Each radio button becomes its own independent group. The user can select all of them at once instead of only one.

**Wrong:**
```html
<input type="radio" id="male" name="gender_male" value="male">
<input type="radio" id="female" name="gender_female" value="female">
```

**Correct:** All radio buttons in a group must share exactly the same `name`:
```html
<input type="radio" id="male" name="gender" value="male">
<input type="radio" id="female" name="gender" value="female">
```

---

### Mistake 5: Forgetting `enctype` for File Uploads

**What happens:** Only the filename is sent to the server. The actual file content is never received. The upload silently fails.

**Wrong:**
```html
<form action="/upload.php" method="post">
  <input type="file" name="cv">
</form>
```

**Correct:**
```html
<form action="/upload.php" method="post" enctype="multipart/form-data">
  <input type="file" name="cv">
</form>
```

---

### Mistake 6: Using `placeholder` Instead of `<label>`

**What happens:** When the user clicks the field, the hint text disappears. They forget what they were supposed to type. This is especially frustrating on long forms.

**Wrong:**
```html
<input type="text" name="fullname" placeholder="Full Name">
```

**Correct:**
```html
<label for="fullname">Full Name:</label>
<input type="text" id="fullname" name="fullname" placeholder="e.g. Chidi Okafor">
```

The placeholder is a supplement to the label, not a replacement.

---

### Mistake 7: A `<button>` Without `type` Inside a Form

**What happens:** All `<button>` elements default to `type="submit"` when inside a form. A button intended as a general-purpose button (e.g., "Show Password") accidentally submits the form.

**Wrong:**
```html
<button onclick="showPreview()">Preview</button>  <!-- accidentally submits form! -->
<button type="submit">Submit</button>
```

**Correct:**
```html
<button type="button" onclick="showPreview()">Preview</button>  <!-- safe -->
<button type="submit">Submit</button>
```

---

### Mistake 8: Forgetting `for`/`id` Connection on Labels

**What happens:** Clicking the label text does NOT focus the input. Accessibility for screen readers is broken.

**Wrong:**
```html
<label>Username:</label>
<input type="text" name="username">
```

**Correct:**
```html
<label for="username">Username:</label>
<input type="text" id="username" name="username">
```

---

## Reflection Questions

1. In your own words, explain what an HTML form does and why every useful website needs one.
2. What is the difference between `method="get"` and `method="post"`? Give a real example of when you would use each.
3. What does the `action` attribute on a `<form>` do?
4. Name five different values for `type` on the `<input>` element and explain what each one creates.
5. Why must radio buttons in the same group share the same `name` attribute?
6. What is the difference between `<select>` (a dropdown) and `<datalist>` (autocomplete suggestions)?
7. When would you use `<fieldset>` and `<legend>`? Why?
8. What is the difference between `required`, `readonly`, and `disabled`?
9. What does `enctype="multipart/form-data"` do, and when is it required?
10. What is `formaction` and why is it useful to have two submit buttons with different `formaction` values?
11. What is a hidden input field used for? Give a real-world example.
12. Explain the difference between the `value` attribute and the `placeholder` attribute on an `<input>`.
13. What does `autofocus` do, and why should only one field per page use it?
14. What is the `pattern` attribute and what kind of value does it take?
15. In what situation would you use `type="image"` instead of `type="submit"`?

---

## Completion Checklist

- [ ] I understand what an HTML form is and why it is used.
- [ ] I can write a `<form>` element with the correct `action`, `method`, and `enctype` attributes.
- [ ] I know the difference between `method="get"` and `method="post"`.
- [ ] I can create text, password, email, number, date, and range input fields.
- [ ] I understand how checkboxes and radio buttons differ in usage.
- [ ] I know how to create a dropdown list with `<select>` and `<option>`.
- [ ] I know how to group dropdown options with `<optgroup>`.
- [ ] I can create an autocomplete field using `<datalist>`.
- [ ] I can build a multi-line text area with `<textarea>`.
- [ ] I can upload files using `type="file"` with the correct `enctype`.
- [ ] I know when and how to use `<fieldset>` and `<legend>`.
- [ ] I understand the difference between `readonly` and `disabled`.
- [ ] I can use `required`, `maxlength`, `minlength`, `min`, `max`, `step`, and `pattern`.
- [ ] I know what `autofocus`, `placeholder`, `value`, and `name` do.
- [ ] I understand hidden input fields and what they are used for.
- [ ] I can use `formaction`, `formmethod`, `formtarget`, and `formnovalidate` on submit buttons.
- [ ] I have completed all three guided exercises.
- [ ] I have built the complete job application mini-project.
- [ ] I can list at least five common beginner mistakes in form building.

---

## Lesson Summary

In this lesson, you have mastered the complete set of HTML form tools. Here is a quick reference:

**The Form Container:**
```html
<form action="/url" method="post" enctype="multipart/form-data"
      autocomplete="off" novalidate target="_blank">
```

**The Most Common Input Types:**
```html
<input type="text">         <!-- Single-line text -->
<input type="password">     <!-- Hidden text -->
<input type="email">        <!-- Email with @ validation -->
<input type="number">       <!-- Numbers with min/max/step -->
<input type="date">         <!-- Calendar date picker -->
<input type="checkbox">     <!-- Tick-box (multiple allowed) -->
<input type="radio">        <!-- Circle button (one per group) -->
<input type="file">         <!-- File upload -->
<input type="submit">       <!-- Submit the form -->
<input type="hidden">       <!-- Invisible data field -->
```

**Other Key Elements:**
```html
<textarea rows="5" cols="40"></textarea>     <!-- Multi-line text -->
<select><option>...</option></select>         <!-- Drop-down list -->
<datalist><option>...</option></datalist>     <!-- Autocomplete -->
<fieldset><legend>...</legend></fieldset>     <!-- Section grouper -->
<button type="submit|reset|button">           <!-- Flexible button -->
<label for="id">Text</label>                  <!-- Field label -->
```

**Critical Input Attributes:**
```
name        → The key sent to the server (required for all submittable fields)
value       → Pre-filled default value
placeholder → Hint text inside empty field
required    → Must be filled before submitting
readonly    → Visible but not editable (still sent to server)
disabled    → Greyed out and not sent to server
maxlength   → Maximum characters allowed
pattern     → Custom regex validation rule
autofocus   → Move cursor here on page load
```

**Form-Override Button Attributes:**
```
formaction      → Send this button's data to a different URL
formmethod      → Override the form's GET/POST method
formtarget      → Open response in different window/tab
formnovalidate  → Skip browser validation for this button only
```

HTML forms are the bridge between your users and your application's data. With what you have learned in this lesson, you can build forms for any real-world use case — from simple contact pages to complex multi-step applications.
