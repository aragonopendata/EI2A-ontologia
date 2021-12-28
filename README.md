![](./docs/images/logo_gobiernodearagon_fondosocialeuropeo.png)

# EI2A. Estructura de Información Interoperable de Aragón

1. [Introducción](#1-introducción)

2. [Vocabularios](#2-vocabularios)

3. [Diagrama de alto nivel](#3-diagrama-de-alto-nivel)

4. [Diagrama UML](#4-diagrama-uml)

5. [Mantenimiento del modelo ontológico](#5-mantenimiento-del-modelo-ontológico)

6. [Descripción de entidades principales](#6-descripción-de-entidades-principales)

   6.1. [Persona](#61-persona)
 
   6.2. [Organización](#62-organización)
 
   6.3. [Lugar](#63-lugar)
 
   6.4. [Evento](#64-evento)
 
   6.5. [Legislatura](#65-legislatura)
 
   6.6. [Documento](#66-documento)
 
   6.7. [Normativa](#67-normativa)
 
   6.8. [Contrato](#68-contrato)
 
   6.9. [Licitación](#69-licitación)
 
   6.10. [Trámite administrativo](#610-trámite-administrativo)
 
   6.11. [Transporte](#611-transporte)
 
   6.12. [Tema](#612-tema)
 
   6.13. [DataCube](#613-datacube)
 
   6.14. [Dispositivo. Internet de las Cosas. IoT](#614-dispositivo-internet-de-las-cosas-iot)
 
   6.15. [Información de Datasets y Procedencia](#615-información-de-datasets-y-procedencia)
 
   [Anexo A. Organigrama del Gobierno de Aragón](#anexo-a-organigrama-del-gobierno-de-aragón)


## 1. Introducción

Este repositorio contiene la documentación del nuevo modelo ontológico EI2A, correspondiente al entregable (versión 1), relacionado con el hito de facturación: _[Nº1] 2.2.1 a) Actualización y mejoras de la web de ontologías del Gobierno de Aragón,_ ubicado en el proyecto _Lote 2 (Evolución de la infraestructura semántica de la Aragón Open Data)_.

El modelo desarrollado responde, en primer lugar, a un requisito de simplificación del modelo [EI2A en su versión 1.2.0](https://opendata.aragon.es/def/ei2a/), vigente en el momento de realización de este trabajo, con el objetivo de facilitar su comprensión por parte de los usuarios proveedores de datos y de los usuarios reutilizadores.

Por tanto, no se trata de modificar o actualizar la versión actual, sino de diseñar un nuevo modelo ontológico por completo, que mantenga los aspectos positivos del modelo actual y supere sus constatados problemas de uso y reutilización; y que ponga las bases para una evolución razonable que preserve el requisito primario de simplicidad.

Además de la sencillez, el modelo busca una flexibilidad que permita futuras extensiones. Esto se ha conseguido mediante el uso de categorizaciones con conceptos en lugar de jerarquías de clases (particularmente en Temas) y gracias a la reutilización de vocabularios estándar y generalistas para representar las entidades, evitando modelados propios y reduciendo al mínimo los atributos generados _ad-hoc_ para representar informaciones muy específicas de las entidades.

Los principios que han guiado el diseño del nuevo modelo ontológico han sido:

 - **Reusabilidad**. Evitar modelar conceptos y entidades con soluciones particulares cuando existen ontologías apropiadas y en uso.
 - **Extensibilidad**. El modelo debe permitir la incorporación de nuevas entidades y relaciones, si los datos a cargar lo precisan.   
 - **Mantenibilidad**. El nuevo modelo es más sencillo que el anterior, lo que facilitará su mantenimiento.
 - **Integridad**. En el nuevo modelo se especifican las restricciones de una manera más clara (some, only, min, max, exactly), para que los procesos de carga y reutilización puedan gestionar mejor que datos son necesarios en el modelo
 - **Usabilidad**. El uso de las propiedades no seguirá un diseño tipo “_open world_”, sino que se indican explícitamente cuáles son los atributos de cada entidad, para que los reutilizadores sepan con claridad los datos representados en cada caso.

Está disponible una [documentación HTML del modelo EI2A](https://opendata.aragon.es/def/ei2av2/), desarrollada con [LODE](https://essepuntato.it/lode/).

## 2. Vocabularios

En el nuevo modelo se ha descartado la reutilización de algunos vocabularios y ontologías que, a pesar de ser más específicos, ofrecen dudas en cuanto a su mantenimiento o vigencia; y otros que, siendo vigentes y apropiados, resultarían en una mayor complejidad del modelo EI2A sin aportar ventajas en el uso o reutilización.

En el siguiente listado se sumarizan las ontologías y vocabularios reutilizados en la definición del nuevo modelo ontológico del EI2A:

-   **_OWL:_** Lenguaje de la web semántica para definir una ontología y representar conocimiento acerca de cosas, grupos de cosas y sus relaciones. Véase [http://www.w3.org/2002/07/owl](http://www.w3.org/2002/07/owl).
-   **_RDF Schema:_** Vocabulario de uso general que se utiliza en el modelado de esquemas en RDF para la creación de otros Vocabularios. Véase [http://www.w3.org/2000/01/rdf-schema](http://www.w3.org/2000/01/rdf-schema).
-   **_XML Schema:_** Lenguaje de esquema utilizado para describir la estructura y las restricciones de los contenidos de los documentos XML de una forma muy precisa, más allá de las normas sintácticas impuestas por el propio lenguaje XML. Para facilitar la interoperabilidad de algunos metadatos se utilizan algunos de los tipos primitivos utilizados por el Esquema de definición de XML. Véase [http://www.w3.org/2001/XMLSchema](http://www.w3.org/2001/XMLSchema).
-   **_Simple Knowledge Organization System (SKOS):_** Ontología para definir sistemas de organización del conocimiento (vocabularios, tesauros, etc.). Véase [http://www.w3.org/2004/02/skos](http://www.w3.org/2004/02/skos).
-   **_Dublin Core Metadata Terms:_** Conjunto completo de términos elaborado por la iniciativa de metadatos de Dublin Core, entidad de referencia en el desarrollo de metadatos de amplio ámbito de actuación, así como en las buenas prácticas para su gestión. Los términos de Dublin Core incluyen clases, propiedades, vocabularios, esquemas comunes de codificación y tipos. Véase [http://dublincore.org/](http://dublincore.org/).
-   **_The Organization Ontology (ORG):_** Ontología desarrollada por W3C para describir organizaciones. Véase [https://www.w3.org/TR/vocab-org/](https://www.w3.org/TR/vocab-org/).
-   **_Friend Of A Friend:_** Ontología que describe personas, sus actividades y sus relaciones con otras personas y objetos. Véase [http://xmlns.com/foaf/0.1/](http://xmlns.com/foaf/0.1/).
-   **_BIO._** A vocabulary for biographical information. Sólo se usa el atributo biography para expresar la biografía en texto de los cargos del Gobierno de Aragón. [https://vocab.org/bio/](https://vocab.org/bio/)
-   **_Schema.org:_** Esquema ampliamente reconocido y utilizado por una amplia variedad de sitios Web (Google, Bing, Yahoo, …), que contiene diversas entidades de múltiples ámbitos para etiquetar el contenido de la Web. En el modelo de EI2A se usa para modelar documentos, expedientes, trámites y eventos. Véase [http://schema.org](http://schema.org/).
-   **_vCard._** vCard Ontology. Es una ontología que mapea la especificación vCard, que se usa para describir personas y organizaciones, en particular su dirección con datos de geoposicionamiento. [https://www.w3.org/TR/vcard-rdf/](https://www.w3.org/TR/vcard-rdf/)
-   **_GTFS (General Transport Feed Specification):_** Vocabulario utilizado para modelar aspectos de transporte. Se mantiene este vocabulario, a pesar de [no estar actualizado desde el año 2016](https://github.com/OpenTransport/linked-gtfs) y de que también podría modelarse con schema.org; porque permitiría generar y publicar archivos GTFS de manera más directa y sencilla. Véase en [https://github.com/OpenTransport/linked-gtfs/blob/master/spec.md](https://github.com/OpenTransport/linked-gtfs/blob/master/spec.md) y [http://vocab.gtfs.org/gtfs.ttl](http://vocab.gtfs.org/gtfs.ttl)
-   **_ELI:_** European Legislation Identifier (ELI) legislación en un formato normalizado, de manera que pueda localizarse, intercambiarse y reutilizarse por encima de las fronteras Véase [http://data.europa.eu/eli/ontology](http://data.europa.eu/eli/ontology).
-   **_OCDS._** Open Contracting Data Standard (ontología generada en el proyecto They Buy for You). Modela los contratos públicos y el proceso de contratación. [http://data.tbfy.eu/ontology/ocds#](http://data.tbfy.eu/ontology/ocds)
-   **_SSN._** Semantic Sensor Network Ontology. Es una recomendación del W3C que permite el modelado de sistemas, sensores y dispositivos en el ámbito de IoT. Se aplica en EI2A para el modelado de sistemas de gestión de agua, sustituyendo a WISDOM, y permitirá la incorporación de otros sistemas y dispositivos en el futuro. Véase: [https://www.w3.org/TR/vocab-ssn/](https://www.w3.org/TR/vocab-ssn/)
-   **_Datacube._** The RDF Data Cube Vocabulary. Es una recomendación del W3C para publicar datos multidimensionales, como pueden ser los datos estadísticos, en un modo que permite su enlazado con datasets y conceptos. Ya se aplica en los datos incorporados en Aragopedia desde el IAEST (Instituto Aragonés de Estadística) y se utilizan en EI2A para modelar datos como el presupuesto de Aragón. [https://www.w3.org/TR/vocab-data-cube/](https://www.w3.org/TR/vocab-data-cube/)
-   **_wGS84_pos:_** Describe puntos a través de su latitud, longitud y altitud dentro de la especificación WGS84. Véase [http://www.w3.org/2003/01/geo](http://www.w3.org/2003/01/geo).
-   **_OWL-Time:_** Ontología utilizada para describir conceptos temporales desarrollada por el W3C. Incluye elementos como instantes, intervalos de tiempo, duraciones y momentos específicos. Véase [http://www.w3.org/2006/time](http://www.w3.org/2006/time).
-   **_PROV-O._** The PROV Ontology. Proponemos que el proceso de carga en el nuevo grafo genere información de la procedencia de cada entidad, modelando mediante esta recomendación del W3C. Cada entidad cargada o actualizada incorporará un triple informando del proceso de carga del que proviene. [https://www.w3.org/TR/prov-o/](https://www.w3.org/TR/prov-o/)
-   **_DCAT._** Data Catalog Vocabulary. Se trata de una recomendación del W3C para facilitar la interoperabilidad de entre catálogos de datos publicados en la web y permite la descripción de datasets y servicios de datos. En el ámbito del proyecto se usará, además, para mostrar información explicativa del dato y su procedencia. [https://www.w3.org/TR/vocab-dcat-2/](https://www.w3.org/TR/vocab-dcat-2/)

Durante el proceso de análisis se han descartado los siguientes vocabularios:

- **_WISDOM_** (Water analytics and Intelligent Sensing for Demand Optimised Management, ver [Project impact on standardization and liaison activities. Final report](https://cordis.europa.eu/docs/projects/cnect/5/619795/080/deliverables/001-WISDOMWP5D55FinalDelivered.pdf)). La ontología desarrollada, en el ámbito de un proyecto europeo, es muy completa y permite modelar los dispositivos y procesos relacionados con la gestión inteligente del agua (_smart water_). Su uso en el nuevo modelo presentaba dos inconvenientes. En primer lugar, resulta demasiado complejo para el caso de uso de los datos de Aragón. En segundo, el modelo WISDOM no parece estar mantenido y finalmente no ha conseguido formar parte de un grupo de interés de W3C. Los datos de dispositivos de agua de Aragón quedan suficientemente modelados con SSN (ver más arriba) que, además, era una de las ontologías reutilizadas por WISDOM.
- **_OpenBudget_** (ver [https://github.com/openbudgets/data-model](https://github.com/openbudgets/data-model)) El proyecto no está mantenido y, a pesar de que la ontología es adecuada para modelar el presupuesto de una administración pública, resulta demasiado compleja para el uso esperado. Los presupuestos se modelarán con Datacube.
- **_HARMONET:_** Ontología generada para modelar aspectos de turismo. No se ha mantenido ni incorporado a ningún proceso de estandarización. De momento las entidades de turismo se modelarán como organizaciones y lugares usando los temas para categorizarlas en el ámbito del turismo.
- **_Categorization Ontology:_** Ontología generada para categorizar webs, subdominios o portales del Gobierno de Aragón. Está basada en la categorización de enlinea.aragon.es. Véase [CategorizationOntology.owl](https://opendata.aragon.es/def/ei2a/CategorizationOntology.owl). Se sustituye por una categorización SKOS.
- **_ISA Programme Person Core Vocabulary:_** Vocabulario que proporciona un conjunto de clases y propiedades para describir personas. Véase [https://www.w3.org/ns/person](https://www.w3.org/ns/person).

## 3. Diagrama de alto nivel

En el siguiente diagrama presentamos el modelo de alto nivel y las relaciones de las entidades principales propuestas:

![](docs/images/ei2a-diagrama-alto-nivel.png)

## 4. Diagrama UML

![](docs/images/ei2a-diagrama.jpg)

## 5. Mantenimiento del modelo ontológico

Para el mantenimiento del modelo ontológico proponemos usar el presente repositorio de GitHub (https://github.com/aragonopendata/EI2A-ontologia), del siguiente modo:

- Generación de un nuevo proyecto en GitHub para albergar la documentación y el archivo OWL generado.
- Configuración de GitHub pages para el acceso a la documentación.
- Uso de issues para gestionar los reportes de errores y las peticiones de cambio.
- Generación de una rama para trabajar sobre los cambios.
  - Rama de versión cuando sea un cambio mayor.
  - Rama relacionada con el issue cuando se trate de solucionar un error o un cambio menor.
- Generación de una release correspondiente a cambios mayores. Podrá incluir cambios en el documento OWL, documento HTML, diagramas y el presente documento.

Además de la documentación de GitHub, generamos una documentación HTML usando [LODE](https://essepuntato.it/lode/), al estilo de la existente actualmente, en la que se describirán las entidades, atributos, propiedades y relaciones de todos los objetos.

## 6. Descripción de las entidades principales

### 6.1. Persona

#### 6.1.1 Descripción de vocabulario y entidad seleccionada

Para modelar a las personas utilizamos dos vocabularios:

- **_FOAF_**. Datos públicos de filiación y relación con su puesto en una organización, si lo tiene.
- **_ORG_**. Puesto ocupado por la persona en una organización. El puesto puede contar con fechas de vigencia y está relacionado con un rol.
- **_BIO_**. Biografía en formato texto de la persona.

#### 6.1.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-Person.jpg)

#### 6.1.3. Definición avanzada de los atributos

Persona
|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|Person|dc:identifier|Identificador de la persona|String|0..1|
| |foaf:name|Nombre completo|String|1|
| |foaf:givenName|Nombre |String|1|
| |foaf:familyName|Apellidos |String|1|
| |foaf:phone|Teléfono|String|0..1|
| |bio:biography|Biografía|String|0..1|
| |foaf:mbox|Email|String|0..1|
| |foaf:homepage|Página web|String|0..1|
| |foaf:img|Foto|String|0..1|
| |org:holds|Enlace con el puesto|org:Post|0..* |
|org:Post|dc:identifier|Identificador el puesto|String|1|
| |ei2a:order|Orden|Int|1|
| |org:role|Enlace con Rol|org:Role|1|
| |time:hasBeginning|Fecha de inicio|Date|0..1|
| |time:hasEnd|Fecha de Final|Date|0..1|
| |org:postIn|Enlace con Organización|org:Organization|0..*|
| |org:heldBy|Inversa de org:holds|org:Person|1|


Rol
|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|Rol|dc:identifier|Identificador del rol|String|1|
| |dc:title|Nombre del rol|String|1|


#### 6.1.4. Casos de uso

Las vistas más destacadas relacionadas con las personas son las siguientes:
|Id de vista|Descripción|Datos|Conjunto de datos |Nº de accesos|Última act.|
|:----|:----|:----|:----|:----|:----|
|160|Cargos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=160&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/organigrama-del-gobierno-de-aragon)|555|19/03/2020|
|3|Pleno municipio|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=3&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/composicion-de-plenos-municipales)|190|19/03/2020|
|69|Registro de Guías de Turismo|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=69&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/guias-turisticos-en-la-comunidad-autonoma-de-aragon)|180|19/03/2020|
|4|Pleno Comarca|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=4&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/composicion-de-plenos-comarcales)|90|19/03/2020|
|51|Composicion del Pleno de Consorcios|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=51&_pageSize=100&_page=1)| | | |
|52|Composicion del Pleno de Entidades Menores|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=52&_pageSize=100&_page=1)| | | |
|53|Composicion del Pleno de Mancomunidades|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=53&_pageSize=100&_page=1)| | | |
|54|Composicion del Pleno de Organismos Autónomos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=54&_pageSize=100&_page=1)| | | |
|56|Composicion del Pleno de Villas y Tierras|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=56&_pageSize=100&_page=1)| | | |


En la representación de una persona destaca la vista _160 – Cargos_ donde, además de ser los datos más visitados, podemos ver un ejemplo de vinculación con otras entidades como son las Organizaciones a las que pertenecen y el Cargo que ejercen en ellas.

El mapeo correspondiente a esta vista con el nuevo modelo es el siguiente (los atributos de origen que no aparecen en la siguiente tabla no se utilizan en el mapeo con el nuevo modelo):
|Atributo de origen|Entidad principal|Propiedad |Entidad relacionada|Propiedad|
|:----|:----|:----|:----|:----|
|NOMBRE|foaf:Person|foaf:name| | |
|TELEFONO|foaf:Person|foaf:phone| | |
|BIOGRAFIA|foaf:Person|bio:biography| | |
|FOTO_PATH|foaf:Person|foaf:img| | |
|EMAIL|foaf:Person|foaf:mbox| | |
|PAGINA_WEB|foaf:Person|foaf:homepage| | |
|ID_CARGO|foaf:Person -> org:Post|dc:identifier| | |
|ID_ENTIDAD|foaf:Person -> org:Post|org:postIn|org:Organization|dc:identifier|
|ORDEN|foaf:Person -> org:Post|ei2a:order| | |
|CARGO|foaf:Person -> org:Post|org:role|org:Role|dc:title|
|FECHA_INI|foaf:Person -> org:Post|time:hasBeginning| | |
|FECHA_FIN|foaf:Person -> org:Post|time:hasEnd| | |
| | | |


### 6.2. Organización	

#### 6.2.1. Descripción de vocabulario y entidad seleccionada
Para modelar a las organizaciones y sus centros utilizamos dos vocabularios:

- ***ORG***. Modela datos públicos de filiación de la organización y la relación con otras organizaciones (suborganización; antecesora y sucesora mediante ChangeEvent) e incluye relaciones inversas hacia centros, contratos y puestos. La clasificación SKOS permitirá diferenciar varios tipos de organizaciones, desde las unidades administrativas del gobierno a los hoteles rurales.
- ***vCARD***. Modela lugares con direcciones y geoposicionamiento, para definir dónde se encuentra un centro.

#### 6.2.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-Organization.jpg)                 


#### 6.2.3. Definición avanzada de los atributos

Organización	

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|org:Organization|dc:identifier|Identificador|String|0..1|
| |org:identifier|Identificador de la organización|String|1|
| |dc:title|Nombre |String|1|
| |org:subOrganizationOf|Enlace con Organización padre|org:Organization|0..*|
| |ei2a:legislature|Enlace con legislatura|ei2a:Legislature|0..1|
| |dc:description|Observaciones|String |0..1|
| |ei2a:order|Orden|int|0..1|
| |org:hasSite|Enlace con Centro|org:Site|0..* |
| |foaf:homepage|Página web|String|0..1|
| |ocds:isSupplierFor|Enlace con el contrato|ocds:Contract|0..* |
| |ocds:isTendererFor|Enlace con la licitación|ocds:Tender|0..* |
| |org:hasPost|Inversa de org:postIn|org:Post|0..* |
| |org:classification|Enlace categoría|Skos:Concept|1|
| |org:resultedFrom|Enlace a evento  creación de organización|Org:ChangeEvent|0..1|
| |org:linkedTo|Enlace con Organización relacionada|org:Organization|0..*|
| |org:changedBy|Enlace con evento  modificación de organización|Org:ChangeEvent|0..1|
|org:ChangeEvent|org:originalOrganization|Organización que ha sido creada tras un evento, inversa org:resultedFrom|org:Organization|0..1|
| |org:resultingOrganization|Organización que ha sido modificada tras un evento, inversa org:changedBy|org:Organization|0..1|
| |prov:startedAtTime|Fecha de inicio del cambio|date|1|
| |prov:endedAtTime|Fecha de Fin del cambio|date|0..1|
| | | |
| | | |


Centro y Lugar	

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|org:Site|dc:identifier|Identificador|String|1|
| |dc:title|Nombre|string|0..1|
| |org:siteAddress|Enlace con lugar|vcard:Location|0..1|
|vcard:Location|vcard:fn|Nombre|string|0..1|
| |vcard:region|Provincia|string|0..1|
| |vcard:locality|Localidad |String|0..1|
| |vcard:postal-code|Código postal|int |0..1|
| |vcard:street-address|Dirección  |String |0..1|
| |vcard:email|Email|string|0..1|
| |vcard:tel|Teléfono|int |0..1|
| |vcard:org|Enlace con organización|org:Organization|0..1|
| |vcard:hasGeo|Enlace con una entidad geoespacial (long, lat, shape, height)|geo:SpatialThing|0..* |
| |wgs84_pos:lat|Latitud|Double|0..1|
| |wgs84_pos:long|Longitud|Double |0..1|
| |org:siteAddress|Enlace con lugar|org:Site|0..1|

#### 6.2.4. Casos de uso

Las vistas relacionadas con organización, ordenadas según el interés generado en el banco de datos son:

|Id de vista|Descripción|Datos|Conjunto de datos |Nº de accesos|Última act.|
|:----|:----|:----|:----|:----|:----|
104|IAF polígonos industriales|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=104&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/suelo-y-poligonos-industriales-de-aragon)|1506|19/03/2020|
24|Datos de Mancomunidades|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=24&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/informacion-general-de-mancomunidades-de-aragon)|616|19/03/2020|
159|Entidades|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=159&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/organigrama-del-gobierno-de-aragon)|556|19/03/2020|
11|Datos Municipio|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=11&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/informacion-general-de-los-municipios-de-aragon)|422|19/03/2020|
67|Registro de Cafeterías y Restaurantes|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=67&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/cafeterias-y-restaurantes-en-la-comunidad-autonoma-de-aragon)|414|19/03/2020|
65|Registro de Alojamientos hoteleros|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=65&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/alojamientos-hoteleros-en-la-comunidad-autonoma-de-aragon)|374|19/03/2020|
88|SGT Agricultura, Comarcas agrarias|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=88&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/comarcas-agrarias-de-aragon)|366|09/09/2015|
64|Registro de Albergues y Refugios|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=64&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/albergues-y-refugios-en-la-comunidad-de-aragon)|324|19/03/2020|
286|IGEAR - Centros de Salud|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=286&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/sanidad)|316|14/04/2020|
287|IGEAR - Hospitales|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=287&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/sanidad)|316|14/04/2020|
288|IGEAR - Centros de Salud Mental|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=288&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/sanidad)|316|14/04/2020|
73|Registro de Alojamientos de Turismo Rural|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=73&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/alojamientos-de-turismo-rural-en-la-comunidad-autonoma-de-aragon)|301|19/03/2020|
63|Registro de Agencias de Viaje|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=63&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/agencias-de-viaje-de-aragon)|268|19/03/2020|
10|Datos Comarca|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=10&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/informacion-general-de-las-comarcas-de-aragon)|252|19/03/2020|
16|Datos de diputación|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=16&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/informacion-general-de-las-diputaciones-provinciales-de-aragon)|244|19/03/2020|
26|Datos de Núcleos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=26&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/nucleos-de-aragon)|215|19/03/2020|
89|SGT Agricultura, Oficinas comarcales|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=89&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/oficinas-comarcales-de-aragon)|209|10/09/2015|
241|INAGA Terrenos cinegéticos y no cinegéticos de Aragón|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=241&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/registro-de-terrenos-cinegeticos-de-aragon)|205|01/10/2018|
66|Registro de Apartamentos turísticos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=66&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/apartamentos-turisticos-en-la-comunidad-autonoma-de-aragon)|191|19/03/2020|
68|Registro de Campings Turísticos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=68&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/campings-turisticos-en-la-comunidad-autonoma-de-aragon)|179|19/03/2020|
70|Registro de Oficinas de Turismo|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=70&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/oficinas-de-turismo-en-la-comunidad-autonoma-de-aragon)|178|19/03/2020|
167|IGEAR - Centros Educativos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=167&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/educacion-y-cultura)|178|25/11/2020|
282|Bibliotecas - Definición de las bibliotecas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=282&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/catalogo-de-la-red-de-bibliotecas-de-aragon-en-formatos-abiertos)|171|20/02/2020|
72|Registro de Empresas de Turismo Activo|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=72&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/registro-de-empresas-de-turismo-activo)|148|19/03/2020|
17|Direcciones de interés|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=17&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/informacion-de-diferentes-organismos-aragoneses)|143|19/03/2020|
20|Datos de Entidades Singulares|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=20&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/informacion-general-de-entidades-singulares-de-aragon)|135|19/03/2020|
12|Agrupación Secretarial|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=12&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/agrupaciones-secretariales-de-aragon)|132|19/03/2020|
22|Datos de Fundaciones|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=22&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/fundaciones-existentes-en-el-registro-de-administracion-local)|129|19/03/2020|
71|Registro de Puntos de Información Turística|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=71&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/puntos-de-informacion-turistica-en-la-comunidad-autonoma-de-aragon)|129|19/03/2020|
13|Consorcios|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=13&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/consorcios-en-aragon)|114|19/03/2020|
28|Datos de Organizaciones Complementarias|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=28&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/organizaciones-complementarias-de-gobierno-en-las-administraciones-locales-aragonesas)|102|19/03/2020|
246|Responsable del tratamiento|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=246&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/registro-de-actividades-de-tratamiento-de-datos-de-caracter-personal-del-gobierno-de-aragon)|92|28/01/2020|
247|Encargado del tratamiento|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=247&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/registro-de-actividades-de-tratamiento-de-datos-de-caracter-personal-del-gobierno-de-aragon)|92|28/01/2020|
248|Delegado de protección de datos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=248&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/registro-de-actividades-de-tratamiento-de-datos-de-caracter-personal-del-gobierno-de-aragon)|92|28/01/2020|
278|Información al ciudadano de protección de datos - |[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=278&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/registro-de-actividades-de-tratamiento-de-datos-de-caracter-personal-del-gobierno-de-aragon)|92|28/01/2020|
27|Datos de Organismo Autónomo|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=27&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/informacion-general-de-diferentes-entes-vinculados-a-la-administracion-local-patronatos-medios-institutos-etc)|85|19/03/2020|
19|Datos de Entidad Menor|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=19&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/informacion-general-de-entidades-menores-de-aragon)|84|19/03/2020|
164|IGEAR - Oficinas del Consumidor|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=164&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/consumo)|33|14/05/2018|
34|Datos de Sociedad Mercantil|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=34&_pageSize=100&_page=1)| | | |
35|Datos de Villas y Tierras|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=35&_pageSize=100&_page=1)| | | |
57|Relaciones de Comarca|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=57&_pageSize=100&_page=1)| | | |
58|Relaciones de Entidades Singulares|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=58&_pageSize=100&_page=1)| | | |
59|Relaciones de Fundaciones|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=59&_pageSize=100&_page=1)| | | |
60|Relaciones de Mancomunidades|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=60&_pageSize=100&_page=1)| | | |
61|Relaciones de Villas y Tierras|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=61&_pageSize=100&_page=1)| | | |
143|CRA - Centros|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=143&_pageSize=100&_page=1)| | | |
283|Bibliotecas - Definición de las sucursales|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=283&_pageSize=100&_page=1)| | | |
		

