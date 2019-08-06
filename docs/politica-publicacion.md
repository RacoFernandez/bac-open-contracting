# Política de publicación

La política de datos abiertos del Gobierno de la Ciudad de Buenos Aires tiene sus inicios en 2012 con el lanzamiento del portal data.buenosaires.gob.ar, el cual al día de hoy ya concentra más de 1000 recursos disponibles en formato abierto. Hace más de una década que la Ciudad cuenta con el sistema de compras y contrataciones públicas llamado BAC (Buenos Aires Compras), el cual garantiza transparencia y celeridad en los procesos. Si bien desde sus inicios el sistema contaba con un portal para consultar información acerca de los procesos de compra, la misma no se encontraba en formato abierto lo cual obstaculizaba su reutilización. Desde principios del año 2018 el Gobierno de la Ciudad de Buenos Aires comenzó a trabajar en la publicación de la información del sistema de compras y contrataciones públicas BAC (Buenos Aires Compras) en formato abierto. Con este trabajo, se pone a disposición de la ciudadanía, el acceso a información sobre las contrataciones públicas que le permite saber cómo se gestionan las mismas. La disponibilidad de estos datos fue un salto cualitativo fundamental, garantizando el derecho a la información, fortaleciendo la transparencia de los actos de gobierno.

El procedimiento de compras y contrataciones que se realiza en la ciudad, se instrumenta a través del Sistema de Registro Informatizado de Contrataciones en el ámbito del Ministerio de Hacienda de la Ciudad de Buenos Aires. Regulada por la Ley N° 2.095, Ley de Compras y Contrataciones de la Ciudad de Buenos Aires y su decreto reglamentario.

La adopción del Estándar de Datos para las Contrataciones Abiertas (OCDS por sus siglas en inglés) fue un desafío para el Gobierno de la Ciudad que implicó la revisión de sus procesos actuales y traducción de los mismos al estándar dispuesto por Open Contracting Partnership. Con este trabajo, se contribuyó a la política de transparencia e integridad pública que se lleva adelante y de esta forma, inspirar a otras ciudades a encarar procesos similares. 

La publicación de las compras y contrataciones en formato abierto y con el estándar de Contrataciones Abiertas fue gracias al trabajo en conjunto entre el Ministerio de Economía y Finanzas y Secretaría General y Relaciones Internacionales del Gobierno de la Ciudad de Buenos Aires.


## Propósito de la publicación

El Estándar de Datos para las Contrataciones Abiertas (OCDS) es una estándar global de datos que promueve la divulgación de datos y documentos en todas las etapas del proceso de contratación. Este estándar ha sido desarrollado para que los proveedores de información compartan datos estructurados, estandarizados y reutilizables.

La publicación de los datos de contratación, se encuentran disponibles data.buenosaires.gob.ar y tiene como objetivo garantizar que toda la información que se produce en las compras y contrataciones públicas de bienes y servicios en la ciudad estén disponibles en línea y en formatos abiertos.  

La importancia de la adaptación a este estándar radica en:

- Mejorar la calidad de los datasets publicados.
- Mejorar la capacidad de comprensión de los datasets utilizados.
- Impulsar la adopción de estándares para la apertura de datos.
- Impulsar la reutilización de los datos abiertos.
- Promover la toma de decisiones basadas en evidencia.
- Mejorar la competitividad entre los proveedores de gobierno.
- Reducir los costos y optimizar la relación precio calidad que enfrentan las áreas de gobierno.



## Creación de Datasets OCDS
La Dirección General de Compras y Contrataciones dependiente del Ministerio de Economía y Finanzas de la Ciudad de Buenos Aires realiza la instrumentación de los procedimientos para la tramitación de compras o contrataciones, cualquiera sea su modalidad o naturaleza, interviniendo en todas las instancias del trámite administrativo que se derivan de la acción de contratar, regulado por la Ley de Compras y Contrataciones de la Ciudad de Buenos Aires y su decreto reglamentario. 

La Dirección General de Calidad Institucional y Gobierno Abierto posee el permiso para la extracción completa de la base de datos de Buenos Aires Compras (BAC) que incluyen las tres etapas del proceso de compras y contrataciones, las modalidades de contratación y los procedimientos de selección, descriptos precedentemente. 

Las modalidades de contratación se encuentran detalladas como prefijo en los valores de campo contracts/0/id. 

- SPR- para los contratos con modalidad **Orden de Compra Abierta**

- OCC- para los contratos con modalidad **Orden de Compra Cerrada**

- CM- para los contratos con modalidad **Convenio Marco**

Los procedimientos de selección de los proveedores se encuentran detallados en el campo  procurementMethod y procurementMethodDetails de la etapa “tender”. 

