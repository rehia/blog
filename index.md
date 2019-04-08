---
layout: default
---

{% assign blogposts = site.posts | where: "type","blogpost" %}
{% for post in blogposts %}
<div class="row" style="margin-bottom: 30px;">
  <h1>
    <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
  </h1>
  <small>{{ post.date | date_to_long_string }}</small>
  <p>{{ post.excerpt }}</p>
  <a href="{{ site.baseurl }}{{ post.url }}">Lire le post...</a>
  <hr />
</div>
{% endfor %}

