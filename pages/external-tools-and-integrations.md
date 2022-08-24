---
title: External Tools and Integrations
layout: default
section: Resources
permalink: /external-tools-and-integrations
keywords: ["Resources", "Tools", "Cataloging", "Creating Records", "Databases", "Data Management", "Technical Metadata", "MediaInfo", "ProTrack", "Collective Access", "Omeka"]
---

<h2 class="red title bold">Herramientas Externas e Integraciones</h2>

<p class="med-text">Muchos software cuya manutención y financiación dependen de organizaciones externas permiten la gestión y exportación de metadatos de PCBore. Si usted gestiona software que admite PBCore y le gustaría incluirlo en esta lista, por favor contáctenos mediante correo electrónico a PBCoreInfo@wgbh.org.</p>

<h3 id="mediainfo">MediaInfo</h3>

MediaInfo es una herramienta de código abierto que crea documentación de metadatos técnicos para archivos de video y audio, como formato, codec, título, duración, tasa de bits, profundidad de bits, submuestreo de croma, canales, etc. Mediainfo admite varios tipos de envío de metadatos, entre los que se incluyen PBCore 1.2 y PBCore 2.1. Para descargar MediaInfo, visite <a href="https://mediaarea.net/en/MediaInfo/Download">https://mediaarea.net/en/MediaInfo/Download</a>

Cuando MediaInfo exporta PBCore crea InstantiationDocuments de PBCore que se construyen a partir de la información que reúne MediaInfoLib. Los metadatos adicionales que se incluyen en un documento de instanciación pero que MediaInfo no logra informar (como instantiationGenerations y instantiationLocation) también pueden agregarse a los documentos PBCore que se crean. Puede leer más sobre el uso de las exportaciones de PBCore que realiza MediaInfo <a href="/2018/11/28/pbcore-audiovisual-tricks">aquí</a>.

El desarrollo de la exportación de PBCore 2.1 de MediaInfo fue financiado por NEH, como parte del programa PBCore Development and Training Project.

<h3 id="protrack">ProTrack Broadcast Management System</h3>

ProTrack es una solución para la gestión de sistemas profesionales de radiodifusión que centraliza los metadatos de contenido y permite múltiples flujos de trabajo de distribución desde un único punto de control. Lo utiliza el 98% de las estaciones que son miembro de PBS. Para saber más sobre cómo comenzar a utilizar ProTrack, contacte a <a href="http://myersinfosys.com/contact-us/">Myers InfoSys</a>.

Existen dos métodos para exportar XML de PBCore desde ProTrack:

Exportar PBcore desde Program Search (Búsqueda de Programa) (<a href="/assets/downloads/PBCore_Export_ProTrack.pdf" download>PDF</a>)

Exportar PBcore desde Air Date Search (Búsqueda de Fecha de Emisión) (<a href="/assets/downloads/PBCore_Export_ProTrack_AirDateSearch.pdf" download>PDF</a>)

Esta documentación también se puede ver en la KnowledgeBase de ProTrack.

El desarrollo de la exportación de PBCore 2.1 de ProTrack fue financiado por NEH, como parte del programa PBCore Development and Training Project.

<h3 id="collectiveaccess">Collective Access</h3>
Collective Access es un software de código abierto que se utiliza para la gestión y publicación de colecciones de museos y archivos. La aplicación central de catalogación y gestión de datos de Collective Access, Providence, incluye soporte integrado para estándares de metadatos ya existentes, incluyendo PBCore. La documentación XML para el perfil de instalación de PBCore de Collective Access puede encontrarse en el <a href="https://github.com/collectiveaccess/providence/blob/master/install/profiles/xml/pbcore.xml">Collective Access GitHub</a> En el momento de la instalación, el perfil se admite como un perfil de configuración para catalogación a nivel del ítem (contenido de instanciación/intelectual), y como un destino de exportación. (Este perfil se revisó por última vez en 2013).

En 2019 se desarrolló un perfil de PBCore 2.1 con financiación de NEH, como parte del programa PBCore Development and Training Project. Puede encontrar el perfil de instalación y otra documentación general en el <a href="https://github.com/PBCore-AV-Metadata/collective-access-for-2.1">PBCore GitHub</a>.

Muchos de los usuarios de Collective Access prefieren configurar sus propios perfiles de instalación en vez de usar una versión integrada. Aquí abajo puede encontrar ejemplos de perfiles de instalación de varios usuarios de Collective Access que incorporaron PBCore a sus aplicaciones de gestión de datos:

<a href="assets/downloads/homemovie_collectiveaccess_profile.png" download>The South Side Home Movie Project</a>

<a href="https://www.collectiveaccess.org/sites/default/files/profiles/sni_config_0.xml">Smithsonian Channel</a>

<a href="https://www.collectiveaccess.org/sites/default/files/profiles/sni_config_0.xml">Academy of Motion Picture Arts and Sciences</a>

<a href="/assets/downloads/nhf_collective-access_config.xml" download>Northeast Historic Film</a>

<a href="/assets/downloads/appalshop_collectiveaccess_config.xml" download>Appalshop, Inc.</a>

<h3 id="omeka">Omeka</h3>
Omeka es una plataforma de publicación web de código libre pensada para mostrar colecciones digitales y crear exhibiciones virtuales multimedia. La funcionalidad principal de Omeka tiene elementos del esquema de metadatos Dublin Core, pero la funcionalidad de Omeka se puede ampliar mediante plugins que permiten añadir elementos de otros estándares de metadatos.

En 2019 se desarrolló un <a href="https://omeka.org/classic/plugins/PBCore2/">plugin de PBCore para Omeka</a>, gracias al financiamiento de NEH, como parte del programa PBCore Development and Training Project. Este plugin permite añadir elementos de metadatos de PBCore para describir contenido audiovisual en Omeka tanto al nivel del activo como al de la instanciación. La documentación sobre el uso de este plugin está disponible <a href="https://omeka.org/classic/docs/Plugins/PBCore/">en el sitio web de Omeka.</a>

<h3 id="archivesspace">ArchivesSpace</h3>
<a href="https://archivesspace.org/" target="_blank">ArchivesSpace</a> es una aplicación web de código abierto para gestión de información de archivos. El diseño de la aplicación permite funciones básicas de la administración de archivos, como ingreso, descripción y disposición de los materiales procesados incluyendo el contenido analógico, híbrido y de origen digital, gestión de autoridades (agentes y temas) y derechos, y servicios de referencia. La aplicación permite la gestión de colecciones mediante los registros de gestión de colección, el seguimiento de eventos, y un número cada vez mayor de reportes administrativos. La aplicación también funciona como una herramienta de creación de metadatos, lo que permite la generación de datos formateados EAD, MARCXML, MODS, Dublin Core, y METS.

WGBH Media Library and Archive desarrolló <a href="https://github.com/WGBH-MLA/pbspace" target="_blank">PBSpace</a>, un plugin para ArchivesSpace, que añade nuevas propiedades y relaciones de objeto a la aplicación para representar mejor la estructura, elementos y atributos de PBCore. El desarrollo de PBSpace fue posible gracias al National Endowment for the Humanities: Exploring the human endeavor.
