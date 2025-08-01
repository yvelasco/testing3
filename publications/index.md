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

## Publications Related To This Project’s Core Scope

These publications align with the central aims of this project. They showcase the key findings and innovations that this project is contributing to the field of computer science education:

{% for doi in grant_citations %}
  {% include citation.html lookup=doi style="rich" %}
{% endfor %}

{% include section.html %}

## Additional Publications

The following works reflect other contributions from our research team that, while outside the immediate scope of this project, provide valuable context and complementary insights.

{% comment %} Trim grant DOIs {% endcomment %}
{% assign trimmed_grant_dois = "" | split: "" %}
{% for doi in grant_citations %}
  {% assign trimmed = doi | strip %}
  {% assign trimmed_grant_dois = trimmed_grant_dois | push: trimmed %}
{% endfor %}

{% comment %} Now filter all_citations into non_grant_citations {% endcomment %}
{% assign non_grant_citations = "" | split: "" %}
{% for citation in all_citations %}
  {% unless trimmed_grant_dois contains citation.id %}
    {% assign non_grant_citations = non_grant_citations | push: citation %}
  {% endunless %}
{% endfor %}

{% include search-box.html %}
{% include search-info.html %}

{% comment %} Show non-grant-specific publications {% endcomment %}
{% for item in non_grant_citations %}
  {% include citation.html lookup=item.id style="rich" %}
{% endfor %}