Para la representación de las organizaciones destaca la vista 159 – Entidades donde encontramos la relación con las entidades de Centro y a su vez, con Lugar. También es posible encontrar la relación jerárquica entre las unidades organizativas y sus organizaciones padre. Por último, cada organización se encuentra ubicada en el tiempo gracias a la relación con la entidad Legislatura.

El mapeo correspondiente a esta vista con el nuevo modelo es el siguiente (los atributos de origen que no aparecen en la siguiente tabla no se utilizan en el mapeo con el nuevo modelo):

|Atributo de origen|Entidad principal|Propiedad |Entidad relacionada|Propiedad|
|:----|:----|:----|:----|:----|
|ID_ENTIDAD|org:Organization|dc:identifier| | |
|ID_ENTIDAD_PADRE|org:Organization|org:subOrganizationOf|org:Organization|dc:identifier|
|ID_LEGISLATURA|org:Organization|ei2a:legislature|ei2a:Legislature|dc:identifier|
|ORDEN|org:Organization|ei2a:order| | |
|NOMBRE|org:Organization|dc:title| | |
|OBSERVACIONES|org:Organization|dc:description| | |
|COD_SIU|org:Organization|org:identifier| | |
|PAGINA_WEB|org:Organization|foaf:homepage| | |
|EDIFICIO|org:Organization -> org:Site|dc:title| | |
|DIRECCION|org:Organization -> org:Site|vcard_siteAddress|vcard:Location|vcard:street-address|
|CP|org:Organization -> org:Site|vcard_siteAddress|vcard:Location|vcard:postal-code|
|LOCALIDAD|org:Organization -> org:Site|vcard_siteAddress|vcard:Location|vcard:locality|
|PROVINCIA|org:Organization -> org:Site|vcard_siteAddress|vcard:Location|vcard:region|
|TELEFONO|org:Organization -> org:Site|vcard_siteAddress|vcard:Location|vcard:tel|
|EMAIL|org:Organization -> org:Site|vcard_siteAddress|vcard:Location|vcard:email|
|COOR_X|org:Organization -> org:Site|vcard_siteAddress|vcard:Location|wgs84_pos:lat|
|COOR_Y|org:Organization -> org:Site|vcard_siteAddress|vcard:Location|wgs84_pos:long|



