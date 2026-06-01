# 01-06-2026

[Back to lesson index](../lessons.md)

## Gesture & Motion Design: Experimental Gesture Interfaces

### Purpose of The Day

**_This session has been cancelled. As a substitute, please follow the steps under Exercises._**

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
  1.  [Hand Puck - Introduction to webcam hand gestures](https://github.com/cederdorff/webcam-ui/blob/main/README.md)
  2.  [Hand Catch Game - Try out the game and make minor customisations](https://github.com/cederdorff/hand-catch-game/blob/main/README.md)
  3.  [Air Juggler Game - Version 1 (Advanced)](https://github.com/cederdorff/air-juggler-game/blob/main/IMPLEMENTATION_GUIDE.md)
      - Optional advanced challenge. If you get stuck, you can view the full solution here: [Air Juggler Game Repository](https://github.com/cederdorff/air-juggler-game)
  4.  [Air Juggler (React + TensorFlow.js) - Version 2](https://github.com/cederdorff/webcam-controlled-game/blob/main/README.md)
- **Core resources**
  - [TensorFlow.js Documentation](https://www.tensorflow.org/js)
  - [MediaPipe Hands Guide](https://mediapipe.readthedocs.io/en/latest/solutions/hands.html)
  - [Hand Pose Detection API](https://github.com/tensorflow/tfjs-models/tree/master/hand-pose-detection)
  - [WebRTC getUserMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia)

---
