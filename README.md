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

## Project Structure

```text
repository-root/
├── README.md
└── test-app/
    ├── data/questions.json   # Categories and quiz questions
    ├── src/colors.js         # ANSI color helpers
    ├── src/input.js          # Readline input and selection helpers
    ├── src/quiz.js           # Quiz state, scoring, shuffling, and results
    ├── index.js              # Application entry point and game loop
    └── package.json          # Scripts, metadata, license, and Node.js requirement
```

The repository also contains macOS metadata under `__MACOSX/` and `.DS_Store`; these files are not used by the application.

## Usage

From the `test-app` directory, start the application with:

```bash
npm start
```

The equivalent command is:

```bash
node index.js
```

During a session:

1. Choose a category by entering its displayed number.
2. Choose the question count.
3. Press Enter to begin.
4. Select each answer by entering its number.
5. Review the score and incorrect answers.
6. Enter `y` at the replay prompt to start another quiz; any other response exits.

Question order is randomized for every quiz. JSON answer indexes are zero-based, while displayed choices are numbered from one.

## API / Interface Documentation

The project does not expose an HTTP API, network service, or command-line argument interface. Its interface is an interactive terminal prompt.

## Testing

Run the declared Node.js test command from `test-app`:

```bash
npm test
```

This executes `node --test`. No test files are currently included, and there is no separate linting or coverage configuration.

## Build

There is no compilation or build step. The application runs directly from its JavaScript source files.

## Deployment

No Docker, CI/CD, hosting, or other deployment configuration is included. Run the application in an environment with Node.js 18 or newer and an interactive terminal.

## Troubleshooting

### Node.js is unavailable or too old

Install Node.js 18 or newer and verify it with `node --version`.

### Questions cannot be loaded

Run the application with `test-app/data/questions.json` present. If the file was edited, ensure it remains valid JSON and retains the expected `categories` structure.

### Input is rejected

Enter the number corresponding to a displayed option. The application continues prompting until a valid selection is entered.

### Terminal formatting is incorrect

The application emits ANSI escape sequences and Unicode symbols. Use a terminal with ANSI and Unicode support for the intended presentation.

## Contributing

Make a focused change, update the relevant source or question data, run `npm start` for a manual check, and run `npm test` before opening a pull request. When adding questions, keep each `answer` value synchronized with the zero-based `options` array.

## License

This project is licensed under the MIT License, as specified in `test-app/package.json`.

## Additional Information

`index.js` loads the question data and controls the game loop. `Quiz` owns question state and scoring, `input.js` handles asynchronous terminal interaction, and `colors.js` provides presentation helpers. Startup or runtime errors are printed with a message and stack trace before the process exits with status code `1`.
