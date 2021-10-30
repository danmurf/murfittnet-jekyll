# murfittnet-jekyll

This repository contains the Jekyll code for my personal website, http://murfitt.net

## Setup

1. Install Ruby. Here are the Mac instruction <https://jekyllrb.com/docs/installation/macos/>
2. If you follow the above instructions, you should have Ruby and the Bundler
2. Run `bundle install`
4. For a local server, run `bundle exec jekyll serve --watch --drafts`

## Create draft post
```
bundle exec jekyll draft "Name of blog post"
```

## Publish a draft
```
bundle exec jekyll publish _drafts/name-of-blog-post.md
```

## Create a published blog post (skip draft)
```
bundle exec jekyll post "Name of blog post"
```
