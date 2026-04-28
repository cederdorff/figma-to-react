# Tool Setup Guide

**Rasmus Cederdorff (RACE)**  
Senior Lecturer & Web App Developer  
race@eaaa.dk

---

## Purpose

This guide helps you install and configure the tools we will use for web development.

The goal is not to install everything. The goal is to set up a small, reliable toolchain that works well for HTML, CSS, JavaScript, React and GitHub-based projects.

Follow the steps in this order:

1. Install VS Code.
2. Install the essential VS Code extensions.
3. Configure formatting in VS Code.
4. Create a GitHub account.
5. Install and configure Git.
6. Install and configure GitHub Desktop.
7. Install Node.js and npm.
8. Check your browser and Developer Tools.
9. Run a final setup test.

---

## 1. Install VS Code

VS Code is the code editor we will use in the course.

You will use it to write and edit:

- HTML
- CSS
- JavaScript
- React components
- Project files
- Terminal commands

Download and install VS Code:

[Download VS Code](https://code.visualstudio.com/download)

After installing, open VS Code once to make sure it starts correctly.

---

## 2. Install VS Code Extensions

Extensions add features to VS Code. Start with a small setup. Too many extensions can make VS Code slower, noisier and harder to troubleshoot.

Open the Extensions view in VS Code:

- Windows: `Ctrl + Shift + X`
- macOS: `Cmd + Shift + X`

Search for each extension by name and click **Install**.

### Essential Extensions

Install these now.

| Extension | Why we use it |
| --- | --- |
| [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) | Formats code automatically and keeps style consistent. |
| [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) | Shows JavaScript and React problems when a project includes ESLint rules. |
| [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) | Runs simple HTML, CSS and JavaScript projects locally in the browser. |

### Optional Extensions

Install these later if the course or project needs them.

| Extension | Recommendation |
| --- | --- |
| [es6-string-html](https://marketplace.visualstudio.com/items?itemName=Tobermory.es6-string-html) | Useful if we write HTML inside JavaScript template strings. Not needed for normal HTML files or most React components. |
| [ES7+ React/Redux/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets) | Useful when working actively with React. Not needed for the first setup. |
| [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client) | Useful for testing APIs. Install later if we need an API client. |

### Skip for Now

These are not needed for this setup.

| Extension | Why we skip it |
| --- | --- |
| Auto Rename Tag | VS Code already supports linked tag editing with `editor.linkedEditing`. |
| Auto Close Tag | VS Code already auto-closes HTML tags. |

---

## 3. Configure VS Code Formatting

Formatting means indentation, spacing, line breaks, quotes and general code layout.

We will use Prettier as the default formatter and make VS Code format files when you save.

In VS Code:

1. Open **Settings**.
2. Search for `format on save`.
3. Enable **Editor: Format On Save**.
4. Search for `format on paste`.
5. Enable **Editor: Format On Paste**.
6. Search for `default formatter`.
7. Select **Prettier - Code formatter**.
8. Search for `linked editing`.
9. Enable **Editor: Linked Editing**.

Linked editing makes VS Code update the matching closing HTML tag when you rename an opening tag.

### Test Formatting

Create a file called `test.js`.

Paste this:

```js
function hello(){console.log("hi")
if(true){console.log("yay")}}
```

Save the file.

It should become:

```js
function hello() {
  console.log("hi");
  if (true) {
    console.log("yay");
  }
}
```

If it does not format:

- Check that Prettier is installed.
- Check that Prettier is selected as the default formatter.
- Check that **Format On Save** is enabled.
- Save manually with `Ctrl + S` or `Cmd + S`.
- Restart VS Code if you just changed the settings.

---

## 4. Create a GitHub Account

GitHub is where we store and share code online.

Create a free account:

[Create a GitHub account](https://github.com/)

Recommendations:

- Use an email address you will keep after your studies.
- Use a username you are comfortable sharing professionally.
- Save your password in a password manager.

---

## 5. Install Git

Git tracks changes in your code. VS Code and GitHub Desktop both work better when Git is installed correctly.

Install Git before GitHub Desktop. This avoids many `Git not found` problems later.

Use the steps for your operating system.

### Windows

Download Git:

[Download Git](https://git-scm.com/downloads)

Run the Git installer.

Recommended installer choice:

- Select **Use Git from the command line and also from 3rd-party software**.

Keep the other default options unless instructed otherwise.

After installation:

1. Restart VS Code.
2. Restart your terminal.
3. Restart your computer if Git is still not found.

### macOS

Open Terminal and run:

```bash
xcode-select --install
```

This installs Apple's Command Line Tools, which include Git.

If macOS says the tools are already installed, check Git with:

```bash
git --version
```

### Verify Git

Open Terminal, PowerShell or Command Prompt and run:

```bash
git --version
```

You should see something like this:

```bash
git version 2.xx.x
```

Your exact version number may be different.

### Configure Git

Set your name and email:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Check your settings:

```bash
git config --global --list
```

Use the same email address as your GitHub account if possible.

---

## 6. Install GitHub Desktop

GitHub Desktop gives you a visual interface for Git and GitHub.

Download and install GitHub Desktop:

[Download GitHub Desktop](https://desktop.github.com/)

Then:

1. Open GitHub Desktop.
2. Sign in to **GitHub.com**.
3. Confirm your name and email.
4. Choose VS Code as your external editor if asked.

GitHub Desktop is useful for common Git tasks:

- Cloning repositories
- Seeing changed files
- Committing changes
- Pushing changes to GitHub
- Pulling updates from GitHub

---

## 7. Install Node.js and npm

Node.js lets us run JavaScript tools outside the browser.

npm is installed together with Node.js and is used to install project packages.

Download Node.js:

[Download Node.js](https://nodejs.org/en/download/)

Choose the **LTS** version.

LTS means Long Term Support. It is the stable version recommended for most users.

After installing, restart your terminal.

### Verify Node.js and npm

Open Terminal, PowerShell or Command Prompt and run:

```bash
node --version
npm --version
```

You should see two version numbers, for example:

```bash
vxx.x.x
x.x.x
```

The exact numbers depend on the current LTS version. The important part is that both commands return a version number.

If `node` or `npm` is not found:

- Restart your terminal.
- Restart VS Code.
- Restart your computer if needed.
- Reinstall Node.js using the LTS installer.

---

## 8. Browser and Developer Tools

You need a modern browser for testing websites.

Recommended browsers:

- Chrome
- Edge
- Firefox

Safari is also fine, but you may need to enable developer features manually.

Developer Tools help you inspect and debug websites.

You will use Developer Tools to:

- Inspect HTML
- Edit and test CSS
- Read JavaScript errors
- Use the Console
- Inspect network requests
- Test responsive layouts

### Open Developer Tools

Open Developer Tools:

- Windows/Linux: `F12` or `Ctrl + Shift + I`
- macOS: `Cmd + Option + I`

Open the Console directly:

- Windows/Linux: `Ctrl + Shift + J`
- macOS: `Cmd + Option + J`

Inspect an element:

1. Open a webpage.
2. Right-click an element.
3. Choose **Inspect**.

### Safari Users

If you use Safari:

1. Open Safari Settings.
2. Go to **Advanced**.
3. Enable developer features.
4. Enable full website address if available.

---

## 9. Final Setup Test

Use this final test to check that the tools work together.

### 9.1 Check Terminal Tools

Open Terminal, PowerShell or Command Prompt and run:

```bash
git --version
node --version
npm --version
```

Each command should return a version number.

### 9.2 Clone a Test Project

In GitHub Desktop:

1. Choose **File** -> **Clone Repository**.
2. Select the **URL** tab.
3. Paste this repository URL:

```txt
https://github.com/cederdorff/project-template
```

4. Choose a local folder for your code projects.
5. Click **Clone**.

Recommended project folder examples:

```bash
/Users/your-name/Developer/project-template
```

```txt
C:\Users\your-name\Developer\project-template
```

### 9.3 Open the Project in VS Code

In GitHub Desktop:

1. Click **Open in Visual Studio Code**.
2. In VS Code, open `index.html`.
3. Right-click `index.html`.
4. Select **Open with Live Server**.

The project should open in your browser.

### 9.4 Open Developer Tools

In the browser:

1. Open Developer Tools.
2. Go to the **Console** tab.
3. Check whether there are messages, warnings or errors.
4. Right-click an element on the page and choose **Inspect**.

If this works, your basic setup is ready.

---

## 10. Setup Checklist

Before the course starts, check that you have:

- VS Code installed.
- Prettier installed.
- ESLint installed.
- Live Server installed.
- Format On Save enabled.
- Git installed.
- Git configured with your name and email.
- A GitHub account.
- GitHub Desktop installed and signed in.
- Node.js installed.
- npm installed.
- A browser with Developer Tools.
- The test project running with Live Server.

---

## 11. If You Need Help

If you get stuck, include this information when asking for help:

- Your operating system.
- What you were trying to do.
- The exact error message.
- The command you ran.
- A screenshot if useful.

Example:

```txt
I am on Windows 11.
VS Code says "Git not found".
When I run git --version, I get "command not found".
How do I fix this?
```

---

## References

- [VS Code](https://code.visualstudio.com/download)
- [VS Code HTML support](https://code.visualstudio.com/docs/languages/html)
- [Git](https://git-scm.com/downloads)
- [GitHub](https://github.com/)
- [GitHub Desktop](https://desktop.github.com/)
- [GitHub Desktop documentation](https://docs.github.com/en/desktop)
- [Node.js](https://nodejs.org/en/download/)
- [npm documentation](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm/)
- [Chrome DevTools shortcuts](https://developer.chrome.com/docs/devtools/shortcuts)
- [MDN browser Developer Tools](https://developer.mozilla.org/en-US/docs/Learn_web_development/Howto/Tools_and_setup/What_are_browser_developer_tools)
