# Revista Decred Abril 2021

![portada]()

Destacados de Abril

- La sexta votación por consenso de Decred ha sido aprobada por unanimidad y con una alta participación de votantes.
- Politeia v1.0 ya está disponible con una infraestructura más escalable y preparada para el futuro.
- Se está votando la primera propuesta de Politeia para formalizar la hoja de ruta de desarrollo y el presupuesto.
- DCRDEX se dirige hacia la actualización v0.2 con varias mejoras de backend y UX, así como las bases para futuras funciones interesantes.
- La integración inicial de DCRDEX se ha fusionado en Decrediton.

Contenido:
- Desarrollo
- Comunidad
- Gobernanza
- Red
- Ecosistema
- Alcanse
- Eventos
- Media
- Discusiones de la comunidad
- Mercados
- Relevantes externos
- Sobre esta edición

## Desarrollo

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
