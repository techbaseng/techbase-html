---
render_with_liquid: false
title: "Lesson 16: HTML Tables — From Zero to Professional"
nav_order: 16
---

# Lesson 16: HTML Tables — From Zero to Professional

---

## Lesson Introduction

Imagine you are a teacher who wants to show students their exam results. You need a neat grid with rows for each student and columns for each subject. Or imagine you are a web developer building a product pricing page with plans, features, and prices lined up side by side. That neat, grid-like arrangement of data is a **table** — and HTML gives you everything you need to build one.

In this lesson, you will learn how to create HTML tables from scratch, style them beautifully with CSS, control their size and layout, merge cells across rows and columns, and use advanced features like column grouping. By the end, you will build a realistic mini project: a fully styled class schedule table.

**What you will learn:**
- What HTML tables are and why they exist
- How to build a basic table with rows, columns, and headers
- How to add borders, adjust sizes, and control spacing
- How to add captions and vertical headers
- How to merge cells horizontally (colspan) and vertically (rowspan)
- How to style tables with zebra stripes, hover effects, and dividers
- How to use `<colgroup>` to style entire columns at once

> **No prior experience needed.** This lesson assumes you know basic HTML tags like `<p>`, `<h1>`, and `<div>`. If you do, you are ready!

---

## Prerequisite Concepts

Before diving into tables, let us quickly cover two ideas you need to understand.

### What is CSS?

**CSS** stands for Cascading Style Sheets. It is a language you use to control how HTML elements look — their colour, size, font, spacing, and more. You write CSS rules like this:

```css
/* This means: "Select all <p> tags and make the text colour blue." */
p {
  color: blue;
}
```

In this lesson, we will use CSS inside a `<style>` tag (placed in the `<head>` of your HTML page) or directly on elements using the `style=""` attribute.

### What is a Grid?

A **grid** is a system of rows and columns, like a spreadsheet or a calendar. Tables are HTML's built-in way to create a grid. Every table has:

- **Rows** — horizontal lines going left to right
- **Columns** — vertical lines going top to bottom
- **Cells** — the individual boxes where a row and column cross

---

## Part 1: Understanding HTML Tables

### What Is an HTML Table?

An HTML table is a structured element that arranges data into **rows** and **columns**. Think of it like a spreadsheet embedded in a web page.

**Real-world uses of tables:**
- Student grade sheets
- Product comparison charts
- Price lists
- Train/bus schedules
- Sports standings
- Financial reports

### The Core Table Tags

Before writing any code, you need to understand the building blocks. There are four main tags:

| Tag | What it means | What it does |
|---|---|---|
| `<table>` | "table" | Wraps the whole table |
| `<tr>` | "table row" | Creates one horizontal row |
| `<td>` | "table data" | Creates one cell inside a row |
| `<th>` | "table header" | Creates a header cell (bold + centred by default) |

Think of it like a spreadsheet:
- `<table>` = the whole spreadsheet
- `<tr>` = one row in the spreadsheet
- `<td>` = one cell in that row
- `<th>` = a heading at the top or side of the spreadsheet

### Additional Table Tags

There are more tags you will use as tables grow more complex:

| Tag | Description |
|---|---|
| `<caption>` | Adds a title above the table |
| `<thead>` | Groups the header rows (top section) |
| `<tbody>` | Groups the body rows (middle section) |
| `<tfoot>` | Groups the footer rows (bottom section) |
| `<colgroup>` | Groups one or more columns for styling |
| `<col>` | Defines style properties for a column inside `<colgroup>` |

---

## Part 2: Building Your First Table

### Step 1 — The Simplest Possible Table

Let us start with the smallest table that makes sense: one row, three cells.

```html
<table>
  <tr>
    <td>Emil</td>
    <td>Tobias</td>
    <td>Linus</td>
  </tr>
</table>
```

**What each line does:**
- `<table>` — Opens the table. Everything between here and `</table>` is part of the table.
- `<tr>` — Opens a row. One `<tr>` = one horizontal row in the table.
- `<td>Emil</td>` — Opens a cell and puts the text "Emil" inside it. Then closes the cell.
- `<td>Tobias</td>` — Same, but with "Tobias".
- `<td>Linus</td>` — Same, but with "Linus".
- `</tr>` — Closes the row.
- `</table>` — Closes the whole table.

**Expected output (no borders yet, just plain text in a row):**

```
Emil   Tobias   Linus
```

> **Think about this:** What happens if you add a second `<tr>...</tr>` block with three more `<td>` tags? Try it!

### Step 2 — Adding Multiple Rows

Now let us add two rows, each with three cells:

```html
<table>
  <tr>
    <td>Emil</td>
    <td>Tobias</td>
    <td>Linus</td>
  </tr>
  <tr>
    <td>16</td>
    <td>14</td>
    <td>10</td>
  </tr>
</table>
```

**Expected output (no borders, two rows):**

```
Emil    Tobias   Linus
16      14       10
```

Each `<tr>` is a new row. Each `<td>` inside it is a new cell in that row.

**Important rule:** Every row should have the same number of cells. If one row has 3 cells and another has 2, the table looks broken. (We will learn about exceptions when we cover `colspan`.)

### Step 3 — Adding Header Cells

Header cells use `<th>` instead of `<td>`. They are automatically displayed in **bold** and **centred** in most browsers — no extra CSS needed.

```html
<table>
  <tr>
    <th>Person 1</th>
    <th>Person 2</th>
    <th>Person 3</th>
  </tr>
  <tr>
    <td>Emil</td>
    <td>Tobias</td>
    <td>Linus</td>
  </tr>
  <tr>
    <td>16</td>
    <td>14</td>
    <td>10</td>
  </tr>
</table>
```

**Expected output:**

```
Person 1   Person 2   Person 3   ← bold, centred (header row)
Emil       Tobias     Linus
16         14         10
```

