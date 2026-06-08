---
title: "Publications"
permalink: /publications/
author_profile: true
---



{% assign last_updated = "2026-06-07" | date: "%b %Y" %}
{% assign show_preprints_first = false %}

{% if page.author and site.data.authors[page.author] %}
  {% assign author = site.data.authors[page.author] %}{% else %}{% assign author = site.author %}
{% endif %}


*Updated {{ last_updated }}*

{% if author.googlescholar %}
  For the most up-to-date list of publications, please visit my <a href="{{author.googlescholar}}">Google Scholar page</a>.
{% endif %}


{% include base_path %}

{% assign show_preprints = false %}
{% for post in site.publications reversed %}
  {% if post.status == "preprint" %}
    {% assign show_preprints = true %}
  {% endif %}
{% endfor %}

{% if show_preprints %}
{% if show_preprints_first %}
## Preprints

{% for post in site.publications reversed %}
  {% if post.status == "preprint" %}
    {% if post.include_on_website %}
      {% include publication-single.html %}
    {% endif %}
  {% endif %}
{% endfor %}

{% endif %}
{% endif %}

## Peer-Reviewed Publications

{% for post in site.publications reversed %}
  {% if post.status == "published" or post.status == "to appear" or post.status == "accepted" %}
    {% unless post.type == "dissertation" %}
      {% if post.include_on_website %}
        {% include publication-single.html %}
      {% endif %}
    {% endunless %}
  {% endif %}
{% endfor %}

{% if show_preprints %}
{% if show_preprints_first == false %}
## Preprints

{% for post in site.publications reversed %}
  {% if post.status == "preprint" %}
    {% if post.include_on_website %}
      {% include publication-single.html %}
    {% endif %}
  {% endif %}
{% endfor %}

{% endif %}
{% endif %}

## Dissertation

{% for post in site.publications reversed %}
  {% if post.type == "dissertation" %}
    {% if post.include_on_website %}
      {% include publication-single.html %}
    {% endif %}
  {% endif %}
{% endfor %}