### 6.3. Lugar

#### 6.3.1. Descripción de vocabulario y entidad seleccionada

Para modelar los lugares utilizamos un vocabulario:

- ***vCARD***. Modela lugares con direcciones y geoposicionamiento.
- ***wGS84_pos***. Describe puntos a través de su latitud y longitud, dentro de la especificación WGS84.


#### 6.3.2. Diagrama de la entidad
 
![](docs/images/ei2a-diagrama-Location.jpg) 

#### 6.3.3. Definición avanzada de los atributos

Lugar

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|vcard:Location|vcard:fn|nombre|string|0..1|
| |vcard:region|Provincia|string|1|
| |vcard:locality|Localidad |String|1|
| |vcard:postal-code|Código postal|int |1|
| |vcard:street-address|Dirección  |String |1|
| |vcard:email|Email|string|0..1|
| |vcard:tel|Teléfono|int |0..1|
| |vcard:org|Enlace con organización|org:Organization|1|
| |vcard:hasGeo|Enlace con una entidad geoespacial (long, lat, shape, height)|geo:SpatialThing|0..* |
| |wgs84_pos:lat|Latitud|Double|0..1|
| |wgs84_pos:long|Longitud|Double |0..1|
| |org:siteAddress|Enlace con lugar|org:Site|0..1|


