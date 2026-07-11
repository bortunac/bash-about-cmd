# about

> **A universal shell inspector for Bash.**

`about` is a small Bash utility that answers the question:

> *"What exactly is this command?"*

Instead of remembering whether to use `which`, `type`, `declare`, `alias`, `file`, `cat`, or `bat`, simply use:

```bash
about <command>
```

## Features

* 🔎 Detects executables in `PATH`
* 📄 Displays script source with syntax highlighting (`bat`)
* ⚙️ Detects compiled binaries
* 🧠 Shows shell function definitions
* 📍 Shows the file and line where a function was defined (using `extdebug`)
* 🔗 Resolves aliases
* 📂 Pretty-prints files received from standard input
* 🎨 Colorized output

## Examples

Inspect an executable:

```bash
about php
about grep
about git
```

Inspect a shell function:

```bash
about about
```

Output:

```text
about 6 ~/.xbash.sh

about ()
{
    ...
}
```

Inspect an alias:

```bash
about sql.cluster
```

Output:

```text
alias sql.cluster='cluster_info'
```

Inspect files from a pipeline:

```bash
find . -name "*.sh" | about
```

## Requirements

* Bash
* `bat` (optional, for syntax highlighting)
* `file`
* `ripgrep` (`rg`) (optional, for locating alias definitions)

Without `bat`, `about` automatically falls back to `cat`.

## Installation

Copy the `about()` function into your shell initialization file:

```bash
~/.bashrc
```

or

```bash
~/.xbash.sh
```

Reload your shell:

```bash
source ~/.bashrc
```

Enable command completion:

```bash
complete -A command about
```

## Motivation

I kept switching between commands like:

```bash
which
type
declare -f
declare -F
alias
file
cat
bat
```

just to inspect a command.

`about` unifies those operations behind a single, memorable command.

## Philosophy

The goal is not to replace existing Unix tools, but to provide a convenient front-end that automatically chooses the right one.

Think of it as:

> **`man` tells you how to use a command.**
> **`about` tells you what the command actually is.**

## License

MIT
