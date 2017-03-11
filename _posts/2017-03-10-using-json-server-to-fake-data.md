---
title: Using json-server to fake Rest data
---

A few months ago, I needed an REST API to test an application. I did some research on google, and I found [json-server](https://github.com/typicode/json-server).

Json-server really is what it is. An API running over any json. It's really simple to configurate and get it running.
<!--more-->
So to get started, you need just to install json-server.

{% highlight bash %}
npm install -g json-server
{% endhighlight %}

Next, create a file named db.json anywhere you want it. Then, write a json with some data, just as you wish.

{% highlight json %}
{
	"employees": [
	{
		"id": 0,
		"name": "Samantha"
	},
	{
		"id": 1,
		"name": "Josh"
	},
	{
		"id": 2,
		"name": "Laurie"
	}
	]
}
{% endhighlight %}

Save your file and run json-server.

{% highlight bash %}
json-server db.json
{% endhighlight %}

Something like this will popup in your terminal.

![My helpful screenshot]({{ site.url }}/{{ site.baseurl }}/assets/terminal_json.PNG)

As you can see, you can take a snapshot of the actual state of your db.json by hiting enter + s.
Ok. After that, go in your localhost to see it running.

![My helpful screenshot]({{ site.url }}/{{ site.baseurl }}/assets/hp_json.PNG)

Ok, that's cool. Now we got an API, which can be used to POST, GET, PUT and whatsoever.
Let's just test it. I used insomnia to achieve that.

So, making a GET request would return something like this

![My helpful screenshot]({{ site.url }}/{{ site.baseurl }}/assets/insomnia_get.PNG)

Ok, that's nice. However I wanted to be able to have a large amount of data.
So I went back to google again, and I've found [faker](https://github.com/marak/Faker.js/).


So here is the ideia, first, install lodash and faker to your project.
{% highlight bash %}
npm install lodash faker
{% endhighlight %}

After that, create a gen.js file to write the code that will generate the fake data.

{% highlight javascript %}
module.exports = () => {

	const faker = require("faker");
	const lodash = require("lodash");

	return {
		employees: lodash.times(500, (n) => {
			return{
				id: n,
				name: faker.name.findName()
			}
		})
	}
}
{% endhighlight %}


The code is pretty simple, you've to export the function, and return an object with the property that you wish to populate.
Lodash is just used to iterate and faker do all the hard work. To see what properties faker could generate, just see this cool documentation [here](https://github.com/marak/Faker.js/).

And now, after a few short steps, let's give a try. In your terminal, type the following

{% highlight bash %}
json-server gen.js
{% endhighlight %}

And voilà. Let's see the result in GET.

![My helpful screenshot]({{ site.url }}/{{ site.baseurl }}/assets/insomnia_json2.PNG)

Nice and easy. If you need something that's not much specific, you could give a try in [this](https://jsonplaceholder.typicode.com/).
Also, I made available in [here](https://github.com/lcpunch/fake-rest-api/), if you want it.
