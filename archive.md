---
permalink: /archive
layout: page
title: Архив новостей
---
<ul>
  {% for post in site.posts %}
    <li>
      <a href=".{{ post.url }}"><b>{{ post.date | date: "%Y-%m-%d" }}</b> {{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
