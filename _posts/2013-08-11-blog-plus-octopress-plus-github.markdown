---
layout: post
title: Blog + Octopress + GitHub
date: 2013-08-11 18:04
comments: true
categories: [Octopress, GitHub]
tags: [jekyl]
keywords: blog, octopress, this, GitHub, Blog + Octopress + GitHub
description: Blog + Octopress + GitHub

seo:
  date_modified: 2020-05-12 19:35:06 -0300
---

---

<!--more-->
### Quick Summary for creating and deploying a post
{% highlight ruby %}
$ rake new_post["New Post"]
$ rake generate
$ git add .
$ git commit -am "Some comment here." 
$ git push origin source
$ rake deploy
{% endhighlight %}

### Installation Process
Go to the terminal and clone the Octopress repo:
{% highlight ruby %}
git clone git://github.com/imathis/octopress.git octopress
cd octopress
{% endhighlight %}
### Check the version of Ruby is 1.9.2. This version is required.
{% highlight ruby %}
ruby --version
bundle install
{% endhighlight %}
### This command installs Octopress
{% highlight ruby %}
rake install
{% endhighlight %}
### Deploying to Github
Create a new Github repository. If you are creating a personal blog create a repo called:
{% highlight ruby %}
username.github.com
{% endhighlight %}
After creating the repo, run the following command.
{% highlight ruby %}
$rake setup_github_pages
{% endhighlight %}
Which is supposed to:
___
* init a git repo
* rename the branch from master to source
* add your repo to origin.
___

Running the previous command shows this:
{% highlight ruby %}
Enter the read/write url for your repository
{% endhighlight %}
You have to enter it like this:
{% highlight ruby %}
git@github.com:username/username.github.com.git
{% endhighlight %}
For me it didn’t rename the branch from master to source or add my remote repo. I did it manually (see below)
### Add your remote repo
Check what remote repositories you have:
{% highlight ruby %}
git remote -v
{% endhighlight %}
My output was:
{% highlight ruby %}
octopress   git://github.com/imathis/octopress.git (fetch)
octopress   git://github.com/imathis/octopress.git (push)
{% endhighlight %}
To add your repo do:
{% highlight ruby %}
git remote add origin git@github.com:username/username.github.com.git
{% endhighlight %}
Rename the branch from master to source
{% highlight ruby %}
$git branch
* master
$git branch -m master source
$git branch
* source
{% endhighlight %}
Preview on development stage
{% highlight ruby %}
$ rake preview
{% endhighlight %}
Then browse to:
{% highlight ruby %}
localhost:4000
{% endhighlight %}
If you get this error:
{% highlight ruby %}
Sorry, I cannot find /
{% endhighlight %}
Read this link: Deploying to a Subdirectory
### First push to Github
{% highlight ruby %}
$rake generate
$git add .
$git commit -am "First deploy to github." 
$git push origin source
$rake deploy
{% endhighlight %}
Create a new posting
{% highlight ruby %}
$rake new_post["Creating a Github Blog Using Octopress"]
{% endhighlight %}
Go to the app folder source/_posts to find the new posting
Edit the posting and then follow these steps
{% highlight ruby %}
$rake generate
$git add .
$git commit -m "Initial blog post." 
$git push origin source
$rake deploy
{% endhighlight %}
Add a custom domain
Go to source folder and create 2 files :
(mate if you are using Textmate)
{% highlight ruby %}
cd source
mate CNAME
mate .nojekyll
{% endhighlight %}
Open the CNAMe file and this line:
{% highlight ruby %}
www.yourdomain.com
{% endhighlight %}
The NoJekyll file will make Octopress works in Github Pages.
Push again to github
{% highlight ruby %}
rake generate
git add .
git add -am 'domain configuration'
git push origin source
rake deploy
{% endhighlight %}
Github need time to read your CNAME and updating the sites.
___