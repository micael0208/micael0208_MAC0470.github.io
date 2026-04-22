---
layout: home
title: Home
---

# Diário de Desenvolvimento - Kernel Linux

Esse é meu diário de aprendizado em desenvolvimento de kernel Linux.

## Tutoriais

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}
