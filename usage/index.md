---
title: Usage
layout: default
---

# Usage

Create a file called `Cask` in your project root and specify
dependencies:

```
$ cask init [--dev]
```

_(Use `--dev` if the project is for package development)_

If you are using Cask for your Emacs configuration, add this to your
`.emacs` file:

```
(require 'cask "~/.cask/cask.el")
(cask-initialize)
```

To install all dependencies, run:

```
$ cask [install]
```

This will create a directory called `.cask`, containing all dependencies.

The commands below execute using the `emacs` binary. To specify a
custom Emacs, use the `EMACS` environment variable, for example:

```
$ EMACS="$(evm bin emacs-24.1)" cask command
```

## Commands & Options

Below all Cask commands and options are described.

* [exec](#exec)
* [help, --help, -h](#help)
* [info](#info)
* [init](#init)
* [install](#install)
* [list](#list)
* [load-path](#load-path)
* [outdated](#outdated)
* [package](#package)
* [package-directory](#package-directory)
* [path](#path)
* [update](#update)
* [upgrade](#upgrade)
* [version](#version)
* [--version](#option-version)
* [--dev](#option-dev)
* [--debug](#option-debug)
* [--path](#option-path)

### <a id="exec"></a>exec

Execute command with correct `PATH` (see [path](#path)) and
`EMACSLOADPATH` (see [load-path](#load-path)) set up.

```
$ cask exec echo foo
$ cask exec ecukes --script --reporter gangsta
$ cask exec ert-runner --pattern performance
```

### <a id="help"></a>help

Show Cask usage information.

```
$ cask help
$ cask -h
$ cask --help
```

### <a id="info"></a>info

Show info about this project, such as name, description and version.

```
$ cask info
```

### <a id="init"></a>init

Create new `Cask`-file. If the project is for package development, use
the `--dev` option.

```
$ cask init       # For Emacs configuration
$ cask init --dev # For package development
```

### <a id="install"></a>install

This is the default command, which installs all runtime and
development dependencies specified in the `Cask`-file.

```
$ cask
$ cask install
```

### <a id="list"></a>list

List all runtime and development dependencies.

```
$ cask list
```

### <a id="load-path"></a>load-path

Print `EMACSLOADPATH`-friendly string with path to all dependencies to
this project.

The [exec](#exec) command includes the output of this command
automatically. This means that if the command executed is an Emacs
process, there's no hassle with the `load-path`, just require the
dependencies.

```
$ cask load-path
```

### <a id="outdated"></a>outdated

Show list of all outdated dependencies. That is dependencies that have
a more recent version available.

```
$ cask outdated
```

### <a id="package"></a>package

Create a `-pkg.el` file (see
<http://www.gnu.org/software/emacs/manual/html_node/elisp/Multi_002dfile-Packages.html#Multi_002dfile-Packages>).

```
$ cask package
```

### <a id="package-directory"></a>package-directory

Print path to package directory, that is the path to the directory
where all dependencies are installed (`.cask/EMACS-VERSION/elpa`).

```
$ cask package-directory
```

### <a id="path"></a>path

Print `PATH` and prepend path to all directories called `bin` in this
projects dependencies.

For example if this project depends on `ecukes`, this command will
include `.cask/EMACS-VERSION/elpa/ecukes-VERSION/bin`.

```
$ cask path
```

### <a id="update"></a>update

Update all project dependencies.

```
$ cask update
```

### <a id="upgrade"></a>upgrade

Upgrade Cask and all its dependencies.

```
$ cask upgrade
```

### <a id="version"></a>version

Print version of this package.

```
$ cask version
```

---

### <a id="option-version"></a>--version

Print Cask's version.

```
$ cask --version
```

### <a id="option-dev"></a>--dev

Perform action in development mode. This option does only take affect
for some commands. See resp. command for that information.

```
$ cask --dev
```

### <a id="option-debug"></a>--debug

Enable debug information.

```
$ cask --debug
```

### <a id="option-path"></a>--path

Change default directory to path before executing command.

```
$ cask --path /path/to
```
