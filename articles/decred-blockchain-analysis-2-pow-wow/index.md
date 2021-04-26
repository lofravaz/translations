# Análisis de la Blockchain de Decred Pt. 2 POW wow

![portada](./assets/cover.png)

> Artículo original escrito por Richard Red (inglés) : [Decred Blockchain Analysis - Part 2 PoW wow](https://blockcommons.org/post/dcr-on-chain-2/)

## Sumergiéndonos en la blockchain de Decred

Desde [el primer informe](https://blockcommons.org/post/dcr-on-chain-1/) sobre los datos de la blockchain de Decred, hemos viajado más profundo en busca por comprender lo que podemos aprender de la red de Decred. Este trabajo se ha progresado en tres direcciones, de la siguiente manera:

- Agrupar las direcciones de DCR para ver cuáles gastan fondos y/o compran tickets, por lo que probablemente pertenezcan a la misma billetera.
- Observar a los exchanges e identificar las transacciones relacionadas con ellos: estas son plataformas clave dentro del ecosistema, por lo que es importante poder identificarlas en los datos.
- Mirar el proceso del mezclador y los DCR que participan en él.

Mi plan para el segundo informe era terminar de agrupar y proporcionar un historial detallado de la blockchain de Decred, pero agrupar a todos los mineros / stakeholders / contratistas / exchanges de Decred al mismo tiempo es una labor demasiado ardua. He pasado por muchas iteraciones en este proceso, y en las últimas ha sido difícil identificar los errores, pero aún así encuentro algunos datos curiosos que no tienen mucho sentido, por lo que no son 100% confiables. Aún.

Si bien todavía planeo escribir este tipo de historiales detallados, hay un largo camino por recorrer, y será bastante largo cuando esté terminado. Sin embargo, he llegado a un punto en el que la exploración es bastante interesante, por lo que escribiré reportes breves que darán una idea de los diferentes aspectos de la actividad en blockchain a medida que voy avanzando.

El primer informe analiza a los principales mineros entre 2019-2020 (firmemente la era ASIC), para mostrar algunas de las herramientas que he desarrollado y ver qué tipo de imagen podemos exportar con los análisis disponibles. Detuve la recopilación de datos para este informe el 9 de enero del 2021.

## Conociendo a los mineros

Para empezar, tomé todas las recompensas de PoW para este período y rastreé su flujo durante 2 estapas, la estapa 2 debería cubrir la etapa 0 (recompensa de bloque) a la etapa 1 (para grupos, a menudo un pago de grupo o movimiento interno predecesor).

Hubo 192 direcciones que recibieron las recompensas de PoW directamente del coinbase, y estas a su vez enviaron DCR recién acuñado a 242 226 direcciones. En el proceso típico sería que la transacción del coinbase acuñe DCR a una dirección que el grupo siempre usa (las 192 mencionadas), luego el grupo realiza las transacciones hacia los participantes del grupo de minería, pero existe una variación considerable en cómo los grupos gestionan este proceso.

![histograma-direcciones](./assets/pow-hop0-addresses-histogram.png)
Histograma que muestra la distribución de recompensas de PoW hacia las direcciones

Ejecuté mi código de agrupación en este conjunto de direcciones que recibieron recompensas de PoW en la etapa 0 o 1, el proceso fue: tomar una dirección, buscar todas sus entradas comunes en las transacciones, compras de tickets y cualquier dirección adicional, repetir durante algunos ciclos hasta que deje de buscar nuevas direcciones y almacenar todo en la base de datos.

He seleccionado algunos grupos para ver con más detalle la cantidad de recompensas de PoW obtenidas desde 2019, los 5 primeros se seleccionaron en base a los destinatarios directos del coinbase (¡no creerás el tercero!), que deberían cubrir a los grupos de minería, y seleccione también a el top 5 en base de los DCR recibido de las transacciones del coinbase (debería cubrir a los mineros que usan los grupos de minería).

Al principio, busqué separar a los grupos de minería y los mineros, pero la presencia de mineros en solitario y algunas variaciones en la forma en que los grupos de minería administran los pagos hizo que fuera complicado diferenciarlos con solo mirar las métricas básicas. Entonces, el plan es hablar en que consta el proceso para averiguar cuál es el tipo de minero, ya que eso también debería ser más instructivo para los lectores.

> **Importante**: Los clústeres se seleccionan en función de las recompensas de minería a partir del 2019, pero una vez que se identificaron a los clústeres, utilicé los datos históricos completos para compilar su información resumida.

## Vista de la red

Mirar tablas de direcciones y hashes de las transacciones y tratar de seguir un flujo entre estos es difícil para la mente, por lo que en algunas ocasiones he buscado métodos para visualizar estas redes. Los métodos convencionales para extraer los nodos y los límites de una red no se adaptan bien al tamaño de estos grupos. La mayoría de las veces, cuando pruebo uno de estos, golpeo a mi máquina durante horas antes de fallar o me rindo y lo dejo. Cuando los gráficos se dibujan, generalmente son incomprensibles.

Mientras experimentaba con muestras más pequeñas para aprender a controlar los diseños y demás, me di cuenta de que funcionan bastante bien para dar una idea de cómo el minero o el grupo de minería organiza sus direcciones y transacciones. Para estos clústeres de minería, tomar solo las primeras 2 000 - 20 000 filas de la tabla de direcciones (entradas / salidas) parece lograr un buen equilibrio entre tener una muestra representativa que ilustre cómo fluye los DCR y poder dibujarlo. La mayor limitación sería si el grupo de minería cambiara su estructura más adelante, lo que no estaría representado en estos gráficos. Se puede hacer clic en todos los gráficos para expandirlos.

La gran decisión al representar el flujo de los DCR como una red es usar una de uno o dos modos. He optado por de dos modos aquí, siendo las Direcciones y Transacciones los dos tipos diferentes de nodo. DCR fluye de una dirección a una transacción y de una transacción a nuevas direcciones. También he experimentado con redes monomodo (donde solo existen nodos de direcciones y las transacciones se representan con límites entre ellos), pero la masa de conexiones que esto genera es difícil de visualizar.

El tipo de red en las visualizaciones es una [red de ego](https://research.library.gsu.edu/c.php?g=916490&p=6612505) muy básica centrada en las direcciones del clúster, es una red de ego ligeramente poco convencional porque utilicé mi técnica de agrupamiento para definir el límite de la red, luego solo extendí el límite de los nodos dentro de este "ego".

Las visualizaciones de la red utilizan las primeras 2000 - 20 000 entradas / salidas de las direcciones del clúster y dan un salto en cada dirección para ver si las entradas provienen de las direcciones del clúster o las salidas van a las direcciones del clúster. En estos casos (la mayoría de los límites), el DCR se mueve entre direcciones controladas por la misma billetera. Cuando las entradas no provienen de una dirección controlada por un clúster, los he marcado como nodos "**inward** (internos)"; las transacciones del coinbase son un tipo especial de nodo interno y les he dado su propio color. Cuando las salidas de las transacciones del clúster no van a direcciones controladas por clúster, las he marcado como nodos "**onward** (externas)". Las direcciones posteriores que coinciden con las direcciones de los exchanges conocidas se han resaltado con su propio color también.

La visualización de las redes es una adición reciente a mi conjunto de herramientas de exploración, pero ahora que tengo métodos para producir este tipo de red de ego, hay muchos otros grupos de minería para mirar. Cada grupo de minería tiene un gráfico de red con los mismos parámetros de color. Varié en la cantidad de filas de datos que se utilizarán para sembrar la red ego y elegí diferentes niveles para cada clúster, el número máximo legible (y el punto en el que se vuelven muy lentos para dibujar) depende de cuánto se extienden las transacciones del clúster. También estoy experimentando con diseños, y estos pueden tener un gran efecto en el aspecto de las redes, el diseño se da en el título (junto con el número de filas).

## Top 5 del Coinbase (grupos de minería)

### 1 - DsiD

Este clúster se vio por primera vez en enero de 2019 y todavía estaba activo en enero de 2021, recibió 987 000 de recompensas en PoW por la extracción de 53 766 bloques. El grupo controla 1 109 direcciones, está la dirección principal que recibe las recompensas PoW y las otras son direcciones de cambio para las transacciones de pago, el cambio se repite hasta que se usa como pago adicional.

![balance-DsiD](./assets/balance-DsiD.png)
Balance en DCR del clúster DsiD

El balance de las direcciones de este clúster nunca fué demasiado grande. Otro indicador útil de lo que está haciendo el clúster es observar la regularidad de su comportamiento. Los comportamientos muy regulares que se repiten durante meses o años son un signo de automatización.

![flujo-entrada-salida-DsiD](./assets/flows-DsiD.png)
Flujo de entradas y salidas de DCR para el cluster DsiD

La cantidad de DCR que se extrae y se mueve fuera del clúster cada día es similar, lo que sugiere que se trata de un grupo de minería, el más grande que opera actualmente en la red de DCR.

![distribucion-salidas-drc](./assets/outputs-distribution-DsiD.png)
Distribución de las salidas (gasto) de DCR hacia direcciones externas

También podemos ver hacia dónde fluye ese DCR, y en este caso hay dos direcciones que han recibido alrededor de 200 000 DCR del grupo de minería, con otras dos que han recibido 40 000-50 000 DCR. El destinatario más grande (DsgK) aparece a continuación en el número 3 en la lista de los 5 principales mineros de los grupos de minería.

![cluster-DsiD](./assets/cluster-DsiD-layout-stress-rows-20000.png)
Visualización de red para el clúster DsiD

### 2 - Dsnx

Este clúster se inició en julio de 2019 y todavía está activo, ha recibido 695 000 DCR en recompensas mineras por la extracción de 38 923 bloques. Este grupo de minería controla 19 direcciones, un número mucho menor que el pool considerado anteriormente, probablemente porque este mismo tiene un propósito diferente.

![balance-de-Dsnx](./assets/balance-Dsnx.png)
Balance en DCR del clúster Dsnx

![balance-cluster-Dsnx-en-dcr](./assets/flows-Dsnx.png.png)
Flujo de entradas y salidas de DCR para el cluster Dsnx

![distribucion-del-gasto-dsnx](./assets/outputs-distribution-Dsnx.png)
Distribución de las salidas (gasto) de DCR hacia direcciones externas

El DCR se mueve de manera constante a través de lo que parece una infraestructura de grupo de minería, con pagos a 32 direcciones, pero casi todo (~ 97%) va directamente a una dirección (DsUb). Las otras direcciones parecen direcciones de exchange, por lo que el propósito de este clúster es simplemente pasar el DCR extraído a DsUb (que se considera a continuación).

![red-cluster-dsnx](./assets/cluster-Dsnx-using-layout-stress-rows-5000.png)
Visualización de red para el clúster Dsnx

## 3 - DsSW

El grupo de minería alrededor de esta dirección, que comenzó a minar a mediados de 2018, es bastante diferente, porque este minero participa en la votación de DCR. Más específicamente, este minero extrajo 45 960 bloques y compró 622 tickets, a partir de junio de 2019 y continúa presente.

![balance-dcr-votacion-cluster-dssw](./assets/DsSW-plot.png)
Balance en DCR y votación del clúster DsSW

He creado un conjunto de scripts que recopilan datos de votación para cualquier ticket asociado con un grupo de minería. En este caso, el segundo panel no es interesante porque el stakeholder no votó sobre las propuestas de Politeia, y el tercero muestra que no configuraron su billetera para votar en ninguna de las propuestas de la agenda de DCP para implementar reglas de consenso que cambian las actualizaciones de la red.

![dcr-entradas-salidas-dcr-dssw](./assets/flows-DsSW.png)
Flujo de entradas y salidas de DCR para el cluster DsSW

Poniendo esto junto al balance, parece que el clúster se ha convertido en un minero menos importante en 2020, pero siguen participando con algo en el staking.

![red-dssw](./assets/cluster-DsSW-layout-kk-rows-20000.png)
Visualización de red para el clúster DsSW

El período cubierto por este gráfico es antes de que el clúster comenzara a participar en el staking, pero puedes consultar el final del informe para ver un gráfico que muestra un clúster de staking y votaciones.

Este clúster tiene muchas salidas hacia direcciones de exchanges conocidas y, a diferencia de los clústeres anteriores, suman cantidades significativas de DCR (45 000 a Binance, 34 000 a Bittrex, 19 000 a Poloniex).

## 4 - Dsju

Este clúster recibió 202 000 DCR en recompensas de minería de la etapa 0. Empezó a estar activo partir de marzo de 2019 y continua en la actualidad.

![balance-cluster-dsju](./assets/balance-Dsju.png)
Balance en DCR del clúster Dsju

![dcr-flujo-entrada-salida-cluster-dsju](./assets/flows-Dsju.png)
Flujo de entradas y salidas de DCR para el cluster Dsju

![distribucion-salidas-cluster-dsju](./assets/outputs-distribution-Dsju.png)
Distribución de las salidas (gasto) de DCR hacia direcciones externas

Esto parece ser un minero en solitario que usa la infraestructura del un grupo de minería, solo hay una dirección que ha recibido DCR de este clúster (DsVy): el minero realiza retiros periódicos cuando el saldo alcanza unos pocos miles.

![red-cluster-dsju](./assets/cluster-Dsju-using-layout-kk-rows-2000.png)
Visualización de red para el clúster Dsju

## 5 - DscM

Este clúster recibió 160 000 DCR, a partir de septiembre de 2019 y aún se encuentra activo. Aunque el clúster compró 22 tickets, también parece funcionar como un grupo de minería, con salidas bastante consistentes a un rango de direcciones.

![balance-en-dcr-del-cluster-dscm](./assets/DscM-plot.png)
Balance en DCR y votación del clúster DscM

![flujo-de-dcr-entradas-salidas](./assets/flows-DscM.png)
Flujo de entradas y salidas de DCR para el clúster de DscM

Grandes picos en el flujo de entrada indican que alguien envió DCR al clúster más allá del que estaba extrayendo.

![distribucion-salidas-del-cluster-dscm](./assets/outputs-distribution-DscM.png)
Distribución de las salidas (gasto) de DCR hacia direcciones externas

![red-cluster-dscm](./assets/cluster-DscM-using-layout-fr-rows-2000.png)
Visualización de red para el clúster DscM

Este grupo de minería tiene visitas en los 3 exchanges, pero tiene una preferencia por Binance, con 11 000 DCR yendo allí, y menos de 2 000 para los otros dos.

## Top 5 Mineros (de los grupos de minería)

### 1 - DsUb

Este clúster comenzó a mediados de 2018, todavía está activo y hasta ahora ha recibido 526 000 DCR uno desde la transacción de coinbase (la fuente es el clúster anterior: **2 - Dsnx**).

![balance-dsub](./assets/balance-DsUb.png)
Balance en DCR del clúster DsUb

La línea de este gráfico es más entrecortada porque el grupo de minería regularmente pone a cero su saldo.

![flujo-entradas-salidas-dsub](./assets/flows-DsUb.png)
Flujo de entradas y salidas de DCR para el cluster DsUb

![distribucion-de-salidas-gasto](./assets/outputs-distribution-DsUb.png)
Distribución de las salidas (gasto) de DCR hacia direcciones externas

Este parece que podría ser un grupo de minería de segundo nivel. No estoy seguro de cuál es el propósito de agrupar los fondos en una dirección antes de enviarlos a otra para distribuirlos a los mineros, pero así es como parece estar funcionando. La dirección que recibió la mayor parte de estos pagos obtuvo 139 000 DCR, eché un vistazo rápido y han enviado 71 500 a Binance, 2 500 a Bittrex y 1 600 a Poloniex.

La segunda dirección en la clasificación de salidas para este clúster (DsgK) se muestra a continuación porque también recibió DCR extraído de otro lugar.

Este clúster ha enviado a 1 377 direcciones diferentes que no forman parte del clúster, la mayoría de estas probablemente sean pagos a mineros. Entre los beneficiarios aquí se encuentran algunas direcciones de exchanges, incluidas 71 500 DCR que van a 111 direcciones de Binance, 2 543 DCR a 119 direcciones de Bittrex y 1 637 DCR a 44 direcciones de Poloniex. Tomo esto como una señal más de que este clúster representa la infraestructura de un grupo de minería, o cómo si alguien registrara muchas cuentas en los exchanges para que de la impresión de muchos usuarios.

![red-cluster-dsub](./assets/cluster-DsUb-using-layout-fr-rows-2000.png)
Visualización de red para el clúster DsUb

## 2 - DshF

Este clúster se inició en mayo de 2018 y recibió 292 000 DCR en la etapa 1 del coinbase (también recibió 73 000 directamente en recompensas de PoW y algo más en la etapa 2). Este grupo de minería también tiene algunos resultados en los rastreadores de flujo del Airdrop y del fondo de tesorería: se enviaron 174 DCR del airdrop a direcciones controladas por este grupo de minería, así como 1 132 DCR en de la primera etapa desde el fondo de tesorería; hay 4 transacciones a las que un contratista de Decred parece haber enviado DCR a direcciones en este clúster. Este grupo de minería también recibió 680 DCR mezclados de algún lugar. Independientemente de lo que estén haciendo, abarca más que administrar un grupo de minería.

![balance-dshf](./assets/balance-DshF.png)
Balance en DCR del clúster DshF

El grupo de minería conserva un saldo significativo de DCR.

![balance-dshf](./assets/flows-DshF.png)
Flujo de entradas y salidas de DCR para el cluster DshF

![flujo-entradas-salidas-dshf](./assets/outputs-distribution-DshF.png)
Distribución de las salidas (gasto) de DCR hacia direcciones externas

Hay muchas direcciones y cada una recibió un poco de DCR de este grupo de minería, pero algunas recibieron mucho, y una dirección obtuvo más de 300 000. Apliqué una transformación logarítmica al eje y en este gráfico, esto hizo que las barras para casos individuales desaparecieran, así que agregué números para las barras.

Este clúster ha recibido DCR de fuentes distintas a la minería y ha enviado una gran cantidad de DCR a los exchanges: 832 000 a Binance, 349 000 a Bittrex y 99 000 a Poloniex. El número y el patrón de estos depósitos a los exchanges indican que este grupo de minería probablemente cubre a muchos usuarios distintos, pero no estoy seguro de por qué está enredado con un saldo significativo de DCR. Es posible que algo no esté al 100% con la agrupación en este caso, pero todavía tengo que identificar los problemas en estos datos. Esto también puede ser el aspecto de la billetera para una entidad que brinda algunos otros servicios, así como un grupo de minería, como un OTC o una solución de custodia.

![red-cluster-dshf](./assets/cluster-DshF-using-layout-kk-rows-2000.png)
Visualización de red para el clúster DshF

## 3 - DsgK

Este clúster inició en diciembre de 2018, recibió 201 000 DCR en de la etapa 1 de la recompensa por PoW; la fuente es el clúster DscM anterior.

![balance-dsgk](./assets/balance-DsgK.png)
Balance en DCR del clúster DsgK

El saldo se pone a cero periódicamente.

![flujo-entradas-salidas-dsgK](./assets/flows-DsgK.png)
Flujo de entradas y salidas de DCR para el cluster DsgK

![salidas-dsgK](./assets/outputs-distribution-DsgK.png)
Distribución de las salidas (gasto) de DCR hacia direcciones externas

La mayor parte del DCR va a una dirección y no es una dirección que coincida con ningún exchange. En este caso podríamos asumir que el minero envía de una billetera a otra que también controla, y sigue el DCR desde esa dirección en adelante. Este es el tipo de juicio que haré cuando construya la historia más completa de la blockchain de Decred, y al observar cómo interactúan los clústeres, debería ser posible explicar mucho más las motivaciones detrás de las transacciones.

![red-cluster-dsgK](./assets/cluster-DsgK-using-layout-drl-rows-2000.png)
Visualización de red para el clúster DsgK

## 4 - DsVy

Este clúster inició en febrero del 2019 y recibió 191 000 DCR de la etapa 1 del coinbase, proveniente del clúster de minería Dsju anterior.

![balance-dsvy](./assets/balance-DsVy.png)
Balance en DCR del clúster DsVy

Permiten que el saldo crezca a cientos o miles de dólares antes de que la mayor parte se transfiera.

![flujo-entradas-salidas-dsvy](./assets/flows-DsVy.png)
Flujo de entradas y salidas de DCR para el cluster DsVy

![salidas-dsvy](./assets/outputs-distribution-DsVy.png)
Distribución de las salidas (gasto) de DCR hacia direcciones externas

33 000 de las salidas DCR de este clúster fueron a Binance, 143 DCR a Bitrex y 231 DCR a Poloniex. Parece un grupo de minería que hace pagos a los mineros, pero posiblemente podría ser la billetera de un individuo.

![red-cluster-dsvy](./assets/cluster-DshF-using-layout-kk-rows-500.png)
Visualización de red para el clúster DshF

## 5 - DsgR

Este clúster inició en septiembre del 2018, tiene 141 000 DCR por la etapa 1 de las recompensas en PoW, pero también extrajo 10 877 bloques directamente y reclamó 112 000 DCR por hacerlo.

![balance-dsgr](./assets/balance-DsgR.png)
Balance en DCR del clúster DsgR

Este grupo de minería conserva un balance significativo, lo que sugiere que es más probable que represente a un individuo. El clúster también parece recibir sumas significativas de DCR de fuentes distintas a la minería, pero el único impacto que obtuve para la fuente de esto es 10 DCR que viajó en la etapa 2 de un pago del fondo de tesorería.

![flujo-entradas-salidas-dsgr](./assets/flows-DsgR.png)
Flujo de entradas y salidas de DCR para el cluster DsgR

![salidas-dsgr](./assets/outputs-distribution-DsgR.png)
Distribución de las salidas (gasto) de DCR hacia direcciones externas

Las direcciones de salida para este clúster incluyen Binance (131 000 DCR), Bittrex (2 300 DCR) y Poloniex (6 DCR).

![red-cluster-dsgr](./assets/cluster-DsgR-using-layout-kk-rows-2000.png)
Visualización de red para el clúster DsgR

## Mineros en los exchange

Además de esta visión basada en la agrupación de las direcciones de los mineros, también he analizado las recompensas de PoW desde una perspectiva de las exchanges, específicamente Binance. Estoy bastante seguro de que esto captura todos los PoW enviados por los mineros a Binance.

![recompensa-pow-depositada-a-binance](./assets/mining-rewards-deposited-to-binance-per-month.png)
Flujo de DCR extraído a Binance

## Minero en el bloque de votación

Este informe no entra en el tema de los principales votantes de la red, ya que esto se tratará en su propio reporte. Sin embargo, ya he desarrollado las herramientas para esto, y como ninguno de los principales mineros votó sobre las propuestas de Politeia, he seleccionado otro minero para mostrar el gráfico.

El clúster de Dcgi que inició en abril del 2018, extrajeron 1 621 DCR de la etapa 1 del coinbase, subiendo a 2 230 DCR en la etapa 2, una minoría de los 57 000 DCR que llegaron a este clúster, por lo que probablemente también estaban comprando o recibiendo algo en otro lugar.

Dcgi también ha comprado 2 798 tickets, y he mirado cada ticket para ver 1) cuántas propuestas de Politeia era elegible para votar mientras estaba en vivo, 2) cuántas de estas propuestas votó, 3) si cada una de sus votos estaban de acuerdo o en oposición a la mayoría. He etiquetado los votos en los que el ticket vota de manera opuesta a la mayoría como “**vote cast**”. Tenía curiosidad sobre el 5-10% de las entradas que parecen votar Sí en cosas locas o No en propuestas que parecen victorias fáciles, así que he seleccionado un grupo de minería de ejemplo que se involucra en este tipo de comportamiento.

