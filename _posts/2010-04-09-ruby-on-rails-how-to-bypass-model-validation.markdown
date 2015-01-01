--- 
layout: post
title: "Ruby on Rails: How to bypass Model validation"
wordpress_id: 198
wordpress_url: http://randika.com/?p=198
date: 2010-04-09 12:55:27 +01:00
---
In my recent application I have these two models (User, BusinessAccount) with some data validation which works well with their respective controllers.

While keeping these models with their data validation as it is, I wanted to create another Controller (SignupController) which save both model data at once. But  I wanted to bypass the original model validation when saving the data from SignupController.

Here is what I did to achieve it with <a href="http://api.rubyonrails.org/classes/ActiveRecord/Validations.html#M002153" target="_blank"><strong>save_with_validation</strong>(perform_validation = false)</a> , hope this will help someone else who looking for the same.

<script src="http://gist.github.com/361105.js?file=gistfile1.ru"></script>
