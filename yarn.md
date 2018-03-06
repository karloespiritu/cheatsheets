---
layout: page
title: Yarn
permalink: /yarn/
---

## Quick Install

```bash
# If you use nvm or similar, you should exclude installing Node.js
# so that nvm’s version of Node.js is used.
$ brew install yarn --without-node

# Upgrade yarn
$ brew upgrade yarn
```

## CLI Commands

```bash
# Add package to 'dependencies'
$ yarn add <package>

# Add package to 'devDependencies'
$ yarn add -D <package>

# Add packages as exact versions
$ yarn add -E <package>

# Install packages globally on your operating system
$ yarn global add <package>

# Removes the package from all types of dependencies
$ yarn remove <package>

# List installed packages
$ yarn list

# List top-level installed packages
$ yarn list --depth=0

# List installed top-level global packages
$ yarn global list --depth=0

# List packages with filter string and depth level
$ yarn list --pattern "gulp|grunt" --depth=1

# Cleans and removes unnecessary files from package dependencies.
$ yarn autoclean

# Checks for outdated package dependencies
$ yarn outdated

# Show information about why a package is installed.
$ yarn why <query>
$ yarn why jest

# Running this command will clear the global cache. It will be
# populated again the next time yarn or yarn install is run.
# Additionally, you can specify one or more packages that you
# want to clean.
$ yarn cache clean

```
