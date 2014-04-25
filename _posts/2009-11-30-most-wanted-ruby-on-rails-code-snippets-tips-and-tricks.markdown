--- 
layout: post
title: Most wanted ruby on rails code snippets, tips and tricks
wordpress_id: 149
wordpress_url: http://randika.com/?p=149
date: 2009-11-30 10:44:53 +00:00
---
I keep forgetting all those fancy ruby on rails commands and the important code snippets always. I better keep them documented some where I can find easily. So I'm going to write down as much as code snippets, command lines, tips tricks where I need. Anyway this looks messy as I update this page time to time, hope you also can contribute for the list. I hope this will help someone else too.

<strong>How to add/remove new columns to table (models) ?</strong>
you can specify columns you want to add/remove in your migration by passing attribute:type pairs to the migration generator command line. here is an example to add the mobile number to existing user model.
<pre class="console">[randika@localhost MyApp]$ script/generate migration AddMobileToUser mobile:string</pre>
and run the <strong>rake db:migrate</strong> command.  This will create the migration schema for you as:
<pre lang="ruby">class AddMobileToUser &lt; ActiveRecord::Migration
  def self.up
    add_column :users, :mobile, :string
  end

  def self.down
    remove_column :users, :mobile
  end
end</pre>
Similarly when you need to remove a column try using below command, followed by the the <strong>rake db:migrate </strong>
<pre class="console">[randika@localhost MyApp]$ script/generate migration RemoveMobileFromUser mobile:string</pre>
<strong>How to create dynamic drop down menu from a another model</strong>
<pre lang="ruby">&lt;%= f.select :country_id, Country.all.collect {|country| [ country.name, country.id ] } %&gt;</pre>
this will output:
<pre lang="html"><select id="country_country_id" name="country[country_id]">
<option value="1">Country A</option>
<option value="2">Country B</option>
<option value="3">Country C</option>
</select></pre>
<br/>
<strong>How to find the configuration settings, versions of the development environment</strong>
<ul>
	<li>To determine the version of Rails that you are running, you can issue <code>rails -v</code> at a command prompt.</li>
<pre class="console">$rails -v</pre>
	<li>To determine the Rails installation path type <code>which rails</code> at a command prompt. (only on linux)</li>
<pre class="console">$which rails</pre>
	<li>To determine the list of gems installed type <code>gem list</code></li>
<pre class="console">$gem list</pre>
</ul>
<br/>
<strong>How to print the month name from a month number</strong>
<br/>
Putting this code in a view, will print "December" as the output.
<pre lang="ruby"><%= Date::MONTHNAMES[12] %></pre>
<strong>How to assign a css class to <code>link_to</code> method in Ruby on Rails</strong>
<script src="http://gist.github.com/270233.js?file=gistfile1.rb"></script>
<strong>How to install/start mongrel http server</strong>
<br/>
<pre class="console">
$ sudo gem install mongrel
$ cd yourrailsapp
$ mongrel_rails start -d
</pre>
<br/>
<strong>How to stop mongrel http server</strong>
<br/>
<pre class="console">$ mongrel_rails stop</pre>
