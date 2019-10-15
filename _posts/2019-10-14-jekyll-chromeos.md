---
layout: post
title:  "Previewing Jekyll on ChromeOS"
date:   2019-08-01
categories: blog
---

It's nice to be able to preview how Jekyll will render my Github Pages site
before merging a new post. There is a minor wrinkle in ChromeOS which means that
the default `jekyll serve` does not work.

Install Jekyll as per [the docs](https://jekyllrb.com/docs/installation/ubuntu/)

```sh
sudo apt-get install ruby-full build-essential zlib1g-dev

# docs advise against installing as root
sudo gem install jekyll bundler
```

