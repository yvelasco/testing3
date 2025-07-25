---
title: Publications
nav:
  order: 2
  tooltip: Published works
---

# {% include icon.html icon="fa-solid fa-book" %}Publications

{% include section.html %}

{% comment %} Grab grant-specific publications and all citations {% endcomment %}
{% assign grant_citations = site.data.grant_citations.grant %}
{% assign all_citations = site.data.citations %}
{% comment %} The variable below will be modified later. {% endcomment %}
{% assign non_grant_citations = all_citations %}

## Grant-Specific Publications

The following publications are directly linked to this grant's scope and objectives. They showcase the key findings and innovations that this project is contributing to the field of computer science education:

{% for doi in grant_citations %}
  {% include citation.html lookup=doi style="rich" %}
{% endfor %}

{% include section.html %}

## All Publications by Research Team

These works represent the broader research contributions from our team that have laid the foundation for this project and continue to inform our approach to investigating student help-seeking behaviors:

{% comment %}
The loop below is roughly equivalent to:
non_grant_citations = [item for item in all_citations if item["id"].strip() not in grant_citations]
Liquid doesn’t mutate in place, so we build a filtered copy instead.
{% endcomment %}

{% for doi in grant_citations %}
  {% assign trimmed_doi = doi | strip %}
  {% assign non_grant_citations = non_grant_citations | reject: "id", trimmed_doi %}
{% endfor %}

{% include search-box.html %}
{% include search-info.html %}

{% comment %} Show non-grant-specific publications {% endcomment %}
{% for item in non_grant_citations %}
  {% include citation.html lookup=item.id style="rich" %}
{% endfor %}
