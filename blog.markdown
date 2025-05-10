---
layout: page
title: Blog Archive
permalink: /blog/
---

<h1>All Posts</h1>

<div class="accordion-container">
  {% for category in site.categories %}
    {% assign cat_name = category[0] %}
    {%- capture display_cat_name -%}
      {%- assign name_parts = cat_name | replace: "-", " " | split: " " -%}
      {%- for part in name_parts -%}
        {{ part | capitalize }}{%- unless forloop.last -%} {{ " " }}{%- endunless -%}
      {%- endfor -%}
    {%- endcapture -%}
    <button class="accordion">{{ display_cat_name | strip }}</button>
    <div class="panel">
      <div class="panel-content"> 
        <ul class="post-list">
          {% for post in category[1] %}
          <li>
            <h3><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></h3>
            <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
          </li>
        {% endfor %}
      </ul>
      </div> 
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
      
      // Initialize panel as closed
      var panel = acc[i].nextElementSibling;
      // panel.style.display = "none"; // Old: using display property
      panel.style.maxHeight = null; // New: use max-height for animation, CSS handles initial closed state (max-height: 0)

      acc[i].addEventListener("click", function() {
        this.classList.toggle("active");
        var panel = this.nextElementSibling;
        var icon = this.querySelector('.icon');
        
        // Toggle icon rotation using CSS class
        if (this.classList.contains('active')) {
          icon.classList.add('rotated');
        } else {
          icon.classList.remove('rotated');
        }
        
        // Toggle panel visibility with max-height animation
        if (panel.style.maxHeight && panel.style.maxHeight !== "0px") { // If maxHeight is set (i.e., panel is open)
          panel.style.maxHeight = null; // Close it by resetting to CSS default (max-height: 0)
        } else {
          // panel.scrollHeight includes padding and border of the content, if box-sizing is content-box.
          // For .panel-content, scrollHeight will be its content's actual height.
          panel.style.maxHeight = panel.scrollHeight + "px"; // Open it by setting max-height to its content height
        }
      });
    }
  });
</script>
