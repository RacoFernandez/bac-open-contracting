# Ejemplos - Casos de Uso

## El recorrido de un proceso dentro del estándar Open Contracting

Los procesos de compras dentro del estándar Open Contracting se identifican con un identificador único internacional. Se encuentran en el campo *“ocid”* y para el caso de Buenos Aires llevan el prefijo *“ocds-bulbcf”*. El campo *“ocid”* identifica a todos los procesos de compras a lo largo de las distintas etapas del mismo.

En el recurso llamado **[“Convocatoria”](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/f8eb531f-120c-4e91-bd5d-d43bb28cc696)** se puede encontrar la información correspondiente a la convocatoria de proveedores de los bienes y servicios que las distintas reparticiones del Gobierno de la Ciudad pretenden contratar. En esta etapa se define el procedimiento de selección de proveedores y la modalidad de contratación que llevará el documento contractual al momento de su firma. 
El archivo, a su vez, contiene los datos del resultado de la convocatoria y el detalle de cada uno de los ítems que se desean adquirir a través del proceso de compras en cuestión, incluyendo las cantidades a contratar y el precio unitario del bien o servicio en el caso que corresponda (en convenios marco no se especifica ex-ante el precio unitario del bien).
La información se encuentra desagregada a nivel de ítem. Por esta razón, cada una de las filas del recurso contiene la descripción y cantidades del ítem que se espera contratar y se encuentran asociadas a su correspondiente proceso a través del campo *“ocid”* o **“tender/id”*.

En el recurso llamado **[“Adjudicación”](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/b7e4bae8-0e0f-4e10-8b89-3860cf5b7f1b)** se especifica la información correspondiente a los procesos que han sido adjudicados, incorporando el detalle de los ítems asociados a cada adjudicación.
Los datos se encuentran desagregados a nivel de tipo de ítem, los cuales se encuentran vinculados a su correspondiente proceso de compras a través del campo *“ocid”*. 

El recurso llamado **[“Contratación”](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/a85472d6-b949-4617-a3a0-50e25f1274b3)** contiene el detalle de los contratos firmados entre las distintas entidades del Gobierno de la Ciudad y los proveedores participantes del contrato. Tal como ocurre en **“Convocatoria”** y **“Adjudicación”**, los datos están desagregados a nivel de ítem.
Del recurso se puede extraer información relativa a la cantidad efectiva de items contratados, el precio unitario y el monto total del contrato (que puede ser distinto al monto esperado por el cual se convoca). 

El inicio de un proceso de compras puede concluir sin un contrato firmado (en el caso de que la convocatoria fracasa o queda desierta de proveedores) o con al menos un contrato firmado. Los procesos pueden resultar adjudicados a más de un proveedor, siendo estos encargados de proveer un tipo de bien de los diversos que la entidad del Gobierno pretende adquirir. Con cada uno de ellos se firma un contrato específico siguiendo la modalidad de contratación que se fija en la convocatoria.
Dada esta relación entre los procesos de compras y la cantidad de contratos que pueden resultar del mismo, es necesario tomar en cuenta al campo *“contracts/0/id”* para identificar los ítems que se contratan con un proveedor específico y al campo *“ocid”* para encontrar todos los contratos que derivan de un proceso de compras en particular.


## Preguntas a responder con los datos

### ¿Cuál fué el porcentaje de convocatorias de las iniciadas y finalizadas en 2018 que resultaron adjudicadas?

1- Descargar el recurso **[“Convocatoria”](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/f8eb531f-120c-4e91-bd5d-d43bb28cc696)**, es el que contiene la información necesaria para el análisis. 

2- Filtrar los procesos de compras según su fecha de inicio y fin: Seleccionar aquellos que tienen fecha de inicio (*“tender/tenderPeriod/startDate”*) mayor al 31 de diciembre de 2017 y fecha de fin (*“tender/tenderPeriod/endDate”*) menor al 1 de enero de 2019.

