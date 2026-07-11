# about

> **my universal shell inspector for Bash.**

`about` answers a simple question:

> **"What exactly is this command?"**

Instead of remembering whether to use `which`, `type`, `declare`, `alias`, `file`, `cat`, or `bat`, simply type:

```bash
about <command>
```

---

## Features

* 🔎 Detects executables in `PATH`
* 📄 Displays script source with syntax highlighting (`bat`)
* ⚙️ Detects compiled binaries
* 🧠 Displays shell function definitions
* 📍 Shows the file and line where a shell function was defined (using `extdebug`)
* 🔗 Detects aliases
* 🏗 Detects builtins and shell keywords
* 📂 Pretty-prints files received from standard input
* 🎨 Automatic colored output
* ⌨️ Supports **TAB completion** for commands, functions, aliases and executables



## Examples
Inspect itself (funny)

```bash
about about
```



Inspect an executable:

```bash
about bash
about git
```

Inspect a shell builtin:

```bash
about cd
```


---

## Requirements

* Bash
* `file`
* `bat` *(optional, for syntax highlighting)*
* `ripgrep` (`rg`) *(optional, for locating alias definitions)*

If `bat` is unavailable, `about` automatically falls back to `cat`.

---

## Installation

Copy the `about()` function into your shell initialization file, for example:

```bash
~/.bashrc
```

Add Enable command completion:

```bash
complete -A command about
```

Reload your shell:

```bash
source ~/.bashrc
```



---

## Why?

just to answer one simple question:

> **"What is this thing?"**

`about` is a memorable command and automatically chooses the most appropriate way to inspect its target.

`about` is not intended to replace existing Unix tools, it simply provides a convenient front-end that makes command introspection effortless.

> **`man` tells you how to use a command.**
> **`about` tells you what it actually is.**

---

## License

MIT
