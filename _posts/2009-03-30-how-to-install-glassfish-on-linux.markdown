--- 
layout: post
title: How to Install Glassfish on Linux
wordpress_id: 4
wordpress_url: http://localhost/randika_wp/?p=4
date: 2009-03-30 07:12:00 +01:00
---
Before start the installation, verify the availability of java in your linux node.
<pre class="console">$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-Fedora-10) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode)</pre>
<span style="font-size:85%;">Now you need the latest version of </span><a title="Download glassfish" href="https://glassfish.dev.java.net/downloads">Glassfish application server</a><span style="font-size:85%;">, I’m using Glassfish V2 for Linux for this installation.</span> I'm going to download this file to <span style="font-weight: bold;">/opt </span>dir.
<pre class="console">$ lwp-download http://java.net/download/javaee5/v2ur2/promoted/Linux/glassfish-installer-v2ur2-b04-linux.jar</pre>
once finished, execute
<pre class="console">$ java -Xmx256m -jar glassfish-installer-v2ur2-b04-linux.jar</pre>
Files will be decompressed in a directory named <span style="font-weight: bold;">/opt/glassfish</span>

switch to glassfish dir and type
<pre class="console">$ chmod +x -R lib/ant/bin
$ lib/ant/bin/ant -f setup.xml</pre>
Ok, its almost done. Let's start the server now.
<pre class="console">$ bin/asadmin start-domain</pre>
Now type http://localhost:8080 and see it's working. you can reach to the admin console http://localhost:4848 here with default username/password. (admin/adminadmin)

hope this helps some one. <span style="font-family:monospace;">
</span>