![votacion-cluster-dcgi](./assets/Dcgi-plot.png)
Votación en el clúster de dcgi

En total, los tickets de este grupo de minería han tenido la oportunidad de votar 6 223 veces sobre las propuestas de Politeia; han aprovechado esta oportunidad 139 veces (todas sin votos). Dcgi fue un "votante en contra" durante un tiempo, pero en este caso es probable que sea solo un efecto secundario de solo votar No en las propuestas: simplemente estaban votando en un momento en que la mayoría de las propuestas estaban aprobadas.

En cualquier caso, Dcgi no votó en las propuestas de Politeia durante mucho tiempo, y después de votar en 5 propuestas diferentes se detuvieron. Aunque posteriormente aumentaron la compra de tickets, ya no votan sobre las propuestas de Politeia.

Dcgi entonces no es parte de una conspiración a pequeña escala para votar en contra de la mayoría en todo, pero seguiré buscando este tipo de votante, y tengo otras métricas de "contrariedad" más experimentales en mi bolsillo para ayudar a encontrarlos.

Algo más a tener en cuenta en los grupos de votación será este patrón de abandonar la votación de Politeia (que es completamente opcional) mientras se continúa participando en staking. Si este patrón se vuelve común, podría indicar algún problema con el mantenimiento del staking de los votantes en las propuestas de Politeia.

