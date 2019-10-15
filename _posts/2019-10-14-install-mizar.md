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
CONFIG=~/.zshrc
echo 'export MIZFILES=/usr/local/share/mizar' >> $CONFIG
source $CONFIG
echo $MIZFILES
```

After setup is complete you can verify your installation by checking the smallest legal proof
```
mkdir dict text
touch dict/my_mizar.voc
echo "environ\nbegin\n" > text/my_mizar.miz 
mizf text/my_mizar.miz 
```

If all goes well output should look like this 
```
Make Environment, Mizar Ver. 8.1.09 (Linux/FPC)
Copyright (c) 1990-2019 Association of Mizar Users

-Vocabularies  [   1]
-Constructors  [   1]
-Requirements  [   1]
-Registrations [   1]
-Notations     [   1]

Verifier based on More Strict Mizar Processor, Mizar Ver. 8.1.09 (Linux/FPC)
Copyright (c) 1990-2019 Association of Mizar Users
Processing: text/my_mizar.miz

Parser   [   3]   0:00
MSM      [   2]   0:00
Analyzer   0:00
Checker  [   1]
Time of mizaring: 0:00
```
