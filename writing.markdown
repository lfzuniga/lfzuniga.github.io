---
layout: base
title: Writing
# permalink: /writing/
---



<ul class="post-list">
  {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
  {%- for post in site.posts -%} <!-- Change this line -->
    <li class="post-item">
      <span class="post-meta">{{ post.date | date: date_format }}</span>
      <h3 class="post-title">
        <a class="post-link" href="{{ post.url | relative_url }}">
          {{ post.title | escape }}
        </a>
      </h3>
      {%- if site.show_excerpts -%} {{ post.excerpt }} {%- endif -%}
    </li>
  {%- endfor -%}
</ul>