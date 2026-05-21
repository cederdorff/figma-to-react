# 26-05-2026

[Back to lesson index](../lessons.md)

## Gesture & Motion Design: Touch Gestures as Interface

### Purpose of The Day

In `20-05-2026` you built a React prototype from a Figma design. Most of those prototypes use buttons and clicks. Today we focus on touch gestures in React and ask: when should an interaction be drag, swipe, long press or slide instead of a tap?

We will use **Framer Motion** to replace one key button-based interaction with a gesture — drag, swipe, long press, or slide-to-confirm — and explore how the gesture changes what the interface feels like.

Focus question:

> When is a gesture better than a button?

By the end of the session you will have one gesture-based interaction in your prototype that is discoverable, gives feedback while the user is interacting, and supports your concept.

---

### Preparation

1. **Have your prototype from `20-05-2026` ready**
   - Open it in VS Code and make sure it runs locally.
2. **Install Framer Motion in your project**
   - Run `npm install framer-motion` in your project folder before class.
3. **Identify one candidate interaction**
   - Look at your prototype and pick one key action the user performs (e.g. navigating between screens, confirming something, exploring content).
   - Think about whether drag, swipe, long press or slide-to-confirm might work better than a button for that action.
4. **Bring a phone or use browser mobile preview**
   - Gestures feel different on a touch screen. Be ready to test there.

---

### Agenda

1. **Framing: gestures as interaction model** (~20 min)
   - Recap the prototype from `20-05-2026` and identify interactions currently solved with buttons.
   - Look at a few gesture examples and ask: which user goals are better solved by touch gestures?
   - Introduce Framer Motion: `motion.div`, `drag`, `whileTap`, `whileHover`.
2. **Demo: building a gesture interaction** (~30 min)
   - Live demo on a fresh small example: a swipeable card with drag constraints, threshold detection on `onDragEnd`, snap-back on cancel and a state change on success.
   - Show how to add visual feedback _during_ the interaction, not only after.
3. **Guided build together** (~45 min)
   - Build a small gesture interaction step by step with the class.
   - Focus: drag constraints, thresholds, release states (success / snap-back), and feedback while dragging.
4. **Workshop: add a gesture to your own prototype** (~60 min)
   - Choose the candidate interaction you identified in preparation.
   - Replace or extend it with a Framer Motion gesture.
   - Ask: does the gesture make the action feel more intentional, more physical, or more appropriate for the concept?
5. **Test and share** (~20 min)
   - Test on mobile or browser preview.
   - Share one thing that worked and one thing that still feels off.

---

### Key Concepts

- `motion.div` — the Framer Motion wrapper that enables animation and gesture props
- `drag` / `dragConstraints` — constrain how far an element can be dragged
- `onDragEnd` — check `offset` to decide if the gesture crossed a threshold
- `whileTap` / `whileHover` — visual feedback states during interaction
- `animate` — drive state changes (success, snap-back, reveal) after a gesture completes
- **Affordance** — how does the user know something can be dragged or swiped?
- **Threshold** — how far is far enough for the action to count?

---

### Teacher Run Sheet (What To Do With Students)

If you are unsure what to do in class, follow this exactly.

1. **Kickoff (10 min)**
   - Say this: "Today each group replaces one button interaction with one touch gesture in React."
   - Ask students to show the screen they built in the previous lesson.
   - Ask each group to pick one action: navigate, confirm, reveal, sort, or dismiss.
2. **Mini theory (10 min)**
   - Say this rule: "Gesture is better than button when movement gives meaning."
   - Give 3 examples:
     - Swipe: browse/dismiss
     - Drag: move/place
     - Slide-to-confirm: prevent accidental tap
3. **Live demo (30 min)**
   - Build one swipe card from scratch.
   - Must include: drag constraints, threshold in `onDragEnd`, snap-back, and success state.
   - Show feedback during drag (scale/opacity/label change).
4. **Guided build (30 min)**
   - Students copy your demo first.
   - Checkpoint after 15 min: everyone must have drag working.
   - Checkpoint after 30 min: everyone must have threshold + release behavior.
5. **Apply to own prototype (60 min)**
   - Students implement one gesture in their own project.
   - Require these 4 acceptance criteria:
     - clear affordance (user can see it is draggable/swipeable)
     - live feedback while interacting
     - threshold logic (not every tiny move triggers action)
     - fallback option (tap/button alternative)
6. **Test and share (20 min)**
   - Students test on phone or mobile preview.
   - Pair feedback questions:
     - "Did you understand what to do without explanation?"
     - "Did the gesture feel better than tap? Why?"
   - End with a 1-minute demo per group.

#### Fast Fallback Plan (If Students Get Stuck)

- Track A (beginner): Implement only swipe-to-dismiss card.
- Track B (intermediate): Add slide-to-confirm with success state.
- Track C (advanced): Add constraints + snap points + animated state transitions.

#### Suggested Student Deliverable

Each group must hand in:

- one short video/gif of the gesture in action
- one code snippet of the gesture component
- 3 lines of reflection:
  - What user action did we change?
  - Why is gesture better here?
  - What still needs improvement?

---

### Materials

- **Framer Motion docs**
  - [Framer Motion – Getting Started](https://www.framer.com/motion/introduction/)
  - [Framer Motion – Drag](https://www.framer.com/motion/drag/)
  - [Framer Motion – Gestures](https://www.framer.com/motion/gestures/)
- **Your prototype**
  - [`20-05-2026-figma-react-mcp.md`](20-05-2026-figma-react-mcp.md)

---
