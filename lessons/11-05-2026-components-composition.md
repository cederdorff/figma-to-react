# 11-05-2026

[Back to lesson index](../lessons.md)

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