> **Why use `<th>` instead of just making `<td>` text bold?**
> Because `<th>` tells the browser (and screen readers for people with vision impairments) that this cell is a *header* — a label, not just data. It makes your HTML more meaningful and accessible.

### A Complete Real-World Example

Here is a company contact table — the kind you see on many business websites:

```html
<table>
  <tr>
    <th>Company</th>
    <th>Contact</th>
    <th>Country</th>
  </tr>
  <tr>
    <td>Alfreds Futterkiste</td>
    <td>Maria Anders</td>
    <td>Germany</td>
  </tr>
  <tr>
    <td>Centro comercial Moctezuma</td>
    <td>Francisco Chang</td>
    <td>Mexico</td>
  </tr>
  <tr>
    <td>Ernst Handel</td>
    <td>Roland Mendel</td>
    <td>Austria</td>
  </tr>
</table>
```

**Expected output:**

```
Company                     Contact           Country
Alfreds Futterkiste         Maria Anders      Germany
Centro comercial Moctezuma  Francisco Chang   Mexico
Ernst Handel                Roland Mendel     Austria
```

This is a proper data table with a header row and three data rows. The first row uses `<th>` for "Company", "Contact", and "Country".

---

## Part 3: Table Borders

Right now, your table has no visible lines. The data floats in space. We use CSS to add borders.

### Why Borders Matter

Without borders, the columns and rows are hard to read. With borders, the table looks clean and professional — like a real spreadsheet.

### Adding a Basic Border

Use the CSS `border` property on `table`, `th`, and `td` elements:

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    table, th, td {
      border: 1px solid black;
    }
  </style>
</head>
<body>

<table>
  <tr>
    <th>Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Alice</td>
    <td>25</td>
  </tr>
</table>

</body>
</html>
```

**What the CSS does:**
- `table, th, td` — Selects the table AND all `th` AND all `td` elements at once.
- `border: 1px solid black;` — Adds a 1-pixel-wide solid black border around each of these elements.

**Expected output:** A table where every cell has its own border drawn around it. However, notice something: each cell has its OWN border, so between two adjacent cells, you will see a DOUBLE line (one from each cell's border). Let us fix that next.

### Collapsed Borders (Removing Double Lines)

The `border-collapse: collapse` property merges touching borders into a single border:

```html
<style>
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
</style>
```

**Before `border-collapse: collapse`:** Every cell has its own border → double lines between cells.
**After `border-collapse: collapse`:** Touching borders are merged → single clean lines everywhere.

This is the most common way to style tables, so **always add `border-collapse: collapse`** when you want a traditional table look.

> **Real-world analogy:** Without `border-collapse`, it is like every house in a street has its own fence — so there are double fences between neighbours. With `border-collapse`, neighbours share a single fence.

### Styled/Invisible Borders (Modern Look)

You can create a modern "no visible outer border" effect by using a white border combined with a coloured background:

```html
<style>
  table, th, td {
    border: 1px solid white;
    border-collapse: collapse;
  }
  th, td {
    background-color: #96D4D4;  /* teal background */
  }
</style>
```

**What this does:** The borders exist (they are 1px wide) but are the same colour as the background. So visually, you only see the gap between cells created by the border, giving an invisible-divider effect.

### Rounded Borders

Add `border-radius` to give cells rounded corners:

```html
<style>
  table, th, td {
    border: 1px solid black;
    border-radius: 10px;
  }
</style>
```

**Expected output:** Every cell has rounded corners. Note: if you also want rounded corners on the outer table box, include `table` in the selector. If you only want rounded inner cells, write:

```html
<style>
  th, td {
    border: 1px solid black;
    border-radius: 10px;
  }
</style>
```

### Border Styles

The `border-style` property controls the visual appearance of the border line. Supported values: `dotted`, `dashed`, `solid`, `double`, `groove`, `ridge`, `inset`, `outset`, `none`, `hidden`.

```html
<style>
  th, td {
    border-style: dotted;
  }
</style>
```

**Expected output:** All cell borders appear as dotted lines instead of solid lines.

### Border Colour

Control the border colour with `border-color`:

```html
<style>
  th, td {
    border: 1px solid #96D4D4;  /* teal border */
    border-collapse: collapse;
  }
</style>
```

**Expected output:** All cell borders are teal-coloured instead of black.

> **Common beginner mistake:** Writing `border: 1px solid black` on only `table` but not `th` and `td`. This draws a box around the whole table but leaves the inner cells without borders. Always style all three: `table, th, td`.

---

## Part 4: Table Sizes

By default, a table is only as wide as its content needs it to be. You can control the width and height using the CSS `width` and `height` properties.

### Setting Table Width

To make the table take up the full width of the page:

```html
<table style="width: 100%">
  <tr>
    <th>Firstname</th>
    <th>Lastname</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Jill</td>
    <td>Smith</td>
    <td>50</td>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td>
    <td>94</td>
  </tr>
</table>
```

**What `width: 100%` means:** The table will be as wide as its parent element — usually the page body. So if the browser window is 1000 pixels wide, the table becomes 1000 pixels wide.

**Expected output:** The table stretches to fill the entire width of the browser window.

You can also use pixel values: `style="width: 500px"` would make the table exactly 500 pixels wide.

### Setting Column Width

To make a specific column wider, add the `style` attribute to that column's `<th>` or `<td>`:

```html
<table style="width: 100%">
  <tr>
    <th style="width: 70%">Firstname</th>
    <th>Lastname</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Jill</td>
    <td>Smith</td>
    <td>50</td>
  </tr>
</table>
```

**What this does:** The first column ("Firstname") takes 70% of the total table width. The remaining 30% is shared between the other two columns.

**Expected output:** The first column is noticeably wider than the other two.

> **Think about this:** If you set column 1 to 70%, column 2 to 20%, and column 3 to 10%, that adds up to 100%. What happens if you set them to values that add up to more than 100%?

### Setting Row Height

Add `style="height: Xpx"` to a `<tr>` to make that row taller:

```html
<table style="width: 100%">
  <tr>
    <th>Firstname</th>
    <th>Lastname</th>
    <th>Age</th>
  </tr>
  <tr style="height: 200px">
    <td>Jill</td>
    <td>Smith</td>
    <td>50</td>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td>
    <td>94</td>
  </tr>
