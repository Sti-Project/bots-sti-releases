# BOTS STI — Releases

Repositorio publico de **distribucion** del proyecto **BOTS STI**: la app de escritorio que centraliza los bots de automatizacion de **Southern Travel International** (TRAMS Back Office + Google Sheets + Outlook).

Aca **solo viven los instaladores `.exe`**. El codigo fuente esta en el repo privado [`Sti-Project/bots-sti`](https://github.com/Sti-Project/bots-sti) y no se publica.

---

## Bajar la ultima version

[![Latest release](https://img.shields.io/github/v/release/Sti-Project/bots-sti-releases?label=Ultima%20version&color=0066b2)](https://github.com/Sti-Project/bots-sti-releases/releases/latest)

[**Bajar BOTS-STI-Setup-vX.Y.Z.exe**](https://github.com/Sti-Project/bots-sti-releases/releases/latest)

Doble click al `.exe` -> wizard en espanol -> instala en `C:\BOTS STI\` y crea un acceso directo en el escritorio. Pide elevacion de admin.

> **Nota**: la primera vez hay que copiar a mano los archivos `credentials.json` de cada bot a sus carpetas. Los enviaron por canal interno (no se distribuyen en el `.exe` por seguridad).

---

## Que trae la app

Una sola ventana con menu lateral. Cada bot vive como un panel propio con boton de iniciar/detener, log en vivo y KPIs (OK/ERROR/total).

| Bot | Para que sirve |
|---|---|
| **TXT LAN** | Genera TXTs IUR Sabre con invoice unico y los carga a TRAMS via Interface Download/Process. |
| **Interface** | Ciclo diario de download + process para los 6 sistemas Sabre/Amadeus, mas envio de PDF por mail. |
| **Cierre Tarjetas** | Cierra Payment Made en TRAMS para vouchers de hotel pagados con tarjeta corporativa. |
| **Invoices Open Lan** | Cambia el "Invoice Group" de invoices LAN ya cargadas, en batch desde planilla. |
| **Carga Supplier Aereos** | Submit to Supplier en batch para invoices de aerolinea. |
| **Crear Hoteles** | Da de alta vendor profiles de hoteles nuevos en TRAMS desde planilla. |

Detalles tecnicos completos: [README del repo privado](https://github.com/Sti-Project/bots-sti#readme) (acceso restringido al equipo STI).

---

## Autoactualizacion

A partir de la **v1.0.10** la app se actualiza sola:

1. Al arrancar (en background) chequea si hay version nueva en este repo.
2. Si la hay, muestra un dialog: **"Hay una nueva version disponible (vX.Y.Z). Actualizar ahora?"**.
3. Si aceptas: descarga el `.exe`, cierra la app y lanza el installer en silencio. Inno Setup pisa los archivos sin tocar tus credenciales.
4. Al terminar, abre la version nueva.

Tambien hay un boton **"Buscar actualizaciones"** en el header de la app para forzar el chequeo manual.

> **Si tenes una version anterior a v1.0.10**, instala manualmente la ultima desde [Releases](https://github.com/Sti-Project/bots-sti-releases/releases). Despues de eso, los upgrades son self-service.

---

## Compatibilidad

- **OS**: Windows 10 / 11 (64 bits).
- **Resolucion recomendada**: 1920x1080. El bot Interface usa coordenadas absolutas y requiere TRAMS maximizado en esa resolucion.
- **TRAMS Back Office** y **Outlook** instalados (no los bundlea la app).

---

## Como se publican estas releases

El workflow CI del repo privado, cada vez que mergea a `main`:

1. Compila la GUI con PyInstaller + el instalador con Inno Setup.
2. Crea la release **en el repo privado** (con tag `vX.Y.Z`).
3. Crea una release identica **en este repo publico** y le adjunta el `BOTS-STI-Setup-vX.Y.Z.exe`.

El codigo fuente queda cerrado, los binarios publicos.

---

## Soporte

Para reportar bugs, pedir features o solicitar credenciales nuevas: contactar al equipo STI internamente. El issue tracker publico esta deshabilitado a proposito — no es para reportes externos.
