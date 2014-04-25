--- 
layout: post
title: "Ruby on rails: how to install ruby 1.8.7 on windows"
wordpress_id: 178
wordpress_url: http://randika.com/?p=178
date: 2010-01-11 16:47:23 +00:00
---
I couldn't find the very famous ruby one-click-installer for ruby 1.8.7, after trying various ways I ended up with a solution for this. Here is what I did to get ruby 1.8.7 installed on windows.

First download the ruby 1.8.7 from this link: <a href="http://www.ruby-lang.org/en/downloads/">http://www.ruby-lang.org/en/downloads/</a> (I took Ruby 1.8.7-p72 Binary)

extract this to c:\ruby (or somewhere else you prefer but avoid using spaces on directories for your own safety)

Now update your <code>PATH</code> environment variable with appending <code>c:\ruby\bin</code> and verify the status of the installation by typing <code>ruby -v</code> in the command line prompt.
<pre class="console">C:\Users\Randika&gt;ruby -v
ruby 1.8.7 (2008-08-11 patchlevel 72) [i386-mswin32]</pre>
Ok now we need some dependencies  packages which doesn't bundle with ruby 1.8.7

Download <strong>libiconv package</strong> from here
<a href="http://www.ruby-lang.org/en/downloads/">http://sourceforge.net/projects/gettext/files/</a>
find the libiconv-1.9.1.bin.woe32\bin\iconv.dll and place it inside <code>c:\ruby\bin\</code>

Download <strong>zlib package</strong> from here
<a href="http://www.zlib.net/zlib123-dll.zip ">http://www.zlib.net/zlib123-dll.zip</a>
extract it and find the zlib1.dll and place it inside  inside <code>c:\ruby\bin\</code>

OK, now we can install <strong>rubygems</strong>
Get it from here <a href="http://rubyforge.org/frs/?group_id=126">rubygems-1.3.5.zip</a> and extract to wherever you prefer. And then run <code>ruby setup.rb</code>
<pre class="console">D:\gems\rubygems-1.3.5&gt;ruby setup.rb</pre>
by now gems should be ready to use with. Now you can update gems with
<pre class="console">gem update --system</pre>
finally install rails
<pre class="console">D:\&gt;gem install rails
.....
...
D:\&gt;rails -v
Rails 2.3.5</pre>
<span style="color: #000000;"><strong>UPDATE: (20100422)</strong></span>
There is a Release Candidate (RC) of Ruby 1.8.7 (Ruby 1.8.7-p249 (RC2)) at http://rubyinstaller.org/download.htm
You can try that instead of what I have told in this post. Anyway I didn't try it myself yet.
