## HTML (Hypertext Markup Language) – Structure
HTML is the standard markup language used to create and structure the content of webpages. It uses **tags and elements** to define headings, paragraphs, images, links, forms, tables, and other page elements.

### Features of HTML:
- Provides the **skeleton or structure** of a webpage.
- Uses **opening and closing tags** for elements (e.g., `<p>...</p>`).
- Divides content into **head** (meta information, title, scripts) and **body** (visible content).
- Supports **forms, tables, images, links, lists, and multimedia**.
- Human-readable and easy to learn.
- Works with other technologies like CSS and JavaScript to enhance the page.

### Example HTML Document:
```bash
<!DOCTYPE html>
<html>
<head>
    <title>My Page</title>
</head>
<body>
    <h1>Hello World!</h1>
    <p>This is a sample webpage.</p>
</body>
</html>
```

---
## CSS (Cascading Style Sheets) – Styling
CSS is used to **control the presentation, design, and layout** of HTML elements. It separates content (HTML) from design (CSS), allowing web pages to look attractive and consistent.

### Features of CSS:
- Controls **colors, fonts, and typography**.
- Handles **layout** using Flexbox, Grid, or positioning.
- Allows **animations and transitions**.
- Enables **responsive design** with media queries.
- Can be applied **inline, internal, or external**.
- Supports **pseudo-classes** and **pseudo-elements** for advanced styling.

### Example CSS:
```bash
body {
    background-color: #f0f0f0;
    font-family: Arial, sans-serif;
}

h1 {
    color: #333;
    text-align: center;
}

p {
    color: #666;
    line-height: 1.5;
}
```


---
## JavaScript – Behavior

JavaScript is a **programming/scripting language** used to add **interactivity, dynamic behavior, and logic** to webpages. It can manipulate HTML and CSS, respond to user events, and communicate with servers.

## Features of JavaScript:
- Handles **events** like clicks, hovers, or form submissions.
- Can **validate forms** before submission.
- Manipulates the **DOM** (Document Object Model) to dynamically change content.
- Makes asynchronous calls using **AJAX or Fetch API**.
- Can create **interactive components** like sliders, pop-ups, and animations.
- Supports **ES6+ features** such as let/const, arrow functions, classes, and modules.

## Example JavaScript:
```bash
document.getElementById("myBtn").addEventListener("click", function() {
    alert("Button clicked!");
});
```

---
---

## HTML vs CSS vs JavaScript
| Factor                    | HTML                                             | CSS                                                            | JavaScript                                           |
| ------------------------- | ------------------------------------------------ | -------------------------------------------------------------- | ---------------------------------------------------- |
| **Purpose**               | Defines the structure and content of the webpage | Styles and designs HTML elements                               | Adds functionality and interactivity                 |
| **Type**                  | Markup language                                  | Style sheet language                                           | Scripting/programming language                       |
| **Controls**              | Content (text, images, links, tables)            | Visual presentation (colors, fonts, layout)                    | Behavior and logic (events, animations, validations) |
| **Execution**             | Directly interpreted by the browser              | Interpreted after HTML is loaded                               | Interpreted after HTML and CSS are loaded            |
| **Dynamic?**              | No – static content                              | No – static style                                              | Yes – content and behavior can change dynamically    |
| **Syntax**                | Tags and elements (e.g., `<h1>`)                 | Selectors and properties (e.g., `color: red;`)                 | Statements, functions, objects, and variables        |
| **Interaction with User** | Minimal – content is static                      | Indirect – changes look but not behavior                       | Direct – responds to clicks, keypress, mouse events  |
| **Learning Complexity**   | Easy – basic tags                                | Moderate – understanding selectors, layout, and responsiveness | More complex – logic, syntax, DOM manipulation       |
| **File Extension**        | .html                                            | .css                                                           | .js                                                  |
| **Example**               | `<h1>Hello World</h1>`                           | `h1 { color: blue; }`                                          | `document.querySelector('h1').textContent = "Hi";`   |

---
