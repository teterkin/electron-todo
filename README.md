# electron-todo
Simple todo app made with Electron.

# About electron-todo

This app is basic electron app showing todo functionality.

My goal is to create something simple, but still it should have at least some usefulness: in our case it will be a todo app.

README has a **"Quick start"** section, to *get the code and run it*.

But also it has a **"Learning the hard way"** section, where novice Electron users can *learn the Electron app development process gradually*: step by step.

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
touch index.html preload.js renderer.js style.css
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

## Add Browser Process

In order to add Browser process to our app we need to prepare four things:

1. We need to fill our `index.html` file to display some text in Browser window.
2. We need to fill our `style.css` file to make out app beautiful.
3. We need to fill our `preload.js` file to change HTML file dynamically.
4. We need to modify our `main.js` file to load those new components above and do some additional useful stuff.

### index.html

First, let's add code to our `index.html` file we created in `src` folder:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <!-- https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP -->
    <meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self'">
    <title>Hello Electron World!</title>
    <link rel="stylesheet" type="text/css" href="./style.css">
  </head>
  <body>
    <h1>Hello World!</h1>
    This Electron app is using following software components:
    <ul>
        <li>Node.js&nbsp; ver. <span id="node-version"></span>;</li>
        <li>Chromium ver. <span id="chrome-version"></span>;</li>
        <li>Electron ver. <span id="electron-version"></span>.</li>
    </ul>
  </body>
</html>
```

Note, this code has some placeholders designated with `<span id="<Some_ID>"></span>` *HTML* spans. We will use JavaScript code later to fill these placeholders with actual versions for Node.js, Chromium and Electron.

Also note that at the end of the header section we added link to our `style.css` file.

### style.css

This file is pretty simple:

```css
body {
    font-family: 'Courier New', Courier, monospace;
    font-size: larger;
}

span {
    color: red;
}
```

It just makes default font to larger monospace font and paints span sections of the document with red color.

### preload.js

Add content to our `preload.js` file:

```javascript
window.addEventListener('DOMContentLoaded', () => {
  const replaceText = (selector, text) => {
    const element = document.getElementById(selector)
    if (element) element.innerText = text
  }

  for (const dependency of ['chrome', 'node', 'electron']) {
    replaceText(`${dependency}-version`, process.versions[dependency])
  }
})
```

This file will be run just before the renderer process is loaded. It has access to both renderer globals (e.g. window and document) and a Node.js environment (to do some fancy stuff).

Particularly here we adding Event Listener on 'DOMContentLoaded' event. When fired, it will create a function and run the function from the for loop.

Function gets two attributes (selector name and text to replace with) and do simple replacement of inner text of particular selector with the text specified. 

The for loop goes through all the software components we need (chrome, node, electron) and run the function created specifying selector name and version, getting those versions from global `process` object.

### main.js

First, we need to add path module to our `main.js` file. Add it to the top of the file, next to first line:

```javascript
const path = require('node:path')
```

Next we add `createWindow` function (which will be run on app `whenReady` event later):

```javascript
const createWindow = () => {
  // Create the browser window.
  const mainWindow = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      preload: path.join(__dirname, 'preload.js')
    }
  })

  // and load the index.html of the app.
  mainWindow.loadFile('index.html')

  // Open the DevTools.
  // mainWindow.webContents.openDevTools()
}
```

Now let's add listener which fill be fired on app `whenReady` event.

We will add some extra code for application to run smoothly on any supported platform.

Place the following code at the end of `main.js` file:

```javascript
// This method will be called when Electron has finished
// initialization and is ready to create browser windows.
// Some APIs can only be used after this event occurs.
app.whenReady().then(() => {
  createWindow()

  app.on('activate', () => {
    // On macOS it's common to re-create a window in the app when the
    // dock icon is clicked and there are no other windows open.
    if (BrowserWindow.getAllWindows().length === 0) createWindow()
  })
})

// Quit when all windows are closed, except on macOS. There, it's common
// for applications and their menu bar to stay active until the user quits
// explicitly with Cmd + Q.
app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') app.quit()
})

// In this file you can include the rest of your app's specific main process
// code. You can also put them in separate files and require them here.
```

Start the app again:

```bash
npm start
```

You should see the following in the console output:

```bash
> electron-todo@1.0.0 start
> electron .

> App is ready!
```

## Add todo functionality 

`TODO`

# Resources for Learning Electron

- [electronjs.org/docs](https://electronjs.org/docs) - all of Electron's documentation
- [Electron Fiddle](https://electronjs.org/fiddle) - Electron Fiddle, an app to test small Electron experiments

# License
[MIT License](./LICENSE)
