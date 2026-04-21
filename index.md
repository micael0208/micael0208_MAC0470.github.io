---
layout: default
title: Home
---

# Diário de Desenvolvimento - Kernel Linux

Aqui registro minha jornada no curso de Desenvolvimento de Software Livre.

## Posts

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}