#### 6.3.4. Casos de uso

Las vistas que podemos relacionar con Lugar son las siguientes:

|Id de vista|Descripción|Datos|Conjunto de datos |Nº de accesos|Última act.|
|:----|:----|:----|:----|:----|:----|
102|Turismo de Aragon, Senderos Rutas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=102&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/senderos-de-aragon)|669|19/03/2020|
157|IAA Depuradoras núcleos de población servidos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=157&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/depuradoras-de-agua-residual-gestionadas-o-financiadas-por-la-c-a-de-aragon)|255|19/03/2020|
261|Provincias|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=261&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/registro-de-actividades-de-tratamiento-de-datos-de-caracter-personal-del-gobierno-de-aragon)|93|28/01/2020|
262|Códigos de país|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=262&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/registro-de-actividades-de-tratamiento-de-datos-de-caracter-personal-del-gobierno-de-aragon)|93|28/01/2020|
142|CRA - Localidades|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=142&_pageSize=100&_page=1)| | | |
168|IGEAR - Zonas Educativas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=168&_pageSize=100&_page=1)| | | |
170|IGEAR - Suelo Industrial de Aragon|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=170&_pageSize=100&_page=1)| | | |
185|IGEAR - Edificaciones Zonas Verdes Urbanas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=185&_pageSize=100&_page=1)| | | |
197|IGEAR - Grandes Dominios de Paisaje|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=197&_pageSize=100&_page=1)| | | |
199|IGEAR - Miradores de paisaje|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=199&_pageSize=100&_page=1)| | | |
200|IGEAR - Recorridos de interes paisajistico|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=200&_pageSize=100&_page=1)| | | |
201|IGEAR - Regiones de Paisaje|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=201&_pageSize=100&_page=1)| | | |
202|IGEAR - Unidades de paisaje|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=202&_pageSize=100&_page=1)| | | |
215|IGEAR - Instalaciones Sanitarias|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=215&_pageSize=100&_page=1)| | | |
216|IGEAR - Otros Senderos de Aragon: Miradores|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=216&_pageSize=100&_page=1)| | | |
217|IGEAR - Otros Senderos de Aragon: Senderos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=217&_pageSize=100&_page=1)| | | |
218|IGEAR - Senderos Turisticos de Aragon|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=218&_pageSize=100&_page=1)| | | |
219|IGEAR - Señaletica de Senderos Turisticos de Aragon|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=219&_pageSize=100&_page=1)| | | |
285|IGEAR - Áreas de Salud|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=285&_pageSize=100&_page=1)| | | |
289|IGEAR- Zonas de Salud - |[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=289&_pageSize=100&_page=1)| | | |
290|IGEAR - Indicadores geométricos COVID-19|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=290&_pageSize=100&_page=1)| | | |

Se puede obtener una representación en la vista 159 – Entidades donde aunque su entidad principal es Organización, es posible visualizar la vinculación con Lugar. El mapeo se puede revisar en el apartado 6.2.4 de este documento.

### 6.4. Evento

#### 6.4.1. Descripción de vocabulario y entidad seleccionada

Para modelar los eventos utilizamos el vocabulario Schema:

- ***Schema.org***. Utilizamos la clase Event con sus atributos relevantes al caso.

#### 6.4.2. Diagrama de la entidad 

![](docs/images/ei2a-diagrama-Event.jpg) 
 
#### 6.4.3. Definición avanzada de los atributos

Evento

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|schema:Event|schema:identifier|Identificador del evento|string|0..1|
| |schema:name|Nombre del evento|string|1|
| |schema:description|Descripción |string|1|
| |schema:startDate|Fecha de inicio|Date |1|
| |schema:endDate|Fecha de fin|Date|0..1|
| |schema:eventSchedule|Horario del evento  |string|0..1|
| |schema:image|Imagen|string|0..1|
| |schema:location|Enlace con lugar del evento|vcard:Location|0..1|


#### 6.4.4. Casos de uso

Las vistas más destacadas relacionadas con los eventos son las siguientes:

|Id de vista|Descripción|Datos|Conjunto de datos |Nº de accesos|Última act.|
|:----|:----|:----|:----|:----|:----|
62|Registro de llamadas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=62&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/consulta-consumidores)|335|14/05/2018|
90|DG Relaciones Institucionales, Procesos Electorales|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=90&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/resultados-electorales-agrupados-a-escala-municipal-historico)|112|11/11/2020|
15|Datos de cursos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=15&_pageSize=100&_page=1)| | | |
32|Datos de Postgrado|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=32&_pageSize=100&_page=1)| | | |


En la vista 62 – Registro de llamadas podemos ver un ejemplo de vinculación de Evento con otras entidades como Lugar.
El mapeo correspondiente a esta vista con el nuevo modelo es el siguiente (los atributos de origen que no aparecen en la siguiente tabla no se utilizan en el mapeo con el nuevo modelo):

|Atributo de origen|Entidad principal|Propiedad |Entidad relacionada|Propiedad|
|:----|:----|:----|:----|:----|
|NUMERO_REG|schema:Event|schema:identifier| | |
|FECHA_REG|schema:Event|schema:startDate| | |
|PROVINCIA|schema:Event|schema:location|vcard:location|vcard:region|
|LOCALIDAD|schema:Event|schema:location|vcard:location|vcard:locality|
| | |


### 6.5. Legislatura

#### 6.5.1. Descripción de vocabulario y entidad seleccionada
Hemos decidido modelar legislatura a pesar de que sólo se va a cargar la actual, porque pensamos que en un futuro podrían añadirse más. La hemos modelado como una subclase de schema:Event:

- ***Schema.org***. El modelado de evento se ajusta a lo que define a una legislatura.

#### 6.5.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-Legislature.jpg)   

#### 6.5.3. Definición avanzada de los atributos

Legislatura

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|ei2a:Legislature|schema:identifier|Identificador de la legislatura|String|1|
| |schema:name|Nombre de la legislatura|String|1|
| |schema:startDate|Fecha de inicio|Date|0..1|
| |schema:endDate|Fecha final|Date|0..1|

#### 6.5.4. Casos de uso

La vista relacionada con la legislatura es la siguiente:

|Id de vista|Descripción|Datos|Conjunto de datos |Nº de accesos|Última act.|
|:----|:----|:----|:----|:----|:----|
|158|Periodo de legislatura|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=158&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/organigrama-del-gobierno-de-aragon)|556|19/03/2020|

El mapeo correspondiente a esta vista con el nuevo modelo es el siguiente (los atributos de origen que no aparecen en la siguiente tabla no se utilizan en el mapeo con el nuevo modelo):

|Atributo de origen|Entidad principal|Propiedad |Entidad relacionada|Propiedad|
|:----|:----|:----|:----|:----|
|ID_LEGISLATURA|ei2a:Legislature|schema:identifier| | |
|NOMBRE|ei2a:Legislature|schema:name| | |
|FECHA_INI|ei2a:Legislature|schema:startDate| | |
|FECHA_FIN|ei2a:Legislature|schema:endDate| | |


### 6.6. Documento

#### 6.6.1. Descripción de vocabulario y entidad seleccionada

Para modelar los lugares utilizamos el vocabulario:

- ***Schema.org***. Hemos optado por modelar con schema:CreativeWork, explicitando atributos opcionales que se usarán en función del tipo de documento que se quiera representar en el grafo; como expedientes, obras de arte, símbolos municipales o páginas web. Se complementa con algunos términos de ELI y Dublin Core e incluye relaciones con Organización, Centro y Lugar.

#### 6.6.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-CreativeWork.jpg) 
 
#### 6.6.3. Definición avanzada de los atributos

Documento

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|schema:CreativeWork|schema:identifier|Identificador|String|1|
| |schema:title|Título|String|1|
| |org:organization|Enlace con organización|org:Organization|0..1|
| |org:hasSite|Enlace con centro|org:Site|0..1|
| |org:siteAddress|Enlace con lugar|vcard:Location|0..1|
| |eli:first_date_entry_in_force|Fecha de entrada en vigor|Date|0..1|
| |eli:date_applicability|Fecha de aplicación|Date|0..1|
| |schema:abstract|Descripción|String|0..* |
| |schema:image|Imagen |String|0..1|
| |schema:license|Licencia |String|0..1|
| |schema:url|url |String|0..1|
| |schema:contributor|Enlace con persona |Foaf:Person|0..* |
| |schema:hasPart|Enlace con documento|schema:CreativeWork|0..1|
| |schema:isPartOf|Inversa de schema:hasPart|schema:CreativeWork|0..1|
| |schema:material|Material|String|0..1|
| |schema:size|Tamaño |String|0..1|
| |schema:temporal|Literal de fecha (año)|String|0..1|
| |schema:locationCreated|Enlace con lugar de creación|vcard:Location|0..1|
| |schema:citation|Bibliografía|String|0..1|
| |dcterm:provenance|Decreto|String|0..1|
| |schema:version|Edición|String|0..1|
| |schema:publisher|Editorial |String|0..1|
| |schema:creator|Creador|String|0..1|
| |schema:inLanguage|Idioma|String|0..1|
| |schema:sdPublisher|ente que obtiene la información|org:Organization|0..1|
| |schema:sdDatePublished|fecha en la que se obtiene la información|Date|0..1|
| |schema:datePublished|fecha de primera publicación|Date|0..1|
| |schema:expires|Fecha de suspensión|Date|0..1|


