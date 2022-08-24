---
title: PBCore Mappings to Other Standards
layout: default
section: Resources
permalink: /mappings
keywords: ["Resources", "Tools", "Metadata Mapping", "MARC Metadata Standard", "Resource Description Framework (RDF)", "EBUCore", "Extensions", "International Press Telecommunications Council (IPTC)", "Preservation Metadata Implementation Strategies (PREMIS)"]
---

<h2 class="red title bold">Mapeos</h2>

<h3>PBCore y MARC</h3>
La documentación que encontrará aquí abajo provee recomendaciones para hacer conversiones desde el estándar de metadatos de PBCore al Formato para Datos Bibliográficos MARC 21. Puesto que MARC tiene más campos que PBCore, en algunos casos hay múltiples recomendaciones para el mismo elemento de PBCore, según el contexto y el nivel de detalle deseado. La documentación incluye recomendaciones tanto para mapeos simples y complejos. Los campos de MARC 21 están detallados por número de campos con sucampos específicos en los casos en los que es necesario.

Este mapeo incluye todos los elementos de PBCore, pero no incluye todos los atributos posibles para esos elementos. Los mapeos de atributos se incluyen cuando los atributos son necesarios dentro de PBCore, o cuando el mapeo de un atributo permite un mapeo más específico dentro de MARC.

Estos documentos no incluyen recomendaciones para la conversión de MARC 21 a PBCore, pero en algunos casos se pueden usar como una guía para realizar ese trabajo.

Descargue la <a href="/assets/downloads/pbcore-marc-mapping-20180430.xlsx" download>planilla de Excel con el mapeo</a> y la <a href="/assets/downloads/PBCore-MARC_documentation.pdf" download>documentación asociada</a>.

MARC 21 cuenta con el apoyo de Library of Congress. Este mapeo se refiere a <a href="https://www.loc.gov/marc/bibliographic/">la edición de 1999, actualización n° 27.</a>

<h3>PBCore y PREMIS</h3>
Si bien PBCore no se encarga específicamente de la preservación y el acceso contínuo de los activos que describe, la comunidad reconoce el valor de almacenar los datos de un modo estandarizado. Uno de los métodos más comunes para hacer esto es mediante el uso de <a href="https://www.loc.gov/standards/premis/">PREMIS</a> (Preservation Metadata Implementation Strategies, es español Metadatos de preservación: estrategias de implementación), que es el estándar internacional que se utiliza para que los metadatos admitan la preservación de los objetos digitales y asegurar su usabilidad a largo plazo. De manera deliberada, PREMIS no fue diseñado para describir formatos específicos, si no que incluye unidades semánticas específicas para aquellas propiedades que comparten todos los objetos digitales, dejando las descripciones de propiedades más específicas a los formatos para los estándares más especializados en formatos. Existen varios modos en los que los usuarios de PBCore y PREMIS pueden combinar las particularidades de ambos estándares para describir exhaustivamente las complejidades técnicas de los activos audiovisuales y la información necesaria para preservarlos y poder acceder a ellos.

La documentación que <a href="/assets/downloads/PBCore_PREMIS_Implementations_and_Mappings.pdf">aquí</a> brindamos incluye mapeos entre entidades de PREMIS y elementos raíz de PBCore, mapeos entre unidades semánticas de PREMIS y elementos y atributos de PBCore, y opciones de implementación para el uso conjunto de PREMIS y PBCore.

Descarge la guía completa comprimida de documentación y ejemplos <a href="/assets/downloads/PBCore_and_PREMIS.zip" download>aquí</a>.

<h3>PBCore y Dublin Core</h3>

PBCore se creó con el objetivo de ampliar el Dublin Core Metadata Element Set (Conjunto de elementos de metadatos de Dublin Core) y así poder describir de modo más integral los materiales audiovisuales. En consecuencia, la conversión desde PBCore hacia Dublin Core resulta en una pérdida de información específica del aspecto audiovisual. Sin embargo, en algunos casos puede resultar conveniente ofrecer sólo un subconjunto de los metadatos. Tal es el caso, por ejemplo, cuando se quiere compartir una lista de títulos y descripciones de activos con otra organización que utiliza Dublin Core, o para mostrarlos en un sistema de descubrimiento con una configuración similar.

La documentación que aquí se ofrece incluye un mapeo simple de elementos de PBCore hacia el <a href="http://www.dublincore.org/documents/dces/">Dublin Core Metadata Element Set Version 1.1</a> y los <a href="https://www.dublincore.org/specifications/dublin-core/dcmi-terms/">DCMI Metadata Terms</a> (Términos de Metadatos de DCMI).

Descargue el <a href="/assets/downloads/PBCore_to_DublinCore_mapping.xlsx">mapeo.</a>

Se recomienda que cada registro de Dublin Core se corresponda con una única instanciación de PBCore. Por ejemplo, si un registro de PBCore describe un activo con cuatro instanciaciones, el mismo deberá representarse con cuatro registros en Dublin Core. El vínculo entre estos registros se puede documentar utilizando el elemento Relación (Relation) de Dublin Core.

