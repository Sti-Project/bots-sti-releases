# BOTS STI — Releases

Repositorio publico **solo de distribucion** del proyecto BOTS STI. Contiene unicamente los instaladores `.exe` adjuntos a cada release.

El **codigo fuente vive en el repo privado** [`Sti-Project/bots-sti`](https://github.com/Sti-Project/bots-sti) y no se publica aca.

## Para que sirve este repo

La app BOTS STI tiene un sistema de **autoactualizacion** que consulta este repo para detectar nuevas versiones. Al ser publico, los clientes instalados en distintos remotos pueden chequear y bajar updates sin necesidad de un PAT ni de acceder al repo privado.

## Como obtener la app

Bajar el ultimo `BOTS-STI-Setup-vX.Y.Z.exe` desde la pagina de [Releases](https://github.com/Sti-Project/bots-sti-releases/releases) y ejecutarlo. El instalador pide elevacion de admin y deja un acceso directo en el escritorio.

> **Importante**: la primera vez hay que copiar a mano los `credentials.json` de cada bot a su carpeta. Los archivos de credenciales **no** se distribuyen en el instalador por seguridad.

## Como se publican estas releases

El workflow de CI del repo privado, cada vez que mergea a `main`:

1. Compila la app + el instalador con Inno Setup.
2. Crea la release **en el repo privado** (con tag `vX.Y.Z`).
3. Crea una release identica **en este repo publico** y le adjunta el `BOTS-STI-Setup-vX.Y.Z.exe`.

De esta forma el codigo fuente queda cerrado pero los binarios estan disponibles para los clientes y el autoupdater.

## Soporte

Para reportar bugs o pedir features, contactar al equipo STI internamente. El issue tracker publico esta deshabilitado.
