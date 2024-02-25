# electron-todo
Simple electron todo app made with electron

# About electron-todo

This app is basic electron app showing todo functionality.

A basic Electron application needs just these files:

- `package.json` - Points to the app's main file and lists its details and dependencies.
- `main.js` - Starts the app and creates a browser window to render HTML. This is the app's main process.
- `index.html` - A web page to render. This is the app's renderer process.
- `preload.js` - A content script that runs before the renderer process loads.

You can learn more about each of these components in depth within the [Tutorial](https://electronjs.org/docs/latest/tutorial/tutorial-prerequisites).

You can take electron-quick-start files [here](https://github.com/electron/electron-quick-start/tree/main), but I prefer to make it manually using the Tutorial above.

This app has some extra files:

- `TODO`

You can see original todo idea at [codeburst.io](https://codeburst.io/build-a-todo-app-with-electron-d6c61f58b55a)

# Quick start

To clone and run this repository you'll need [Git](https://git-scm.com/) and [Node.js](https://nodejs.org/en/download/) (which comes with [npm](http://npmjs.com/)) installed on your computer.

Next, run these commands from command line:

```bash
# Clone this repository
git clone git@github.com:teterkin/electron-todo.git

# Go into the repository
cd electron-todo

# Install dependencies
npm install

# Run the app
npm start
```

Note: If you're using Linux Bash for Windows, see [this guide](https://www.howtogeek.com/261575/how-to-run-graphical-linux-desktop-applications-from-windows-10s-bash-shell/) or use node from the command prompt. Also you can use [Git Bash for Windows](https://gitforwindows.org/).

# Resources for Learning Electron

- [electronjs.org/docs](https://electronjs.org/docs) - all of Electron's documentation
- [Electron Fiddle](https://electronjs.org/fiddle) - Electron Fiddle, an app to test small Electron experiments

# License
[MIT License](./LICENSE)
