--- 
layout: post
title: "Fedora: Accidentally deleted Gnome desktop panels, how to restore?"
wordpress_id: 276
wordpress_url: http://randika.com/?p=276
date: 2010-06-15 09:38:12 +01:00
---
I accidentally deleted the entire panels at the bottom and the top of the my fedora Gnome installation. Start menu, the clock, desktop switchers, workspaces and everything are gone now.

After googling for few minutes I found a fix for this. Here is what I did.
<pre class="console">[randika@localhost ~]$ mkdir bak
[randika@localhost ~]$ mv -rf {.gnome*,.gconf*} bak/
</pre>
As you can see I moved (I really don't recommend deleting configuration files) all the gnome configuration files from my account to another directory named
<pre>/home/randika/bak/</pre>
then I restarted the OS. Done, now I have the default settings back on my screen.
