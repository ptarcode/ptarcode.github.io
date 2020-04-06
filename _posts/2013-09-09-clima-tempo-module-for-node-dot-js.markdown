---
layout: post
title: "Clima tempo module for Node.js"
date: 2013-09-09 11:33
comments: true
categories: 
keywords: "node.js,climatempo, climatempo node.js, climatempo module node.js, climatempo module"
description: "Clima tempo module for Node.js"
---

---
<!--more-->

### version : 0.0.9
Communication with Clima Tempo accessing information about the weather of Brazil.

## Installation
{% highlight ruby %}
    npm install clima-tempo
{% endhighlight %}

## Usage
{% highlight ruby %}
		var clima = require(clima-tempo);
			 
		var callback = function(error, result) {
		    if (error) {
		        console.error(error);
		    }
		    else{
		    	......
		    }
		}
{% endhighlight %}
### .days
{% highlight ruby %}
		//type = Default or  Extended
		clima.days(codCity,"Extended",callback);
{% endhighlight %}
#### return
{% highlight ruby %} 
		[ { dia: '2013-09-09',
		    tempo: 'Parcialmente Nublado',
		    maxima: '30',
		    minima: '17' },
		  { dia: '2013-09-10',
		    tempo: undefined,
		    maxima: '29',
		    minima: '18' },
		  { dia: '2013-09-11',
		    tempo: 'Parcialmente Nublado',
		    maxima: '29',
		    minima: '18' },
		  { dia: '2013-09-12',
		    tempo: 'Parcialmente Nublado',
		    maxima: '29',
		    minima: '18' },
		  { dia: '2013-09-13',
		    tempo: 'Parcialmente Nublado',
		    maxima: '29',
		    minima: '17' },
		  { dia: '2013-09-14',
		    tempo: 'Parcialmente Nublado',
		    maxima: '29',
		    minima: '17' },
		  { dia: '2013-09-15',
		    tempo: 'Parcialmente Nublado',
		    maxima: '29',
		    minima: '17' } ]
{% endhighlight %}     
### .nowFromPage
{% highlight ruby %}    
		clima.nowFromPage('3156',callback);
{% endhighlight %}
#### return 
{% highlight ruby %}     
		  { last_update: 'Atualizado às: 18:00 ',
			wind: { velocity: '22 Km/h', direction: 'Nor-nordeste' },
			moisture: '83%',
			condition: 'Alguma nebulosidade',
			pression: '1011 hPa',
			temperature: '23ºC' } 
{% endhighlight %}
### .fullFromPage
{% highlight ruby %}
		clima.fullFromPage('3156',callback);
{% endhighlight %}
#### return
{% highlight ruby %} 
		[ { last_update: 'Previsão do tempo atualizada às: 19:40 ',
		    date: ' Quarta-Feira, 04/09 ',
		    condition: 'Chuvoso durante o dia e a noite',
		    wind: 'NNE8km/h',
		    probability_of_precipitation: '26mm90%',
		    moisture_relative_complete: { max: '90%', min: '50%' },
		    temperature: { max: '27º', min: ' 21º ' },
		    uv: 'Alto',
		    sunrise: '06h43',
		    sunset: '18h26' },
		  { last_update: 'Previsão do tempo atualizada às: 19:40 ',
		    date: ' Quinta-Feira, 05/09 ',
		    condition: 'Sol com algumas nuvens. Não chove.',
		    wind: 'S9km/h',
		    probability_of_precipitation: '0mm0%',
		    moisture_relative_complete: { max: '93%', min: '52%' },
		    temperature: { max: '28º', min: ' 17º ' },
		    uv: 'Extremo',
		    sunrise: '06h42',
		    sunset: '18h26' },
		  { last_update: 'Previsão do tempo atualizada às: 19:40 ',
		    date: ' Sexta-Feira, 06/09 ',
		    condition: 'Sol com algumas nuvens. Não chove.',
		    wind: 'ESE12km/h',
		    probability_of_precipitation: '0mm0%',
		    moisture_relative_complete: { max: '91%', min: '50%' },
		    temperature: { max: '30º', min: ' 16º ' },
		    uv: 'Extremo',
		    sunrise: '06h41',
		    sunset: '18h27' },
		  { last_update: 'Previsão do tempo atualizada às: 19:40 ',
		    date: ' Sábado, 07/09 ',
		    condition: 'Sol com algumas nuvens. Não chove.',
		    wind: 'ESE11km/h',
		    probability_of_precipitation: '0mm0%',
		    moisture_relative_complete: { max: '91%', min: '51%' },
		    temperature: { max: '29º', min: ' 20º ' },
		    uv: 'Extremo',
		    sunrise: '06h40',
		    sunset: '18h27' },
		  { last_update: 'Previsão do tempo atualizada às: 19:40 ',
		    date: 'Domingo, 08/09',
		    condition: 'Sol e aumento de nuvens de manhã. Pancadas de chuva à tarde e à noite.',
		    wind: 'E11km/h',
		    probability_of_precipitation: '5mm80%',
		    moisture_relative_complete: { max: '90%', min: '49%' },
		    temperature: { max: '32º', min: ' 18º ' },
		    uv: 'Muito Alto',
		    sunrise: '06h39',
		    sunset: '18h27' } ] 
{% endhighlight %}
### .trendsFromPage
{% highlight ruby %}
		clima.trendsFromPage('3156',callback);

		[ { date: 'Domingo, 08/09',
		    condition: 'Sol e aumento de nuvens de manhã. Pancadas de chuva à tarde e à noite.',
		    probability_of_precipitation: '23mm80%',
		    temperature: { max: '33º', min: '33º' } },
		  { date: 'Segunda-Feira, 09/09',
		    condition: 'Sol e aumento de nuvens de manhã. Pancadas de chuva à tarde e à noite.',
		    probability_of_precipitation: '2mm80%',
		    temperature: { max: '34º', min: '34º' } },
		  { date: 'Terça-Feira, 10/09',
		    condition: 'Sol com algumas nuvens. Não chove.',
		    probability_of_precipitation: '0mm0%',
		    temperature: { max: '34º', min: '34º' } },
		  { date: 'Quarta-Feira, 11/09',
		    condition: 'Sol com algumas nuvens. Não chove.',
		    probability_of_precipitation: '0mm0%',
		    temperature: { max: '36º', min: '36º' } },
		  { date: 'Quinta-Feira, 12/09',
		    condition: 'Sol com aumento de nuvens ao longo do dia. À noite ocorrem pancadas de chuva.',
		    probability_of_precipitation: '3mm80%',
		    temperature: { max: '37º', min: '37º' } } ]
{% endhighlight %}
## Dependencies
{% highlight ruby %}
    cherrio       : ">=0.12.1",
    libxml-to-js  : ">=0.3.11",
    xmlhttprequest: ">=1.6.0"
{% endhighlight %}
---
