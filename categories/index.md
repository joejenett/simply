---
layout: default
permalink: /categories/
title: Categories
---


<div class="home">
{%- if page.title -%}
    <h1 class="page-heading" style="margin-top:36px;">{{ page.title }}</h1>
  {%- endif -%}
{% assign sorted_categories = site.categories | sort %}
{% for category in sorted_categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <p></p>

    <a name="{{ category_name | slugize }}"></a>
    <h3 class="category-head">{{ category_name }}</h3>
    {% for post in site.categories[category_name] %}
    {% if post.title != "" %}
    <article class="archive-item">
      <li><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a> <span><small>({{ post.date | date:'%b %-d, %Y'}})</small></span> &nbsp; </li>
    </article>
    {% endif %}
        {% if post.title == "" %}
    <article class="archive-item">
      <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.content | strip_html | truncatewords:6 }}</a> <span><small>({{ post.date | date:'%b %-d, %Y'}})</small></span> &nbsp; </li>
    </article>
    {% endif %}
    {% endfor %}
  </div>
{% endfor %}
</div>
<p style="margin-top:48px;" class="rss-subscribe">subscribe <a href="{{ "/feed.atom" | relative_url }}">via RSS</a></p>
