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
  <div style="float: left; margin-right: 20px">
    <a href="{{ author.googlescholar }}"><i class="fas fa-graduation-cap"></i> Google Scholar</a>
  </div>
{% endif %}

{% if author.researchgate %}
  <div style="float: left; margin-right: 20px">
    <a href="{{ author.researchgate }}"><i class="fab fa-researchgate" aria-hidden="true"></i> ResearchGate</a>
  </div>
{% endif %}

{% if author.pubmed %}
  <div style="float: left; margin-right: 20px">
    <a href="{{ author.pubmed }}"><i class="ai ai-pubmed-square ai-fw"></i> PubMed</a>
  </div>
{% endif %}
{% if author.orcid %}
  <div style="float: left; margin-right: 20px">
    <a href="{{ author.orcid }}"><i class="ai ai-orcid-square ai-fw"></i> ORCID</a>
  </div>
{% endif %}

{% if author.impactstory %}
  <div style="float: left; margin-right: 20px">
    <a href="{{ author.impactstory }}"><i class="ai ai-impactstory ai-fw"></i> Impactstory</a>
  </div>
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
