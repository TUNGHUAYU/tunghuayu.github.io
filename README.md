# README


## Build up local environment for development.

```bash
# 
$ gem install jekyll bundler

#
$ bundle install

# Build the site and make it available on a local server.
$ bundle exec jekyll serve 
```

## Add new post

[jekyll-compose](https://github.com/jekyll/jekyll-compose)

> install Jekyll::Compose

```bash
# append line into Gemfile
$ echo "gem 'jekyll-compose', group: [:jekyll_plugins]" >> Gemfile

# install
$ bundle

```

> usage

```bash

# show help message 
$ bundle exec jekyll help

# add new draft
$ bundle exec jekyll draft "<page-title>"

# publish draft to post
$ bundle exec jekyll publish _draft/<page-title>

# unpublish post back to draft
$ bundle exec jekyll unpublish 

# add new post
$ bundle exec jekyll post "<page-title>"

```