</table>
```

**Expected output:** The second row (Jill Smith, 50) is 200 pixels tall. The third row (Eve Jackson, 94) is its normal height. This is useful for tables where rows contain images or large amounts of content.

---

## Part 5: Table Headers

You have already seen horizontal headers (at the top of a table). But headers can also appear vertically on the left side, and a table can have a caption (a title above it).

### Horizontal Header (Top Row)

The most common pattern: use `<th>` in the first row to label each column.

```html
<table>
  <tr>
    <th>Firstname</th>
    <th>Lastname</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Jill</td>
    <td>Smith</td>
    <td>50</td>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td>
    <td>94</td>
  </tr>
</table>
```

**Expected output:**

```
Firstname   Lastname   Age    ← bold, centred (header row)
Jill        Smith      50
Eve         Jackson    94
```

### Vertical Header (Left Column)

Use `<th>` as the first cell in each row to create a vertical header on the left side:

```html
<table>
  <tr>
    <th>Firstname</th>
    <td>Jill</td>
    <td>Eve</td>
  </tr>
  <tr>
    <th>Lastname</th>
    <td>Smith</td>
    <td>Jackson</td>
  </tr>
  <tr>
    <th>Age</th>
    <td>50</td>
    <td>94</td>
  </tr>
</table>
```

**Expected output:**

```
Firstname   Jill    Eve
Lastname    Smith   Jackson
Age         50      94
```

Each row now has ONE `<th>` (the label on the left) and multiple `<td>` (the actual data). This is useful when comparing properties of different items.

### Aligning Header Text to the Left

By default, `<th>` text is centred and bold. To left-align it (like regular text):

```html
<style>
  th {
    text-align: left;
  }
</style>
```

**Expected output:** Header text is aligned left, matching the alignment of data cells.

### Header That Spans Multiple Columns

Sometimes one header label applies to multiple columns. For example, "Name" might cover both "First Name" and "Last Name". Use the `colspan` attribute:

```html
<table>
  <tr>
    <th colspan="2">Name</th>  <!-- spans 2 columns -->
    <th>Age</th>
  </tr>
  <tr>
    <td>Jill</td>
    <td>Smith</td>
    <td>50</td>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td>
    <td>94</td>
  </tr>
</table>
```

**What `colspan="2"` does:** The "Name" header cell stretches horizontally to cover 2 columns instead of 1.

**Expected output:**

```
     Name          Age    ← "Name" stretches across 2 columns
First Name  Last Name
Jill        Smith   50
Eve         Jackson 94
```

We will explore `colspan` and its vertical equivalent `rowspan` in detail in Part 7.

### Adding a Table Caption

A `<caption>` tag adds a title above the table (or sometimes below, depending on CSS):

```html
<table style="width: 100%">
  <caption>Monthly Savings</caption>
  <tr>
    <th>Month</th>
    <th>Savings</th>
  </tr>
  <tr>
    <td>January</td>
    <td>$100</td>
  </tr>
  <tr>
    <td>February</td>
    <td>$50</td>
  </tr>
</table>
```

**Important:** `<caption>` must come immediately after the opening `<table>` tag — before any `<tr>` elements.

**Expected output:**

```
        Monthly Savings         ← centred title
Month         Savings
January       $100
February      $50
```

The caption is automatically centred above the table. Captions are great for reports and data documents because they label the table's purpose.

---

## Part 6: Table Padding and Spacing

Now let us talk about the space around and between cell content. There are two separate concepts here: **padding** and **spacing**.

### What is Padding vs Spacing?

Imagine a table cell like a room in a house:

- **Padding** = the distance from the wall to the furniture *inside* the room. It is the gap between the cell border and the cell content (the text).
- **Spacing** = the distance from one room's wall to the next room's wall. It is the gap between one cell and another cell.

### Cell Padding

Cell padding is controlled with the CSS `padding` property on `th` and `td`:

```html
<style>
  th, td {
    padding: 15px;   /* 15px of space on all 4 sides inside the cell */
    border: 1px solid black;
    border-collapse: collapse;
  }
</style>
```

**Expected output:** Each cell has a comfortable 15px gap between its border and its text. Without padding, the text would be squished right against the border.

You can also control each side independently:

```html
<style>
  th, td {
    padding-top: 10px;
    padding-bottom: 20px;
    padding-left: 30px;
    padding-right: 40px;
  }
</style>
```

This gives 10px of space above the text, 20px below, 30px to the left, and 40px to the right inside each cell.

> **Real-world use:** Professional tables on websites usually use at least `padding: 8px 12px` (8px top/bottom, 12px left/right) so the content does not look cramped.

### Cell Spacing

Cell spacing is controlled with `border-spacing` on the `table` element itself. This adds a gap *between* cells:

```html
<style>
  table {
    border-spacing: 30px;   /* 30px gap between each cell */
    border: 1px solid black;
  }
  th, td {
    border: 1px solid black;
  }
</style>
```

**Important:** `border-spacing` only works when `border-collapse` is NOT set to `collapse`. If you use `border-collapse: collapse`, the cells are merged — there is no gap to control.

**Expected output:** Each cell appears separated from its neighbours by a 30-pixel gap.

> **Think about this:** What is the difference between adding more `padding` to cells vs adding more `border-spacing`? 
> - More **padding** makes the content *inside* each cell smaller relative to the cell.
> - More **spacing** makes the cells themselves further apart.

---

## Part 7: Colspan and Rowspan (Merging Cells)

This is one of the most powerful table features. You can make a single cell cover multiple columns or multiple rows — just like "merging cells" in Microsoft Excel or Google Sheets.

### What is Colspan?

`colspan` lets a cell stretch **horizontally** across multiple columns. Think of it as a cell that is "2 columns wide" or "3 columns wide".

**Real-world example:** A table showing a person's contact info where "Name" covers both "First Name" and "Last Name" columns.

#### Colspan Example

```html
<table style="width:100%">
  <tr>
    <th colspan="2">Name</th>   <!-- stretches across 2 columns -->
    <th>Age</th>
  </tr>
  <tr>
    <td>Jill</td>
    <td>Smith</td>
    <td>43</td>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td>
    <td>57</td>
  </tr>
