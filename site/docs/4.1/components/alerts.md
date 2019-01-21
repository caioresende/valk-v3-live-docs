---
layout: docs
title: Alerts
description: Provide contextual feedback messages for typical user actions with the handful of available and flexible alert messages.
group: components
toc: true
---

## Examples

Alerts are available for any length of text, as well as an optional dismiss button. For proper styling, use one of the eight **required** contextual classes (e.g., `.alert-success`). For inline dismissal, use the [alerts jQuery plugin](#dismissing).

<div class="alert toast alert-danger" role="alert">
  <i class="fa fa-exclamation-circle"></i>Error message toast.<a href="javascript:;">Action</a>
</div>
<br/>
<div class="alert toast alert-success" role="alert">
  <i class="fa fa-check"></i>Your application has been submitted.<a href="javascript:;">Undo</a>
</div>
<br/>
<div class="alert toast alert-neutral" role="alert">
  Your reservation has been cancelled.<a href="javascript:;">Undo</a>
</div>


<div class="alert alert-success" role="alert">
  <i class="fa fa-check"></i><b>Success!</b> Action completed successfully - Messages Alert.
</div>

<div class="alert alert-primary" role="alert">
  <button type="button" class="close" data-dismiss="alert" aria-label="Close">
    <span aria-hidden="true">&times;</span>
  </button>
  <i class="fa fa-info-circle"></i>Be careful what you believe because is that you will experience, Your belief system is a mechanism which is uniquely yours. It is powered by your desire and controlled by your thoughts and actions. In other words, your success is measured by the strength of god.  
</div>

<div class="alert alert-warning" role="alert">
  <button type="button" class="close" data-dismiss="alert" aria-label="Close">
    <span aria-hidden="true">&times;</span>
  </button>
  <i class="fa fa-exclamation-triangle"></i><b>Warning! Please be careful to proceed the action.</b><br/>
  Sony Laptops Are Still Part Of The Sony Family.<br/>
  <button type="button" class="btn btn-secondary">Secondary</button>
  <button type="button" class="btn btn-secondary">Secondary</button>
</div>

<div class="alert alert-danger" role="alert">
  <button type="button" class="close" data-dismiss="alert" aria-label="Close">
    <span aria-hidden="true">&times;</span>
  </button>
  <i class="fas fa-exclamation-circle"></i><b>Error message.</b><br/>
  <ul>
    <li>Photographs are a way of preserving a moment in out lives for the rest of our lives.</li>
    <li>Many of us have at least been tempted at the flashy array of photo printers.</li>
    <li>if surely seems old fashioned to talk about 35mm film and non-digital cameras in  today's day and non-digital cameras in today's day.</li>
  </ul>
</div>

{% capture example %}
{% for color in site.data.theme-colors %}
<div class="alert alert-{{ color.name }}" role="alert">
  A simple {{ color.name }} alert—check it out!
</div>{% endfor %}
{% endcapture %}
{% include example.html content=example %}

{% include callout-warning-color-assistive-technologies.md %}

### Link color

Use the `.alert-link` utility class to quickly provide matching colored links within any alert.

{% capture example %}
{% for color in site.data.theme-colors %}
<div class="alert alert-{{ color.name }}" role="alert">
  A simple {{ color.name }} alert with <a href="#" class="alert-link">an example link</a>. Give it a click if you like.
</div>{% endfor %}
{% endcapture %}
{% include example.html content=example %}

### Additional content

Alerts can also contain additional HTML elements like headings, paragraphs and dividers.

{% capture example %}
<div class="alert alert-success" role="alert">
  <h4 class="alert-heading">Well done!</h4>
  <p>Aww yeah, you successfully read this important alert message. This example text is going to run a bit longer so that you can see how spacing within an alert works with this kind of content.</p>
  <hr>
  <p class="mb-0">Whenever you need to, be sure to use margin utilities to keep things nice and tidy.</p>
</div>
{% endcapture %}
{% include example.html content=example %}


### Dismissing

Using the alert JavaScript plugin, it's possible to dismiss any alert inline. Here's how:

- Be sure you've loaded the alert plugin, or the compiled Bootstrap JavaScript.
- If you're building our JavaScript from source, it [requires `util.js`]({{ site.baseurl }}/docs/{{ site.docs_version }}/getting-started/javascript/#util). The compiled version includes this.
- Add a dismiss button and the `.alert-dismissible` class, which adds extra padding to the right of the alert and positions the `.close` button.
- On the dismiss button, add the `data-dismiss="alert"` attribute, which triggers the JavaScript functionality. Be sure to use the `<button>` element with it for proper behavior across all devices.
- To animate alerts when dismissing them, be sure to add the `.fade` and `.show` classes.

You can see this in action with a live demo:

{% capture example %}
<div class="alert alert-warning alert-dismissible fade show" role="alert">
  <strong>Holy guacamole!</strong> You should check in on some of those fields below.
  <button type="button" class="close" data-dismiss="alert" aria-label="Close">
    <span aria-hidden="true">&times;</span>
  </button>
</div>
{% endcapture %}
{% include example.html content=example %}

## JavaScript behavior

### Triggers

Enable dismissal of an alert via JavaScript:

{% highlight js %}
$('.alert').alert()
{% endhighlight %}

Or with `data` attributes on a button **within the alert**, as demonstrated above:

{% highlight html %}
<button type="button" class="close" data-dismiss="alert" aria-label="Close">
  <span aria-hidden="true">&times;</span>
</button>
{% endhighlight %}

Note that closing an alert will remove it from the DOM.

### Methods

| Method | Description |
| --- | --- |
| `$().alert()` | Makes an alert listen for click events on descendant elements which have the `data-dismiss="alert"` attribute. (Not necessary when using the data-api's auto-initialization.) |
| `$().alert('close')` | Closes an alert by removing it from the DOM. If the `.fade` and `.show` classes are present on the element, the alert will fade out before it is removed. |
| `$().alert('dispose')` | Destroys an element's alert. |

{% highlight js %}$(".alert").alert('close'){% endhighlight %}

### Events

Bootstrap's alert plugin exposes a few events for hooking into alert functionality.

| Event | Description |
| --- | --- |
| `close.bs.alert` | This event fires immediately when the <code>close</code> instance method is called. |
| `closed.bs.alert` | This event is fired when the alert has been closed (will wait for CSS transitions to complete). |

{% highlight js %}
$('#myAlert').on('closed.bs.alert', function () {
  // do something…
})
{% endhighlight %}
