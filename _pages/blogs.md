---
title: "Blog"
layout: page
sitemap: false
permalink: /blogs/
---

<ul>
  {% for post in site.posts %}
    <li> 
      <h5>{{ post.date | date_to_string }}: <a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}">{{ post.title}}</a> </h5>
    </li>
  {% endfor %}
</ul>
