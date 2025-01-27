---
abbreviations:
  GUI: Graphical User Interface
  CLI: Command Line Interface
  URL: Unified Resource Locator
---

# Intro to Linux

:::{figure} ../../images/tux.webp
:label: tux
:align: center

Meet Tux, the official mascot of Linux.
:::

Linux is an open-source operating system built on top of the Linux kernel. It was initially developed by Linus Torvalds in 1991 and has now grown to involve a few hundred contributors from the open-source community. 

In genomics, Linux has been the prefered platform by scientists to run and orchestrate sophisticated pipelines due to its low memory footprint, stability, and maturity.

## Command Line Interface

The command line, sometimes called the terminal, is a text-based user interface for interacting with the Linux kernel. Upon opening a new shell session, the user is greeted with a command prompt that looks like:

```bash
$
```

The dollar symbol (`$`) is what we call the command prompt. It is an indication that the current shell is ready to accept commands from the user. A linux command has the following form:

```bash
$ <command> <argument> <value>
```

The `<command>` is the name of the executable (or program) to be invoked by the user. Parameters that modify the behavior of the program are usually passed after the command name in the form of arguments (`<argument>`). Arguments (or flags) are preceeded by two dashes (`--`) by convention, followed by the name of the argument. 

As an example, linux systems offer the `mkdir` command for creating new directories. It can be invoked as follows:

```bash
$ mkdir -p data/reads
```

`mkdir` is the command name. It is followed by the `-p` argument which is a **boolean argument**, meaning that it sets a particular value to one of its two states. In this case, `-p` tells the program to automatically create the `data` (parent) directory to store the `reads` (child) folder. 

`data/reads` is an example of a **positional argument** which the program expects from the user. Multiple positional arguments should be passed in the right order to ensure that the program behaves as expected.

## File Navigation


In most modern computers, a GUI is provided to allow users to navigate between files and directories. However, the shell only supports text input, hence commands are used for moving between directories.

A **file path** is a string that represents the location of a particular file or directory within your system. On a high level, the directory structure for _most_ linux systems follows @file-tree.

:::{figure} ../../images/linux-file-tree.png
:label: file-tree
:align: center

The Linux file tree.
:::

The **root path** is the top-most directory that store all other files within your system. It is usually denoted with a forward slash (`/`) and its serves as the starting point for **absolute paths**. As an example, we could write the absolute path to mary's data directory as `/home/mary/data`.

In contrast, **relative paths** are, as the name suggests, _relative_ to your current directory. This provides a way to anchor the location of a file based on where another file is stored. The path to the `lib` directory relative to robert's home directory is `../local/lib` where `..` is the parent directory of robert.

Some paths are accessed more often than others. Examples include the root and home directories. For convenience, special symbols are used to denote these file locations as tabulated in @path-symbols.

:::{table} Path aliases.
:label: path-symbols
:align: center

| Symbol | Path Description |
| --- | ---------- |
| `.` | the current directory |
| `..` | the parent of your current directory |
| `/` | the root directory |
| `~` | the home directory |
| `-` | the previously navigated directory |

:::

## A Survey of Linux Commands

:::{table} Command Cheatsheet.
:label: commands
:align: center

| Command | Description |
| ----- | ---------- |
| `pwd` | print your current working directory |
| `ls` | list all files and directory in your current path |
| `cd` | change to another directory |
| `mkdir` | make a new directory |
| `cp` | copy a file or the contents of a directory | 
| `rm` | remove a file or a directory |
| `mv` | move a file or a directory to a new location |
| `cat` | concatenate the contents of one or more files |
| `less` | load the contents of a text file to a new, interactive buffer |
| `curl` | a tool for downloading data associated with a URL |
| `man` | access the manual of a program |
| `grep` | a tool for searching text in a file that follows a specified pattern |
 
:::
