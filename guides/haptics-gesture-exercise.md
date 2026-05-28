# Web Haptics + Motion Lab (React + Vite)

**Rasmus Cederdorff (RACE)**  
Senior Lecturer & Web App Developer  
race@eaaa.dk

---

## Goal

In this lab, you will:

1. Create a brand new blank React + Vite project (same way as in [motion-react-guided-tour.md](motion-react-guided-tour.md)).
2. Install and test `web-haptics` in a clean starter project.
3. Build multiple small haptics components and experiment.
4. Install Motion and combine motion + haptics in one interaction.

Reference for haptics patterns:

- [Haptics by Lochie](https://haptics.lochie.me/)

---

## What Web Haptics Is

`web-haptics` is a small library that gives your web app tactile feedback using the browser vibration API.

In practice, this means your UI can "feel" different for different outcomes, for example:

1. Success: short and light confirmation pulse
2. Warning: medium, noticeable pattern
3. Error: stronger pattern

In this lab, you use haptics as communication, not decoration.

`useWebHaptics({ debug: true })` also gives audio feedback on desktop, so you can still test behavior when real vibration is limited.

---

## What You Are Practising

You are not only installing libraries. You are practising interaction design decisions:

1. Which actions deserve feedback?
2. How strong should feedback be?
3. When does feedback help, and when does it annoy?
4. How do motion and haptics reinforce each other?

---

## Step 1: Create a New Blank React + Vite Project

Create a new project folder on your machine. You can name it:

```text
web-haptics-motion
```

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

---

## Step 2: Install Web Haptics and Create a Clean Starter

Why this step matters:

1. A clean starter removes visual noise.
2. You can focus on interaction behavior before complex UI.
3. You get a controlled baseline for testing and comparing patterns.

If your dev server is still running, stop it in the terminal by pressing `Ctrl + C`.

Then continue in the same terminal.

Install package:

```bash
npm install web-haptics
```

Create a components folder:

```text
src/components
```

Reset `src/App.jsx` to a simple baseline:

```jsx
import "./App.css";

export default function App() {
  return (
    <main className="page">
      <h1 className="title">Web Haptics + Motion Lab</h1>
      <p className="subtitle">Starter app is running. Ready for Step 2.</p>
    </main>
  );
}
```

Replace `src/index.css` with:

```css
* {
  box-sizing: border-box;
}

html,
body,
#root {
  margin: 0;
  min-height: 100%;
}

button {
  font: inherit;
}
```

Replace `src/App.css` with:

```css
body {
  background: #09111f;
  color: #e2e8f0;
  font-family: "IBM Plex Sans", "Segoe UI", sans-serif;
}

.page {
  margin: 0 auto;
  max-width: 980px;
  min-height: 100vh;
  padding: 28px 18px 48px;
}

.title {
  font-size: clamp(1.4rem, 2vw, 2rem);
  margin: 0 0 6px;
}

.subtitle {
  color: #94a3b8;
  margin: 0 0 20px;
}

.grid {
  display: grid;
  gap: 16px;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}

.card {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 12px;
  padding: 16px;
}

.card h2 {
  font-size: 1rem;
  margin: 0 0 8px;
}

.hint {
  color: #94a3b8;
  font-size: 0.9rem;
  margin-top: 8px;
}

.controls {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.button {
  background: #0ea5e9;
  border: 0;
  border-radius: 8px;
  color: #041016;
  cursor: pointer;
  font-weight: 700;
  padding: 10px 14px;
}

.button.alt {
  background: #f59e0b;
  color: #101010;
}

.button.danger {
  background: #ef4444;
  color: #fff;
}

.swipe-zone {
  align-items: center;
  background: #111827;
  border: 1px dashed #475569;
  border-radius: 10px;
  display: grid;
  height: 100px;
  margin-top: 10px;
  overscroll-behavior: contain;
  text-align: center;
  touch-action: none;
  -webkit-user-select: none;
  user-select: none;
}

.status {
  color: #7dd3fc;
  margin-top: 10px;
}
```

At the end of this step, run the project again and confirm it still works:

```bash
npm run dev
```

Open the local URL and make sure the app renders without errors before continuing.

### Test on Mobile from Localhost

To test haptics properly, run the app on your phone from your local machine:

1. Make sure your laptop and phone are on the same Wi-Fi network.
2. Start Vite with host enabled:

```bash
npm run dev -- --host
```

3. In the terminal output, find the network URL (for example `http://192.168.1.24:5173`).
4. Open that URL on your phone browser.

If it does not open:

1. Re-check that both devices are on the same network.
2. Temporarily disable VPN.
3. Check local firewall settings.

---

## Step 3: Add Web Haptics Components

In this step, you will build one component at a time and test after each one.

This order is intentional:

1. Presets first, so you understand default behavior.
2. Custom patterns second, so you control the feel.
3. List mapping third, so you connect haptics to real UI actions.

Each mini-test helps you isolate bugs early and learn faster.

### 3.1 First component: presets

What this teaches:

1. How to call `trigger()` from UI events.
2. The difference between built-in semantic presets.

Create `src/components/HapticPresetsCard.jsx`:

```jsx
import { useWebHaptics } from "web-haptics/react";

export default function HapticPresetsCard() {
  const { trigger } = useWebHaptics({ debug: true });

  return (
    <article className="card">
      <h2>Preset Haptics</h2>
      <div className="controls">
        <button className="button" onClick={() => trigger("success")}>
          Success
        </button>
        <button className="button alt" onClick={() => trigger("nudge")}>
          Nudge
        </button>
        <button className="button danger" onClick={() => trigger("error")}>
          Error
        </button>
      </div>
      <p className="hint">Use debug audio on desktop. Test on mobile for real vibration.</p>
    </article>
  );
}
```

Now update `src/App.jsx` so you only render this first component:

```jsx
import "./App.css";
import HapticPresetsCard from "./components/HapticPresetsCard";

export default function App() {
  return (
    <main className="page">
      <h1 className="title">Web Haptics Starter Lab</h1>
      <p className="subtitle">Start with preset haptic feedback patterns.</p>

      <section className="grid">
        <HapticPresetsCard />
      </section>
    </main>
  );
}
```

How `trigger` works:

1. `const { trigger } = useWebHaptics(...)` gives you a function to play haptic feedback.
2. You call `trigger(...)` inside an interaction event such as `onClick`.
3. The value you pass decides the pattern, for example a preset (`"success"`) or a custom array (`[40, 35, 40]`).

Why we create buttons first:

1. Buttons are simple and predictable, so you can test haptics without gesture complexity.
2. Each button maps one action to one feedback type, which makes comparisons easy.
3. This helps you design a clear feedback language before combining with Motion.

Test now:

1. Save files and check the browser.
2. Click each button.
3. Confirm you get feedback from `success`, `nudge`, and `error`.

### 3.2 Second component: custom patterns

What this teaches:

1. How vibration arrays change rhythm and intensity.
2. How to stop an active pattern with `cancel()`.

Required experiment in this part:

1. You must customize at least one pattern array.
2. Test the original and customized version back-to-back.
3. Keep the version that communicates intent more clearly.

Create `src/components/HapticCustomCard.jsx`:

```jsx
import { useWebHaptics } from "web-haptics/react";

export default function HapticCustomCard() {
  const { trigger, cancel } = useWebHaptics({ debug: true });

  return (
    <article className="card">
      <h2>Custom Patterns</h2>
      <div className="controls">
        <button className="button" onClick={() => trigger([40, 35, 40])}>
          Short Double
        </button>
        <button className="button alt" onClick={() => trigger([80, 40, 120])}>
          Ramp
        </button>
        <button className="button danger" onClick={() => cancel()}>
          Cancel
        </button>
      </div>
      <p className="hint">Try editing arrays and compare with haptics.lochie.me references.</p>
    </article>
  );
}
```

Now update `src/App.jsx` and render both components:

```jsx
import "./App.css";
import HapticCustomCard from "./components/HapticCustomCard";
import HapticPresetsCard from "./components/HapticPresetsCard";

export default function App() {
  return (
    <main className="page">
      <h1 className="title">Web Haptics Starter Lab</h1>
      <p className="subtitle">Preset patterns + custom vibration arrays.</p>

      <section className="grid">
        <HapticPresetsCard />
        <HapticCustomCard />
      </section>
    </main>
  );
}
```

Test now:

1. Click `Short Double` and `Ramp`.
2. Change one array value and test again.
3. Press `Cancel` while a longer pattern is running.

Customizing help (do this before moving on):

1. Change only one thing at a time so you can feel what changed.
2. Start with duration values first, then change pauses.
3. Compare each new version against the previous one immediately.

Try these starter edits:

1. Softer confirmation: change `[40, 35, 40]` to `[25, 20, 25]`.
2. Stronger warning: change `[80, 40, 120]` to `[110, 50, 140]`.
3. Sharper rhythm: try `[30, 15, 30, 15, 30]`.

Use this quick decision rule:

1. If it feels noisy, reduce durations.
2. If it feels unclear, increase contrast between short and long patterns.
3. If two patterns feel too similar, change pause timing first.

Mini log (recommended):

```text
Pattern A: [40, 35, 40] -> "clear but a bit heavy"
Pattern B: [25, 20, 25] -> "clear and lighter"
Final: [25, 20, 25]
```

### 3.3 Third component: list interaction mapping

What this teaches (in plain language):

1. A real UI has many actions, not just one button.
2. You choose a haptic meaning per action, then apply it consistently.
3. Users learn your pattern language over time (for example: success always feels similar).

Why this step matters:

1. In 3.1 and 3.2 you tested isolated patterns.
2. In 3.3 you apply patterns inside a small interaction system.
3. This is the bridge from demo code to product-like behavior.

Create `src/components/HapticListCard.jsx`:

```jsx
import { useWebHaptics } from "web-haptics/react";

const items = [
  { label: "Inbox", haptic: "nudge" },
  { label: "Archive", haptic: "success" },
  { label: "Reminder", haptic: "nudge" },
  { label: "Done", haptic: "success" }
];

export default function HapticListCard() {
  const { trigger } = useWebHaptics({ debug: true });

  return (
    <article className="card">
      <h2>List Interactions</h2>
      <div className="controls">
        {items.map((item) => (
          <button key={item.label} className="button" onClick={() => trigger(item.haptic)}>
            {item.label}
          </button>
        ))}
      </div>
      <p className="hint">Map different actions to different haptic intent levels.</p>
    </article>
  );
}
```

Test now:

1. Click all four actions and notice which ones share the same haptic meaning.
2. Change one mapping (for example make `Reminder` use `error`) and evaluate if it still makes sense.
3. Keep the mapping that best matches the action intent.

Now update `src/App.jsx` and render all three components:

```jsx
import "./App.css";
import HapticCustomCard from "./components/HapticCustomCard";
import HapticListCard from "./components/HapticListCard";
import HapticPresetsCard from "./components/HapticPresetsCard";

export default function App() {
  return (
    <main className="page">
      <h1 className="title">Web Haptics Starter Lab</h1>
      <p className="subtitle">Test presets, custom patterns, and UI action mapping.</p>

      <section className="grid">
        <HapticPresetsCard />
        <HapticCustomCard />
        <HapticListCard />
      </section>
    </main>
  );
}
```

Final checkpoint for Step 3:

1. You can trigger haptics from at least 3 components.
2. You can hear debug feedback on desktop.
3. You changed at least one pattern and re-tested it.
4. You can compare patterns on mobile.

---

## Step 4: Experiment and Document

Keep this step simple: choose your final haptic language in 15 minutes.

Use [Haptics by Lochie](https://haptics.lochie.me/) as reference while testing.

### 4.1 Pick 3 final patterns

In `HapticCustomCard`, decide one pattern for each meaning:

1. Confirmation (light)
2. Warning (medium)
3. Error (strong)

Suggested starting point:

1. Confirmation: `[25, 20, 25]`
2. Warning: `[60, 30, 60]`
3. Error: `[110, 40, 110, 40, 110]`

### 4.2 Test quickly

1. Trigger each pattern 5 times.
2. If a pattern feels too heavy, reduce durations.
3. If two patterns feel too similar, increase contrast.

### 4.3 Save your final version

Write this short note:

```text
Confirmation: [ ... ]
Warning: [ ... ]
Error: [ ... ]
Why these work: ...
```

Done means:

1. You can clearly tell the 3 states apart.
2. None of them feel annoying after repeated testing.

---

## Step 5: Install Motion and Combine with Web Haptics

Why combine them:

1. Motion gives visual continuity.
2. Haptics gives tactile confirmation.
3. Together they make outcomes clearer, especially during gesture interactions.

Install Motion:

```bash
npm install motion
```

### 5.1 Start simple: Motion only

Create `src/components/MotionStarterCard.jsx`:

```jsx
import { motion } from "motion/react";

export default function MotionStarterCard() {
  return (
    <article className="card">
      <h2>Motion Starter</h2>
      <motion.button className="button" whileHover={{ scale: 1.05 }} whileTap={{ scale: 0.95 }}>
        Tap me
      </motion.button>
      <p className="hint">First, verify Motion works before adding haptics.</p>
    </article>
  );
}
```

Update `src/App.jsx` and add this new component:

```jsx
import "./App.css";
import HapticCustomCard from "./components/HapticCustomCard";
import HapticListCard from "./components/HapticListCard";
import HapticPresetsCard from "./components/HapticPresetsCard";
import MotionStarterCard from "./components/MotionStarterCard";

export default function App() {
  return (
    <main className="page">
      <h1 className="title">Web Haptics Starter Lab</h1>
      <p className="subtitle">Now adding Motion step by step.</p>

      <section className="grid">
        <HapticPresetsCard />
        <HapticCustomCard />
        <HapticListCard />
        <MotionStarterCard />
      </section>
    </main>
  );
}
```

Test now:

1. Hover and tap the button.
2. Confirm scale animation works.

### 5.2 Add haptics to the simple Motion component

Update `src/components/MotionStarterCard.jsx`:

```jsx
import { motion } from "motion/react";
import { useWebHaptics } from "web-haptics/react";

export default function MotionStarterCard() {
  const { trigger } = useWebHaptics({ debug: true });

  return (
    <article className="card">
      <h2>Motion + Tap Haptics</h2>
      <motion.button
        className="button"
        whileHover={{ scale: 1.05 }}
        whileTap={{ scale: 0.95 }}
        onClick={() => trigger("success")}
      >
        Tap me
      </motion.button>
      <p className="hint">Now one interaction gives both visual and tactile feedback.</p>
    </article>
  );
}
```

Test now:

1. Tap the button repeatedly.
2. Confirm both animation and haptic response happen together.

### 5.3 Move forward: swipe + outcome-based haptics

Create `src/components/HapticMotionSwipeCard.jsx`:

```jsx
import { motion } from "motion/react";
import { useState } from "react";
import { useWebHaptics } from "web-haptics/react";

export default function HapticMotionSwipeCard() {
  const { trigger } = useWebHaptics({ debug: true });
  const [state, setState] = useState("idle");

  function handleDragEnd(_, info) {
    const x = info.offset.x;

    if (x > 70) {
      setState("accepted");
      trigger("success");
      return;
    }

    if (x < -70) {
      setState("rejected");
      trigger("error");
      return;
    }

    setState("maybe");
    trigger("nudge");
  }

  let message = "Swipe left or right";

  if (state === "accepted") message = "Accepted (right swipe)";
  if (state === "rejected") message = "Rejected (left swipe)";
  if (state === "maybe") message = "Not far enough, try again";

  return (
    <article className="card">
      <h2>Motion + Haptics Swipe</h2>

      <motion.div
        className="swipe-zone"
        drag="x"
        dragConstraints={{ left: -120, right: 120 }}
        style={{ touchAction: "none" }}
        whileTap={{ scale: 0.98 }}
        onDragEnd={handleDragEnd}
        animate={{ x: 0 }}
        transition={{ type: "spring", stiffness: 300, damping: 22 }}
      >
        {message}
      </motion.div>

      <p className="status">Outcome: {state}</p>
    </article>
  );
}
```

How this component works:

1. `handleDragEnd` runs when you release the swipe.
2. `info.offset.x` tells how far you dragged on the x-axis.
3. Thresholds decide meaning:

- `x > 70`: accepted -> `success`
- `x < -70`: rejected -> `error`
- otherwise: not far enough -> `nudge`

4. Keeping this logic in `handleDragEnd` (instead of inline JSX) makes the code easier to read and easier to adjust.

What to tweak if needed:

1. Lower thresholds (for example 55) if swipes feel too hard.
2. Raise thresholds (for example 90) if accidental swipes happen too often.
3. Swap haptic presets if the feedback meaning feels wrong.

Update `src/App.jsx` by adding the new card:

```jsx
import "./App.css";
import HapticCustomCard from "./components/HapticCustomCard";
import HapticListCard from "./components/HapticListCard";
import HapticMotionSwipeCard from "./components/HapticMotionSwipeCard";
import HapticPresetsCard from "./components/HapticPresetsCard";
import MotionStarterCard from "./components/MotionStarterCard";

export default function App() {
  return (
    <main className="page">
      <h1 className="title">Web Haptics Starter Lab</h1>
      <p className="subtitle">Now combining web-haptics with Motion gestures.</p>

      <section className="grid">
        <HapticPresetsCard />
        <HapticCustomCard />
        <HapticListCard />
        <MotionStarterCard />
        <HapticMotionSwipeCard />
      </section>
    </main>
  );
}
```

Checkpoint:

1. Basic Motion interaction works (`MotionStarterCard`).
2. Motion + tap haptics works in one component.
3. Drag gesture works in `HapticMotionSwipeCard`.
4. Different swipe outcomes trigger different haptics.

If mobile still scrolls or zooms while dragging:

1. Make sure you are dragging on the swipe card itself, not outside it.
2. Confirm your `motion.div` includes `style={{ touchAction: "none" }}`.
3. Confirm `.swipe-zone` includes both `touch-action: none;` and `overscroll-behavior: contain;`.
4. Restart dev server and reload the page on mobile.

---

## Troubleshooting

If haptics do not trigger:

1. Test on Android Chrome for best support.
2. Make sure trigger calls come from user interaction (click/drag).
3. Keep `{ debug: true }` during development to hear desktop feedback.

If Motion does not work:

1. Verify `npm install motion`.
2. Use `import { motion } from "motion/react";`.

If swiping scrolls instead of drags:

1. Keep `touch-action: none` on swipe target.
2. Keep `drag="x"` and `dragConstraints`.

---

## Deliverables

Submit:

1. A screenshot or short recording of your final lab.
2. Three final haptic mappings (success, warning, error).
3. One Motion + haptics interaction you are most happy with.
4. One thing you would improve next.

---

## Wrap-Up

You now have a clean starter/test project for web haptics,
plus a combined Motion + haptics interaction in the same app.
