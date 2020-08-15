---
layout: post
title:  "Migrating data to a new ZFS Pool"
date:   2020-08-14
categories: blog, zfs
---

I recently had to migrate my data to a new ZFS pool. There was lots of great
info in this [serverfault
post](https://serverfault.com/questions/88638/moving-a-zfs-filesystem-from-one-pool-to-another). I'm
writing this to bring it all together in one place for the next time I need to
remember how to do this.

First, create a snapshot on the source pool, and send it to the new pool. You
can leave your source pool online while the snapshot is being sent.

```
sudo zfs snapshot -r sourcepool@moving1

# Maybe do this next bit a screen. It can take a while.
sudo zfs send -R sourcepool@moving1 | mbuffer \
    | sudo zfs receive -F destpool
```

Since that step probably took a while, there are probably difference between the
snapshot and what's on your new pool. Take a new snapshot and send it. You can
do an incremental send which should be much faster than the first send.

```
sudo zfs snapshot -r sourcepool@moving2

sudo zfs send -Ri sourcepool@moving1 sourcepool@moving2 | mbuffer \
    | sudo zfs receive -F destpool
```

Now, we'll have some downtime. Stop everything that's currently accessing the
old pool. You can check what's using your pool with:

```
sudo lsof | grep /my/mountpoint
```


Now that nothing is using the original pool we no longer have a moving target to
copy over. Do one last snapshot and send.

```
sudo zfs snapshot -r sourcepool@moving3

sudo zfs send -Ri sourcepool@moving2 sourcepool@moving3 | mbuffer \
    | sudo zfs receive -F destpool
```

At this point, both pools should have exactly the same data. All that's left is
to mount the new pool where the old one was.

Before changing how things are mounted, you can double check your current
mountpoint with.

```
sudo zfs get mountpoint sourcepool 
```

Now, rearrange 
```
zfs set mountpoint=/backup/mountpoint sourcepool
zfs set mountpoint=/original/mountpoint destpool
```

After you're satisfied that everything worked, you can destroy the snapshots you used to migrate.

```
sudo zfs destroy destpool@moving1
sudo zfs destroy destpool@moving2
sudo zfs destroy destpool@moving3
```

Optionally, destroy the old pool.

```
sudo zfs destroy sourcepool
```
