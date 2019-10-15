---
layout: post
title:  "Previewing Jekyll on ChromeOS"
date:   2019-08-01
categories: blog
---

It's nice to be able to preview how Jekyll will render my Github Pages site
before merging a new post. There is a minor wrinkle in ChromeOS which means that
the default `jekyll serve` does not work.

At first I tired to install Jekyll deps as per [the
docs](https://jekyllrb.com/docs/installation/ubuntu/)

```
sudo apt-get install ruby-full build-essential zlib1g-dev
```

Then I tried to install as root. The docs advise against this, but I don't want
go to the trouble of setting up a bunch of stuff in my `.zshrc` for ruby which I
don't plan to use except for Jekyll. When I tried to `sudo gem install jekyll
bundler` I got the following error:

```
ERROR:  Error installing jekyll:
        jekyll-sass-converter requires Ruby version >= 2.4.0.
Successfully installed bundler-2.0.2
Parsing documentation for bundler-2.0.2
Done installing documentation for bundler after 28 seconds
1 gem installed
```

Fortunately, I noticed that there's a version of Jekyll available via apt so a
quick `sudo apt install jekyll` is all that's required to install.

To run, use `jekyll serve -P 4200`. It defaults to trying to use port 4000 which
is blocked by the default crostini port forwarding configuration. This [reddit
post](https://www.reddit.com/r/Crostini/comments/99s3t9/wellknown_ports_are_now_autoforwarded_to_the/)
has a more complete list of what ports work.
