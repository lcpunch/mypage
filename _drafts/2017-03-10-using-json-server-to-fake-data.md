---
title: Using json-server to fake Rest data
---

A few months ago, I needed an REST API to test an application. I did some research on google, and I found [json-server](https://github.com/typicode/json-server).

Json-server really is what it is. An API running over any json. It's really simple to configurate and get it running.

So to get started, you need just to install json-server.

{% highlight %}
npm install -g json-server
{% endhighlight %}

Next, create a file named db.json anywhere you want it. Then write a json with some data, just as you wish.

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

{% highlight %}
json-server db.json
{% endhighlight %}

Something like this will popup in your terminal.
![My helpful screenshot]({{ site.url }}/assets/terminal_json.jpg)

As you can see, you can take a snapshot of the actual state of your db.json by hiting enter + s.
And then, go in your localhost to see it running.
![My helpful screenshot]({{ site.url }}/assets/hp_json.jpg)

Ok, that's cool. Now we got an API, which can be used to POST, GET, PUT and whatsoever.
Let's just test it. I used insomnia to achieve that.

So, making a GET request would return something like this
![My helpful screenshot]({{ site.url }}/assets/hp_json.jpg)

Ok, that's nice. But I wanted to be able to have a large amount of data. Then I found this [video](https://egghead.io/lessons/nodejs-creating-demo-apis-with-json-server), which gave me a great solution to my problem at the moment, using lodash and faker.

First, install lodash and faker to your project.
{% highlight %}
npm install lodash faker
{% endhighlight %}

After that, create a js file to write the code that will generate the fake data.

{% highlight javascript %}
module.exports = () => {

	const faker = require("faker");
	const _ = require("lodash");

	return {
		employees: _.times(500, (n) => {
			return{
				id: n,
				name: faker.name.findName()
			}
		})
	}
}
{% endhighlight %}


The code is pretty simple, you've to export the function, and return an object with the property that you wish to populate.

Lodash is just used to iterate.

To see what properties faker could generate, just see this cool documentation [here](https://github.com/marak/Faker.js/).