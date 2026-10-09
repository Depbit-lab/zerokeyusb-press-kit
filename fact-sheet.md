# ZeroKeyUSB — Fact sheet

These are the official numbers. If another source disagrees, this sheet is correct.

## Product

| | |
|---|---|
| Size / weight | 60 × 15 × 5 mm · 6 g |
| Capacity | 61 credentials |
| Each credential | Site name, username, password (up to 32 characters each) and optional TOTP secret |
| Connector | USB-C |
| Shows up as | Standard HID keyboard + CDC serial port (for the optional browser tools) |
| Power | From the USB port, about 20 mA. No battery |
| Wireless | None: no Wi-Fi, Bluetooth or NFC hardware on the board |
| Display | SSD1306 OLED, 128 × 32 |
| Input | 5 gold-plated capacitive touch pads (the PIN is entered here, never on the computer) |
| Enclosure | Resin-encapsulated, no screws or seams. Splash and dust resistant, not rated for submersion |
| Keyboard layouts | EN-US, DA-DK, DE-DE, ES-ES, FR-FR, HU-HU, IT-IT, PT-PT, SV-SE |
| 2FA | TOTP, 6 digits, SHA-1 / SHA-256 / SHA-512, generated on the device |
| Compatibility | Windows, macOS, Linux, Android, iPadOS (USB-C models) |

## Hardware

| | |
|---|---|
| Microcontroller | Microchip SAMD21E18A, ARM Cortex-M0+ at 48 MHz |
| Secure element | Microchip ATECC608A (true random number generator + hardware AES) |
| Storage | M24C64 EEPROM, 8 KB |

## Security model

- **PIN on the device.** Entered on the touch pads and verified on the device. It never travels over USB.
- **Brute-force delay.** Each wrong PIN adds a waiting period stored on the device, so unplugging it doesn't reset it (up to about 43 minutes per attempt). Wrong PINs never erase the vault.
- **Encryption.** AES-128 CBC. The 128-bit key is generated inside the ATECC608A and never leaves it. The memory chip only holds ciphertext.
- **Signed firmware.** The bootloader verifies an ECDSA P-256 signature before running any firmware. Updates require physical access; there are no over-the-air updates.
- **Physical approval for bulk access.** Exporting or importing the whole vault requires holding a pad on the device.
- **Tamper evidence.** The electronics are sealed in resin; reaching them means visibly destroying the device.
- **Known limits.** An attacker who destroys the case and reaches the internal bus could attack the PIN hash offline, which is why PIN length matters. CSV exports are plaintext; the browser manager can also make AES-256-GCM encrypted backups.

## Open source

Firmware, PCB files, 3D case files and browser tools are published under the MIT licence: https://github.com/Depbit-lab/Zerokey
Retail units run a signed build. The source is there to be inspected and audited.

## Campaign and company

| | |
|---|---|
| Platform | Crowd Supply (backed by Mouser Electronics): https://www.crowdsupply.com/depbit/zerokeyusb |
| Launch | September 22, 2026 |
| Status | Over 250 % of funding goal |
| Campaign ends | November 5, 2026 |
| Price | $99 (shipping $8 US / $18 international) |
| Estimated delivery | April 2027 |
| Company | Depbit LLC |
| Manufacturing | In Spain, with Reidite. A first batch of 50 production units has already been built and tested |
| Origin | Undergraduate thesis at the University of Cádiz, Spain. Winner of the atrÉBT! TFG/TFM award (16th edition) |