3- Los datos del recurso **[“Convocatoria”](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/f8eb531f-120c-4e91-bd5d-d43bb28cc696)** se encuentran desagregados al nivel de *“Ítem”*. Cada fila contiene el detalle de cada uno de los ítems que un proceso de compras (identificado en *“ocid”*) pretende adquirir. Asimismo, cada una de las filas contiene información relativa al detalle del proceso de compras (si se trata de un mismo proceso de compras, la información va a ser exactamente igual en todas las filas), entre lo que se encuentra el estado actual del mismo, representado en el campo *“tender/status”*. Es necesario eliminar los valores duplicados utilizando la columna *“ocid”*.

4- Contar los valores del campo *“tender/status”*: Contiene el estado actual del proceso de compras. 
Sus valores posibles son: *active* (la convocatoria está en proceso), *cancelled* (el \
proceso ha sido cancelado), *unsuccessful* (la convocatoria no ha sido exitosa), *complete* (la convocatoria se ha completado).


### ¿Cómo calcular estadísticas descriptivas de los montos totales de los contratos iniciados y finalizados en 2018?

1- Descargar el recurso **[“Contratación”](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/a85472d6-b949-4617-a3a0-50e25f1274b3)**, es el que contiene la información necesaria para el análisis. 

2- Filtrar los contratos según su fecha de inicio y fin: Seleccionar aquellos que tienen fecha de inicio (*“contracts/0/period/startDate”*) mayor al 31 de diciembre de 2017 y fecha de fin (*“contracts/0/period//endDate”*) menor al 1 de enero de 2019.

3- El campo *“contracts/0/value/amount”* es el que contiene los montos totales de los contratos perfeccionados. Es el dato relevante para responder a la pregunta. Pero, dado que los datos publicados se encuentran desagregados a nivel de ítem, el monto de la columna *“contracts/0/value/amount”* se encuentra repetido una cantidad de veces igual a la cantidad de ítems distintos que se adquieren mediante el contrato en cuestión. En consecuencia, es central para el análisis eliminar esos valores duplicados.

4- Cada uno de los contratos está identificado con un identificador en el campo *“contracts/0/id”*. Utilizando los valores de este campo se eliminan las filas que duplican la información que necesitamos para el análisis.

5- Finalmente, se debe alcanzar una tabla que contenga un único ID de contrato por fila y que tenga asociado los campos *“contracts/0/value/amount”* y *“contracts/0/value/currency”* para conocer el monto total por el cual se perfeccionó el contrato y la moneda del mismo (pueden ser pesos argentinos, dólares estadounidenses o euros).

6- Con los valores de esta tabla se pueden calcular estadísticas descriptivas sin estar incurriendo en errores por duplicaciones.


### ¿Cuáles son las empresas a las cuales se adjudicaron los mayores contratos durante el 2018?

1- Descargar los recursos **[“Contratación”](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/a85472d6-b949-4617-a3a0-50e25f1274b3)** y **[“Participantes”](https://data.buenosaires.gob.ar/dataset/buenos-aires-compras/archivo/bece0240-eb9b-40c4-8928-cd77c4f62704)**, son los que contienen la información necesaria para el análisis. **“Participantes”** especifica quienes son las partes que firman cada uno de los contratos.

2- Filtrar los contratos según su fecha de inicio y fin: Seleccionar aquellos que tienen fecha de inicio (*“contracts/0/period/startDate”*) mayor al 31 de diciembre de 2017 y fecha de fin (*“contracts/0/period//endDate”*) menor al 1 de enero de 2019.

3- El campo *“contracts/0/value/amount”* es el que contiene los montos totales de los contratos perfeccionados. Es el dato relevante para responder a la pregunta. Pero, dado que los datos publicados se encuentran desagregados a nivel de ítem, el monto de la columna *“contracts/0/value/amount”* se encuentra repetido una cantidad de veces igual a la cantidad de ítems distintos que se adquieren mediante el contrato en cuestión. En consecuencia, es central para el análisis eliminar esos valores duplicados.

4- Cada uno de los contratos está identificado con un identificador en el campo *“contracts/0/id”*. Utilizando los valores de este campo se eliminan las filas que duplican la información que necesitamos para el análisis.

5- Con la tabla resultante, se ordenan los valores según *“contracts/0/value/amount”* para conseguir aquellos de mayor valor.

6- Utilizando el Identificador de los contratos con montos mas grandes, se filtran las filas de la tabla **“Participantes”** para encontrar la entidad compradora y la empresa proveedora del contrato en cuestión.
