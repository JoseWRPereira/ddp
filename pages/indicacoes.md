---
layout: page
title: Indicações
permalink: /indicacoes/
---

# Indicações


## Curta Eletrônica []
{% include alert.html type="primary" content="This is a primary alert" %}

[Curta Eletrônica](curtaeletronica.wordpress.com.br)


<button class="btn btn-danger">
     <i class="fab fa-youtube">
     Curta eletrônica

     </i>
</button>

Welcome to the {{ site.title }} Documentation pages! Here you can quickly jump to a
particular page.

# Buttons

<button class="btn btn-danger">
     Curta eletrônica
     <i class="fab fa-youtube"></i>
     <a href="www.google.com" color="red">CurtaEletrônica</a>
</button>

<!--<button class="btn btn-success">
     <i class="fab fa-youtube"></i>
     .btn-success
</button>
<button class="btn btn-info">.btn-info</button>
<button class="btn btn-secondary">.btn-secondary</button>
<button class="btn btn-primary">.btn-primary</button>
<button class="btn btn-danger">.btn-danger</button>
<button class="btn btn-warning">.btn-warning</button>-->

## Badges


<span class="badge badge-warning">warning-badge</span>
<span class="badge badge-danger">danger-badge</span>
<span class="badge badge-success">success-badge</span>
<span class="badge badge-info">info-badge</span>
<span class="badge badge-secondary">secondary-badge</span>
<span class="badge badge-primary">primary-badge</span>

## Alerts

{% include alert.html
  type="info"
  title="What is an alert?"
  content="An alert is a box that can stand out to indicate important information. You can choose from levels success, warning, danger, info, and primary. This example is an info box, and the code for another might look like this:"
%}


{% include alert.html type="warning" content="This is a warning" %}
{% include alert.html type="danger" content="This alerts danger!" %}
{% include alert.html type="success" content="This alerts success" %}
{% include alert.html type="info" content="This is useful information." %}
{% include alert.html type="primary" content="This is a primary alert" %}
{% include alert.html type="secondary" content="This is a secondary alert" %}
