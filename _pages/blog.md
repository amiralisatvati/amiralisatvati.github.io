---
layout: home
title: "بلاگ"
permalink: /blog/
author_profile: false
---

## آخرین مقالات

{% for post in site.posts %}
<div class="post-card">
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
  <p class="post-meta">
    <small>{{ post.date | date: '%d %B %Y' }} • {% include read-time.html %}</small>
  </p>
  {% if post.excerpt %}
  <p>{{ post.excerpt }}</p>
  {% endif %}
  <a href="{{ post.url }}">مطالعه بیشتر →</a>
</div>
{% endfor %}
