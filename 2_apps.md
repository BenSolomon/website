---
layout: inner
title: Apps
permalink: /apps/
---

<div class="home">


    <div class="row pack">

        {% for post in site.posts %}
            {% if post.categories contains "app" %}
            <div class="col-md-4 card">
             <a href="{{ post.project_link }}" class="index-anchor">    
                <div class="panel panel-default">

                  {% if post.featured_image %}
                  <img width="100%" src="{{site.baseurl}}{{post.featured_image}}" alt="{{post.title}}">
                  {% else %}
                  <img width="100%" src="{{site.baseurl}}/images/webjeda-logo-big.jpg" alt="{{site.title}}">
                  {% endif %}

                  <div class="panel-body">
                    <h3 class="panel-title pull-left">{{ post.title }}</h3><span class="post-meta pull-right"><small>{{ post.date | date: "%b %-d, %Y" }}</small></span>
                  </div>

                  <div class="panel-body"><small>
                    {{ post.lead_text | truncate: 180 }}</small>
                  </div>
                </div>
                </a>
            </div>
            {% endif %}

          {% endfor %}

    </div>


</div>
