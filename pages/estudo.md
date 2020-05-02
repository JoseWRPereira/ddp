---
layout: page
title: Estudo
permalink: /docs/
---

# Estudo

Bem vindo ao sítio {{ site.title }} - DdP!!!

Esta é um local de publicação de material de *estudo* nas diferentes áreas de interesse, *Ciência, Tecnologia e Humanidades* com a finalidade de auxiliar o processo de aquisição de *conhecimento* através de sua consolidação em forma de texto, aprimorando a *habilidade* de escrita e mantendo *atitude* positiva, curiosa e resiliente.

<div class="section-index">
    <hr class="panel-line">
    {% for post in site.docs  %}        
    <div class="entry">
    <h5><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h5>
    <p>{{ post.description }}</p>
    </div>{% endfor %}
</div>
