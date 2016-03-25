---
layout: page
title: Ruby on Rails
permalink: /rails/
---

## Directory structure

```bash
|-- app
|   |-- assets
|   |   |-- images
|   |   |-- javascripts
|   |   |   `-- application.js
|   |   `-- stylesheets
|   |       `-- application.css
|   |-- controllers
|   |   |-- application_controller.rb
|   |   `-- concerns
|   |-- helpers
|   |   `-- application_helper.rb
|   |-- mailers
|   |-- models
|   |   `-- concerns
|   `-- views
|       `-- layouts
|           `-- application.html.erb
|-- bin
|   |-- bundle
|   |-- rails
|   |-- rake
|   |-- setup
|   `-- spring
|-- config
|   |-- application.rb
|   |-- boot.rb
|   |-- database.yml
|   |-- environment.rb
|   |-- environments
|   |   |-- development.rb
|   |   |-- production.rb
|   |   `-- test.rb
|   |-- initializers
|   |   |-- assets.rb
|   |   |-- backtrace_silencers.rb
|   |   |-- cookies_serializer.rb
|   |   |-- filter_parameter_logging.rb
|   |   |-- inflections.rb
|   |   |-- mime_types.rb
|   |   |-- session_store.rb
|   |   `-- wrap_parameters.rb
|   |-- locales
|   |   `-- en.yml
|   |-- routes.rb
|   `-- secrets.yml
|-- config.ru
|-- db
|   `-- seeds.rb
|-- Gemfile
|-- Gemfile.lock
|-- lib
|   |-- assets
|   `-- tasks
|-- log
|-- public
|   |-- 404.html
|   |-- 422.html
|   |-- 500.html
|   |-- favicon.ico
|   `-- robots.txt
|-- Rakefile
|-- README.rdoc
|-- test
|   |-- controllers
|   |-- fixtures
|   |-- helpers
|   |-- integration
|   |-- mailers
|   |-- models
|   `-- test_helper.rb
|-- tmp
|   `-- cache
|       `-- assets
`-- vendor
`-- assets
    |-- javascripts
    `-- stylesheets
```

## Basic Commands

Generate a controller

```bash
rails generate controller controller_name action1 action2
```

Generate a mailer. Mailers are similar to controllers and have their own view
files in `app/views/mailer_name/`. More info [here](http://guides.rubyonrails.org/v2.3.8/action_mailer_basics.html)

```bash
rails generate mailer MailerName
```

```bash
rails console
rails server
bin/rails
rails generate
rails dbconsole
rails new app_name
```

## Rake

Rake is Ruby Make, a standalone Ruby utility that replaces the Unix utility 'make', and uses a `Rakefile` and `.rake `files to build up a list of tasks. In Rails, Rake is used for common administration tasks, especially sophisticated ones that build off of each other.

```bash
rake assets:precompile
rake assets:clean

rake db:migrate
rake db:create

rake doc:app
rake doc:guides
rake doc:rails

```
