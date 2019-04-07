---
layout: default
---

{% for post in site.posts %}
<div class="row">
  <h1>
    <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
  </h1>
  <small>{{ post.date }}</small>
  <p>{{ post.excerpt }}</p>
  <a href="{{ site.baseurl }}{{ post.url }}">Lire le post...</a>
</div>
{% endfor %}

