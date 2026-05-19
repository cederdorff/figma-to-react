# Figma MCP Starter Guide

**Rasmus Cederdorff (RACE)**  
Senior Lecturer & Web App Developer  
race@eaaa.dk

---

## Purpose

This guide helps you get started with Figma MCP in VS Code and use it in a small React project.

The goal is not to generate a perfect app in one prompt.

The goal is to:

1. set up Figma MCP correctly
2. create a small React project
3. use a Figma design as context
4. inspect the generated code
5. improve the result with your own React knowledge

---

## Quick Version

If you want the short version, do this:

1. Set up the **remote** Figma MCP server in VS Code.
2. Create a blank React project with Vite.
3. Make or choose **one** clean Figma frame.
4. Paste a link to that frame into Copilot, Codex, or Claude Code in VS Code.
5. Ask it to implement the design in your React project.
6. Run the app, inspect the code, and improve the result.

If that works, then move on to more screens, more views, and more advanced tasks.

---

## Before You Start

Make sure you have:

- VS Code installed
- GitHub Copilot enabled in VS Code
- Node.js and npm installed
- Figma installed

You can also use Codex or Claude Code in VS Code.

Note:

- GitHub Copilot is required for the official Figma MCP setup flow in VS Code.
- Claude Code requires a paid Claude plan.
- For this course, use the **remote Figma MCP server**, not the desktop server.

> **Credits, limits, and budget**
>
> Depending on the AI tool you use, you may be using your own credits, limits, or budget.
>
> To use them more carefully:
>
> - start with smaller prompts first
> - use the smallest relevant Figma context you can
> - refine a working prompt instead of starting over each time
> - do not keep resending large prompts without changing anything

Official setup article:

