---
layout: post
title: Latest Post
permalink: /
---

{% assign first_post = site.posts.last %}
{% assign earliest_post = site.posts[-1] %}
<div class="home">
  {% if site.posts.size > 0 %}
    {{ first_post.content }}
  {% else %}
    <p>No posts yet. Check back soon!</p>
  {% endif %}

  {% if site.posts.size > 1 %}
    <div style="margin-top: 2em; text-align: center;">{% comment %} Changed to earliest post {% endcomment %}
      <a href="{{ earliest_post.url | relative_url }}" class="button">Read the Earliest Post &raquo;</a>
    </div>
  {% endif %}
</div>
