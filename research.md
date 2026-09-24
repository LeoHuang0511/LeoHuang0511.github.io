---
layout: homepage
title: Research
permalink: /research/
---

# Research

My research interests are centered on artificial intelligence, machine learning, computer vision, and multimedia processing. I am particularly interested in developing computer vision methods for real-world applications.

{% assign projects = site.data.optional_content.research.projects %}
{% if projects.enabled and projects.items.size > 0 %}
## Selected Projects
{% include content-list.html items=projects.items %}
{% endif %}
