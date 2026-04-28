# 01-06-2026

[Back to lesson index](../lessons.md)

## Gesture & Motion Design: Experimental Gesture Interfaces

### Purpose of The Day

You will explore experimental gesture interfaces, including camera-based hand gestures and other non-standard input methods. The focus is on how physical movement can control a digital interface, and how React state and motion feedback can make the interaction understandable.

Focus question:

> How can physical movement become meaningful input for an interactive digital experience?

By the end of the day, you should have tested or prototyped an alternative gesture interaction, such as hand tracking, camera input or another non-standard input method.

### Preparation

- Bring your prototype.
- Think about one interaction that could be controlled without a mouse, keyboard or touch.
- Make sure your laptop camera works if you want to test hand gestures.
- Be ready to test with camera input or a fallback interaction.
- Be ready to reflect on reliability, privacy, discoverability and accessibility.

### Agenda

- Intro: experimental gesture interfaces
  - Explore hand gestures, camera input, embodied interaction and alternative controls.
  - Discuss why non-standard input can be useful, risky or conceptually interesting.
- Camera input in the browser
  - Understand how browser camera access works through `getUserMedia()`.
  - Discuss permissions, privacy, lighting, performance and fallback interaction.
- Hand tracking concept
  - Map the flow: camera input → hand landmarks → gesture interpretation → React state → motion feedback.
  - Discuss the difference between detecting a hand and designing a usable gesture interaction.
- Simple hand gesture vocabulary
  - Explore gestures such as open palm, fist, pinch, pointing, hand left/right and two-hand expand/collapse.
  - Connect each gesture to possible interface meanings: stop, grab, select, navigate, reveal, zoom or confirm.
- Technical demo or guided experiment
  - Use a simple camera or hand-tracking example to change interface state.
  - Add visible feedback so the user knows the gesture has been recognized.
- Concept mapping
  - Choose one interaction from your concept that could use experimental input.
  - Decide why the gesture is meaningful and what fallback interaction is needed.
- Prototype or sketch exercise
  - Build, test or storyboard one alternative gesture interaction.
  - You can use camera-based hand tracking, simulated hand gesture state, keyboard fallback or another experimental input method.
- Test and reflect
  - Test whether the gesture is understandable, reliable and connected to the concept.
  - Reflect on what works, what fails and whether the technology adds real value.

### Materials

- MediaPipe Hand Landmarker example or starter
- `getUserMedia()` camera example
- React starter component for camera or gesture state
- Motion feedback example
- Your prototype
- Laptop camera
- Fallback interaction checklist
- Experimental gesture reflection questions

---
