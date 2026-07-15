---
layout: default
title: "Laravel projects"
---

<p>A curated list of Laravel projects from the GitHub account <strong>JOHNBSE</strong>. Click a project to read more.</p>

<ul>
{% for project in site.projects %}
  <li>
    <h2><a href="{{ project.repo_url }}">{{ project.title }}</a></h2>
    <p>{{ project.excerpt }}</p>
    <p><img src="{{ project.image }}" alt="{{ project.title }} screenshot" style="max-width:360px;border-radius:8px;border:1px solid #e5e7eb"/></p>
    <p><a href="{{ project.url }}">Read more</a></p>
  </li>
{% endfor %}
</ul>
