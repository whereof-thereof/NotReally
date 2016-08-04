---
layout: page
title: Archive
permalink: /archive/
---

{% if posts %}
<ul class="archive">
  {% for post in site.posts %}
    {% unless post.next %}
      <h3 class="mono">{{ post.date | date: '%Y' }}</h3>
    {% else %}
      {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h3 class="mono">{{ post.date | date: '%Y' }}</h3>
      {% endif %}
    {% endunless %}
    <li>
      <span class="mono">{{ post.date | date:"%d&nbsp;%b" }}</span>&nbsp;
      {% if post.platform %}
        <a href="{{ post.exturl }}">"{{ post.title }}"</a>
      {% else %}
        <a href="{{ post.url }}">"{{ post.title }}"</a>
      {% endif %}
      {% if post.type %}<span class="grey"> //{{ post.type }}</span>{% endif %}
      {% if post.platform %}<span class="grey">/{{ post.platform }}</span>{% endif %}
      <br>
      <em>
        {% if post.subtitle %}
          {{ post.subtitle }}
        {% else %}
          {{ post.content | strip_html | truncatewords:35 }}
        {% endif %}
      </em>
    </li>
  {% endfor %}
</ul>
{% else %}
{% include empty.html %}
{% endif %}