</table>
```

**What `colspan="2"` does:** The "Name" cell occupies the space of TWO normal cells. So that row effectively has only 2 things in it: "Name" (spanning 2 columns) + "Age" (1 column) = 3 columns total.

**Expected output:**

```
         Name            Age
First Name   Last Name
Jill         Smith        43
Eve          Jackson      57
```

> **The rule for colspan:** The number of cells in a row must still add up to the total number of columns. If your table has 3 columns, and one cell has `colspan="2"`, that row should have only 2 `<td>` or `<th>` tags (one with colspan=2, one without).

### What is Rowspan?

`rowspan` lets a cell stretch **vertically** across multiple rows. Think of it as a cell that is "2 rows tall" or "3 rows tall".

**Real-world example:** A schedule where "Monday" spans all the time slots for that day.

#### Rowspan Example

```html
<table style="width:100%">
  <tr>
    <th>Name</th>
    <td>Jill</td>
  </tr>
  <tr>
    <th rowspan="2">Phone</th>  <!-- stretches across 2 rows -->
    <td>555-1234</td>
  </tr>
  <tr>
    <td>555-8745</td>
  </tr>
</table>
```

**What `rowspan="2"` does:** The "Phone" header cell occupies the space of TWO rows vertically. So it appears tall, aligned with the row below it as well.

**Expected output:**

```
Name     Jill
Phone    555-1234
         555-8745
```

"Phone" spans both the second and third rows vertically.

> **Common beginner mistake with rowspan:** If a cell has `rowspan="2"`, the NEXT row must have one fewer `<td>` because the rowspanned cell is already occupying that space. Forgetting this causes rows to shift incorrectly.

### Combining Colspan and Rowspan

You can use both in the same table to create complex layouts like timetables or invoice templates:

```html
<table style="width:100%">
  <tr>
    <th colspan="3">First Half of 2024</th>  <!-- spans 3 columns -->
  </tr>
  <tr>
    <th>Month</th>
    <th>Sales</th>
    <th>Profit</th>
  </tr>
  <tr>
    <td rowspan="2">Q1</td>    <!-- spans 2 rows (Jan and Feb) -->
    <td>January</td>
    <td>$5,000</td>
  </tr>
  <tr>
    <td>February</td>
    <td>$4,500</td>
  </tr>
</table>
```

**Expected output:**

```
          First Half of 2024
Month       Sales        Profit
Q1          January      $5,000
            February     $4,500
```

---

## Part 8: Table Styling with CSS

Now let us go beyond basic borders and make your tables look truly professional.

### Zebra Stripes (Alternating Row Colours)

One of the most common and readable table styles is "zebra striping" — alternating light and slightly darker rows. This makes it much easier to scan across long rows of data.

```html
<style>
  table {
    width: 100%;
    border-collapse: collapse;
  }
  th, td {
    padding: 10px;
    text-align: left;
  }
  tr:nth-child(even) {
    background-color: #D6EEEE;
  }
</style>

<table>
  <tr>
    <th>#</th>
    <th>Name</th>
    <th>Score</th>
  </tr>
  <tr>
    <td>1</td>
    <td>Alice</td>
    <td>95</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Bob</td>
    <td>88</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Carol</td>
    <td>91</td>
  </tr>
  <tr>
    <td>4</td>
    <td>David</td>
    <td>77</td>
  </tr>
</table>
```

**What `tr:nth-child(even)` means:** Select every even-numbered `<tr>` (rows 2, 4, 6, 8...) and apply the background colour. Row 1 (the header), row 3, and row 5 remain uncoloured.

**Expected output:** Rows 2 (Bob) and 4 (David) have a light teal background. Rows 1, 3, 5 have a white background. This creates the "zebra" pattern.

> **Tip:** If you use `nth-child(odd)` instead, the colouring applies to rows 1, 3, 5 etc.

### Vertical Zebra Stripes (Column Colouring)

You can also stripe COLUMNS instead of rows:

```html
<style>
  td:nth-child(even), th:nth-child(even) {
    background-color: #D6EEEE;
  }
</style>
```

**Expected output:** Every second column is tinted — columns 2 and 4 have colour, columns 1 and 3 are plain. This works well for wide tables with many columns.

### Combined Zebra Stripes

Combine both to create a grid-like checkered pattern. Use a transparent colour so where rows and columns overlap, the colours blend:

```html
<style>
  tr:nth-child(even) {
    background-color: rgba(150, 212, 212, 0.4);
  }

  th:nth-child(even), td:nth-child(even) {
    background-color: rgba(150, 212, 212, 0.4);
  }
</style>
```

**What `rgba()` does:** `rgba(150, 212, 212, 0.4)` is the same teal colour at 40% opacity (transparency). Where a coloured row AND a coloured column overlap, the two transparent teal layers blend together, creating a slightly darker teal at the intersections.

**Expected output:** A visually appealing grid where every other row is lightly tinted, every other column is lightly tinted, and intersecting cells are slightly darker.

### Horizontal Dividers (Row-only Borders)

Instead of borders on all sides, you can add borders only at the bottom of each row for a cleaner, minimalist look:

```html
<style>
  table {
    width: 100%;
    border-collapse: collapse;
  }
  th, td {
    padding: 12px;
    text-align: left;
  }
  tr {
    border-bottom: 1px solid #ddd;
  }
</style>

