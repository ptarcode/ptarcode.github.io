---
layout: post
title: "Gem previsao-clima-tempo"
date: 2013-08-17 00:00
comments: true
categories: [Rails, Gems]
keywords: "clima tempo, clima-tempo, gem clima tempo, gem clima-tempo, previsao tempo, previsao-clima-tempo, gem" 
description: "Gem Communication with Clima Tempo accessing information about the weather of Brazil."
---
---


<!--more-->
[![Gem Version](https://badge.fury.io/rb/previsao-clima-tempo.png)](http://badge.fury.io/rb/previsao-clima-tempo)

Communication with Clima Tempo accessing information about the weather of Brazil.

## Installation

Add this line to your application's Gemfile:
{% highlight ruby %}
    gem 'previsao-clima-tempo'
{% endhighlight %}

And then execute:
{% highlight ruby %}
    $ bundle
{% endhighlight %}

Or install it yourself as:
{% highlight ruby %}
    $ gem install previsao-clima-tempo
{% endhighlight %}

## Usage
	 
### From Webservice
#####  .new
Instantiating a object.The city code should be informed.
	 {% highlight ruby %}
PrevisaoClimaTempo.new(:codCity => '3156')
     {% endhighlight %}
##### .now     
Returns an object PrevisaoDia with information from the current day.
     {% highlight ruby %}
     PrevisaoClimaTempo.new(:codCity => '3156').now
     {% endhighlight %}
##### .tomorrow     
Returns an object PrevisaoDia with information the next day.
     {% highlight ruby %}
     PrevisaoClimaTempo.new(:codCity => '3156').tomorrow
     {% endhighlight %}
##### .days     
Returns a collection of objects PrevisaoDia with information of days referenced.
     {% highlight ruby %}
     PrevisaoClimaTempo.new(:codCity => '3156').days(13) maximum of 13 days from the current day
     {% endhighlight %}
##### .day     
Returns an object PrevisaoDia with information the day referenced.
     {% highlight ruby %}
     PrevisaoClimaTempo.new(:codCity => '3156').day(date)
     {% endhighlight %}
     
### From Page
#### (contains more information than is extracted from the webservice)
##### .nowFromPage     
Returns a hash of condtions of weather from page
     {% highlight ruby %}
	 PrevisaoClimaTempo.new(:codCity => '314').nowFromPage
	 {% endhighlight %}
return:
	 {% highlight ruby %}
	 {
		:last_update: 18:00
		:wind:
		  :velocity: 3 Km/h
		  :direction: Su-sudeste
		:moisture: 91%
		:condition: Poucas nuvens
		:pression: 1022 hPa
		:temperature: 13ºC  
 	 }
 	 {% endhighlight %}
##### .fullFromPage 	 
Returns a hash of condtions of weather whith 5 days from page.
     {% highlight ruby %}
  	 PrevisaoClimaTempo.new(:codCity => '314').fullFromPage
  	 {% endhighlight %}
return:
	 {% highlight ruby %}
	 {
		1:
		  :last_update: 19:00
		  :date: Sábado, 17/08/2013
		  :condition: Sol com muitas nuvens durante o dia e períodos de céu nublado. Noite
		    com muitas nuvens.
		  :wind:
		    :velocity: 6km/h
		    :direction: Su-sudeste
		  :probability_of_precipitation:
		    :volume: 0mm
		    :percentage: 0%
		  :moisture_relative_complete:
		    :max: 100%
		    :min: 49%
		  :temperature:
		    :max: 16º
		    :min: 7º
		  :uv: Alto
		  :sunrise: 06h13
		  :sunset: 17h36
		2: ...
 	 }
 	 {% endhighlight %}
##### .trendsFromPage 	 
Returns a hash of condtions of weather whith 5 days from page.
If today is 16-12-2013 returns 21,22,23,24,25 trends.
	 {% highlight ruby %}
  	 PrevisaoClimaTempo.new(:codCity => '314').trendsFromPage
  	 {% endhighlight %}
return:
	 {% highlight ruby %}
	 {
		1:
		  :date: Quinta-Feira, 22/08/2013
		  :condition: Sol com algumas nuvens. Não chove.
		  :probability_of_precipitation:
		    :volume: 0mm
		    :percentage: 0%
		  :temperature:
		    :max: 23º
		    :min: 7º
		2: 
 	 }
 	 {% endhighlight %}
 	 
---
