---
layout: archive
permalink: /work/
title: "My Data Science Work"
author_profile: true
excerpt: "Browse Works Below or Go Directly to my GitHub Profile"
header:
  overlay_image: "/assets/ProjectsBackground.jpg"
  overlay_filter: 0.3 # same as adding an opacity of 0.3 to a black background
  actions:
    - label: "My GitHub Profile"
      url: "https://github.com/xanderhieken/"  
---


{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
