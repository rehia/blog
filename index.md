---
layout: default
---

{% for post in site.posts %}
<div class="row">
  <h1>{{ post.title }}</h1>
  <small>{{ post.date }}</small>
  <p>{{ post.excerpt }}</p>
  <a href="{{ post.url }}">Lire le post...</a>
  </div>
{% endfor %}

