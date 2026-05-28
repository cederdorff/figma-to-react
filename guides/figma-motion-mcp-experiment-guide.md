# Figma -> Motion -> MCP Experiment Guide

**Rasmus Cederdorff (RACE)**  
Senior Lecturer & Web App Developer  
race@eaaa.dk

---

## Purpose

This guide helps you run a practical workflow where you:

1. Design interaction intent in Figma
2. Build behavior in React + Motion
3. Use Figma MCP to move design context into code
4. Compare and improve the result through iteration

This is an experiment-first guide. The goal is not pixel perfection. The goal is to test how design intent survives implementation.

---

## Who This Is For

You should have:

1. Basic Figma confidence
2. Basic React knowledge
3. Basic Motion knowledge

You do not need to be an expert in Figma components.

---

## Learning Outcomes

By the end, you can:

1. Define interaction states in Figma (idle, drag, success, reject)
2. Implement those states in React with Motion
3. Use Figma MCP as a bridge from design context to code
4. Explain where implementation differs from design and why

---

## Prerequisites

1. A React project ready (recommended: from [motion-react-guided-tour.md](motion-react-guided-tour.md))
2. Access to a Figma file with a simple card/list interaction
3. Figma MCP available in your Copilot workflow

Optional but useful:

- [haptics-gesture-exercise.md](haptics-gesture-exercise.md) if you also want tactile feedback experiments

---

## Workflow Overview

1. Figma = define intent
2. MCP = transfer context into first code version
3. Motion = refine behavior in code
4. Iteration = close the gap

---

## Step 1: Choose One Micro-Flow

Choose one micro-flow only:

1. Swipe card left/right
2. Drag to confirm
3. Tap to expand details

Keep scope small on purpose.

---

## Step 2: Prepare The Figma Interaction

In Figma, create one frame with one interaction component.

Use this minimum checklist:

1. Name the component clearly (for example: `SwipeCard`)
2. Define visual states:
   - Idle
   - Dragging
   - Accepted
   - Rejected
3. Add one note near the component:
   - "What should this feel like?"
   - "When is action accepted?"

Make your Figma file code-ready:

1. Put all states on one page, close to each other.
2. Keep spacing, labels, and colors consistent across states.
3. Use clear layer names such as `Card`, `StateLabel`, `ActionHint`.
4. Copy the Figma node link you want to implement (right click -> Copy/Paste link).

Deliverable for this step:

- One Figma node link with clear interaction intent.

Optional: quick animation sketch in Figma

If you want, you can prototype transitions in Figma to communicate intent.

Keep it simple:

1. One transition for success
2. One transition for reject
3. One transition for snap-back

Important:

1. Treat Figma timing/easing as communication, not exact implementation values.
2. Final behavior should be implemented and tuned in React Motion.

---

## Step 3: Create First Code Version With Figma MCP

In this step, you go directly from your Figma node to a first React + Motion component.

### 3.1 Extract context from your Figma node

Use the node link from Step 2.

Suggested prompt:

```text
Use Figma MCP on this node link and summarize the interaction design intent.
Return: 1) states, 2) layout/spacing, 3) text/content, 4) behavior assumptions.
```

### 3.2 Ask for a first component version

Suggested prompt:

```text
Use the Figma MCP context to help me create a first React + Motion component for this interaction.
Keep it simple: one component, clear state names, drag/tap behavior, and visible state feedback.
```

### 3.3 Keep the first version simple

Your first version should include:

1. One component
2. Clear state names (`idle`, `accepted`, `rejected`, etc.)
3. Basic Motion behavior (`drag` or `whileTap`)
4. Visible text feedback for current state

Deliverable for this step:

- A first MCP-assisted React + Motion component that runs.

---

## Step 4: Refine Motion Behavior In Code

Now refine the MCP-first version so behavior feels good in real use.

Improve in this order:

1. Thresholds (`handleDragEnd`)
2. Motion transitions (spring stiffness/damping)
3. State labels/messages
4. Mobile drag behavior (`touch-action`, constraints)

Suggested refinement prompt:

```text
Refine this React + Motion component to better match interaction intent from Figma.
Focus on thresholds, transitions, and state feedback clarity.
Keep the same component structure.
```

Deliverable for this step:

- Updated component with improved behavior and clearer state feedback.

---

## Step 5: Compare And Refine

Run a side-by-side check:

1. Figma interaction intent
2. React + Motion behavior

Evaluate:

1. Is acceptance/rejection threshold understandable?
2. Is state feedback clear?
3. Does motion feel too heavy or too subtle?
4. If using haptics, does tactile feedback match visual feedback?

Make one focused improvement, not ten.

Deliverable for this step:

1. One concrete improvement with a short reason.

---

## Step 6: Share Back (Short Crit)

Share in 90 seconds:

1. What you designed in Figma
2. What changed after MCP-assisted adaptation
3. One thing that still does not match and why

This keeps reflection practical and technical.

---

## Prompts You Can Reuse

### Prompt A: Context extraction

```text
Use Figma MCP to extract design context for this interaction node and summarize:
1) states
2) layout rules
3) behavior assumptions
```

### Prompt B: Adapt existing code

```text
Adapt my MCP-generated React + Motion component to better match this Figma node.
Keep my current component structure.
Only change what is needed for state clarity and interaction behavior.
```

### Prompt C: Gap analysis

```text
Compare my current component against this Figma node.
List the top 3 behavior mismatches and suggest minimal fixes.
```

---

## Assessment Rubric (Lightweight)

Score each area 1-3:

1. Interaction clarity
2. State feedback quality
3. Code readability
4. Design-to-code alignment
5. Iteration quality (did they improve based on comparison?)

Maximum: 15

---

## Common Pitfalls

1. Building too much before testing one flow
2. Trying to copy Figma 1:1 before behavior works
3. Accept/reject thresholds too strict on mobile
4. Rewriting entire component from MCP output

Keep yourself focused on one interaction loop at a time.

---

## Extension Ideas

1. Add haptics mapping (success, warning, error)
2. Add reduced motion/reduced haptics mode
3. Test same component on desktop vs mobile and compare behavior

---

## Wrap-Up

This workflow teaches a realistic product loop:

- Design intent -> implementation -> comparison -> refinement

Figma MCP is strongest when used as an accelerator inside that loop, not as a one-click replacement for engineering judgement.
