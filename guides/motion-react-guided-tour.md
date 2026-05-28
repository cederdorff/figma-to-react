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

.comparison {
  align-items: start;
  display: grid;
  gap: 24px;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  width: min(760px, 100%);
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

Later, when you want to view a different saved implementation, change two lines in `src/App.jsx`:

1. The `import` line at the top.
2. The component inside `<main className="stage">`.

For example, this shows the first saved component:

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
    <main className="stage">
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

Show this component in `src/App.jsx`:

```jsx
import RevealDetailsCard from "./components/RevealDetailsCard";
import "./App.css";

export default function App() {
  return (
    <main className="stage">
      <RevealDetailsCard />
    </main>
  );
}
```

Save the files and check the browser. Click the button and make sure the details animate in and out.

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

Do at least two of these changes. After each change, save the file, click the button in the browser, and notice what changed.

- Add a second animated value, such as `scale`.
- Make the details slide from the side instead.
- Add different text or colors for open and closed states.

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

Show this component in `src/App.jsx`:

```jsx
import SpringTransitionCard from "./components/SpringTransitionCard";
import "./App.css";

export default function App() {
  return (
    <main className="stage">
      <SpringTransitionCard />
    </main>
  );
}
```

Save the files and check the browser. Refresh the page if you want to see the entry animation again.

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

Show this component in `src/App.jsx`:

```jsx
import PressableButton from "./components/PressableButton";
import "./App.css";

export default function App() {
  return (
    <main className="stage">
      <PressableButton />
    </main>
  );
}
```

Save the files and check the browser. Hover and press the button to test the feedback.

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

Do at least two of these changes. After each change, save the file and test the interaction in the browser.

- Add `whileHover` to `MotionIntroCard`.
- Add `whileTap` to a like button.
- Make the effect smaller until it feels calm.

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

Show this component in `src/App.jsx`:

```jsx
import DraggableCard from "./components/DraggableCard";
import "./App.css";

export default function App() {
  return (
    <main className="stage">
      <DraggableCard />
    </main>
  );
}
```

Save the files and check the browser. Drag the card and notice how it is constrained.

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

Do at least two of these changes. After each change, save the file and drag the card in the browser.

- Limit drag to only the x-axis with `drag="x"`.
- Disable momentum with `dragMomentum={false}`.
- Change `dragElastic` to `0.05`, then `0.6`, and feel the difference.

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

Show this component in `src/App.jsx`:

```jsx
import SwipeDecisionCard from "./components/SwipeDecisionCard";
import "./App.css";

export default function App() {
  return (
    <main className="stage">
      <SwipeDecisionCard />
    </main>
  );
}
```

Save the files and check the browser. Drag right, drag left, and try a small drag that is not far enough.

Before you tweak it, compare the example with the official docs:

- [Motion drag animation](https://motion.dev/docs/react-drag)

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

Do at least two of these changes. After each change, save the file and test a short drag, a left drag, and a right drag.

- Change the threshold from `100` to another number.
- Add color feedback for accepted and rejected states.
- Add a visible fallback button below the card.

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
    <motion.article
      className="card"
      layout
      transition={{ layout: { duration: 0.3 } }}
    >
      <p className="eyebrow">Motion practice</p>
      <motion.h1 layout>User details</motion.h1>

      <motion.button
        className="button"
        layout
        onClick={() => setIsOpen(!isOpen)}
        whileTap={{ scale: 0.96 }}
      >
        {isOpen ? "Hide details" : "Show details"}
      </motion.button>

      {isOpen && (
        <motion.p layout>
          Extra information appears here. The card smoothly changes size.
        </motion.p>
      )}
    </motion.article>
  );
}
```

Show this component in `src/App.jsx`:

```jsx
import ExpandingCard from "./components/ExpandingCard";
import "./App.css";

