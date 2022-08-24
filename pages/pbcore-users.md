---
title: PBCore Case Studies
layout: default
section: Community
permalink: /pbcore-users
keywords: ["Community", "Learning Tools", "Case Studies"]
---


<h2 class="title dark-grey">PBCore Case Studies</h2>

Si bien no es una lista comprehensiva de todos los usuarios de PBCore, esta página incluye ejemplos del mundo real de cómo varias instituciones encuentran valor en implementar PBCore – como estructura subyacente para una base de datos, formato de importación/exportación, modelo conceptual y más. Si está interesado en contribuir con un estudio de caso para resaltar cómo su institución implementa PBCore, contáctenos en PBCoreInfo@wgbh.org. 

<section id="pbcore-users" class="" style="margin-bottom: 4%; background-color: #ddd;">

  <div class="row">

      <div class="col-md-6">
        <ul class="pb-list">
          {% for item in site.data.pbcore_users.users %}
            {% if item.column == 'left' %}
              <li>
                <a href="#{{ item.id }}">
                  <p class="pb-user-list">{{ item.user }}</p>
                </a>
              </li>
            {% endif %}
          {% endfor %}
        </ul>
      </div>

      <div class="col-md-6">
        <ul class="pb-list">
          {% for item in site.data.pbcore_users.users %}
            {% if item.column == 'right' %}
              <li>
                <a href="#{{ item.id }}">
                  <p class="pb-user-list">{{ item.user }}</p>
                </a>
              </li>
            {% endif %}
          {% endfor %}
        </ul>
      </div>

  </div>

</section>

<hr>

{% for item in site.data.pbcore_users.users %}
  <div class="row">
    <div class="col-md-12">
      <img id="{{ item.id }}" style="width: 100%; display: block; border: 2px solid black;" src="/assets/images/{{ item.logo-file }}" alt="{{item.user}} logo">
    </div>
  </div>

  <div class="row" style="margin-bottom: 5%;margin-top: 3%;">
    <div class="col-md-1">
    </div>
    <div class="col-md-10">
      <h3 class="bold">{{ item.title }}</h3>
          <p>{{ item.statement}}</p>
    </div>
    <div class="col-md-1">
    </div>
  </div>
{% endfor %}
