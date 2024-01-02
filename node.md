# Introduction to Node.js

---

## What is Node and why do we need it?

- JS runtime built on Chrome's V8 JS engine - basically busted out of the browser so it can run on a server
- Lets us build server-side web applications (like APIs) with JS
- Non-blocking, event-driven I/O -> means it's fast and scalable
- It's used for a lot of things! You use Slack and VSCodium -- they are built using Node

---

## Node vs JavaScript in the browser

- Both have a set of standard objects: `Array`, `String`, `Object`, `Date`, etc
- Node has no DOM (no `window` and no `document`)
- Node has a standard library (modules) that can do things like work with the filesystem

---

### Non-blocking

When a request is made to a Node server, it doesn't wait to finish processing that request before it starts processing the next request.

---

### Event-driven

Node uses events to handle requests. A request comes in and triggers an event. The server listens for that event and then runs the code associated with that event.

---

## I/O is input/output

- Input: reading data from a source (like a file or a database)
- Output: writing data to a destination (like a file or a database)

---

## There are lots of possible I/O Sources

- File system on the server
- Databases like MongoDB or PostgreSQL
- HTTP requests from a web browser or mobile app
- APIs like Stripe or Google Maps (there are lots and lots of APIs)

---

## Running Node locally

Check that you have `node` and `npm` installed by running `node -v` and `npm -v` in your terminal.

- Run `node <filename>` to run a JS file in Node

---

## Node REPL

Run `node` in your terminal to open up the Node REPL

REPL stands for 

**R**ead

**E**valuate

**P**rint

**L**oop

---

## Nodemon

- Install [nodemon](https://nodemon.io/) to automatically restart your server when you make changes to your code
- Run `nodemon <filename>` to run a JS file in Node with nodemon

---

## Modules

Modules provide a way to organize your code into separate files. You can write code for one purpose in a single file, then import that files into any other file you want to use it in.

---

- You can also create your own modules and import them into your code
- Modules are just JS files that export something
- You can export a function, an object, a class, etc
- You can import a module into another module using `require`
- You can also import a module into another module using `import` and `export` (ES6 syntax)

---

## ES Modules

You've been using this syntax in Vue to import and export components.

```js
// App.vue

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

```

---

## ESM import/export works in Node, but...

As of version 15.3.0, you can use ESM in Node, but you have to do a few things to make it work.

- Add `"type": "module"` to your `package.json` file
- Change the file extension of your JS files to `.mjs`
- Use `import` and `export` instead of `require` and `module.exports`

---

## CommonJS (CJS) Modules

The default way to import and export modules in Node using the `require` function and the `module.exports` object.

---

### exporting a module


```js
// define and export a module
// lib.js

const default_theme = 'dark'

const add(num1, num2) {
  return num1 + num2
}

module.exports = {
  default_theme,
  add
}
```

---

### importing a module

```js
// import a module in another file
// index.js
const { default_theme, add } = require('./lib.js')

console.log(default_theme) // 'dark'

// or you can import the whole module into a variable which will "namespace" all the exported values
const lib = require('./lib.js')

console.log(lib.default_theme) // 'dark'
```

---

## A note about `require`

`require` is a function that takes a string as an argument. The string is the path to the module you want to import. The path can be relative or absolute.

- Relative paths start with `./` or `../`
- Absolute paths start with `/` or `~/`
- You can omit the file extension if it's a `.js` file
- You can omit the path if it's a built-in module or a module installed in `node_modules`

---

All of these require statements are potentially valid, depending on the location and name of the module you are trying to include:

```js
const utils = require('./utils.js')
const myUtils = require('./utils')
const stuff = require('/lib/foo/blah/stuff.js')
const fs = require('fs')
```

---

## Node's Standard Library

Let's check out a few of the modules in Node's standard library.

- [`fs` - file system](https://nodejs.org/docs/latest/api/fs.html)
  - check out [fs.readFile](https://nodejs.org/docs/latest/api/fs.html#fsreadfilepath-options-callback)
- [`process`](https://nodejs.org/docs/latest/api/process.html) - information about the current process
  - check out [`process.argv`](https://nodejs.org/docs/latest/api/process.html#processargv)
- [`readline`](https://nodejs.org/docs/latest/api/readline.html) - read from a stream one line at a time
  - check out [`readline.createInterface`](https://nodejs.org/docs/latest/api/readline.html#readline_readline_createinterface_options)

---

### more modules

- [`http`](https://nodejs.org/docs/latest/api/http.html) - create an HTTP server
  - check out [`http.createServer`](https://nodejs.org/docs/latest/api/http.html#http_http_createserver_options_requestlistener)
- [global objects](https://nodejs.org/docs/latest/api/globals.html#global-objects) (not a module, but still part of the standard library)
- [URL](https://nodejs.org/docs/latest/api/url.html#url)
  - check out the [`URL` class](https://nodejs.org/docs/latest/api/url.html#class-url)
