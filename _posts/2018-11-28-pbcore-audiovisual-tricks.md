---
layout: post
title: "Trucos Audiovisuales de PBCore"
section: Community
excerpt-separator: <span class="end-blurb"></span>
---

Este posteo, escrito por Dave Rice, describe cómo se pueden usar varias herramientas como MediaInfo y ffmpeg en los flujos de trabajo de descripción, acceso y preservación audiovisual.
<span class="end-blurb"></span>

## Salidas básicas de MediaInfo

Se puede producir una salida general de MediaInfo con un comando como:
<pre>
  <code>
    mediainfo your-file-here.mkv
  </code>
</pre>
Tenga en cuenta que si su instancia de MediaInfo se compiló con soporte cURL, también podría usar esto con una URL como:
<pre>
  <code>
    mediainfo http://samples.ffmpeg.org/flac/Yesterday.ogg
  </code>
</pre>
Se puede generar una versión más detallada de la salida de MediaInfo agregando la opción `-f` (full, para completo).
<pre>
  <code>
    mediainfo -f your-file-here.mkv
  </code>
</pre>  

Y para obtener una salida más analizable, la opción `--language=raw` garantiza que todas las etiquetas de metadatos sean únicas. 

<pre>
  <code>
    mediainfo -f --language=raw your-file-here.mkv
  </code>
</pre>  

MediaInfo admite muchos tipos diferentes de salidas de metadatos, como HTML, XML, JSON, EBUCore y... ¡PBCore! … y PBCore2. A menos que se necesiten versiones heredadas de PBCore, se recomienda PBCore2. Esto se puede generar con la opción --Output=PBCore2 como:

<pre>
  <code>
    mediainfo --Output=PBCore2 your-file-here.mkv
  </code>
</pre>  

Esta salida se puede escribir en un archivo con redirección, agregando `> outputfile.xml` al final del comando, como: 

<pre>
  <code>
    mediainfo --Output=PBCore2 your-file-here.mkv > now-i-have-a-pbcore.xml
  </code>
</pre>  

Para crear un lote de archivos xml PBCore adicionales, se puede ejecutar un ciclo como: 

<pre>
  <code>
    find /look/here -name '*.mov' | while read file ; do mediainfo --Output=PBCore2 "${file}" > "${file}_pbcore.xml" ; done
  </code>
</pre>  

Simplemente reemplace `/look/here`  con una ruta a un directorio en el que le gustaría buscar archivos y tal vez cambie `-name '*.mov`  a otro patrón para que coincida con los archivos para los que desea crear registros PBCore. 

## Personalización de la salida de PBCore

La salida de PBCore de MediaInfo se construye a partir de la información recopilada por MediaInfoLib. En algunos casos, es posible que desee reemplazar algunos de esos datos o agregar información que cubre el elemento Instanciación de PBCore pero que MediaInfo no puede informar (como las instantiationGenerations). Se pueden agregar metadatos en el proceso de llamar a MediaInfo usando el comando --ExternalMetadata como: 

<pre>
  <code>
    mediainfo --Output=PBCore2 --ExternalMetadata="instantiationLocation;my house" file-at-home.mp4
  </code>
</pre>

La sintaxis aquí consiste en que dentro de la opción `--ExternalMetadata` se proporciona un valor que contiene el nombre de los metadatos de PBCore, luego un punto y coma y luego el valor de esos metadatos (la instantiationLocation está establecida en "mi casa" en este ejemplo). Esto reemplazará la instantiationLocation proporcionada por MediaInfo (que es la ruta del archivo), con la información proporcionada por el usuario. Esto puede ser útil cuando no se quiere la ruta del archivo para instantiationLocation o cuando tiene más sentido proporcionar un valor general, como "Archivo WXXX", en lugar de un valor específico como la ruta de ese archivo en su sistema de archivos.

Tenga en cuenta que `--ExternalMetadata` funcionará con `instantiationGenerations` y `instantiationLocation`.

## Uso de PBCore para proporcionar metadatos de descripción en la creación de derivados

Al generar archivos audiovisuales derivados para facilitar el acceso a los contenidos, resulta de utilidad proporcionar metadatos audiovisuales integrados dentro de ese derivado para facilitarle al usuario la búsqueda y el acceso. Varios formatos de distribución audiovisual, como m4a, mp3, mp4 y otros, tienen métodos para almacenar metadatos descriptivos que los reproductores audiovisuales pueden usar. Esta información es importante para evitar que nuestras bibliotecas de iTunes y otras colecciones audiovisuales personales se conviertan en un caos absoluto.

En un proceso habitual de transcodificación de un archivo audiovisual para hacer un derivado, tenemos un proceso como este:

<pre>
  <code>
    preservation_master.mkv -> access_file.mp4
  </code>
</pre>

For `preservation_master.mkv` it may have some embedded metadata, pero en la mayoría de los entornos de gestión de colecciones, los metadatos descriptivos se encuentran en una base de datos separada (quizás una base de datos que pueda representar registros descriptivos en formato PBCore). En la situación hipotética anterior, el archivo `access_file.mp4` resultante compartirá algunos de los metadatos técnicos como el archivo de origen, pero no refleja ninguno de los metadatos descriptivos que pueden almacenarse en la base de datos. Si se introduce un XML PBCore XML en el proceso de transcodificación, sería más algo así:

<pre>
  <code>
    preservation_master.mkv + pbcore.xml -> access_file_with_metadata.mp4
  </code>
</pre>

Hay varios métodos para lograr esto. Si usa FFmpeg para facilitar la transcodificación, entonces un método es convertir el PBCore en un documento ffmetadata al que se podría hacer referencia en la transcodificación. El script de bash adjunto llamado <a href="/assets/downloads/pbcore2ffmetadata.sh" download>pbcore2ffmetadata</a> extrae datos seleccionados de PBCore para crear un archivo ffmetadata. Se puede utilizar de la siguiente manera:

