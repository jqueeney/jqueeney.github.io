---
permalink: /
title: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

{% include base_path %}

<style>body {text-align: justify}</style>

I am a Postdoctoral Research Fellow at [Mitsubishi Electric Research Laboratories](https://merl.com/), and a Research Affiliate at MIT in the [Aerospace Controls Laboratory](https://acl.mit.edu/). 

I am interested in developing **reliable, data-driven algorithms for decision making and control**. In order to trust that data-driven methods will deliver reliable performance in complex real-world applications, my research focuses on the need for **robustness**, **safety**, and **generalization**. I primarily explore these topics in the context of deep reinforcement learning, imitation learning, and self-supervised learning, with applications in robotics.

I received my PhD in systems engineering from Boston University, where I was advised by Yannis Paschalidis and Christos Cassandras. I also hold a MS in systems engineering from Boston University, and a BA in mathematics and mathematical economics from Colgate University.



{% assign show_news = false %}
{% capture last_date %}{{site.news.last.date | date: '%s'}}{% endcapture %}
{% capture oldest_date %}{{site.announcements.oldest_news | date: '%s'}}{% endcapture %}

{% if last_date >= oldest_date and site.announcements.enabled %}
  {% assign show_news = true %}
{% endif %}

{% if show_news %}
## Selected News
{% include news.html %}
{% endif %}



{% assign show_publications = false %}
{% for post in site.publications reversed %}
  {% if post.featured %}
    {% assign show_publications = true %}
  {% endif %}
{% endfor %}

{% if show_publications %}
## Selected Publications

Check out the [Publications](/publications/) page for a full list of my publications.

{% for post in site.publications reversed %}
  {% if post.featured %}
    {% include publication-single.html %}
  {% endif %}
{% endfor %}

{% endif %}