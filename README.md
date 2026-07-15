# about

> **A universal shell inspector for Bash.**

`about` answers one practical question:

> **What exactly is this command?**

Instead of remembering whether to use `type`, `declare`, `alias`, `file`, `cat`, `bat`, or `which`, you can run:

```bash
about <command>
```

It inspects Bash functions, aliases, builtins, keywords, executables in `PATH`, and files coming from standard input.

---

## What it can inspect

- Executables found in `PATH`
- Shell scripts and other readable text files
- Compiled binaries
- Bash function definitions
- Aliases
- Builtins and shell keywords
- File paths received from standard input

---

## Features

- 🔎 Detects executables in `PATH`
- 📄 Displays script source with syntax highlighting via `bat` when available
- ⚙️ Detects compiled binaries and prints file information instead of dumping binary output
- 🧠 Displays shell function definitions using `declare -f`
- 📍 Shows function definition metadata through Bash `extdebug`
- 🔗 Detects aliases and tries to locate their definitions in common shell startup files
- 🏗 Detects builtins and shell keywords via `type`
- 📂 Pretty-prints files received from standard input
- 🎨 Uses colored output when supported
- ⌨️ Supports TAB completion for commands

---

## Examples

Inspect itself:

```bash
about about
```

Inspect common executables:

```bash
about bash
about git
about rg
```

Inspect a shell builtin:

```bash
about cd
```

Inspect an alias or function:

```bash
about ll
about my_function
```

Inspect files from standard input:

```bash
find . -maxdepth 1 -type f | about
```

---

## How it works

When you run `about <name>`, the function tries, in order:

1. Resolve `<name>` as an executable in `PATH`
2. If it is a binary, show file metadata
3. If it is a text script, print its contents
4. If it is a Bash function, print the function definition
5. If it is an alias, print the alias and search common shell rc files for where it was defined
6. Otherwise, fall back to `type`

When `about` receives input through a pipe, it treats each line as a file path and prints file contents for readable non-binary files.

---

## Requirements

### Required

- Bash
- `file`

### Optional

- `bat` for syntax highlighting
- `ripgrep` (`rg`) for locating alias definitions in shell startup files

If `bat` is not installed, `about` falls back to `cat`.

---

## Installation

Copy the `about` file contents into your shell initialization file, for example:

```bash
~/.bashrc
```

Or source the file directly from your shell rc:

```bash
source /path/to/about
```

Enable completion:

```bash
complete -A command about
```

Reload your shell:

```bash
source ~/.bashrc
```

---

## Notes and limitations

- This tool is written for **Bash**, not for generic POSIX `sh`
- Alias location lookup depends on the configured `ABOUT_SHELL_FILES` paths
- Some systems may not have `bat`; in that case plain output is used
- Output formatting depends on local tools such as `file`, `type`, and `bat`

---

## Why `about about` works

`about` is itself a Bash function. When it cannot resolve `about` to a standalone executable in `PATH`, it falls back to checking whether `about` is a shell function and then prints the function definition.
