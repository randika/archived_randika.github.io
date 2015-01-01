--- 
layout: post
title: How to enable root login under Fedora 10 Gnome GUI login screen
wordpress_id: 6
wordpress_url: http://localhost/randika_wp/?p=6
date: 2009-04-17 13:30:00 +01:00
---
By default on fedora 10 you can't login as the root user from the Gnome login screen(GUI). I'm not exactly sure why it is disabled. anyway there we can enable it by doing some modification to  /etc/pam.d/gdm

to do so, just login as a normal user and type this command to become root user:
<pre class="console">
# su -
</pre>
provide the password for the root account and open the above mentioned file from your favourite editor:
<pre class="console">
# gedit /etc/pam.d/gdm
</pre>
or
<pre class="console">
# vi /etc/pam.d/gdm
</pre>
find this line and uncomment it.
<pre class="console">
auth required pam_succeed_if.so user != root quiet
</pre>
Save and close the file. Logout from the system. Now you should be able to login as root user from the login screen.
