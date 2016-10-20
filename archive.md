---
layout: default
title: Archivo
description: Navegar a través de todos los artículos que he escrito hasta ahora.
permalink: /archivo/
---

<ul class="archive-list">
{% for post in site.posts %}
{% unless post.next %}
  <li class="archive-list--heading">
    <h2>{{ post.date | date: '%Y' }}</h2>
  </li>
{% else %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
  {% if year != nyear %}
  <li class="archive-list--heading">
    <h2>{{ post.date | date: '%Y' }}</h2>
  </li>
  {% endif %}
{% endunless %}
<li class="archive-list--item">
  <a href="{{ post.url }}">{{ post.title | xml_escape }}</a>
  <time datetime="{{ post.date | date: "%Y-%m-%d" }}" class="post__time">
    <small>{{ post.date | date_to_string }}</small>
  </time>
</li>
{% endfor %}
</ul>
