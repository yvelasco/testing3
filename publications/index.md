---
title: Publications
nav:
  order: 2
  tooltip: Published works
---

# {% include icon.html icon="fa-solid fa-book" %}Publications

{% include section.html %}

## Grant-Specific Publications

The following publications are directly linked to this grant's scope and objectives. They showcase the key findings and innovations that this project is contributing to the field of computer science education:

{% include citation.html lookup="https://doi.org/10.1145/3649165.3690130" style="rich" %}

{% include citation.html lookup="https://doi.org/10.1145/3632620.3671099" style="rich" %}

{% include section.html %}

## All Publications by Research Team

These works represent the broader research contributions from our team that have laid the foundation for this project and continue to inform our approach to investigating student help-seeking behaviors:

{% assign raw_highlighted = "https://doi.org/10.1145/3649165.3690130, https://doi.org/10.1145/3632620.3671099" %}
{% assign highlighted_citations = raw_highlighted | split: "," %}


{% assign non_highlighted = site.data.citations %}
{% for doi in highlighted_citations %}
  {% assign trimmed_doi = doi | strip %}
  {% assign non_highlighted = non_highlighted | reject: "id", trimmed_doi %}
{% endfor %}

{% include search-box.html %}

{% include search-info.html %}

{% include list.html data="citations" component="citation" style="rich" %}
