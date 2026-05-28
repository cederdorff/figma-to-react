# Motion for React Guided Tour

**Rasmus Cederdorff (RACE)**  
Senior Lecturer & Web App Developer  
race@eaaa.dk

---

## Purpose

This guide introduces **Motion for React** as a way to make interaction clearer in a React prototype.

This guide builds on the early React work from **Getting started with React** and **Codeagram**, but you will use a new React project as a blank canvas. That way you can focus on Motion without changing an existing project too early.

React decides what the interface is. Motion helps the user understand what is happening when the interface changes.

The goal is not to add animation everywhere. The goal is to use motion as feedback:

1. What changed?
2. What can the user interact with?
3. What happened after the interaction?
4. What should the user do next?

Key question:

> Does the motion help the user understand the interaction?

Official Motion docs used in this guide:

- [Motion for React - Get started](https://motion.dev/docs/react)
- [React animation](https://motion.dev/docs/react-animation)
- [Gesture animation](https://motion.dev/docs/react-gestures)
- [Drag animation](https://motion.dev/docs/react-drag)
- [Hover animation](https://motion.dev/docs/react-hover-animation)
- [Scroll animation](https://motion.dev/docs/react-scroll-animations)
- [Layout animation](https://motion.dev/docs/react-layout-animations)
- [Transitions](https://motion.dev/docs/react-transitions)

---

## How This Fits With Your Current Work

Use this guide as a small practice project before you add motion to your own work.

The examples are not meant to replace Codeagram or your prototype. They are a safe place to learn the pattern first. After that, you can transfer the same ideas to a post card, image, like button, comment area or swipe interaction in Codeagram.

Each implementation step follows the same rhythm:

1. Add a working solution.
2. Test it in the browser.
3. Compare it with the official Motion documentation.
4. Tweak the values and notice what changes.

---

## Before You Start

This guide uses a new React project so everyone starts from the same blank canvas.

### 1. Create a New React Project

Create a new project folder on your machine. You can name it `motion-react-guided-tour`.

Open that folder in VS Code, and only that folder.

Open the terminal in VS Code.

Run:

```bash
npm create vite@latest . -- --template react
```

Then run:

```bash
npm install
```

Start the project:

```bash
npm run dev
```

Open the local URL in the browser and make sure the blank React app works before you continue.

### 2. Create and View the First Component

Keep the dev server running while you work.

You will now add your first small component. This first version does not use Motion yet. It is a checkpoint you can keep and compare with the animated versions later.

In the VS Code Explorer, open the `src` folder.

Create a new folder inside `src` and name it:

```text
components
```

Inside the new `components` folder, create a new file and name it:

```text
StaticPracticeCard.jsx
```

Your file should now be here:

```text
src/components/StaticPracticeCard.jsx
```

Paste this into `src/components/StaticPracticeCard.jsx`:

```jsx
export default function StaticPracticeCard() {
  return (
    <article className="card">
      <p className="eyebrow">Motion practice</p>
      <h1>Practice card</h1>
      <p>Use this card to practise animation before adding Motion to your own project.</p>
      <button className="button">Like</button>
    </article>
  );
}
```

Replace the content of `src/App.jsx`:

```jsx
import StaticPracticeCard from "./components/StaticPracticeCard";
import "./App.css";

export default function App() {
  return (
    <main className="stage">
      <StaticPracticeCard />
    </main>
  );
}
```

Replace the content of `src/index.css`.

Vite adds some default global styling here. For this guide, replace it with a small reset so it does not fight with your own component styles:

```css
* {
  box-sizing: border-box;
}

html {
  min-width: 320px;
}

body {
  margin: 0;
}

button {
  font: inherit;
}
```

Replace the content of `src/App.css`.

This CSS includes styles for the first card and the later saved Motion examples:

Do not worry if some class names are not used yet. They will be used by the saved components you create later in the guide.

```css
body {
  background: #08111f;
  color: #f8fafc;
  font-family: Inter, system-ui, sans-serif;
  margin: 0;
}

.stage {
  display: grid;
  min-height: 100vh;
  place-items: center;
  padding: 24px;
}

.gallery {
  display: grid;
  gap: 40px;
  justify-items: center;
  padding: 32px 24px;
}

.comparison {
  align-items: start;
  display: grid;
  gap: 24px;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  width: min(1120px, 100%);
}

.card {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.28);
  max-width: 360px;
  padding: 24px;
}

.eyebrow {
  color: #7dd3fc;
  font-size: 0.78rem;
  font-weight: 700;
  margin: 0 0 8px;
  text-transform: uppercase;
}

.button {
  background: #7dd3fc;
  border: 0;
  border-radius: 8px;
  color: #08111f;
  cursor: pointer;
  font: inherit;
  font-weight: 700;
  margin-top: 12px;
  padding: 12px 18px;
}

.details {
  border-top: 1px solid #334155;
  margin-top: 18px;
  overflow: hidden;
  padding-top: 18px;
}

.practice-stack {
  display: grid;
  gap: 16px;
  place-items: center;
  text-align: center;
}

.drag-card {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.28);
  cursor: grab;
  max-width: 360px;
  padding: 24px;
  text-align: center;
  touch-action: none;
  user-select: none;
}

.drag-card:active {
  cursor: grabbing;
}

.progress {
  background: #7ae7c7;
  height: 6px;
  left: 0;
  position: fixed;
  right: 0;
  top: 0;
  transform-origin: 0%;
  z-index: 10;
}

.scroll-page {
  align-content: space-around;
  display: grid;
  gap: 48px;
  margin: 0 auto;
  max-width: 720px;
  min-height: 180vh;
  padding: 120px 24px;
}
```

Save all four files:

```text
src/components/StaticPracticeCard.jsx
src/App.jsx
src/index.css
src/App.css
```

Go back to the browser and check the result.

You should see a dark card in the middle of the page with the heading **Practice card** and a **Like** button.

If you still see the default Vite page, check that `src/App.jsx` was saved and that it imports `StaticPracticeCard` from `./components/StaticPracticeCard`.

The rest of this guide saves each implementation in its own component file. That means you can go back and compare the examples instead of overwriting your work each time.

You do not need to change anything else yet.

Right now, `src/App.jsx` only shows the first component:

```jsx
import StaticPracticeCard from "./components/StaticPracticeCard";
import "./App.css";

export default function App() {
  return (
    <main className="stage">
      <StaticPracticeCard />
    </main>
  );
}
```

In the next steps, you will keep adding new saved components to `App.jsx` so the page becomes a small gallery of everything you have built.

---

## Step 1 - Install Motion

Install Motion in your React project:

```bash
npm install motion
```

Import `motion` in the component where you want to animate something (we'll do it in the next step):

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

Keep `StaticPracticeCard.jsx` exactly as it is.

Now create a new component for the first Motion version. In `App.jsx`, you will show both cards so you can compare the plain React version with the animated Motion version.

In `src/components`, create a new file:

```text
MotionIntroCard.jsx
```

Paste this into `src/components/MotionIntroCard.jsx`:

```jsx
import { motion } from "motion/react";

export default function MotionIntroCard() {
  return (
    <motion.article
      className="card"
      initial={{ opacity: 0, y: 16 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.35, ease: "easeOut" }}
    >
      <p className="eyebrow">Motion practice</p>
      <h1>Motion card</h1>
      <p>This card fades in and moves slightly into place.</p>
      <button className="button">Like</button>
    </motion.article>
  );
}
```

Show both components in `src/App.jsx`:

```jsx
import StaticPracticeCard from "./components/StaticPracticeCard";
import MotionIntroCard from "./components/MotionIntroCard";
import "./App.css";

export default function App() {
  return (
    <main className="gallery">
      <section className="comparison">
        <StaticPracticeCard />
        <MotionIntroCard />
      </section>
    </main>
  );
}
```

Save the files and check the browser. You should see two cards: the static checkpoint and the Motion card. The Motion card should fade in and move slightly into place.

Before you tweak it, compare the example with the official docs:

- [Motion React animation](https://motion.dev/docs/react-animation)

What the props mean:

- `initial` is the starting state.
- `animate` is the state the element animates to.
- `transition` controls timing and feel.
- `y` moves the element on the vertical axis.

Required experiment:

Do at least two of these changes. After each change, save the file and check the browser before you continue.

- Make the card start lower.
- Make it fade in slower.
- Change `y` to `x`.
- Remove `transition` and notice the difference.

When you are done experimenting, choose the version that feels clearest and keep that.

---

## Step 3 - Animate React State

Motion becomes more useful when it reacts to state changes.

React state is used when the interface needs to remember something that can change.

In this example, the card needs to remember whether the details are open or closed.

You will create one state value:

```jsx
const [isOpen, setIsOpen] = useState(false);
```

This means:

- `isOpen` is the current value.
- `setIsOpen` is the function that changes the value.
- `false` means the details start closed.

When the user clicks the button, this line changes the state:

```jsx
onClick={() => setIsOpen(!isOpen)}
```

The `!` means "the opposite of". If `isOpen` is `false`, it becomes `true`. If it is `true`, it becomes `false`.

Motion then uses `isOpen` to decide which values to animate to:

```jsx
opacity: isOpen ? 1 : 0;
```

This means:

- if `isOpen` is `true`, opacity becomes `1`
- if `isOpen` is `false`, opacity becomes `0`

So React decides the state. Motion makes the change visible.

Create a new file:

```text
src/components/RevealDetailsCard.jsx
```

Paste this into `RevealDetailsCard.jsx`:

```jsx
import { useState } from "react";
import { motion } from "motion/react";

export default function RevealDetailsCard() {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <article className="card">
      <p className="eyebrow">Motion practice</p>
      <h1>React state</h1>

      <motion.button className="button" onClick={() => setIsOpen(!isOpen)} whileTap={{ scale: 0.96 }}>
        {isOpen ? "Hide details" : "Show details"}
      </motion.button>

      <motion.section
        className="details"
        initial={false}
        animate={{
          opacity: isOpen ? 1 : 0,
          height: isOpen ? "auto" : 0,
          y: isOpen ? 0 : -8
        }}
        transition={{ duration: 0.25 }}
      >
        <h2>Details</h2>
        <p>The animation now follows React state.</p>
      </motion.section>
    </article>
  );
}
```

Add this component to the gallery in `src/App.jsx`:

```jsx
import StaticPracticeCard from "./components/StaticPracticeCard";
import MotionIntroCard from "./components/MotionIntroCard";
import RevealDetailsCard from "./components/RevealDetailsCard";
import "./App.css";

export default function App() {
  return (
    <main className="gallery">
      <section className="comparison">
        <StaticPracticeCard />
        <MotionIntroCard />
        <RevealDetailsCard />
      </section>
    </main>
  );
}
```

Save the files and check the browser. You should now see three cards. Click the button in the React state card and make sure the details animate in and out.

Before you tweak it, compare the example with the official docs:

- [Motion React animation](https://motion.dev/docs/react-animation)

Important idea:

> React decides what state the interface is in. Motion helps the user see the change.

Good places to use this:

- show/hide post details
- open/close a menu
- reveal a comment area
- show selected or active state
- communicate success or error

Required experiment:

Do at least two of these experiments. After each one, save the file, click the button in the browser, and notice what changed.

You may need to refresh the browser between experiments to make sure you are seeing the newest version.

### Experiment A - Add Scale

In the `animate` prop, add `scale`:

```jsx
animate={{
  opacity: isOpen ? 1 : 0,
  height: isOpen ? "auto" : 0,
  y: isOpen ? 0 : -8,
  scale: isOpen ? 1 : 0.85
}}
```

Question:

> Does the scale make the state change clearer, or does it feel too dramatic?

### Experiment B - Slide From the Side

Change `y` to `x`:

```jsx
animate={{
  opacity: isOpen ? 1 : 0,
  height: isOpen ? "auto" : 0,
  x: isOpen ? 0 : -16
}}
```

Question:

> Does sideways movement fit this interaction better than vertical movement?

### Experiment C - Change the Message

Change the text inside the details section:

```jsx
<h2>More information</h2>
<p>This content is only visible when the card is open.</p>
```

Question:

> Does the text make it obvious what changed when you clicked the button?

### Experiment D - Make the Timing Slower

Change the transition:

```jsx
transition={{ duration: 0.6 }}
```

Question:

> Does the slower animation help, or does it make the interface feel delayed?

When you are done experimenting, choose the version that makes the state change easiest to understand.

---

## Step 4 - Tune the Transition

The `transition` prop controls how an animation feels.

Create a new file:

```text
src/components/SpringTransitionCard.jsx
```

Paste this into `SpringTransitionCard.jsx`:

```jsx
import { motion } from "motion/react";

export default function SpringTransitionCard() {
  return (
    <motion.article
      className="card"
      initial={{ opacity: 0, x: -48 }}
      animate={{ opacity: 1, x: 0 }}
      transition={{
        x: { type: "spring", stiffness: 240, damping: 18 },
        opacity: { duration: 0.2 }
      }}
    >
      <p className="eyebrow">Motion practice</p>
      <h1>Spring transition</h1>
      <p>The movement uses a spring. The opacity uses a short duration.</p>
    </motion.article>
  );
}
```

Add this component to the gallery in `src/App.jsx`:

```jsx
import StaticPracticeCard from "./components/StaticPracticeCard";
import MotionIntroCard from "./components/MotionIntroCard";
import RevealDetailsCard from "./components/RevealDetailsCard";
import SpringTransitionCard from "./components/SpringTransitionCard";
import "./App.css";

export default function App() {
  return (
    <main className="gallery">
      <section className="comparison">
        <StaticPracticeCard />
        <MotionIntroCard />
        <RevealDetailsCard />
        <SpringTransitionCard />
      </section>
    </main>
  );
}
```

Save the files and check the browser. You should now see four saved examples. Refresh the page if you want to replay the spring entry animation.

Before you tweak it, compare the example with the official docs:

- [Motion transitions](https://motion.dev/docs/react-transitions)

Useful transition choices:

- `duration` makes an animation faster or slower.
- `ease` controls the timing curve.
- `type: "spring"` gives a more physical feeling.
- `stiffness` and `damping` tune how firm or bouncy a spring feels.
- Different values can have different transitions.

Required experiment:

Do at least two of these changes. After each change, save the file and refresh the browser to replay the animation.

- Change `stiffness` to `80`, then to `400`.
- Change `damping` to `8`, then to `30`.
- Change the `opacity` duration to `1`.

When you are done experimenting, keep the version that feels responsive but not jumpy.

Rules of thumb:

- Interface feedback should usually be quick.
- Big movement can be slower than small button feedback.
- If users must wait for an animation, it is probably too slow.
- If everything bounces, nothing feels important.

---

## Step 5 - Understand Gestures

Gestures are interactions that happen through the pointer, mouse, keyboard or touch.

Motion supports common UI gestures such as:

- hover
- tap
- drag
- pan
- focus
- in-view

Most gesture feedback uses `while-` props:

```jsx
<motion.button whileHover={{ scale: 1.06 }} whileTap={{ scale: 0.94 }} />
```

Documentation to compare with:

- [Motion gesture animations](https://motion.dev/docs/react-gestures)

Use gestures when they make the interface feel understandable:

- A card can feel selectable.
- A button can feel pressed.
- A draggable element can feel like it is being lifted.
- A swipe can communicate accept, reject, reveal or dismiss.
- A focus animation can help keyboard users see where they are.

Avoid gestures when:

- the gesture hides an important action
- there is no fallback button or visible cue
- the motion is only decoration
- the same gesture means different things in different places

---

## Step 6 - Add Hover and Tap Feedback

Hover and tap are the easiest gestures to add.

Create a new file:

```text
src/components/PressableButton.jsx
```

Paste this into `PressableButton.jsx`:

```jsx
import { motion } from "motion/react";

export default function PressableButton() {
  return (
    <article className="card">
      <p className="eyebrow">Motion practice</p>
      <h1>Button feedback</h1>
      <p>Hover the button, then press it.</p>

      <motion.button
        className="button"
        whileHover={{ scale: 1.06 }}
        whileTap={{ scale: 0.94 }}
        transition={{ type: "spring", stiffness: 420, damping: 18 }}
      >
        Press me
      </motion.button>
    </article>
  );
}
```

Add this component to the gallery in `src/App.jsx`:

```jsx
import StaticPracticeCard from "./components/StaticPracticeCard";
import MotionIntroCard from "./components/MotionIntroCard";
import RevealDetailsCard from "./components/RevealDetailsCard";
import SpringTransitionCard from "./components/SpringTransitionCard";
import PressableButton from "./components/PressableButton";
import "./App.css";

export default function App() {
  return (
    <main className="gallery">
      <section className="comparison">
        <StaticPracticeCard />
        <MotionIntroCard />
        <RevealDetailsCard />
        <SpringTransitionCard />
        <PressableButton />
      </section>
    </main>
  );
}
```

Save the files and check the browser. You should now see five saved examples. Hover and press the button feedback card to test the interaction.

Before you tweak it, compare the example with the official docs:

- [Motion hover animation](https://motion.dev/docs/react-hover-animation)
- [Motion gesture animations](https://motion.dev/docs/react-gestures)

Where this makes sense:

- a comment button
- a card that opens details
- a button in your practice project

Important:

- Hover is useful on desktop, but touch screens do not really have hover.
- Tap should never be the only sign that something is clickable.
- The UI should still be understandable before the user touches it.

Required experiment:

Do at least two of these experiments. After each one, save the file and test the interaction in the browser.

### Experiment A - Make the Hover Stronger

In `PressableButton.jsx`, change `whileHover`:

```jsx
whileHover={{ scale: 1.15 }}
```

Question:

> Is the stronger hover clearer, or does it feel too much?

### Experiment B - Make the Tap Smaller

Change `whileTap`:

```jsx
whileTap={{ scale: 0.85 }}
```

Question:

> Does the button feel pressed, or does it shrink too much?

### Experiment C - Add Hover to the Whole Card

Change the outer `<article>` to `<motion.article>`:

```jsx
<motion.article
  className="card"
  whileHover={{ y: -4 }}
  transition={{ type: "spring", stiffness: 300, damping: 20 }}
>
```

Then change the closing tag:

```jsx
</motion.article>
```

Question:

> Does moving the whole card help users understand that the card is interactive?

### Experiment D - Make the Feedback Calmer

Try smaller values on the button:

```jsx
whileHover={{ scale: 1.03 }}
whileTap={{ scale: 0.97 }}
```

Question:

> Does the calmer version still give enough feedback?

When you are done experimenting, keep the version that gives feedback without feeling too loud.

---

## Step 7 - Add Drag

Drag is useful when movement is part of the interaction itself.

Create a new file:

```text
src/components/DraggableCard.jsx
```

Paste this into `DraggableCard.jsx`:

```jsx
import { motion } from "motion/react";

export default function DraggableCard() {
  return (
    <motion.div
      className="drag-card"
      drag
      dragConstraints={{ left: -120, right: 120, top: -40, bottom: 40 }}
      whileDrag={{ scale: 1.06, rotate: 2 }}
    >
      Drag me
    </motion.div>
  );
}
```

Add this component to the gallery in `src/App.jsx`:

```jsx
import StaticPracticeCard from "./components/StaticPracticeCard";
import MotionIntroCard from "./components/MotionIntroCard";
import RevealDetailsCard from "./components/RevealDetailsCard";
import SpringTransitionCard from "./components/SpringTransitionCard";
import PressableButton from "./components/PressableButton";
import DraggableCard from "./components/DraggableCard";
import "./App.css";

export default function App() {
  return (
    <main className="gallery">
      <section className="comparison">
        <StaticPracticeCard />
        <MotionIntroCard />
        <RevealDetailsCard />
        <SpringTransitionCard />
        <PressableButton />
        <DraggableCard />
      </section>
    </main>
  );
}
```

Save the files and check the browser. You should now see six saved examples. Drag the drag card and notice how it is constrained.

Before you tweak it, compare the example with the official docs:

- [Motion drag animation](https://motion.dev/docs/react-drag)

What the props mean:

- `drag` makes the element draggable.
- `drag="x"` locks the drag to the horizontal axis.
- `drag="y"` locks the drag to the vertical axis.
- `dragConstraints` limits how far it can move.
- `whileDrag` gives feedback while the user is dragging.
- `dragMomentum={false}` removes the inertia after release.
- `dragElastic` controls how stretchy the constraint feels.

Where drag makes sense:

- swipe through cards
- drag a product or content item
- reorder or move something
- scrub through media
- compare before/after states
- reveal extra actions on a list item

Where drag does not make sense:

- important navigation that should be obvious
- forms where users need precision
- actions that need confirmation
- content that also needs normal scrolling

Required experiment:

Do at least two of these experiments. After each one, save the file and drag the card in the browser.

### Experiment A - Lock Drag to One Direction

Change `drag` to `drag="x"`:

```jsx
<motion.div
  className="drag-card"
  drag="x"
  dragConstraints={{ left: -120, right: 120 }}
  whileDrag={{ scale: 1.06, rotate: 2 }}
>
```

Question:

> Does horizontal-only dragging feel more intentional than dragging in every direction?

### Experiment B - Remove Momentum

Add `dragMomentum={false}`:

```jsx
<motion.div
  className="drag-card"
  drag
  dragConstraints={{ left: -120, right: 120, top: -40, bottom: 40 }}
  dragMomentum={false}
  whileDrag={{ scale: 1.06, rotate: 2 }}
>
```

Question:

> Does removing momentum make the card feel easier to control?

### Experiment C - Change the Elastic Feel

Add `dragElastic`:

```jsx
<motion.div
  className="drag-card"
  drag
  dragConstraints={{ left: -120, right: 120, top: -40, bottom: 40 }}
  dragElastic={0.05}
  whileDrag={{ scale: 1.06, rotate: 2 }}
>
```

Then try:

```jsx
dragElastic={0.6}
```

Question:

> Which value feels more controlled? Which value feels more playful?

### Experiment D - Change the Drag Feedback

Change `whileDrag`:

```jsx
whileDrag={{ scale: 1.12, rotate: 6 }}
```

Then try a calmer version:

```jsx
whileDrag={{ scale: 1.03, rotate: 0 }}
```

Question:

> How much feedback does the user need to understand that the card is being dragged?

When you are done experimenting, keep the version that feels most controlled.

---

## Step 8 - React to Drag Release

A gesture should usually have a result. Did the user drag far enough? Should the item snap back? Should something be accepted or rejected?

Create a new file:

```text
src/components/SwipeDecisionCard.jsx
```

Paste this into `SwipeDecisionCard.jsx`:

```jsx
import { useState } from "react";
import { motion } from "motion/react";

export default function SwipeDecisionCard() {
  const [status, setStatus] = useState("Drag the card");

  function handleDragEnd(_event, info) {
    if (info.offset.x > 100) {
      setStatus("Accepted");
    } else if (info.offset.x < -100) {
      setStatus("Rejected");
    } else {
      setStatus("Not far enough");
    }
  }

  return (
    <section className="practice-stack">
      <p>{status}</p>

      <motion.div
        className="drag-card"
        drag="x"
        dragConstraints={{ left: -160, right: 160 }}
        dragMomentum={false}
        whileDrag={{ scale: 1.05 }}
        onDragEnd={handleDragEnd}
      >
        Swipe me
      </motion.div>
    </section>
  );
}
```

Add this component to the gallery in `src/App.jsx`:

```jsx
import StaticPracticeCard from "./components/StaticPracticeCard";
import MotionIntroCard from "./components/MotionIntroCard";
import RevealDetailsCard from "./components/RevealDetailsCard";
import SpringTransitionCard from "./components/SpringTransitionCard";
import PressableButton from "./components/PressableButton";
import DraggableCard from "./components/DraggableCard";
import SwipeDecisionCard from "./components/SwipeDecisionCard";
import "./App.css";

export default function App() {
  return (
    <main className="gallery">
      <section className="comparison">
        <StaticPracticeCard />
        <MotionIntroCard />
        <RevealDetailsCard />
        <SpringTransitionCard />
        <PressableButton />
        <DraggableCard />
        <SwipeDecisionCard />
      </section>
    </main>
  );
}
```

Save the files and check the browser. You should now see seven saved examples. In the swipe card, drag right, drag left, and try a small drag that is not far enough.

Before you tweak it, compare the example with the official docs:

- [Motion drag animation](https://motion.dev/docs/react-drag)

How `handleDragEnd` works:

```jsx
function handleDragEnd(_event, info) {
  if (info.offset.x > 100) {
    setStatus("Accepted");
  } else if (info.offset.x < -100) {
    setStatus("Rejected");
  } else {
    setStatus("Not far enough");
  }
}
```

The function runs when the user lets go of the draggable card because it is connected here:

```jsx
onDragEnd = { handleDragEnd };
```

Motion gives the function two values:

- `_event` is the browser event. This example does not use it, so the name starts with `_`.
- `info` contains information about the drag movement.

This line checks how far the card was dragged horizontally:

```jsx
info.offset.x;
```

Think of `info.offset.x` like this:

- a positive number means the card moved to the right
- a negative number means the card moved to the left
- a number close to `0` means the card did not move very far

The number `100` is the threshold. The user must drag more than `100` pixels to the right to get **Accepted**, or more than `100` pixels to the left to get **Rejected**.

Important idea:

> A gesture is not only movement. It is a decision made through movement.

Where this makes sense:

- swipe right to save
- swipe left to dismiss
- drag far enough to confirm
- pull a card to reveal more information
- drag a ticket, product or image into a selected area

Be careful:

- Give the user a visible cue before the gesture.
- Provide a fallback button if the action is important.
- Use clear feedback after release.
- Do not make destructive actions too easy to trigger by accident.

Required experiment:

Do at least two of these experiments. After each one, save the file and test a short drag, a left drag, and a right drag.

### Experiment A - Change the Threshold

Make the swipe easier by changing `100` to `60`:

```jsx
if (info.offset.x > 60) {
  setStatus("Accepted");
} else if (info.offset.x < -60) {
  setStatus("Rejected");
} else {
  setStatus("Not far enough");
}
```

Then make the swipe harder by trying `140`.

Question:

> Which threshold feels fair? When does the interaction become too easy or too hard?

### Experiment B - Change the Feedback Text

Change the status messages:

```jsx
setStatus("Saved");
```

```jsx
setStatus("Dismissed");
```

```jsx
setStatus("Try dragging farther");
```

Question:

> Do the new words make the result easier to understand?

### Experiment C - Add Fallback Buttons

Add these buttons below the draggable card (and inside `section`):

```jsx
<div>
  <button className="button" onClick={() => setStatus("Accepted")}>
    Accept
  </button>
  <button className="button" onClick={() => setStatus("Rejected")}>
    Reject
  </button>
</div>
```

Question:

> Why is it helpful to have buttons as a fallback for a drag gesture?

### Experiment D - Show the Drag Distance

Add one more state value:

```jsx
const [distance, setDistance] = useState(0);
```

Update it inside `handleDragEnd`:

```jsx
function handleDragEnd(_event, info) {
  setDistance(Math.round(info.offset.x));

  if (info.offset.x > 100) {
    setStatus("Accepted");
  } else if (info.offset.x < -100) {
    setStatus("Rejected");
  } else {
    setStatus("Not far enough");
  }
}
```

Show the value under the status:

```jsx
<p>Distance: {distance}px</p>
```

Question:

> Does seeing the distance make the threshold easier to understand?

When you are done experimenting, keep the version where the result is clearest.

---

## Step 9 - Add Layout Animation

Layout animation helps when the size or position of an element changes.

This is useful for:

- expanding a card
- opening details in a list
- changing a grid
- moving an active underline in navigation
- showing a selected item

The simplest version is the `layout` prop.

Create a new file:

```text
src/components/ExpandingCard.jsx
```

Paste this into `ExpandingCard.jsx`:

```jsx
import { useState } from "react";
import { motion } from "motion/react";

export default function ExpandingCard() {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <motion.article className="card" layout transition={{ layout: { duration: 0.3 } }}>
      <p className="eyebrow">Motion practice</p>
      <motion.h1 layout>User details</motion.h1>

      <motion.button className="button" layout onClick={() => setIsOpen(!isOpen)} whileTap={{ scale: 0.96 }}>
        {isOpen ? "Hide details" : "Show details"}
      </motion.button>

      {isOpen && <motion.p layout>Extra information appears here. The card smoothly changes size.</motion.p>}
    </motion.article>
  );
}
```

Add this component to the gallery in `src/App.jsx`:

```jsx
import StaticPracticeCard from "./components/StaticPracticeCard";
import MotionIntroCard from "./components/MotionIntroCard";
import RevealDetailsCard from "./components/RevealDetailsCard";
import SpringTransitionCard from "./components/SpringTransitionCard";
import PressableButton from "./components/PressableButton";
import DraggableCard from "./components/DraggableCard";
import SwipeDecisionCard from "./components/SwipeDecisionCard";
import ExpandingCard from "./components/ExpandingCard";
import "./App.css";

export default function App() {
  return (
    <main className="gallery">
      <section className="comparison">
        <StaticPracticeCard />
        <MotionIntroCard />
        <RevealDetailsCard />
        <SpringTransitionCard />
        <PressableButton />
        <DraggableCard />
        <SwipeDecisionCard />
        <ExpandingCard />
      </section>
    </main>
  );
}
```

Save the files and check the browser. You should now see eight saved examples. In the layout card, click the button and watch the card resize.

Before you tweak it, compare the example with the official docs:

- [Motion layout animation](https://motion.dev/docs/react-layout-animations)

Important idea:

> Use `layout` when the layout changes. Use `animate` when a visual value changes.

Required experiment:

Do at least two of these experiments. After each one, save the file and click the button in the browser.

### Experiment A - Slow Down the Layout Change

Change the layout transition:

```jsx
transition={{ layout: { duration: 0.8 } }}
```

Then try a faster version:

```jsx
transition={{ layout: { duration: 0.15 } }}
```

Question:

> Which duration makes the size change easiest to follow?

### Experiment B - Add More Content

Find this block in `ExpandingCard.jsx`:

```jsx
{
  isOpen && <motion.p layout>Extra information appears here. The card smoothly changes size.</motion.p>;
}
```

Replace it with this:

```jsx
{
  isOpen && (
    <motion.div layout>
      <p>Extra information appears here. The card smoothly changes size.</p>
      <p>Layout animation helps the new content feel connected to the card.</p>
    </motion.div>
  );
}
```

Question:

> Does layout animation still feel clear when the card grows more?

### Experiment C - Move the Button Below the Content

This experiment changes the order of the elements inside the card.

The button currently comes before the extra content:

```text
heading
button
extra content
```

In this experiment, change the order to:

```text
heading
extra content
button
```

Find the content inside `<motion.article>`.

It starts here:

```jsx
<p className="eyebrow">Motion practice</p>
```

And ends before this closing tag:

```jsx
</motion.article>
```

Replace that inside part with this:

```jsx
<p className="eyebrow">Motion practice</p>
<motion.h1 layout>User details</motion.h1>

{isOpen && (
  <motion.p layout>
    Extra information appears here. The card smoothly changes size.
  </motion.p>
)}

<motion.button
  className="button"
  layout
  onClick={() => setIsOpen(!isOpen)}
  whileTap={{ scale: 0.96 }}
>
  {isOpen ? "Hide details" : "Show details"}
</motion.button>
```

If you did Experiment B, move the whole `{isOpen && (...)}` block above the button instead. The important part is the order:

```text
extra content first
button after
```

Now the button moves down when the extra content appears.

Question:

> Does the moving button help the layout feel connected, or does it make the interaction harder to use?

### Experiment D - Remove One `layout` Prop

Remove `layout` from the heading:

```jsx
<motion.h1>User details</motion.h1>
```

Question:

> What changes when one element is no longer part of the layout animation?

When you are done experimenting, keep the version where the size change feels easiest to follow.

Good examples from your current work:

- Practice project: expand the `ExpandingCard` details.
- Codeagram later: expand a post, image caption or comment area.
- Your own prototype: expand one card, panel or content section.

---

## Step 10 - Add Scroll Animation

Scroll animation can be useful when the interface has a longer page or a story-like flow.

There are two main types:

- Scroll-triggered: animation starts when an element enters the viewport.
- Scroll-linked: animation follows the scroll position.

### Scroll-triggered Reveal

Create a new file:

```text
src/components/ScrollRevealCard.jsx
```

Paste this into `ScrollRevealCard.jsx`:

```jsx
import { motion } from "motion/react";

export default function ScrollRevealCard({ title, children }) {
  return (
    <motion.article
      className="card"
      initial={{ opacity: 0, y: 24 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true }}
      transition={{ duration: 0.4 }}
    >
      <h2>{title}</h2>
      <p>{children}</p>
    </motion.article>
  );
}
```

Where this makes sense:

- a portfolio page
- a project case page
- an onboarding flow
- a museum or event prototype with sections
- explaining steps in a service flow

Do not use scroll animation just to make a page feel fancy. Use it when it helps pace information.

### Scroll Progress Bar

Create another new file:

```text
src/components/ScrollProgress.jsx
```

Paste this into `ScrollProgress.jsx`:

```jsx
import { motion, useScroll } from "motion/react";

export default function ScrollProgress() {
  const { scrollYProgress } = useScroll();

  return <motion.div className="progress" style={{ scaleX: scrollYProgress, originX: 0 }} />;
}
```

Add the scroll components to the gallery in `src/App.jsx`:

```jsx
import StaticPracticeCard from "./components/StaticPracticeCard";
import MotionIntroCard from "./components/MotionIntroCard";
import RevealDetailsCard from "./components/RevealDetailsCard";
import SpringTransitionCard from "./components/SpringTransitionCard";
import PressableButton from "./components/PressableButton";
import DraggableCard from "./components/DraggableCard";
import SwipeDecisionCard from "./components/SwipeDecisionCard";
import ExpandingCard from "./components/ExpandingCard";
import ScrollProgress from "./components/ScrollProgress";
import ScrollRevealCard from "./components/ScrollRevealCard";
import "./App.css";

export default function App() {
  return (
    <>
      <ScrollProgress />

      <main className="gallery">
        <section className="comparison">
          <StaticPracticeCard />
          <MotionIntroCard />
          <RevealDetailsCard />
          <SpringTransitionCard />
          <PressableButton />
          <DraggableCard />
          <SwipeDecisionCard />
          <ExpandingCard />
        </section>

        <section className="scroll-page">
          <ScrollRevealCard title="Plan">Motion can pace longer content.</ScrollRevealCard>

          <ScrollRevealCard title="Reveal">Each card appears when it enters the viewport.</ScrollRevealCard>

          <ScrollRevealCard title="Progress">The bar at the top follows the scroll position.</ScrollRevealCard>
        </section>
      </main>
    </>
  );
}
```

Save the files and check the browser. You should now see the saved example gallery and a scroll section underneath it. Scroll the page and watch the cards appear. The progress bar should move as you scroll.

Before you tweak it, compare the example with the official docs:

- [Motion scroll animation](https://motion.dev/docs/react-scroll-animations)

Required experiment:

Do at least two of these experiments. After each one, save the file and scroll through the page again.

You may need to refresh the browser and scroll from the top of the page to see the reveal again.

### Experiment A - Make the Reveal Movement Larger

In `ScrollRevealCard.jsx`, find this line:

```jsx
initial={{ opacity: 0, y: 24 }}
```

Change it to:

```jsx
initial={{ opacity: 0, y: 80 }}
```

Question:

> Does the larger movement help you notice the reveal, or does it feel too dramatic?

### Experiment B - Let the Reveal Happen More Than Once

In `ScrollRevealCard.jsx`, find this line:

```jsx
viewport={{ once: true }}
```

Change it to:

```jsx
viewport={{ once: false }}
```

Now scroll down, then scroll back up, then scroll down again.

Question:

> Is it helpful that the animation can happen again, or does it become distracting?

### Experiment C - Change the Reveal Speed

In `ScrollRevealCard.jsx`, find this line:

```jsx
transition={{ duration: 0.4 }}
```

Try a slower version:

```jsx
transition={{ duration: 1 }}
```

Then try a faster version:

```jsx
transition={{ duration: 0.15 }}
```

Question:

> Which speed helps the content appear clearly without slowing the page down?

### Experiment D - Change the Progress Bar Color

In `src/App.css`, find `.progress`:

```css
.progress {
  background: #7ae7c7;
```

Change the background color:

```css
background: #fbbf24;
```

Question:

> Does the progress bar still feel helpful, or does the brighter color pull too much attention?

When you are done experimenting, keep the version that helps the page feel clearer.

Where this makes sense:

- a long guide
- a story page
- a multi-section case presentation
- a page where users benefit from knowing progress

---

## Step 11 - Review the Saved Examples

At this point, your `src/components` folder contains several saved implementations:

```text
StaticPracticeCard.jsx
MotionIntroCard.jsx
RevealDetailsCard.jsx
SpringTransitionCard.jsx
PressableButton.jsx
DraggableCard.jsx
SwipeDecisionCard.jsx
ExpandingCard.jsx
ScrollRevealCard.jsx
ScrollProgress.jsx
```

At this point, `src/App.jsx` works as a small gallery of your saved examples.

The card-sized examples live inside the comparison layout:

```jsx
<main className="gallery">
  <section className="comparison">
    <StaticPracticeCard />
    <MotionIntroCard />
    <RevealDetailsCard />
    <SpringTransitionCard />
    <PressableButton />
    <DraggableCard />
    <SwipeDecisionCard />
    <ExpandingCard />
  </section>
</main>
```

The scroll example is different because it needs a longer section. It can sit underneath the card gallery:

```jsx
<main className="gallery">
  <section className="comparison">
    <StaticPracticeCard />
    <MotionIntroCard />
  </section>

  <section className="scroll-page">
    <ScrollRevealCard title="Plan">Motion can pace longer content.</ScrollRevealCard>
  </section>
</main>
```

If the gallery becomes distracting while you work on one experiment, temporarily remove the other components from `App.jsx` and add them back afterwards.

Note about `touch-action`:

- The shared CSS uses `touch-action: none` on `.drag-card`.
- Use that only on elements where a drag gesture needs it.
- Do not disable normal scrolling for the whole page unless you have a very good reason.

---

## Step 12 - Improve Codeagram With Motion

Now move from the practice project into **Codeagram**.

The goal is not to add motion everywhere. The goal is to improve the existing Codeagram interactions:

- posts should feel like they enter the feed intentionally
- like and bookmark should give clear feedback
- motion should support the interface, not decorate it

Open your Codeagram project in VS Code.

The example project used for this guide is here:

```text
/Users/race/Developer/codeagram
```

### 1. Install Motion in Codeagram

Motion was installed in the practice project. Codeagram is a different React project, so it needs its own installation.

In the Codeagram terminal, run:

```bash
npm install motion
```

Start Codeagram:

```bash
npm run dev
```

Check that it still works before editing.

### 2. Find the Best Place to Start

Open this file:

```text
src/components/PostCard.jsx
```

This is the best first place to add Motion because it already has React state:

```jsx
const [liked, setLiked] = useState(false);
const [bookmarked, setBookmarked] = useState(false);
```

React already decides whether a post is liked or bookmarked.

Motion can make those state changes visible.

### 3. Animate Posts Into the Feed

In `src/components/PostCard.jsx`, add this import:

```jsx
import { motion } from "motion/react";
```

Change the outer wrapper from:

```jsx
<div className="post-card">
```

to:

```jsx
<motion.article
  className="post-card"
  initial={{ opacity: 0, y: 24 }}
  whileInView={{ opacity: 1, y: 0 }}
  viewport={{ once: true, amount: 0.2 }}
  transition={{ duration: 0.35, ease: "easeOut" }}
>
```

At the very bottom of the component return, change the final closing tag from:

```jsx
</div>
```

to:

```jsx
</motion.article>
```

This is the closing tag for the outer `post-card` wrapper.

Save and test in the browser.

Scroll through the feed. Each post should fade in and move slightly into place when it enters the viewport.

### 4. Add Feedback to Like and Bookmark

In `PostCard.jsx`, find the like button:

```jsx
<button className="action-button" type="button" onClick={toggleLike}>
  <Heart className={liked ? "is-active" : ""} />
</button>
```

Replace it with:

```jsx
<motion.button
  className="action-button"
  type="button"
  onClick={toggleLike}
  whileTap={{ scale: 0.82 }}
  animate={liked ? { scale: [1, 1.25, 1] } : { scale: 1 }}
  transition={{ duration: 0.25 }}
>
  <Heart className={liked ? "is-active" : ""} />
</motion.button>
```

Find the bookmark button:

```jsx
<button className="action-button post-bookmark" type="button" onClick={toggleBookmark}>
  <Bookmark className={bookmarked ? "is-active" : ""} />
</button>
```

Replace it with:

```jsx
<motion.button
  className="action-button post-bookmark"
  type="button"
  onClick={toggleBookmark}
  whileTap={{ scale: 0.88 }}
  animate={{ y: bookmarked ? -2 : 0 }}
  transition={{ type: "spring", stiffness: 500, damping: 20 }}
>
  <Bookmark className={bookmarked ? "is-active" : ""} />
</motion.button>
```

Save and test in the browser.

Click like and bookmark on several posts.

Ask:

> Does the motion make it clearer that the action happened?

### 5. Required Codeagram Experiment

Do at least two of these experiments. After each one, save the file and test Codeagram in the browser.

#### Experiment A - Tune the Post Reveal

Open:

```text
src/components/PostCard.jsx
```

Find the opening `<motion.article>` for the post card:

```jsx
<motion.article
  className="post-card"
  initial={{ opacity: 0, y: 24 }}
  whileInView={{ opacity: 1, y: 0 }}
  viewport={{ once: true, amount: 0.2 }}
  transition={{ duration: 0.35, ease: "easeOut" }}
>
```

First, change the `initial` line from:

```jsx
initial={{ opacity: 0, y: 24 }}
```

to:

```jsx
initial={{ opacity: 0, y: 60 }}
```

Save and scroll the feed again.

Then change the `transition` line from:

```jsx
transition={{ duration: 0.35, ease: "easeOut" }}
```

to:

```jsx
transition={{ duration: 0.7, ease: "easeOut" }}
```

Question:

> When does the feed feel smooth, and when does it start to feel slow?

#### Experiment B - Tune the Like Feedback

Stay in:

```text
src/components/PostCard.jsx
```

Find the like `<motion.button>`.

It starts like this:

```jsx
<motion.button
  className="action-button"
  type="button"
  onClick={toggleLike}
  whileTap={{ scale: 0.82 }}
  animate={liked ? { scale: [1, 1.25, 1] } : { scale: 1 }}
  transition={{ duration: 0.25 }}
>
```

First, change the `whileTap` line from:

```jsx
whileTap={{ scale: 0.82 }}
```

to:

```jsx
whileTap={{ scale: 0.95 }}
```

Save and click the like button on a post.

Then change the `animate` line from:

```jsx
animate={liked ? { scale: [1, 1.25, 1] } : { scale: 1 }}
```

to:

```jsx
animate={liked ? { scale: [1, 1.1, 1] } : { scale: 1 }}
```

Save and click the like button again.

Question:

> Which version makes the like action feel clear without feeling exaggerated?

#### Experiment C - Add Hover Feedback to Header Buttons

Open:

```text
src/components/HeaderActions.jsx
```

Add this import:

```jsx
import { motion } from "motion/react";
```

Change one header button from:

```jsx
<button className="icon-button" type="button">
  <Search />
</button>
```

to:

```jsx
<motion.button className="icon-button" type="button" whileHover={{ scale: 1.08 }} whileTap={{ scale: 0.92 }}>
  <Search />
</motion.button>
```

Question:

> Does the header feel more responsive, or does this motion compete with the feed?

#### Experiment D - Add Image Hover Feedback

In `PostCard.jsx`, change the post image from:

```jsx
<img className="post-image" src={post.image} />
```

to:

```jsx
<motion.img className="post-image" src={post.image} whileHover={{ scale: 1.02 }} transition={{ duration: 0.2 }} />
```

Question:

> Does this make the image feel interactive? If the image does not do anything when clicked, should it have hover feedback?

### 6. Discuss Drag and Gestures in Codeagram

Codeagram is a feed, so gestures can be useful, but they need to be obvious.

Good places for gestures:

- tap feedback on like and bookmark
- hover feedback on real buttons
- drag or swipe on a post if it has a clear result
- drag to reveal an action such as save, hide or share

Risky places for gestures:

- dragging the image if the image does not do anything
- swipe-to-delete without confirmation
- gestures that fight normal page scrolling
- hover effects on elements that are not clickable

Before adding drag, answer:

1. What does the drag mean?
2. How far does the user need to drag?
3. What feedback appears after release?
4. Is there a button fallback for users who do not discover the gesture?

Optional drag challenge:

Use `PostCard.jsx` to make a horizontal swipe set the post as bookmarked.

This version uses a small Motion Value so the post can move while dragging and then spring back into place after release.

Open:

```text
src/components/PostCard.jsx
```

Find the Motion import:

```jsx
import { motion } from "motion/react";
```

Replace it with these imports:

```jsx
import { animate } from "motion";
import { motion, useMotionValue } from "motion/react";
```

Find the state values:

```jsx
const [liked, setLiked] = useState(false);
const [bookmarked, setBookmarked] = useState(false);
```

Add this line below them:

```jsx
const x = useMotionValue(0);
```

This `x` value stores the horizontal drag position of the post.

Find the existing `toggleBookmark` function:

```jsx
function toggleBookmark() {
  setBookmarked(!bookmarked);
}
```

Add this new function below it:

```jsx
function handleDragEnd(_event, info) {
  if (info.offset.x > 120) {
    setBookmarked(true);
  } else if (info.offset.x < -120) {
    setBookmarked(false);
  }

  animate(x, 0, { type: "spring", stiffness: 500, damping: 30 });
}
```

This means:

- if the post is dragged more than `120` pixels to the right, it becomes bookmarked
- if the post is dragged more than `120` pixels to the left, the bookmark is removed
- if the post is not dragged far enough, nothing changes
- `animate(x, 0, ...)` moves the post back to its normal position after release
- the bookmark button still works as before

Find the opening `<motion.article>`:

```jsx
<motion.article
  className="post-card"
  initial={{ opacity: 0, y: 24 }}
  whileInView={{ opacity: 1, y: 0 }}
  viewport={{ once: true, amount: 0.2 }}
  transition={{ duration: 0.35, ease: "easeOut" }}
>
```

Add the drag props to it:

```jsx
<motion.article
  className="post-card"
  style={{ x }}
  initial={{ opacity: 0, y: 24 }}
  whileInView={{ opacity: 1, y: 0 }}
  viewport={{ once: true, amount: 0.2 }}
  transition={{ duration: 0.35, ease: "easeOut" }}
  drag="x"
  dragConstraints={{ left: -140, right: 140 }}
  dragMomentum={false}
  whileDrag={{ scale: 1.02 }}
  onDragEnd={handleDragEnd}
>
```

If you already changed the `initial` or `transition` values in an earlier experiment, keep your own values. Just add these lines:

```jsx
style={{ x }}
drag="x"
dragConstraints={{ left: -140, right: 140 }}
dragMomentum={false}
whileDrag={{ scale: 1.02 }}
onDragEnd={handleDragEnd}
```

The important parts are:

- `style={{ x }}` connects the post position to the Motion Value
- `drag="x"` only allows horizontal dragging
- `onDragEnd={handleDragEnd}` runs the decision when the user lets go

Save and test.

Drag a post to the right. When you drag far enough and release, the bookmark icon should become active.

Drag the same post to the left. When you drag far enough and release, the bookmark should be removed.

Keep the bookmark button. The drag is an extra shortcut, not the only way to bookmark.

Test:

- drag a post slightly
- drag a post far to the right
- drag a bookmarked post far to the left
- use the bookmark button instead
- try scrolling normally through the feed

Question:

> Does swipe-to-bookmark feel natural in Codeagram, or does it get in the way of scrolling?

### 7. Decide What to Keep

After experimenting, remove any motion that does not help.

Keep motion when it answers one of these questions:

1. What changed?
2. What did I just interact with?
3. Did my action work?
4. What should I look at next?

For Codeagram, the strongest motion is probably:

- post reveal on scroll
- like tap feedback
- bookmark tap feedback

Be careful with:

- hover effects on things that are not clickable
- drag or swipe gestures without fallback buttons
- slow animations in the feed

---

## What to Learn Next

This guide covers the most common Motion concepts for interaction feedback:

- `motion` components
- `initial`, `animate` and `transition`
- React state-driven animation
- hover, tap and drag gestures
- drag release with `onDragEnd`
- layout animation
- scroll-triggered and scroll-linked animation

Motion can do more than this. These are good next concepts when you are ready:

- [AnimatePresence](https://motion.dev/docs/react-animate-presence): animate elements when they are removed from the page.
- [Variants](https://motion.dev/docs/react-animation#variants): organise animation states and reuse them across elements.
- [Staggered animation](https://motion.dev/docs/react-animation#stagger): animate a group of elements one after another.
- [Motion values](https://motion.dev/docs/react-motion-value): track and transform changing values outside normal React state.
- [useReducedMotion](https://motion.dev/docs/react-use-reduced-motion): respect users who prefer less motion.
- [SVG animation](https://motion.dev/docs/react-svg-animation): animate SVG shapes, paths and drawing effects.

You do not need all of these for every project. Start with the motion that helps the user understand what changed.

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

### The animation feels annoying

Try:

- shorter duration
- smaller movement
- lower scale
- less bounce
- using motion only on the most important element

---

## Official References

- [Motion for React - Get started](https://motion.dev/docs/react)
- [React animation](https://motion.dev/docs/react-animation)
- [Gesture animation](https://motion.dev/docs/react-gestures)
- [Drag animation](https://motion.dev/docs/react-drag)
- [Hover animation](https://motion.dev/docs/react-hover-animation)
- [Scroll animation](https://motion.dev/docs/react-scroll-animations)
- [Layout animation](https://motion.dev/docs/react-layout-animations)
- [Transitions](https://motion.dev/docs/react-transitions)
