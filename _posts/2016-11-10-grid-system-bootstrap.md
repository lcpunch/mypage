---
title: Bootstrap Grid System
---

A few days ago, I was developing some standard window, and I did some research inside the system code to seek an inspiration. Then, I realize that some developers tend to use html tables to make something that doesn't need a table. For instance, a set of inputs. You can easily achieve that using Bootstrap Grid System, which is already responsive, and it fits well by itself.

<!--more-->

Like this:

{% highlight html %}

<div class="container">
    <div class="row row-content">
       <div class="col-xs-12 col-sm-3">
          <p style="padding:20px;"></p>
          <h2>Please, reserve something</h2>
       </div>
       <div class="col-xs-12 col-sm-9">
          <form class="form-horizontal" role="form">
              <div class="form-group">
                  <label for="firstname" class="col-sm-2 control-label">Number</label>
                  <div class="col-sm-10">
                    <label class="radio-inline"><input type="radio" name="optradio">1</label>
                    <label class="radio-inline"><input type="radio" name="optradio">2</label>
                  </div>
              </div>

              <div class="form-group has-feedback">
                  <label for="firstname" class="col-sm-2 control-label">Date and Time</label>
                  <div class="col-sm-3">
                    <input type="text" class="form-control" name="date" placeholder="Date">
                    <span class="glyphicon glyphicon-calendar form-control-feedback"></span>
                  </div>
                  <div class="col-sm-3 col-sm-offset-1">
                    <input type="text" class="form-control" name="time" placeholder="Time">
                    <span class="glyphicon glyphicon-time form-control-feedback"></span>
                  </div>
              </div>
              <div class="form-group">
                <div class="col-sm-10 col-sm-offset-2">
                  <button type="submit" class="btn btn-primary">Some button</button>
                </div>
              </div>
              <div class="form-group">
                <div class="alert alert-warning">
                  <strong>Warning::</strong> Please <strong><a class="text-warning" href="#">call</a></strong> us.
                  <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
                </div>
              </div>
          </form>
        </div>
   </div>
</div>

{% endhighlight %}

So, instead of using table - tr- td style of code, you can easily use Bootstrap to achieve the same effect, actually even better because it is designed to be to be responsive, "mobile first" and fluid.

First you must create the "container", which encloses the content of the page, or whatsoever. The best thing, it's that he will be automatically fixed to the screen size.

{% highlight html %}

<div class="container">
    ...Content...
</div>

{% endhighlight %}

After the container, you are going to declare the rows. Rows will automatically occupy the width of the container.

{% highlight html %}

<div class="container">
    <div class="row">row 1</div>
    <div class="row">row 2</div>
</div>

{% endhighlight %}

So inside each row Bootstrap creates 12 equal columns. This is exactly where Bootstrap Grid System starts to act, and where we can take profit. For example, if you want that in the first row that some content take the first 4 columns, and another content occupy the remaining, you just declare the first class as col-sm-4, and the second as col-sm-8. In the middle of two, Bootstrap will create the "gutter", which is a margin of 30 pixels.

{% highlight html %}

<div class="container">
    <div class="row">
      <div class="col-sm-4">Column 1</div>
      <div class="col-sm-8">Column 2</div>
    </div>
</div>

{% endhighlight %}

Pretty simple. And if you need a different behavior, for each media, bootstrap provides 4 different classes: col-xs-, col-sm-, col-md- and col-lg. Correspondingly, the extra small, small, medium, and large screen sizes. Each of these classes have a setup, which will determine their behavior as the page is resized. So basically, if you want that your page shows a content for small devices to large devices side by side, and for extra small you want the same content occupying two entire rows:

{% highlight html %}

<div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-4">Column 1</div>
      <div class="col-xs-12 col-sm-7">Column 2</div>
    </div>
</div>

{% endhighlight %}

You don't need to declare for medium and large because bootstrap by default will always take the earlier one. So in this case, col-sm-4 will work for medium and large sizes as well. Another functionality that will help you, is that you can nest columns. You just need to declare another row inside a column, and voilà, you have another twelve columns system to take profit.

{% highlight html %}

<div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-4">Column 1</div>
      <div class="col-xs-12 col-sm-7">
        <div class="row">
          <div class="col-xs-12 col-sm-4">Column 2.1</div>
          <div class="col-xs-12 col-sm-7">Column 2.2</div>
        </div>
      </div>
    </div>
</div>

{% endhighlight %}

So nesting will give us a lot of flexibility. We just need to elaborate the logic, and let the Bootstrap do the rest. You could read more in the [official documentation](http://getbootstrap.com/css/#grid).Also, there is an excellent explanation of the functionality of grid system [here](http://www.helloerik.com/the-subtle-magic-behind-why-the-bootstrap-3-grid-works).

That's pretty much it. Avoid headaches and take advantage of Bootstrap which I think is genial :).
