# Advanced C Shell 💻🐚

A **feature-rich shell implementation** in C that replicates Unix/Linux shell functionality, demonstrating deep understanding of process management, system calls, and command-line interfaces.

## 🎯 Project Overview
This project implements a fully functional shell with advanced features comparable to bash/zsh. It processes user commands, manages processes, handles I/O redirection, pipes, and background job execution—core concepts in operating systems.

## ✨ Key Features
- 🔧 **Command execution** - Execute built-in and external commands
- 📢 **I/O Redirection** - Input (`<`) and output (`>`, `>>`) redirection
- 🔀 **Piping** - Chain commands with pipes (`|`)
- 🔄 **Background execution** - Run jobs in background (`&`)
- 📋 **Job control** - List, manage, and control background processes
- 🏠 **Built-in commands** - cd, pwd, echo, exit, jobs, fg, bg, etc.
- 🔍 **Command history** - Navigate previous commands
- ⚙️ **Environment variables** - Set, modify, and use environment variables
- 💬 **Prompt customization** - Configurable shell prompt
- 🛡️ **Error handling** - Graceful error management

## 🛠️ Tech Stack
- **C** - Core implementation
- **POSIX APIs** - Process management (fork, exec)
- **Linux/Unix** - Operating system
- **Make** - Build system

## 📦 Installation & Setup

```bash
# Clone the repository
git clone https://github.com/Pavaneswar6699/Advanced-C-Shell.git
cd Advanced-C-Shell

# Compile the shell
make clean
make

# Run the shell
./shell

# Or compile with debug info
make DEBUG=1
```

## 🏗️ Project Structure
```
Advanced-C-Shell/
├── src/
│   ├── shell.c          # Main shell loop and initialization
│   ├── parser.c         # Command parsing logic
│   ├── executor.c       # Command execution
│   ├── builtins.c       # Built-in command implementations
│   ├── redirections.c   # I/O redirection handling
│   ├── pipes.c          # Pipe implementation
│   └── jobs.c           # Background job management
├── include/
│   ├── shell.h
│   ├── parser.h
│   ├���─ executor.h
│   └── utils.h
├── Makefile
└── README.md
```

## 🔧 Built-in Commands

| Command | Description |
|---------|-------------|
| `cd <path>` | Change directory |
| `pwd` | Print working directory |
| `echo <args>` | Display text |
| `exit` | Exit the shell |
| `export VAR=value` | Set environment variable |
| `unset VAR` | Unset variable |
| `jobs` | List background jobs |
| `fg [job_id]` | Bring job to foreground |
| `bg [job_id]` | Resume job in background |
| `help` | Show available commands |

## 📖 Usage Examples

```bash
# Basic command execution
$ ls -la
$ mkdir my_directory

# I/O Redirection
$ echo "Hello" > file.txt
$ cat < input.txt > output.txt
$ echo "Append" >> file.txt

# Piping
$ cat file.txt | grep "pattern" | wc -l
$ ps aux | grep "process_name"

# Background execution
$ long_running_task &
$ jobs
$ fg 1

# Environment variables
$ export MY_VAR="value"
$ echo $MY_VAR

# Multiple commands
$ command1; command2 && command3
```

## 🔍 Core Concepts Implemented

### 1. Process Management
- **fork()** - Create child processes
- **execvp()** - Execute external commands
- **wait()/waitpid()** - Wait for child processes
- **signal handling** - Handle signals (SIGCHLD, SIGINT)

### 2. Command Parsing
- Tokenization and argument parsing
- Special character handling
- Quote and escape sequence processing

### 3. I/O Redirection
- File descriptor manipulation
- Input/output file handling
- Append vs overwrite modes

### 4. Pipe Implementation
- Bidirectional communication between processes
- Multiple pipe chains
- Data flow synchronization

### 5. Job Control
- Background process tracking
- Job state management
- Foreground/background switching

## 🧪 Testing

```bash
# Basic functionality tests
./shell < test_commands.txt

# Interactive testing
./shell
$ pwd
$ ls
$ echo "test"
$ exit
```

## 🚀 Performance Features
- ✅ Efficient memory usage
- ✅ Minimal process overhead
- ✅ Fast command parsing
- ✅ Optimized I/O operations

## 🎓 Learning Outcomes
This project demonstrates expertise in:
- Advanced C programming
- Process control and management
- System call interfaces
- Signal handling
- File descriptor manipulation
- Parser implementation
- Command-line interface design

## 🚀 Future Enhancements
- [ ] Command history with file persistence
- [ ] Tab completion
- [ ] Advanced job scheduling
- [ ] Script execution mode
- [ ] Configuration file support

## 🤝 Contributing
Contributions welcome! Potential areas:
- Additional built-in commands
- Performance optimizations
- Better error messages
- Test suite expansion

## 📄 License
This project is licensed under the MIT License.

## 👨‍💻 Author
**Pavaneswar** - [GitHub Profile](https://github.com/Pavaneswar6699)

---
⭐ Learning shell internals? Please star this project!