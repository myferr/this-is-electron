# This is Electron. (An introduction to Electron.js)

Electron is a **JavaScript framework** used for building desktop applications. Using the power of **JavaScript** and web development Electron makes desktop apps.

> index.js - JavaScript
```javascript
const { app, BrowserWindow } = require('electron/main')

const path = require('node:path')

function createWindow () {
  const win = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      preload: path.join(__dirname, 'preload.js')
    }
  })

  win.removeMenu()
  win.loadFile('./src/gui/index.html')
}

  

app.whenReady().then(() => {
  createWindow()

  app.on('activate', () => {
    if (BrowserWindow.getAllWindows().length === 0) {
      createWindow()
    }
  })
})

app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') {
    app.quit()
  }
})
```

Using this JavaScript code my HTML file at `./src/gui/index.html` is ran as a desktop app! Turning HTML, CSS and JS into applications for desktop, Electron is super easy to download.

## Downloading Electron
> Node.JS and NPM are required in order to use Electron.JS
 
Electron is super easy to download using [NPM](https://www.npmjs.com/)!

◉ Installing NPM

○ [Go here to install NPM](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)


◉ Installing Electron.js

○ Enter in your command line `npm install electron`

## Setting up an Electron project

After downloading Electron run in your command line `npm init`. This will prompt you with a series of questions on setting up your `package.json`!

<img src="images/Pasted image 20240208115328.png">

After that you should have two files. Your first file is your `index.js` file and your second file is `package.json`. Inside of your `package.json` you want this in your scripts:

```json
  "scripts": {
    "start": "electron ."
  }
```

Then after that create a folder called `src` put your `index.js` inside of your `src` folder.
Inside of the `src` folder create a file called `preload.js`, inside of your `preload.js` enter the following code:

```javascript
window.addEventListener('DOMContentLoaded', () => {
  const replaceText = (selector, text) => {
    const element = document.getElementById(selector)
    if (element) element.innerText = text
  }
  
  for (const type of ['chrome', 'node', 'electron']) {
    replaceText(`${type}-version`, process.versions[type])
  }
})
```

After that create a folder inside your `src` folder and name it `gui`. Inside of your `gui` folder add your HTML, CSS and JavaScript files and save it all!

<img src="images/Pasted image 20240208115924.png">

You should have your files looking like this now! Go into your terminal and run `npm start`
that will start your Electron application!

<img src="images/Pasted image 20240208120115.png">
<img src="images/Pasted image 20240208120144.png">

## Learn more about Electron

You've now learned how to setup a basic Electron application!
To learn even more go to the [official documentation for Electron](https://www.electronjs.org/docs/latest/)
