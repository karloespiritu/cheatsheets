---
layout: page
title: rbenv
permalink: /rbenv/
---

`rbenv` - Groom your app’s Ruby environment

## rbenv commands

```bash
# Install rbenv
$ brew install rbenv

# Completely uninstall rbenv
$ brew uninstall rbenv

# list all available versions
$ rbenv install -l

# install a specific Ruby version
$ rbenv install 2.3.0

# Sets a local application-specific Ruby version
# by writing the version name to a `.ruby-version`
$ rbenv local 2.2.2

# Sets the global version of Ruby to be used in all shells
# by writing the version name to the `~/.rbenv/version` file
$ rbenv global 2.2.1

# Sets a shell-specific Ruby version by setting the
# RBENV_VERSION environment variable in your shell.
$ rbenv shell 2.2.1

# Lists all Ruby versions known to rbenv
$ rbenv versions

# Displays the currently active Ruby versions
$ rbenv version

# Run this command after you install a new version of Ruby,
# or install a gem that provides commands.
$ rbenv rehash

# Displays the full path to the executable that rbenv will
# invoke when you run the given command
$ rbenv which irb
```