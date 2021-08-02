# Revista Decred Junio 2021

![portada]('./assets/202006.png)
Core Lattice por @saender

Lo más destacado de junio:

- Se aprobó una próxima actualización de consenso en Politeia que haría que los cambios de consenso futuros sean más fáciles, más confiables y más seguros.
- Un error con los controles de los gastos de tesorería provocó la imposición de un límite demasiado bajo; esto requerirá una actualización por consenso para solucionarlo.
- Tres propuestas de Politeia aprobadas con una alta participación (~ 47%) y votos a favor (97–99%): Bug Bounty, Traducciones y la versión explícita de mejora en el cambio de consenso.
El hashrate de PoW ha experimentado una caída significativa, probablemente asociada con la represión de la minería en China.

Contenido

- [Nuevo bug en el fondo de tesorería]()
- [Desarrollo]()
- [Comunidad]()
- [Gobernanza]()
- [Red]()
- [Ecosistema]()
- [Alcance]()
- [Eventos]()
- [Media]()
- [Discusiones]()
- [Mercado]()
- [Relevantes externos]()
- [Sobre]()


## Nuevo bug en el fondo de tesorería

Los pagos del nuevo fondo de tesorería están bloqueados durante varios meses por un error en la implementación de la política de gastos. La transacción de gasto de tesorería de prueba extraída el [22 de mayo](https://explorer.dcrdata.org/tx/7507bcc72bfde895065034e12e6d462f2360163cd0c879f0db35514f9456b2c1) desencadenó una condición pasada por alto en el mecanismo de seguridad que protege de gastar demasiado DCR en un corto período de tiempo. Durante los próximos meses, solo se pueden gastar alrededor de 0.15 DCR de la nueva tesorería, que es demasiado bajo para pagar a los contratistas.

Si bien este es un retraso desafortunado en la migración a la tesorería descentralizada y trabajo adicional para corregir el error, el plan de migración se creó para manejar casos como este. Todos los fondos de la red están seguros y los pagos de los contratistas continuarán desde la tesorería anterior. Arreglar el algoritmo de seguridad requiere otro cambio de consenso que está [en desarrollo](https://github.com/decred/dcps/pull/20).

Leé la historia completa del error en la [publicación del blog](https://blog.decred.org/2021/06/25/Treasury-Expenditure-Policy-Bug/) y en los hilos de Twitter de [@matheusd](https://twitter.com/matheusd_tech/status/1409928455974699013) y [@lukebp](https://twitter.com/lukebp_/status/1409929016400822279).

> En una nota al margen, este incidente nos recuerda que incluso el código de consenso ampliamente [revisado](https://github.com/decred/dcrd/pull/2170) y probado no es inmune a los errores, pero son más fáciles de corregir cuando existe un proceso de actualización bien definido y no controvertido.

## Desarrollo

## Comunidad

¡Damos la bienvenida a los nuevos contribuidores con código fusionado en la rama principal:  @vibros68 ([politeiagui](https://github.com/decred/politeiagui/commits?author=vibros68)) y @x-walker-x ([politeiagui](https://github.com/decred/politeiagui/commits?author=x-walker-x))!

Estadísticas de la comunidad :

- Seguidores de [Twitter](https://twitter.com/decredproject): 46 919 (+1 195)
- Suscriptores de [Reddit](https://www.reddit.com/r/decred/): 11 322 (+132)
- Usuarios en la sala #general de [Matrix](https://chat.decred.org/): 501 (+34)
- Usuarios de [Discord](https://discord.com/invite/GJ2GXfz): 1 933 (+146)
- Usuarios de [Telegram](https://t.me/Decred): 2 733 (+28)
- Suscriptores de [Youtube](https://www.youtube.com/decredchannel): 4 570 (+30), views: 188K (+2K)
- Estrellas en el repo de [dcrd](https://github.com/decred/dcrd): 601 (+3), forks: 256 (+1)

El resumen de junio de la inusual dinámica de las redes sociales se puede encontrar [aquí](https://decredcommunity.github.io/social-media-stats/posts/20210711.1).

## Gobernanza

En junio, el [nuevo fondo de la tesorería](https://dcrdata.decred.org/treasury?chart=balance&zoom=knj8yxs0-kse64gw0&bin=month) recibió 10 510 DCR por un valor de 1.4 millones de dólares a la tasa promedio de mayo de 131.52 dólares. Se gastaron 1 460 DCR (de la dirección de tesorería heredada) para pagar a los contratistas, por un valor de $192 000 a la tasa de junio, o $253 000 a la tasa de facturación de mayo de $173.47. Al 2 de julio, el saldo combinado de la nueva tesorería [heredada](https://dcrdata.decred.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx?chart=balance&zoom=ijhhasg0-kr5vh280&bin=month) es de 692 988 DCR (91.4 millones de dólares a 131.88 dólares). 

La primera transacción real de la nueva tesorería no se extrajo debido al [bug](https://xaur.github.io/decred-news/journal/202106#new-treasury-bug) descrito anteriormente y los contratistas recibieron el pago de la antigua manera. A pesar de que no funcionó según lo [planeado](https://twitter.com/behindtext/status/1402628975676035078), esa transacción mostró un alto compromiso de los votantes en cadena y un alto apoyo de la administración actual de la tesorería: 11 943 tickets, 17 280 votaron Sí y cero votaron No, fue una participación del 69%. Este podría aumentar aún más cuando se implemente la votación TSPEND para los usuarios de VSP, que actualmente poseen alrededor del 20% de los tickets en vivo.

Se publicaron tres propuestas en Politeia y las tres han sido aprobadas con fuertes índices de aceptación.


- La propuesta de [cambio de consenso de actualizaciones de versión explícita](https://proposals.decred.org/record/3a98861) alcanzó un nuevo hito de aprobación con un 99.9% de votos a favor y solo 13 tickets votando en contra de la propuesta, entre el 47% de participación.

- La cuarta iteración de la [propuesta](https://proposals.decred.org/record/e1f104b) de Bug Bounty regresó con un calendario de pagos mejorado y fue aprobada con un 98.5% de votos a favor y una participación del 47%. Esto es + 0.5% de votos a favor y + 15% de participación en comparación con la [Fase 3](https://proposals-archive.decred.org/proposals/2170df6). @degeri [agradece](https://twitter.com/degeri_crypto/status/1409714139396591617) a los stakeholders por la creciente cantidad de fe y confianza.

- La segunda fase de la gran [propuesta](https://proposals.decred.org/record/af9942a) de traducción fue aprobada con un 97.3% de aprobación y una participación del 46%, un gran aumento en el apoyo del 75% Sí y el 28% de participación para la primera [propuesta](https://proposals-archive.decred.org/proposals/c093b8a).
- 
Consulte el [issue #43](https://blockcommons.red/politeia-digest/issue043/) de Politeia Digest para obtener más detalles sobre las propuestas del mes.
