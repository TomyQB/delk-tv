# Diversión en la Kikoneta (DelK)

Reproductor de listas IPTV para la tele: directo con guía, películas y series.

## Instalarlo en tu tele

Lo más fácil es pedírselo a un agente de código, como Claude Code, Codex u opencode. Ábrelo en tu ordenador y escríbele:

> Lee https://github.com/TomyQB/delk-tv e instálame DelK en mi tele. Mi tele es [marca y modelo].

Las instrucciones exactas para el agente están en [AGENTS.md](AGENTS.md). Te irá diciendo qué tienes que pulsar con el mando.

### Qué teles valen

| Tele o aparato | ¿Funciona? |
|---|---|
| Fire TV Stick / Fire TV, Android TV, Google TV (Sony, TCL, Philips, Chromecast…) | Sí. Se instala en unos minutos, incluso sin ordenador |
| Xiaomi (Mi TV, Xiaomi TV A / S Pro, Mi Box, Mi TV Stick), también los modelos chinos | Sí |
| Samsung de 2022 o más nueva | Sí, pero hace falta un ordenador y una cuenta de Samsung (30–60 min) |
| LG de 2022 o más nueva | Sí, con un ordenador y una cuenta gratuita de LG. El modo desarrollador se renueva cada ~50 días con un botón |
| Móvil o tablet Android | Sí |
| LG o Samsung anteriores a 2022, Hisense/Toshiba con VIDAA, Apple TV, iPhone | No. Con un Fire TV Stick o un Google TV enchufado a la tele, sí |

### Sin agente, en Fire TV / Android TV / Google TV

1. Instala la app **Downloader** desde la tienda de la tele.
2. Activa las opciones de desarrollador y permite que Downloader instale apps. Los pasos exactos para cada sistema están en [AGENTS.md](AGENTS.md#android-tv-google-tv-y-fire-tv).
3. En Downloader, escribe esta dirección y pulsa *Go*:
   `https://github.com/TomyQB/delk-tv/releases/latest/download/DelK.apk`
4. Instala y abre.

## Al abrirla

Pide **usuario, contraseña y servidor**. Te los pasa por privado quien te dio este enlace. El servidor se escribe tal cual (`servidor.com`), sin `http://` ni `:80`.

## Versiones

Cada versión está en [Releases](https://github.com/TomyQB/delk-tv/releases). Para actualizar, se instala la nueva encima y no se pierde nada.
