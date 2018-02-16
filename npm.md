---
layout: page
title: NPM
permalink: /npm/
---

## Top NPM commands

* `npm init` - displays a simple wizard to help you create and define your new project
* `npm install module_name`: install a module;
* `npm install -g module_name`: install a global module;
* `npm install module_name --save`: install a module and add it into the `package.json` file, inside dependencies;
* `npm install module_name --save-dev` - install a module and add it into the `package.json` file, inside devDependencies;
* `npm list` - lists all the modules installed on the project;
* `npm list -g` - lists all the installed global modules
* `npm remove module_name` - uninstall a module from the project;
* `npm remove -g module_name` - uninstall a global module;
* `npm remove module_name --save` - uninstall a module from the project and also remove it from the attribute dependencies
* `npm remove module_name --save-dev` - uninstall a module from the project and also remove it from the attribute devDependencies;
* `npm update module_name` - updates the module version
* `npm update -g module_name` - updates the a global module version
* `npm -v` - displays the npm current version;
* `npm adduser username` - creates an account to npmjs.org2;
* `npm whoami` - displays details of your public npm’s profile (you must create an account using the previous command;
* `npm publish` - publishes a module into npmjs.org (it’s necessary to have an active account first);
