# monitoreo-oyameles

[![DOI](https://zenodo.org/badge/333581041.svg)](https://zenodo.org/badge/latestdoi/333581041)

(English below)

Datos y análisis del monitoreo participativo del estado de salud de árboles de oyamel en el Parque Nacional Desierto de los Leones y sus zonas de influencia en Bienes Comunales Santa Rosa Xochiac, cuyo resumen de resultados [puede verse aquí](scripts/2_resumen_monitoreo_no_code.pdf). 

Estos resultados forman parte del proyecto 308488 *Monitoreo y manejo para la conservación de bosques aledaños a la CDMX afectados por contaminación atmosférica* de la convocatoria FORDECYT 2019-5, y son uno de los insumos de la elaboración de la propuesta en extenso de la convocatoria Proyectos Nacionales de Investigación e Incidencia para la Sustentabilidad de los Sistemas Socioecológicos.

El monitoreo fue realizado por brigadistas de Bienes Comunales Santa Rosa Xochiac durante diciembre 2020 y enero 2021. En total se muestrearon 48 parcelas de 10 x 10 m dentro del polígono del Parque Nacional Desierto de los Leones y Santa Rosa Xochiac. Dentro de cada parcela se censaron todos los árboles de oyamel superiores a 20 cm de alto o 0.5 cm de dimámetro, con un total de más de 1,700 árboles muestreados. Ver sección "Formularios kobo" para detalles.

Los datos se tomaron con la aplicación kobo-toolbox instalada en los servidores de la conabio (kobo.conabio.gob.mx). Todos los árboles fueron etiquetados en campo con etiquetas de madera biodegradables. Todos las fotografías fueron revisadas manualmente como parte del control de calidad.

Se realizó un taller de retroalimentación con la comunidad de Bienes Comunales Santa Rosa Xochiac donde se discutieron tanto los resultados del monitoreo como oportunidades de mejora en su impliementación en campo.


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

### `data/kobo_images`

Contiene las fotografías tomadas en campo de cada árbol. Por el momento este contenido sólo está disponible localmente en los servidores de la CONABIO.

### `data/spatial`

Contiene en formato shapefile los archivos:

* __CDMX.\*__ polígono de la CDMX
* __Desierto\_Leones\_Geo\_ITRF08.*__ polígono del Parque Nacional Desierto de los Leones.


Mismos que fueron utilizados junto con imágenes satelitales de google (ver `scripts/2_resumen_monitoreo.Rmd` y `scripts/3_figuras_propuesta.Rmd`) para realizar los mapas del reporte y la propuesta en extenso.


## Análisis y reporte de resultados

Los datos se procesaron con los siguientes scripts. De cada script existe también una versión html del mismo nombre que muestra el código y los resultados. 

### [scripts/1\_preprocesamiento\_datos\_kobo](scripts/1_preprocesamiento_datos_kobo.Rmd): 
Toma los datos crudos generados en kobo (*_raw.txt) y realiza un proceso de control de calidad con los siguientes pasos generales:

* Revisión de errores comunes (eg. valores fuera de rango)
* Examinar y limpiar datos de salud de los árboles
* Examinar y limpiar datos del daño por ozono
* Examinar y limpiar notas sobre reforestación
* Reformatear datos a formato "largo" para análisis y exportar datos (*_tidy.txt)

### [scripts/2\_resumen\_monitoreo](scripts/2_resumen_monitoreo.Rmd): 

Utiliza los datos limpios (*_tidy.txt) para hacer un reporte del monitoreo participativo que incluye: 

* La distribución geográfica del estado de salud de los árboles por parcela
* Distribución del daño ozono segun altitud y latitud
* Estado de salud de árboles individuales según: origen (natural, reforestado), exposición (cubierto/expuesto), altura, diámetro, edad
* Porcentaje de daño del árbol dañado por ozono en áboles individuales según: origen (natural, reforestado), exposición (cubierto/expuesto), altura, diámetro y edad.

### [scripts/3\_figuras\_propuesta](scripts/3_figuras_propuesta.Rmd):

Utiliza los datos limpios (*_tidy.txt) para hacer el subconjunto de figuras del reporte que se utilizaron para la propuesta en extenso.

### [scripts/4\_figures\_Monitoring-Paper.Rmd](scripts/4_figures_Monitoring-Paper.Rmd):
Análisis y figuras para el artículo *Evaluating pollution-related damage and restoration success in urban forests with participatory monitoring and digital tools* Conservation Biology.  https://doi.org/10.1111/cobi.14112.


## Formularios kobo


Los formularios kobo utilizados se encuentran en el directorio `/kobo_forms`. Los formularios se presentan en formato .xlsx, lo que permite importarlos en el servidor web de kobo, y en formato .pdf, lo que permite visualizar más fácilmente las preguntas.

### Formulario CX\_Colecta\_Censo\_2020

Formulario utilizado por las personas brigadistas para la recolección de datos de árboles individuales dentro de las parcelas.

De cada árbol se tomaron coordenadas geográficas, datos dasométricos, fenológicos y de salud, origen (reforestado/natural), exposición (expuesto/cubierto) si habían sido utilizados como fuente de semilla, fotografías y muestras de tejido que fueron preservadas en sílica gel. Ver versión pdf para la lista de preguntas completas.

### Formulario CX\_Parcelas\_censo\_oyameles

Formulario utilizado por el equipo académico para el levantamiento de datos de las parcelas.

De cada parcela se tomaron datos sobre la cobertura forestal y arbustiva, suelo, especies vegetales dominantes, pendiente y relieve. 


# English

[![DOI](https://zenodo.org/badge/333581041.svg)](https://zenodo.org/badge/latestdoi/333581041)

Data and analysis of the participatory monitoring of the health status of oyamel trees in the Desierto de los Leones National Park and its areas of influence in Bienes Comunales Santa Rosa Xochiac, whose summary of results [can be seen here](scripts/2_resumen_monitoreo_no_code.pdf).

These results are part of project 308488 *Monitoring and management for the conservation of forests surrounding CDMX affected by air pollution* of the FORDECYT 2019-5 CONACYT grant, and are one of the inputs for the preparation of the full proposal for PRONACES.

The monitoring was carried out by brigade members of Santa Rosa Xochiac Bienes Comunales during December 2020 and January 2021. In total, 48 plots of 10 x 10 m were sampled within the polygon of the Desierto de los Leones and Santa Rosa Xochiac. Within each plot, all fir trees greater than 20 cm tall or 0.5 cm in diameter were censused, with a total of more than 1,700 sampled trees. See the "Kobo Forms" section for details.

The data was taken with the kobo-toolbox application installed on the CONABIO servers (kobo.conabio.gob.mx). All trees were tagged in the field with biodegradable wooden tags. All photographs were manually reviewed as part of quality control.

A feedback workshop was held with the Bienes Comunales Santa Rosa Xochiac community where both the monitoring results and opportunities for improvement in its implementation in the field were discussed.

## Data

The data correspond to the result of the participatory sampling carried out with kobo-conabio and to spatial data used to spatially contextualize the results.

The data is organized as follows:

### `data/kobo`

Raw data:

* **muestreo\_dic2020\_raw.txt** Raw data resulting from exporting the data from the kobo CX\_Collecta_Censo\_2020 form. This form was used to collect information on all fir trees present within 48 plots of 10x10 m in December 2020 and January 2021. The information was collected in the field by 13 brigade members from Santa Rosa Xochiac.

* **parcelas\_dic2020\_raw.txt** Raw data resulting from exporting the data from the kobo CX formulary\_Plots\_census\_oyameles. This form was used to collect general information on the 48 plots sampled in December and January 2021. The information was collected by Alicia Mastretta.

Once the data is cleaned and organized by the script [scripts/1\_preprocessing\_data\_kobo.Rmd](scripts/1_preprocessing_data_kobo.Rmd) the following files are produced:

* **muestreo\_dic2020\_tidy.txt**: data from the 48 plots after cleaning processing.
* **parcelas\_dic2020\_tidy.txt**: in addition to the original data, it includes the sum of trees under each health category (healthy, ozone damage, among others).


### `data/kobo_images`

It contains the photographs taken in the field of each tree. At the moment this content is only available locally on the CONABIO servers.

### `data/spatial`

It contains the files in shapefile format:

* __CDMX.\*__ CDMX polygon
* __Desierto\_Leones\_Geo\_ITRF08.*__ polygon of the Desierto de los Leones National Park.


These were used together with google satellite images (see scripts/2_resumen_monitoreo.Rmd` and `scripts/3_figuras_propuesta.Rmd`) to make the maps of the report and the full proposal.


## Analysis and reporting of results

The data was processed with the following scripts. For each script there is also an html version of the same name that shows the code and the results.

### [scripts/1\_preprocesamiento\_datos\_kobo](scripts/1_preprocesamiento_datos_kobo.Rmd):
Take the raw data generated in kobo (*_raw.txt) and perform a quality control process with the following general steps:

* Review of common errors (eg. values ​​out of range)
* Browse and clean tree health data
* Examine and clean ozone damage data
* Examine and clean notes on reforestation
* Reformat data to "long" format for analysis and export data (*_tidy.txt)

### [scripts/2\_resumen\_monitoreo](scripts/2_resumen_monitoreo.Rmd):

Use the clean data (*_tidy.txt) to make a participatory monitoring report that includes:

* The geographical distribution of the state of health of the trees by plot
* Distribution of ozone damage according to altitude and latitude
* Health status of individual trees according to: origin (natural, reforested), exposure (covered/exposed), height, diameter, age
* Percentage of tree damage damaged by ozone in individual trees according to: origin (natural, reforested), exposure (covered/exposed), height, diameter, and age.

### [scripts/3\_figuras\_propuesta](scripts/3_figuras_propuesta.Rmd):

Use the clean data (*_tidy.txt) to make the subset of report figures that were used for the full proposal.

### [scripts/4\_figures\_Monitoring-Paper.Rmd](4\_figures\_Monitoring-Paper.Rmd):
Analysis and figures for the article *Evaluating pollution-related damage and restoration success in urban forests with participatory monitoring and digital tools* Conservation Biology. https://doi.org/10.1111/cobi.14112.

## Kobo Forms


The kobo forms used are located in the `/kobo_forms` directory. The forms are presented in .xlsx format, which allows you to import them into the kobo web server, and in .pdf format, which makes it easier to view the questions.

### Form CX\_Collection\_Census\_2020

Form used by brigade members to collect data on individual trees within the plots.

Geographic coordinates, dasometric, phenological and health data, origin (reforested/natural), exposure (exposed/covered) if they had been used as a seed source, photographs and tissue samples that were preserved in silica gel were taken from each tree. See pdf version for the list of complete questions.

### Form CX\_Colecta\_Censo\_2020

Form used by the academic team to collect data from the plots.

Data on forest and shrub cover, soil, dominant plant species, slope, and relief were collected from each plot.



