---
layout: homepage
title: Home
description: Feng-Kai (Leonel) Huang's academic homepage.
---

# About Me

Feng-Kai (Leonel) Huang is a Ph.D. student in Computer Science and Information Engineering at National Taiwan University (NTU), where he is a member of the Communications and Multimedia Laboratory ([CMLab](https://www.cmlab.csie.ntu.edu.tw/new_cml_website/index.php)) in the Artificial Intelligence and MultiMedia ([AIMM](https://aimm.cmlab.csie.ntu.edu.tw/index.html)) Research Group. His research is supervised by Prof. [Wen-Huang Cheng](https://www.csie.ntu.edu.tw/~wenhuang/) and Prof. [Hong-Han Shuai](https://basiclab.lab.nycu.edu.tw/). His consistent academic excellence is highlighted by his induction into the Phi Tau Phi Scholastic Honor Society twice during his undergraduate and master's studies.

His research interests are centered on artificial intelligence, machine learning, computer vision, and multimedia processing. He is passionate about developing algorithms to solve real-world challenges in computer vision, with publications in international conferences such as ACM MM, ICCV, WACV, and ICIP. He is open to potential research collaborations.

## Research Interests

Computer vision, artificial intelligence, machine learning, and multimedia processing.

{% assign news = site.data.optional_content.news %}
{% if news.enabled and news.items.size > 0 %}
## News
{% include content-list.html items=news.items %}
{% endif %}

## Selected Publications

{% include publication-list.html limit=3 %}

<p class="more-link"><a href="{{ '/publications/' | relative_url }}">All publications →</a></p>