![red-cluster-dcgi](./assets/cluster-Dcgi-using-layout-stress-rows-10000.png)
Visualización de red para el clúster Dcgi

## Tabla de comparación de los mineros

[Una gran tabla con la mayoría de las variables](./PoW-miners-top-10-clusters-stats.csv) que produje para el análisis de los conglomerados.

## Viendo desde lejos

Mientras escribía todo eso y obtenía esos gráficos de red dibujados a la perfección, se completó la agrupación completa de los destinos de transacción de las etapas de recompensa 1 y 2 de PoW. Se han considerado todas las direcciones que han recibido DCR dentro de las 3 etapas del coinbase, y he mirado para ver si se agrupan con otras direcciones. En total, había 35 890 direcciones en el conjunto y se produjeron 13 411 clústeres, pero más de la mitad de estos (8 559) son direcciones de un solo uso que no se agrupan con ninguna otra dirección y tienen un máximo de 2 transacciones (1 recibo y 1 gasto). Estas direcciones juntas no son demasiado significativas, obteniendo 23 etapas de 1 DCR, 68 000 en la etapa 2 y 132 000 en la etapa 3. Una forma de leer esto es que establece un máximo probable en el número de diferentes entidades que extraen DCR en este período: 4 852. Sin embargo, dentro de este número, es probable que algunos mineros usen más de una billetera, o usen direcciones nuevas con la frecuencia suficiente para que su actividad se haya dividido en más de un grupo de minería.

