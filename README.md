# monitoreo-oyameles

Datos y análisis del monitoreo participativo del estado de salud de árboles de oyamel en el Parque Nacional Desierto de los Leones y sus zonas de influencia en Santa Rosa Xochiac.

Estos resultados forman parte del proyecto 308488 *Monitoreo y manejo para la conservación de bosques aledaños a la CDMX afectados por contaminación atmosférica* de la convocatoria FORDECYT 2019-5, y son uno de los insumos de la elaboración de la propuesta en extenso de la convocatoria Proyectos Nacionales de Investigación e Incidencia para la Sustentabilidad de los Sistemas Socioecológicos.


## Datos

Los datos corresponden al resultado del muestreo participativo realizado con kobo-conabio y a datos espaciales utilizados para contextualizar espacialmente los resultados.

### data/kobo

Datos crudos:

* **muestreo_dic2020_raw.txt** Datos crudos resultado de exportar los datos del formulario de kobo CX\_Colecta_Censo\_2020. Este formulario se ocupó para levantar información de todos los árboles de oyamel presentes dentro de 48 parcelas de 10x10 m en diciembre 2020 y enero 2021. La información fue levantada en campo por 13 brigadistas de Santa Rosa Xochiac.

* **parcelas_dic2020_raw.txt** Datos crudos resultado de exportar los datos del formulairo de kobo CX\_Parcelas\_censo\_oyameles. Este formulario se ocupó para levantar información general de las 48 parcelas muestreadas en diciembre y enero 2021. La información fue levantada por Alicia Mastretta.

Una vez que los datos son limpiados y organizados por el script [1\_preprocesamiento_datos\_kobo.Rmd](1_preprocesamiento_datos_kobo.Rmd) se producen los siguientes archivos:

* **muestreo_dic2020_tidy.txt**
* **parcelas_dic2020_tidy.txt**: además de los datos originales, incluye la suma de árboles bajo cada categoría de salud (sano, daño por ozno, entre otros).