#### 6.6.4. Casos de uso

Las vistas más destacadas relacionadas con los documentos son las siguientes:

|Id de vista|Descripción|Datos|Conjunto de datos |Nº de accesos|Última act.|
|:----|:----|:----|:----|:----|:----|
77|Planeamiento General|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=77&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/expedientes-de-planeamiento-general-de-aragon-de-la-direccion-general-de-urbanismo)|304|25/11/2020|
75|Modificaciones de Planeamiento General|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=75&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/expedientes-de-modificaciones-de-planeamiento-general-y-de-modificaciones-de-delimitaciones-de-suelo-urbano-de-aragon-de-la-direccion-general-de-urbanismo)|255|06/11/2020|
76|Planeamiento de Desarrollo|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=76&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/expedientes-de-planeamiento-de-desarrollo-de-aragon-de-la-direccion-general-de-urbanismo)|147|19/03/2020|
74|Modificaciones de Planeamiento de Desarrollo|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=74&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/expedientes-de-modificaciones-de-planeamiento-de-desarrollo-de-aragon-de-la-direccion-general-de-urbanismo)|132|19/03/2020|
237|ENERGIA - Cert. Data|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=237&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo?texto=registro%20de%20certificaci%C3%B3n)|129|06/06/2018|
260|Meta datos estado|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=260&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/registro-de-actividades-de-tratamiento-de-datos-de-caracter-personal-del-gobierno-de-aragon)|94|28/01/2020|
103|DG Cultura y Patrimonio, Colecciones de Museos de Aragon|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=103&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/colecciones-y-recursos-de-los-museos--gestionados-por-el-gobierno-de-aragon)|93|25/11/2020|
265|Dominios|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=265&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo?texto=subdominios)|72|30/10/2019|
2|Símbolos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=2&_pageSize=100&_page=1)| | | |
25|Datos de Noticias|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=25&_pageSize=100&_page=1)| | | |
30|Datos de Planeamiento|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=30&_pageSize=100&_page=1)| | | |
31|Datos de Plantillas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=31&_pageSize=100&_page=1)| | | |
145|DARA|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=145&_pageSize=100&_page=1)| | | |
240|INAGA - Resoluciones publicadas boa y expedientes publicados|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=240&_pageSize=100&_page=1)| | | |
242|Actividad de Tratamiento de datos personales|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=242&_pageSize=100&_page=1)| | | |
259|Medidas de seguridad|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=259&_pageSize=100&_page=1)| | | |
277|Información al ciudadano de primer nivel - |[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=277&_pageSize=100&_page=1)| | | |
279|Información al ciudadano de segundo nivel - |[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=279&_pageSize=100&_page=1)| | | |
280|Bibliotecas - Títulos existentes|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=280&_pageSize=100&_page=1)| | | |
281|Bibliotecas - Ejemplares|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=281&_pageSize=100&_page=1)| | | |

Si revisamos en detalle la vista 77 – Planeamiento General , podemos ver un ejemplo de vinculación con otra entidad como la Organización. El mapeo correspondiente a esta vista con el nuevo modelo es el siguiente (los atributos de origen que no aparecen en la siguiente tabla no se utilizan en el mapeo con el nuevo modelo):

|Atributo de origen|Entidad principal|Propiedad |Entidad relacionada|Propiedad|
|:----|:----|:----|:----|:----|
|NUM_EXPTE|schema:CreativeWork|schema:identifier| | |
|TITULO|schema:CreativeWork|schema:title| | |
|MUNICIPIO_EXPEDIENTE|org:Organization|dc:identifier| | |
|PROVINCIA_EXPEDIENTE|org:Organization|dc:identifier| | |
|NOMBRE_MUNICIPIO|org:Organization|dc:title| | |
|F_ACUERDO|eli:LegalResource|eli:date_applicability| | |
|FECHA_ENTRADA|eli:LegalResource|eli:first_date_entry_in_force| | |
|F_PUB_ACUERDO|eli:LegalResource|eli:date_publication| | |
|TELEFONO|schema:CreativeWork|foaf:phone| | |
|TELEFONO|schema:CreativeWork|foaf:phone| | |
|TELEFONO|schema:CreativeWork|foaf:phone| | |
		

### 6.7. Normativa

#### 6.7.1. Descripción de vocabulario y entidad seleccionada

Para modelar las normas utilizamos el vocabulario:

- ***ELI***. Modela normas y leyes, como las ordenanzas generales y fiscales. En este caso se opta por un vocabulario específico que incluye atributos más ajustados.

#### 6.7.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-LegalResource.jpg) 
 
#### 6.7.3. Definición avanzada de los atributos

Normativa

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|eli:LegalResource|eli:date_document|Fecha del documento|Date|0..1|
| |eli:date_publication|Fecha de aplicación|Date|1|
| |eli:type_document|Enlace con tipo documento|eli:ResourceType|1|
| |eli:is_member_of|Enlace a normativa |eli:LegalResource|1|
| |eli:is_realized_by|Enlace a la expresión legal|eli:LegalExpression|1|
|eli:LegalExpression|eli:title|Título|String|1|
| |eli:language|Enlace al Lenguaje del recurso legal|eli:Language|1|
| |eli:realizes|Enlace inversa con normativa que modifica|eli:LegalResource|1|
| |eli:publisher_agent|Enlace con organización|org:Oganization|1|
| |eli:is_embodied_by|Enlace formato|eli:Format|1|
|eli:Format|eli:rightsholder_agent|Enlace con organización|org:Organizacion|1|
| |eli:format|Enlace al formato|objeto|1|
| |eli:license|Enlace a la Licencia|objeto|1|
| |eli:embodies|Enlace inversa de eli:is_embodied_by|eli:LegalExpression|1|

#### 6.7.4. Casos de uso

Las vistas más destacadas relacionadas con la normativa son las siguientes:

|Id de vista|Descripción|Datos|Conjunto de datos |Nº de accesos|Última act.|
|:----|:----|:----|:----|:----|:----|
7|Ordenanzas Fiscales Municipio|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=7&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/ordenanzas-fiscales-municipales)|221|19/03/2020|
5|Ordenanzas Generales Municipio|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=5&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/ordenanzas-generales-municipales)|202|19/03/2020|
6|Ordenanzas Generales Comarca|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=6&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/ordenanzas-generales-comarcales)|98|19/03/2020|
8|Ordenanzas Fiscales Comarca|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=8&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/ordenanzas-fiscales-comarcales)|76|19/03/2020|
38|Ordenanzas fiscales de Consorcios|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=38&_pageSize=100&_page=1)| | | |
39|Ordenanzas fiscales de Diputación|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=39&_pageSize=100&_page=1)| | | |
40|Ordenanzas fiscales de Entidad Menor|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=40&_pageSize=100&_page=1)| | | |
41|Ordenanzas fiscales de Mancomunidades|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=41&_pageSize=100&_page=1)| | | |
42|Ordenanzas fiscales de Organismos Autónomos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=42&_pageSize=100&_page=1)| | | |
43|Ordenanzas fiscales de Villas y Tierras|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=43&_pageSize=100&_page=1)| | | |
44|Ordenanzas generales de Consorcios|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=44&_pageSize=100&_page=1)| | | |
45|Ordenanzas generales de Diputaciones|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=45&_pageSize=100&_page=1)| | | |
46|Ordenanzas generales de Entidades Menores|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=46&_pageSize=100&_page=1)| | | |
47|Ordenanzas generales de Mancomunidades|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=47&_pageSize=100&_page=1)| | | |
48|Ordenanzas generales de Núcleos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=48&_pageSize=100&_page=1)| | | |
49|Ordenanzas generales de Organismos Autónomos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=49&_pageSize=100&_page=1)| | | |
50|Ordenanzas generales de Villas y Tierras|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=50&_pageSize=100&_page=1)| | | |
245|Base jurídica tratamiento|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=245&_pageSize=100&_page=1)| | | |

El mapeo correspondiente a la vista 45 - Ordenanzas generales de Diputaciones se relaciona con la entidad Normativa y además con la entidad Organización de la siguiente forma (los atributos de origen que no aparecen en la siguiente tabla no se utilizan en el mapeo con el nuevo modelo):

|Atributo de origen|Entidad principal|Propiedad |Entidad relacionada|Propiedad|
|:----|:----|:----|:----|:----|
|DIPUTACION_ID|eli:Agent|org:organization|org:Organization|dc:identifier|
|DENOMINACION|eli:Agent|org:organization|org:Organization|dc:title|
|TIPO|eli:LegalResource|eli:type_document| | |
|TEXTO|eli:LegalResource|eli:description| | |
|ORDYREG_ID|eli:LegalResource|eli:id_local| | |
|CLOB_ID|eli:LegalResource|eli:number| | |
|F_ACUERDO_APRO_INI|eli:LegalResource|eli:date_applicability| | |
|F_ACUERDO_APRO_DEF|eli:LegalResource|eli:first_date_entry_in_force| | |
|F_PUBLICACION_APRO_DEF|eli:LegalResource|eli:date_publication| | |


### 6.8. Contrato

#### 6.8.1. Descripción de vocabulario y entidad seleccionada

Para modelar los contratos y sus procesos utilizamos el vocabulario:

- ***OCDS***. Modela contratos y el proceso de contratación. En este caso se opta por un vocabulario específico que incluye atributos más ajustados.

#### 6.8.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-Contract.jpg) 
  

#### 6.8.3. Definición avanzada de los atributos

Contrato

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|ocds:Contract|ocds:contractId|Identificador|Int|1|
| |ocds:description|Descripción|string|1|
| |dc:title|Título|string|1|
| |org:organization|Enlace con Organización|org:Organization|1|
| |ocds:hasContractPeriod|Enlace con Periodo|ocds:Period|0..* |
| |ocds:hasContractValue|Enlace con Valor|ocds:Value|0..* |
|ocds:Period|ocds:startDate|Fecha de inicio|Date|1|
| |ocds:endDate|Fecha de final|Date|0..1|
|ocds:Value|ocds:valueAmount|Total|Double|1|