Para concluir, quería producir una visualización de red más práctica para las recompensas de PoW, que transmite información de una manera más sencilla. Establecí un objetivo para mostrar todos los movimientos de recompensa de PoW durante un período de 3 etapas. El período que terminó funcionando fue de aproximadamente 3 meses (desde el 1 de octubre de 2020 hasta el 9 de enero de 2021), pero tuve que eliminar muchas transacciones pequeñas (cualquier cosa que valga menos de 10 DCR) y direcciones (cualquiera que haya recibido menos de 1 000 DCR ) para que sea legible. Esto utiliza un diseño de árbol, con las direcciones que recibieron recompensas de PoW directamente desde el coinbase que se colocan como la capa superior. Moviéndose hacia abajo en el gráfico, el DCR fluye a la transacción, luego a la dirección, y algunos van a Binance (no hay otros exchanges en este conjunto) y algunos se meten a staking, como una ventaja, también puede ver algunos de los DCR de diferentes grupos en la billetera hot de Binance.

![100-dias-de-flujo-pow](./assets/PoW-Rewards-Flow-Oct2020-Jan2021.png)
100 días y 3 etapas de flujos de recompensa en PoW

Esta publicación se centra en el ciclo de vida inicial de DCR extraído, a medida que fluye en los exchanges, OTC o al grupo de tickets. Lo siguiente podría ser una mirada más cercana a los exchanges, votantes o el grupo de mezclado: el orden depende en parte de con qué avance mejor, pero debería haber un flujo más regular de reportes en blockchain por un tiempo después de la larga brecha desde el reporte inicial. Esta investigación está financiada por el fondo de tesorería de Decred (aplaude a los stake holders), y mis planes para las próximas investigaciones dependen de que se renueven los fondos a través de una próxima propuesta.
