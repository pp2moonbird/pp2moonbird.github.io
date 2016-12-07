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
  <a name="{{ category | first}}"> {{category | first}}</a>
  <ul>
  {% for posts in category %}
    {% for post in posts %}
      {% if post.url %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
        <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </li>
      {% endif %}
    {% endfor %}
  {% endfor %}
  </ul>
</h4>

{% endfor %}
