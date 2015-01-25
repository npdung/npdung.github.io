---
layout: post
title:  "RUBY ON RAILS FOR BEGINNER"
date:   2015-01-25
tags: instagram
comments: true
---

# **RUBY ON RAILS FOR BEGINNER** #

## 1. SOMETHING IMPORTANT !!! ##

### **SOME BASIC COMMAND** ###

---

**rails new 'name_project' -d 'xxxxx'** : create new project

	if only "rails new 'name_project' " default use SQlite database
    with xxxxx = mysql : use mySQL database
		 xxxxx = postgresql : use Postgres database

**rails server** : start server 

**rails generate controller 'name_controller'** : create a controller 

**rails generate model 'name_model'** : create a model 

**rake routes** : rake routes will list all of your defined routes, which is useful for tracking down routing problems in your app, or giving you a good overview of the URLs in an app you're trying to get familiar with.

**rake db:create** : create database

**rake db:migrate** : runs (single) migrations that have not run yet.

---

### **A BASIC RUNDOWN ON THE FUNCTION OF EACH OF THE FILES AND FOLDERS** ###

---

**app/** : Contains the controllers, models, views, helpers, mailers and assets for your application. You'll focus on this folder for the remainder of this guide.

**bin/** : Contains the rails script that starts your app and can contain other scripts you use to setup, deploy or run your application.

**config/** : Configure your application's routes, database, and more.

**config.ru** : Rack configuration for Rack based servers used to start the application.

**db/** : Contains your current database schema, as well as the database migrations.

**Gemfile, Gemfile.lock** : These files allow you to specify what gem dependencies are needed for your Rails application. These files are used by the Bundler gem.

**lib/** : Extended modules for your application.

**log/** : Application log files.

**public/** : The only folder seen by the world as-is. Contains static files and compiled assets.

**Rakefile** : This file locates and loads tasks that can be run from the command line. The task definitions are defined throughout the components of Rails. Rather than changing Rakefile, you should add your own tasks by adding files to the lib/tasks directory of your application.

**README.rdoc** : This is a brief instruction manual for your application. You should edit this file to tell others what your application does, how to set it up, and so on.

**test/** : Unit tests, fixtures, and other test apparatus. 

**tmp/** : Temporary files (like cache, pid, and session files).

**vendor/** : A place for all third-party code. In a typical Rails application this includes vendored gems.

---

## 2. SIGNUP SIMPLE PAGE !!! ##

Step 1: First, we create a project.

	rails new signup

Then, we need a signup page. Here, I use signup page is a root. We need controller for signup page:

	rails g controller signup

Now, we can go signup\config\router.rb and add

	Rails.application.routes.draw do
		root 'signup#index'
	end

Go console, check and see result:

	rake routes

![Rake Routes](http://i.imgur.com/5jYnYem.png)

We can use 'Prefix'\_path to link a page signup. Ex: root\_path. Now, we need create action 'index' for controller 'signup'. Go signup\app\controllers\signup_controller.rb:

	class SignupController < ApplicationController
		def index
		end
	end

Now, we need create a page view for signup page. Go signup\app\views\signup, create index.html.erb:
	
	<h1>SIGNUP PAGE</h1>

Now, we can see demo. First, we go console and start server. 

	rails s

Then go http://localhost:3000/ and see

![Localhost](http://i.imgur.com/VMZkC3E.png)

Next step, we create a controller 'User'

	rails g controller User	

we create a model 'User' have 'username' and 'password'

	rails g model User username:string password:string

go routes.rb and add
	
	post 'user' => 'user#create'

go user_controller.rb and add

	def create
		@user = User.new(username: params[:user][:username], password: params[:user][:password])
		if !@user.save
			render 'signup/index'
		end
	end

Then, create and migrate database

	rake db:create
	rake db:migrate

Then, We create a form sign up for signup page:

	<h1>SIGNUP PAGE</h1>
	<%= form_for :user, url: user_path do |f| %>
	  <p>
	    <%= f.label :username %><br>
	    <%= f.text_field :username %>
	  </p>
	 
	  <p>
	    <%= f.label :password %><br>
	    <%= f.password_field :password %>
	  </p>
	 
	  <p>
	    <%= f.submit :'sign up' %>
	  </p>
	<% end %>

we create a view signup\app\views\user\create.html.erb

	<p> Success !</p>
	<p>
	  <strong>Username:</strong>
	  <%= @user.username %>
	</p>
	 
	<p>
	  <strong>Password:</strong>
	  <%= @user.password %>
	</p>

Now, see and enjoy

![signup](http://i.imgur.com/aCi3qIV.png)

---

![success](http://i.imgur.com/tL82doV.png)