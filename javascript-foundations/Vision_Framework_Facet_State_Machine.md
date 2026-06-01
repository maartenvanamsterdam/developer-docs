# Vision Framework — Facet State Machine

## Overview

Each Vision Framework facet represents a single concept with two possible views:

* Archetype
* Essence

Examples:

| Archetype           | Essence       |
| ------------------- | ------------- |
| Creative Building   | Manifestation |
| Curious Exploration | Wonder        |
| Deep Understanding  | Wisdom        |

The state machine controls:

1. Which view is currently visible.
2. Whether the facet is currently transitioning.
3. The fade-out → swap → fade-in animation cycle.

---

# Data Model

Each facet is represented by a single HTML element.

```html
<li
  class="facet"
  data-view="archetype"
  data-transitioning="false"
  data-icon="🍊"
  data-archetype="Creative Building"
  data-essence="Manifestation">
  🍊 Creative Building
</li>
```

---

## Permanent Data

These values never change.

```html
data-icon
data-archetype
data-essence
```

Example:

```html
data-icon="🍊"
data-archetype="Creative Building"
data-essence="Manifestation"
```

These are considered the source of truth for facet content.

---

## Runtime State

### data-view

Determines which representation is currently active.

Possible values:

```html
data-view="archetype"
```

or

```html
data-view="essence"
```

---

### data-transitioning

Determines whether the facet is currently animating.

Possible values:

```html
data-transitioning="false"
```

or

```html
data-transitioning="true"
```

This prevents interaction while a transition is running.

---

# Animation State

The animation uses a CSS class.

```css
.facet-hidden {
  opacity: 0;
}
```

When present:

```html
class="facet facet-hidden"
```

the facet fades out.

When removed:

```html
class="facet"
```

the facet fades in.

---

# Events

The state machine is driven by two browser events:

## click

Triggered by the user.

```javascript
facet.addEventListener("click", ...)
```

## transitionend

Triggered by the browser when a CSS transition completes.

```javascript
facet.addEventListener("transitionend", ...)
```

No timers are used.

The browser determines when transitions are complete.

---

# State Machine

## Idle

Initial state:

```html
data-view="archetype"
data-transitioning="false"
```

Facet is visible and clickable.

---

## User Click

When clicked:

```javascript
if (
  facet.dataset.transitioning === "true"
) {
  return;
}
```

If already transitioning:

```text
Ignore click
```

Otherwise:

```javascript
facet.dataset.transitioning = "true";
facet.classList.toggle("facet-hidden");
```

This starts the fade-out transition.

---

## Fade-Out Complete

Triggered by:

```javascript
transitionend
```

while:

```javascript
facet.classList.contains("facet-hidden")
```

returns:

```javascript
true
```

Meaning:

```text
Fade-out complete
```

Actions:

1. Read facet data.
2. Swap content.
3. Update data-view.
4. Remove facet-hidden.

Example:

```javascript
facet.textContent =
  `${icon} ${essenceName}`;

facet.dataset.view =
  "essence";
```

Then:

```javascript
facet.classList.remove(
  "facet-hidden"
);
```

This starts the fade-in transition.

---

## Fade-In Complete

Triggered by:

```javascript
transitionend
```

while:

```javascript
facet.classList.contains("facet-hidden")
```

returns:

```javascript
false
```

Meaning:

```text
Fade-in complete
```

Actions:

```javascript
facet.dataset.transitioning =
  "false";
```

The facet returns to the idle state.

---

# Complete Flow

```text
Idle
│
├─ data-transitioning=false
│
Click
│
├─ data-transitioning=true
├─ add facet-hidden
│
Fade Out
│
transitionend
│
├─ swap content
├─ update data-view
├─ remove facet-hidden
│
Fade In
│
transitionend
│
├─ data-transitioning=false
│
Idle
```

---

# Design Principles

## DOM as State Container

The DOM stores both:

* content state
* transition state

Examples:

```html
data-view
data-transitioning
```

No external state object is required.

---

## Single Source of Truth

Facet content lives in:

```html
data-icon
data-archetype
data-essence
```

Event handlers always read data directly from the facet.

---

## Event-Driven Architecture

The implementation uses:

```text
click
transitionend
```

instead of:

```text
setTimeout()
```

The browser decides when transitions are complete.

This keeps animation logic synchronized with CSS.

