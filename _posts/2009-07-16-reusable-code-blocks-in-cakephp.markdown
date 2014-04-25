--- 
layout: post
title: Reusable code blocks in CakePhp
wordpress_id: 63
wordpress_url: http://randika.com/uncategorized/reusable-code-blocks-in-cakephp
date: 2009-07-16 04:30:28 +01:00
---
Many web applications has code blocks such as header areas, footer areas, navigation menus that need to be repeated from page to page. In Cake These reusable parts are called Elements. This short tutorial demonstrates how to create and reuse code block in <a href="http://cakephp.org">cakephp</a>.

All you needs do first is, find the /app/views/elements/ directory from your cakephp web app and create a new file with the .ctp extension. oh if you are using .thtml as your views extension no matter you can use it.

For this example I'm creating footer block for my cake app. in /app/views/elements/footer.ctp
Then add the codes that requires for the footer in that page.

and from my other views, now i can call for this block as
<pre lang="php">echo $this->element('footer');</pre>
Yeah, It's that simple. Also you can pass data to an element through the element's second argument:
<pre lang="php">echo $this->element('footer', array("var_foo"=>"bar"));</pre>
On your element now you can get that variable, as this variable is available as members of the parameter array.
<pre lang="php">echo $var_foo; //this will print "bar" as the output.</pre>