#### 6.8.4. Casos de uso

Las vistas más destacadas relacionadas con los contratos son las siguientes:

|Id de vista|Descripción|Datos|Conjunto de datos |Nº de accesos|Última act.|
|:----|:----|:----|:----|:----|:----|
147|Transporte - Concesiones|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=147&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/transporte-regular-de-viajeros-por-carretera-en-aragon)|718|19/03/2020|
152|IAA - Contratos|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=152&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/depuradoras-de-agua-residual-gestionadas-o-financiadas-por-la-c-a-de-aragon)|253|19/03/2020|
153|IAA - Contratos gastos anuales|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=153&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/depuradoras-de-agua-residual-gestionadas-o-financiadas-por-la-c-a-de-aragon)|253|19/03/2020|
154|IAA - Contratos depuradoras incluidas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=154&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/depuradoras-de-agua-residual-gestionadas-o-financiadas-por-la-c-a-de-aragon)|253|19/03/2020|


El mapeo correspondiente a la vista 152 – IAA - Contratos con el nuevo modelo es el siguiente (los atributos de origen que no aparecen en la siguiente tabla no se utilizan en el mapeo con el nuevo modelo):

|Atributo de origen|Entidad principal|Propiedad |Entidad relacionada|Propiedad|
|:----|:----|:----|:----|:----|
|CONTRATO|ocds:Contract|ocds:contractId| | |
|TITULO|ocds:Contract|dc:title| | |
|FECHA_INICIO|ocds:Contract|ocds:hasContractPeriod|ocds:Period|ocds:startDate|
|FECHA_FIN|ocds:Contract|ocds:hasContractPeriod|ocds:Period|ocds:endDate|
|EMPRESA|ocds:Contract -> org:organization|dc:title| | |
|DIRECCION|ocds:Contract -> org:organization -> org:Site|vcard_siteAddress|vcard:Location|vcard:street-address|
|CODIGO_POSTAL|ocds:Contract -> org:organization -> org:Site|vcard_siteAddress|vcard:Location|vcard:postal-code|
|MUNICIPIO|ocds:Contract -> org:organization -> org:Site|vcard_siteAddress|vcard:Location|vcard:locality|
|PROVINCIA|ocds:Contract -> org:organization -> org:Site|vcard_siteAddress|vcard:Location|vcard:region|


### 6.9. Licitación

#### 6.9.1. Descripción de vocabulario y entidad seleccionada

Al igual que en Contratos, usamos el siguiente vocabulario:

- ***OCDS***. Modela licitaciones. En este caso se opta por un vocabulario específico que incluye atributos más ajustados.


#### 6.9.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-Tender.jpg) 
  
#### 6.9.3. Definición avanzada de los atributos

Licitación

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|ocds:Tender|ocds:id|Identificador|Int|1|
| |dc:title|Título|string|1|
| |ocds:description|Descripción|string|1|
| |org:organization|Enlace con Organización|org:Organization|1|
| |ocds:hasTenderPeriod|Enlace con Periodo|ocds:Period|0..* |
|ocds:Period|ocds:startDate|Fecha de inicio|Date|1|
| |ocds:endDate|Fecha de final|Date|0..1|


#### 6.9.4. Casos de uso

La vista relacionada con Licitación es la siguiente:

|Id de vista|Descripción|Datos|Conjunto de datos |Nº de accesos|Última act.|
|:----|:----|:----|:----|:----|:----|
|284|Contratación - Licitaciones publicadas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=284&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/anuncios-del-perfil-del-contratante-del-gobierno-de-aragon)|408|11/03/2021|


El mapeo correspondiente a esta vista con el nuevo modelo es el siguiente (los atributos de origen que no aparecen en la siguiente tabla no se utilizan en el mapeo con el nuevo modelo):

|Atributo de origen|Entidad principal|Propiedad |Entidad relacionada|Propiedad|
|:----|:----|:----|:----|:----|
|FECHAPUBLICACION|ocds:Tender|ocds:hasTenderPeriod|ocds:Period|ocds:startDate|
|ORGANISMCODEGG|ocds:Tender|org:organization|org:Organization|org:identifier|
|NOMBREGG|ocds:Tender|org:organization|org:Organization|dc:title|
|IDEXPEDIENTEPLACSP|ocds:Tender|ocds:id| | |
|ORGANISMCODEOC|ocds:Tender|org:organization|org:Organization|org:identifier|
|NOMBREOC|ocds:Tender|org:organization|org:Organization|dc:title|
|OBJETOCONTRATO|ocds:Tender|dc:title| | |


### 6.10. Trámite administrativo

#### 6.10.1. Descripción de vocabulario y entidad seleccionada

Para modelar los lugares utilizamos el vocabulario:

- ***Schema.org***. Hemos optado por modelar con schema:ItemList, que permite definir el trámite con sus relaciones y cuenta con un ListItem para modelar los pasos del trámite, tal y como está definido en la web de Aragón.

#### 6.10.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-ItemList.jpg) 
 
#### 6.10.3. Definición avanzada de los atributos

Trámite administrativo

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|schema:ItemList|schema:identifier|Identificador |string|0..1|
| |schema:title|Título|string|1|
| |schema:abstract|Descripción |string|1|
| |schema:itemListElement|Enlace con el  paso del tramite|schema:ListItem|1..* |
| |skos:concept|Enlace con categoría|skos:Concept|0..1|
| |org:organization|Enlace con organización|org:Organization|0..* |
| |eli:related_to|Enlace con normativa|eli:LegalResouce|0..* |
|schema:ListItem|schema:identifier|Identificador |string|0..1|
| |schema:title|Título del paso |string|1|
| |schema:abstract|Descripción del paso|string|1|
| |schema:nextItem|Enlace con siguiente paso del tramite|schema:ListItem|0..1|
| |schema:previousItem|Enlace con el paso previo del tramite|schema:ListItem|0..1|
| |schema:position|Posición|int|1|


#### 6.10.4. Casos de uso

Actualmente no disponemos de información de ninguna vista relacionada con trámites administrativos por lo que tendremos que incorporar un origen de estos datos para poder alinearlo con el nuevo modelo. 

### 6.11. Transporte

#### 6.11.1. Descripción de vocabulario y entidad seleccionada

Para modelar el transporte utilizamos el vocabulario:

- ***GTFS***. Se trata de un vocabulario inspirado en la iniciativa General Transit Feed Specification (GTFS). Se modelan datos de paradas, estaciones, etc. 
- ***WGS84***. Coordenadas de la entidad o de cada punto de una ruta expresada como un gtfs:Shape.
- ***vCard***. Opcionalmente, org:siteAddress hacia vCard:Location
- ***ORG***. Opcionalmente, enlace hacia una organización (municipio), org:organization hacia org:Organization.

#### 6.11.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-Transporte.jpg) 
 
#### 6.11.3. Definición avanzada de los atributos

Ruta

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|gtfs:Route|dc:identifier|Identificador de la ruta|String|0..1|
| |dc:title|Nombre de la ruta|String|0..1|
| |gtfs:originStop|Parada de origen|gtfs:Stop|1|
| |gtfs:destinationStop|Parada de destino|gtfs:Stop|1|
| |gtfs:routeType|Tipo de ruta|gtfs:Bus|1|
| |gtfs:agency|Enlace con la agencia|gtfs:Agency|0..1|

Parada

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|gtfs:Stop|dc:title|Nombre de la parada|string|1|
| |dc:identifier|Identificador de la parada|String|1|
| |wgs84_pos:long|Longitud|double|1|
| |wgs84_pos:lat|Latitud|double|1|
| |org:siteAddress|Lugar|vcard:Location|1|

Itinerario

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|gtfs:Trip|dc:identifier|Identificador del viaje|string|1|
| |dc:description|descripción|string|0..1|
| |gtfd:route|Enlace con la ruta|gtfs:Route|1|
| |dc:date|Fecha del viaje|date|0..1|

Horario de parada

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|gtfs:StopTime|dc:identifier|Identifica un viaje|string|0..1|
| |gtfs:stopSequence|Identifica el destino del viaje|int|1|
| |gtfs:arrivalTime|Hora de llegada|date|0..1|
| |gtfs:trip|Enlace con el viaje|gtfs:Trip|1|
| |gtfs:stop|Enlace con la parada|gtfs:Stop|1|

Agencia de transporte

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|gtfs:Agency|dc:identifier|Identificador de la Agencia|string|1|
| |dc:title|Nombre de la Agencia|string|1|
| |rdfs:subClassOf|label|org:Organization|1|
| |foaf:name|Nombre organizacion|string|1|
| |schema:startDate|Fecha de inicio|Date|1|
| |schema:endDate|Fecha de fin|Date |0..1|
| |org:organization|Enlace con organización|org:Organization|1|


#### 6.11.4. Casos de uso

Las vistas relacionadas con Transporte son las siguientes:

