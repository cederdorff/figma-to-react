# Interactive Design and Development

## RACE Session Plan

## Core Progression

**Design → Components → Interactive Prototype → Touch Gesture → Motion Feedback → Experimental Gesture Interfaces**

The RACE sessions form the technical spine of the elective. The focus is to help you turn visual design into working interactive prototypes, while connecting React, gestures and motion to UX, concept development, emerging technologies and technology choices.

The course progression is not only about learning tools. You will use relevant technologies to develop, prototype, test and argue for interactive experiences where design and programming merge.

The first three RACE sessions focus on React fundamentals and design-to-code thinking, so you can understand, evaluate and improve the code that Figma MCP/AI workflows generate from a Figma design.

---

## Gesture & Motion Block Goal

By the end of the Gesture & Motion block, you should be able to design and prototype interactions where input, motion and feedback work together.

The block moves from familiar touch and pointer gestures, to motion as UX feedback, and finally to experimental gesture interfaces such as camera-based hand tracking.

The goal is not to use gestures or motion because they are impressive. The goal is to choose interaction techniques that support the concept, make the interface understandable and create a meaningful digital layer.

---

## Figma to React Block Goal

By the end of the Figma to React block, you should be able to use React to understand how a Figma design becomes components, props, state and interaction.

You should also be able to use Figma MCP/AI-assisted workflows to create a React prototype from a Figma design, then evaluate the generated output, refactor it into meaningful components and add interaction where needed.

MCP/AI is introduced as an assisted workflow, not as a replacement for understanding React, UX structure or design judgement.

---

## Recurring Case

You will work with one recurring case throughout the course:

> Choose an existing company, service, product, event, museum, store, venue or public space. Develop an interactive digital prototype that adds a meaningful digital layer to the user experience.

The case should help you connect technical choices to a real context, user need and concept opportunity.

Possible examples:

- Museum guide with gesture-based exploration
- Retail product finder with motion-based filtering
- Event or festival app with an interactive schedule
- Restaurant ordering flow with playful microinteractions
- Public transport concept with a touch or gesture interface
- Exhibition prototype connecting physical objects and digital content

---

## RACE Overview

| Date           | Session                             | Improved Focus                                         | Curriculum Link                                      | Output                                           |
| -------------- | ----------------------------------- | ------------------------------------------------------ | ---------------------------------------------------- | ------------------------------------------------ |
| **04-05-2026** | Intro, Tools & React                | React foundations for understanding generated code      | Design + programming, interactive solutions          | A running React project with simple interaction  |
| **11-05-2026** | From Components to Composition      | Component structure for evaluating MCP/AI output        | Transition from design to programming                | A small component system and one composed screen |
| **20-05-2026** | Figma to React with MCP             | Using MCP/AI to create and improve a React prototype    | Emerging tech, prototype testing, UX/UI              | A React prototype generated from a Figma design and improved manually |
| **26-05-2026** | Touch Gestures as Interface         | Pointer, touch, drag and swipe as meaningful input     | Alternative interfaces, interactive experiences      | One touch or pointer gesture interaction         |
| **01-06-2026** | Motion as UX Feedback               | Motion as feedback, meaning and flow                   | UX/UI, interaction quality                           | An animated prototype flow                       |
| **09-06-2026** | Experimental Gesture Interfaces     | Camera input, hand gestures and embodied interaction   | Emerging technologies, alternative interfaces        | An experimental gesture prototype or concept test |

---

# 04-05-2026

## Figma to React: Intro, Tools & React

### Purpose of The Day

You will get a shared technical foundation and make React feel usable rather than intimidating. React is framed as a tool for building interactive prototypes and as the language you need in order to understand MCP/AI-generated output later in the block.

Focus question:

> How do we turn a visual interface into interactive components?

By the end of the day, you should have a working React project, one interactive component and a basic understanding of how to read a React component file.

### Preparation

- Bring a laptop.
- Make sure you have access to Figma.
- Make sure you have a code editor installed.
- Be ready to set up or check your local React development environment.
- Think about an existing company, service, place or physical experience you might want to work with during the course.

### Agenda

- Welcome, introductions and course framing
  - You will get introduced to the course structure, the overall theme and the expected way of working.
  - We will connect the elective to interactive design, development, prototyping and emerging technologies.
- What is an interactive prototype?
  - We will discuss the difference between a visual mockup and an interactive prototype.
  - You will look at how technology can add a digital layer to an existing company, service, place or physical experience.
- Tool setup
  - Set up or check VS Code, Node, Vite and Browser DevTools.
  - Create a React project and make sure it runs locally.
  - Understand the basic project structure you will use during the course.
- React basics
  - Work with components, JSX, props, `useState` and event handlers.
  - See how a visual UI becomes interactive through state and user actions.
