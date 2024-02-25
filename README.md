# electron-todo
Simple todo app made with Electron

# About electron-todo

This app is basic electron app showing todo functionality.

A basic electron.js application needs just these files:

- `package.json` - Points to the app's main file and lists its details and dependencies.
- `main.js` - Starts the app and creates a browser window to render HTML. This is the app's main process.
- `index.html` - A web page to render. This is the app's renderer process.
- `preload.js` - A content script that runs before the renderer process loads.

You can learn more about each of these components in depth within the [Tutorial](https://electronjs.org/docs/latest/tutorial/tutorial-prerequisites).

You can take electron-quick-start files [here](https://github.com/electron/electron-quick-start/tree/main), but I prefer to make it manually using the Tutorial above.

This app has some extra files:

- `.gitignore` — file to ignore some files while adding to your git project (especially node_modules folder). You can use [this example](https://github.com/github/gitignore/blob/main/Node.gitignore).

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

# Learning the hard way

> You can use these instructions to install Node.js and create all the necessary files from scratch for our app

## Prerequisites

Use [these instructions](https://www.electronjs.org/docs/latest/tutorial/quick-start#prerequisites) from Electron documentation to install Node.js.

## Create basic Electron app

Next, create the basic app using [these instructions](https://www.electronjs.org/docs/latest/tutorial/quick-start#create-your-application), but use `electron-todo` name for your folder name:

```bash
mkdir electron-todo
cd electron-todo
npm init
```

Use following settings for initialization of your app (change git repo and author according to your needs):

- package name: (electron-todo)
- version: (1.0.0)
- description: Simple Electron Todo app
- entry point: (index.js) main.js
- test command: npm test
- git repository: https://github.com/teterkin/electron-todo
- keywords: electron, todo, simple
- author: amteterkin@yandex.ru
- license: (ISC) MIT

 Those settings will end up at the `package.json` file after initialization complete:

```json
{
  "name": "electron-todo",
  "version": "1.0.0",
  "description": "Simple Electron Todo app",
  "main": "main.js",
  "scripts": {
    "test": "npm test"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/teterkin/electron-todo.git"
  },
  "keywords": [
    "electron",
    "todo",
    "simple"
  ],
  "author": "amteterkin@yandex.ru",
  "license": "MIT",
  "bugs": {
    "url": "https://github.com/teterkin/electron-todo/issues"
  },
  "homepage": "https://github.com/teterkin/electron-todo#readme"
}
```

Install all the prerequisites:

```bash
npm install --save-dev electron
```

Add start command to your `package.json` file:

```json
"scripts": {
    "test": "npm test",
    "start": "electron ."
  },
```

### Add source files for electron app

```bash
touch main.js
mkdir src
cd src
touch index.html renderer.js
```

First, we test `main.js` is running.

Add following to `main.js`:
```javascript
const {app, BrowserWindow } = require ('electron')

app.on('ready', () => {
    console.log('> App is ready!')
})
```

Start the app using this command:

```bash
npm start
```

You should see the following in the console output:

```bash
> electron-todo@1.0.0 start
> electron .

> App is ready!
```

# Add todo functionality 

`TODO`

# Resources for Learning Electron

- [electronjs.org/docs](https://electronjs.org/docs) - all of Electron's documentation
- [Electron Fiddle](https://electronjs.org/fiddle) - Electron Fiddle, an app to test small Electron experiments

# License
[MIT License](./LICENSE)
