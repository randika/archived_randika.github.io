--- 
layout: post
title: "Cakephp Tips: Routing an Admin dashboard"
wordpress_id: 89
wordpress_url: http://randika.com/?p=89
date: 2009-09-09 12:49:11 +01:00
---
I had some issues today with the admin routes of my XYZ :) cakephp app. I want the administrator to be able to type <strong>domainfoo.bar/admin</strong> and be directed to a log in. Then right after the authentication I want them to be redirected to admin_index of  the dashboards_controller (Admin's Dashboard), So here is what I did for redirection.
<pre lang="php" line="1">
$this->redirect(array('controller'=>'dashboards','action'=>'admin_index'));
</pre>
But the problem is that I get the following error:
<h2 style="margin: 0.3em 0px; padding: 0.8em 0px 0px; font-weight: normal; background-color: #ffffff; color: #ee3322; font-family: 'Gill Sans','lucida grande',helvetica,arial,sans-serif; font-size: 27px;">Private Method in DashboardsController</h2>
<p class="error" style="margin: 1em 0px; padding: 0.8em; background-color: #ee3322; color: #ffffff; font-family: Courier,monospace; font-size: 14px; line-height: 19px;"><strong style="margin: 0px; padding: 0px;">Error:<span class="Apple-converted-space"> </span></strong><em style="margin: 0px; padding: 0px; color: #000000; font-weight: normal; line-height: 19px;">DashboardsController::</em><em style="margin: 0px; padding: 0px; color: #000000; font-weight: normal; line-height: 19px;">admin_index()</em><span class="Apple-converted-space"> </span>cannot be accessed directly.</p>
<p class="notice" style="margin: 1em 0px; padding: 0.8em; background-color: #ffcc00; color: #000000; display: block; font-family: Courier,monospace; font-size: 14px; line-height: 19px;"><strong style="margin: 0px; padding: 0px;">Notice:<span class="Apple-converted-space"> </span></strong>If you want to customize this error message, create app\views\errors\private_action.ctp</p>

The issue is when using,
<pre lang="php" line="1">
$this->redirect(array('controller'=>'dashboards','action'=>'admin_index'));
</pre>
it tries to access the admin_index() function directly which is private as the URL goes<strong> domainfoo.bar/dashbords/admin_index</strong>

Instead we should set it as:

<pre lang="php" line="1">
$this->redirect(array('controller'=>'dashboards','action'=>'index','admin'=>true));
</pre>
or
<pre lang="php" line="1">
$this->redirect(array('controller'=>'dashboards','action'=>'index','prefix'=>'admin'));
</pre>
Hope this will help someone one day.
