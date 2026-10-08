# User Provisioning App: File Flow (Start to End)

## The Path in One Line

```
npm run dev → vite.config.js → index.html → src/main.jsx → src/App.jsx → Browser Console
```

## Flow Diagram

```
┌────────────────────┐
│  npm run dev       │  Starts the Vite dev server (defined in package.json)
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│  vite.config.js    │  Tells Vite to use the React plugin
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│  index.html        │  Browser loads this page. It has <div id="root"> and
└─────────┬──────────┘  a script tag pointing to /src/main.jsx
          │
          ▼
┌────────────────────┐
│  src/main.jsx      │  1. Imports Bootstrap CSS
└─────────┬──────────┘  2. Imports the App component
          │             3. Renders <App /> into <div id="root">
          ▼
┌────────────────────┐
│  src/App.jsx       │  Draws the form, holds the data in state,
└─────────┬──────────┘  validates the fields, handles Submit
          │
          ▼
┌────────────────────┐
│  Browser Console   │  On valid Submit: console.log(form data)
└────────────────────┘
```

## Step-by-Step

### 1. `package.json`: the starting point
Running `npm run dev` looks up the `dev` script in this file, which runs `vite`. This file also lists the dependencies (React, Bootstrap, Vite).

### 2. `vite.config.js`: the build setup
Vite reads this file first. It enables the React plugin so Vite understands JSX.

### 3. `index.html`: the page the browser loads
Opening `http://localhost:5173` loads this file. It contains an empty `<div id="root"></div>` and a script tag that loads `/src/main.jsx`.

### 4. `src/main.jsx`: the entry point
This file connects React to the page:
- Imports Bootstrap's CSS, so the styling applies to the whole app.
- Imports the `App` component from `App.jsx`.
- Finds `<div id="root">` and renders `<App />` inside it.

### 5. `src/App.jsx`: the application
This is where everything happens:
1. Shows the form: First Name, Last Name, Email Address, Role (dropdown) and a Submit button.
2. Stores what the user types in state (`useState`).
3. On Submit click, checks that all fields are filled in and the email is valid.
4. If invalid, Bootstrap highlights the problem fields in red.
5. If valid, logs the data to the browser console.

### 6. Browser console: the result
Press F12 and open the **Console** tab to see the logged user data, for example:

```js
User provisioning data: { firstName: "Jane", lastName: "Doe", email: "jane@example.com", role: "Role 1" }
```

## Summary Table

| Order | File | Role |
|-------|------|------|
| 1 | `package.json` | Defines the `npm run dev` command and the dependencies |
| 2 | `vite.config.js` | Configures Vite with the React plugin |
| 3 | `index.html` | Page with the empty `root` div that the browser loads |
| 4 | `src/main.jsx` | Loads Bootstrap CSS and renders `App` into `root` |
| 5 | `src/App.jsx` | The form, validation and submit logic |
| 6 | Browser console | Where the submitted data is logged |

## Where to Make Changes

- **Change the role list:** edit the `ROLES` array at the top of `src/App.jsx`.
- **Change what happens on Submit:** edit `handleSubmit` in `src/App.jsx`.
- **Change the page title:** edit `<title>` in `index.html`.