- [VS Code and Figma: Set up the MCP server](https://help.figma.com/hc/en-us/articles/39890361040535-VS-Code-and-Figma-Set-up-the-MCP-server)

---

## Exercise

### 1. Set up the remote Figma MCP server in VS Code

![Figma MCP setup in VS Code](assets/figma-mcp-vscode-setup.gif)

The GIF above shows the last part of the setup flow in VS Code.

Do these steps directly in VS Code:

1. Open the **Command Palette**:
   - macOS: `Cmd + Shift + P`
   - Windows: `Ctrl + Shift + P`
2. Search for `MCP: Open User Configuration`.
3. Open the `mcp.json` file that VS Code shows you.
4. Paste this configuration into the file:

```json
{
  "inputs": [],
  "servers": {
    "figma": {
      "url": "https://mcp.figma.com/mcp",
      "type": "http"
    }
  }
}
```

5. Save the file:
   - macOS: `Cmd + S`
   - Windows: `Ctrl + S`
6. After saving, stay in VS Code and look for the Figma MCP server entry. See the GIF above.
7. When you see a **Start** button above the Figma server entry, click it to begin authentication.
8. Complete the authentication flow in the external browser window using your Figma account.
9. Return to VS Code and confirm that the Figma MCP server is now running. See the GIF above if you are unsure what this should look like.

Expected result:

- The Figma MCP server appears as **running** in VS Code.

Important:

- This guide only covers the **remote** Figma MCP server.
- Do **not** continue to the **desktop Figma MCP server** section in the official guide.

If the Figma guide changes in the future, use the official article here:

- [VS Code and Figma: Set up the MCP server](https://help.figma.com/hc/en-us/articles/39890361040535-VS-Code-and-Figma-Set-up-the-MCP-server#h_01KPPGM2WBVB21ZYNEXJYDH16P)

---

### 2. Create a new React project

1. Create a new project folder on your machine.
2. Open that folder in VS Code, and only that folder.
3. Open the terminal in VS Code.
4. Run:

```bash
npm create vite@latest . -- --template react
```

5. Then run:

```bash
npm install
```

6. Start the project:

```bash
npm run dev
```

7. Open the local URL in the browser and make sure the blank React app works before you continue.

---

### 3. Choose a Figma design

Start simple.

For your first try, use:

- one main screen, or
- one small flow with two screens

Recommended:

- Recreate the **Codeagram** feed in Figma, or
- use Figma Make to help you create a first draft, then copy the result into a normal **Figma Design** file

Make sure your design is as structured as possible:

- use Auto Layout where it makes sense
- use components for repeated UI
- name layers clearly
- keep spacing and hierarchy clean
- avoid messy or half-finished frames

Important:

- Figma MCP works better when the design is structured well.
- Do not start with a huge multi-page app.
- Start with one good frame.

---

### 4. Get the Figma link for design context

This step is based on the official Figma guide:

- [Guide to the Figma MCP server](https://help.figma.com/hc/en-us/articles/32132100833559-Guide-to-the-Figma-MCP-server#example-get-design-context)

The remote Figma MCP workflow is **link-based**.

Your goal in this step is only to get the correct link to the frame or layer you want to use as context.

Do this:

1. In Figma Design, select the frame or layer you want to work from.
2. Copy the link to that frame or layer.

How to copy the link:

- **If you are using Figma in the browser:**
  - select the frame or layer
  - copy the link from the browser address bar, or
  - use **Copy link to selection**
- **If you are using the Figma desktop app:**
  - select the frame or layer
  - right-click the frame on the canvas or in the Layers panel
  - go to **Copy/Paste as > Copy link**

Tip:

- For the remote MCP server, the important thing is that you get a URL pointing to the frame or layer you want to use as context.

![MCP client with link-based prompt](assets/mcp-client-link-prompt.png)

Important:

- Start with one frame or one important part of the design.
- Do not begin with a huge multi-screen app unless your design is very small.
- Your MCP client will not open the Figma link like a browser tab. Instead, it extracts the node ID from the URL and uses that to get design context from Figma.

---

### 5. Prompt your MCP client

Now use the link from step 4 in your MCP-enabled chat in VS Code.

In VS Code:

1. Open GitHub Copilot Chat, Codex, or Claude Code.
2. Paste the Figma link into the chat.
3. Ask the AI to implement the design in your blank React project.

Start simple.

For the first prompt, ask for:

- one screen
- a simple component structure
- a working first version
- an explanation of what files it changes

Suggested first prompt:

```text
Use this Figma link as design context:
[PASTE FIGMA LINK HERE]

Implement the screen in this React project.
Keep the code simple.
Split the UI into meaningful components.
Use props where values repeat.
Tell me what files you create or change.
Explain the component structure briefly before or after you make the changes.
```

If you want a slightly more technical version, try this:

```text
Use this Figma link as design context:
[PASTE FIGMA LINK HERE]

Implement this screen in my blank React project.
Use a clean component structure.
Keep the styling simple.
Do not over-engineer the solution.
Tell me what files you create or change, and explain the components you add.
```

Important:

- Start with one frame, not a whole app.
- Do not ask for too many features in the first prompt.
- First get a working version. Then improve it in later prompts.
- If the result is messy, ask for refactoring in the next prompt instead of trying to fix everything at once.

More official prompt examples:

- [Tools and prompts](https://developers.figma.com/docs/figma-mcp-server/tools-and-prompts/)

After the AI has made changes:

1. let it do the work
2. run the app
3. check whether it actually works
4. restart the dev server if needed
5. if something breaks, read the error before prompting again

Do not continue until you have a real first result running in the browser.

---

### 6. Investigate the code

Do not stop at “it works”.

Look at the code and ask:

1. How is the project structured?
2. What components do you see?
3. Where are props used?
4. Is any state used?
5. Does the component structure make sense?
6. How is it different from your own Codeagram implementation?
7. What looks good?
8. What looks messy, over-generated, or too literal?

This step is important.

MCP and AI can help you move faster, but you still need React knowledge to evaluate the result.

---

## Prompting Tips and Best Practices

When you prompt your MCP client, these habits usually lead to better results:

### Start small

- Start with one frame, not a whole app.
- Ask for one working screen before asking for multiple pages.
- Get a simple result first, then improve it.

### Be specific

- Say exactly what you want the AI to do.
- If you want structure help, ask for structure help.
- If you want styling help, ask for styling help.
- If you want refactoring, say that directly.

### Improve one thing at a time

- Do not ask for layout fixes, new features, routing, animations, and refactoring in the same prompt.
- Change one thing, test it, then continue.

### Use better links

- Link to the whole frame when you want a first implementation.
- Link to a specific component, layer, icon, or section when you want a more targeted change.
- Smaller context often gives cleaner results.

### Ask for explanation

- Ask the AI to explain the files it changed.
- Ask it to explain the component structure.
- Ask it where props and state are used.

### Ask for React quality, not only visual similarity

- A result can look correct and still be poorly structured.
- Ask whether the component structure can be improved.
- Ask whether repeated values should become props.
- Ask whether the code is too duplicated or too literal.

### Use your technical knowledge in the prompt

- Your technical knowledge helps you write better prompts.
- The more clearly you can describe the structure you want, the better the result is often going to be.
- You do not only have to say `implement this in React`.
- You can also guide the AI with technical choices about routing, styling, components, and code structure.

Examples of useful technical directions:

- `Use React Router if this needs multiple pages.`
- `Use plain CSS instead of Tailwind.`
- `Use semantic HTML where it makes sense.`
- `Split repeated UI into reusable components.`
- `Keep the first version simple and avoid over-engineering.`
- `Explain where props and state are used.`

Example prompts:

```text
Use this Figma link as design context:
[PASTE FIGMA LINK HERE]

Implement this screen in React.
Use plain CSS.
Split repeated UI into reusable components.
Explain where props are used.
```

```text
Use this Figma link as design context:
[PASTE FIGMA LINK HERE]

Implement this design in React.
Use React Router for navigation between pages.
Keep the code simple.
Explain what files you create or change.
```

```text
Use this Figma link as design context:
[PASTE FIGMA LINK HERE]

Implement this screen using components from src/components/ui.
Style it with Tailwind.
Keep the structure close to the existing codebase.
```

### Compare against your own knowledge

- Do not assume the generated code is “correct” just because it runs.
- Compare it to your own Codeagram implementation.
- Use your own React understanding to judge the result.

### Example follow-up prompts

```text
Refactor this implementation into clearer reusable React components.
Explain what you change and why.
```

```text
Use this Figma link for the navigation only.
Update my existing React code so the navigation matches the design more closely.
Keep the current functionality working.
```

```text
The UI works, but the component structure feels messy.
Please clean up the structure without changing the visual result.
```

---

### 7. Improve the result

Now improve what the AI created.

Do not just keep prompting randomly.

Use this order:

1. **Identify the problem**
   - What is wrong right now?
   - Is it mainly a visual problem, a code structure problem, or a missing interaction?
2. **Choose one thing to improve**
   - Do not try to fix everything in one prompt.
   - Pick one clear improvement first.
3. **Decide whether to improve it yourself or with AI**
   - If the change is small and you understand it, try doing it yourself.
   - If the change is larger or repetitive, ask AI for help.
4. **Give better context**
   - Link to a specific frame, component, layer, or icon when possible.
   - Smaller and more focused prompts often work better than broad ones.
5. **Test the result**
   - Run the app again.
   - Check that the change worked.
   - Make sure the previous functionality still works.

Common things to improve:

- visual accuracy
- spacing and layout
- component structure
- repeated code
- missing props
- missing state
- missing interaction
- navigation between views

Use the Codeagram app from the previous lesson as a reference:

- That version was coded from scratch.
- It was built by thinking about React structure step by step.
- It gives you a useful comparison when judging the generated result.

Ask yourself:

- Is the generated structure better or worse than the version we coded ourselves?
- Does the generated code follow the same kind of React thinking?
- Is anything in the generated version too flat, too duplicated, or harder to understand?

Example improvement prompts:

```text
Use this Figma link for the PostCard only:
[PASTE FIGMA LINK HERE]

Refactor my current implementation so PostCard becomes its own reusable component.
Keep the existing behavior working.
Explain what you change.
```

```text
Use this Figma link for the header only:
[PASTE FIGMA LINK HERE]

Update my existing React implementation so the header matches the design more closely.
Do not change the rest of the app.
```

```text
The layout works, but the code structure is messy.
Please clean up the component structure without changing the visual result.
Tell me what files you change and why.
```

Important:

- Do not only ask for visual fixes.
- Also ask for structural improvements when needed.
- A nicer-looking result is not always a better React implementation.
- Repeat this process until the result becomes clearer and more useful.

---

### 8. Add more screens or views

If your first screen works, continue.

For example in Codeagram:

1. Add one new screen or view in Figma.
   - For example a **Profile** page or a **Notifications** page.
2. Make sure the new design is structured well.
   - Clean up layout, naming, and repeated UI if needed.
3. Copy the link to the new frame or view.
4. Ask the AI to implement that one new screen in your existing React project.
5. Connect the new screen to the rest of the app.
   - For example, connect the navigation buttons or links so the screen can actually be opened.
6. Test that navigation still works.

Start with one new screen first. Do not add multiple new screens at once unless the first one is already working well.

One well-connected new screen is enough for a good first result.

Helpful technical direction:

- Ask for **React Router** if you want multiple pages or views.
- If you already have navigation in the UI, ask the AI to connect it to the new screen.

> **React Router**
>
> React Router is a library for React that helps you create navigation between pages or views in your app.
>
> It is useful when your app should move between screens such as:
>
> - feed
> - profile
> - notifications
>
> Official website:
> [reactrouter.com](https://reactrouter.com/)

Example prompt:

```text
Use this Figma link as design context:
[PASTE FIGMA LINK HERE]

Add this new screen to my existing React project.
Use React Router for navigation.
Keep the existing feed page working.
Update the navigation so this new page can be opened.
Tell me what files you create or change.
```

Another example:

```text
Use this Figma link as design context:
[PASTE FIGMA LINK HERE]

Implement this profile page in my existing React app.
Reuse existing components where possible.
Keep the code structure consistent with the rest of the project.
Update the existing navigation if needed.
```

Important:

- Add one new screen at a time.
- Reuse the components you already have when possible.
- Do not let the new page become a completely separate code style from the rest of the app.
- After each change, test that the app still runs and that navigation works.

---

### 9. Use the advanced Codeagram tasks

Now use the same workflow to extend the Codeagram app.

Use this part of the Codeagram guide:

- [Codeagram Feed with React Components: 7. Advanced Tasks (For Skilled Students or Anyone Curious)](https://github.com/cederdorff/codeagram/blob/main/docs/EXERCISE_GUIDE.md#7-advanced-tasks-for-skilled-students-or-anyone-curious)

Pick one advanced task at a time.

Do not try to implement all of them at once.

Suggested tasks:

1. Add tags to the post data
2. Add comments to the post data
3. Implement search
4. Show bookmarked posts in their own view
5. Make it possible to create new posts
6. Add one more action button

This is where you combine:

- Figma design work
- MCP context
- AI prompting
- your own React knowledge

Use this order:

1. Choose one advanced task.
2. Decide which workflow makes most sense:
   - **Workflow A: start in Figma, then go to code**
   - **Workflow B: start in code, then update the Figma design**
3. Implement a first version.
4. Inspect the result.
5. Improve it through smaller iterations.

### Workflow A: start in Figma, then go to code

Use this when the visual design should come first.

This is often a good choice for:

- tags
- comments
- buttons
- layouts
- new screens or views

Use this order:

1. Design the change in Figma first.
2. Make sure the frame or component is structured well.
3. Copy the link to the relevant frame or component.
4. Paste that link into your MCP-enabled chat in VS Code.
5. Ask the AI to implement the change in your existing React project.
6. Run the app and test the result.
7. Improve the code or design in smaller steps if needed.

Example:

- **Tags:** start in Figma, design how tags should look on the post card, then implement them in code

### Workflow B: start in code, then update the Figma design

Sometimes it makes more sense to begin in React instead of Figma.

This is useful when:

- the feature is easier to think through in code first
- the logic matters more than the visual design at the beginning
- you already know roughly how the UI should work

In that case, use this order:

1. Implement the feature in your React project first.
2. Make sure it actually works in the browser.
3. Decide what needs to be reflected in the design.
   - Do you need a new page?
   - A new component?
   - A new state or interaction pattern?
4. In Figma, choose the frame or component that should be updated.
5. Copy the link to that frame or component.
6. Ask the AI to help you update the Figma design so it matches the code you already built.
7. Check whether the design now reflects the real behavior and structure of the code.

Example prompt for this workflow:

```text
I already implemented this feature in my React project.
Now help me update the Figma design so it matches the code.

Use this Figma link as the design context:
[PASTE FIGMA LINK HERE]

Look at my current code and suggest or apply updates so the design reflects:
- the new screen or view
- the new interaction
- the new UI elements

Tell me what should change in the design.
```

Important:

- In this workflow, code comes first and Figma follows.
- This is different from the earlier workflow where Figma came first and code followed.
- Use this only when it is genuinely easier to think through the feature in code first.

Examples:

- **Comments:** decide how comments should appear and whether they are always visible or expandable
- **Search:** decide what the search should search through before you prompt
- **Bookmarked posts:** this may be easier to start in code, then update the design afterward

Important:

- Keep the task small enough that you can still understand the result.
- Be clear about what behavior you want before you prompt.
- Compare the generated result to what you would build yourself.
- Compare different prompting strategies and notice what gives the clearest result.

---

### 10. Try a new design-to-code experiment

When Codeagram feels more stable, try the workflow on a new small app or concept.

Use this order:

1. Choose a small idea.
   - Use an existing Figma design, or create one yourself (or use Figma Make to get started).
2. Keep the scope small.
   - Start with one screen or one very small flow.
3. Create a new React project.
4. Reuse your existing MCP setup in VS Code.
5. Get the Figma link for the frame or view you want to implement.
6. Prompt your MCP client.
7. Inspect the generated result.
8. Improve the result through smaller iterations.

Good starting ideas:

- a small product card view
- a simple profile page
- a small dashboard screen
- an event card or event detail page
- a booking or confirmation screen

Start simple.

Do not try to build a huge app on your first attempt.

The goal here is not to build something impressive as fast as possible.

The goal is to practice the workflow again in a new context:

- design
- context
- prompt
- inspect
- improve

---

## Minimum Success Criteria

You are on the right track if you can say yes to most of these:

1. Is the remote Figma MCP server running in VS Code?
2. Does your blank React project run locally?
3. Have you used one Figma link as design context successfully?
4. Did the AI create a working first version in React?
5. Can you explain at least some of the generated component structure?
6. Have you improved at least one part of the generated code or design?
7. Does the result feel closer to a small prototype than just a static screen?

---

## Tips for Better Results

- Start with one clean frame, not a whole product.
- Structure your Figma design before prompting.
- Ask for a simple implementation first.
- Inspect the generated code before continuing.
- Be specific when asking for improvements.
- Use your own React knowledge to clean up the result.
- Treat MCP and AI as support, not as a replacement for understanding.
- A working result is not automatically a good React solution.

---

## If You Get Stuck

1. Check whether the problem is:
   - MCP setup
   - Figma structure
   - prompting
   - React code
2. Restart VS Code and the dev server if something seems stuck.
3. Try a smaller prompt with a smaller part of the design.
4. Ask the AI to explain the code it created.
5. Ask for help if you are blocked too long.

### Common Problems

#### The MCP server does not seem to work

- Check that you set up the **remote** server, not the desktop one.
- Check that GitHub Copilot is enabled in VS Code.
- Restart VS Code and try again.
- Open the MCP configuration again and verify that the Figma server is still listed.

#### The AI does not understand the design

- Use a smaller and cleaner Figma frame.
- Link to one part of the design instead of the whole app.
- Improve the Figma structure first.

#### The React project does not run

- Make sure you ran `npm install`.
- Restart the dev server with `npm run dev`.
- Read the terminal error carefully before prompting again.

#### The generated code works but looks messy

- Ask the AI to refactor the component structure.
- Ask it to explain what it created.
- Compare it to your own Codeagram implementation.

---

## Recommended Official Resources

Start with these:

1. [VS Code and Figma: Set up the MCP server](https://help.figma.com/hc/en-us/articles/39890361040535-VS-Code-and-Figma-Set-up-the-MCP-server)
2. [Guide to the Figma MCP server](https://help.figma.com/hc/en-us/articles/32132100833559-Guide-to-the-Figma-MCP-server)
3. [Tools and prompts](https://developers.figma.com/docs/figma-mcp-server/tools-and-prompts/)
4. [Figma MCP collection](https://help.figma.com/hc/en-us/sections/35280374295831-Figma-MCP-collection)

The Figma MCP collection is a good extra resource, but I would use it as **optional support**, not as the main exercise text.

---

## Why We Are Doing This

The point of this exercise is not only to see whether AI can generate code from a design.

The real point is to understand:

- how design becomes components
- how components become React code
- where AI is helpful
- where you still need technical judgement
- how to improve generated output instead of accepting it blindly

---
