---
layout: page
permalink: /publications/
title: Publications
description:
years: [2021,2019]
nav: true
---

<div class="publications">
[Google Scholar](https://scholar.google.com/citations?user=nT2T8M4AAAAJ&hl=en)

{% for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
