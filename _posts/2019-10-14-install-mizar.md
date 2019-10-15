---
layout: post
title:  "Installing Mizar"
date:   2019-10-14
categories: blog
---

Mizar is a system for formalizing mathematical proofs.

It can be downloaded [here](http://mizar.org/system/index.html#download). The
server with the binaries wasn't up one of the times I tried to download it.

Nevertheless, I did eventually manage to get a copy with

```sh
FILE=mizar-8.1.09_5.57.1355-i386-linux.tar
wget -c http://mizar.uwb.edu.pl/~softadm/current/${FILE}
```

(it stalled a few times, thus the `-c`)

Extract and install with
```sh
tar xvf $FILE
sudo ./install.sh --default
```

Finally, verify that `$PATH` contains the install path and setup a `MIZFILES` var
```sh
echo $PATH | grep usr/local/bin
CONFIG="~/.zshrc"
echo 'export MIZFILES=/usr/local/share/mizar' >> $CONFIG
source $CONFIG
echo $MIZFILES
```
