---
layout: post
title:  "Fixing Corrupt Crosh Window App"
date:   2016-09-27
categories: blog
---

Lately whenever I try to launch crosh it shows 

![broken crosh](/assets/crosh-1.png)


    This site can't be reached

    The webpage at chrome-extension://pnhechapfaindjhompbnflcldabbghjo/html/crosh.html
	might be temporarily down or it may have moved permanently to a new web address.

    ERR_FAILED

Looking at the corresponding entry in the chrome webstore seems to indicate the extension is disabled. Unfortunately however, the "Enable this item" link doesn't work. However, visiting the chrome extensions page (chrome://extensions) quickly reveals the problem.

<center>
<img src="/assets/crosh-2.png" alt="chrome webstore doesnt help" style="width: 600px;"/>
</center>

It's potentially confusing that the "Crosh Window" app appears to be working fine. However a closer insepction reveals that Secure Shell has become corrupted! Fortunately the repair button works just fine to fix this time.

![crosh extensions entry](/assets/crosh-4.png "Text 1")
![secure shell entry](/assets/crosh-3.png "Text 1")

Don't forget to re-add `run@>crosh` to secure shell after repair is complete.

<center>
<img src="/assets/crosh-5.png" alt="secure shell window" style="width: 600px;"/>
</center>