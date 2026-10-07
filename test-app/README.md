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

## Project Structure

```text
test-app/
├── data/
│   └── questions.json   # Categories, questions, answer indexes, and explanations
├── src/
│   ├── colors.js        # ANSI color helpers and display styles
│   ├── input.js         # Readline interface, selection, confirmation, and pause helpers
│   └── quiz.js          # Quiz state, shuffling, scoring, progress, and results
├── index.js             # Application entry point and main game loop
├── package.json         # Project metadata, scripts, license, and Node.js requirement
└── README.md            # Project documentation
```

The repository also contains macOS metadata entries under `__MACOSX/` and a `.DS_Store` file. These are not used by the application.

## Usage

Start the quiz from the `test-app` directory:

```bash
npm start
```

The equivalent direct Node.js command is:

```bash
node index.js
```

During a session:

1. Choose a category by entering its displayed number.
2. Choose all questions, three questions, or five questions when those options are available.
3. Press Enter to begin.
4. Choose an answer for each question by entering its number.
5. Press Enter between questions when prompted.
6. Review the score and any incorrect answers.
7. Enter `y` to play again or any response not beginning with `y` to exit.

Question order is randomized for each quiz. The answer index in the JSON data is zero-based, while the choices shown to players are numbered starting at one.

## API / Interface Documentation

This repository does not expose an HTTP API, network service, or public CLI argument interface. Its interface is an interactive terminal prompt.

The application reads `data/questions.json` relative to `index.js`, so it can be launched from another working directory when the script is invoked by its path, for example:

```bash
node /path/to/test-app/index.js
```

## Testing

The package declares the following test script:

```bash
npm test
```

This runs Node.js's built-in test runner with:

```bash
node --test
```

No test files are currently included in the repository, so the command may complete without executing project-specific test cases. There is no separate linting or coverage configuration.

## Build

There is no compilation or build step. The application runs directly from its JavaScript source files with Node.js.

## Deployment

No deployment, Docker, CI/CD, or production hosting configuration is included. The application can be run on any environment that provides Node.js 18 or newer and an interactive terminal.

## Troubleshooting

### `node` is not recognized or the version is too old

Install Node.js 18 or newer, then confirm the installation with:

```bash
node --version
```

### The application cannot load questions

Run the application with the repository's `test-app` directory intact and verify that this file exists:

```text
data/questions.json
```

Also verify that the JSON is valid and preserves the expected `categories` structure.

### Input is rejected

Selections must be entered as numbers corresponding to the displayed options. The application continues prompting until a valid number is entered. For the replay prompt, a response beginning with `y` means yes; other responses end the session.

### Colors or box-drawing characters render incorrectly

The application writes ANSI escape sequences and Unicode symbols directly to the terminal. If the output is difficult to read, use a terminal with ANSI and Unicode support; gameplay itself remains text-based.

## Contributing

To contribute, make a focused change, update the relevant source or question data, and verify the application manually with `npm start`. Run the declared test command with `npm test` before opening a pull request. Keep question answer indexes synchronized with the zero-based `options` array.

## License

This project is licensed under the MIT License, as specified in `package.json`.

## Additional Information

The application is intentionally dependency-free. `index.js` loads the question data, `Quiz` owns the state and scoring logic, `input.js` handles asynchronous terminal interaction, and `colors.js` provides presentation helpers. Errors during startup or gameplay are printed with a message and stack trace, and the process exits with status code `1`.
