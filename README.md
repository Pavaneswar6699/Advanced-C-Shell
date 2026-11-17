# Advanced C Shell

A Unix shell written from scratch in C on top of POSIX system calls (`fork`, `execvp`, `waitpid`, `pipe`, `dup2`, `sigaction`). It runs system commands and a set of custom built-ins, and handles pipes, redirection, background jobs and job control.

Linux only: several commands read from `/proc`.

## Build and run

```bash
make        # compiles every .c file into ./a.out
./a.out
```

The directory you start the shell from is treated as home (`~`), and `.myshrc` is read from there.

## What it supports

**Running commands**
- Any system command, run in the foreground or in the background with `&`
- Several commands on one line separated by `;`
- Pipes of any length (`cat file | grep x | wc -l`)
- Input and output redirection: `<`, `>`, `>>`, also combined with pipes
- A message when a background process finishes, showing whether it exited normally
- A prompt of the form `<user@host:path>`, with paths under home shown relative to `~`

**Built-in commands**

| Command | What it does |
|---|---|
| `hop <path>` | Change directory. Supports `~`, `-`, `.` and `..` |
| `reveal [-a] [-l] <path>` | List a directory, colour-coded (directories blue, executables green) |
| `seek [-d] [-f] [-e] <name> [dir]` | Recursively search for files or directories by name. `-e` opens the file or enters the directory when there is exactly one match |
| `log` / `log purge` / `log execute <n>` | Show command history saved across sessions, clear it, or re-run an earlier command |
| `proclore [pid]` | Show a process's PID, state, process group, virtual memory and executable path, read from `/proc` |
| `activities` | List processes started by this shell with their PID and state |
| `ping <pid> <signal>` | Send a signal to a process |
| `fg <pid>` / `bg <pid>` | Bring a job to the foreground, or resume a stopped job in the background |
| `neonate -n <secs>` | Print the most recently created PID every `<secs>` seconds until you press `x` (switches the terminal to raw mode) |
| `iMan <command>` | Fetch a man page from `man.he.net` over a raw TCP socket using a hand-written HTTP GET request |

**Signals**
- `Ctrl-C` sends SIGINT to the foreground process, not to the shell
- `Ctrl-Z` stops the foreground process and moves it to the background
- `Ctrl-D` kills all child processes and exits the shell

**Config file**
- Aliases and simple shell functions are loaded from `.myshrc` at startup.

## Code layout

| File | Responsibility |
|---|---|
| `main.c` | Startup and the read–execute loop |
| `command.c` | Parsing (`;`, `&`, `|`, redirection), dispatch to built-ins, `fork`/`exec` |
| `signal.c` | `sigaction` handlers for SIGCHLD, SIGINT, SIGTSTP and SIGQUIT |
| `linkedlist.c` | List of child processes used by `activities`, `fg` and `bg` |
| `display.c` | Prompt |
| `hop.c`, `reveal.c`, `seek.c`, `log.c`, `proclore.c`, `neonate.c`, `iman.c` | One built-in each |
| `custom.c` | `.myshrc` aliases and functions |
| `color.c` | Terminal colour helpers |
