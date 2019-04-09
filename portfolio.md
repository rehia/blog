---
layout: default
author: Jérôme
title: Portfolio
---

Ce portfolio référence les conférences que j'ai eu l'occasion de donner. J'y ai mis les vidéos quand elles existaient, et les slides quand je les ai retrouvés :) 

{% assign confs = site.posts | where: "type","conf" %}
{% for conf in confs %}
# {{ conf.title }} 

{{ conf.description }}

### Abstract

{{ conf.content }}

### Vidéo

{% if conf.video == 'youtube' %}
<iframe width="560" height="315" src="https://www.youtube.com/embed/{{ conf.youtube-id }}" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
{% else %}
Pas de vidéo ! ¯\\\_(ツ)\_/¯
{% endif %}

### Slides

{% if conf.slides %}
[{{ conf.slides }}]({{ conf.slides }})
{% else %}
Pas de slides ! ¯\\\_(ツ)\_/¯
{% endif %}
* * *
{% endfor %}