<table>
  <tr>
    <th>First Name</th>
    <th>Last Name</th>
    <th>Savings</th>
  </tr>
  <tr>
    <td>Peter</td>
    <td>Griffin</td>
    <td>$100</td>
  </tr>
  <tr>
    <td>Lois</td>
    <td>Griffin</td>
    <td>$150</td>
  </tr>
  <tr>
    <td>Joe</td>
    <td>Swanson</td>
    <td>$300</td>
  </tr>
</table>
```

**Expected output:** Each row has a thin grey line below it. No side borders on individual cells. This is a popular modern "flat design" table style used on most professional websites today.

### Hoverable Table Rows

Add an interactive highlight when the user moves their mouse over a row:

```html
<style>
  tr:hover {
    background-color: #D6EEEE;
  }
</style>
```

**What `:hover` means:** This is a CSS "pseudo-class" that applies when the user's mouse pointer is over the element. When the mouse moves over any row, that row turns teal.

**Expected output:** As you move your mouse over different rows in the browser, each row you hover over turns teal. Moving away removes the colour.

> **Real-world use:** Hoverable rows make tables feel interactive and help users track which row they are reading, especially in wide tables.

---

## Part 9: Table Colgroup — Styling Entire Columns

`<colgroup>` is a special element that lets you apply styles to entire columns without adding `style=""` to every single cell. This is a big time-saver!

### Why Do We Need Colgroup?

Imagine a table with 50 rows and 4 columns. You want the first column to have a yellow background. Without `<colgroup>`, you would have to add `style="background-color: yellow"` to 50 individual `<td>` elements. With `<colgroup>`, you do it once.

### Basic Colgroup Usage

Place `<colgroup>` immediately after `<table>` (and after `<caption>`, if present) — before any rows:

```html
<table style="width: 100%">
  <colgroup>
    <col span="2" style="background-color: #D6EEEE">
  </colgroup>
  <tr>
    <th>MON</th>
    <th>TUE</th>
    <th>WED</th>
    <th>THU</th>
    <th>FRI</th>
  </tr>
  <tr>
    <td>1</td>
    <td>2</td>
    <td>3</td>
    <td>4</td>
    <td>5</td>
  </tr>
</table>
```

**Breaking down the `<colgroup>` section:**
- `<colgroup>` — A container for column definitions. It wraps all `<col>` elements.
- `<col span="2" style="background-color: #D6EEEE">` — This single `<col>` element targets 2 columns (MON and TUE) and gives them a teal background.
- `span="2"` — Means "apply this style to 2 columns". Without `span`, it only affects 1 column.
- `style="background-color: #D6EEEE"` — The CSS style to apply.

**Expected output:** The Monday and Tuesday columns have a teal background throughout all rows. Wednesday, Thursday, and Friday remain plain white.

### Multiple Col Elements

Style different groups of columns differently by using multiple `<col>` elements:

```html
<table style="width: 100%">
  <colgroup>
    <col span="2" style="background-color: #D6EEEE">  <!-- MON, TUE = teal -->
    <col span="3" style="background-color: pink">     <!-- WED, THU, FRI = pink -->
  </colgroup>
  <tr>
    <th>MON</th>
    <th>TUE</th>
    <th>WED</th>
    <th>THU</th>
    <th>FRI</th>
  </tr>
</table>
```

**Expected output:** The first two columns (MON, TUE) are teal, and the next three (WED, THU, FRI) are pink.

### Skipping Columns (Empty Col)

To style only the *middle* columns (not the first ones), insert an empty `<col>` for the columns you want to skip:

```html
<table style="width: 100%">
  <colgroup>
    <col span="3">  <!-- Skip the first 3 columns (no style applied) -->
    <col span="2" style="background-color: pink">  <!-- Style columns 4 and 5 -->
  </colgroup>
  <tr>
    <th>MON</th>
    <th>TUE</th>
    <th>WED</th>
    <th>THU</th>
    <th>FRI</th>
  </tr>
</table>
```

**What `<col span="3">` does:** Declares that the first 3 columns exist, but applies no style to them. This is a "placeholder" that tells the browser to skip ahead 3 columns.

**Expected output:** MON, TUE, and WED have no background colour. THU and FRI have a pink background.

### Hiding Columns

Use `visibility: collapse` to hide entire columns from view (but keep the table structure intact):

```html
<table style="width: 100%">
  <colgroup>
    <col span="2">  <!-- First 2 columns: visible -->
    <col span="3" style="visibility: collapse">  <!-- Columns 3, 4, 5: hidden -->
  </colgroup>
  <tr>
    <th>MON</th>
    <th>TUE</th>
    <th>WED</th>
    <th>THU</th>
    <th>FRI</th>
  </tr>
</table>
```

**Expected output:** Only MON and TUE columns are visible. WED, THU, and FRI are hidden. The rows that contained data for those days simply disappear.

> **Use case:** In a responsive web design, you might hide certain columns on small screens (like mobile phones) and show them on larger screens (like laptops).

### Legal CSS Properties for Colgroup

Only a limited set of CSS properties work inside `<col>` and `<colgroup>`:
- `width`
- `visibility`
- `background` properties (`background-color`, `background-image`, etc.)
- `border` properties

Other CSS properties like `font-size`, `color`, `padding`, and `text-align` **will not work** on `<col>` elements. For those, you need to style the `td` and `th` elements directly.

---

## Guided Practice Exercises

### Exercise 1 — Build a Student Grade Table

**Objective:** Create a basic HTML table showing student grades.

**Scenario:** You are a teacher recording results for 4 students across 3 subjects.

**Steps:**

1. Open a text editor and create an HTML file.
2. Add a `<table>` with a `<caption>` that says "Class Results — Term 2".
3. Create a header row with these columns: "Student Name", "Maths", "English", "Science".
4. Add 4 data rows with these values:

| Student Name | Maths | English | Science |
|---|---|---|---|
| Amara | 85 | 90 | 78 |
| Chidi | 72 | 88 | 91 |
| Ngozi | 95 | 83 | 87 |
| Emeka | 60 | 75 | 82 |

5. Add a CSS `<style>` block that:
   - Collapses borders
   - Adds `padding: 10px` to all cells
   - Applies zebra striping to even rows (`background-color: #f2f2f2`)

