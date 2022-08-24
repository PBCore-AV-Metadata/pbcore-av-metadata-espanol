---
title: PBCore XML Schema
layout: default
section: Schema
permalink: /xsd
keywords: ["Schema", "Elements", "Attributes", "XML", "Structure", "Revisions", "GitHub"]
---

<h2 class="green title bold">Esquema XML de PBCore</h2>

PBCore es un estándar de metadatos diseñado para describir activos de medios, tanto digitales como analógicos. La definición de esquema XML de PBCore (XSD) define la estructura y el contenido de PBCore. La versión actual (PBCore 2.1) se puede ver en nuestro [repositorio de GitHub](https://github.com/PBCore-AV-Metadata/PBCore_2.1/) o puede <a href="/assets/downloads/PBCore_2.1-master.zip" download>descargar</a> el archivo .xsd.

PBCore 2.1 fue creado por la comunidad de televisión pública en los Estados Unidos de América para uso de las emisoras públicas y otros. PBCore se basa en Dublin Core (ISO 15836), un estándar internacional para el descubrimiento de recursos. PBCore fue desarrollado con fondos proporcionados por la Corporation for Public Broadcasting (Corporación para la Televisión Pública) y es mantenido por WGBH con el apoyo y la orientación del AMIA PBCore Advisory Sub-Committee (Subcomité Asesor de AMIA PBCore).

<h3>Estructura</h3>

PBCore 2.1 se compone de 15 contenedores y 82 elementos, y utiliza 49 atributos XML. Los atributos se utilizan para calificar o describir aún más los elementos y sus valores. No todos los atributos se pueden utilizar para describir todos los elementos. En este sitio, cada elemento tiene una página que describe qué atributos se pueden usar con ese elemento.

Dentro de un documento XML de PBCore, el XSD determina el orden y la estructura de los elementos. Los elementos deben incluirse en el orden correcto, o el documento XML no se validará. Puede encontrar una lista del orden correcto de los subelementos en PBCore en la página [Jerarquía de elementos]({{ site.url }}/elements-hierarchy).

Para obtener un glosario de términos utilizados en el esquema PBCore, visite la página [Glosario]({{ site.url }}/glossary) en este sitio.

<h3>Revisiones de PBCore 2.0 a PBCore 2.1</h3>

PBCore 2.1 es una actualización incremental del esquema de PBCore 2.0 que proporciona definiciones de elementos más claras y más opciones para incluir información de origen detallada para los metadatos, sin dejar de ser compatible con versiones anteriores de PBCore 2.0.

Los cambios para 2.1 incluyen:
<p>1. La opción de incluir información de '@fuente, @ref, @versión, @anotación' en todos los elementos.</p>
<p>2. La adición de nuevos grupos de atributos opcionales para los siguientes elementos:</p>
<p>para pbcoreTitle:</p>
- <span>@titleTypeSource</span>
- <span>@titleTypeRef</span>
- <span>@titleTypeVersion</span>
- <span>@titleTypeAnnotation</span>
<p>para pbcoreSubject:</p>
- <span>@subjectTypeSource</span>
- <span>@subjectTypeRef</span>
- <span>@subjectTypeVersion</span>
- <span>@subjectTypeAnnotation</span>
<p>para pbcorePart:</p>
- <span>@partType</span>
- <span>@partTypeSource</span>
- <span>@partTypeRef</span>
- <span>@partTypeVersion</span>
- <span>@partTypeAnnotation</span>
<p>para creator, contributor y publisher:</p>
- <span>@affiliationSource</span>
- <span>@affiliationRef</span>
- <span>@affiliationVersion</span>
- <span>@affiliationAnnotation</span>
<p>3. La adición de un atributo @unitofmeasure al elemento “essenceTrackBitDepth”</p>
<p>4. El cambio de los elementos “instantiationLanguage” and “essenceTrackLanguage” de no repetible a repetible</p>
<p>5. El cambio del elemento “extensionAuthorityUsed” de requerido a opcional dentro del contenedor “extensionWrap”</p>
<p>6. Definiciones generales actualizadas y mejores prácticas para cada elemento</p>

Para obtener más información sobre el proceso y la justificación detrás del desarrollo de PBCore 2.1, consulte [“Léame”](https://github.com/PBCore-AV-Metadata/PBCore_2.1/blob/master/README.md) en el [repositorio de PBCore 2.1 GitHub.](https://github.com/PBCore-AV-Metadata/PBCore_2.1).
