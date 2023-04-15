---
layout: default
title: Cheatsheets
tags: cheatsheet
---

<ul>
{% for page in site.pages %}
 {% if page.path contains 'cheatsheets/' %}
   {% if page.title != "Cheatsheets" %}
    <li><a href="{{ page.url }}">{{ page.title }}</a></li>
  {% endif %}
  {% endif %}
{% endfor %}
</ul>