Esta información es proporcionada a través de un archivo CSV con datos estructurados y la conversión a OCDS se realiza a través de un script de python. La publicación de datos de compras de bienes o servicios bajo el estándar propuesto están disponibles en formato CSV y JSON. Su actualización se realiza con una frecuencia de 15 días corridos.

## Recursos del dataset

La información del sistema de compras y contrataciones se encuentra publicada en el dataset [Buenos Aires Compras](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras) 

### [Buenos Aires Compras](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/2a3d077c-71b6-4ba7-8924-f3e38cf1b8fc)

Archivo con formato [JSON (JavaScript Object Notation)](https://es.wikipedia.org/wiki/JSON) que contiene la información de todos los procesos de compras publicados en sus diferentes etapas (convocatoria, adjudicación, contratación, participantes). Para cada proceso de compra se asigna un OCID (Open Contracting Identifier), al cual se asocia toda la información referida a las etapas por las que pasa el proceso. 

### [Convocatoria](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/f8eb531f-120c-4e91-bd5d-d43bb28cc696)
Archivo con formato [CSV (comma-separated values)](https://es.wikipedia.org/wiki/Valores_separados_por_comas) con la información de la convocatoria a participantes para todos los procesos de compras y contrataciones gestionados a través del BAC.
Contiene el detalle de los pliegos de bases y condiciones (fechas, montos, organizaciones), los documentos web donde se publica la información y el detalle de los ítems que se van a contratar.

### [Adjudicación](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/b7e4bae8-0e0f-4e10-8b89-3860cf5b7f1b) 
Archivo con formato CSV con la información de la adjudicación de los procesos de compras. Incorpora el detalle de los documentos publicados luego de la adjudicación y los ítems adjudicados. 

### [Contratación](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/a85472d6-b949-4617-a3a0-50e25f1274b3)
Archivo con formato CSV con la información de los contratos firmados por las partes participantes del proceso. Contiene el detalle de los montos efectivamente erogados por las reparticiones del GCBA, los ítems contratados, los plazos de contratación.

### [Participantes](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/bece0240-eb9b-40c4-8928-cd77c4f62704)
Archivo con formato CSV que contiene el detalle de las partes participantes (proveedores, compradores, unidades de adquisiciones) de cada uno de los procesos de compras gestionados a través del BAC.


## Alcance de los datos 
	
**Fecha**: Marzo de 2011 - Actualidad

**Compradores**: Son las unidades ejecutoras del Gobierno de la Ciudad de Buenos Aires.Incluye las áreas de Jefatura de Gobierno, Vicejefatura, Jefatura de Gabinete de Ministros, Ministerios, Secretarías, Subsecretarías, Direcciones Generales, Unidades de proyectos especiales. 

**Valores**:El Gobierno de la Ciudad de Buenos Aires no tiene un valor de contratación por debajo o por encima del cual se excluyan los datos de contratación.

**Tipos de proceso**: Orden de compra abierta, orden de compra cerrada, compra unificada, subasta inversa y convenio Marco. 

**Etapas**: Publicamos los datos de convocatoria, licitación o concurso, adjudicación y contratos para cada proceso de contratación. 

**Cantidad de procesos**: La cantidad de procesos publicados es creciente con el correr de los años. Esto se encuentra directamente relacionado con la extensión del uso del sistema BAC para gestionar compras y contrataciones.

## Codigos, lista de códigos y extensiones utilizadas en la publicación de datos 

* **Códigos:** Items
* **Nombre de la lista:** x_catalogo_bienes_servicios_BAC
* **Descripción:** Listado de códigos utilizados en el sistema BAC para identificar bienes o servicios y sus respectivos modelos. Disponible [aquí](https://catalogoba.dguiaf-gcba.gov.ar/). Usuario: CATALOGO ; Contraseña: consulta

* **Códigos:** Unidades de medida
* **Nombre de la lista:** x_unidades_medida_bac
* **Descripción:** Unidades de medida utilizadas en el sistema BAC

* **Códigos:** Unidades de medida
* **Nombre de la lista:** UNCEFACT
* **Descripción:** Códigos de unidades de medida propuestos por Naciones Unidas para el comercio internacional.

* **Códigos:** Código de identificación de proveedores
* **Nombre de la lista:** AR-CUIT
* **Descripción:** Listado de códigos utilizados para identificar a los proveedores de bienes o servicios. Se construye en base al número de CUIT de los mismos.

* **Códigos:** Código de identificación de unidades ejecutoras y unidades operativas de adquisiciones
* **Nombre de la lista:** CABA-UE
* **Descripción:** Listado de códigos utilizados para identificar a las agencias de gobierno que participan del proceso de compras.

* **Campo:** procurementMethod 
* **Valor OCDS:** direct
* **Valor BAC:** contratación menor; contratación directa

* **Campo:** procurementMethod
* **Valor OCDS:** open
* **Valor BAC:** licitación pública

* **Campo:** procurementMethod
* **Valor OCDS:** limited
* **Valor BAC:** licitación privada

* **Extensión utilizada:** Signatories
* **Descripción:** Listado de participantes en la firma del contrato. Compradores, proveedores y entidades procuradoras
* **Link a la extensión:** [https://github.com/open-contracting-extensions/ocds_contract_signatories_extension](https://github.com/open-contracting-extensions/ocds_contract_signatories_extension)

## Licencias 

La publicación de los datos de compras y contrataciones del sistema BAC en el Estándar para las Contrataciones Abiertas (OCDS) se realiza bajo la licencia Creative Commons Legal Code Atribución 2.5 Argentina. Esto permite que los usuarios de datos realicen las siguientes acciones: 

- Compartir, copiar y redistribuir material en cualquier medio o formato. 
- Adaptar, remezclar, transformar y construir a partir del material para cualquier propósito, incluso comercial. 
- Utilizar estos datos para cualquier propósito, incluido uso comercial y no comercial.
- Publicar contenido basado en el uso de los datos publicados.

El texto completo de la licencia, se puede encontrar en [creativecommons.org/licenses/by/2.5/ar/legalcode](creativecommons.org/licenses/by/2.5/ar/legalcode)


## Aspectos legales y OCDS

El Gobierno de la Ciudad lleva adelante la política de apertura de datos desde el años 2012 con la firma del decreto 156/2012. Esto impulsó la creación de la plataforma de datos publicos data.buenosaires.gob.ar para facilitar la búsqueda, descubrimiento y acceso de los datos abiertos producidos por la ciudad. 

A fines de 2015, la Ciudad firmó la Carta Internacional de Datos Abiertos a través de la cual, se compromete a seguir e implementar los lineamientos para datos públicos. Sumado, a la sanción de la Ley de Acceso a la Información Pública (Ley N° 104) implicó un avance en materia de apertura ya que establece el formato abierto como criterio fundamental. 

La Dirección General de Calidad Institucional y Gobierno Abierto es el área responsable de diseñar e implementar la política de datos abiertos de la ciudad a través de data.buenosaires.gob.ar. Actualmente, aplicamos el estándar Open Contracting a través de la publicación de datos OCDS. 


## Responsabilidad, información de contacto y comentarios 

La Dirección General de Compras y Contrataciones (DGCYC) del Ministerio de Economía y Finanzas es el responsable de producir la información de las compras y contrataciones que se registran en el sistema Buenos Aires Compras (BAC). Para entender el proceso de compras de la ciudad, la Dirección General de Compras y Contrataciones (DGCYC) pone a disposición de los empleados y proveedores del Gobierno de la Ciudad, cursos de capacitación presenciales y de forma online. Para solicitar información sobre los cursos online puede acceder al campus virtual dguiafvirtual.buenosaires.gob.ar/ o puede enviar un mail a [logistica@dguiaf-gcba.gov.ar](mailto: logistica@dguiaf-gcba.gov.ar). 

La Dirección General de Calidad Institucional y Gobierno Abierto (DGCIGA) es responsable de la implementación del estándar Open Contracting y de la publicación de los OCDS. Ante cualquier comentario o duda puede contactarse por mail a través de [gobiernoabierto@buenosaires.gob.ar](mailto: gobiernoabierto@buenosaires.gob.ar). Cuando nos envíe sus comentarios, realizaremos un análisis y seguimiento del tema planteado, posteriormente nos pondremos en contacto para informar sobre los resultados y/o acciones posteriores.
 

## Documentación Adicional 

La [Ley 104 de Acceso a la Información Pública](buenosaires.gob.ar/gobierno/ley-ndeg-104) establece la obligación de los distintos sujetos obligados de publicar en sus respectivas páginas web, de manera completa y actualizada y en lo posible en formatos abiertos y reutilizables, la información relativa a contrataciones públicas.

La normativa completa que regula la compra y contratación de bienes y servicios de la ciudad, que incluye la Ley Nº 2090 y su decreto reglamentario Decreto N° 326/17, se encuentran disponibles en buenosairescompras.gob.ar/normativa.aspx.

El Pliego Único de Bases y Condiciones Generales para los procesos de compras y contrataciones mediante BAC, aprobado por Disposición Nº 396/DGCYC/14 se encuentra disponible en el portal de compras, tanto en la sección “Normativa” como en cada uno de los procesos tramitados por esa vía. 
