# 11-05-2026

[Back to lesson index](../lessons.md)

## Figma to React: From Components to Composition

### Purpose of The Day

The purpose of today is to strengthen the React foundation from the first session. We will revisit questions from the exercises and workday, then practice React basics and component thinking through the Codeagram app.

Focus question:

> How do we break a design into reusable components and build them into a working app?

By the end of the day, you should have a clearer React mental model, a better sense of how to break a UI into components, a small set of reusable components and a Codeagram app that shows how components, props, state and events fit together.

---

### Preparation

1. **Finish exercises from last lesson**
   - [Getting started with React](https://www.notion.so/Getting-started-with-React-0fd48b8ae90a438bb6ec8dc95628f13f)
   - [React Page Layout with Components](https://github.com/cederdorff/react-vite-page-layout/blob/main/docs/EXERCISE_GUIDE.md)
2. **Use the self-study guide if you need more support**
   - If HTML, CSS or JavaScript still feel shaky, keep working on [Self-study with CodeDex.io](https://www.notion.so/Self-study-with-CodeDex-io-350bc239db1180af9beacc9a801f863a)
3. **CodeDex React course**
   - [CodeDex React course](https://www.codedex.io/react)
   - Do the sections "First React App", "JSX & Components", "Props & State" and "Events".

---

### Agenda

1. **Today's goals and recap**
   - Set the focus for the day.
   - Show the end result of the day: Codeagram.
   - Learn how to export the Reveal slides as a PDF.
   - Note the GitHub Student Developer Pack for next time.
   - Revisit last lesson's exercises and workday questions.
2. **React basics and component thinking**
   - Practice the React mental model: components, JSX, props, state and events.
   - See how these pieces work together in a React file.
   - Break a UI into reusable parts.
   - Decide what should become a component, a prop, data or state.
3. **Codeagram App**
   - Build the Codeagram app as the main example for the day.
   - Set up components, layout, data, props, events and state.
   - Refactor parts of the code for clarity and reuse.
4. **Small component system**
   - Find the first reusable patterns that already exist in Codeagram.
   - Extract small pieces such as `Avatar` and `IconButton` before making anything bigger.
   - Connect visual consistency to reusable values in code.
5. **Wrap-up and next steps**
   - Reflect on what the Codeagram app taught us.
   - End with questions, next steps and Workday.
   - Remember: if you have problems with the GitHub Student Developer Pack, write on Teams or email `race@eaaa.dk`.

---

### Materials

- **Slides**
  - [11-05-2026-components-composition](https://cederdorff.com/figma-to-react/slides/11-05-2026-components-composition.html)
- **Exercises**
  - [Codeagram Feed with React Components](https://github.com/cederdorff/codeagram/blob/main/docs/EXERCISE_GUIDE.md)

- **Other links**
  - [GitHub Student Developer Pack](https://education.github.com/pack)
  - [CodeDex React course](https://www.codedex.io/react)

---

### Small Component System Focus

Use the local Codeagram app as the example and start from what is already repeated in the code.

- `HeaderActions` already repeats icon-only buttons.
- `UserInfo` already has a clear avatar pattern.
- `PostCard` is already a repeated feature component in the feed.

Suggested first extractions:

1. `Avatar`
2. `IconButton`
3. Maybe `Card` later, if more wrappers start sharing the same structure

Possible folder structure after the first extractions:

```text
src/
   components/
      Avatar.jsx
      Header.jsx
      HeaderActions.jsx
      HeaderBrand.jsx
      IconButton.jsx
      PostCard.jsx
      UserInfo.jsx
   data/
      posts.js
   App.jsx
   main.jsx
   styles.css
```

Class exercise:

1. Create an `Avatar` component and use it inside `UserInfo`.
2. Create an `IconButton` component and use it inside `HeaderActions`.
3. If there is time, try using the same `IconButton` in `PostCard`.
4. Keep `PostCard` as a feature component.
5. Test that the UI still looks the same and that likes and bookmarks still work.

---
