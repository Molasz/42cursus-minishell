# minishell

_This project has been created as part of the 42 curriculum by molasz-a & akozin._

> Part of [42 Barcelona — molasz-a](https://github.com/Molasz/42), a monorepo centralizing every project completed at 42 Barcelona.

## Description

**minishell** is one of the most significant projects at 42, requiring the creation of a custom command-line interpreter, or shell. This project provides a deep dive into process management, parsing, and the inner workings of a shell like `bash`.

The goal is to create a program that can parse and execute user-input commands, handle pipes, redirections, environment variables, and implement a set of built-in commands.

---

## Features

- **Command Prompt:** Displays a prompt and waits for user input.
- **History:** Stores and allows navigation of command history (using the `readline` library).
- **Parsing:**
  - **Tokenizer:** Splits the input string into a sequence of tokens.
  - **Parser:** Builds a command structure from the tokens.
- **Execution:**
  - **Command Execution:** Executes external commands found in the system's `PATH`.
  - **Pipes (`|`):** Chains multiple commands together.
  - **Redirections:**
    - Input: `<`
    - Output: `>` (truncate) and `>>` (append)
    - `here_doc`: `<<`
- **Environment Variables:**
  - Expansion of variables (e.g., `$USER`).
  - Handling of the exit status (`$?`).
- **Built-in Commands:**
  - `echo` (with the `-n` option)
  - `cd`
  - `pwd`
  - `export`
  - `unset`
  - `env`
  - `exit`
- **Signals:** Handles `Ctrl-C`, `Ctrl-D`, and `Ctrl-\` gracefully.

---

## Architecture

![Skills](https://skillicons.dev/icons?i=c,linux)

The minishell pipeline can be broken down into several stages:

1.  **Read:** Read a line of input from the user using `readline`.
2.  **Tokenize:** The input line is split into a series of tokens (words, operators, etc.).
3.  **Parse:** The tokens are parsed to build an execution tree, identifying commands, arguments, pipes, and redirections.
4.  **Expand:** Environment variables and special characters are expanded.
5.  **Execute:** The commands are executed. This involves forking processes, setting up pipes and redirections, and calling `execve` for external commands or running built-in functions.

The project is highly modular, with different components responsible for each stage of the pipeline.

---

## ⚙️ Instructions

The project uses the `readline` library, which needs to be downloaded and compiled.

```bash
# This will download, configure, and compile all necessary libraries,
# and then compile the minishell project.
make

# Cleanup
make clean
make fclean

# Recompile
make re
```

### Usage

To start the shell:

```bash
./minishell
```

---

_molasz-a | akozin · 42 Barcelona_
