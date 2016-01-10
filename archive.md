---
layout: page
title: Archive
permalink: /archive/
---

<ul>
  {% for post in site.posts %}

    {% unless post.next %}
      <h3>{{ post.date | date: '%Y' }}</h3>
    {% else %}
      {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h3>{{ post.date | date: '%Y' }}</h3>
      {% endif %}
    {% endunless %}

    <li>{{ post.date | date:"%d&nbsp;%b" }} &raquo; <a href="{{ post.url }}">{{ post.title }}</a>{% if post.type %}<span class="grey"> //{{ post.type }}</span>{% endif %}</li>
  {% endfor %}
</ul>
