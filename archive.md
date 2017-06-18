---
layout: page
title: Archive
permalink: /archive/
---

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
