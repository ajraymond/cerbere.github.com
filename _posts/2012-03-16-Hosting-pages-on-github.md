---
title: Hosting pages on Github
layout: post
category: web_tutorials
---

Github uses the Jekyll framework to host pages.

## About ##
This post details the [Jekyll][] framework, which can be used --- among other things --- to host your website on Github.

## Details ##
Jekyll generates static pages from a framework which separates the contents (handled by a markup language) and the templates (handled by [Liquid][]).


### Markup ###
Jekyll supports a variety of markup languages, such as [Markdown][] and [Textile][]. As long as a file contains a [YAML][] header, it will be processed by Jekyll. This header defines variables which can be accessed from the templates. Some are built in, like "layout" and "permalink", whereas others can be defined by the user. Those fields are accessed in the template using \{\{ foo \}\}.

### Liquid ###
Jekyll adds a [few extensions][Jekyll extensions] to that, which can be used in the template files.

- See [Liquid for designers] for more information about how Liquid markup works. 

### Directory structure ###
A sample directory structure looks like this:
> * *\_config.yml*: a global YAML configuration file. Some variables in this file are used to configure Jekyll's behavior whereas others can be passed directly to the templates. The configuration variables include "auto", "pygments", etc.
> * *\_posts/*: the contents of the website, in a variety of markup languages
> * *\_layout/*: the Liquid layouts

### Useful to know ###
A file has to be named YYYY-MM-DD-title.ext in order to be recognized by Jekyll
as a valid post. That doesn't mean that other files won't get processed by the
templating engine, quite the contrary! Any file containing the YAML header will
get processed, but it will not become a post, and you won't be able to refer to
it from the posts variables.

You can iterate over all posts belonging to a category as follows:
{% highlight python %}
for post in site.categories.mycategory
{% endhighlight %}

or over all posts containing a given tag:
{% highlight python %}
for post in site.tags.mytag
{% endhighlight %}

or, more globally, over all posts:
{% highlight python %}
for post in site.posts
{% endhighlight %}

### Generating the pygments CSS ###
{% highlight bash %}
pygmentize -f html -S colorful -a .highlight > syntax.css
{% endhighlight %}

Pygments supports highlighting of [several languages][Pygments languages].
[Jekyll]: https://github.com/mojombo/jekyll
[Jekyll extensions]: https://github.com/mojombo/jekyll/wiki/liquid-extensions
[Liquid]: https://github.com/Shopify/liquid/wiki
[YAML]: https://github.com/mojombo/jekyll/wiki/yaml-front-matter
[Liquid for designers]: https://github.com/Shopify/liquid/wiki/Liquid-for-Designers
[Markdown]: http://daringfireball.net/projects/markdown
[Pygments languages]: http://pygments.org/languages/
[Textile]: http://textile.thresholdstate.com
