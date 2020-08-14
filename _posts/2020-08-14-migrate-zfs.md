---
layout: post
title:  "Migrating data to a new ZFS Pool"
date:   2020-08-14
categories: blog, zfs
---


Now, we should stop everything that's currently accessing the old pool 

```
sudo lsof | grep /my/mountpoint
# shutdown stuff and repeat
```

and take one last snapshot.

```
sudo zfs snapshot -r sourcepool@moving3
sudo zfs send -Ri sourcepool@moving2 sourcepool@moving3 | mbuffer | sudo zfs receive -F destpool
```

double check your current mountpoint wiht 

```
sudo zfs get mountpoint sourcepool 
```

finally, destryo
```
sudo zfs destroy datum@moving2
```


https://serverfault.com/questions/88638/moving-a-zfs-filesystem-from-one-pool-to-another

