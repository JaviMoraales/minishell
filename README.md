# minishell

![Static Badge](https://img.shields.io/badge/Project-42-blue) ![Static
Badge](https://img.shields.io/badge/Language-C-blue) ![Static
Badge](https://img.shields.io/badge/Status-Final-green)

**Developed by:** `asandova-ui` and `jamorale`

## 🐚 Overview

`minishell` is a minimal Unix shell built in C as part of the 42
curriculum.\
It reproduces core shell behavior including parsing, pipes,
redirections, environment variables, heredocs, built-ins, and signal
handling, while following strict coding norms.

## 🎯 Objectives

-   Parse commands, quotes, and variables
-   Handle pipes, redirections, and heredoc
-   Implement built-ins: echo, cd, pwd, export, unset, env, exit
-   Integrate readline with history
-   Handle signals (SIGINT, SIGQUIT)
-   Maintain strict coding standards

## ⚙️ Features

### Parsing & Expansion

-   Tokenization with quotes
-   `$VAR` and `$?` expansion
-   Robust handling of unclosed quotes

### Built-ins

-   echo (with -n and \$?)
-   cd, pwd, export, unset, env, exit

### Execution

-   Pipes: cmd1 \| cmd2 \| cmd3
-   Redirections: \> \>\> \<
-   Heredoc: \<\< limiter
-   Fork/exec external commands

### Signals

-   Shell resists Ctrl+C
-   Proper child process behavior
-   Heredoc interrupt

### User Experience

-   Arrow-key history
-   Bash-like behavior

## 🚀 Compilation

    make
    ./minishell

## 📁 Repository Structure

    src/
    include/
    Makefile
    README.md

## 🧪 Tests

Manual tests for pipes, redirections, env expansion, and heredoc.

## 👥 Authors

-   asandova-ui
-   jamorale
