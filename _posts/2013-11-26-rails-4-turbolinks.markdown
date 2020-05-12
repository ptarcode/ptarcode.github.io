---
layout: post
title: "Rails 4 Turbolinks"
date: 2013-11-26 23:36
comments: true
tags: [ruby]
categories: [Ruby on Rails]
keywords: "rails 4, rails turbolinks, turbolinks"
description: "Rails 4 Turbolinks"
---

---
<!--more-->

### What is it?
{% highlight ruby %}
	gem 'turbolinks'
{% endhighlight %}
"This is a gem that works similar to pjax, but instead of worrying about what element on the page to replace, and tailoring the server-side response to fit, we replace the entire body. This means that you get the bulk of the speed benefits from pjax (no recompiling of the JavaScript or CSS) without having to tailor the server-side response. It just works."

### PJAX
Uses AJAX and PushState to deliver a faster browsing experience by only loading and updating parts of the page HTML each page load. PushState makes it possible to add real permalinks, page titles, and a working back button so that your visitors won't be able to tell the difference between PJAX page load and ordinary full page loads.

[Tutorial](http://www.youtube.com/watch?v=CKv9C2qUL-8 "Title")

### Using the gem
Gemfile:
{% highlight ruby %}
	gem 'turbolinks'
{% endhighlight %}

Add this line on app/assets/javascripts/application.js:
{% highlight ruby %}
	//= require turbolinks
{% endhighlight %}

app/views/layouts/application.html.erb:
{% highlight ruby %}
<%= stylesheet_link_tag    "application", media: "all", "data-turbolinks-track" => true %>
<%= javascript_include_tag "application", "data-turbolinks-track" => true %>
{% endhighlight %}

If you wont use Turbolink in some link, you can manually exclude:
{% highlight ruby %}
<a href="/examples" data-no-turbolink>Examples</a>
{% endhighlight %}

"With Turbolinks pages will change without a full reload, so you can't rely on DOMContentLoaded or jQuery.ready() to trigger your code. Instead Turbolinks fires events on document to provide hooks into the lifecycle of the page."
Runtime Dependencies coffee-rails, but if you want use javascript.You can manually download and compile the turbolinks.js.coffee to JavaScript.
{% highlight ruby %}
ready = ->

  ...your coffeescript goes here...

$(document).ready(ready)
$(document).on('page:load', ready)
{% endhighlight %}

{% highlight ruby %}
var ready;
ready = function() {

  ...your javascript goes here...

};

$(document).ready(ready);
$(document).on('page:load', ready);

{% endhighlight %}


### Links
[Turbolinks Project](https://github.com/rails/turbolinks "Turbolinks Project")

[Railscasts Turbolinks](http://railscasts.com/episodes/390-turbolinks "Railscasts Turbolinks")

---