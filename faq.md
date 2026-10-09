# ZeroKeyUSB — FAQ

**How is it different from a cloud password manager (1Password, Bitwarden…)?**
There is no server. The credential database lives only on the device in your pocket, and the device types the credentials itself. The trade-off is honest: cloud managers sync, share and hold unlimited entries; ZeroKeyUSB holds 61 and doesn't sync. In exchange, there is no account, no subscription, and nothing stops working if a company goes offline.

**Is it the same as a YubiKey?**
No, they do different jobs. A security key (FIDO2/U2F) proves your identity to sites that support that protocol. ZeroKeyUSB stores credentials and types them into any login form. Plenty of people carry both.

**How is it different from KeePass on a USB stick?**
With KeePass on a stick, the whole database is opened on the computer. With ZeroKeyUSB the computer never sees the database: it only receives the one credential you choose, typed as keystrokes. The PIN is entered on the device, not on the computer.

**Do I need to install anything?**
No. The computer sees a standard USB keyboard. Two optional browser tools exist: a manager page for bulk editing and backups, and a Chrome/Edge extension that focuses the login field. Both also run offline from a local file.

**What if I lose it, or it's stolen?**
Whoever has it needs the PIN. Every wrong PIN adds a waiting period that survives unplugging; after about ten wrong attempts each further guess costs about 43 minutes. Keep a backup and restore it onto a new device.

**What if I forget the PIN?**
There is no recovery and no backdoor, for anyone, including us. A factory reset erases the vault; your backup brings the credentials back.

**Can I back it up?**
Yes. Exporting requires physically holding a pad on the device. The browser manager can save an encrypted backup (AES-256-GCM); a plain CSV export is also available and should be encrypted straight away.

**Does it need internet?**
No, and it can't use it: there is no wireless hardware. 2FA codes only need the clock set once, over USB.

**Does it work on phones and tablets?**
Yes, on Android and iPadOS devices with USB-C, plus Windows, macOS and Linux. It works wherever a USB keyboard works, but check your specific device, since some restrict which USB accessories they accept.

**What if the company disappears?**
The device keeps working: it never contacts a server. Firmware, PCB files and browser tools are published under the MIT licence.

**Can the firmware be updated?**
Yes, but only with the device in your hands, and only with firmware signed by us. The bootloader rejects anything it cannot verify. There are no remote or automatic updates.

**Why $99?**
It is a small production run made in Spain, with a dedicated secure element, a resin-sealed enclosure and signed firmware. Because everything is open source, makers can also build their own from the published files.

**Is it waterproof?**
It is resistant to splashes, rain and dust thanks to the resin. It is not rated for submersion.
