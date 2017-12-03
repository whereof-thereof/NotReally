---
layout: page
title: Archive
permalink: /archive/
---

<ul class="archive">
  {% for page in site.pages %}
    {% if page.subtitle %}
      <li>
        <h3><a href="{{ page.url }}">"{{ page.title }}"</a></h3>
        {% if page.subtitle %}
          {{ page.subtitle }}
        {% endif %}
      </li>
    {% endif %}
  {% endfor %}
</ul>
{% if site.posts %}
<ul class="archive">
  {% for post in site.posts %}
    {% unless post.next %}
      <h2 class="mono">{{ post.date | date: '%Y' }}</h2>
    {% else %}
      {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h2 class="mono">{{ post.date | date: '%Y' }}</h2>
      {% endif %}
    {% endunless %}
    <li>
      {% include postItem.html %}
    </li>
  {% endfor %}
</ul>
{% else %}
{% include empty.html %}
{% endif %}
