---
layout: page
title: projects
permalink: /projects/
description: 
nav: true
nav_order: 3
display_categories: [Academic]
horizontal: false
---

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-1">
    {% for project in sorted_projects %}
      <!-- {% include projects_horizontal.liquid %} -->
      <div>
        <h2><a href="#">{{ project.title }}</a></h2>
        <p>{{ project.description | markdownify}}</p>
        {% for repo in project.repositories %}
          <div>
            <a href="{{ repo.url }}" target="_blank">{{ repo.name }}</a>
          </div>
        {% endfor %}
      </div>
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-1">
    {% for project in sorted_projects %}
      <div>
        <h2><a href="#">{{ project.title }}</a></h2>
        <p>{{ project.description | markdownify}}</p>
        {% for repo in project.repositories %}
          <div>
            <a href="{{ repo.url }}" target="_blank">{{ repo.name }}</a>
          </div>
        {% endfor %}
      </div>
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-1">
    {% for project in sorted_projects %}
      <div>
        <h2><a href="#">{{ project.title }}</a></h2>
        <p>{{ project.description | markdownify }}</p>
        {% for repo in project.repositories %}
          <div>
            <a href="{{ repo.url }}" target="_blank">{{ repo.name }}</a>
          </div>
        {% endfor %}
      </div>
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-1">
    {% for project in sorted_projects %}
      <div>
        <h2><a href="#">{{ project.title }}</a></h2>
        <p>{{ project.description | markdownify }}</p>
        {% for repo in project.repositories %}
          <div>
            <a href="{{ repo.url }}" target="_blank">{{ repo.name }}</a>
          </div>
        {% endfor %}
      </div>
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
