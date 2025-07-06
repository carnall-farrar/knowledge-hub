# Introduction to Unix

Unix is a powerful, multiuser, multitasking operating system originally developed in the 1960s and 70s at Bell Labs by Ken Thompson, Dennis Ritchie, and others. It's known for its simplicity, modular design, and influence on almost all modern operating systems.

It is the foundation for many of the systems we use today. It's like the blueprint or "grandparent" of operating systems such as:
- Linux
- macOS
- Android (via Linux)

Even Windows includes Unix-inspired tools via WSL (Windows Subsystem for Linux) or Git Bash.

## Key Features
- Command-line based: Although some versions have GUIs, Unix is built for command-line control.
- Multitasking: Can run multiple programs at once.
- Multiuser: Many users can use the system at the same time (especially on servers).
- File system hierarchy: Everything is a file—including hardware and processes.
- Portability: Originally written in C, Unix code could be compiled on different machines.

## Why it matters
Git, Bash, SSH, Python, Docker, and many programming tools are built for or inspired by Unix environments. If you're working on servers, deploying web apps, or collaborating in open-source, you're almost certainly dealing with a Unix-like system. Understanding Unix fundamentals helps you work more effectively with the terminal and shell scripting.

## Basic commands

#### File System Navigation & Administration

| Command | Description                                           | Example                   |
|---------|-------------------------------------------------------|---------------------------|
| cd      | Changes the current working directory.                | cd Documents              |
| ls      | Lists files and directories in the current directory. | ls                        |
| pwd     | Prints the current working directory.                 | pwd                       |
| mkdir   | Creates a new directory.                              | mkdir new_folder          |
| rmdir   | Removes an empty directory.                           | rmdir empty_folder        |
| mv      | Moves files or directories.                           | mv file1.txt Documents/   |
| df      | Displays disk space usage.                            | df -h                     |
| du      | Displays disk usage of files and directories.         | du -sh /path/to/directory |
| grep	  | Searches for patterns in text files.                  | grep "error" logfile.txt  |

## File Manipulation

| Command | Description                                                         | Example                    |
|---------|---------------------------------------------------------------------|----------------------------|
| touch   | Creates an empty file or updates the access and modification times. | touch new_file.txt         |
| cp      | Copies files or directories.                                        | cp file1.txt file2.txt     |
| mv      | Moves files or directories.                                         | mv file1.txt Documents     |
| rm      | Remove files or directories.                                        | rm old_file.txt            |
| chmod   | Changes the permissions of a file or directory.                     | chmod 644 file.txt         |
| chown   | Changes the owner and group of a file or directory.                 | chown user:group file.txt  |
| ln      | Creates links between files.                                        | ln -s target_file symlink  |
| cat     | Concatenates files and displays their contents.                     | cat file1.txt file2.txt    |
| head    | Displays the first few lines of a file.                             | head file.txt              |


## Text Editors in Unix

| Text Editor | Description | Example |
|-------------|-------------|---------|
| Vi / Vim    | Vi (Vim) is a highly configurable, powerful, and feature-rich text editor based on the original Vi editor. Vim offers modes for both command-line operations and text editing. | Open a file with Vim: vim filename. Exit Vim editor: Press Esc, then type :wq and press Enter                               |
| Emacs       | Emacs is a versatile text editor with extensive customization capabilities and support for various programming languages.                                                      | Open a file with Emacs: emacs filename. Save and exit Emacs: Press Ctrl + X, then Ctrl + S and Ctrl + X, then Ctrl + C to exit  |
| Nano        | Nano is a simple and user-friendly text editor designed for ease of use and accessibility.                                                                                     | Open a file with Nano: nano. Save and exit Nano: Press Ctrl + O, then Ctrl + X                                       |
| Ed          | Ed is a standard Unix text editor that operates in line-oriented mode, making it suitable for batch processing and automation tasks.                                           | Open a file with Ed: ed filename. Exit Ed editor: Type q and press Enter                                                  |
| Jed         | Jed is a lightweight yet powerful text editor that provides an intuitive interface and support for various programming languages.                                              | Open a file with Jed: jed filename                                                      |


## References
- [geeksforgeeks](https://www.geeksforgeeks.org/linux-unix/essential-linuxunix-commands/)