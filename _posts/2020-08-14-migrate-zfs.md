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

sudo zfs send -Ri sourcepool@moving2 sourcepool@moving3 | mbuffer \
    | sudo zfs receive -F destpool
```

Before changing how things are mounted, you can double check your current mountpoint with.

```
sudo zfs get mountpoint sourcepool 
```

Now, rearrange 
```
zfs set mountpoint=/backup/mountpoint sourcepool
zfs set mountpoint=/original/mountpoint destpool
```


Finally, you can destroy the snapshots you used to migrate

```
sudo zfs destroy destpool@moving1
sudo zfs destroy destpool@moving2
sudo zfs destroy destpool@moving3
```


[serverfault post](https://serverfault.com/questions/88638/moving-a-zfs-filesystem-from-one-pool-to-another)