**Expected output:** A clean, readable grade table with a caption, header row, 4 data rows, and alternating row colours.

**Hints:**
- Remember: `<th>` in the header row, `<td>` in the data rows.
- `caption` goes right after `<table>` and before the first `<tr>`.
- Your zebra stripe CSS: `tr:nth-child(even) { background-color: #f2f2f2; }`

**Self-check questions:**
- Does each row have exactly 4 cells?
- Does "Class Results — Term 2" appear above the table?
- Do the even rows (Chidi and Emeka) have the grey background?

---

### Exercise 2 — Weekend Market Schedule (Rowspan Practice)

**Objective:** Practice using `rowspan` to merge cells vertically.

**Scenario:** A market has different vendors at different times. Some vendors are there all morning.

**Steps:**

Build this table:

| Time | Stall 1 | Stall 2 |
|---|---|---|
| 9:00am | Bread & Baking (rowspan=2) | Fresh Juice |
| 10:00am | (merged above) | Smoothies |
| 11:00am | Vegetables | Spices |

**Code to build this:**

```html
<table style="width: 60%">
  <caption>Weekend Market Schedule</caption>
  <tr>
    <th>Time</th>
    <th>Stall 1</th>
    <th>Stall 2</th>
  </tr>
  <tr>
    <td>9:00am</td>
    <td rowspan="2">Bread &amp; Baking</td>
    <td>Fresh Juice</td>
  </tr>
  <tr>
    <td>10:00am</td>
    <!-- No <td> here for Stall 1 — it is covered by the rowspan above -->
    <td>Smoothies</td>
  </tr>
  <tr>
    <td>11:00am</td>
    <td>Vegetables</td>
    <td>Spices</td>
  </tr>
</table>
```

**Important detail:** Notice `&amp;` instead of `&` in "Bread & Baking". In HTML, you should write `&amp;` to represent the `&` character safely.

**Self-check questions:**
- Does "Bread & Baking" span both the 9:00am and 10:00am rows?
- Does the 10:00am row have only TWO cells instead of THREE? (Because one is covered by the rowspan)
- Is "Vegetables" in its own row alongside "Spices" at 11:00am?

---

### Exercise 3 — Pricing Table (Colspan + Colgroup)

**Objective:** Build a pricing comparison table using colspan for header grouping and colgroup for column styling.

**Scenario:** A software company offers Basic, Pro, and Enterprise plans.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    table {
      width: 80%;
      border-collapse: collapse;
    }
    th, td {
      padding: 12px 15px;
      text-align: center;
      border-bottom: 1px solid #ddd;
    }
    th {
      background-color: #4CAF50;
      color: white;
    }
    tr:hover {
      background-color: #f5f5f5;
    }
  </style>
</head>
<body>

<table>
  <caption>Software Plans Comparison</caption>
  <colgroup>
    <col style="width: 40%">
    <col style="background-color: #e8f5e9">
    <col>
    <col style="background-color: #e8f5e9">
  </colgroup>
  <tr>
    <th>Feature</th>
    <th>Basic — $9/mo</th>
    <th>Pro — $29/mo</th>
    <th>Enterprise — $99/mo</th>
  </tr>
  <tr>
    <td>Storage</td>
    <td>5 GB</td>
    <td>50 GB</td>
    <td>500 GB</td>
  </tr>
  <tr>
    <td>Users</td>
    <td>1</td>
    <td>5</td>
    <td>Unlimited</td>
  </tr>
  <tr>
    <td>Support</td>
    <td>Email</td>
    <td>Priority Email</td>
    <td>24/7 Phone</td>
  </tr>
  <tr>
    <td>Analytics</td>
    <td>Basic</td>
    <td>Advanced</td>
    <td>Custom</td>
  </tr>
</table>

</body>
</html>
```

**Self-check questions:**
- Do the Basic and Enterprise columns have a light green background (from colgroup)?
- Does hovering over a row highlight it in light grey?
- Is the header row green with white text?

---

## Mini Project: Class Weekly Timetable

Let us combine everything you have learned to build a real class schedule — the kind displayed in schools and universities worldwide.

### Project Goal

Build a fully styled weekly class timetable for a fictional school. It should have:
- Time slots as row headers (left column)
- Days of the week as column headers (top row)
- Merged cells where a subject spans two periods
- Zebra-striped rows for readability
- Hover highlighting
- A caption
- Column colouring for the weekend using colgroup

### Stage 1 — Setup and Basic Structure

```html
<!DOCTYPE html>
<html>
<head>
  <title>Class Timetable</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
    }
    table {
      width: 100%;
      border-collapse: collapse;
    }
    caption {
      font-size: 1.4em;
      font-weight: bold;
      margin-bottom: 10px;
    }
    th, td {
      border: 1px solid #ccc;
      padding: 10px 14px;
      text-align: center;
    }
  </style>
</head>
<body>

<table>
  <caption>Grade 10 — Weekly Timetable</caption>
  <tr>
    <th>Time</th>
    <th>Monday</th>
    <th>Tuesday</th>
    <th>Wednesday</th>
    <th>Thursday</th>
    <th>Friday</th>
  </tr>
  <tr>
    <th>8:00 - 9:00</th>
    <td>Maths</td>
    <td>English</td>
    <td>Science</td>
    <td>History</td>
    <td>Art</td>
  </tr>
  <tr>
    <th>9:00 - 10:00</th>
    <td>English</td>
    <td>Maths</td>
    <td>History</td>
    <td>Science</td>
    <td>Music</td>
  </tr>
  <tr>
    <th>Break</th>
    <td colspan="5">⏸ Break Time</td>
  </tr>
  <tr>
    <th>10:30 - 11:30</th>
    <td>Science</td>
    <td>Art</td>
    <td>Maths</td>
    <td>English</td>
    <td>PE</td>
  </tr>
  <tr>
    <th>11:30 - 12:30</th>
    <td>History</td>
    <td>Music</td>
    <td>English</td>
    <td>Maths</td>
    <td>Science</td>
  </tr>
