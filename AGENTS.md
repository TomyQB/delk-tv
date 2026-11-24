# Instalar DelK en una tele: instrucciones para agentes de código

Eres un agente de código (Claude Code, Codex, opencode u otro) y alguien te ha pedido instalar **DelK («Diversión en la Kikoneta»)**, un reproductor de listas IPTV, en su tele. Sigue este documento al pie de la letra.

**Qué es esto:** el repositorio solo contiene estas instrucciones. Los paquetes están en *Releases*:

| Fichero | Para | Dirección fija (siempre la última versión) |
|---|---|---|
| `DelK.apk` | Android TV, Google TV, Fire TV, móviles y tablets Android | https://github.com/TomyQB/delk-tv/releases/latest/download/DelK.apk |
| `DelK-samsung.zip` | Teles Samsung (Tizen) de 2022 o posteriores | https://github.com/TomyQB/delk-tv/releases/latest/download/DelK-samsung.zip |
| `SHA256SUMS` | Comprobar las dos descargas | https://github.com/TomyQB/delk-tv/releases/latest/download/SHA256SUMS |

## Reglas

1. **Habla con la persona en español**, con palabras sencillas: no tiene por qué saber de informática. Antes de cada paso que tenga que hacer con el mando, dile exactamente qué botones pulsar y espera a que te confirme.
2. **Las credenciales no son cosa tuya:**
   - El usuario, la contraseña y el servidor de la lista los escribe la persona en la tele, dentro de la app. No se los pidas, no los escribas en ficheros y no los pongas en comandos.
   - Lo mismo con la contraseña de su cuenta de Samsung y la del certificado: las escribe ella en las ventanas del programa.
3. **Solo instalas lo que dice este documento:**
   - de este repositorio, únicamente los ficheros de Releases;
   - fuera de aquí, solo las herramientas indicadas: Downloader, Android platform-tools o Tizen Studio.
   - Nada de tiendas IPTV de terceros, APKs de otras webs ni «hacks» del sistema de la tele.
4. **Comprueba siempre la huella SHA-256** de lo que descargues contra `SHA256SUMS` antes de instalarlo. Si no coincide, para y avisa.
5. **Avisa antes de lo que no se puede deshacer.** Pide confirmación antes de reiniciar la tele, desinstalar una versión anterior o cambiar ajustes del ordenador.
6. **Si algo falla dos veces seguidas, para:** explica a la persona lo que ves y propón la alternativa del documento, en vez de improvisar.

## Paso 1: averiguar qué tele y qué sistema tiene

Pregunta la marca y el modelo. Si no lo sabe, que lo busque en la etiqueta de detrás o en *Ajustes → Asistencia / Información*. Con eso:

