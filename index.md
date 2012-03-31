---
layout: page
title: My little corner of the web
tagline: Also an extension of my brain
---
{% include JB/setup %}

## My posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

