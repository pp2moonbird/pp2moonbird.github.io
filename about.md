---
layout: page
title: About
permalink: /about/
---

This is pp's blog. My main focus is Data Analysis, Data visualization. I use Python, Qlikview, QlikSense and Tableau.

I will also share thoughts on games, animations, comic or other interesting stuff.

This site is powered by [Jekyll](http://jekyllrb.com/) and [github-pages](https://pages.github.com/)

## Archive ##

<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

      <h4>
        <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </h4>
    </li>
  {% endfor %}
</ul>
