# 26-05-2026

[Back to lesson index](../lessons.md)

## Gesture & Motion Design: Touch Gestures as Interface

### Purpose of The Day

You will explore touch and pointer gestures as meaningful interface input. The focus is on familiar gestures such as drag, swipe, long press and slide-to-confirm, and how they can support the concept instead of becoming decoration.

Focus question:

> When is a gesture better than a button?

By the end of the day, you should have one central touch or pointer gesture in your prototype that feels discoverable, gives feedback and supports the concept.

### Preparation

- Bring your prototype or a screen where one key user action can be explored through gesture.
- Be ready to explain what the user is trying to do in that interaction.
- Think about whether the action might work better as tap, drag, swipe, long press, hold-to-confirm or slide-to-reveal.
- Bring a phone or be ready to use browser mobile preview if possible.

### Agenda

- Intro: touch gestures as interaction model
  - Explore tap, drag, swipe, long press and slide-to-confirm as alternatives to traditional buttons and links.
  - Connect familiar gestures to mobile and touch-based interaction contexts.
- Gesture intention
  - Discuss what different gestures communicate: swipe to browse/dismiss, drag to move/place, long press to inspect, slide to confirm.
  - Ask whether the gesture supports the user goal or only makes the interface feel more playful.
- Technical demo: pointer/touch events and drag
  - See how gesture input can be implemented in React.
  - Work with native pointer events, Framer Motion drag or a gesture library if needed.
- Thresholds, constraints and release states
  - Decide how far a user must drag or swipe before an action counts.
  - Define what happens on release, cancel, snap-back and success.
- Affordance and feedback while interacting
  - Discuss how users know that something can be dragged, swiped or held.
  - Add visual feedback while the user is interacting, not only after the interaction is complete.
- Guided build: one touch gesture
  - Build a small gesture interaction together.
  - Focus on input, feedback, thresholds and the state change that happens afterwards.
- Exercise: connect one touch gesture to your concept
  - Choose one key interaction from your concept and make it gesture-based.
  - Possible examples: swipe between cards/products, drag to sort, drag item into a zone, slide to confirm, long press to reveal details or draggable timeline/carousel.
- Test and adjust
  - Test whether the gesture feels discoverable and meaningful.
  - Adjust affordance, thresholds, feedback and fallback behaviour.

### Materials

- Touch gesture demo examples
- Starter code for pointer events or Framer Motion drag
- Your prototype or screen to modify
- Mobile device or browser mobile preview
- Gesture evaluation questions
- Optional React gesture library reference

---
