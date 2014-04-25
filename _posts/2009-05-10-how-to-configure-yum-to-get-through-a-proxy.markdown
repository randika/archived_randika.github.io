--- 
layout: post
title: How to configure yum to get through a proxy
wordpress_id: 10
wordpress_url: http://localhost/randika_wp/?p=10
date: 2009-05-10 08:41:00 +01:00
---
Today I had a new problem with one of a Fedora 8 server. The issue was with "yum". When I try to install some apps with yum it didn't work for me. Sorry I can't really remember the error at this time. But It was something related to Yum repository is not accessible.

First I thought there is some issue with internet, but I was wrong. Internet was fine. The server's internet connection was running with a proxy. So I realized there is still something to do with yum configuration.

So I had to google a bit to find out a solution or fix for get through the proxy server. here is what I did.

I just execute this command on a shell prompt and yum worked fine for me.
NOTE: my proxy server is 130.10.32.3 on port 9000. make sure to use your one instead :)
<pre class="console">
export http_proxy=http://130.10.xxx.xxx:xxxx
export ftp_proxy=http://130.10.xxx.xxx:xxxx
</pre>
Alternately you may add this line to /etc/yum.conf
<pre class="console">
http_proxy=http://130.10.xxx.xxx:xxxx
ftp_proxy=http://130.10.xxx.xxx:xxxx
</pre>
