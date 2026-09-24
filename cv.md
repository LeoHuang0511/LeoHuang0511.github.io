---
layout: homepage
title: CV
permalink: /cv/
---

# Curriculum Vitae

{% if site.cv_link %}<p><a class="button" href="{{ site.cv_link | relative_url }}">Download CV (PDF)</a></p>{% endif %}

{% assign cv = site.data.optional_content.cv %}
{% include cv-section.html title="Education" section=cv.education %}
{% include cv-section.html title="Experience" section=cv.experience %}
{% include cv-section.html title="Awards" section=cv.awards %}
{% include cv-section.html title="Talks" section=cv.talks %}
{% include cv-section.html title="Teaching" section=cv.teaching %}
{% include service-section.html %}
