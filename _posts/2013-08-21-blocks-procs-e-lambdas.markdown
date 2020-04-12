---
layout: post
title: "Blocks, Procs e Lambdas"
date: 2013-08-21 22:35
comments: true
tags: [code, rubyOnRails]
categories: Ruby
keywords: "blocks, procs, lambdas, ruby"
description: "Blocks, Procs e Lambdas"
---

---
<!--more-->

## Blocks
Writing methods that can accept blocks is simple. There's no special syntax needed, you can simply write the method as you would any other. To call any block passed to the method, use the yield keyword. Like any other method call, when you use the yield keyword you can leave it as it is and call the block without any parameters. Or, if you wish, you can add a parameter list as you would with a method call. 
{% highlight ruby %}
def call_this_block
	yield
end

call_this_block { puts "tweet" }

{% endhighlight %}

#### Optional Block

{% highlight ruby %}
class Optional
	def initialize
	   yield self if block_given?
	end
end
{% endhighlight %}

## Procs
Proc objects are blocks of code that have been bound to a set of local variables. Once bound, the code may be called in different contexts and still access those variables.

{% highlight ruby %}
def gen_times(factor)
  return Proc.new {|n| n*factor }
end

times3 = gen_times(3)
times5 = gen_times(5)

times3.call(12)               #=> 36
times5.call(5)                #=> 25
times3.call(times5.call(4))   #=> 60

{% endhighlight %}


## Lambdas
You may have heard of lambdas before. Perhaps you've used them in other languages. Despite the fancy name, a lambda is just a function... peculiarly... without a name. They're anonymous, little functional spies sneaking into the rest of your code. Lambdas in Ruby are also objects, just like everything else! The last expression of a lambda is its return value, just like regular functions. As boring and familiar as that all sounds, it gives us a lot of power.

{% highlight ruby %}
my_proc = lambda { puts "tweet" }
my_proc.call # => tweet
{% endhighlight %}

#### Multiple Lambdas
{% highlight ruby %}
class Comment
	def post(
		if authenticate?(@user, @password)
		 	# submit the comment
			success
			success.call
		else
			error.call
		end
	end
end


comment   = Comment.new('Yeeeeeep!')
success = -> { puts "Sent!" }
error   = -> { raise 'Auth Error' }
comment.post(success, error)
{% endhighlight %}

#### Lambda to Block
{% highlight ruby %}
blablas = ["First", "Second"]
blablas.each do |blabla|
puts blabla					#Lets try converting to a proc
end

blablas = ["First", "Second"]
printer = lambda { |blabla| puts blabla }

blablas.each(&printer)       

#‘&’ turns proc into block 
#because each expects a block, not a proc 
								
{% endhighlight %}
---