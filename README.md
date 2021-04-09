# monitoreo-oyameles

Datos y análisis del monitoreo participativo del estado de salud de árboles de oyamel en el Parque Nacional Desierto de los Leones y sus zonas de influencia en Santa Rosa Xochiac.

Estos resultados forman parte del proyecto 308488 *Monitoreo y manejo para la conservación de bosques aledaños a la CDMX afectados por contaminación atmosférica* de la convocatoria FORDECYT 2019-5, y son uno de los insumos de la elaboración de la propuesta en extenso de la convocatoria Proyectos Nacionales de Investigación e Incidencia para la Sustentabilidad de los Sistemas Socioecológicos.

El monitoreo fue realizado por brigadistas de Santa Rosa Xochiac durante diciembre 2020 y enero 2021. En total se muestrearon 48 parcelas de 10 x 10 m dentro del polígono del Parque Nacional Desierto de los Leones y Santa Rosa Xochiac. Dentro de cada parcela se censaron todos los árboles de oyamel superiores a 20 cm de alto o 0.5 cm de dimámetro, con un total de más de 1,700 árboles muestreados. De cada árbol se tomaron datos dasométricos, fenológicos y de salud, así como fotografías y muestras de tejido que fueron preservadas en sílica gel. De las parcelas se tomaron datos sobre la cobertura forestal y arbustiva, suelo, especies vegetales dominantes, pendiente, entre otros. Ver sección "Formularios kobo" para detalles.

Los datos se tomaron con la aplicación kobo-toolbox instalada en los servidores de la conabio (kobo.conabio.gob.mx). Todos los árboles fueron etiquetados en campo con etiquetas de madera biodegradables. Todos las fotografías fueron revisadas manualmente como parte del control de calidad.

Se realizó un taller de retroalimentación con la comunidad de Santa Rosa Xochiac donde se discutieron tanto los resultados del monitoreo como oportunidades de mejora en su impliementación en campo.


## Datos

Los datos corresponden al resultado del muestreo participativo realizado con kobo-conabio y a datos espaciales utilizados para contextualizar espacialmente los resultados.

Los datos se encuentran organizados de la siguente forma:

### `data/kobo`

Datos crudos:

* **muestreo\_dic2020\_raw.txt** Datos crudos resultado de exportar los datos del formulario de kobo CX\_Colecta_Censo\_2020. Este formulario se ocupó para levantar información de todos los árboles de oyamel presentes dentro de 48 parcelas de 10x10 m en diciembre 2020 y enero 2021. La información fue levantada en campo por 13 brigadistas de Santa Rosa Xochiac.

* **parcelas\_dic2020\_raw.txt** Datos crudos resultado de exportar los datos del formulairo de kobo CX\_Parcelas\_censo\_oyameles. Este formulario se ocupó para levantar información general de las 48 parcelas muestreadas en diciembre y enero 2021. La información fue levantada por Alicia Mastretta.

Una vez que los datos son limpiados y organizados por el script [scripts/1\_preprocesamiento\_datos\_kobo.Rmd](scripts/1_preprocesamiento_datos_kobo.Rmd) se producen los siguientes archivos:

* **muestreo\_dic2020\_tidy.txt**: datos de las 48 parcelas tras el procesamiento de limpieza.
* **parcelas\_dic2020\_tidy.txt**: además de los datos originales, incluye la suma de árboles bajo cada categoría de salud (sano, daño por ozno, entre otros).

### data/kobo_images

Contiene las fotografías tomadas en campo de cada árbol. Por el momento este contenido sólo está disponible localmente en los servidores de la CONABIO.

### data/spatial

Contiene en formato shapefile los archivos:

* __CDMX.\*__ polígono de la CDMX
* __Desierto\_Leones\_Geo\_ITRF08.*__ polígono del Parque Nacional Desierto de los Leones.


Mismos que fueron utilizados junto con imágenes satelitales de google (ver `scripts/2_resumen_monitoreo.Rmd` y `scripts/3_figuras_propuesta.Rmd`) para realizar los mapas del reporte y la propuesta en extenso.


## Análisis y reporte de resultados

Los datos se procesaron con los siguientes scripts:

### [scripts/1\_preprocesamiento\_datos\_kobo.Rmd](scripts/1_preprocesamiento_datos_kobo.Rmd): 
Toma los datos crudos generados en kobo (*_raw.txt) y realiza un proceso de control de calidad con los siguientes pasos generales:

* Revisión de errores comunes (eg. valores fuera de rango)
* Examinar y limpiar datos de salud de los árboles
* Examinar y limpiar datos del daño por ozono
* Examinar y limpiar notas sobre reforestación
* Reformatear datos a formato "largo" para análisis y exportar datos (*_tidy.txt)

### [scripts/2\_resumen\_monitoreo.Rmd](scripts/2_resumen_monitoreo.Rmd): 

Utiliza los datos limpios (*_tidy.txt) para hacer un reporte del monitoreo participativo que incluye: 

* La distribución geográfica del estado de salud de los árboles por parcela
* Distribución del daño ozono segun altitud y latitud
* Estado de salud de árboles individuales según: origen (natural, reforestado), exposición (cubierto/expuesto), altura, diámetro, edad
* Porcentaje de daño del árbol dañado por ozono en áboles individuales según: origen (natural, reforestado), exposición (cubierto/expuesto), altura, diámetro y edad.

### [scripts/3\_figuras\_propuesta.Rmd](scripts/3_figuras_propuesta.Rmd):

Utiliza los datos limpios (*_tidy.txt) para hacer el subconjunto de figuras del reporte que se utilizaron para la propuesta en extenso.


