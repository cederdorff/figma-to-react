# Lottie in React: Figma to Code Guide

**Rasmus Cederdorff (RACE)**  
Senior Lecturer & Web App Developer  
race@eaaa.dk

---

## Purpose

In this guide, you will take a Lottie animation you created in Figma and use it inside a React app.

You will learn how to:

1. Export your animation from Figma to a Lottie `.json` file
2. Load it in React with `lottie-react`
3. Control playback (loop, play, pause)
4. Connect animation to interaction states

---

## What You Build

You build a small React page with:

1. One Lottie animation component
2. Basic controls (play, pause, replay)
3. One interaction state (for example loading, success, or error)

---

## Prerequisites

1. A React + Vite project (you can reuse your Motion project)
2. A Lottie animation exported from Figma
3. Basic React knowledge (components, state, events)

---

## Step 1: Export Lottie from Figma

Use your existing Figma animation.

Export checklist:

1. Export as Lottie `.json`
2. Keep the file name simple, for example `success-check.json`
3. If possible, test the file in a Lottie preview before coding

Suggested folder in your React project:

```text
src/assets/lottie
```

Place your file there, for example:

```text
src/assets/lottie/success-check.json
```

---

## Step 2: Install Lottie in React

In your React project terminal, run:

```bash
npm install lottie-react
```

Run the app to make sure install worked:

```bash
npm run dev
```

---

## Step 3: Render Your First Lottie Component

Create a new component:

```text
src/components/LottiePreviewCard.jsx
```

Add:

```jsx
import { useRef } from "react";
import Lottie from "lottie-react";
import successCheck from "../assets/lottie/success-check.json";

export default function LottiePreviewCard() {
  const lottieRef = useRef();

  return (
    <article className="card">
      <h2>Lottie Preview</h2>

      <Lottie animationData={successCheck} loop={true} lottieRef={lottieRef} style={{ height: 180 }} />

      <div className="controls">
        <button className="button" onClick={() => lottieRef.current?.play()}>
          Play
        </button>
        <button className="button alt" onClick={() => lottieRef.current?.pause()}>
          Pause
        </button>
        <button className="button danger" onClick={() => lottieRef.current?.goToAndPlay(0, true)}>
          Replay
        </button>
      </div>
    </article>
  );
}
```

Now render it in `src/App.jsx`:

```jsx
import "./App.css";
import LottiePreviewCard from "./components/LottiePreviewCard";

export default function App() {
  return (
    <main className="page">
      <h1 className="title">Figma Lottie -> React</h1>
      <p className="subtitle">Load and control a Lottie animation in React.</p>

      <section className="grid">
        <LottiePreviewCard />
      </section>
    </main>
  );
}
```

Test now:

1. Animation renders
2. Play/pause/replay works
3. No console errors for JSON import

---

## Step 4: Connect Lottie to UI State

Now use Lottie as feedback, not just decoration.

Example: animate when an action succeeds.

Update `LottiePreviewCard.jsx`:

```jsx
import { useRef, useState } from "react";
import Lottie from "lottie-react";
import successCheck from "../assets/lottie/success-check.json";

export default function LottiePreviewCard() {
  const lottieRef = useRef();
  const [status, setStatus] = useState("idle");

  function handleCompleteAction() {
    setStatus("success");
    lottieRef.current?.goToAndPlay(0, true);
  }

  return (
    <article className="card">
      <h2>Lottie State Feedback</h2>

      <Lottie
        animationData={successCheck}
        loop={false}
        autoplay={false}
        lottieRef={lottieRef}
        style={{ height: 180 }}
      />

      <div className="controls">
        <button className="button" onClick={handleCompleteAction}>
          Complete action
        </button>
        <button
          className="button alt"
          onClick={() => {
            setStatus("idle");
            lottieRef.current?.stop();
          }}
        >
          Reset
        </button>
      </div>

      <p className="hint">Current status: {status}</p>
    </article>
  );
}
```

What this teaches:

1. Lottie can express state changes
2. Animation should support meaning, not just visual style
3. You control exactly when playback starts/stops

---

## Step 5: Pair Experiment (15 min)

In pairs, test and improve one behavior:

1. Choose one UI event (save, submit, complete, error)
2. Attach one Lottie animation to that event
3. Decide if it should loop, run once, or wait for user action
4. Adjust timing so it feels clear and not noisy

Mini reflection:

1. Did the animation clarify what happened?
2. Was it too much, too little, or just right?

---

## Common Issues

1. **Animation does not render**
   - Check import path to `.json`
   - Verify file is valid Lottie JSON
2. **Buttons do nothing**
   - Confirm `lottieRef` is connected to the `Lottie` component
3. **Animation plays at wrong time**
   - Set `autoplay={false}` and trigger playback manually
4. **Too distracting**
   - Use non-looping playback and trigger only on key events

---

## Extensions

1. Add a second animation for error state
2. Combine Lottie and Motion in the same component
3. Add haptics so visual + tactile feedback match

---

## Wrap-Up

You now have a working Figma-to-React animation workflow:

1. Figma animation intent
2. Lottie JSON export
3. React integration
4. State-based playback control

This is the core pattern for using Lottie as meaningful UX feedback in React.
