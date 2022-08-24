---
title: PBCore Handbook
layout: default
section: Resources
permalink: /handbook
keywords: ["Resources", "Getting Started", "Cataloging", "Introduction"]
---
<div class="row">
  <div class="col-md-12">

    <h2 class="title red bold">Manual de PBCore</h2>
  </div>
</div>

<div class="row">
  <div class="col-md-12 index-text">
    El Manual de PBCore compila la mayor parte de la documentación sobre PBCore que se encuentra disponible en este sitio web en formato de PDF descargable. Dado que la documentación abarca muchos temas, ponemos a disposición tanto archivos separados descargables para cada sección, como también una versión completa.
  </div>
</div>

<div class="row" style="margin-top:4%;">
  <div class="col-md-3"></div>

  <div class="col-md-9">

    {% for block in site.data.handbook %}
      <a href="{{ site.url }}{{ block.filepath }}" download>
        <span class="spread-title white dark-grey-back med-text">
          <img src="/assets/images/icons/download.png" alt="" style="max-width: 4%;">
          {{ block.title }}
        </span>
      </a>
      <span class="spread-body">
        {{ block.description | markdownify }}
      </span>
    {% endfor %}
  </div>
</div>
