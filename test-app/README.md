# Quiz CLI

An interactive command-line quiz game for learning JavaScript, Node.js, and general programming concepts.

## Overview

Quiz CLI is a dependency-free Node.js terminal application. It loads quiz content from a local JSON file, lets the player choose a category and question count, presents shuffled multiple-choice questions, gives immediate feedback and explanations, and displays a final score with incorrect-answer review.

The project also serves as a small example of modern JavaScript development with ES modules, asynchronous file operations, `readline`, classes, array methods, destructuring, template literals, and ANSI terminal styling.

## Features

- Interactive terminal-based gameplay.
- Three included categories:
  - JavaScript Basics
  - Node.js Fundamentals
  - General Programming
- Select all available questions or a shorter quiz when the category supports it.
- Fisher–Yates shuffling for each quiz session.
- Numbered answer selection with input validation.
- Progress bar and question counter.
- Immediate correct/incorrect feedback.
- Explanations for questions that provide them.
- Final score, percentage, and performance message.
- Review of questions answered incorrectly.
- Option to start another quiz without restarting the process.
- ANSI color output implemented with Node.js code only; no runtime dependencies are required.

## Technologies Used

- JavaScript (ECMAScript modules)
- Node.js built-in modules:
  - `node:fs/promises` for loading quiz data
  - `node:path` and `node:url` for locating the data file in an ES-module context
  - `node:readline` for terminal input
- JSON for question and category data
- Node.js built-in test runner configuration via `node --test`

## Prerequisites

- Node.js 18.0.0 or newer. This requirement is declared in `package.json`.
- A terminal capable of running an interactive Node.js process. ANSI colors are emitted directly by the application.

No database, external service, API key, environment variable, or third-party package is required.

## Installation

Clone or download the repository, then move into the application directory:

```bash
cd test-app
```

The project has no declared dependencies, so an `npm install` step is not required. Verify that Node.js is available:

```bash
node --version
```

The reported version must satisfy Node.js `>=18.0.0`.

## Configuration

Quiz content is stored in:

```text
data/questions.json
```

The application expects this file to contain a top-level `categories` object. Each category has a `name` and a `questions` array. Each question uses the following fields:

- `question`: question text.
- `options`: ordered answer choices.
- `answer`: zero-based index of the correct option.
- `explanation`: optional explanation shown after the answer.

There is no `.env` file or other runtime configuration documented by the repository. Changes to `data/questions.json` are loaded when the application starts.
