---
layout: page
title: Projects
permalink: /projects/
---

<section class="projects">
  <div class="project-cards">
    {% for project in site.projects %}
      <div class="project-card">
        <h2><a href="{{ project.url }}">{{ project.title }}</a></h2>
        <p>{{ project.description }}</p>
      </div>
    {% endfor %}
  </div>
</section>
