---
layout: page
title: Ghost
permalink: /ghost/
---

## Quick Install

```bash
$ npm install --production
$ npm start
http://127.0.0.1:2368 & http://127.0.0.1:2368/ghost
```

### Theme Structure

```bash
.
├── /assets
    ├── /css
        ├── screen.css
    ├── /fonts
    ├── /images
    ├── /js
├── /partials
    ├── list-post.hbs
├── default.hbs
├── index.hbs [required]
└── post.hbs [required]
└── package.json [required]
```

### Templates


* index.hbs
* home.hbs
* post.hbs
* page.hbs, page-{% raw %}{{slug}}{% endraw %}.hbs
* tag.hbs, tag-{% raw %}{{slug}}{% endraw %}.hbs
* author.hbs, author-{% raw %}{{slug}}{% endraw %}.hbs
* private.hbs
* error.hbs

## Block Helpers

```handlebars
{% raw %}
{{#if}}{{/if}}, {{#foreach posts}}{{/foreach}}
{% endraw %}
```

## Layout Expressions

```handlebars
{% raw %}
{{!< default}} - to declare that it extends the default layout
{{{body}}}
{% endraw %}
```

## Partial Expressions

Partials allow you to create small **reusable** templates which you include in other template files. For example, you might create a `loop.hbs` partial which you use on all of the listing templates to output a short post excerpt. Partials have to live in the `/partials/` directory, and are output with the `{% raw %}{{> loop}}{% endraw %}` partial helper. The partial helper will also take a string path if you have subdirectories inside your partials directory, e.g. {% raw %}{{> 'author/mini-bio'}}{% endraw %}.

```bash
{% raw %}
{{> loop}}
{% endraw %}
```

## Reference

[http://themes.ghost.org/v0.6.3/docs/](http://themes.ghost.org/v0.6.3/docs/)