Los atributos de los elementos de PBCore no se pueden almacenar en Dublin Core. Cuando un activo tiene múltiples valores “‘pbcoreTitle”, todos ellos pueden registrarse mediante la repetición de la propiedad “title” de Dublin Core, pero no se puede registrar el atributo de PBCore “titleType” para diferenciar entre títulos de seres o de programas.

Si bien se pueden agregar a Dublin Core calificadores locales personalizados para incluir más datos de PBCore, estos calificadores no están estandarizados, y por ello dificultan la interoperabilidad con otros usuarios de Dublin Core.

Al Dublin Core Metadata Element Set y los DCMI Metadata Terms los mantiene la <a href="https://www.dublincore.org/about/">Dublin Core Metadata Initiative</a>.


<h3>PBCore XML-RDF (EBUCore/Dublin Core/DC Terms/SKOS)</h3>

El cuadro que presentamos aquí abajo provee un ejemplo simple de mapeo para la conversión desde el estándar de metadatos PBCore hacia predicados RDF existentes, utilizando principalmente términos de la ontología EBUCore, Dublin Core y SKOS.

Este mapeo incluye todos los elementos de PBCore menos los elementos de Extensión (la estructura infinitamente extensible de RDF vuelve a los atributos de Extensión redundantes). Dada la estructura de RDF, el mapeo no incluye atributos o sub-elementos de Type excepto en los casos en los que usarlos permite el mapeo hacia un predicado más específico (por ejemplo, AssetDate @dateType=”broadcast” = ebucore:dateBroadcast, pbcoreRelation with relationType=Has Derivative = ebucore:derivedTo).

Puesto que RDF no es jerárquico, recomendamos que los Activos, las Instanciaciones y los Essence Tracks existan como objetos RDF separados. Los vínculos entre Activos e Instanciaciones se pueden expresar usando dc:hasFormat and dc:isFormatOf. Los vínculos entre las Instanciaciones y los Essence Tracks se pueden expresar usando ebucore:hasTrack y ebucore:isTrackOf.

Descargue el <a href="/assets/downloads/PBCore-RDF_data_modeling%20worksheet_updated.xlsx" download>mapeo simple.</a>.

Las implementaciones de RDF varían según las necesidades específicas de la institución y el uso. EBUCore también insta a los usuarios a definir sus propias subclases y subpropiedades según lo requieran para sus necesidades específicas. Para demostrar el nivel de toma de decisión que se necesita para la indexación, la presentación y las propiedades locales, hemos incluido también <a href="https://docs.google.com/spreadsheets/d/1nk4dDClDl_vAXF-1VrMI9jPi9lA9jdUWdIRdQ-gPk-w/edit?usp=sharing">un ejemplo de planilla completa de modelados de datos,</a> que se utiliza para determinar propiedades y comportamientos para el sistema de gestión de metadatos basado en PBCore del American Archive of Public Broadcasting.

EBUCore está financiado por la European Broadcasting Union; este mapeo refiere a la <a href="https://www.ebu.ch/metadata/ontologies/ebucore/">versión 1.9 de la Ontología EBUCore.</a> El desarrollo de la ontología EBUCore es un esfuerzo conjunto de las comunidades de EBUCore y PBCore; se agregaron varias propiedades específicamente para facilitar el mapeo de PBCore. Para más información sobre EBUCore, visite la página de <a href="https://tech.ebu.ch/MetadataEbuCore">inicio del estándar de metadatos EBUCores</a>.


<h3>PBCore y IPTC</h3>
El IPTC Video Metadata Hub es un conjunto de propiedades de metadatos de video que se pueden expresar a través de múltiples estándares técnicos, entre ellos  XMP, EBUCore y JSON. Para las propiedades primarias que se incluyen en el Hub, se realizó un mapeo a PBCore en 2016, en un esfuerzo conjunto entre el IPTC y el PBCore Advisory Sub-Committee.

Acceda al  <a href="https://iptc.org/std/videometadatahub/recommendation/IPTC-VideoMetadataHub-mapping-Rec_1.2.html">documento de mapeo completo del Video Metadata Hub aquí.</a>

El Video Metadata Hub es financiado por el International Press Telecommunications Council (IPTC). Este mapeo refiere a la  <a href="https://iptc.org/standards/video-metadata-hub/recommendation/">edición 2018, versión 1.2</a>.


<h3 class="red title">Créditos</h3>
Le agradecemos a las siguientes personas por su trabajo en el mapeo de PBCore y MARC: Danielle Calle, Rebecca Fraimow, Rebecca Guenther, Annie Schweikert, y Sigridur R. Sigurthorsdottir.

Le agradecemos a las siguientes personas por su trabajo en el mapeo de PBCore XML/RDF: los miembros del PBCore-EBUCore RDF Working Group; los miembros de las comunidades de PBCore y EBUCore que contribuyeron al <a href="https://www.ebu.ch/metadata/ontologies/ebucore/">EBUCore 1.9</a>; y los miembros del equipo de proyecto <a href="https://github.com/WGBH-MLA/ams">AMS 2</a>.
