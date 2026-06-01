# 02-06-2026

[Back to lesson index](../lessons.md)

## Workday - Webcam Gesture Game Exercises

**Schedule note:** This workday also serves as a substitute for Experimental Gesture Interfaces.

### Purpose of The Day

This day is a guided workday built around webcam and hand-gesture interaction.

If you need help during the workday, you can contact me by email or on Teams: race@eaaa.dk.

You will choose one exercise and work step by step from setup to interaction feedback.

By the end of the day, you should have tested or built a webcam-controlled interaction in React where hand movement affects game state or UI state.

Focus question:

> How can physical movement become meaningful input for an interactive digital experience?

---

### Exercises

Try and work with the exercises below. If you finish early, continue with another one and try out the showcases.

1. **Exercise 1 - [Hand Puck - Introduction to webcam hand gestures](https://github.com/cederdorff/webcam-ui/blob/main/README.md)**
   - Best for getting started with webcam hand gestures.
   - Goal: get webcam input working and connect one basic hand action to one game reaction.

2. **Exercise 2 - [Hand Catch Game (Core Build)](https://github.com/cederdorff/hand-catch-game/blob/main/README.md)**
   - Best for practising by modifying an existing game.
   - Goal: run the project, understand the interaction loop, and make small customisations.

3. **Exercise 3 - [Air Juggler V1 (Advanced)](https://github.com/cederdorff/air-juggler-game/blob/main/IMPLEMENTATION_GUIDE.md)**
   - Optional advanced challenge.
   - This starts from the Hand Puck template repository.
   - Goal: follow the implementation guide and build a more complete gesture-controlled game loop.
   - If you get stuck, review the full solution: [Air Juggler Game Repository](https://github.com/cederdorff/air-juggler-game)

4. **Showcase - Air Juggler V2 (React + TensorFlow.js)**
   - Not an exercise. This is a showcase of that implementation.
   - Best for students who want a newer React + TensorFlow.js version.
   - Goal: explore how gesture detection and React state work together in a full project.
   - [Air Juggler (React + TensorFlow.js) - Version 2](https://github.com/cederdorff/webcam-controlled-game/blob/main/README.md)

5. **Showcase - Dandelion Experiment**
   - Not an exercise. This is a showcase you can explore with minor customisations.
   - Goal: try small changes to interaction, visuals or motion feedback and observe the effect.
   - [Dandelion Experiment](https://github.com/cederdorff/dandelion-experiment)

---

### Suggested Rhythm

1. Choose one exercise and define a small, testable goal.
2. Build in short steps and test often.
3. Add clear feedback for recognized vs not recognized gesture states.
4. Include a fallback interaction (keyboard or pointer) when possible.
5. End by documenting what worked, what was unstable, and what to improve next.

---

### Reflection Prompts

- Which gesture was most reliable, and why?
- Where did recognition fail (lighting, camera angle, speed, confidence threshold)?
- Did users understand the interaction without explanation?
- What should stay experimental, and what could become product behavior?

---

### Materials

- **Previous context**
  - [Experimental Gesture Interfaces (01-06-2026)](01-06-2026-experimental-gesture-interfaces.md)
- **Core resources**
  - [TensorFlow.js Documentation](https://www.tensorflow.org/js)
  - [MediaPipe Hands Guide](https://mediapipe.readthedocs.io/en/latest/solutions/hands.html)
  - [Hand Pose Detection API](https://github.com/tensorflow/tfjs-models/tree/master/hand-pose-detection)
  - [WebRTC getUserMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia)

---
