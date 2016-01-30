---
layout: post
post: Site Migration Issues and Solutions
title: Site Migration Issues and Solutions
---

After more than a decade of gathering and sharing my thoughts using a mix of wikis, Wordpress instances and other random solutions, consolidating them into a format that had long-term value, like plain text files, seemed like a great idea. [Jekyll](http://jekyllrb.com/) makes this easy, in large part because the content can then be easily converted to static sites that can be quickly deployed.

Here are some issues I've run into during this migration and the solutions I've found:

### Dates and titles

The built-in filter converts dates to strings that using English month names, e.g. 29 Jan 2016. Given that some of the content on this site is not in English, I modified the code to make use of the more international [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date format using these [helpful directions](http://alanwsmith.com/jekyll-liquid-date-formatting-examples).

{% highlight ruby %}{% raw %}
{{ page.date | date: "%Y-%m-%d" }}
...
{{ post.date | date: "%Y-%m-%d" }}
{% endraw %}{% endhighlight %}

Similarly, how YAML front matter variables are filtered was important since it changed the word case and stripped accented letters. I therefore need to add not only `post` variables, but also `title` variables where necessary.

### Fonts

I decide to use the Lato font family instead of the one used by the [Hyde](http://apod.nasa.gov/apod/ap100721.html) theme, PT Sans. That required including the appropriate CSS includes in the header and removing the older fonts to speed up performance. Another advantage is that Lato goes better with the vintage 1920s Art Deco logo in my opinion.

### Analytics

I decided to use Piwik, a free and open source web analytics solution, instead of the corporate solution. After installing it on piwik.sanfranciscan.org, I incorporated the necessary code snippet into the page fragments and config files using this [as an example](http://minuteware.net/2013-12-22-integrate-piwik-into-jekyll.html). These instructions did not include the `noscript` code, which excludes tracking of visitors without Javascript, but this was resolved using [these instructions](http://piwik.org/faq/how-to/faq_176/). I am still unsure of how accurate Piwik will be with Varnish, the accelerator my host uses, but on first look, there isn't any caching happening, so perhaps I won't have to resolve this issue.

### Next steps

I haven't found a good, ethical solution for comments that I can run on my current host. I also haven't implemented a way to share the content on social media, although I have a [couple](http://ginoclement.com/jekyll/setup/2015/03/14/Jekyll-Configuration-Part-1.html) of [leads](https://github.com/brandonparsons/blog.brandonparsons.me/blob/gh-pages/_layouts/post.html).

I'm looking forward to slowly consolidating the material I've created over the years into one place. I'm also finally using really great artwork I've found over the years, like the logo and the [background image](http://apod.nasa.gov/apod/ap100721.html). It will not be a quick process, but I'm looking forward to it.
