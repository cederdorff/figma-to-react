# 01-06-2026

[Back to lesson index](../lessons.md)

## Gesture & Motion Design: Experimental Gesture Interfaces

### Purpose of The Day

We explore experimental gesture interfaces with a focus on camera input and hand gestures.

Today we prototype a **Webcam Controlled Game** using **TensorFlow.js** and browser camera APIs.

The focus is on how physical movement can control a digital interface, and how React state plus motion feedback can make interaction understandable.

Focus question:

> How can physical movement become meaningful input for an interactive digital experience?

By the end of the day, you should have tested or prototyped a camera-based interaction where hand movement drives game state, UI state or motion behavior.

---

### Preparation

1. **Work with the 4 tasks from 29-05-2026**
   - [Motion for React Guided Tour](../guides/motion-react-guided-tour.md)
   - [Web Haptics + Motion Lab](../guides/haptics-gesture-exercise.md)
   - [Figma -> Motion -> MCP Experiment Guide](../guides/figma-motion-mcp-experiment-guide.md)
   - [Lottie in React: Figma to Code Guide](../guides/lottie-figma-to-react-guide.md)
2. **Skim the core docs**
   - [TensorFlow.js Documentation](https://www.tensorflow.org/js)
   - [MediaPipe Hands Guide](https://mediapipe.readthedocs.io/en/latest/solutions/hands.html)
   - [Hand Pose Detection API](https://github.com/tensorflow/tfjs-models/tree/master/hand-pose-detection)
   - [WebRTC getUserMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia)

---

### Agenda

1. **Intro and framing**
   - What makes an interface "experimental"?
   - Why use camera input and hand gestures in interactive experiences?
2. **Camera input in the browser**
   - Set up `getUserMedia()` safely.
   - Discuss permissions, privacy, lighting, performance and fallback interaction.
3. **Hand tracking pipeline**
   - Map the flow: camera feed -> hand landmarks -> gesture classification -> React state -> feedback.
   - Clarify the difference between raw detection and usable interaction design.
4. **Guided demo: webcam-controlled interaction**
   - Use TensorFlow.js hand-pose detection to map one gesture to one game action.
   - Add visual state feedback (recognized/not recognized).
5. **Workshop: make a webcam-controlled game**
   - Track A: implement a small game mechanic controlled by hand position or gesture state.
   - Track B: build a simplified prototype with mocked gesture states, then connect real camera input.
6. **Test, share and reflect**
   - Evaluate reliability, fatigue, discoverability, accessibility and conceptual value.
   - Decide what should stay experimental and what should become product behavior.

---

### Key Concepts

- `navigator.mediaDevices.getUserMedia()` - browser camera access and permission flow
- Hand landmarks vs gesture labels - raw model output vs interaction meaning
- Gesture-to-action mapping - turning recognition into understandable UX behavior
- React state loop - camera input -> model output -> UI state -> motion feedback
- Confidence thresholds and smoothing - reducing noisy gesture triggers
- Fallback interaction - keyboard/pointer alternative for robustness and accessibility
- Privacy and consent - being explicit about camera use and data handling

### Materials

- **Slides**
  - Will be available here
- **Exercises**
  - Build a webcam-controlled mini interaction in React
  - Map at least one gesture to one clear game/UI action
  - Add one fallback interaction (keyboard or pointer)
- **Core resources**
  - [TensorFlow.js Documentation](https://www.tensorflow.org/js)
  - [MediaPipe Hands Guide](https://mediapipe.readthedocs.io/en/latest/solutions/hands.html)
  - [Hand Pose Detection API](https://github.com/tensorflow/tfjs-models/tree/master/hand-pose-detection)
  - [WebRTC getUserMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia)
- **Project resources**
  - Your prototype
  - Laptop camera
  - React starter component for gesture state
  - Reflection checklist (reliability, privacy, discoverability, accessibility)

---
