# How to Use Quetz GNU/Linux

A complete walkthrough — from downloading the ISO to installing Quetz GNU/Linux on your machine.

**Download:** https://archive.org/details/quetz-1.0-beta

---

## 1. Download the ISO

1. Open the download link above.
2. Download `quetz-1.0-beta.iso` (approximately 2.6 GB).
3. Also download the checksum files (`quetz.iso.sha256` and `quetz.iso.md5`) if available.

## 2. Verify the ISO (recommended)

Before writing the ISO to a USB drive, verify its integrity.

**On Linux / macOS:**

```bash
sha256sum quetz-1.0-beta.iso
# compare to the value shown on the Archive.org file listing
```

**On Windows (PowerShell):**

```powershell
Get-FileHash quetz-1.0-beta.iso -Algorithm SHA256
```

If the hash matches the one published on the download page, the file is intact.

## 3. Write the ISO to a USB drive

You need a USB flash drive of at least **4 GB**. All data on the drive will be erased.

**Recommended tools:**

- **Ventoy** (Windows / Linux) — copy the ISO directly, no flashing needed, and it supports multiple ISOs on one drive.
- **Rufus** (Windows) — select the ISO, choose GPT + UEFI or MBR + BIOS depending on your target firmware.
- **balenaEtcher** (Windows / macOS / Linux) — simplest cross-platform option.
- **`dd`** (Linux / macOS):

```bash
sudo dd if=quetz-1.0-beta.iso of=/dev/sdX bs=4M status=progress oflag=sync
```

Replace `/dev/sdX` with your USB device (use `lsblk` to identify it — **never use `/dev/sda` unless you are certain**).

## 4. Boot from the USB

1. Insert the USB drive.
2. Reboot your machine and open the firmware boot menu (usually **F12**, **F11**, or **Esc** — depends on the manufacturer).
3. Select the USB device. If both entries appear, choose **UEFI** for modern systems or **Legacy/BIOS** for older ones.
4. The Plymouth splash will appear, followed by the XFCE desktop.

**BIOS settings tip:** if the USB is not detected, ensure **Secure Boot is disabled** and **USB boot is enabled** in your firmware settings.

## 5. First boot — the live session

The live session boots to the XFCE desktop and **auto-logs in** as the user `quetz`. No password is required.

**Default state:**

- **Bottom panel (dock):** Terminal, File Manager, Web Browser, Application Finder
- **Menu:** click the top-left XFCE menu icon or use the Application Finder
- **Passwordless sudo:** `sudo` works without a password in the live session (this is required for the live OS to function; it does **not** apply to the installed system)

**The live session is fully offline-capable** — all developer runtimes, compilers, documentation, and the Quetz interpreter are pre-installed and do not require a network connection to work.

## 6. Included applications

**Developer tools:**
- `build-essential`, `cmake`, `make`, `pkg-config`, `gdb`, `git`, `git-lfs`, `shellcheck`

**CLI utilities:**
- `ripgrep` (`rg`), `fd-find` (`fdfind`), `fzf`, `bat` (`batcat`), `tree`, `ncdu`, `htop`, `jq`, `tmux`, `inxi`, `lshw`, `neofetch`, `vim`, `nano`

**Networking:**
- NetworkManager, `nmap`, `httpie` (`http`), `dig`, `whois`, `traceroute`, `mtr-tiny`, `curl`, `wget`, `openssh-client`

**Documents & media:**
- Evince, Atril, Zathura, Ristretto (images), Parole (video), Audacious (audio)

**Desktop:**
- Firefox ESR, Thunderbird, Mousepad, XFCE Screenshooter, XFCE Taskmanager, file-roller, xarchiver, Galculator

**Programming languages pre-installed:**
Python 3.11, Node.js 18, Go 1.19, Rust 1.63, Java 17 LTS, C/C++ (GCC 12), Ruby 3.1, PHP 8.2, Perl 5.36, Lua 5.4, and of course **Quetz**.

## 7. Using the Quetz programming language

Quetz is installed at `/opt/quetz` with a global wrapper at `/usr/local/bin/quetz`.

**Interactive REPL:**

```bash
quetz
```

