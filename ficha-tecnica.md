# ZeroKeyUSB — Ficha técnica

Estas son las cifras oficiales. Si otra fuente dice algo distinto, vale esta ficha.

## Producto

| | |
|---|---|
| Tamaño / peso | 60 × 15 × 5 mm · 6 g |
| Capacidad | 61 credenciales |
| Cada credencial | Nombre del sitio, usuario, contraseña (hasta 32 caracteres cada uno) y secreto TOTP opcional |
| Conector | USB-C |
| Se presenta como | Teclado HID estándar + puerto serie CDC (para las herramientas opcionales del navegador) |
| Alimentación | Desde el puerto USB, unos 20 mA. Sin batería |
| Inalámbrico | Ninguno: sin Wi-Fi, Bluetooth ni NFC en la placa |
| Pantalla | OLED SSD1306, 128 × 32 |
| Entrada | 5 botones táctiles capacitivos dorados (el PIN se introduce aquí, nunca en el ordenador) |
| Carcasa | Sellada en resina, sin tornillos ni juntas. Resiste salpicaduras y polvo; no es sumergible |
| Distribuciones de teclado | EN-US, DA-DK, DE-DE, ES-ES, FR-FR, HU-HU, IT-IT, PT-PT, SV-SE |
| 2FA | TOTP de 6 dígitos, SHA-1 / SHA-256 / SHA-512, generado en el dispositivo |
| Compatibilidad | Windows, macOS, Linux, Android, iPadOS (modelos USB-C) |

## Hardware

| | |
|---|---|
| Microcontrolador | Microchip SAMD21E18A, ARM Cortex-M0+ a 48 MHz |
| Elemento seguro | Microchip ATECC608A (generador de números aleatorios + AES por hardware) |
| Memoria | EEPROM M24C64, 8 KB |

## Modelo de seguridad

- **PIN en el dispositivo.** Se teclea en los botones táctiles y se verifica en el propio dispositivo. Nunca viaja por USB.
- **Retardo contra fuerza bruta.** Cada PIN incorrecto añade una espera que se guarda en el dispositivo, así que desenchufarlo no la reinicia (hasta unos 43 minutos por intento). Los PIN incorrectos nunca borran las credenciales.
- **Cifrado.** AES-128 CBC. La clave de 128 bits se genera dentro del ATECC608A y nunca sale de él. La memoria solo contiene datos cifrados.
- **Firmware firmado.** El bootloader verifica una firma ECDSA P-256 antes de ejecutar cualquier firmware. Las actualizaciones requieren tener el dispositivo en la mano; no hay actualizaciones remotas.
- **Aprobación física para accesos masivos.** Exportar o importar todas las credenciales exige mantener pulsado un botón del dispositivo.
- **Evidencia de manipulación.** La electrónica está sellada en resina; llegar a ella implica destruir el dispositivo de forma visible.
- **Límites conocidos.** Quien destruya la carcasa y acceda al bus interno podría atacar el hash del PIN fuera del dispositivo; por eso importa la longitud del PIN. Las exportaciones CSV van en texto plano; el gestor del navegador también permite copias de seguridad cifradas con AES-256-GCM.

## Código abierto

Firmware, archivos de la PCB, modelos 3D de la carcasa y herramientas del navegador se publican bajo licencia MIT: https://github.com/Depbit-lab/Zerokey
Las unidades comerciales llevan un firmware firmado. El código está publicado para que cualquiera pueda revisarlo y auditarlo.

## Campaña y empresa

| | |
|---|---|
| Plataforma | Crowd Supply (respaldada por Mouser Electronics): https://www.crowdsupply.com/depbit/zerokeyusb |
| Lanzamiento | 22 de septiembre de 2026 |
| Estado | Más del 250 % del objetivo |
| Fin de la campaña | 5 de noviembre de 2026 |
| Precio | 99 $ (envío 8 $ EE. UU. / 18 $ internacional) |
| Entrega prevista | Abril de 2027 |
| Empresa | Depbit LLC |
| Fabricación | En España, con Reidite. Ya se ha fabricado y probado un primer lote de 50 unidades |
| Origen | Trabajo de fin de grado en la Universidad de Cádiz. Premio atrÉBT! TFG/TFM (XVI edición) |