</table>

</body>
</html>
```

**Milestone output:** A full timetable with a header row, time labels in the left column, and "Break Time" spanning all 5 day columns (using `colspan="5"`).

### Stage 2 — Adding Zebra Stripes and Hover

Add these styles to your `<style>` block:

```css
tr:nth-child(even) {
  background-color: #f0f7ff;  /* light blue for even rows */
}

tr:hover {
  background-color: #ffe0b2;  /* orange highlight on hover */
}

/* Make the header row stay green even when hovered */
tr:nth-child(1):hover {
  background-color: #4CAF50;
}
```

**Milestone output:** Even rows have a light blue background. Hovering turns rows orange. The header row stays green.

### Stage 3 — Styling the Header Row

```css
tr:first-child th {
  background-color: #4CAF50;
  color: white;
  font-size: 1.05em;
}

/* Style the left-column time labels */
tr td:first-child, tr th:first-child {
  background-color: #e8f5e9;
  font-weight: bold;
}
```

**Milestone output:** The top header row is green with white text. The left column (time labels) is light green and bold.

### Stage 4 — Complete Final Code

Here is the complete timetable project:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Class Timetable</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 30px;
      background-color: #fafafa;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }

    caption {
      font-size: 1.5em;
      font-weight: bold;
      margin-bottom: 12px;
      color: #333;
    }

    th, td {
      border: 1px solid #ccc;
      padding: 12px 16px;
      text-align: center;
    }

    /* Header row */
    tr:first-child th {
      background-color: #2e7d32;
      color: white;
      font-size: 1.1em;
    }

    /* Left column headers (time labels) */
    td:first-child, tr th:first-child {
      background-color: #e8f5e9;
      font-weight: bold;
      text-align: left;
    }

    /* Zebra stripes */
    tr:nth-child(even) {
      background-color: #f5f9ff;
    }

    /* Break row */
    .break-row td {
      background-color: #fff9c4;
      font-style: italic;
      color: #666;
    }

    /* Hover highlight */
    tr:hover {
      background-color: #ffe0b2;
    }

    /* Keep header row coloured on hover */
    tr:first-child:hover {
      background-color: #2e7d32;
    }
  </style>
</head>
<body>

<table>
  <caption>Grade 10A — Weekly Timetable (Term 2)</caption>
  <colgroup>
    <col style="width: 16%">
    <col style="width: 17%">
    <col style="width: 17%">
    <col style="width: 17%">
    <col style="width: 17%">
    <col style="width: 16%">
  </colgroup>
  <tr>
    <th>Time</th>
    <th>Monday</th>
    <th>Tuesday</th>
    <th>Wednesday</th>
    <th>Thursday</th>
    <th>Friday</th>
  </tr>
  <tr>
    <th>8:00 – 9:00</th>
    <td>Maths</td>
    <td>English</td>
    <td>Science</td>
    <td>History</td>
    <td>Art</td>
  </tr>
  <tr>
    <th>9:00 – 10:00</th>
    <td>English</td>
    <td>Maths</td>
    <td>History</td>
    <td>Science</td>
    <td>Music</td>
  </tr>
  <tr class="break-row">
    <th>10:00 – 10:30</th>
    <td colspan="5">⏸ Morning Break</td>
  </tr>
  <tr>
    <th>10:30 – 11:30</th>
    <td>Science</td>
    <td>Art</td>
    <td>Maths</td>
    <td>English</td>
    <td>PE</td>
  </tr>
  <tr>
    <th>11:30 – 12:30</th>
    <td>History</td>
    <td>Music</td>
    <td>English</td>
    <td>Maths</td>
    <td>Science</td>
  </tr>
  <tr class="break-row">
    <th>12:30 – 1:15</th>
    <td colspan="5">🍽 Lunch Break</td>
  </tr>
  <tr>
    <th>1:15 – 2:15</th>
    <td>Art</td>
    <td>History</td>
    <td>Music</td>
    <td>PE</td>
    <td>Maths</td>
  </tr>
  <tr>
    <th>2:15 – 3:00</th>
    <td>PE</td>
    <td>Science</td>
    <td>Art</td>
    <td>Music</td>
    <td>English</td>
  </tr>
</table>

</body>
</html>
```

**Final milestone output:** A professional-looking, fully styled weekly timetable with green headers, zebra stripes, break rows in yellow, hover highlighting, and column widths controlled by colgroup.

**Reflection questions:**
- How does using `colspan="5"` for the break row save you from writing 5 separate `<td>` tags?
- What would happen if you changed `border-collapse: collapse` to `border-collapse: separate`?
- How would you add a "Saturday" column to this timetable?

**Optional extensions:**
- Add a `rowspan` to combine two periods where a subject takes 2 hours (e.g., a double science period)
- Change the Break rows to use a different border colour
- Add a `<tfoot>` section at the bottom of the table with a note like "Total periods: 35"

---

## Common Beginner Mistakes

### Mistake 1: Forgetting to Add `border-collapse: collapse`

**The problem:**

```css
/* BAD — double borders between cells */
table, th, td {
  border: 1px solid black;
}
```

**The fix:**

```css
/* GOOD — clean single borders */
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
```

Without `border-collapse: collapse`, every cell has its own independent border, causing ugly double lines between adjacent cells.

---

### Mistake 2: Styling Only the `table` Tag, Not `th` and `td`

**The problem:**

```css
/* BAD — only the outer table has a border */
table {
  border: 1px solid black;
}
```

**The fix:**

```css
/* GOOD — all elements get borders */
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
```

The CSS selector must target `table`, `th`, AND `td` to get borders on all parts of the table.

---

### Mistake 3: Wrong Row Count with Rowspan

**The problem:**

