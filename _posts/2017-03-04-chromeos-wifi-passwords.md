---
layout: post
title:  "Retrieving Saved Wifi Passwords on ChromeOS"
date:   2017-03-04
categories: blog
---

I was trying to retrieve the stored passwords from my chromebook. I came across [this blogpost](http://www.guidingtech.com/54928/view-saved-wifi-passwords-chromebook/) but their instructions had a few unnecessary steps.

Here's the ugly one-line version:

```bash
echo '(grep "Name=" /home/root/*/shill/shill.profile | cut -c 6- |'\
'sed "s/\(^.*$\)/id:   \1/" | nl && grep Passphrase /home/root/*/shill/shill.profile|'\
'tr "!-~" "P-~!-O" | cut -c 18-| sed "s/\(^.*$\)/pass: \1/" | nl ) | sort -n |'\
'sed "s/\(.*pass:.*\)/\1\n/"' | sudo sh
```

Just paste it into crosh shell. It should produce output like this:

```

     1  id:   home
     1  pass: mypassw0rd

     2  id:   my_network
     2  pass: xtrasecure!

     3  id:   coffee_shop_wifi
     3  pass: cleverPassw0rd
```