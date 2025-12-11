# ft_minishell

[![Project: 42](https://img.shields.io/badge/Project-42-blue.svg)](https://www.42.fr/)
[![Language: C](https://img.shields.io/badge/Language-C-555)](https://en.wikipedia.org/wiki/C_(programming_language))
![Status: Production-ready](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)

Developed by **jamorale** and [asandova-ui](https://github.com/asandova-ui)


---

## Project overview

**minishell** is a professional-grade minimal Unix shell implemented in C as a capstone-style project aligned with the 42 curriculum.  
The project demonstrates a complete, reliable shell runtime environment capable of parsing and executing user commands, handling interactive input with history support, running pipelines, and managing I/O redirections — all while providing a clear, maintainable codebase that follows strict style and architecture conventions.

This repository contains the production-ready implementation developed collaboratively by `asandova-ui` and `jamorale`. The implementation has been designed for Linux environments (Ubuntu recommended) and built using `gcc` and `make`.

---

## Key goals

- Provide a robust, POSIX-style interactive shell experience for typical workflows.
- Implement accurate command parsing (tokenization, quoting, and environment expansions).
- Support multi-stage pipelines, input/output redirections, and heredoc interactions.
- Offer a set of core built-in commands required for daily shell usage.
- Integrate a high-quality interactive user experience via `readline` for editing and history.
- Ensure solid process and signal handling so foreground processes behave predictably.
- Maintain a modular, well-documented codebase following strict style guidelines.

---

## Features

### Command parsing & expansion
- Full tokenization with support for single (`'`) and double (`"`) quotes.
- Environment variable expansion (`$VAR`) and special variable `$?` (last command exit status).
- Proper handling of escaped characters when applicable.

### Built-in commands
- `echo` — supports `-n` and standard echo semantics.
- `cd` — change the working directory with `HOME` fallback.
- `pwd` — print working directory.
- `export` — set environment variables.
- `unset` — remove environment variables.
- `env` — list environment variables.
- `exit` — terminate the shell with optional exit status.

### Execution & I/O
- Execution of external binaries using `fork` + `execve`.
- Full pipeline support (`cmd1 | cmd2 | cmd3 ...`) using sequential process chaining.
- Input and output redirections:
  - Output: `>` (overwrite), `>>` (append)
  - Input: `<`
- Heredoc (`<<`) support with limiter-based input collection.

### Signals & process control
- Proper handling of `SIGINT` (Ctrl+C) and `SIGQUIT` (Ctrl+\) so the shell maintains a stable interactive session while foreground processes receive the signals.
- Children run in appropriate process groups to ensure conventional terminal behavior.

### Interactive experience
- `readline` integration for line editing, search, and persistent history across sessions.
- Clear prompt with contextual information as needed.

### Code quality & project conventions
- Modular architecture with clear separation between parser, executor, builtins, and utilities.
- Adherence to strict coding rules for readability and maintainability:
  - Functions limited in size for easy review.
  - Controlled number of parameters and local variables.
  - Consistent naming and documentation.

---

## Technical stack

- **Language:** C (ISO C99 compatible)
- **Build system:** Makefile
- **Libraries:** GNU Readline (for interactive input)
- **Platform:** Linux (Ubuntu recommended)
- **Toolchain:** `gcc`, `make`

---

## Repository layout

```
.
├── src/                # Source files (parser, executor, builtins, utils, signals)
├── include/            # Public headers
├── tests/              # Test cases and test runner scripts
├── Makefile            # Build & utility targets
└── README.md
```

---

## Prerequisites

Install required packages (on Debian/Ubuntu):

```bash
sudo apt update
sudo apt install -y build-essential libreadline-dev
```

Ensure you have a POSIX-compatible terminal and a modern `gcc`.

---

## Build & run

Clone the repository and build:

```bash
git clone <REPOSITORY_URL>
cd minishell
make
```

Available `Makefile` targets:

- `make` or `make all` — build the `minishell` executable.
- `make clean` — remove compiled object files.
- `make fclean` — remove objects and the binary.
- `make re` — rebuild from scratch.
- `make test` — run included test scenarios (if available).

Run the shell:

```bash
./minishell
```

---

## Usage examples

### Basic commands
```bash
$ ls -la
$ echo "Hello World"
```

### Redirections
```bash
$ echo "hello" > out.txt
$ cat < out.txt
$ echo "append" >> out.txt
```

### Pipelines
```bash
$ ps aux | grep minishell | wc -l
```

### Heredoc
```bash
$ cat << EOF
> line 1
> line 2
> EOF
```

### Environment variables
```bash
$ export USERNAME="javi"
$ echo "$USERNAME"
$ echo $?
```

---