export default function App() {
  return (
    <main className="stage">
      <ExpandingCard />
    </main>
  );
}
```

Save the files and check the browser. Click the button and watch the card resize.

Before you tweak it, compare the example with the official docs:

- [Motion layout animation](https://motion.dev/docs/react-layout-animations)

Important idea:

> Use `layout` when the layout changes. Use `animate` when a visual value changes.

Required experiment:

Do at least two of these changes. After each change, save the file and click the button in the browser.

- Change the layout transition duration from `0.3` to `0.8`.
- Add another paragraph inside the conditional content.
- Move the button below the conditional content.

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

  return (
    <motion.div
      className="progress"
      style={{ scaleX: scrollYProgress, originX: 0 }}
    />
  );
}
```

Show both scroll components in `src/App.jsx`:

```jsx
import ScrollProgress from "./components/ScrollProgress";
import ScrollRevealCard from "./components/ScrollRevealCard";
import "./App.css";

export default function App() {
  return (
    <>
      <ScrollProgress />

      <main className="scroll-page">
        <ScrollRevealCard title="Plan">
          Motion can pace longer content.
        </ScrollRevealCard>

        <ScrollRevealCard title="Reveal">
          Each card appears when it enters the viewport.
        </ScrollRevealCard>

        <ScrollRevealCard title="Progress">
          The bar at the top follows the scroll position.
        </ScrollRevealCard>
      </main>
    </>
  );
}
```

Save the files and check the browser. Scroll the page and watch the cards appear. The progress bar should move as you scroll.

Before you tweak it, compare the example with the official docs:

- [Motion scroll animation](https://motion.dev/docs/react-scroll-animations)

Required experiment:

Do at least two of these changes. After each change, save the file and scroll through the page again.

- Change `y: 24` to `y: 80` in `ScrollRevealCard`.
- Change `viewport={{ once: true }}` to `viewport={{ once: false }}`.
- Change the progress bar color in `.progress`.

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

You can switch between them by changing the import and rendered component in `src/App.jsx`.

Most examples use this wrapper:

```jsx
<main className="stage">
  <ComponentName />
</main>
```

To compare two saved examples, put them inside the comparison layout:

```jsx
<main className="stage">
  <section className="comparison">
    <StaticPracticeCard />
    <MotionIntroCard />
  </section>
</main>
```

The scroll example is different because it needs a longer page:

```jsx
<main className="scroll-page">
  <ScrollRevealCard title="Plan">
    Motion can pace longer content.
  </ScrollRevealCard>
</main>
```

Note about `touch-action`:

- The shared CSS uses `touch-action: none` on `.drag-card`.
- Use that only on elements where a drag gesture needs it.
- Do not disable normal scrolling for the whole page unless you have a very good reason.

---

## Step 12 - Apply Motion to Your Own Work

First, choose one place in the practice project where motion could help. Later, you can use the same idea in Codeagram or your own prototype.

Good places to start:

- opening and closing a detail view
- selecting a card
- switching between steps
- showing success or error
- dragging or swiping an item
- giving feedback after a tap
- showing progress through a long page
- making a layout change feel continuous

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

### Level 6 - Layout Change

Create a card that expands when clicked.

Use:

- `layout`
- `useState`
- conditional content

Goal:

- The size change should feel connected instead of sudden.

### Level 7 - Scroll Feedback

Create one scroll-triggered reveal or a scroll progress bar.

Use:

- `whileInView` or `useScroll`
- `viewport={{ once: true }}` for one-time reveals

Goal:

- The motion should help the user follow the page, not distract from it.

---

## Reflection Questions

Use these questions when testing your animation:

1. Does the motion communicate what changed?
2. Does the motion make the interaction easier to understand?
3. Is the animation fast enough to keep the interface responsive?
4. Is the animation calm enough that it does not distract?
5. Would the interaction still work without motion?
6. Is there a fallback for users who do not discover the gesture?
7. Does the gesture match the user's mental model of the interface?

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
