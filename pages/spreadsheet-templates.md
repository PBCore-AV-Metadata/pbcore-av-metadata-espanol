---
title: Spreadsheet Templates
layout: default
section: Resources
permalink: /spreadsheet-templates
keywords: ["Resources", "Tools", "Inventory", "Cataloging", "Spreadsheet Templates"]
---

<div class="row">
  <div class="col-md-12">

    <h2 class="title red bold">Plantillas de Hojas de Cálculo</h2>
  </div>
</div>

<div class="row">
  <div class="col-md-6 index-text">
    Las plantillas de hoja de cálculo de PBCore pueden usarse para registrar metadatos en un formato simple y legible por humanos, a la hora de crear un inventario de activos y/o instanciaciones.
  </div>

  <div class="col-md-6">
    <a href="{{site.url}}/tutorials">
      <button type="button" class="pb-button pb-button-who" name="button">TUTORIAL</button>
    </a>
  </div>
</div>

<div class="row" style="margin-top:4%;">
  <div class="col-md-3"></div>

  <div class="col-md-9">

    {% for block in site.data.spreadsheets %}
      <a href="{{ site.url }}{{ block.download }}" download>
        <span class="spread-title white dark-grey-back med-text">
          <img src="/assets/images/icons/download.png" alt="" style="max-width: 4%;">
          {{ block.title }}
        </span>
      </a>
      <span class="spread-body">
        {{ block.text | markdownify }}
      </span>
    {% endfor %}
  </div>
</div>
