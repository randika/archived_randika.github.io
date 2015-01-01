--- 
layout: post
title: How to fix the error You don't have permission to access /phpMyAdmin on this server
wordpress_id: 11
wordpress_url: http://localhost/randika_wp/?p=11
date: 2009-05-17 11:34:00 +01:00
---
After installing phpMyAdmin on fedora (FC10) with yum you may notice this error when trying to access it via a remote node.

Forbidden
You don't have permission to access /phpMyAdmin on this server.

This may trigger due to the restrictions which assigned with the default config file. Open it with your favorite editor from the path below.
<pre class="console">[root@megantereon /]# vi /etc/httpd/conf.d/phpMyAdmin.conf</pre>
by default you can only access phpMyAdmin only over localhost. The rule is here.
<pre class="console">Alias /phpMyAdmin /usr/share/phpMyAdmin
order deny,allow
deny from all allow from 127.0.0.1</pre>
To allow access over remote web browsers, comment out the lines on the above config file as shown below.
<pre class="console">Alias /phpMyAdmin /usr/share/phpMyAdmin
#order deny,allow
#deny from all allow from 127.0.0.1</pre>
