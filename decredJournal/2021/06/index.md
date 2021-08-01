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
