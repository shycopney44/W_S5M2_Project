# Sprint 5 Module 2 Project

## Introduction

Welcome to Module 2 Project! In this project, you will practice using "vanilla" JavaScript to manipulate the DOM without any frameworks. Your goal is to build a video game using only JavaScript.

By the time you finish this project, you will have gained the foundation needed to build games such as Minesweeper, Connect-Four, Battleship, or any grid-based game you wish to create.

To successfully complete this project, you will need the following technical skills:

1. **Selecting elements** and groups of elements from the DOM.
1. **Looping** over arrays and lists of DOM elements.
1. **Manipulating class names and inline styles** of elements.
1. **Manipulating text** contents of elements.
1. **Traversing the DOM** using properties of the DOM nodes.
1. **Creating listeners** for click events and keyboard events.

In addition to these technical skills, the following soft skills will greatly impact your performance:

1. Attention to detail. Make sure there isn't a single character out of place!
1. Perseverance. Keep trying until you figure it out!
1. Patience. Make sure to read the entire README for important information.

## Instructions

You have been given a take-home coding assessment as part of the hiring process for a Web Developer position. Your task is to complete a video game using only JavaScript.

To help you complete the task, two of your future team members will provide you with instructions and advice. You can find a [fully-functional mock](https://bloominstituteoftechnology.github.io/W_U2_S5M2_module_project/) showing the desired end result.

Make sure to carefully read and follow their instructions. Good luck!

### 💾 DevOps Engineer

**Below, a DevOps Engineer will help you set up your local environment and launch the project:**

This is a **full-stack web application** that comprises both back-end and front-end components. If deployed to production, the back-end part would run in the cloud, while the front-end would execute inside the user's web browser (like Chrome for Android or Firefox for desktop).

As a front-end engineer, your focus is mainly on the files that load **on the user's device**. In this particular case, these files live inside the `frontend` folder. The `backend` folder contains a web server built in Node, but the project as a whole is managed as a Node application. As such, it contains a `package.json` file at the root, containing some meta-information like name and version, and a few useful scripts developers can use as they work on the app, like "npm test".

1. You will **clone this repository** to your computer, which will allow you to run the software locally for development purposes.

1. You will navigate your terminal to the project folder **and execute `npm install`**. This will install the libraries declared inside `package.json`. Some of these packages are needed for the back-end to do its job of serving front-end assets. Other libraries help with things like testing and linting your code.

1. After successful installation, you will run `npm start` in your terminal. On successful start, you will load the app in Chrome by **navigating the browser to `http://localhost:3003`**. The term "localhost" means "your machine," and the number is called a port, allowing multiple web servers to run on the same computer, with one server per port.

1. If you haven't already, install the [Eslint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) for VSCode. It will highlight syntax errors and problems right inside your editor, which saves tons of time.

### 🥷 Lead Developer

**Below, your Team Lead will discuss the tasks you need to complete.**

Hey! Let's make sure you're up to speed with your **action items so far**.

- [x] The app is installed on your machine, with the `start` script running in a terminal.
- [x] You studied the working [mock](https://bloominstituteoftechnology.github.io/W_U2_S5M2_module_project/).
- [x] You loaded your app in `http://localhost:3003`.

Awesome! If you look inside the `frontend` folder you will see it contains, among other assets, an `index.js` script, which is loaded inside `index.html`.

Let's discuss `index.js` and the tasks you need to complete inside that script. **You are not allowed to modify any other files.**

Have fun, and check out the Solution Video for this project if you get too stuck!

#### 👉 TASK 1 - Understand the existing code

<details>
  <summary>Click to read</summary>

  ---

Read the whole script, line by line! If you don't understand the existing code, it will be very difficult to work on it.

Use a `console.log` if you have any doubts about what kind of value a particular variable holds. Research any syntax that looks foreign. Read the comments carefully!

**In its current state, the script is performing the following DOM manipulations:**

1. Setting up a footer dynamically so that the year number is always correct.
1. Populating the `div#grid` with five children `div.row`.
1. Populating each `div.row` with five children `div.square`.
1. Adding a class name of `targeted` to one of the squares to highlight it.
1. Building a helper function to get five random indices in the range 0-24 inclusive.
1. Populating 5 random squares, using the indices above, with live mosquitoes.

**The script also declares several useful variables and helpers:**

1. A `startTime` variable and a `getTimeElapsed` function to create the Game Over message.
1. A `getAllSquares` helper function to grab all the `div.square` elements from the DOM.
1. A `keys` dictionary of the keyboard's keys used in the game. Keyboard events will contain which key was pressed.

  ---

</details>

#### 👉 TASK 2 - Use a click event to highlight a new square

<details>
  <summary>Click to read</summary>

  ---

You will have noticed by playing with the mock that clicking on the highlighted square has no effect, and clicking on a non-highlighted square removes the highlighting from the old square and applies it to the new one.

The highlighting is controlled by an extra class name on `div.square`. When clicking on a new target, the class name must be removed from the old target, or from _all_ squares for a more "brute-force" approach, and added to the clicked square.

You will find the event listener function already scaffolded in its proper place; all you have to do is implement it!

  ---

</details>

#### 👉 TASK 3 - Use the arrow keys to highlight a new square

<details>
  <summary>Click to read</summary>

  ---

You will have noticed by playing with the mock that the arrow keys can be used to target a new square.

Note that we mustn't fall out of the bounds of the grid: clicking the "up" arrow when the target is already at the top row should have no effect, and so on.

Once again, the event listener function is already scaffolded. It's up to you to make it work! Here are a few pointers and hints:

1. You can find out which key was pressed by inspecting the event's `key` property and comparing it against the `keys` dictionary at the top of the script.

1. You can determine which square is currently targeted by searching for the `div.square` element that contains the class name responsible for highlighting.

1. To make your work easier, you should take advantage of the following properties of DOM elements:

   - `.children` gives you the list of squares inside a row element.
   - `.parentElement` gives you the row containing a particular square element.
   - `.previousElementSibling` gives you the preceding square or row, if any.
   - `.nextElementSibling` gives you the following square or row, if any.

1. These properties can be chained together to easily traverse the DOM. For example: `square.parentElement.children[2].classList.add('a-cousin-of-square')`.

1. Pseudo code for "up" (SPOILER ALERT ❗):

```js
// If the key is the up key
// The current square is the square with the class name that enables highlighting
// If the parent row of the current square has a sibling row before it
// Get the index `i` of the current square within its parent row
// Remove the class name that enables highlighting from the current square
// Apply the class name to the square within the parent row's previous sibling at index `i`
```

  ---

</details>

#### 👉 TASK 4 - Use the space bar to exterminate a mosquito

<details>
  <summary>Click to read</summary>

  ---

You will have noticed by playing with the mock that the space bar is used to squash a targeted mosquito.

Note that hitting the space bar while on an empty square or on a square holding a dead mosquito has no effect.

If the square contains a live mosquito, you must edit a **data attribute** on the mosquito to mark it as dead (inspect the DOM in the mock to see the data attribute on the mosquito).

The data attribute is how you determine whether a given mosquito is dead or alive. Data attributes allow us to store string information inside DOM elements that is not meant to be rendered.

After marking the mosquito as dead, you must change the background color of the square to red using an inline style. Once the background is red, it remains red.

  ---

</details>

#### 👉 TASK 5 - End the game

<details>
  <summary>Click to read</summary>

  ---

Once the player exterminates all mosquitoes, there are some changes in the DOM that require additional logic within our "space bar" code.

Whenever you squash a mosquito, use `querySelectorAll` to find out how many _live_ mosquitoes remain. Game over is determined by all mosquitoes being dead as per their data-attribute.

One change you need to implement on game's end is that the text of `p.info` is updated to `Extermination completed in <time elapsed> seconds!`. You can use the helper function at the top of the script to determine the time elapsed since the script was loaded.

The other change is the appearance of a Restart button inside `header h2`. This button allows the player to restart the game by forcibly reloading the page within a click listener.

If you are unsure about how to force a browser window reload using JavaScript, you can ask ChatGPT by saying **"How can I force a browser window reload using JavaScript?"**, or you can search on Google using the query **"force page reload with javascript site:stackoverflow.com"**.

For extra practice, instead of reloading the browser, you can utilize your DOM manipulation skills to reset the DOM and reposition the mosquitoes.

It would be a nice touch to move the focus of the window to the Restart button upon Game Over, for easier restarting.

  ---

</details>

## FAQ

<details>
  <summary>I feel very stuck. What can I do?</summary>

Check out the Solution Video for this project in your learning platform. In it, an industry expert will walk yoy through their thinking in detail while they solve the tasks. The Solution Videos are highly recommended even if you are not stuck: you will learn lots of tricks.

</details>

<details>
  <summary>Are there automated tests in this project?</summary>

No. All testing will be manual testing, performed by the developer - you! Make sure the app behaves just like the mock. In a real team, the QA specialist or the Product Designer will easily spot the differences between the design and the implementation.

</details>

<details>
  <summary>I am getting errors when I run npm install or npm start. What is going on?</summary>

This project requires Node correctly installed on your computer in order to work. Your learning materials should have covered installation of Node. Sometimes Node can be installed but mis-configured. You can try executing `npm run fixit` (check `package.json` to see what this does), but if Node errors are recurrent, it indicates something is wrong with your machine or configuration, in which case you should request assistance from Staff.

</details>

<details>
  <summary>Do I need to install libraries or add scripts to the HTML?</summary>

No. Everything you need should be installed already.

</details>

<details>
  <summary>Why am I not allowed to edit the CSS file?</summary>

The CSS is the domain of a different team, and in this particular project we're not supposed to touch it. Do not use inline styles to get around this limitation! It will only make the CSS team angry. And believe us, you want CSS specialists happy because they can write CSS twenty times faster than you.

</details>

<details>
  <summary>Why am I not allowed to edit the HTML file?</summary>

This particular part of the product is a Single Page Application, so the HTML is mostly empty and the page is generated automatically using JavaScript. Building a large grid using only HTML would be extremely tedious!

</details>

<details>
  <summary>My page does not work! How do I debug it?</summary>

Save your changes, and reload the site in Chrome. If you have a syntax problem in your code, the app will print error messages in the Console. Focus on the first message. Place console logs right before the crash site (errors usually inform of the line number where the problem is originating) and see if your variables contain the data you think they do. If there are no errors but the page is not doing what it's supposed to, the debugging technique is similar: put console logs to ensure that the code you are working on is actually executing, and to check that all variables in the area hold the correct data.

</details>

<details>
  <summary>I messed up and want to start over! How do I do that?</summary>

**Do NOT delete your repository from GitHub!** Instead, commit _frequently_ as you work. Make a commit whenever you achieve _anything_ and the app isn't crashing in Chrome. This in practice creates restore points you can use should you wreak havoc with your app. If you find yourself in a mess, use `git reset --hard` to simply discard all changes to your code since your last commit. If you are dead-set on restarting the challenge from scratch, you can do this with Git as well, but it is advised that you request assistance from Staff.

</details>

<details>
  <summary>Why are there so many files in this project?</summary>

Although a small, "old-fashioned" website might be made of just HTML, CSS and JS files, these days we mostly manage projects with Node and its package manager, NPM. Node apps typically have a `package.json` file and several other configuration files placed at the root of the project. This project also includes automated tests and a web server, which adds a little bit of extra complexity and files.

</details>

<details>
  <summary>Is this how web projects are normally organized?</summary>

Web projects can be organized in a million ways, there aren't many standards. Some developers like the freedom, while others prefer to use opinionated frameworks, which can do a lot of magic but prescribe that folders and files be structured and named just so.

</details>

<details>
  <summary>Why is all code inside index.js wrapped inside a function?</summary>

This way we can easily import your code as a single function should we want to run it through automated tests.

</details>

<details>
  <summary>What are the package.json and package-lock.json files?</summary>

The `package.json` file contains meta-information about the project like its version number, scripts that the developer can execute, and a list of the dependencies that are downloaded when you execute `npm install`. There can be some wiggle room to allow newer versions of the dependencies to be installed, so the `package-lock.json` file, when present, makes sure the exact same versions of everything are used every time the project is installed from scratch.

</details>

<details>
  <summary>What is the .eslintrc.js file?</summary>

This file works in combination with the Eslint extension for VSCode to highlight syntax errors and problems in your code. By editing this file you can customize your linting rules.

</details>
