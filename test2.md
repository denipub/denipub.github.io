---
layout: page
title: Test2
permalink: /test2/
---

<li>
{% assign url_parts = page.url | split: '/' %}
{% assign url_parts_size = url_parts | size %}
{% assign rm = url_parts | last %}
{% assign base_url = page.url | replace: rm %}

<ul>
{% for node in site.pages %}
  {% if node.url contains base_url %}
    {% assign node_url_parts = node.url | split: '/' %}
    {% assign node_url_parts_size = node_url_parts | size %}
    {% assign filename = node_url_parts | last %}
    {% if url_parts_size == node_url_parts_size and filename != 'index.html' %}
      <li><a href='{{node.url}}'>{{node.title}}</a></li>
    {% endif %}
  {% endif %}
{% endfor %}
  
</li>


<!-- 1st level -->
{% for nav in site.data.menu %}

  {% if nav.sub != null %}

    <li>
      <ul>
        <!-- 2nd level -->
        {% for sub in nav.sub %}
        <li>
          <a href="{{ site.baseurl }}{{ sub.href }}">
            {{ sub.title }}
          </a>
        </li>
        {% endfor %}
      </ul>
    </li>

  {% else %}

    <li>
      <a href="{{ site.baseurl }}{{ nav.href }}">{{ nav.title }}</a>
    </li>

  {% endif %}

{% endfor %}
