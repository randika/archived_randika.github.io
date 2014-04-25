--- 
layout: post
title: How to Change Default User Home Directory on Linux
wordpress_id: 5
wordpress_url: http://localhost/randika_wp/?p=5
date: 2009-04-17 09:46:00 +01:00
---
By default user is added to /home directory. I just came up with a requirement of changing this to somewhere else. So here is the solution if you looking for the same.

Default values for account creation defined in /etc/default/useradd file under Linux distros.
Let's open it up using a text editor. I'm using vi editor as always.
<pre class="console">
# vi /etc/default/useradd
</pre>
here is what i can see in my fedora box:
<pre class="console">
# useradd defaults file
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=/bin/bash
SKEL=/etc/skel
CREATE_MAIL_SPOOL=yes
</pre>
as you can see the default home directory defined by HOME variable.  just replace it with your new path.
<pre class="console">
HOME=/allusers/developers
</pre>