|Id de vista|Descripción|Datos|Conjunto de datos |Nº de accesos|Última act.|
|:----|:----|:----|:----|:----|:----|
148|TRANSPORTE - Expediciones|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=148&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/transporte-regular-de-viajeros-por-carretera-en-aragon)|718|19/03/2020|
149|TRANSPORTE - Expedición Parada Horario|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=149&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/transporte-regular-de-viajeros-por-carretera-en-aragon)|718|19/03/2020|
150|TRANSPORTE - Paradas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=150&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/transporte-regular-de-viajeros-por-carretera-en-aragon)|718|19/03/2020|
151|TRANSPORTE - Rutas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=151&_pageSize=100&_page=1)|[BANCO_DATOS](https://opendata.aragon.es/datos/catalogo/dataset/transporte-regular-de-viajeros-por-carretera-en-aragon)|718|19/03/2020|
140|CRA - Datos de itinerarios de las rutas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=140&_pageSize=100&_page=1)| | | |
141|CRA - Paradas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=141&_pageSize=100&_page=1)| | | |
144|CRA - Datos de las rutas|[GA_OD_CORE](https://opendata.aragon.es/GA_OD_Core/preview?view_id=144&_pageSize=100&_page=1)| | | |

El mapeo correspondiente a las vistas 148, 149, 150 y 150 de TRANSPORTE con el nuevo modelo donde se identifican las expediciones, rutas y paradas con sus horarios es el siguiente (los atributos de origen que no aparecen en la siguiente tabla no se utilizan en el mapeo con el nuevo modelo):

|Id|Atributo de origen|Entidad principal|Propiedad |Entidad relacionada|Propiedad|
|:----|:----|:----|:----|:----|:----|
|148|COD_EXP|gtfs:Trip|dc:identifier| | |
|148|FRECUENCIA|gtfs:Trip|dc:description| | |
| | | | | | |
|149|COD_EXPEDICION|gtfs:StopTime|gtfs:trip|gtfs:Trip|dc:identifier|
|149|ORDEN_PARADA|gtfs:StopTime|gtfs:stopSequence| | |
|149|COD_PARADA|gtfs:StopTime|gtfs:stop|gtfs:Stop|dc:identifier|
|149|HORARIO|gtfs:StopTime|gtfs:arrivalTime| | |
| | | | | | |
|150|COD_PARADA|gtfs:Stop|dc:identifier| | |
|150|DENO_DIRECCIÓN|gtfs:Stop|dc:title| | |
|150|NUCLEO|gtfs:Stop|org:siteAdress|vcard:Location|vcard:locality|
|150|X|gtfs:Stop|wgs84_pos:lat | | |
|150|Y|gtfs:Stop|wgs84_pos:long| | |
| | | | | | |
|151|COD_CONCESION|ocds:Contract|ocds:id| | |
|151|COD_RUTA|gtfs:Route|dc:identifier| | |
|151|DENO_RUTA|gtfs:Route|dc:title| | |
|151|ORIGEN|gtfs:Route|gtfs:originStop|gtfs:Stop|dc:title|
|151|DESTINO|gtfs:Route|gtfs:destinationStop|gtfs:Stop|dc:title|
| | | |



### 6.12. Tema

#### 6.12.1. Descripción de vocabulario y entidad seleccionada

Los temas del Gobierno de Aragón pasan a modelarse con SKOS, en lugar de como una jerarquía de clases, para facilitar el mantenimiento y la reutilización, así como la alineación con las categorías de la NTI. El vocabulario será, por tanto, ***SKOS***.

#### 6.12.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-Concept.jpg) 
  
#### 6.12.3. Definición avanzada de los atributos

Tema

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|skos:Concept|skos:prefLabel|Etiqueta|String|1|
| |dc:identifier|Identificador|String|1|
| |skos:broader|Enlace al concept padre|skos:Concept|0..* |
| |skos:broadMatch|Enlace con concept relacionado|skos:Concept|0..*|
| |dc:source|Origen|string|1|
|skos:Collection|dc:source|Fuente|string|1|
| |dc:source|Origen|string|1|
| |skos:scopeNote|Nota de alcance|string|1|
| |skos:member|Relación con los miembros|skos:Concept|1..* |


#### 6.12.4. Gestión y sincronización de temas

Los temas se sincronizaránn con los indicados en la vista 161 de GA_OD_CORE. Cada concepto SKOS estará relacionado con uno de los temas principales de la recomendación NTI, mediante `skos:broadMatch`. Por ejemplo:

    ei2a:kos/subvencion-medio-ambiente skos:broadMatch <http://datos.gob.es/kos/sector-publico/sector/medio-ambiente>

Cada categoría SKOS se relacionará con la clase del modelo actual que es sustituida por el nuevo tesauro. Para ello se añadirá un triple `rdfs:isDefinedBy` en cada clase del modelo actual, apuntando hacia una categoría SKOS. Por ejemplo:

    <http://opendata.aragon.es/def/ei2a/categorization#EnvironmentSubsidy> rdfs:isDefinedBy ei2a:kos/subvencion-medio-ambiente

### 6.13. DataCube

#### 6.13.1. Descripción de vocabulario y entidad seleccionada

Para modelar datasets de observaciones y medidas utilizamos el vocabulario:
- ***Datacube***. Este modelo permite añadir datasets muy específicos que se caracterizan por tener datos que podrían considerarse medidas. Este modelo ya se usa en el grafo de Aragopedia y se usará en el grafo del nuevo modelo para recoger los datos del presupuesto de Aragón.

#### 6.13.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-qb.jpg) 
 
#### 6.13.3. Casos de uso

Un ejemplo concreto, para entender la via por la que se pueden integrar los datos con la entidad DataCube, es el conjunto de datos que contiene la información estadística provincial del Coronavirus en la comunidad de Aragón (https://opendata.aragon.es/datos/catalogo/dataset/publicaciones-y-anuncios-relacionados-con-el-coronavirus-en-aragon)

Para realizar esta integración es necesario definir una estructura que permita entender cómo leer los datos y para ello basta con identificar qué atributos concretos representan lo que en el modelo de Datacube se denomina "Dimensión" y los que representan una "Medida":
- Medida: Es cada una de las observaciones realizadas y contiene el dato concreto medido.
- Dimensión: Es un concepto por el cual se pueden clasificar los datos indicados en las medidas, que permite clasificar la información y relacionarla con otras entidades.

Una muestra del fichero CSV con los datos indicados es la siguiente:
|fecha|provincia|casos_confirmados|ingresos_hospitalarios|ingresos_uci|fallecimientos|casos_personal_sanitario|altas|codigo_ine|observaciones|
|:----|:----|:----|:----|:----|:----|:----|:----|:----|:----|
|29/03/2020|Zaragoza|1449|720|121|79|211|101|50|Fuente Aragón Hoy|
|29/03/2020|Huesca|201|103|13|11|16|14|22|Fuente Aragón Hoy|
|29/03/2020|Teruel|208|112|19|12|40|10|44|Fuente Aragón Hoy|
|30/03/2020|Zaragoza|1641|843|123|81|214|141|50|Fuente Aragón Hoy|
|30/03/2020|Huesca|215|120|13|11|16|19|22|Fuente Aragón Hoy|
|30/03/2020|Teruel|222|131|20|12|41|14|44|Fuente Aragón Hoy|

En esta muestra se identifican las siguientes dimensiones:
- El campo "fecha" se identifica como una dimensión de tipo fecha.
- El campo "codigo_ine" es el identificador de la provincia y representa una dimensión que permite relacionar los datos con la entidad "Organización", que es la utilizada para representar a las provincias de la comunidad de Aragón.

Las medidas de esta muestra son las siguientes:
- "casos_confirmados": Número de casos confirmados
- "ingresos_hospitalarios": Número de ingresos hospitalarios
- "ingresos_uci": Número de ingresos en UCI
- "fallecimientos": Número de fallecidos
- "casos_personal_sanitario": Número de casos confirmados en el personal sanitario
- "altas": Número de altas

Siguiendo la identificación de elementos indicada anteriormente, la estructura definida para realizar esta carga de información es la siguiente:
    
    ei2a:recurso/dsd/casos-coronavirus-provincia a qb:DataStructureDefinition
    	qb:component [qb:dimension ei2a:recurso/dimension/fecha; qb:order 1];
    	qb:component [qb:dimension ei2a:recurso/dimension/provincia; qb:order 2];
    	qb:component [qb:measure ei2a:recurso/measure/casos_confirmados];
    	qb:component [qb:measure ei2a:recurso/measure/ingresos_hospitalarios];
    	qb:component [qb:measure ei2a:recurso/measure/ingresos_uci];
    	qb:component [qb:measure ei2a:recurso/measure/fallecimientos];
    	qb:component [qb:measure ei2a:recurso/measure/personal_sanitario];
    	qb:component [qb:measure ei2a:recurso/measure/altas];
    ei2a:recurso/dimension/fecha a qb:DimensionProperty
    	rdfs:Label “Fecha”;
    	rdfs:range xsd:datetime;
    ei2a:recurso/dimension/provincia a qb:DimensionProperty
    	rdfs:Label “Provincia”;
    	rdfs:range org:Organization;
    	qb:concept ei2a:kos/provincia;
    ei2a:recurso/measure/casos_confirmados a qb:MeasureProperty
    	rdfs:Label “Casos confirmados”;
    	rdfs:Range xsd:decimal;
    ei2a:recurso/measure/ingresos_hospitalarios a qb:MeasureProperty
    	rdfs:Label “Ingresos hospitalarios”;
    	rdfs:Range xsd:decimal;
    ei2a:recurso/measure/ingresos_uci a qb:MeasureProperty
    	rdfs:Label “Ingresos UCI”;
    	rdfs:Range xsd:decimal;
    ei2a:recurso/measure/fallecimientos a qb:MeasureProperty
    	rdfs:Label “Fallecimientos”;
    	rdfs:Range xsd:decimal;
    ei2a:recurso/measure/personal_sanitario a qb:MeasureProperty
    	rdfs:Label “Casos en personal sanitario”;
    	rdfs:Range xsd:decimal;
    ei2a:recurso/measure/altas a qb:MeasureProperty
    	rdfs:Label “Altas”;
    	rdfs:Range xsd:decimal;
	
A continuación se presenta como se cargarían las observaciones del dataset concreto, para una muestra de "Zaragoza" del día "29/03/2020":

	ei2a:recurso/dataset/casos-coronavirus-provincia a qb:Dataset
		dct:title "Provincias: Datos y cifras acumuladas sobre el Coronavirus";
		qb:structure ei2a:recurso/dsd/casos-coronavirus-provincia;
	ei2a:recurso/observacion/casos-coronavirus-provincia/50_29/03/2020 a qb:Observation
		qb:Dataset ei2a:recurso/dataset/casos-coronavirus-provincia;
		ei2a:recurso/dimension/fecha "29/03/2020T10:00:00"^^xsd:dateTime;
		ei2a:recurso/dimension/provincia ei2a:recurso/sector-publico/organizacion/provincia/50;
		ei2a:recurso/medida/casos_confirmados 1449.0;
		ei2a:recurso/medida/ingresos_hospitalarios 720.0;
		ei2a:recurso/medida/ingresos_uci 121.0;
		ei2a:recurso/medida/fallecimientos 79.0;
		ei2a:recurso/medida/personal_sanitario 211.0;
		ei2a:recurso/medida/altas 101.0;

### 6.14. Dispositivo. Internet de las Cosas. IoT

#### 6.14.1. Descripción de vocabulario y entidad seleccionada

Para modelar los sistemas y dispositivos (como los de gestión de agua) utilizamos el vocabulario SSN (Semantic Sensor Network):

- ***SSN***. (Semantic Sensor Network Ontology). Modela sistemas y dispositivos en el ámbito de IoT. Como ya se ha indicado en el apartado de vocabularios, se reducen las clases respecto al uso anterior de WISDOM, lo que simplifica el modelo.
- ***vCard***. Opcionalmente, org:siteAddress hacia vCard:Location
- ***ORG***. Opcionalmente, enlace hacia una organización (municipio), org:organization hacia org:Organization.

Este modelo podría usarse para modelar dispositivos y sus mediciones en el ámbito de IoT (Internet Of Things).

#### 6.14.2. Diagrama de la entidad

![](docs/images/ei2a-diagrama-Featureofinterest.jpg) 
 
#### 6.14.3. Definición avanzada de los atributos

Dispositivo

|Entidad|Atributo|Descriptor|Tipo|Multiplicidad|
|:----|:----|:----|:----|:----|
|sosa:Featureofinterest|dc:identifier|Identificador|String|1|
| |dc:title|Nombre|String|1|
| |dc:date|Fecha |Date|1|
| |org:siteAddress|Enlace con lugar|Vcard:Location|1|
| |sosa:ObservableProperty|Enlace con el valor observable |Sosa:Observation|1|
|sosa:Observation|rdfs:comment|Definición|string|1|
| |sosa:hasFeatureOfInterest|Inversa de sosa:ObservableProperty|sosa:Featureofinterest|1|
| |sosa:hasResult|valor|string|1|
| |sosa:phenomenonTime|valor|dateTimeStamp|0..1|


#### 6.14.4. Casos de uso

Por ejemplo, los datos de un Ramal (vista 106) se representarían:

    ei2a:recurso/medio-ambiente/ramal/49340 a sosa:FeatureOfInterest
    	dc:identifier 869908;
    	dc:date “"06/08/2013 11:58:16";
    	org:siteAddress ei2a:recurso/sector-publico/lugar/poblacion/50130>;
    	sosa:ObservableProperty ei2a:recurso/medio-ambiente/observacion/ramal/49340-1;
	sosa:ObservableProperty ei2a:recurso/medio-ambiente/observacion/ramal/49340-2;
    ei2a:recurso/medio-ambiente/observacion/ramal/49340-1 a sosa:Observation
    	rdfs:comment “Longitud”;
    	sosa:HasResult 56.19;
    	sosa:phenomenonTime "2021-04-09T12:00:00Z"^^xsd:dateTimeStamp;
    ei2a:recurso/medio-ambiente/observacion/ramal/49340-2 a sosa:Observation
    	rdfs:comment “Caudal en m3/s”;
    	sosa:HasResult 0.5;
    	sosa:phenomenonTime "2021-04-09T12:00:00Z"^^xsd:dateTimeStamp;

#### 6.15. Información de Datasets y Procedencia

#### 6.15.1. Descripción de vocabularios y entidades seleccionadas

 - ***DCAT***. (Data Catalog Vocabulary). Se trata de una recomendación del W3C para facilitar la interoperabilidad de entre catálogos de datos publicados en la web y permite la descripción de datasets y servicios de datos. En el ámbito del proyecto se usará, además, para mostrar información explicativa del dato y su procedencia, enlazando con los metadatos declarados mediante PROV-O.
 - ***PROV-O***. (The PROV Ontology).  El proceso de carga en el grafo correspondiente a este nuevo modelo ontológico va a generar información de procedencia para cada entidad, modelando mediante esta recomendación del W3C. Cada entidad cargada o actualizada incorporará un triple informando del proceso de carga del que proviene y enlazará con el Dataset de procedencia.

#### 6.15.2. Casos de uso

Cada entidad cargada o actualizada incorpora un triple informando del proceso de carga del que proviene (entidad actividad); y se genera una entidad de tipo prov:Activity con información de dicho proceso. 
Además, la actividad se enlaza con el dataset mediante el atributo prov:wasAssociatedWith, lo que permite utilizar la información descriptiva del dataset, proveniente de CKAN, para explicar la información de la entidad cargada. Para conseguir esto se ha preparado un proceso que exporta y carga en en el grafo de EI2Av2 los triples de los metadatos de los datasets del [Banco de Datos](https://opendata.aragon.es/datos/catalogo). El vocabulario que modela la carga de estos triples es DCAT.

Por ejemplo, estos triples asociarían una organización (comarca) con el dataset de comarcas (en GA-OD-CORE y en CKAN) y con el proceso de carga del que provienen sus datos:

    http://opendata.aragon.es/recurso/sector-publico/organizacion/comarca/10 a org:Organization.
    http://opendata.aragon.es/recurso/sector-publico/organizacion/comarca/10 prov:wasUsedBy http://opendata.aragon.es/recurso/procedencia/BE669411-8147-1BF0-18D9-E81CAF9D86C8.
    http://opendata.aragon.es/recurso/procedencia/BE669411-8147-1BF0-18D9-E81CAF9D86C8
        a prov:Activity;
        prov:startedAtTime "2021-04-25T01:30:00Z"^^xsd:dateTime;
        prov:wasAssociatedWith http://opendata.aragon.es/recurso/carga/aodpoolv2;        
        prov:wasAssociatedWith http://opendata.aragon.es/datos/catalogo/dataset/ga-od-core/10;
    http://opendata.aragon.es/recurso/carga/aodpoolv2
        a prov:SoftwareAgent;
        foaf:name "Proceso de carga de Aragón Open Data Pool";
    http://opendata.aragon.es/datos/catalogo/dataset/ga-od-core/10
        a dcat:Dataset;
        dc:title "10 region";
        dcat:distribution http://opendata.aragon.es/dataset/e7c5d011-9a12-423b-a2c5-d0443a298e53/resource/1a489f66-89ba-40ab-8d8c-9a42dd7fd306;
    http://opendata.aragon.es/dataset/e7c5d011-9a12-423b-a2c5-d0443a298e53/resource/1a489f66-89ba-40ab-8d8c-9a42dd7fd306
        a dcat:Distribution;
        dc:title "Información general de las comarcas de Aragón";
	...
    http://opendata.aragon.es/datos/catalogo/dataset/e7c5d011-9a12-423b-a2c5-d0443a298e53
        a dcat:Dataset;
        dcat:distribution http://opendata.aragon.es/dataset/e7c5d011-9a12-423b-a2c5-d0443a298e53/resource/1a489f66-89ba-40ab-8d8c-9a42dd7fd306;
        dct:identifier "http://opendata.aragon.es/datos/catalogo/dataset/informacion-general-de-las-comarcas-de-aragon";
	...

En el caso de datos cargados directamente desde el [Banco de Datos](https://opendata.aragon.es/datos/catalogo), los datos de procedencia serían un poco diferentes, ya que no contarían con el dataset de GA-OD-CORE. Por ejemplo:

    http://opendata.aragon.es/recurso/sector-publico/organizacion/comarca/10 a qb:Observation.
    http://opendata.aragon.es/recurso/sector-publico/organizacion/comarca/10 prov:wasUsedBy http://opendata.aragon.es/recurso/procedencia/E8B10C55-06BA-8F51-2379-2DB6EF32014F.
    http://opendata.aragon.es/recurso/procedencia/E8B10C55-06BA-8F51-2379-2DB6EF32014FC8
        a prov:Activity;
        prov:startedAtTime "2021-04-25T01:30:00Z"^^xsd:dateTime;
        prov:wasAssociatedWith http://opendata.aragon.es/recurso/carga/aodpoolv2;        
        prov:wasAssociatedWith http://opendata.aragon.es/dataset/3a34f30b-2568-4f85-bbcc-04d6c5932556/resource/52d26a9f-523c-4b5b-8194-107655ffaf3e;
    http://opendata.aragon.es/recurso/carga/aodpoolv2
        a prov:SoftwareAgent;
        foaf:name "Proceso de carga de Aragón Open Data Pool";
    http://opendata.aragon.es/dataset/3a34f30b-2568-4f85-bbcc-04d6c5932556/resource/52d26a9f-523c-4b5b-8194-107655ffaf3e
        a dcat:Distribution;
        dc:title "Datos acumulados de Centros y aulas afectadas por coronavirus en Aragón";
        ...
    http://opendata.aragon.es/datos/catalogo/dataset/3a34f30b-2568-4f85-bbcc-04d6c5932556
        a dcat:Dataset;
        dcat:distribution http://opendata.aragon.es/dataset/3a34f30b-2568-4f85-bbcc-04d6c5932556/resource/52d26a9f-523c-4b5b-8194-107655ffaf3e;
        dct:identifier "https://opendata.aragon.es/datos/catalogo/dataset/publicaciones-y-anuncios-relacionados-con-el-coronavirus-en-aragon";
        ...


## Anexo A. Organigrama del Gobierno de Aragón

Para la incorporación de la información de las unidades organizativas y cargos que forman parte del Gobierno de Aragón, teniendo en cuenta las diferentes legislaturas con el fin de identificar la relación de sucesión entre ellas, se han utilizado principalmente las entidades de Persona, Puesto, Organización y Legislatura.

![](docs/images/ei2a-diagrama-organigrama.png)
 
Los datos disponibles que se encuentran ubicados en la siguiente vista https://opendata.aragon.es/datos/catalogo/dataset/organigrama-del-gobierno-de-aragon representan la información de las personas que han ejercido todos los cargos correspondientes a las entidades que han formado parte de todas las legislaturas del Gobierno de Aragón.
En el archivo de datos “periodo de legislatura.csv” encontramos los periodos de cada legislatura que representamos con la entidad Legislatura que hereda de Evento.
En el archivo de datos “entidades.csv” se encuentran todas las unidades organizativas del Gobierno de Aragón relacionadas con las diferentes legislaturas y su dependencia ante otras unidades. Se encuentran representadas por la entidad “Organización”, su ubicación en un “Lugar” mediante la definición de un “Centro” y su relación temporal con una “Legislatura”.
En el archivo de datos “cargos.csv”, encontramos cada “Puesto” perteneciente a una unidad organizativa “Organización” y la “Persona” que lo ejerce.

