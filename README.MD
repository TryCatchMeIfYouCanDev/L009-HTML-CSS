# LESSON NEIN - CSS Layouts and Flexbox Fundamentals #

## 1. Introduction ##
CSS layouts define how HTML elements are organised on a webpage. Understanding layout models — **fixed**, **fluid**, **elastic**, and **hybrid** — is crucial for creating responsive and accessible web designs.

---

## 2. Flexbox Overview ##

### 2.1 Why Flexbox? ###
Before Flexbox, developers relied heavily on `float` for layout positioning, which was complex and error-prone. Flexbox simplifies alignment, spacing, and responsiveness by treating elements as flexible boxes.

### 2.2 Basic Principles ###
- Flexbox always starts from **block-level elements**.  
- An element can be both a **flex container** and a **flex item** inside another container.  
- **Images should not be flex items**, as they can stretch or distort unexpectedly.  
- It is good practice to have a **main flex container** (e.g., a wrapper) that groups all layout elements.

### 2.3 Core Flex Properties ###
```css
body {
  width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-flow: row wrap; /* shorthand for flex-direction + flex-wrap */
}
```
- To place an element on a new line: give it `width: 100%`.
- Horizontal alignment: `justify-content`.
- Vertical alignment: `align-items`.

```css
header {
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
```

---

## 3. CSS Reset ##

### 3.1 What Is a CSS Reset? ###
Browsers apply default styles that differ across platforms. A **CSS Reset** removes these inconsistencies, providing a consistent baseline for all browsers.

### 3.2 Common Resets ###
| Author | Year | Description | Link |
|---------|------|-------------|------|
| **Eric A. Meyer** | 2011 | Classic reset that removes default margins, padding, borders, and font sizes. | [Meyer Reset](http://meyerweb.com/eric/tools/css/reset/) |
| **Yahoo YUI Reset** | 2014 | Lightweight, BSD-licensed reset used in YUI library. | [YUI CSS Reset](https://clarle.github.io/yui3/yui/docs/cssreset/) |
| **Josh Comeau** | 2022 | Modern reset that combines reset and normalization principles. | [Comeau Reset](https://www.joshwcomeau.com/css/custom-css-reset/) |

### 3.3 Implementation Example ###
```css
@import url("reset.css");
```

> Always include your CSS Reset **before** any custom styles, even before the `:root` declaration.

---

## 4. Image and Media Scaling ##

Images that exceed their container’s width will overflow unless restricted. To prevent this, apply:
```css
figure img {
  max-width: 100%;
  display: block; /* Prevents inline spacing issues */
}
```
- `max-width: 100%` ensures images shrink but never stretch beyond their container.
- Avoid using `width: 100%` as it enlarges smaller images and causes pixelation.

---

## 5. Layout Types ##

### 5.1 Fixed (Rigid) Layout ###
A **fixed layout** uses absolute measurements (e.g., `px`) that do not adapt to different viewport sizes.

| Characteristic | Description |
|----------------|--------------|
| **Width** | Set in pixels (e.g., 1200px) |
| **Adaptability** | None — may cause scrollbars |
| **Wrapper** | A centred container with fixed width |

### 5.2 Fluid (Liquid) Layout ###
A **fluid layout** uses relative measurements (percentages) to adapt to the viewport width.

| Property | Description |
|-----------|--------------|
| `max-width` | Limits the maximum container width |
| `%` | Used to define proportional element widths |
| Example Formula | `(child width / parent width) × 100` |

**Example:**
```css
nav ul li {
  width: calc(100% / 6);
}
```

### 5.3 Elastic Layout ###
In an **elastic layout**, not only containers but also **media elements** adapt to their parent’s size using `max-width: 100%`.

| Feature | Description |
|----------|--------------|
| **Scalable media** | Images and videos resize dynamically |
| **Avoid distortion** | Use `max-width`, not `width` |

### 5.4 Hybrid Layout ###
A **hybrid layout** mixes fixed and flexible elements — for example, a static banner alongside fluid content.

| Use Case | Technique |
|-----------|------------|
| Mixed fixed & fluid boxes | Use `calc()` to distribute remaining space |

```css
.main-content {
  width: calc(100% - 300px); /* Adjust around a fixed sidebar */
}
```

---

## 6. Navigation Bar Example ###

### 6.1 HTML Structure ###
```html
<nav>
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">Courses</a></li>
    <li><a href="#">For Companies</a></li>
    <li><a href="#">LabForJob</a></li>
    <li><a href="#">Contacts</a></li>
    <li><a href="#">Open Day</a></li>
  </ul>
</nav>
```

### 6.2 CSS Styling ###
```css
nav ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
  display: flex;
}

nav ul li {
  width: calc(100% / 6);
  background-color: orange;
  border-right: 1px solid #fff;
  text-align: center;
  padding: 1em 0;
}

nav ul li + li {
  border-left: 1px solid #fff;
}

nav ul li:last-child {
  border-right: none;
}

nav ul li a {
  text-decoration: none;
  color: #fff;
  display: block;
}
```

> Avoid using `height` for vertical centring — use padding or Flexbox alignment instead.

---

## 7. CSS Selectors and Pseudo-Classes ##

### 7.1 Structural Selectors ###
- `:first-child`, `:last-child` — work only when elements share the same type.
- `:nth-child(n)` — targets elements based on order.
- `:of-type` — preferred when container children are heterogeneous.

```css
body > div article:last-of-type {
  background-color: yellowgreen;
}
```

---

## 8. Best Practices Summary ##

| Concept | Recommendation |
|----------|----------------|
| **Float** | Avoid for layout — use Flexbox or Grid |
| **Images** | Always `max-width: 100%; display: block;` |
| **Padding vs Height** | Use padding for spacing, not height |
| **CSS Reset** | Always include before any other rule |
| **Responsive Units** | Prefer `%`, `em`, `rem`, and `fr` |
| **Layout Choice** | Match layout type to project needs |

---


**Useful Links**

1. https://meyerweb.com/eric/tools/css/reset/
2. https://clarle.github.io/yui3/yui/docs/cssreset/
3. http://yui.yahooapis.com/3.18.1/build/cssreset-context/cssreset-context-min.css
4. https://en.wikipedia.org/wiki/Responsive_web_design
5. https://alistapart.com/article/responsive-web-design/
6. https://www.joshwcomeau.com/css/custom-css-reset/#our-finished-product-11
7. https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox
8. https://www.w3.org/TR/css-flexbox-1/

*End of Class Notes Summary*