- Reading a React file
  - Identify imports, component functions, returned JSX, CSS/classes, data and state.
  - Practice reading code so MCP/AI-generated output becomes easier to understand later.
- Guided exercise: build one small interactive component
  - Build a small UI component with one meaningful interaction.
  - Possible examples: selected product card, museum object, booking option, event card, expand/collapse profile card, tabs or mini onboarding stepper.
- Case brainstorm
  - Start thinking about an existing company, service, physical location or user situation you might work with.
  - Identify where an interactive digital layer could create value.
- Share-out and reflection
  - Share what you built and what you found difficult.
  - Reflect on how React can work as a prototyping material.

### Materials

- Course slides or course framing notes
- React/Vite setup guide
- Starter repo or setup commands
- Simple Figma design, screenshot or UI reference
- Example interactive component
- Browser DevTools
- Optional GitHub/deployment guide

---

# 11-05-2026

## Figma to React: From Components to Composition

### Purpose of The Day

You will learn how to structure UI instead of copy-pasting screens. The transition from Figma decisions to React decisions is made explicit, so you are prepared to evaluate and refactor MCP/AI-generated code.

Focus question:

> How do we break a design into reusable components?

By the end of the day, you should have a small component library, one screen composed from reusable components and a clearer sense of what good generated React code should become after refactoring.

### Preparation

- Bring your React project from the first session.
- Bring or choose a case you can use for interface inventory.
- Bring a Figma design, screenshot or visual reference if you already have one.
- Be ready to identify repeated UI patterns, user actions, states and content types.
- Be ready to refactor code into reusable components.

### Agenda

- Recap: components, props, state and reading React files
  - Review the React basics from the first session.
  - Revisit how to read imports, component functions, JSX, styling, data and state.
- Figma frames vs. React components
  - Compare how a design is structured in Figma with how an interface is structured in React.
  - Identify repeated UI patterns that should become reusable components.
- Design-to-code decisions
  - Decide what becomes a component, prop, data or state.
  - Discuss what should be refactored when code is too flat, repetitive or hard to maintain.
- Live coding: component variants
  - Build components such as `Button`, `Card` and `Tag`.
  - Use props to create variants instead of duplicating code.
- Design tokens light
  - Work with colors, spacing, border radius and typography as reusable design decisions.
  - Connect visual consistency in Figma to reusable values in code.
- Mapping over data and composing a screen
  - Use arrays and `.map()` to render repeated UI.
  - Compose a screen from smaller reusable components.
- Exercise: build a small component system
  - Build reusable components from a Figma design, screenshot or visual reference.
  - Suggested components: `Button`, `Card`, `Navigation`, `Section`, `Filter`, `Modal` and `Tag`.
- Interface inventory
  - Create a small inventory from your case.
  - Identify repeated UI elements, user actions, possible states and content types.
- Refactor discussion
  - Discuss what good React code should become after refactoring.
  - Connect this to how you will later evaluate MCP/AI-generated code.

### Materials

- Figma design or screenshot with repeated UI patterns
- React starter project or your previous project
- Example component code
- Example design tokens
- Small repetitive/generated-like React example for refactoring
- Exercise brief for component inventory

---

# 20-05-2026

## Figma to React with MCP: From Design to Interactive Prototype

### Purpose of The Day

You will use Figma MCP/AI-assisted workflows to create a React prototype from a Figma design. You should understand the generated output, evaluate its quality, refactor where needed and add meaningful interaction.

Focus question:

> How can AI/MCP help us inspect, translate or scaffold from Figma, and where do we still need human design and development judgement?

By the end of the day, you should have a deployed or shareable React prototype created from a Figma design with MCP/AI assistance, improved through React refactoring, meaningful interaction and a short test task for a classmate.

### Preparation

- Bring your React project.
- Make sure you understand components, props and state from the first two sessions.
- Bring or choose a Figma design that can become a small interactive prototype.
- Be ready to inspect generated code and decide what should be kept, refactored or rebuilt.
- Be ready to test your prototype with a classmate.

### Agenda

- Recap: why React knowledge matters before using MCP/AI
  - Revisit components, props, state and component structure.
  - Connect the first two React sessions to the ability to understand generated code.
- Figma MCP/AI workflow overview
  - See how MCP/AI can inspect, translate or scaffold from a Figma design.
  - Discuss MCP/AI as an assisted workflow, not a replacement for design and development judgement.
- Demo: generate or scaffold a React version
  - Start from a Figma design.
  - Use MCP/AI to create a first React version or scaffold.
- Read the generated output
  - Identify components, props, layout, styling, assets and missing state.
  - Look for where the generated code is helpful and where it needs human decisions.
