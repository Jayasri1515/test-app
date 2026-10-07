# Quiz CLI

An interactive, dependency-free command-line quiz game for learning JavaScript, Node.js, and general programming concepts.

## Overview

Quiz CLI is a Node.js terminal application. It loads quiz content from `test-app/data/questions.json`, lets players choose a category and quiz length, presents shuffled multiple-choice questions, gives immediate feedback and explanations, and displays a final score with a review of incorrect answers.

The project also demonstrates modern JavaScript and Node.js concepts, including ES modules, asynchronous file operations, `readline`, classes, array methods, destructuring, template literals, and ANSI terminal styling.

## Features

- Interactive terminal gameplay.
- JavaScript Basics, Node.js Fundamentals, and General Programming categories.
- All-question, three-question, or five-question quiz lengths when supported by a category.
- Fisher–Yates question shuffling for each session.
- Numbered answer selection with input validation.
- Progress bar and question counter.
- Immediate correct/incorrect feedback and optional explanations.
- Final score, percentage, and performance message.
- Incorrect-answer review.
- Replay without restarting the process.
- No third-party runtime dependencies.

## Technologies Used

- JavaScript using ECMAScript modules.
- Node.js 18 or newer.
- Node.js built-in modules: `node:fs/promises`, `node:path`, `node:url`, and `node:readline`.
- JSON question data.
- Node.js built-in test runner.

## Prerequisites

- Node.js `>=18.0.0`, as declared in `test-app/package.json`.
- An interactive terminal with ANSI color and Unicode support recommended.

No database, external service, API key, environment variable, or third-party package is required.

## Installation

Clone or download the repository and enter the application directory:

```bash
cd test-app
```

There are no declared dependencies, so `npm install` is not required. Confirm the Node.js version:

```bash
node --version
```

The version must satisfy `>=18.0.0`.

## Configuration

Quiz content is stored in `test-app/data/questions.json`. It contains a top-level `categories` object. Each category has a display `name` and a `questions` array. Each question contains:

- `question`: question text.
- `options`: ordered answer choices.
- `answer`: zero-based index of the correct option.
- `explanation`: optional feedback shown after answering.

The application does not use `.env` files or other runtime configuration.

<!-- README_CONTINUE -->
