---
layout: page
title: Blog Archive
permalink: /blog/
---

<h1>All Posts</h1>

<div class="accordion-container">
  {% for category in site.categories %}
    {% assign cat_name = category[0] %}
    <button class="accordion">{{ cat_name }}</button>
    <div class="panel">
      <ul class="post-list">
        {% for post in category[1] %}
          <li>
            <h3><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></h3>
            <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
          </li>
        {% endfor %}
      </ul>
    </div>
  {% endfor %}
</div>
<script>
  document.addEventListener("DOMContentLoaded", function() {
    var acc = document.getElementsByClassName("accordion");
    for (var i = 0; i < acc.length; i++) {
      // Create and append icon element
      var icon = document.createElement("i");
      icon.className = "fas fa-chevron-down icon";
      acc[i].appendChild(icon);

      acc[i].addEventListener("click", function() {
        this.classList.toggle("active");
        var panel = this.nextElementSibling;
        var icon = this.querySelector('.icon');
        if (panel.style.display === "block") {
          panel.style.display = "none";
          icon.classList.replace('fa-chevron-up', 'fa-chevron-down');
        } else {
          panel.style.display = "block";
          icon.classList.replace('fa-chevron-down', 'fa-chevron-up');
        }
      });
    }
  });
</script>
