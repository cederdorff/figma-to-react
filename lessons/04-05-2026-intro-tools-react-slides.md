# Figma to React: Intro, Tools & React

04-05-2026

Interactive Design and Development

> Speaker note: Welcome them into the course as a practical design and development space. The first lesson should feel like a shared beginning, not a technical test.

---

# Today

- Get to know the course and each other
- Translate the curriculum into something practical
- Look at alternative interfaces and interactive experiences
- Set up the basic tools
- Begin the bridge from Figma to React
- Build small interactive UI pieces with React

> Speaker note: Keep the promise simple. Today is about orientation, confidence and first contact with React as a prototyping material.

---

# The Course in One Sentence

We turn visual interface ideas into working interactive prototypes.

Design becomes structure.

Structure becomes code.

Code becomes interaction.

> Speaker note: This is the short version students should remember. It also prepares them for the full course progression.

---

# What Does the Curriculum Really Mean?

This elective is about how design and programming work together.

You will explore how technologies can be used to create interactive experiences, alternative interfaces and meaningful digital layers for real contexts.

> Speaker note: Avoid reading the formal curriculum aloud. Use this as the student-facing translation.

---

# Course Progression

Design

Components

Interactive prototype

Touch gesture

Motion feedback

Experimental gesture interfaces

> Speaker note: Point out that the course starts with fundamentals before moving toward gestures, motion and experimental input. The technical skills build toward concept work.

---

# The Recurring Case

Choose a real context:

- Company
- Service
- Product
- Event
- Museum
- Store
- Venue
- Public space

Develop a prototype that adds a meaningful digital layer to the experience.

> Speaker note: This helps students move away from random app ideas. The prototype should belong to a situation, audience and concept.

---

# Not Just a Screen

A Figma frame is one moment.

A React prototype can show what happens:

- before
- during
- after
- when something goes wrong
- when the user makes a choice

> Speaker note: This is a key bridge. Design files often show static moments. Interactive prototypes need states, feedback and flow.

---

# What Is an Alternative Interface?

An interface does not have to be only buttons, menus and pages.

It can also use:

- touch
- drag
- swipe
- long press
- movement
- camera input
- hand gestures
- motion feedback

> Speaker note: Ask students where they have met interfaces that felt different from a normal website or app. Keep it broad and accessible.

---

# Discussion

Think of an interface you remember.

What made it interactive?

Was it useful, playful, confusing or surprising?

How could we build something like it?

> Speaker note: Let students answer before showing technical explanations. The goal is to make them observe interaction quality, not just visual style.

---

# Design to Code

When we move from Figma to React, we ask:

- What are the repeated UI elements?
- What should become a component?
- What can change?
- What should the user be able to do?
- What feedback should the interface give?

> Speaker note: This prepares the mental model for components, props, state and events.

---

# Figma Decisions Become React Decisions

Figma:

- frames
- components
- variants
- layout
- styles
- prototype links

React:

- components
- props
- state
- CSS
- event handlers
- user flows

> Speaker note: Do not over-explain yet. This slide is a map students can return to later.

---

# Where MCP and AI Fit

MCP and AI can help us inspect, translate and scaffold from Figma.

But we still need to understand:

- what the code does
- what should be refactored
- what interaction is missing
- whether the prototype supports the concept

> Speaker note: Set expectations early. AI assistance is part of the workflow later, but React understanding is what lets students judge and improve the output.

---

# Why React?

React helps us build interfaces as pieces that can change.

It is useful for prototypes because it gives us:

- components
- reusable structure
- state
- event handling
- interactive flows

> Speaker note: Frame React as a prototyping material, not as full production engineering.

---

# React Mental Model

A component is a piece of interface.

Props are information passed into that piece.

State is information that can change.

Events are things the user does.

> Speaker note: Keep this slide visible when live coding. It gives students four words to hang onto.

---

# Component

A component is a reusable interface piece.

Examples:

- button
- card
- navigation
- filter
- modal
- product item

> Speaker note: Connect this to Figma components. Students already understand repeated visual patterns.

---

# JSX

JSX lets us write interface structure inside React.

It looks like HTML, but it belongs inside JavaScript.

```jsx
function Button() {
  return <button>Save</button>;
}
```

> Speaker note: Make the first example tiny. The point is recognition, not mastery.

---

# Props

Props let the same component show different content.

```jsx
function Button({ label }) {
  return <button>{label}</button>;
}
```

```jsx
<Button label="Save" />
<Button label="Cancel" />
```

> Speaker note: Compare props to component properties or text overrides in Figma.

---

# State

State is what the interface remembers right now.

Examples:

- selected item
- open or closed
- active step
- liked or not liked
- loading, success or error

> Speaker note: This is where students start seeing why code can express more than a static design.

---

# Event Handlers

Events connect user actions to changes in the interface.

```jsx
function LikeButton() {
  const [liked, setLiked] = useState(false);

  return (
    <button onClick={() => setLiked(!liked)}>
      {liked ? "Liked" : "Like"}
    </button>
  );
}
```

> Speaker note: This can be the first live-code pattern. A tiny state change is enough.

---

# First Build

Build a small interactive UI element.

It should include:

- one component
- one prop
- one state value
- one user action

Examples:

- like button
- expandable card
- selected filter
- simple tab switcher

> Speaker note: Let students choose from the examples. Choice makes the exercise feel less like typing practice.

---

# Tool Setup

We need the basics working:

- browser
- code editor
- Node.js
- npm
- GitHub account
- Figma account
- React project

> Speaker note: Treat setup issues as normal. The success criterion is that everyone knows what is missing and what to fix.

---

# Checkpoint

Can you:

- open the project?
- start the local server?
- change text in a component?
- see the browser update?
- explain where the component lives?

> Speaker note: This gives a concrete minimum for the day. It also helps students who are unsure whether they are "following."

---

# From Today to Next Time

Today:

We begin moving from visual design to interactive code.

Next:

We practice the basics and prepare to structure designs as reusable components.

Later:

We use MCP/AI, gestures, motion and alternative input to develop stronger prototypes.

> Speaker note: End with continuity. The course is cumulative, and today's basics matter later.

---

# Reflection

Write down:

- one thing you understood
- one thing that is still unclear
- one interface idea you might want to explore

> Speaker note: Use this to identify where the group is technically. It can also feed the next lesson.

---

# After Today

- Finish the first exercises
- Make sure your tools work
- Continue React self-study if needed
- Start noticing interactive experiences around you
- Bring questions to the workday

> Speaker note: Keep the homework practical. The workday is about strengthening the foundation before the next React session.