You will see a `quetz>` prompt. Type Quetz code directly, press Enter to run.

**Run a script:**

```bash
quetz run program.qz
```

**Syntax check only (parse without executing):**

```bash
quetz check program.qz
```

**Version info:**

```bash
quetz --version
```

**Man page:**

```bash
man quetz
```

**Documentation:** `/usr/share/doc/quetz-language/`

**File associations:** Double-click any `.qz` file in Thunar to open it in an XFCE terminal running Quetz.

**Example — try this in the REPL:**

```quetz
fn make_counter(start = 0) {
    let count = start;
    return fn() {
        count += 1;
        return count;
    };
}

let counter = make_counter(0);
print(counter());
print(counter());
print(counter());
```

Expected output:

```
1
2
3
```

## 8. Installing Quetz GNU/Linux to disk

The Calamares installer is **not shown in the live menu** by default — this is intentional, to prevent accidental execution during a live session.

**To install:**

1. Open a terminal.
2. Run:

```bash
sudo calamares
```

3. Follow the graphical installer:
   - Choose your language and keyboard
   - **Choose your partitioning method carefully** — the default is "manual" (no automatic erase)
   - Create a user account — **minimum password length is 8 characters**
   - Confirm and install

The installation takes 10–20 minutes depending on disk speed.

**Post-install:** reboot, remove the USB drive, and boot from your disk. Your user account and settings are preserved.

## 9. Known issues and limitations

- **Single-maintainer project** — response times for non-critical issues may vary.
- **No automatic background updates** — the system will not update itself silently. Run `sudo apt update && sudo apt upgrade` manually when you want updates.
- **No Flatpak, Snap, or AppStream GUI** — software must be installed via `apt`, language package managers (`pip`, `cargo`, `go`, `npm`), or native binaries.
- **Calamares hidden by default** — run `sudo calamares` from a terminal to install.
- **No proprietary GPU drivers pre-installed** — open-source drivers are included; install proprietary NVIDIA drivers manually if needed.
- **Bootloader is editable** — this is intentional for recovery scenarios. Set a bootloader password in your firmware if you need to prevent local boot tampering.

## 10. Troubleshooting

**The USB does not appear in the boot menu:**
- Try a different USB port (use USB 2.0 if USB 3.0 does not work)
- Disable Secure Boot in firmware
- Recreate the USB with Ventoy instead of a raw flash

**The live session does not reach the desktop:**
- At the boot menu, edit the entry and add `nomodeset` to the kernel parameters
- Try the "failsafe" option if present

**No network in the live session:**
- The live system works without network. To connect, click the network icon in the system tray.
- For Ethernet, the connection is automatic. For Wi-Fi, select your network and enter the password.

**`sudo` asks for a password:**
- In the live session, `sudo` is passwordless for the `quetz` user.
- On the installed system, `sudo` requires your user password (set during install).

**Email links do nothing:**
- Thunderbird is installed and set as the default mail handler. If clicking a `mailto:` link does nothing, ensure Thunderbird is running and open Preferences → Advanced → System Integration → Enable "Always check if Thunderbird is the default client".

**Calamares fails to launch:**
- Ensure you are in a graphical session (XFCE desktop loaded)
- Run `sudo calamares -d` to see debug output

## 11. Getting help and contributing

**Bug reports, feature requests, and discussions:**

- GitHub: https://github.com/jalalkouaki

**When reporting a bug, include:**
- Hardware (CPU, GPU, RAM)
- Whether you were in live or installed mode
- Steps to reproduce
- Relevant log output (`dmesg`, `journalctl -xe`)

Pull requests are welcome — especially for build recipes, documentation, and Quetz interpreter improvements.

## 12. Verifying your download (optional advanced check)

Mount the ISO and inspect its contents:

```bash
sudo mount -o loop,ro quetz-1.0-beta.iso /mnt
ls /mnt
sudo umount /mnt
```

You should see `isolinux/`, `boot/`, `live/`, and other standard ISO 9660 directories.

---

**That's it. Enjoy Quetz GNU/Linux.**

If something in this guide is wrong, incomplete, or confusing, open an issue at https://github.com/jalalkouaki and it will be updated.
