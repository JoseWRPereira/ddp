---
layout: page
title: Diferença de Potencial - DdP
permalink: /
icon: logo.svg
---

# Postagens

<p>Assine o <a href="{{ site.baseurl }}/feed.xml">RSS</a> para acompanhar as últimas postagens.

<br>

{% for post in site.posts limit:10 %}
   <div class="post-preview">
   <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>
   <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span><br>
   {% if post.badges %}{% for badge in post.badges %}<span class="badge badge-{{ badge.type }}">{{ badge.tag }}</span>{% endfor %}{% endif %}
   {{ post.content | split:'<!--more-->' | first }}
   {% if post.content contains '<!--more-->' %}
      <a href="{{ site.baseurl }}{{ post.url }}">leia mais </a>
   {% endif %} 
   </div>
   <hr>
{% endfor %}

Quer ver mais? Acesse <a href="{{ site.baseurl }}/archive/">artigos</a>.