<pre>
  <code>
    pbcore2ffmetadata your-pbcore.xml<br>
    ffmpeg -i your-media.mkv -i your-pbcore.xml.ffmetadata -map_metadata 1 access-file.mp4
  </code>
</pre>

En el comando anterior, cuando `pbcore2ffmetadata` se ejecuta con `your-pbcore.xml` como entrada, creará un nuevo archivo llamado `your-pbcore.xml.ffmetadata`. Ese archivo ffmetadata se puede usar como una segunda entrada en el siguiente comando ffmpeg. Dado que ese comando ffmpeg tiene dos entradas (un archivo audiovisual de origen y un archivo de metadatos), se agrega la opción -`-map_metadata 1` para aclarar que los metadatos de la entrada número 1 (el recuento de entradas comienza desde cero) deben usarse en la transcodificación, por lo tanto si se agrega `-i your-pbcore.xml.ffmetadata -map_metadata 1` después de la primera entrada se incorporarán esos metadatos de PBCore en el archivo de salida.

## Incorporar PBCore en Matroska

Matroska permite adjuntar archivos arbitrarios, lo cual proporciona un sistema para que los registros XML de PBCore se incorporen en cualquier archivo Matroska. A continuación, se brindan dos recomendaciones para incorporar PBCore en Matroska, con la creación de Matroska con FFmpeg o agregando un xml de PBCore a un archivo Matroska existente.

### Incorporar PBCore en Matroska usando FFmpeg

Al crear un archivo Matroska con FFmpeg, se pueden usar estas opciones para incorporar un XML de PBCore como archivo adjunto mientras se realiza la transcodificación.

<pre>
  <code>
    -attach pbcore.xml<br>
    -metadata:s:t:0 mimetype=text/xml<br>
    -metadata:s:t:0 title="PBCore"
  </code>
</pre>

La opción `-attach pbcore.xml` muestra qué archivo usar como archivo adjunto. Reemplace `pbcore.xml` con la ruta del archivo al archivo XML de PBCore que desea incorporar.

La opción `-metadata:s:t:0 mimetype=application/xml` cumple el requisito en Matroska de que el tipo MIME se almacene para todos los archivos adjuntos. El `s:t:0` en la opción de metadatos es un indicador de flujo donde s significa flujo, t significa archivo adjunto y 0 significa el primero (contando desde cero), por lo que esta opción establecerá los metadatos de tipo MIME para el primer archivo adjunto provisto.

La opción `-metadata:s:t:0 title="PBCore"` almacenará la palabra `PBCore` en el elemento FileDescription de Matroska resultante en ese elemento adjunto. Esto ayuda a describir el archivo adjunto de forma más específica que el valor de tipo MIME.

### Incorporar XML de PBCore en un archivo de Matroska existente

Lo anterior se puede usar para adaptar un comando FFmpeg existente que crea un archivo Matroska para incorporar XML de PBCore en el mismo proceso. Si el archivo Matroska ya se generó, FFmpeg no admite un método para adjuntar un PBCore XML rápidamente sin volver a escribir todo el archivo. Para adjuntar XML de PBCore a un archivo existente, mkvpropedit puede adjuntar el XML más rápidamente reescribiendo solo las partes del archivo Matroska que necesitan ajustes y dejando los datos audiovisuales como están.
<pre>
  <code>
    mkvpropedit --attachment-description "PBCore" --add-attachment pbcore.xml existing_file_that_could_use_a_pbcore_attachment.mkv
  </code>
</pre>

De modo similar al comando FFmpeg anterior, este comando de mkvpropedit proporciona una descripción y un nombre de archivo para que la utilidad lo use al ajustar el archivo de salida. En este caso, mkvpropedit puede adivinar correctamente el tipo MIME del XML como "texto/xml", por lo que no es necesario proporcionar esta opción específicamente. 

### Para extraer XML de PBCore de Matroska

Para un archivo llamado test.mkv, se pueden usar los siguientes comandos con FFmpeg y mkvextract para extraer el xml de PBCore del archivo para recrear el documento XML original.

Usando FFmpeg:

<pre>
  <code>
    ffmpeg -dump_attachment:t "" -i test.mkv
  </code>
</pre>

Usando mkvextract

<pre>
  <code>
    mkvextract test.mkv attachments 1
  </code>
</pre>

## Gathering PBCore samples

El script adjunto `pbcoresamples` está escrito para facilitar el uso de contenido en línea para generar un conjunto de archivos de PBCore de ejemplo desde MediaInfo. Este script incluye una matriz llamada `samples` (ejemplos) que contiene una lista de valores delimitada por comas que incluye una URL seguida de un nombre entre paréntesis que se usará para el documento PBCore de salida. Al ejecutar este comando, se generará un conjunto de ejemplos de PBCore a partir de la lista de ejemplos para su revisión. Es útil examinar los datos de PBCore de una amplia variedad de archivos para generar comentarios y sugerencias para la exportación de PBCore de MediaInfo.

## Realizar comentarios sobre el soporte de PBCore de MediaInfo

Los comentarios sobre la exportación de PBCore de MediaInfo deben escribirse en el controlador de problemas en MediaInfoLib en https://github.com/MediaArea/MediaInfoLib/issues. MediaInfoLib es la biblioteca que utiliza MediaInfo para el análisis de archivos y la generación de informes de metadatos. Si desea ver más de cerca lo que sucede detrás de escena, el exportador PBCore2 en MediaInfoLib se puede revisar en https://github.com/MediaArea/MediaInfoLib/blob/master/Source/MediaInfo/Export/Export_PBCore2.cpp .