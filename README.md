A library to give file dropping/selecting abilities to any HTML element.

[![Build Status](https://travis-ci.org/lifenautjoe/droppable.svg?branch=master)](https://travis-ci.org/lifenautjoe/droppable) ![Human Friendly](https://img.shields.io/badge/human-friendly-brightgreen.svg) [![Coverage Status](https://coveralls.io/repos/github/lifenautjoe/droppable/badge.svg?branch=master)](https://coveralls.io/github/lifenautjoe/droppable?branch=master)

## Table of Contents

- [Motivation](#motivation)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Development](#development)
  * [Clone the repository](#clone-the-repository)
  * [Use npm commands](#use-npm-commands)

## Motivation

Wouldn't it be great if you could give any HTML element the ability of dropping files in it or clicking it to select the files to drop in it?

And what's better, that you could retrieve these files by listening to an event?

Well this library does exactly that!

## Features

* Restrict to single or multiple files
* CSS class added when files are being dragged on top of the HTML element.
* Clicking on the html element also prompts user for files.
* Zero dependencies
* Tiny! (~4 KB Minified)

## Basic usage

````typescript
const Droppable = require('droppable');

const droppable = new Droppable({
    element: document.querySelector('#my-droppable-element')
})

droppable.onFilesDropped((files) => {
    console.log('Files were dropped:', files);
});
````

## Installation

```bash
npm install droppable
```

## Advanced usage

### Create a droppable element

````typescript
const Noel = require('Noel');

const droppable = new Droppable({
    element: document.querySelector('#my-droppable-element')
});
````

### Listen for files dropped
```typescript
droppable.onFilesDropped((files) => {
    console.log('Files were dropped:', files);
});
```

### Remove listener for files dropped
`onFilesDropped` returns a function which when called removes the event listener
```typescript
const eventRemover = droppable.onFilesDropped((files) => {
    console.log('Files were dropped on the element:', files);
});

eventRemover();
```

### Get the latest dropped files
```typescript
const latestDroppedFiles = droppable.getLatestDroppedFiles();
```

### Trigger prompt for files
Sometimes you will want to prompt the user for files without him dropping files or clicking the element.
```typescript
droppable.promptForFiles();
```

### Prompt for files when clicked
**This is by default `true`**

The user will be prompted for files when the droppable element is clicked

```typescript
// On instantiation
const droppable = new Droppable({
    element,
    isClickable: false
})

// On runtime
droppable.setIsClickable(true);
```

### Accept multiple dropped/selected files
**This is by default `true`**

The user will be able to drop or select multiple files.

```typescript
// On instantiation
const droppable = new Droppable({
    element,
    acceptsMultipleFiles: false
})

// On runtime
droppable.setAcceptsMultipleFiles(true);
```

### Append CSS class when files are dragged on element
**This is by default `true`**

The class `dragover` will be added to the droppable element when files are being dragged on it.

```typescript
// On instantiation
const droppable = new Droppable({
    element,
    appendStatusClasses: false
})

// On runtime
droppable.setAppendStatusClasses(true);
```


### Clean up event listeners
The library attaches several events to the HTML element which is made droppable.
When you're done remember to call the `cleanUp` function
```typescript
droppable.cleanUp();
```


## Development

### Clone the repository

```bash
git clone git@github.com:lifenautjoe/droppable.git
```

### Use npm commands

* `npm t`: Run test suite
* `npm start`: Runs `npm run build` in watch mode
* `npm run test:watch`: Run test suite in [interactive watch mode](http://facebook.github.io/jest/docs/cli.html#watch)
* `npm run test:prod`: Run linting and generate coverage
* `npm run build`: Generate bundles and typings, create docs
* `npm run lint`: Lints code
* `npm run commit`: Commit using conventional commit style \([husky](https://github.com/typicode/husky) will tell you to use it if you haven't :wink:\)

Author [Joel Hernandez](https://instagram.com/lifenautjoe)
