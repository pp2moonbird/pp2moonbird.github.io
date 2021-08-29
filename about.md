---
layout: page
title: About Me
permalink: /about/
---

This is pp's blog. My main focus is Data Analysis, Data visualization. I use Python, Qlikview, QlikSense and Tableau.

I will also share thoughts on games, animations, comic or other interesting stuff.

This site is powered by [Jekyll](http://jekyllrb.com/) and [github-pages](https://pages.github.com/)

## Archive ##

{% for category in site.categories %}
<h4>
  <div id="{{ category | first}}"> {{category | first}}</div>
</h4>
  <ul>
  {% for posts in category %}
    {% for post in posts %}
      {% if post.url %}
      <li>
        <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
        <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </li>
      {% endif %}
    {% endfor %}
  {% endfor %}
  </ul>


{% endfor %}
