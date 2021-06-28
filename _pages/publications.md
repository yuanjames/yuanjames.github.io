---
layout: page
permalink: /publications/
title: Publications
description:
years: [2021,2019]
nav: true
---

<div class="publications">
<a href="https://scholar.google.com/citations?user=nT2T8M4AAAAJ&hl=en">Google Scholar</a>

<p style="line-height:1.4">
{% for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}
</p>
</div>
