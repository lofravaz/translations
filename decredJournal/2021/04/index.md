# Revista Decred Abril 2021

![portada](./assets/202104.png)
El punto de la integral por @saender

Destacados de Abril

- La sexta votación por consenso de Decred ha sido aprobada por unanimidad y con una alta participación de votantes.
- Politeia v1.0 ya está disponible con una infraestructura más escalable y preparada para el futuro.
- Se está votando la primera propuesta de Politeia para formalizar la hoja de ruta de desarrollo y el presupuesto.
- DCRDEX se dirige hacia la actualización v0.2 con varias mejoras de backend y UX, así como las bases para futuras funciones interesantes.
- La integración inicial de DCRDEX se ha fusionado en Decrediton.

Contenido:
- [Desarrollo](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#desarrollo)
- [Comunidad](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#comunidad)
- [Gobernanza](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#gobernanza)
- [Red](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#red)
- [Ecosistema](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#ecosistema)
- [Alcance](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#alcance)
- [Eventos](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#eventos)
- [Media](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#media)
- [Discusiones de la comunidad](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#discusiones-de-la-comunidad)
- [Mercados](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#mercados)
- [Relevantes externos](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#relevantes-externos)
- [Sobre esta edición](https://github.com/DecredES/translations/blob/master/decredJournal/2021/04/index.md#sobre-esta-edici%C3%B3n)

## Desarrollo

[**dcrd**](https://github.com/decred/dcrd)

- Código base [convertido](https://github.com/decred/dcrd/pull/2625) para usar el nuevo paquete `stdaddr`. El código que se ocupa de las direcciones ahora admite diferentes versiones de secuencias de comandos y está un paso más cerca de poder introducir de forma limpia nuevas versiones de lenguajes de secuencias de comandos. Como es común para los cambios grandes, para facilitar la revisión, este se dividió en una serie de confirmaciones individuales de modo que todo se compile y pase todas las pruebas en cada paso del camino.
- Introucir la [base de datos UTXO](https://github.com/decred/dcrd/pull/2632). Allana el camino para una implementación de base de datos UTXO especializada que se puede hacer más eficiente en términos de tiempo de procesamiento y uso de memoria.
- Se agregó un [tiempo medio](https://github.com/decred/dcrd/pull/2638) durante los últimos 11 bloques para obtener resultados detallados de `getblock` y `getblockheader` (utilizado por DCRDEX).
- Permitir especificar interfaces de red para escuchar por sus [nombres](https://github.com/decred/dcrd/pull/2623) además de las direcciones IP exactas.

La [comparación](https://www.reddit.com/r/decred/comments/mi4ezt/initial_chain_sync_comparison_between_dcrd_v140/) inicial de la sincronización en cadena entre dcrd v1.4.0 y la última muestra cómo todas las mejoras se han acumulado en una gran diferencia en el rendimiento. A pesar de que ahora hay un 70% más de bloques, la última versión tarda casi el mismo tiempo en sincronizarse y asigna mucha menos memoria.

[**dcrwallet**](https://github.com/decred/dcrwallet)

- Un nuevo método que devuelve el [estado de sincronización](https://github.com/decred/dcrwallet/pull/1991) de la billetera.
- Manejar el estado del ticket cuando el VSP ha [recibido](https://github.com/decred/dcrwallet/pull/1965) su tarifa tx pero aún no la ha transmitido.
- Errores corregidos encontrados cuando es utilizado por DCRDEX.

[**Decrediton**](https://github.com/decred/decrediton)

- [Integración](https://github.com/decred/decrediton/pull/3356) inicial del DEX.
- Formulario para [depositar](https://github.com/decred/decrediton/pull/3426) a la cuenta del DEX desde la vista de registro.
- Permitir usar una cuenta de billetera [existente](https://github.com/decred/decrediton/pull/3438) para el DEX en lugar de crear una nueva.
- Agregada generación de [código QR](https://github.com/decred/decrediton/pull/3112) para exportar tickets activos (para seguimiento con la aplicación Decred Address Scanner).
- [Recordar](https://github.com/decred/decrediton/pull/3441) la configuración del comprador automático de tickets.
- Agregó una migración para [inicializar](https://github.com/decred/decrediton/pull/2664) las frases de contraseña de la cuenta con la frase de contraseña de la billetera. Además, algunas operaciones (enviar, comprar ticket, mezclar, revocar) cambiaron para desbloquear solo una cuenta en lugar de desbloquear una billetera completa.
- Bloquear [nuevas cuentas](https://github.com/decred/decrediton/pull/3424) después de la creación
- Permitir restaurar semillas hexadecimales de hasta 128 caracteres (incluidas las semillas BIP0039).
- Diseño actualizado de las vistas de [transacciones](https://github.com/decred/decrediton/pull/3326), [propuestas](https://github.com/decred/decrediton/pull/3345) y [compra de tickets](https://github.com/decred/decrediton/pull/3349).
- Muchos ajustes de diseño más pequeños.
- Cambió a una generación estricta de Protobuf sin `eval()` y restringido para acceder solo a servidores externos a través de `https` en compilaciones de producción utilizando el encabezado [CSP](https://github.com/decred/decrediton/pull/3366).
- Refactorización de la gestión estatal, separación de preocupaciones, actualizaciones de dependencia.
- Mayor cobertura de prueba.
- ~ 24 correcciones de errores.

Se está preparando la versión [v1.6.3](https://github.com/decred/decrediton/tree/release-v1.6%2B), incluidos muchos de los cambios anteriores.

[**Politeia**](https://github.com/decred/politeia)

Politeia v1.0.0 se ha lanzado con el nuevo backend de almacenamiento, API optimizada, nueva arquitectura de complementos y 5 complementos. Leé las [notas de la versión](https://github.com/decred/politeia/releases/tag/v1.0.0) para obtener detalles completos sobre cada función. La nueva versión se ha implementado en [proposals.decred.org](https://proposals.decred.org/).

El soporte de 2FA intentó con todas sus fuerzas escapar de nuestra atención y ahora está disponible. Los usuarios pueden configurarlo en la configuración de la cuenta. No olvide hacer una copia de seguridad de la clave.

Añadido en abril:

- Enumeración de las [propuestas](https://github.com/decred/politeiagui/pull/2340) de [proposals-archive.decred.org](https://proposals-archive.decred.org/) en proposals.decred.org para su conveniencia.
- [Verificar](https://github.com/decred/politeia/pull/1377) paquetes de comentarios y votos con la nueva herramienta `politeiaverify`.
- Enumeración de la tarifa de registro en el [historial](https://github.com/decred/politeiagui/pull/2322) de compras.
- ~ Se han corregido 24 errores descubiertos en la nueva versión.

Un cambio notable es la adición de [marcas de tiempo](https://github.com/decred/politeia/pull/1395) para emitir votos. En el backend de Git, las marcas de tiempo precisas no se almacenaban para mejorar la privacidad de los votantes y, como resultado, solo era posible determinar si un voto se emitió en un período de ~ 60 minutos. En tstore, Trillian ya está registrando la marca de tiempo del backend y esto no se puede cambiar sin escribir una implementación personalizada de Trillian. Debido a que la marca de tiempo de voto ahora es información pública de todos modos, agregarla directamente a la estructura de votación permite que dcrdata la obtenga mucho más fácilmente (por ejemplo, para construir sus [gráficos](https://dcrdata.decred.org/proposal/video-content-production-for-decred-phase-3) de votos). Pero también significa un poco menos de privacidad para las personas que emiten todos sus votos a la vez. Se recomienda encarecidamente a las personas que quieran proteger su privacidad que utilicen la [función](https://github.com/decred/politeia/blob/master/politeiawww/cmd/politeiavoter/README.md#privacy-considerations) `politeiavoter`.

@lukebp habló sobre el desarrollo de Politeia, los últimos lanzamientos y las direcciones futuras en el [podcast](https://www.youtube.com/watch?v=J6IAjmwkki0) Decred in Depth (comienza en el minuto 12).

La primera [propuesta](https://proposals.decred.org/record/91cfcc8) de Politeia está ahora en vivo (y votando), formalizando su hoja de ruta de desarrollo y presupuesto hasta finales de 2021.

[**dcrdpool**](https://github.com/decred/dcrpool)

- [Conectividad](https://github.com/decred/dcrpool/pull/317) mejorada.
- [Manejo](https://github.com/decred/dcrpool/pull/320) [minero](https://github.com/decred/dcrpool/pull/319) más [eficiente](https://github.com/decred/dcrpool/pull/318).

[**dcrlnd**](https://github.com/decred/dcrlnd)

- Soporte para desbloquear una cuenta específica (para Decrediton).

[**DCRDEX**](https://github.com/decred/dcrdex)

- Mostrar [información importante del servidor](https://github.com/decred/dcrdex/pull/1042) (como el tamaño del lote, cantidad mínima negociable) antes de que el usuario pague la tarifa de registro.
- Mejor manejo de pedidos [inactivos](https://github.com/decred/dcrdex/pull/1030).
- Utilizar un [tiempo medio](https://github.com/decred/dcrdex/pull/1058) para la finalización de la transacción.
- Asegurar de que todas las [tarifas](https://github.com/decred/dcrdex/pull/1060) estén limitadas por la configuración.
- Uso reducido de [memoria](https://github.com/decred/dcrdex/pull/1070) durante la actualización de la base de datos.
- GUI [adaptativo](https://github.com/decred/dcrdex/pull/1016).
- Soporte para la creación de [perfiles](https://github.com/decred/dcrdex/pull/1035) de CPU y HTTP.
- Experiencia mejorada del [couch testing](https://github.com/decred/dcrdex/pull/1038).
- Control de versiones agregado para la [API del servidor](https://github.com/decred/dcrdex/pull/1047) y backends de [activos](https://github.com/decred/dcrdex/pull/1054).
- Se corrigieron algunos problemas de sincronización.

En mayo se publicó una [actualización](https://www.reddit.com/r/decred/comments/n9i8z2/dcrdex_updates_v02_release_decrediton_integration/) sobre el desarrollo de la Fase 2 con los siguientes puntos clave:

- La versión v0.2 ha finalizado las pruebas beta, se esperan binarios y actualización del servidor pronto.
- v0.2 trae muchas mejoras, incluida la compatibilidad con la próxima integración de Decrediton.
- El soporte de billetera SPV para Decred y Bitcoin está planeado en los próximos lanzamientos de este año.
- El desarrollo de ETH está en progreso y se espera que se publique hacia el final de la Fase 2.

Para obtener más funciones interesantes, leé la [actualización](https://www.reddit.com/r/decred/comments/n9i8z2/dcrdex_updates_v02_release_decrediton_integration/) y las notas de la versión vinculadas.

[**dcrandroid**](https://github.com/planetdecred/dcrandroid)

- Muestra el [saldo equivalente en USD](https://github.com/planetdecred/dcrandroid/pull/539) en la página de descripción general.
- [dcrlibwallet](https://github.com/planetdecred/dcrlibwallet/pull/183) actualizado al nuevo módulo dcrwallet.

[**dcrios**](https://github.com/planetdecred/dcrios)

- Mostrar [propuestas](https://github.com/planetdecred/dcrios/pull/715) de Politeia y notificar ciertos eventos (nueva propuesta, votación iniciada, votación finalizada).
- Base de datos [actualizada](https://github.com/planetdecred/dcrios/pull/742) a BadgerDB.

[**godcr**](https://github.com/planetdecred/godcr)

- Mostrar [propuestas](https://github.com/planetdecred/godcr/pull/331) de Politeia.
- Interfaz de usuario pulida en [transacciones](https://github.com/planetdecred/godcr/pull/356), [billetera](https://github.com/planetdecred/godcr/pull/355) y páginas de [recepción](https://github.com/planetdecred/godcr/pull/354).
- Muestra el equivalente en USD en la [barra de navegación](https://github.com/planetdecred/godcr/pull/380) y en la ventana emergente de confirmación de [Enviar](https://github.com/planetdecred/godcr/pull/371).
- Añadido envío a [cuenta](https://github.com/planetdecred/godcr/pull/353) propia.
- Numerosos ajustes de UX más pequeños.

[**dcrdata**](https://github.com/decred/dcrdata)

- Diseño de página de [costo de ataque](https://github.com/decred/dcrdata/pull/1777) mejorado.
- Visualización mejorada de tx relacionados con el [fondo de tesorería](https://github.com/decred/dcrdata/pull/1817).
- Actualizado a [Webpack 5](https://github.com/decred/dcrdata/pull/1809) y otras dependencias.

[**docs**](https://github.com/decred/dcrdocs)

- [¡Modo nocturno!](https://github.com/decred/dcrdocs/pull/1161).
- Página de [migraciones](https://github.com/decred/dcrdocs/pull/1163) para el próximo Decrediton v1.6.3.

## Comunidad

Conoce a los colaboradores de Decred en las nuevas entrevistas con [@lukebp](https://www.youtube.com/watch?v=J6IAjmwkki0) y [@phoenixgreen](https://www.youtube.com/watch?v=WOVUvzsp3Eo).

Estádisticas de la comunidad al 1 de Mayo:

- Seguidores en [Twitter](https://twitter.com/decredproject): 44 391 (+763)
- Suscriptores de [Reddit](https://www.reddit.com/r/decred/): 10 987 (+190)
- Usuarios de la sala [#general](https://chat.decred.org/#/room/#proposals:decred.org) de Matrix: 434 (+27)
- Usuarios de [Discord](https://discord.com/invite/GJ2GXfz): 1 566 (+157)
- Usuarios de [Telegram](https://t.me/Decred): 2 645 (+51)
- Suscriptores de [Youtube](https://www.youtube.com/decredchannel): 4 500 (+40), vistas: 182 000 (+3 000)
- GitHub [dcrd](https://github.com/decred/dcrd) stars: 591 (+2), forks: 254 (-1)

Consulta el [informe de abril](https://decredcommunity.github.io/social-media-stats/posts/20210506.1) para conocer las actualizaciones destacadas de las estadísticas de las redes sociales.

## Gobernanza

En abril, el [fondo de tesorería](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) recibió 10 949 DCR y gastó 984 DCR. Usando la tasa de DCR promedio de abril de $198.60, esto es $2.17 millones recibidos y $195 mil gastados. A la tasa promedio de marzo de 161.01 dólares, los dólares estadounidenses facturados por trabajos anteriores son 158 000 dólares. Al 2 de mayo, el saldo del fondo de tesorería es de 672 768 DCR (140 millones de dólares a $208.13).

La votación por consenso para habilitar la nueva tesorería [ha sido aprobada](https://explorer.dcrdata.org/agenda/treasury) con un 99.9% de aprobación y un 83% de participación de los votantes. Esta es la segunda participación de votantes más alta en la historia de Decred después de la votación de [dificultad de staking](https://dcrdata.decred.org/agenda/sdiffalgorithm) en 2017 (88%).

Nuevas propuestas: 

- Una nueva [propuesta](https://proposals.decred.org/record/91cfcc8) para financiar el desarrollo de Politeia acompañó el despliegue de v1.0.0. Esta propuesta solicita un presupuesto máximo de 118 000 dólares para cubrir una variedad de funciones nuevas, que se espera que se entreguen durante un período de seis meses. Las características de este roadmap incluyen otra actualización de la arquitectura, revisión de la API del usuario, cuentas sin correo electrónico, metadatos adicionales para las propuestas, ciclos de vida de las propuestas y actualizaciones del autor de las propuestas. La votación comenzó el 11 de mayo.
- La [propuesta](https://proposals-archive.decred.org/proposals/95a1409) para la fase 3 de producción de video fue aprobada con un 98% de aprobación y una participación de los votantes del 40%.
- La propuesta del dominio de diseño para el resto de 2021 fue [aprobada](https://proposals-archive.decred.org/proposals/76eba5a) con una aprobación del 97% y una participación de los votantes del 28%.

Consulta el [número 42](https://blockcommons.red/politeia-digest/issue042/) de Politeia Digest para obtener más detalles sobre las propuestas del mes.

## Red

Hashrate: el [hashrate](https://explorer.dcrdata.org/charts?chart=hashrate&zoom=kmvlwq6x-ko7rp8zy&scale=linear&bin=block&axis=time) de abril se abrió a ~464 Ph/s y cerró ~429 Ph/s, tocando fondo en 219 Ph/s y alcanzando un máximo de 587 Ph/s durante todo el mes.

Distribución de hashrate [reportada](https://miningpoolstats.stream/decred) por los pools el 1 de mayo: 
- Poolin 35%
- Antpool 28%
- F2Pool 18%
- Easy2Mine 4%
- BTC.com 1.8%
- Luxor 1.3%
- UUPool 0.09%
- Coinmine 0.06%
- Huobipool 0.02%
- otros 12%.

Esta vez, el hashrate informado coincidió estrechamente con la distribución de 1 000 bloques realmente [minados](https://miningpoolstats.stream/decred).

Una fuerte caída del hashrate entre el 15 y el 20 de abril se ha atribuido a un importante [corte de energía en China](https://www.reddit.com/r/decred/comments/mvk976/network_hashrate_plummeting/).

**Staking**: el [precio del ticket](https://explorer.dcrdata.org/charts?chart=ticket-price&zoom=kmvlwq6x-ko7rp8zy&bin=window&axis=time&visibility=true-false) varió entre 163.5 y 204.1 DCR, con un [promedio](https://dcrstats.com/) a 30 días de 185.8 DCR (+7.8).

La [cantidad bloqueada](https://explorer.dcrdata.org/charts?chart=ticket-pool-value&zoom=kmvlwq6x-ko7rp8zy&scale=linear&bin=block&axis=time) fue de 7.11 a 7.51 millones de DCR, lo que significa que del 55.4 al 58.5% del suministro circulante [participó](https://explorer.dcrdata.org/charts?chart=stake-participation&zoom=kmvlwq6x-ko7rp8zy&scale=linear&bin=block&axis=time) en el staking.

**VSP**: El 1 de mayo, los servidores vspd administraron 7 100 (+ 500) tickets en vivo y los servidores de dcrstakepool antiguos enumerados fueron de 2 200 (-1 800). En conjunto, los 15 sistemas antiguos y los 13 nuevos VSP administraron el 23% del grupo de tickets. Los 2 VSP antiguos recientemente retirados de [la lista](https://decred.org/vsp/) todavía tenían 105 tickets en vivo.

**Nodos**: A lo largo de abril, hubo alrededor de 210 nodos accesibles según [dcrextdata](https://analytics.planetdecred.org/).

Versiones de nodo a partir de la [instantánea](https://nodes.jholdstock.uk/user_agents) del 1 de mayo (257 en total, solo dcrd): 
- v1.6.0–26%.
- v1.6.2–24%.
- v1.6.1–22%.
- v1.5.2–7%.
- v1.5.1–7%.
- Compilaciones de desarrollo v1.7: 7%.
- compilaciones de desarrollo v1.6: 4%, v1.5.0–2%.

La proporción de [monedas mixtas](https://explorer.dcrdata.org/charts?chart=coin-supply&zoom=kmvlwq6x-ko7rp8zy&bin=day&axis=time&visibility=true-true-true) ha disminuido ligeramente del 44% al 42%. La [cantidad](https://explorer.dcrdata.org/charts?chart=privacy-participation&zoom=jzuht6o0-kqspslc0&bin=day&axis=time&visibility=true-false) de mezcla diaria varió entre 150 y 300 mil DCR.

La presencia de Bison ha sido detectada en [LN](https://ln-map.jholdstock.uk/) como un nodo llamado "El Gran Bisonte ⚡🐂⚡".


## Ecosistema

Bienvenido al nuevo servidor [vspd](https://github.com/decred/vspd) de [stakey.com](https://vspd.stakey.com/) con una tarifa del 0.3%, la más baja del mercado al momento de escribir este artículo. Su servidor VSP antiguo se eliminó de la [lista](https://decred.org/vsp/), pero aún está operativo con 80 [tickets en vivo](https://stakey.com/stats) a partir del 7 de mayo.

Se observó el [VSP antiguo](https://vsp.dcr.farm/) de dcr.farm con una tarifa del 30%, posiblemente para desalentar nuevos registros. Preste atención a las tarifas para no comprar un ticket de tarifa alta por accidente. El servidor [vspd de dcr.farm](https://vsp.dcr.farm/) tiene una tarifa normal del 0.95%.

[Baap ATM](https://baap.app/) [tuiteó](https://twitter.com/baapapp/status/1376975012830326786) que sus cajeros automáticos y agentes ayudarán a comprar DCR por CAD en algunos lugares de Canadá.

Advertencia: los autores de la revista Decred no tienen idea de la confiabilidad de ninguno de los servicios mencionados anteriormente. Haz tu propia investigación antes de confiar tu información personal o tus activos.

Únete a nuestro chat de [#services](https://chat.decred.org/#/room/#services:decred.org) para seguir las actualizaciones del ecosistema de Decred.

## Alcance

Se ha configurado un nuevo proceso para transmitir anuncios de proyectos importantes en múltiples plataformas. Las "ANN" se emiten solo para actualizaciones importantes y tienen un tráfico mucho menor en comparación con el [Twitter](https://twitter.com/decredproject) de Decred. El canal [#dcr](https://chat.decred.org/#/room/#dcr:decred.org) de Matrix es la incorporación más reciente, los otros destinos son: [Twitter](https://twitter.com/decredproject), [Telegram](https://t.me/DCRann), Discord, [Reddit](https://www.reddit.com/r/decred/), [CoinGecko](https://www.coingecko.com/en/coins/decred), [Blockfolio](https://blockfolio.com/coin/DCR) y [Gab](https://gab.com/decredproject).


Los partidarios de Reddit han defendido a Decred en múltiples conversaciones relevantes sobre r/CryptoCurrency ([uno](https://www.reddit.com/r/CryptoCurrency/comments/m03ay0/what_are_your_favorite_top_100_coins_to_stake_and/), [dos](https://www.reddit.com/r/CryptoCurrency/comments/m2cza0/lets_talk_about_dexs_and_do_we_really_need_so_many/), [tres](https://www.reddit.com/r/CryptoCurrency/comments/m895oa/which_is_your_favorite_dao/), [cuatro](https://www.reddit.com/r/CryptoCurrency/comments/madahw/you_can_buy_5_coins_now_anf_only_access_them/), [cinco](https://www.reddit.com/r/CryptoCurrency/comments/mcqzk7/too_many_post_your_undervalued_coins_posts_here/), [seis](https://www.reddit.com/r/CryptoCurrency/comments/msifo2/one_crypto_for_the_rest_of_your_life/)). Gracias a todos por difundir la conciencia.


Logros de Monde PR para abril: 

- Creó / lanzó 2 historias para publicaciones financieras y criptográficas.
- Consiguió 2 entrevistas con los medios.
- Respondió a 1 solicitud de comentarios.

Cobertura de noticias asegurada por Monde PR:

- El anuncio de la tesorería de Decred fue cubierto por [Bankless Times](https://www.banklesstimes.com/2021/04/12/decred-makes-consensus-change-to-further-decentralize-128m-treasury/).
- Una entrevista con @lukebp sobre el podcast [Keyword: Crypto](https://www.keywordcrypto.com/luke-p-from-decred/).

## Eventos
Atendidos:

- 21 de abril - [Blockchain Land](https://blockchainland.talent-republic.tv/) - Internet. @adcade habló sobre “[Opiniones sobre las criptomonedas](https://blockchainland.talent-republic.tv/on-demand/que-opinar-sobre-las-criptomonedas/)” y el [futuro](https://blockchainland.talent-republic.tv/on-demand/blockchains-futuro-escalabilidad-u-oportunismo/) de las criptomonedas como parte de la participación de Decred en Blockchain Land de Talent Land. Los paneles se transmitieron en los [mundos virtuales](https://es.cointelegraph.com/news/first-massive-spanish-speaking-blockchain-event-created-by-decentraland-and-cryptovoxels) Decentraland y Cryptovoxels.

## Media

Artículos seleccionados:

- Decred realiza un cambio de consenso para descentralizar aún más la tesorería de $128M ([banklesstimes.com](https://www.banklesstimes.com/2021/04/12/decred-makes-consensus-change-to-further-decentralize-128m-treasury/)).
- ¿Qué es Decred y DCR? por Ivan en Tech ([ivanontech.com](https://academy.ivanontech.com/blog/what-is-decred-and-dcr)).
- Revisión del sector monetario del primer trimestre de 21 por Mira Christanto ([messari.io](https://messari.io/article/q1-21-currency-sector-review)): Messari [tuiteó](https://twitter.com/MessariCrypto/status/1381654632515174402) que DCR es el segundo mayor motor después de DOGE en el primer trimestre de 2021.

Videos:

- Entrevista a Luke Powell Decred in Depth (en vivo) por @elima_iii ([youtube](https://www.youtube.com/watch?v=J6IAjmwkki0)).
- Entrevista de Decred Society Decred in Depth (en vivo) @elima_iii ([youtube](https://www.youtube.com/watch?v=WOVUvzsp3Eo)).
- La plataforma de propuestas de Decred Politeia: la fuerza de toma de decisiones detrás del DAO Decred de ~ $125M por @Salirus ([youtube](https://www.youtube.com/watch?v=dfpUgwXBUmM)).
- La evolución del dinero - Decred fundamentals por @phoenixgreen ([youtube](https://www.youtube.com/watch?v=1qadfuFuqzs))
- Interoperabilidad para efectivo digital por @phoenixgreen ([youtube](https://www.youtube.com/watch?v=iBN0ZzlEKMA)).
- Análisis de precios de Decred - 27 de abril de 2021 por Josh Olszewicz de Brave New Coin ([youtube](https://www.youtube.com/watch?v=NfSp5IjPtAI)).

@karamble ha subido todos los videos del canal de YouTube Decred en [tube.decredcommunity.org](https://www.youtube.com/decredchannel). Está impulsado por [PeerTube](https://joinpeertube.org/), una alternativa liviana, autohospedada y de código abierto a YouTube que se puede conectar al [Fediverse](https://en.wikipedia.org/wiki/Fediverse). [Aquí](https://docs.joinpeertube.org/use-third-party-application) hay una lista de herramientas para usuarios habituales. Los administradores que ejecutan instancias de PeerTube pueden ayudar a que el contenido sea aún más resistente al configurar el [seguimiento y la redundancia](https://docs.joinpeertube.org/admin-following-instances).

Audio:
- Rough Consensus 18: Blues del mercado alcista - Checkmate, Permabull Nino y Mister Black ([libsyn](https://roughconsensus.libsyn.com/episode-18-bull-market-blues), [spotify](https://open.spotify.com/episode/0E7k86gme05YINpdBlVPqy)).
- Keyword: Crypto Podcast - Luke P. de Decred ([youtube](https://www.youtube.com/watch?v=pRJ1zJFVoFo), [keywordcrypto.com](https://www.keywordcrypto.com/luke-p-from-decred/)).

Traducciones:

- Análisis de Decred Blockchain - Parte 2 PoW wow - en [español](https://medium.com/decred-es/an%C3%A1lisis-de-la-blockchain-de-decred-pt-2-pow-wow-376aab0be23c) por @francov_
- Decred Journal de marzo de 2021 se [tradujo](https://xaur.github.io/decred-news/) al árabe (@arij, @ abdulrahman4), chino (@Dominic) y español (@francov_). ¡Gracias a todos!

Otro contenido no en inglés:

@Dominic habló con Mable Jiang en el episodio 20 de 51% Podcast titulado "Sobre el consenso híbrido y la sabiduría colectiva de Decred", presentado por Multicoin Capital ([apple](https://podcasts.apple.com/cn/podcast/51-with-mable-jiang-presented-by-multicoin-capital/id1540917284?l=en&i=1000515571194), [simplecast.com](https://51-with-mable-jiang-presented-by-multicoin-capital.simplecast.com/episodes/ep20-cn-dt-decred)).

## Discusiones de la comunidad

Noticias del sistema:

Un nuevo tipo de estafadores están enviando mensajes directos a las personas cuando se unen a #support. Tenga en cuenta que ningún administrador o desarrollador le enviará un mensaje de correo electrónico ni le pedirá dinero.

Post seleccionados de Reddit:

- [r/decred](https://www.reddit.com/r/decred/new/) ahora tiene los jueves de charlas de traders semanales y los lunes de muchas reflexiones para alojar contenido que de otro modo se eliminaría como conversaciones de precios duplicadas o fuera de tema.
- Una idea de marketing para ejecutar un [servicio de correo](https://www.reddit.com/r/decred/comments/n11zwu/decredmail_a_marketing_idea/) financiado por Decred.

Discusiones seleccionadas de Twitter:

- @lukebp aclara qué es un [DAO](https://twitter.com/lukebp_/status/1378381506947784706).
- @overthrowy compartió su [mazo de inversión Decred](https://twitter.com/overthrowy/status/1381097293122740225).

> Para las personas que creen que "el mercado" toma las mejores decisiones, Bitcoin puede ser la elección correcta. Durante cualquier cambio contencioso, la red puede dividirse en dos o más bifurcaciones que competirán (lucharán) por el apoyo financiero y social de los mineros, desarrolladores, inversores e intercambios de PoW.
> 
> Para las personas que creen en la colaboración, que aspiran a perseguir el bien común y que están dispuestas a alinearse detrás de la voluntad general del
> colectivo de votantes descentralizados, Decred puede ser la elección correcta.
> 
> Bitcoin y Decred son contratos sociales diferentes. Pueden coexistir. ([@overthrowy](https://twitter.com/overthrowy/status/1381104927108296707))

## Mercados
En abril, DCR cotizaba entre USD 169.50–243.70 / BTC 0.0031–0.0040. La tarifa diaria promedio fue de $198.60.

## Relevantes externos

La "moneda estable" de [Fei](https://www.coindesk.com/1b-fei-stablecoins-rocky-start-is-a-wake-up-call-for-defi-investors) se lanzó a principios de abril, pero desafió las expectativas al cotizar a un precio significativamente más bajo que el objetivo de $1. Esto dejó a muchos inversores en una posición en la que no podían salir de su posición de FEI sin sufrir grandes pérdidas, debido al comportamiento complejo e impredecible de los novedosos mecanismos de incentivos y quema. FEI finalmente [logró](https://www.coindesk.com/1b-stablecoin-fei-hits-price-target-for-first-time-a-month-after-launch) su objetivo de $1 después de aproximadamente 1 mes después del lanzamiento.

La comunidad de Yearn Finance ha estado discutiendo [YIP-61](https://gov.yearn.finance/t/yip-61-governance-2-0/10460/25) “Gobernanza 2.0”, que amplía el acuerdo de firma múltiple establecido temporalmente por YIP-41, y lo [aprueba](https://snapshot.org/#/ybaby.eth/proposal/QmSMyYeKrRpnA7Xn56o2NtbCUzxmhzCupL7LxMA1reXxq4) con un 99.97% de votos a favor. Esta propuesta también delega ciertos poderes a un conjunto de equipos contribuyentes de Yearn (“yTeams”), y “aclara” el papel de los titulares de YFI como principalmente sobre la delegación de poderes a estos equipos y la aprobación de YIP.

La subcomunidad NFT está financiando colectivamente su propia plataforma de nuevos medios ([NFTs WTF](https://nfts.wtf/)), a través del mecanismo de venta de 100 NFT que confieren derechos de voto en un DAO que respaldará la plataforma. Es interesante notar que en la [publicación](https://nfts.wtf/crowdfunding-the-worlds-first-d-zine/) que anunciaba la primera fase de la venta colectiva, en la que se vendieron 51 de los 100 tokens de control, solo 3 se vendieron a Venture Capitalists, y solo como individuos y no como representantes de sus organizaciones.

Coinbase comenzó a [vender](https://consent.yahoo.com/v2/collectConsent?sessionId=1_cc-session_01c56ae8-13dc-41cd-abfb-cf679535e168) acciones en el Nasdaq, a diferencia de una OPI, esto no implicó la creación de nuevas acciones, sino que los accionistas existentes llevaron algunas de las suyas al mercado.

Eso es todo por abril. Envía tus historias [aquí](https://github.com/xaur/decred-news/labels/next%20release) o simplemente comparte tus [comentarios](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback). ¡Siempre estamos buscando [colaboradores](https://github.com/xaur/decred-news/blob/docs/contributing.md) para mejorar La Revista Decred!

## Sobre esta edición

Este es el número 37 de Decred Journal. El índice de todos los números de publicación, copias y traducciones está disponible [aquí](https://xaur.github.io/decred-news/).

> La mayor parte de la información de terceros se transmite directamente desde la fuente después de una verificación mínima de cordura. Los autores del la revista
> Decred no tienen la capacidad de verificar todas las afirmaciones. Ten cuidado con las estafas y haz tu propia investigación.


Créditos (orden alfabético):

- redacción y edición: bee, degeri, l1ndseymm, richardred.
- revisiones y comentarios: chappjc, davecgh, jholdstock, lukebp.
- imagen de título: saender.
- financiación: Stakeholders de Decred.
