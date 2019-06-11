---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% include base_path %}

{% if page.author and site.data.authors[page.author] %}
  {% assign author = site.data.authors[page.author] %}{% else %}{% assign author = site.author %}
{% endif %}

{% if author.googlescholar %}
  <li><a href="{{ author.googlescholar }}"><i class="fas fa-graduation-cap"></i> Google Scholar</a></li>
{% endif %}

{% if author.researchgate %}
 <li><a href="{{ author.researchgate }}"><i class="fab fa-researchgate" aria-hidden="true"></i> ResearchGate</a></li>
{% endif %}

{% if author.pubmed %}
  <li><a href="{{ author.pubmed }}"><i class="ai ai-pubmed-square ai-fw"></i> PubMed</a></li>
{% endif %}
{% if author.orcid %}
  <li><a href="{{ author.orcid }}"><i class="ai ai-orcid-square ai-fw"></i> ORCID</a></li>
{% endif %}

{% if author.impactstory %}
  <li><a href="{{ author.impactstory }}"><i class="ai ai-impactstory ai-fw"></i> Impactstory</a></li>
{% endif %}

<!-- {% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %} -->

<!-- {% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
 -->

<ul>{% for post in site.publications %}
  {% include archive-single-cv.html %}
{% endfor %}</ul>