- Critique the output
  - Ask what works, what is too literal, what is duplicated and what needs interaction.
  - Decide what should be kept, refactored or rebuilt.
- Refactor into clearer components and add state
  - Improve structure, naming and reusability.
  - Add meaningful state and interaction so the result becomes a prototype, not just a static screen.
- Exercise: create a 2-3 step prototype from a Figma design
  - Define a user goal, start state, key action, feedback and end state.
  - Possible flows: overview → detail → action, onboarding → choice → result, product selection → confirmation, or physical object/location → digital content → saved choice.
- Pair testing with a short user task
  - Test whether a classmate can understand and complete the prototype flow.
  - Note where the prototype needs clearer interaction, feedback or structure.
- Wrap-up: MCP/AI and human judgement
  - Reflect on where MCP helped.
  - Reflect on where React knowledge, UX judgement and design decisions were still necessary.

### Materials

- Figma file prepared for MCP/AI workflow
- Figma MCP/AI setup instructions
- React project/starter repo
- Generated-code evaluation checklist
- Refactoring checklist
- Deployment guide
- Pair-testing task template

---

# 26-05-2026

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

# 01-06-2026

## Gesture & Motion Design: Motion as UX Feedback

### Purpose of The Day

You will work with motion as feedback, hierarchy and continuity. The focus is on using motion to make state changes, gestures and user flows easier to understand.

Focus question:

> How can motion help the user understand what happened, what changed and what to do next?

By the end of the day, you should have an animated interaction flow where motion gives clear feedback and supports the user journey.

### Preparation

- Bring your prototype, preferably including the touch gesture from the previous session.
- Identify one flow where users need clearer feedback.
- Be ready to explain what should feel selected, changed, completed, cancelled or in progress.
- Be ready to work with Framer Motion or CSS transitions depending on the technical level of the group.

### Agenda

- Intro: motion as UX logic, not decoration
  - Explore motion as a way to communicate feedback, hierarchy and continuity.
  - Discuss when motion improves understanding and when it becomes visual noise.
- Motion principles
  - Work with timing, easing, direction, hierarchy and continuity.
  - Connect motion choices to how users understand state changes.
- Motion and React state
  - Connect animation to selected, open, closed, loading, success, error and cancelled states.
  - Use motion to make state changes visible and understandable.
- Technical demo: Framer Motion or CSS transitions
  - See how to animate state changes, gesture release, view transitions and component entry/exit.
  - Use Framer Motion if the group is ready, or CSS transitions as a fallback.
- Feedback states
  - Add motion to loading, success, error, selected and cancelled states.
  - Ask what changed, what is selected, what succeeded, what failed and what the user should do next.
- Motion after gestures
  - Animate snap-back, confirmation, reveal, transition or success after a gesture.
  - Connect the previous session's touch gestures to clearer motion feedback.
- Accessibility and reduced motion
  - Discuss how motion can affect accessibility.
  - Consider reduced motion and avoid animation that makes interaction harder to understand.
- Guided build: animate one state change or gesture release
  - Build one motion pattern together.
  - Focus on making the interaction clearer through movement.
- Exercise: add motion to one important prototype flow
  - Choose a flow where users need clearer feedback.
  - Possible examples: opening a detail view, moving between steps, selecting an item, completing an action, changing mode/state, snap-back or gesture release animation.
- Peer feedback
  - Test whether the motion clarifies what happened.
  - Adjust timing, easing or feedback based on what your classmate experiences.

### Materials

- Motion example references
- Framer Motion setup/demo
- CSS transition fallback examples
- Your prototype
- Reduced motion/accessibility reference
- Motion feedback checklist
- Touch gesture prototype from the previous session

---

# 09-06-2026

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

# Suggested Day Rhythm

| Time       | Activity                               |
| ---------- | -------------------------------------- |
| 30-45 min  | Intro, examples and theory             |
| 60-90 min  | Live coding / guided build             |
| 30 min     | Break/checkpoint                       |
| 90-120 min | Apply it to your own project |
| 30 min     | Show, discuss and reflect              |

---

# RACE Learning Focus

## 1. React as a Prototyping Material

You should use React to build believable interactive experiences, not necessarily full production software.

## 2. Design-to-Code Translation

You should understand how Figma decisions become components, props, states and flows.

## 3. Interaction Quality

Gestures and motion should strengthen the user experience and the concept.

## 4. Exam Readiness

You should be able to explain why you chose a technology, not just show that it works.

## 5. Curriculum Alignment

The plan supports the curriculum by focusing on:

- Development-based knowledge of emerging technologies
- Reflection on how technology can be applied in UX/UI and programming
- Digital layers for physical or existing concepts
- Prototyping, testing and improving interactive solutions
- The transition from design to programming
- Technology choice, argumentation and interdisciplinary collaboration
