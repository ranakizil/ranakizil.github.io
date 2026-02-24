---
layout: default
title: Home
---

# hello, welcome to my blog.

### Recent Posts
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> — {{ post.date | date_to_string }}
    </li>
  {% endfor %}
</ul>
