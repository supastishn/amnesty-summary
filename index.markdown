---
layout: post
title: Latest Post
permalink: /
---

{% assign first_post = site.posts.last %}
<div class="home">
  {% if site.posts.size > 0 %}
    {{ first_post.content }}
  {% else %}
    <p>No posts yet. Check back soon!</p>
  {% endif %}
</div>
