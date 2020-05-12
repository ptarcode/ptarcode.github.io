---
layout: post
title: Erlang Basics
date: 2016-02-07 20:07
comments: true
tags: [erlang]
categories: [Dev]
keywords:
description:
seo:
  date_modified: 2020-05-12 19:35:06 -0300
---

<!--more-->

Erlang is a programming language used to build massively scalable soft real-time systems with requirements on high availability. Some of its uses are in telecoms, banking, e-commerce, computer telephony and instant messaging. Erlang's runtime system has built-in support for concurrency, distribution and fault tolerance.

### History

The name "Erlang", attributed to Bjarne Däcker, has been presumed by those working on the telephony switches (for whom the language was designed) to be a reference to Danish mathematician and engineer Agner Krarup Erlang or the ubiquitous use of the unit named for him, and (initially at least) simultaneously as a syllabic abbreviation of "Ericsson Language".

##### 1982 - 1985
Experiments with programming of telecom using > 20 different languages. Conclusion: The language must be a very high level symbolic language in order to achive productivity gains ! (Leaves us with: Lisp , Prolog , Parlog ...)
##### 1985 - 1986
Experiments with Lisp,Prolog, Parlog etc. Conclusion: The language must contain primitives for concurrency and error recovery, and the execution model must not have back-tracking. (Rules out Lisp and Prolog.) It must also have a granularity of concurrency such that one asyncronous telephony process is represented by one process in the language. Rules out Parlog. We must therefore develop our own language with the desirable features of Lisp, Prolog and Parlog, but with concurrency and error recovery built into the language.
##### 1987
The first experiments with Erlang.
##### 1988
ACS/Dunder Phase 1. Prototype construction of PABX functionality by external users Erlang escapes from the lab!
##### 1989
ACS/Dunder Phase 2. Reconstruction of 1/10 of the complete MD-110 system. Results: >> 10 times greater gains in efficency at construction compared with construction in PLEX!Further experiments with a fast implementation of Erlang.
##### 1990
Erlang is presented at ISS'90, which results in several new users, e.g Bellcore.
##### 1991
Fast implementation of Erlang is released to users. Erlang is represented at Telecom'91 . More functionality such as ASN1 - Compiler , graphical interface etc.
##### 1992
A lot of new users, e.g several RACE projects. Erlang is ported to VxWorks, PC, Macintosh etc. Three applications using Erlang are presented at ISS'92. The two first product projects using Erlang are started.
##### 1993
Distribution is added to Erlang, which makes it possible to run a homgeneous Erlang system on a heterogeneous hardware. Decision to sell implementations Erlang externally. Separate organization in Ericsson started to maintain and support Erlang implementations and Erlang Tools. 

### Installation

Erlang Solutions offers a number of installs at http://www.erlang.org/downloads.
Erlang/OTP Platform is a complex system composed of many smaller applications (modules). Installing the erlang package automatically installs the entire OTP suite. Since some of the more advanced users might want to download only a specific selection of modules, Erlang/OTP has been divided into smaller packages, all with the prefix 'erlang-', that can be installed without launching the erlang package.

Most OS package managers provide pre-built binary packages. You can also download the latest stable releases from Erlang Solutions or try install with package managers.

    For Homebrew on OS X: brew install erlang
    For MacPorts on OS X: port install erlang
    For Ubuntu and Debian: apt-get install erlang
    For Fedora: yum install erlang
    For FreeBSD: pkg install erlang

### Shell 

On Windows command line type **werl** on Linux or Mac OS X type **erl**.
{% highlight erlang %}
    Erlang/OTP 18 [erts-7.2] [source-e6dd627] [64-bit] [smp:4:4] [async-threads:10] [hipe] [kernel-poll:false]

    Eshell V7.2  (abort with ^G)
    1>
{% endhighlight %}


#### Browsing the archives

{% highlight ruby %}

pwd(). 
/Users/ptarcode 
ok

{% endhighlight %}

Argument in parentheses but in quotes, preferably double quotes.
{% highlight ruby %}
5> cd("..").
/Users
ok
6> cd("ptarcode"). /Users/ptarcode
ok
7>
{% endhighlight %}

#### Doing ...

{% highlight ruby %}
Eshell V5.9 (abort with ^G) 1> 2+2.
4
2> 39-9.
30
3> 10*43.
430
4> 100 div 15.
6
6> 100 rem 15.
10
7> 3*(5+3).
24
{% endhighlight %} 

#### Functions ...

Mathematical functions supported by Erlang’s math module simple examples.
{% highlight ruby %}
4> math:pi(). 
3.141592653589793

5> math:cos(math:pi()).
-1.0

{% endhighlight %} 

#### Numbers

Erlang recognizes integers and floating-point numbers. Uses the 64-bit IEEE 754-1985 “double precision” representation. This means that it keeps track of about 15 decimal digits plus an exponent.

{% highlight ruby %}

7> 8888888888888888888888888888888888888888888.0. 
8.888888888888889e42

9> 88888888888.88888888888888 .
88888888888.88889

{% endhighlight %}

Digits+Exponent notation

{% highlight ruby %}

7> 2.923e127. 2.923e127
8> 7.6345435e-231. 7.6345435e-231

{% endhighlight %} 

Base2+Value notation
{% highlight ruby %}
11> 2#10101. 
21
12> -2#10101. 
-21
{% endhighlight %}

Base16+Value notation
{% highlight ruby %}
16> 16#fa81.
64129
17> -16#fa81.
-64129
{% endhighlight %}


#### Variables

{% highlight ruby %}
19> V=3 .
3

{% endhighlight %}

Variable can't be signed with a new value.

{% highlight ruby %}

20> V=4 .
** exception error: no match of right hand side value 4
21> 

21> V2= V*4 .
12
22> V2 .
12

{% endhighlight %}

Show bounded variables **b() . **

{% highlight ruby %}
23> b() .
V = 3
V2 = 12
ok
{% endhighlight %}

Clearing bounded variables **f(variable) . **

{% highlight ruby %}
23> b() .
V = 3
V2 = 12
ok
24> f(V) .
ok
25> b() . 
V2 = 12
ok
{% endhighlight %}

Clearing all bounded variables **f() . **

{% highlight ruby %}
23> b() .
V = 3
V2 = 12
ok
24> f() .
ok
25> b() .
ok
{% endhighlight %}

Continue ...