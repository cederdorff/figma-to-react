# 29-05-2026

[Back to lesson index](../lessons.md)

## Motion: Touch, Pointer, Drag and Swipe Gestures

### Purpose of The Day

This session was moved from `26-05-2026`. The [original May 26 lesson page](26-05-2026-touch-gestures-interface.md) and the [original May 29 lesson page](29-05-2026-motion-ux-feedback.md) are kept for reference.

We use **Motion** (formerly Framer Motion) to explore alternative ways of interacting with digital experiences.

This session connects naturally to the Codeagram React work, and it can also refer back to LYDA's ideas about gesture, motion, experience and storytelling.

The focus is on touch and pointer input, especially drag and swipe gestures, and how movement can replace or improve a button-based interaction.

Focus question:

> When is a gesture better than a button?

By the end of the session, you should see that digital experiences can be shaped by more than clicks, tabs and buttons.

---

### Preparation

1. **Finish the Figma MCP Starter Guide**
   - [Figma MCP Starter Guide](https://github.com/cederdorff/figma-to-react/blob/main/guides/figma-mcp-starter-guide.md)
2. **Make sure you know the React basics**
   - Use [React.dev/learn](https://react.dev/learn) as a recap for JSX, components, props, state and events.
   - A good supplement is [Describing the UI](https://react.dev/learn/describing-the-ui).
3. **Skim Motion for React docs**
   - [Motion for React docs](https://motion.dev/docs/react)
4. **Use the optional workday from `26-05-2026`**
   - Catch up, continue your prototype or try one small Motion experiment before class.
5. **Finish the CodeDex React course and/or self-study**
   - You can also finish the [CodeDex React course](https://www.codedex.io/react) and/or the [Self-study with CodeDex.io](https://www.notion.so/Self-study-with-CodeDex-io-350bc239db1180af9beacc9a801f863a).

---

### Agenda

1. **Intro and framing the day**
   - What is Motion, and why use gestures at all?
   - What is haptic feedback, and when does it improve interaction clarity?
   - Show the core props: `motion.div`, `drag`, `whileTap`, `whileHover`, `onDragEnd`.
2. **Short demos**
   - Demo 1: simple swipe with threshold and snap-back.
   - Demo 2: add haptic feedback to interaction outcomes.
3. **Workshop**
   - [Motion for React Guided Tour](../guides/motion-react-guided-tour.md).
   - [Web Haptics + Motion Lab](../guides/haptics-gesture-exercise.md).
   - [Figma -> Motion -> MCP Experiment Guide](../guides/figma-motion-mcp-experiment-guide.md).
   - [Lottie in React: Figma to Code Guide](../guides/lottie-figma-to-react-guide.md).
4. **Share and wrap up**
   - Quick test and discussion: does the gesture make the interaction clearer, better, or more fun?
   - Optional reflection: where could subtle haptic feedback improve the experience?

---

### Key Concepts

- `motion.div` and gesture props — the Motion setup for touch/pointer interaction
- `drag` / `dragConstraints` — control movement and interaction boundaries
- `onDragEnd` + threshold — decide success state vs snap-back behavior
- `whileTap` / `animate` — give feedback during and after interaction
- **Haptic feedback** — when a tiny vibration cue can support gesture confirmation
- **Affordance** — how does the UI communicate that something can be dragged or swiped?
- **Fallback interaction** — when should a simple tap/button alternative be available?

---

### Materials

- **Slides**
  - [29-05-2026 Touch Gestures Slide Deck](../slides/29-05-2026-touch-gestures-interface.html)
- **Exercises**
  - [Motion for React Guided Tour](../guides/motion-react-guided-tour.md)
  - [Web Haptics + Motion Lab](../guides/haptics-gesture-exercise.md)
  - [Figma -> Motion -> MCP Experiment Guide](../guides/figma-motion-mcp-experiment-guide.md)
  - [Lottie in React: Figma to Code Guide](../guides/lottie-figma-to-react-guide.md)
- **Previous workday**
  - [`26-05-2026-guided-workday-gesture-motion.md`](26-05-2026-guided-workday-gesture-motion.md)
- **Original lesson references**
  - [`26-05-2026-touch-gestures-interface.md`](26-05-2026-touch-gestures-interface.md)
  - [`29-05-2026-motion-ux-feedback.md`](29-05-2026-motion-ux-feedback.md)
- **Other links**
  - [Motion for React Guided Tour](../guides/motion-react-guided-tour.md)
  - [Motion docs](https://motion.dev/)
  - [LottieFiles](https://lottiefiles.com/)
  - [Haptics by Lochie](https://haptics.lochie.me/)
  - [React.dev Learn](https://react.dev/learn)
  - [React.dev - Describing the UI](https://react.dev/learn/describing-the-ui)
  - [CodeDex React course](https://www.codedex.io/react)
  - [Self-study with CodeDex.io](https://www.notion.so/Self-study-with-CodeDex-io-350bc239db1180af9beacc9a801f863a)

---