```html
<!-- BROKEN: Row 2 has too many cells because we forgot that the rowspan occupies space -->
<tr>
  <td rowspan="2">Category</td>
  <td>Item A</td>
</tr>
<tr>
  <td>Extra Cell (wrong!)</td>  <!-- This pushes cells out of alignment -->
  <td>Item B</td>
</tr>
```

**The fix:**

```html
<!-- CORRECT: Row 2 has one fewer cell because "Category" still covers it -->
<tr>
  <td rowspan="2">Category</td>
  <td>Item A</td>
</tr>
<tr>
  <!-- No cell here for the first column — the rowspan above covers it -->
  <td>Item B</td>
</tr>
```

When a cell has `rowspan="2"`, the following row must have ONE FEWER `<td>` in that position.

---

### Mistake 4: Using `border-spacing` with `border-collapse: collapse`

**The problem:**

```css
/* These two conflict — border-spacing has no effect when borders are collapsed */
table {
  border-collapse: collapse;
  border-spacing: 20px;  /* This does nothing! */
}
```

**The fix:** Use ONE or the OTHER:

```css
/* OPTION A: Collapsed borders (no gap between cells) */
table {
  border-collapse: collapse;
}

/* OPTION B: Separate borders with spacing */
table {
  border-collapse: separate;
  border-spacing: 10px;
}
```

---

### Mistake 5: Placing `<caption>` After the First Row

**The problem:**

```html
<!-- WRONG order -->
<table>
  <tr>
    <th>Name</th>
  </tr>
  <caption>My Table</caption>  <!-- Too late! -->
</table>
```

**The fix:**

```html
<!-- CORRECT order -->
<table>
  <caption>My Table</caption>  <!-- Must be FIRST inside <table> -->
  <tr>
    <th>Name</th>
  </tr>
</table>
```

---

### Mistake 6: Forgetting `colgroup` Must Come Before Rows

**The problem:**

```html
<!-- WRONG: colgroup after rows -->
<table>
  <tr><th>A</th><th>B</th></tr>
  <colgroup>
    <col style="background: yellow">
  </colgroup>
</table>
```

**The fix:**

```html
<!-- CORRECT: colgroup before all rows (but after caption if present) -->
<table>
  <colgroup>
    <col style="background: yellow">
  </colgroup>
  <tr><th>A</th><th>B</th></tr>
</table>
```

---

## Reflection Questions

Think about these questions to deepen your understanding:

1. You have a table with 4 columns and one cell uses `colspan="3"`. How many cells should that row have in total?

2. What is the difference between `padding` and `border-spacing` in a table? Can you explain using a real-world analogy?

3. If you use `rowspan="3"` on a cell in row 1, how many fewer cells do rows 2 and 3 each need to have?

4. Why do we need the `<colgroup>` element at all? Could you achieve the same result a different way?

5. What would a "hoverable table" be useful for on a real website? Give two examples.

6. Why does `visibility: collapse` in a `<col>` element completely remove the column space, while `display: none` on a single `<td>` would not?

---

## Completion Checklist

Before moving to the next lesson, make sure you can do all of the following:

- [ ] Build a basic HTML table from scratch using `<table>`, `<tr>`, `<td>`, and `<th>`
- [ ] Add borders to a table using CSS, with `border-collapse: collapse`
- [ ] Understand the difference between `solid`, `dotted`, `dashed`, and `double` border styles
- [ ] Set a table to 100% width and set specific column widths with `style`
- [ ] Set row heights using the `style` attribute on `<tr>`
- [ ] Add a table caption using `<caption>`
- [ ] Create both horizontal (top) and vertical (left) table headers
- [ ] Add `padding` to cells to create breathing room
- [ ] Use `border-spacing` for gaps between cells (when not using collapse)
- [ ] Use `colspan` to merge cells horizontally across multiple columns
- [ ] Use `rowspan` to merge cells vertically across multiple rows
- [ ] Apply zebra striping with `tr:nth-child(even)`
- [ ] Add horizontal dividers with `border-bottom` on `tr`
- [ ] Add hover effects with `tr:hover`
- [ ] Use `<colgroup>` and `<col>` to style entire columns at once
- [ ] Use `span` on a `<col>` to target multiple columns with one rule
- [ ] Use `visibility: collapse` on a `<col>` to hide a column
- [ ] Build the class timetable mini project

---

## Lesson Summary

In this lesson, you learned everything you need to create professional, well-styled HTML tables. Here is a quick recap of the key concepts:

**Building a table:** Use `<table>` to wrap everything, `<tr>` for rows, `<td>` for data cells, and `<th>` for header cells. Header cells are automatically bold and centred.

**Borders:** Apply borders using the CSS `border` property on `table, th, td`. Always add `border-collapse: collapse` to prevent double borders. You can change border style, radius, and colour with CSS.

**Size:** Control table width with `style="width: 100%"` on `<table>`. Control column width with `style="width: X%"` on `<th>` or `<td>`. Control row height with `style="height: Xpx"` on `<tr>`.

**Headers and Captions:** Use `<caption>` right after `<table>` for a table title. Use `<th>` in the first row for column headers, or in the first cell of each row for row headers. Left-align headers with `text-align: left` in CSS.

**Padding and Spacing:** Use `padding` on `th, td` to add space inside cells. Use `border-spacing` on `table` to add space between cells (only works without `border-collapse: collapse`).

**Colspan and Rowspan:** Use `colspan="n"` on `<th>` or `<td>` to stretch a cell across `n` columns horizontally. Use `rowspan="n"` to stretch a cell across `n` rows vertically.

**Styling:** Use `tr:nth-child(even)` for zebra stripes, `border-bottom` on `tr` for dividers, and `tr:hover` for interactive row highlighting.

**Colgroup:** Use `<colgroup>` before all rows to define column groups, and `<col span="n" style="...">` to apply styles to columns. Only a limited set of CSS properties work (width, visibility, background, border).

You now have a complete toolkit for building any kind of data table on a web page — from simple school reports to complex business dashboards. Great work!
