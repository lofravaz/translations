# Revista Decred Mayo 2021

Novedades en Mayo

- El nuevo sistema del fondo de tesorería está recibiendo activamente recompensas en bloque y ya se ha probado de manera exitosa con las nuevas transacciones tspend.
- Se lanzó la versión 1.6.3 del software de nodos y billeteras para corregir algunos problemas con la participación del VSP y agregar algunas de las funciones más recientes.
- Se lanzó DCRDEX v0.2.0, incorporando más de 3 meses de trabajo, y se agregó una integración del DCRDEX experimental a Decrediton v1.6.3.

Contenido

- [Lanzamiento del parche v1.6.3](https://github.com/DecredES/translations/new/master/decredJournal/2021#nuevo-parche-v163)
- [Nueva tesorería activada](https://github.com/DecredES/translations/new/master/decredJournal/2021#la-nueva-tesorer%C3%ADa-por-fin-se-encuentra-activa)
- [Desarrollo]()
- [Comunidad](https://github.com/DecredES/translations/new/master/decredJournal/2021#comunidad)
- [Gobernanza](https://github.com/DecredES/translations/new/master/decredJournal/2021#gobernanza)
- [Red]()
- [Ecosistema]()
- [Divulgación]()
- [Media]()
- [Discusiones]()
- [Mercados]()
- [Relevante Externo]()
- [Sobre esta versión]()

## Nuevo parche V1.6.3
La última versión de nuestra billetera insignia de GUI, Decrediton, soluciona problemas con el staking de VSP, hace que la billetera sea más "genial" con el desbloqueo granular de cuentas y agrega la integración experimental de la [nueva versión del DCRDEX](https://xaur.github.io/decred-news/journal/202105#dcrdex). La línea de comandos dcrwallet también se actualiza con correcciones y mejoras del staking en VSP.

Los usuarios de Decrediton deben tener en cuenta:

- La pestaña DEX solo se muestra en modo completo y está oculta en modo SPV.
- Necesita ejecutar Bitcoin Core y sincronizarlo completamente para usar la pestaña DEX.
- La descarga de Windows se actualizó para corregir el [error](https://github.com/decred/decrediton/pull/3469) predeterminado del directorio de Bitcoin, si obtuvo el instalador antes del 25 de mayo, descárguelo de nuevo y vuelva a instalarlo.

Vea las notas de la versión completa y las descargas [aquí](https://github.com/decred/decred-binaries/releases/tag/v1.6.3). Como siempre, respete el ritual de [verificación de firmas](https://docs.decred.org/advanced/verifying-binaries/) para asegurarse de ejecutar los binarios correctos.

## La nueva tesorería por fin se encuentra activa

Las nuevas reglas de consenso se activaron el 8 de mayo. A partir del bloque [552,448](https://explorer.dcrdata.org/block/00000000000000001c6fc262b2673d94827f87daa329b0bdeb7866562ef919cf), el 10% de las recompensas del bloque fluyen a la [nueva cuenta del fondo de tesorería](https://explorer.dcrdata.org/treasury?chart=balance&zoom=knj8yxs0-kpz09i80&bin=month) y ya no fluyen a la [dirección anterior](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx).

La diferencia clave es que la nueva cuenta del Fondo de Tesorería está controlada por los stake holders de Decred. Gastar desde la dirección anterior solo requería una transacción firmada por Decred Holdings Group LLC ("DHG"), una entidad corporativa convencional creada para iniciar Decred. Solo es posible gastar desde la nueva cuenta si los stake holders votan para aprobar una transacción especial de “gasto de tesorería” (“tspend”).

Un sofisticado proceso de votación para respaldarlo se especificó en [Decred Change Proposal 6](https://github.com/decred/dcps/blob/master/dcp-0006/dcp-0006.mediawiki) y se implementó en la versión de software v1.6. En términos simples, los pasos clave son:

- Los administradores de Politeia crean una transacción tspend que se ajusta a ciertos requisitos (no gastar demasiado dinero, con un tiempo de vencimiento no demasiado largo, firmada por una de las dos claves permitidas por consenso, etc.)
- La transacción se publica en el mempool y las billeteras de votación comienzan a votar sobre ella.
- La votación tiene una duración de hasta 12 días, pero puede acelerarse a tan solo ~ 7 días si el resultado no se puede cambiar por los votos restantes.
- Hasta 17,280 tickets que son llamados a votar durante este período pueden emitir votos para gastar (junto con la aprobación de bloque normal y los votos de actualización por consenso).
- Si se aprueba la votación, la transacción se incluye en un bloque (hasta 1 día después) y se paga a los contratistas.

El nuevo sistema de la tesorería se probó con éxito en mainnet rápidamente después de la activación. El 10 de mayo se [notificó](https://twitter.com/decredproject/status/1391877816292151296) a los stake holders que configuraran sus billeteras de votación. Luego, el 12 de mayo, se transmitió a la red una pequeña [transacción](https://explorer.dcrdata.org/tx/7507bcc72bfde895065034e12e6d462f2360163cd0c879f0db35514f9456b2c1) tspend de prueba. La ventana de votación más cercana fue del 13 al 24 de mayo, pero el voto tuvo una aceleración después de acumular 6,755 votos a favor y 1 en contra durante 9 días. De los 12,550 tickets que tuvieron la oportunidad de votar en ese período, el 54% votó activamente. El tspend se extrajo en el bloque [556,416](https://explorer.dcrdata.org/block/000000000000000000b8bed4b8511e3c5197d3eee6372db2ba199481e14d5376).

A partir de la versión del software v1.6.3, la votación tspend solo es compatible con los "votantes en solitario" que administran billeteras de votación las 24 horas del día, los 7 días de la semana (~ 77% de todos los stakeholders a partir del 1 de junio). [Se está trabajando para habilitar](https://github.com/decred/decrediton/issues/3184) esto para los votantes de VSP.

La votaciónp para el gasto del fondo de tesorería se convertirá en un proceso mensual importante para pagar a las personas que construyen Decred. [Se aconseja](https://twitter.com/decredproject/status/1391877959410233344) a los votantes individuales que se preparen para las próximas votaciones tspend configurando sus billeteras de votación con el siguiente comando:

```code

dcrctl --wallet settreasurypolicy "03f6e7041f1cf51ee10e0a01cd2b0385ce3cd9debaabb2296f7e9dee9329da946c" "yes or no"

```

Este comando expresa su confianza en la administración de la tesorería actual y su clave ```03f6e704 ...```, y establece cómo su billetera votará por los gastos firmados por ella. Puede verificar esta clave en el [DCP-0006](https://github.com/decred/dcps/blob/master/dcp-0006/dcp-0006.mediawiki) o en el [código fuente](https://github.com/decred/dcrd/blob/master/chaincfg/mainnetparams.go#L389). La votación es semiautomatizada con esta configuración única, pero es posible votar en transacciones tspend individuales cuando se necesita un control más granular.

¡Felicitaciones a todas los stake holders por este hito y gracias a todos los [colaboradores](https://twitter.com/matheusd_tech/status/1390981711736053760) que lo han hecho realidad!

## Comunidad

Damos la bienvenida a los nuevos colaboradores con código fusionado de la rama principal: @LasTshaMAN ([politeia](https://github.com/decred/politeia/commits?author=LasTshaMAN))!

- Seguidores en [Twitter](https://twitter.com/decredproject): 45,724 (+1,333)
- Suscriptores en [Reddit](https://www.reddit.com/r/decred/): 11,190 (+203)
- Usuarios en la sala [#general de Matrix](https://chat.decred.org/): 467 (+25)
- Usuarios en [Discord](https://discord.com/invite/GJ2GXfz): 1,787 (+221)
- Usuarios en [Telegram](https://t.me/Decred): 2,705 (+60)
- Suscriptores en [YouTube](https://www.youtube.com/decredchannel): 4,540 (+40), visualizaciones: 186,000 (+4,000)
- Estrellas en el repositorio dcrd en [GitHub](https://github.com/decred/dcrd): 598 (+7), forks: 255 (+1)

Ya se [publicó](https://decredcommunity.github.io/social-media-stats/posts/20210604.1) el resumen de mayo de las interesantes dinámicas de las redes sociales, ahora con tablas para facilitar la lectura. Se agradecen los comentarios para comprender lo valiosos que son estos informes.

Las tablas de crecimiento de la comunidad se han modificado, actualizado y trasladado a una nueva [ubicación](https://decredcommunity.github.io/social-media-stats/docs/charts).

## Gobernanza

En mayo, el fondo de la tesorería recibió 11 342 DCR (2 564 para la [dirección anterior](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) y 8 778 para el [nuevo sistema](https://explorer.dcrdata.org/treasury?chart=balance&zoom=knj8yxs0-kr5vh280&bin=month)) por valor de 1.97 millones de dólares a la tasa promedio de mayo de 173.47 dólares. No se gastó DCR en mayo. El 2 de junio, se gastaron 698 DCR de la dirección anterior para las facturas de abril, por un valor de $121K a la tarifa de mayo, o $ 139 000 a la tarifa de facturación de abril de $198.60. Al 3 de junio, el saldo combinado del fondo de de tesorería es de 683 438 DCR (107 millones de dólares a 156 dólares cada DCR).

En mayo se presentó y aprobó 1 propuesta, la propuesta para el desarrollo continuo de Politeia (detallada el [mes pasado](https://xaur.github.io/decred-news/journal/202104)) tuvo una aprobación del 98.4% y una participación del 44%.

Se han [agregado](https://twitter.com/_Checkmatey_/status/1392266971228430338) gráficos de la tesorería en [checkonchain.com](https://checkonchain.com/) para ayudar con las decisiones de gobernanza en torno a los gastos.