| Marca / aparato | Sistema | ¿Se puede? | Sección |
|---|---|---|---|
| Fire TV Stick / Fire TV Cube / teles «Fire TV Edition» | Fire OS (Android) | Sí | [Android](#android-tv-google-tv-y-fire-tv) |
| Xiaomi (Mi TV, Xiaomi TV A / A Pro / S Pro / Q, Mi Box, Mi TV Stick) | Android TV / Google TV / Fire TV, según modelo | Sí | [Xiaomi](#xiaomi) y luego [Android](#android-tv-google-tv-y-fire-tv) |
| Chromecast con Google TV, Google TV Streamer, Sony, TCL, Philips, Hisense con Google TV, Nvidia Shield, cajas Android | Android TV / Google TV | Sí | [Android](#android-tv-google-tv-y-fire-tv) |
| Samsung de 2022 o posterior | Tizen 6.5 o superior | Sí, pero laborioso (hace falta un ordenador) | [Samsung](#samsung-tizen) |
| Samsung de 2021 o anterior | Tizen 6.0 o inferior | No | [Sin soporte](#teles-sin-soporte) |
| LG | webOS | No | [Sin soporte](#teles-sin-soporte) |
| Hisense / Toshiba con VIDAA, Roku, Apple TV, Philips Saphi, otras | — | No | [Sin soporte](#teles-sin-soporte) |
| Móvil o tablet Android | Android 5.1 o superior | Sí | [Móvil o tablet](#móvil-o-tablet-android) |
| iPhone / iPad | iOS | No | [Sin soporte](#teles-sin-soporte) |

- **Año de un Samsung:** en el código de modelo, la letra de año va justo después del número de serie (Q75**B**, QN90**C**, S90**D**) o al principio de la serie en las Crystal UHD (UE55**B**U8000, UE55**C**U7100).
  - Son de 2022 o posteriores: B = 2022, C = 2023, D = 2024, F = 2025.
  - No sirven: A = 2021, T = 2020, R = 2019, N = 2018.
- **Para distinguir el sistema** (Android TV, Google TV, Fire OS, VIDAA…), mira la pantalla de inicio o *Ajustes → Información*. Si dudas, pide una foto de esa pantalla.

## Xiaomi

Todas las teles y aparatos Xiaomi con apps son Android por dentro, así que se instala el mismo `DelK.apk`. Antes, averigua cuál de estas variantes es, para seguir los menús correctos:

| Cómo se ve la pantalla de inicio | Variante | Menús a seguir |
|---|---|---|
| Pone «Google TV» y recomienda pelis de varias apps | Google TV (Xiaomi TV A / A Pro / S Pro de 2022 en adelante) | Los de **Google TV** de la sección Android |
| Fila de apps de Android TV, a veces con la capa **PatchWall** de Xiaomi (botón propio en el mando) | Android TV (Mi TV 4S / 4A / P1 / Q1 / Q2, Mi Box, Mi TV Stick) | Los de **Android TV** de la sección Android. Si al pulsar Inicio sale PatchWall, los ajustes están en el engranaje de arriba a la derecha o con el botón ☰ del mando |
| Logo de Amazon / Fire TV | Fire TV (Xiaomi «Fire TV Edition») | Los de **Fire TV** de la sección Android |
| Menús solo en chino, sin Google Play ni tienda de Amazon | Modelo para China (MIUI TV / HyperOS) | [Modelo chino](#modelo-chino-sin-google-play) |

Lo propio de Xiaomi:
- **Opciones para desarrolladores:**
  - En Android TV: *Ajustes → Preferencias del dispositivo → Información → Compilación*, pulsar OK 7 veces.
  - En algunos modelos con PatchWall la entrada se llama «Versión de Android TV» o «Número de compilación».
- **Fuentes desconocidas:**
  - Ruta habitual: *Ajustes → Preferencias del dispositivo → Seguridad y restricciones → Fuentes desconocidas*.
  - En modelos antiguos con PatchWall puede ser un único interruptor general en vez de una lista por app. Actívalo para instalar y desactívalo al terminar.
- **El mando de Xiaomi no tiene botones de canal:** se cambia de canal con ▲ ▼ en pantalla completa. Si tiene teclado numérico, no hace falta.

### Modelo chino (sin Google Play)

No hay tienda donde buscar Downloader. Elige una de estas dos vías:
- **Por adb** (camino B de la sección Android):
  - La depuración está en *设置 (Ajustes) → 账号与安全 (Cuenta y seguridad) → ADB调试 (Depuración ADB)*.
  - En el mismo menú está *安装未知来源应用 (Instalar apps de origen desconocido)*: actívalo.
- **Con un pendrive** (si la persona no tiene ordenador a mano cerca de la tele):
  1. Copiar `DelK.apk` (comprobado con `SHA256SUMS`) a un pendrive en FAT32.
  2. Enchufarlo a la tele y abrir el gestor de archivos (*高清播放器* o *文件管理*).
  3. Elegir el APK e instalar. Hay que activar antes lo de origen desconocido.

La app se ve en español aunque la tele esté en chino.

## Android TV, Google TV y Fire TV

Hay dos caminos:
- **A, con la app Downloader:** no hace falta ordenador; la persona lo hace con el mando y tú la guías.
- **B, por adb desde el ordenador:** lo haces tú. El ordenador tiene que estar en la misma red (wifi o cable) que la tele.

Ofrece A por defecto, y B si la persona prefiere que lo hagas tú o si A falla.

### Activar las opciones de desarrollador (necesario para A y B)

- **Fire TV:**
  1. *Ajustes → Mi Fire TV → Acerca de*.
  2. Pulsar OK 7 veces sobre el nombre del aparato (p. ej. «Fire TV Stick 4K»), hasta que diga que ya es desarrollador.
  3. Aparece *Mi Fire TV → Opciones para desarrolladores*.
- **Google TV:**
  1. *Ajustes → Sistema → Información*.
  2. Pulsar OK 7 veces sobre «Compilación del SO de Android TV».
  3. Aparece *Ajustes → Sistema → Opciones para desarrolladores*.
- **Android TV (sin «Google»):**
  1. *Ajustes → Preferencias del dispositivo → Información*.
  2. Pulsar OK 7 veces sobre «Compilación».
  3. Aparece *Preferencias del dispositivo → Opciones para desarrolladores*.

### Camino A: con Downloader (sin ordenador)

1. **Instalar Downloader** (de AFTVnews, gratis): en Fire TV, desde la tienda de Amazon (buscar «Downloader»); en Android TV / Google TV, desde Google Play.
2. **Permitir que Downloader instale apps:**
   - **Fire TV:** *Mi Fire TV → Opciones para desarrolladores → Instalar aplicaciones desconocidas → Downloader: Activado*. En modelos antiguos: *Apps de origen desconocido: Activado*.
   - **Google TV:** *Ajustes → Aplicaciones → Seguridad y restricciones → Fuentes desconocidas → Downloader: activado*.
   - **Android TV:** *Ajustes → Preferencias del dispositivo → Seguridad y restricciones → Fuentes desconocidas → Downloader: activado*.
3. **Descargar e instalar:**
   1. Abrir Downloader. Si pide permiso para acceder a archivos, aceptarlo.
   2. En el cuadro de dirección, escribir exactamente `https://github.com/TomyQB/delk-tv/releases/latest/download/DelK.apk` y pulsar *Go*.
   3. Al terminar la descarga sale la pantalla de instalación: pulsar *Instalar* y luego *Abrir*.
   4. Downloader ofrecerá borrar el fichero descargado: aceptar, ya no hace falta.
4. Ir a [Primer uso](#primer-uso-lo-hace-la-persona). Después, [Al terminar en Android](#al-terminar-en-android).

### Camino B: por adb desde el ordenador

1. **Instalar adb** (Android platform-tools) si no está:
   - macOS: `brew install --cask android-platform-tools`
   - Windows: `winget install Google.PlatformTools`
   - Debian/Ubuntu: `sudo apt install adb`
   - Comprueba con `adb version`.
2. **Activar la depuración en la tele** (pídeselo a la persona):
   - **Fire TV:** *Mi Fire TV → Opciones para desarrolladores → Depuración ADB: Activado*.
   - **Android TV / Google TV:** *Opciones para desarrolladores → Depuración USB: activado*. En las teles también funciona por red.
3. **Saber la IP de la tele:**
   - Fire TV: *Mi Fire TV → Acerca de → Red*.
   - Android TV / Google TV: *Ajustes → Red e Internet →* la red conectada.
4. **Conectar:** `adb connect IP_TELE:5555`.
   - En la tele saldrá «¿Permitir depuración?». La persona marca «Permitir siempre desde este ordenador» y pulsa *Permitir*.
   - Comprueba con `adb devices`: debe salir `IP_TELE:5555 device`. Si sale `unauthorized`, falta aceptar ese aviso.
   - **Si `adb connect` se rechaza** (pasa en Google TV con Android 11 o superior):
     1. En la tele: *Opciones para desarrolladores → Depuración inalámbrica → activar → Vincular dispositivo con un código*.
     2. En el ordenador: `adb pair IP:PUERTO_DE_VINCULACIÓN CÓDIGO`.
     3. Después: `adb connect IP:PUERTO` (el puerto que muestra la pantalla principal de Depuración inalámbrica).
5. **Descargar y comprobar** (en una carpeta temporal):
   ```sh
   curl -fLO https://github.com/TomyQB/delk-tv/releases/latest/download/DelK.apk
   curl -fLO https://github.com/TomyQB/delk-tv/releases/latest/download/SHA256SUMS
   grep DelK.apk SHA256SUMS | shasum -a 256 -c -     # Windows: certutil -hashfile DelK.apk SHA256 y compara a mano
   ```
6. **Instalar y abrir:**
   ```sh
   adb -s IP_TELE:5555 install -r DelK.apk
   adb -s IP_TELE:5555 shell am start -n dev.tomyqb.delk/.MainActivity
   ```
   - **`INSTALL_FAILED_UPDATE_INCOMPATIBLE`:** hay una copia firmada por otra persona. Pide permiso para desinstalarla (se pierden sus favoritos y su progreso) con `adb uninstall dev.tomyqb.delk` y repite la instalación.
   - **`INSTALL_FAILED_OLDER_SDK`:** el aparato tiene Android anterior a 5.1 y no sirve. Ver [Sin soporte](#teles-sin-soporte).
7. Ir a [Primer uso](#primer-uso-lo-hace-la-persona). Después, [Al terminar en Android](#al-terminar-en-android).

### Al terminar en Android

Por seguridad, recomienda a la persona:
- desactivar *Depuración ADB* / *Depuración USB* / *Depuración inalámbrica*;
- quitar el permiso de *Fuentes desconocidas* a Downloader.

La app sigue funcionando igual. Para actualizar más adelante basta con volver a activarlo y repetir el camino elegido: se instala encima y no se pierde nada.

## Móvil o tablet Android

1. Abrir en el navegador del móvil `https://github.com/TomyQB/delk-tv/releases/latest/download/DelK.apk`.
2. Abrir el fichero descargado. Si avisa de que el navegador no puede instalar apps, entrar en el ajuste que ofrece y permitirlo para ese navegador.
3. Pulsar *Instalar*. Luego quitar ese permiso al navegador.

La app está pensada para la tele: en el móvil va en horizontal y se maneja tocando y deslizando.

## Samsung (Tizen)

Solo para teles Samsung de 2022 o posteriores ([cómo saberlo](#paso-1-averiguar-qué-tele-y-qué-sistema-tiene)).

Samsung no deja instalar apps de fuera de su tienda salvo en **modo desarrollador**, y con una condición: cada app tiene que ir firmada con un certificado que incluye el identificador (DUID) de **esa tele concreta**. Por eso `DelK-samsung.zip` va sin firmar y lo firmas tú con el certificado de la persona.

**Avísale antes de empezar:**
- tarda entre 30 y 60 minutos;
- necesita un ordenador (Windows, macOS o Linux) en la misma red que la tele;
- necesita una cuenta de Samsung, que puede crear gratis en account.samsung.com;
- hay que descargar unos 3 GB.

Si no le compensa, la alternativa es un Fire TV Stick o un Google TV enchufado a la tele (unos 30–70 €), siguiendo la sección de Android.

### 1. Instalar Tizen Studio en el ordenador

1. **Descargar** el «Tizen Studio with IDE installer» de su sistema desde https://developer.tizen.org/development/tizen-studio/download e instalarlo en la carpeta por defecto: `~/tizen-studio` en macOS y Linux, `C:\tizen-studio` en Windows.
2. **macOS con Apple Silicon (M1–M4):** varias herramientas son de Intel. Hay que instalar Rosetta antes: `softwareupdate --install-rosetta --agree-to-license`.
3. **Instalar los paquetes de Samsung** con el gestor de paquetes (en Windows, `package-manager-cli.exe`):
   ```sh
   ~/tizen-studio/package-manager/package-manager-cli.bin install --accept-license cert-add-on Certificate-Manager TV-SAMSUNG-Extension-Tools TV-SAMSUNG-Public-WebAppDevelopment
   ```
   - Si algún nombre no existe, lista los disponibles con `show-pkgs` y elige los equivalentes: *Samsung Certificate Extension*, *Certificate Manager*, *TV Extensions Tools* y *TV Web app. development*.
   - Si el gestor se queja de Java en macOS o Linux, usa el JDK que trae Tizen Studio. Por ejemplo: `ln -s ~/tizen-studio/jdk ~/.package-manager/jdk`.
4. **Herramientas que usarás** (en Windows, `.exe` y `.bat` bajo `C:\tizen-studio\`):
   - `~/tizen-studio/tools/sdb`
   - `~/tizen-studio/tools/ide/bin/tizen`

### 2. Poner la tele en modo desarrollador (lo hace la persona)

1. Saber la IP del ordenador:
   - macOS: `ipconfig getifaddr en0` (o `en1`);
   - Windows: `ipconfig`;
   - Linux: `hostname -I`.
2. En la tele, abrir **Aplicaciones**. Con el mando, teclear `1 2 3 4 5` (con los números del mando, o del teclado de la pantalla si el mando no tiene).
3. Poner **Modo desarrollador: Activado**, escribir la IP del ordenador en **IP del PC host** y aceptar.
4. **Reiniciar la tele** de verdad: mantener pulsado el botón de encendido del mando hasta que se apague y vuelva a encenderse, o desenchufarla 30 segundos.
5. Saber la IP de la tele: *Ajustes → General → Red → Estado de red → Ajustes de IP*.

### 3. Conectar el ordenador con la tele

```sh
~/tizen-studio/tools/sdb connect IP_TELE
~/tizen-studio/tools/sdb devices        # debe salir: IP_TELE:26101  device  <modelo>
```

Si no conecta, revisa estas tres cosas: la IP del PC host escrita en la tele, que la tele se haya reiniciado tras activar el modo desarrollador, y que ambos aparatos estén en la misma red.

### 4. Crear el certificado de esa tele (lo hace la persona, tú la guías)

Con la tele conectada por `sdb`, abrir **Certificate Manager**:
- macOS: `open ~/tizen-studio/tools/certificate-manager/certificate-manager.app`
- Windows: `C:\tizen-studio\tools\certificate-manager\certificate-manager.exe`
- Linux: `~/tizen-studio/tools/certificate-manager/certificate-manager`

Pasos en la ventana:
1. Pulsar **+** → elegir **Samsung** → dispositivo **TV** → nombre del perfil: `delk`.
2. **Author certificate:**
   1. *Create a new author certificate*.
   2. Un nombre cualquiera y una contraseña que elija la persona. Que la apunte: hará falta para futuras actualizaciones.
   3. Iniciar sesión con su cuenta de Samsung en la ventana del navegador que se abre.
3. **Distributor certificate:**
   1. *Create a new distributor certificate*, privilegio **Public**.
   2. En la lista de DUID debe aparecer ya el de la tele conectada. Si no aparece, la tele no está conectada: vuelve al apartado 3.
4. Terminar y dejar el perfil `delk` como activo.

### 5. Descargar, comprobar, firmar e instalar

```sh
mkdir -p ~/delk-samsung && cd ~/delk-samsung
curl -fLO https://github.com/TomyQB/delk-tv/releases/latest/download/DelK-samsung.zip
curl -fLO https://github.com/TomyQB/delk-tv/releases/latest/download/SHA256SUMS
grep DelK-samsung.zip SHA256SUMS | shasum -a 256 -c -   # Windows: certutil -hashfile DelK-samsung.zip SHA256
rm -rf DelK-samsung && unzip -q DelK-samsung.zip
~/tizen-studio/tools/ide/bin/tizen package -t wgt -s delk -- DelK-samsung
WGT=$(ls DelK-samsung/*.wgt)
~/tizen-studio/tools/ide/bin/tizen install -s IP_TELE:26101 -n "$(basename "$WGT")" -- DelK-samsung
~/tizen-studio/tools/ide/bin/tizen run -s IP_TELE:26101 -p TmQbDelK01.DelK
```

- **El `.wgt` se llama «Diversión en la Kikoneta.wgt»** (el nombre de la app). Respeta las comillas por el espacio y la tilde.
- **Si `tizen package` pide la contraseña del certificado,** que la escriba la persona.
- **Errores de certificado al instalar** (por ejemplo, `Check certificate error`):
  - Si el certificado se creó sin la tele conectada, el DUID no coincide: créalo de nuevo con la tele conectada.
  - Si hay una versión firmada por otra persona, pide permiso y desinstálala: `tizen uninstall -s IP_TELE:26101 -p TmQbDelK01.DelK`.

La app queda en *Aplicaciones* como «Diversión en la Kikoneta». Para actualizar más adelante:
- repite el apartado 3 y el 5, con el mismo perfil `delk`;
- si se cambia de tele, hace falta un certificado nuevo (apartado 4).

## Teles sin soporte

LG (webOS), Hisense/Toshiba con VIDAA, Roku, Apple TV, Samsung de 2021 o anteriores, iPhone/iPad y aparatos con Android anterior a 5.1 no pueden instalar esta app. No intentes rodeos: ni tiendas alternativas, ni cambios de DNS, ni «jailbreaks».

La solución es enchufar a la tele por HDMI un **Fire TV Stick** o un **Google TV** (Chromecast con Google TV / Google TV Streamer) y seguir la sección de Android. Explícaselo así a la persona.

## Primer uso (lo hace la persona)

Al abrir la app por primera vez pide tres datos. Te los pasa por privado quien te dio el enlace de este repositorio:
- **Usuario** y **Contraseña** de la lista.
- **Servidor:**
  - Basta con escribirlo tal cual, p. ej. `servidor.com`. No hace falta `http://` ni el `:80` del final; la app lo entiende igual con o sin ellos.
  - Solo hay que añadir el puerto si es otro distinto, p. ej. `servidor.com:8080`.

Escribe con el teclado de la pantalla y pulsa **Entrar**. Si los datos son correctos, empieza el directo. Si no, la app dice qué falla: usuario o contraseña incorrectos, cuenta caducada o servidor que no responde.

### Cómo se maneja

| Mando | Qué hace |
|---|---|
| OK | Abre la guía de canales / elige |
| ▲ ▼ o CH+ / CH− | Cambia de canal (en pantalla completa) |
| ◀ ▶ | Cambia de «conexión» del mismo canal (si uno se para, prueba otra) |
| Atrás | Vuelve |
| Mantener OK sobre un canal | Lo añade a Favoritos |

El menú de la izquierda tiene Buscar, Directo, Películas, Series y Ajustes. En *Ajustes → Cuenta* se cambian los datos.

La cuenta permite pocas reproducciones a la vez (normalmente 2). Si se ven en más sitios, la app avisa antes de echar a nadie.
