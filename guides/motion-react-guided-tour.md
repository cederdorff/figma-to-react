# Motion for React Guided Tour

**Rasmus Cederdorff (RACE)**  
Senior Lecturer & Web App Developer  
race@eaaa.dk

---

## Purpose

This guide introduces **Motion for React** as a way to make interaction clearer in a React prototype.

The goal is not to add animation everywhere. The goal is to use motion as feedback:

1. What changed?
2. What can the user interact with?
3. What happened after the interaction?
4. What should the user do next?

Use this guide as a step-by-step classroom tour or as an individual exercise.

Official Motion docs:

- [Motion for React - Get started](https://motion.dev/docs/react)
- [React animation](https://motion.dev/docs/react-animation)
- [Gesture animation](https://motion.dev/docs/react-gestures)

---

## Suggested Teaching Flow

Use this structure if you are introducing Motion live in class.

| Time | Focus | What to show |
| --- | --- | --- |
| 5 min | Why Motion? | Motion as feedback, not decoration |
| 10 min | Install and import | `npm install motion`, `import { motion } from "motion/react"` |
| 15 min | First animation | `initial`, `animate`, `transition` |
| 15 min | React state animation | Animate when state changes |
| 15 min | Gesture animation | `whileHover`, `whileTap`, `drag`, `whileDrag` |
| 30+ min | Student work | Add one useful animation or gesture to an exercise/prototype |

Key question for the whole session:

> Does the motion help the user understand the interaction?

---

## Before You Start

You need:

- A React project
- Node.js and npm installed
- A component you can edit
- Basic understanding of JSX, components, props, state and events

If you do not have a React project yet, create one with Vite:

```bash
npm create vite@latest . -- --template react
npm install
npm run dev
```

---

## Step 1 - Install Motion

Install Motion in your React project:

```bash
npm install motion
```

Import `motion` in the component where you want to animate something:

```jsx
import { motion } from "motion/react";
```

Motion works by giving you animated versions of normal HTML elements:

```jsx
<motion.div />
<motion.button />
<motion.article />
<motion.img />
```

The element still behaves like the normal HTML element. It just gets extra animation props.

---

## Step 2 - Create Your First Motion Component

Start with a simple card.

```jsx
import { motion } from "motion/react";

export default function App() {
  return (
    <main>
      <motion.article
        className="card"
        initial={{ opacity: 0, y: 16 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.35, ease: "easeOut" }}
      >
        <h1>Motion card</h1>
        <p>This card fades in and moves slightly into place.</p>
      </motion.article>
    </main>
  );
}
```

What the props mean:

- `initial` is the starting state.
- `animate` is the state the element animates to.
- `transition` controls timing and feel.
- `y` moves the element on the vertical axis.

Checkpoint:

- Can you make the card start lower?
- Can you make it fade in slower?
- Can you change `y` to `x`?

---

## Step 3 - Animate React State

Motion becomes more useful when it reacts to state changes.

```jsx
import { useState } from "react";
import { motion } from "motion/react";

export default function App() {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <main>
      <motion.button
        className="button"
        onClick={() => setIsOpen(!isOpen)}
        whileTap={{ scale: 0.96 }}
      >
        {isOpen ? "Hide details" : "Show details"}
      </motion.button>

      <motion.section
        className="details"
        animate={{
          opacity: isOpen ? 1 : 0,
          y: isOpen ? 0 : -8,
        }}
        transition={{ duration: 0.25 }}
      >
        <h2>Details</h2>
        <p>The animation now follows React state.</p>
      </motion.section>
    </main>
  );
}
```

Important idea:

> React decides what state the interface is in. Motion helps the user see the change.

Checkpoint:

- Can you add a second animated value?
- Can you make the details slide from the side instead?
- Does the animation make the state change easier to understand?

---

## Step 4 - Add Hover and Tap Feedback

Hover and tap animations are a good place to start because they show affordance: the interface feels interactive.

```jsx
import { motion } from "motion/react";

export default function App() {
  return (
    <main>
      <motion.button
        className="button"
        whileHover={{ scale: 1.06 }}
        whileTap={{ scale: 0.94 }}
        transition={{ type: "spring", stiffness: 420, damping: 18 }}
      >
        Press me
      </motion.button>
    </main>
  );
}
```

Use hover and tap when:

- a button should feel clickable
- a card should feel selectable
- a control should respond immediately to the user

Avoid hover and tap when:

- the motion distracts from the task
- every element starts moving at once
- the animation makes the interface harder to read

Checkpoint:

- Add `whileHover` to a card.
- Add `whileTap` to a button.
- Try a smaller scale effect. Does it feel calmer?

---

## Step 5 - Add Drag

Drag is useful when movement is part of the interaction itself.

```jsx
import { motion } from "motion/react";

export default function App() {
  return (
    <main className="stage">
      <motion.div
        className="drag-card"
        drag
        dragConstraints={{ left: -120, right: 120, top: -40, bottom: 40 }}
        whileDrag={{ scale: 1.06, rotate: 2 }}
      >
        Drag me
      </motion.div>
    </main>
  );
}
```

What the props mean:

- `drag` makes the element draggable.
- `dragConstraints` limits how far it can move.
- `whileDrag` gives feedback while the user is dragging.

Checkpoint:

- Can you limit drag to only the x-axis with `drag="x"`?
- Can you make the card grow while it is dragged?
- Can you make the drag area smaller or larger?

---

## Step 6 - React to Drag Release

A gesture should usually have a result. Did the user drag far enough? Should the item snap back? Should something be accepted or rejected?

```jsx
import { useState } from "react";
import { motion } from "motion/react";

export default function App() {
  const [status, setStatus] = useState("Drag the card");

  function handleDragEnd(event, info) {
    if (info.offset.x > 100) {
      setStatus("Accepted");
    } else if (info.offset.x < -100) {
      setStatus("Rejected");
    } else {
      setStatus("Not far enough");
    }
  }

  return (
    <main className="stage">
      <p>{status}</p>

      <motion.div
        className="drag-card"
        drag="x"
        dragConstraints={{ left: -160, right: 160 }}
        whileDrag={{ scale: 1.05 }}
        onDragEnd={handleDragEnd}
      >
        Swipe me
      </motion.div>
    </main>
  );
}
```

Important idea:

> A gesture is not only movement. It is a decision made through movement.

Checkpoint:

- Change the threshold from `100` to another number.
- Change the status text.
- Add color feedback for accepted and rejected states.

---

## Step 7 - Add Simple CSS

You can use this CSS for the examples:

```css
body {
  background: #08111f;
  color: #f8fafc;
  font-family: Inter, system-ui, sans-serif;
  margin: 0;
}

main,
.stage {
  display: grid;
  min-height: 100vh;
  place-items: center;
}

.card,
.details,
.drag-card {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.28);
  max-width: 360px;
  padding: 24px;
}

.button {
  background: #7dd3fc;
  border: 0;
  border-radius: 8px;
  color: #08111f;
  cursor: pointer;
  font: inherit;
  font-weight: 700;
  padding: 12px 18px;
}

.drag-card {
  cursor: grab;
  text-align: center;
  user-select: none;
}

.drag-card:active {
  cursor: grabbing;
}
```

---

## Step 8 - Apply Motion to Your Own Work

Choose one place in your own prototype where motion could help.

Good places to start:

- opening and closing a detail view
- selecting a card
- switching between steps
- showing success or error
- dragging or swiping an item
- giving feedback after a tap

Before you code, answer:

1. What is the user doing?
2. What changes in the interface?
3. What should the motion help the user understand?
4. Should there be a simpler fallback interaction?

---

## Mini Exercises

Choose one:

### Level 1 - Button Feedback

Add `whileHover` and `whileTap` to one button.

Goal:

- The button should feel interactive.
- The effect should be clear but not distracting.

### Level 2 - Animated Card

Make a card animate in when the page loads.

Use:

- `initial`
- `animate`
- `transition`

Goal:

- The card should enter smoothly.

### Level 3 - State Change

Create a show/hide details interaction.

Use:

- `useState`
- `animate`
- a button click

Goal:

- The user should clearly understand when the details are shown or hidden.

### Level 4 - Drag Interaction

Create a draggable card.

Use:

- `drag`
- `dragConstraints`
- `whileDrag`

Goal:

- The user should understand that the card can be moved.

### Level 5 - Swipe Decision

Create a swipe interaction with a threshold.

Use:

- `drag="x"`
- `onDragEnd`
- `info.offset.x`
- state feedback

Goal:

- Swiping right and left should produce different feedback.

---

## Reflection Questions

Use these questions when testing your animation:

1. Does the motion communicate what changed?
2. Does the motion make the interaction feel easier to understand?
3. Is the animation fast enough to keep the interface responsive?
4. Is the animation calm enough that it does not distract?
5. Would the interaction still work without motion?

---

## Common Problems

### The import does not work

Check that you installed Motion:

```bash
npm install motion
```

Check that the import is exactly:

```jsx
import { motion } from "motion/react";
```

### The element does not animate

Check that:

- the element starts with `motion.`
- `initial`, `animate`, `whileHover`, `whileTap` or `drag` is on the `motion` element
- the value actually changes

### Drag feels strange on touch devices

For touch and pan gestures, you may need to control browser touch behavior with CSS:

```css
.drag-card {
  touch-action: none;
}
```

Use this carefully. Only disable touch scrolling where the gesture needs it.

---

## Official References

- [Motion for React - Get started](https://motion.dev/docs/react)
- [React animation](https://motion.dev/docs/react-animation)
- [Gesture animation](https://motion.dev/docs/react-gestures)

