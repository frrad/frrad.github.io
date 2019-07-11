---
layout: post
title:  "Python SQLite3 Versions"
date:   2019-07-09
categories: blog
tags: technology, python, databases, sqlite3
---

The version of sqlite you get when you do `import sqlite3` in python is is
determined by the version of `libsqlite3` installed on your system, not the
version of the binary.

To check what version of sqlite you are using you can check the `sqlite_version`
string like this

```bash
user@penguin$ python3
Python 3.5.3 (default, Sep 27 2018, 17:25:39) 
[GCC 6.3.0 20170516] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import sqlite3
>>> sqlite3.sqlite_version
'3.16.2'
>>> 
```

To upgrade to a more recent version in Debian Stretch it may be necessary to get
the package from backports.

```shell
echo "deb http://deb.debian.org/debian stretch-backports main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get -t stretch-backports install "libsqlite3-dev"
```
