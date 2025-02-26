---
title: PBCore Tutorials
layout: default
section: Resources
permalink: /tutorials
keywords: ["Resources", "Getting Started", "Key Functions", "Tutorials", "Learning Tools", "Creating Records", "Cataloging", "Spreadsheet Templates", "Cataloging Tool", "Controlled Vocabularies", "Extensions"]
---

<h2 class="red title bold">Tutoriales</h2>
<p class="med-text">Estos videotutoriales brindan una introducción a muchos de los conceptos clave de PBCore y una guía sobre los primeros pasos para comenzar a usar las herramientas de PBCore. Estamos creando nuevos tutoriales que publicaremos aquí a la brevedad.</p>
{% assign i = 0 %}
<div class="row">
  <div class="col-10 mx-auto">

    {% for group in site.data.tutorials %}
      <h3 class="red bold">{{group.section}}</h3>
      <p>{{group.description}}</p>
      <div class="accordion" id="tutorial-accordion">

        {% for block in group.tutorials %}
          {% assign i = i|plus:1 %}

          <div class="card">

            <div class="card-header" id="tutorial{{ i }}" style="padding:1em;">
              <span class="collapsed" data-toggle="collapse" href="#tutorial-collapse{{i}}" aria-expanded="false" aria-controls="tutorial-collapse{{i}}">

                <span class="pres-arrow-icon pres-arrow-down"></span>

                <a href="#{{ block.id }}" id="{{ block.id }}">
                  <span class="red">{{ block.title }}</span>
                  <span class="black"> - {{ block.description }}</span>
                </a>
              </span>

            </div>

            <div id="tutorial-collapse{{i}}" class="collapse fade" aria-labelled by="tutorial{{ i }}">
              <div style="margin: 5px;" class="card-body indent-4">
                {{ block.embed }}
              </div>
            </div>

          </div>
        {% endfor %}

      <div>

    {% endfor %}
  </div>
</div>
