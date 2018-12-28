---
layout: inner
title: Posts
permalink: /posts/
---

<!--
<div class="tags-expo">
  <div class="tags-expo-list">
    {% assign sorted_tags = site.tags | sort %}
    {% for tag in sorted_tags %}
      <a href="#{{ tag[0] | slugify }}" class="post-tag">{{ tag[0] }}</a>
    {% endfor %}
  </div>
  <hr/>
  -->

  <div class="tags-expo-section">
    {% assign sorted_tags = site.tags | sort %}
    {% for tag in sorted_tags %}
      <h2 id="{{ tag[0] | slugify }}">{{ tag | first }}</h2>
      <ul class="tags-expo-posts">
        {% for post in tag[1] %}
        <a class="post-title" href="{{ site.baseurl }}{{ post.url }}">
        <li>
          {{ post.title }}
        </li>
        </a>
        {% endfor %}
      </ul>
    {% endfor %}
  </div>
