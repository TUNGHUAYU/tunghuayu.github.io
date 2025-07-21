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

```bash

# add new draft
$ bundle exec jekyll draft "<page-title>"

# publish draft to post
$ bundle exec jekyll publish _draft/<page-title>

# add new post
$ bundle exec jekyll post "<page-title>"

```
