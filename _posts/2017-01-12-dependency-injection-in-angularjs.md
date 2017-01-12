---
title: Dependency Injection in AngularJS
---

What is dependency injection? Basically, is a software design pattern that implements inversion of control for resolving dependencies.
<!--more-->
Or, simplifying that, is an object that can be used as a service in another object. In this case, the object that is dependent, is not aware of how the other object is implemented.
He just uses it.

There are three ways in angularJS to do so:

 - Using the new operator.

 - Using a local variable.

 - Passing the dependency just when needed.

 The third option is the most flexible because you won't hard code, plus, testing becomes easier.
 You can just mock the object if you need to test it. You don't worry about dependency because the framework will do it for you.

DI has four roles:

 - Service

 - Client

 - Interface

 - Injector

Angular makes use of DI extremely well. His approach is to separate the business logic from dependency construction, so the developer can write the business logic into independent objects,
and then inject them wherever is required.
And to take care of the injection, we can count on the Angular injector subsystem. He creates components, resolve their dependencies and provides them to other components.

Yes, DI is very used in Angular:

 - Components like services, directives, filters and animations

 - Controllers can be injected with anything that is a component.

So, how we can do that? There are three ways:

- Inline array annotation:
{% highlight javascript %}

  module.contoller('SomeController', [$scope, 'someFactory', function($scope, someFactory){}]);

{% endhighlight %}

- $inject property annotation
{% highlight javascript %}

  var Controller = function($scope, someFactory){};
  Controller.$inject=['$scope', 'someFactory'];
  module.controller('Controller', Controller);

{% endhighlight %}

- And implicit annotation

{% highlight javascript %}

  module.controller('Controller', function($scope, someFactory));

{% endhighlight %}

I never used other than inline array. I did read some problems of it with uglification and minification about the implicit annotation, but I never tried.

And you, what you use the most? Do you know any cases that one way of annotation is better than another?
