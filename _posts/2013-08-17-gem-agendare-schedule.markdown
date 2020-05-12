---
layout: post
title: "Gem agendare-schedule"
date: 2013-08-17 12:22
comments: true
tags: [ruby]
categories: [Ruby on Rails, Gems]
keywords: "agendare schedule, agendare-schedule, gem agendare schedule, gem agendare-schedule, agendar, gem schedule, gem" 
description: "The basic structure to implement schedule project. You have 3 objects to implement yours views, because the logic is implemented in this gem."
 
---
---

<!--more-->
[![Gem Version](https://badge.fury.io/rb/agendare-schedule.png)](http://badge.fury.io/rb/agendare-schedule)

The basic structure to implement schedule project. You have 3 objects to implement yours views, because the logic is implemented in this gem.

## Installation

Add this line to your application's Gemfile:
	{% highlight ruby %}
    gem 'agendare-schedule'
    {% endhighlight %}

And then execute:
	{% highlight ruby %}
    $ bundle
    {% endhighlight %}

## Usage
	 
Create controlllers.
{% highlight ruby %}
     rails  generate agendare:install controllers
{% endhighlight %}
     
Create models.
{% highlight ruby %}
     rails  generate agendare:install models
{% endhighlight %}
     
Create migrations.
{% highlight ruby %}
     rails  generate agendare:install migrations
{% endhighlight %}
     
Import the structure to database.
{% highlight ruby %}
     rake db:migrate
{% endhighlight %}
     
Add this lines in your config/routes.rb
{% highlight ruby %}
	 resources :schedules
	 resources :scheduleds
	 resources :users 
{% endhighlight %}

---