# Welcome to _jotr_

[![Build Status](https://travis-ci.org/hakash/jotr.svg?branch=master)](https://travis-ci.org/hakash/jotr)

**[LIBRARY](./LIBRARY.MD)**

_Jot down your ideas, thoughts and notes, whitout leaving the terminal._

>### **TLDR:**
>
>**Install:**
>```sh
>npm i jotr -g
>```
>
>**Usage:**
>
> To get started, simply write `jotr` in your terminal to start the editor. Use `Ctrl+D` to save and exit, `Ctrl+C` to exit without saving.
>
>See your jot using `jotr -l`

## Requirements

Currently only *nix systems are supported, so if you're on Windows, you need to use WSL (Windows subsystem for Linux), Vagrant, a Linux-based container or a Linux emulator to be able to use the tool.

_**Contributors are welcome to assist in making this universally available.**_

## Adding jots

jotr supports adding jots both from the cli and using a simple built-in editor.

### One-liners

Use the following format for one-liners, similar to **_'git commit -m "Some commit message"'_**:

```sh
jotr [tags] -c <your jot>
```

Example:

```sh
jotr javascript -c 'let' is scoped to a block
```

Note that you can have multiple tags. The jot is stored with all tags. Example:

```sh
jotr javascript scope assignment -c 'let' is scoped to a block
```

### Multi-line

For multi-line jots, you need to use the editor:

```sh
jotr javascript scope assignment
```

This clears the terminal window, presenting you with an empty space to write your heart out. Use `Ctrl+D` to save your jot. To cancel, just use `Ctrl+C`.

## Listing and searching through the jots

You can list all jots using the `-l` or `--list` flags. If you supply tags as well, you will get a filtered result, displaying only the jots with those tags.

```sh
jotr -l
```

With flags:

```sh
jotr -l c++ pointers
```

If you are looking for a specific term, rather than a tag, you can use the `-g` or `--grep` flags with the term as an argument.

```sh
jotr -g scope
```

## Editing and purging the raw data

Although jots are made to be remembered, sometimes you need to edit or remove one or more jots. To save you from having to search for the raw storage file, you can access it within the built-in editor using the `--edit` flag:

```sh
jotr --edit
```

> **_Beware!_** This opens the entire YAML-file for editing, so be careful not to create syntax errors in the YAML-format. This will render the file unreadable by jotr until the error is fixed.
>
>Use `jotr -l --debug` to assist you in pinpointing the error, or load the data file into an editor like VS Code (or online service) to use YAML-linting.

To completely empty the data file, you can use the purge function.

```sh
jotr --purge
```

>**_Beware!_** Unless you have a backup of the data, the data is irrevocably lost.

## Exporting your data

Tired of jotr? We're sorry to hear that. Here's how you export your data:

```sh
jotr --export some_filename.json
```

Exchange the `.json` extension with `.yml` to get YAML-formatted data instead of un-prettified JSON.

## Some technicalities

jotr saves all jots in a YAML-file located in a sub-folder in the user's home folder. To go there, simply do:

```sh
cd ~/.jotr
```

Here you will find `jots.yml`. If you remove it, it will be re-created without the old data as the tool will try to create both the file and the directory on each run, if they do not exist.

## Roadmap - in no particular order

- Add support for Windows
- Add support for syncing with an online service
- Add support for configuring the default behaviour
- Add terminal coloring
- Replace or improve the built-in editor to be more intuitive

## API, using the core in you own project

If you are curious about the API of the core parts of jotr, take a look [here](LIBRARY.MD)