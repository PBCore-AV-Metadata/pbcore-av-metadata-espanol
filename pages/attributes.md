---
title: Attributes
layout: default
section: Schema
permalink: /attributes
keywords: ["Schema", "Attributes", "XML", "Creating Records"]
---

<span class="definition-icon def-attributes"></span>
<h2 class="green bold">Attributes Defined</h2>

Los atributos son una forma de estructurar tipos adicionales de información que pueden incluir los registros de PBCore. Específicamente, se utilizan para aclarar aún más la información que proporciona valor a un elemento. La siguiente sección proporciona una definición para cada atributo; información de mejores prácticas, donde se encuentra disponible; y una lista de los elementos con los que se puede utilizar ese atributo.

<div id="attributes-defined" class="attribute-list">
  <ul>
    {% for item in site.data.attributes%}
      <li>
        <div class="row">
          <div class="col-md-3">
              <p id="{{ item[0] }}" class="bolder attribute-name">{{ item[0] }}: </p>
          </div>
          <div class="separator col-md-9">
            <p class="definition">{{ item[1].definition }}</p>
            {% if item[1].best-practice %}
              <p class="light"><span class="green bolder">Práctica recomendada:</span> {{ item[1].best-practice}}</p>
            {% endif %}
          </div>
        </div>
        <div class="spacing">
        </div>
      </li>
    {% endfor %}
  </ul>
</div>
