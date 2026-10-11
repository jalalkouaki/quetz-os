# Quetz GNU/Linux ![Beta](https://img.shields.io/badge/status-beta-orange) ![Base](https://img.shields.io/badge/base-Debian%2012%20Bookworm-red) ![Architecture](https://img.shields.io/badge/arch-amd64-blue) ![License](https://img.shields.io/badge/license-MIT-green)

> A lightweight, developer-focused Debian 12 derivative featuring out-of-the-box multi-language runtimes and native integration with the Quetz programming language.

Quetz GNU/Linux is an independent desktop operating system built on Debian 12 (Bookworm) using Debian's native `live-build` tooling. Designed as a clean workstation for developers and software tinkerers, it couples a responsive, dark-themed XFCE desktop with pre-configured developer toolchains, essential command-line utilities, and an offline-first installation experience. Most notably, the system serves as the reference platform for **Quetz**, a pure-Python multi-paradigm interpreted programming language.

---

> [!WARNING]
> **Beta Disclaimer & Project Status**
>
> * **Active Work in Progress:** Quetz GNU/Linux is currently in **1.0-beta**. Features, default configurations, and included software packages may change, break, or be removed without prior notice.
> * **Early-Access Release:** The first public image of Quetz GNU/Linux 1.0-beta is available on Archive.org. It is an early-access build without a formal support lifecycle.
> * **Audience:** This release is intended strictly for developers, code reviewers, and Linux enthusiasts interested in testing the environment and language integration. It is **not recommended for mission-critical or daily production use**.
> * **Support Model:** This distribution is maintained solely by a single developer as an independent personal and professional portfolio project. No commercial support, SLA, or formal warranty is provided. Community feedback and bug reports are warmly welcome.


---

## ⚡ Features

* **Debian 12 (Bookworm) Rock-Solid Foundation:** Inherits Debian's stability, security updates, and predictable package management, powered by the long-term support Linux 6.1 LTS kernel.
* **Native Quetz Programming Language Support:** Full system-level integration for the Quetz programming language, including interactive REPL support, file associations for `.qz` scripts, syntax checking, documentation, and a man page.
* **Pre-Configured Polyglot Runtimes:** Ten industry-standard programming languages (Python, Node.js, Go, Rust, Java, C/C++, Ruby, PHP, Perl, Lua) ready for development right out of the box with zero setup steps.
* **Curated Modern CLI Suite:** Ships modern, fast command-line utilities including `ripgrep`, `fd-find`, `fzf`, `bat`, `jq`, `tmux`, and `htop` alongside classical Unix diagnostics.
* **Polished Dark Aesthetic:** Consistent dark mode user interface powered by XFCE 4.18, styled with Arc-Dark window borders/controls and Papirus-Dark icons.
* **Custom Boot & Identity Experience:** Boot smoothly with a custom Plymouth splash theme featuring a bespoke logo and spinner on an `#1a1a2e` background, backed by ISOLINUX (BIOS) and GRUB 2.06 (UEFI).
* **Calamares Graphical Installer:** Ships with an integrated, branded Calamares installer for permanent deployment to local storage.
* **100% Offline Capable:** The entire live system, language compilers, interpreter runtimes, and local documentation operate without requiring an active network connection.
* **Minimalist Bloat-Free Environment:** Deliberately excludes heavyweight office suites, complex background daemons, games, and auxiliary package layers (Snap/Flatpak) to keep the footprint light and fast.

---

## 📦 Included Software

Quetz GNU/Linux ships a carefully selected suite of packages balancing developer power and desktop agility.

### Programming Languages & Runtimes

| Language | Version / Implementation | Package Provider | Invocation Command |
| :--- | :--- | :--- | :--- |
| **Quetz** | `v0.2.0` (Flagship Interpreted Language) | Native (`/opt/quetz`) | `quetz` |
| **Python** | `3.11.2` (Python 3.11 LTS) | `python3` / `python3.11` | `python3` |
| **Node.js** | `18.20.4` (LTS Iron) | `nodejs` | `node` |
| **Go** | `1.19.8` | `golang-go` / `golang-1.19-go` | `go` |
| **Rust** | `1.63.0` | `rustc` | `rustc` |
| **Java** | OpenJDK 17 LTS (`17.0.20.1`) | `default-jdk` / `openjdk-17-jdk` | `java`, `javac` |
| **C / C++** | `12.2.0` (GCC 12) | `gcc`, `g++`, `build-essential` | `gcc`, `g++` |
| **Ruby** | `3.1.2` | `ruby`, `ruby3.1` | `ruby` |
| **PHP** | `8.2.34` (PHP CLI) | `php-cli`, `php8.2-cli` | `php` |
| **Perl** | `5.36.0` | `perl`, `perl-base` | `perl` |
| **Lua** | `5.4.4` | `lua5.4` | `lua5.4` |

### Core Applications & Tooling

| Category | Included Applications |
| :--- | :--- |
| **Development & Build Tools** | `build-essential`, `cmake`, `make`, `pkg-config`, `gdb`, `git`, `git-lfs`, `shellcheck` |
| **CLI & Terminal Utilities** | `ripgrep` (`rg`), `fd-find` (`fdfind`), `fzf`, `bat` (`batcat`), `tree`, `ncdu`, `htop`, `jq`, `tmux`, `inxi`, `lshw`, `neofetch`, `vim`, `nano` |
| **Networking & Diagnostics** | `NetworkManager`, `nmap`, `httpie` (`http`), `dnsutils` (`dig`), `whois`, `traceroute`, `mtr-tiny`, `curl`, `wget`, `openssh-client` |
| **Document & PDF Readers** | `Evince`, `Atril`, `Zathura` (with `zathura-pdf-poppler`), `mupdf-tools`, `poppler-utils` |
| **Media Applications** | `Ristretto` (image viewer), `Parole` (media player), `Audacious` (audio player) |
| **Desktop Utilities** | `Galculator`, `Mousepad`, `XFCE Screenshooter`, `XFCE Taskmanager`, `file-roller`, `xarchiver`, `gnome-disk-utility`, `zenity` |
| **Web Browser** | `Firefox ESR` (Extended Support Release) |
| **Desktop Environment** | `XFCE 4.18` (Arc-Dark GTK/WM theme, Papirus-Dark icon theme, LightDM display manager) |

### Intentionally Omitted by Design

To preserve system lightness, resource predictability, and focus on software development, Quetz GNU/Linux deliberately omits:

* **Office Suites:** LibreOffice, OpenOffice *(handled by lightweight document readers)*
* **Heavy Media & Creativity Tools:** VLC, GIMP, Inkscape, Blender
* **Gaming & Compatibility Layers:** Steam, Lutris, Wine
* **Alternative Packaging Frameworks:** Flatpak, Snap *(keeps native APT cleanliness)*
* **Heavyweight Email & Browsers:** Thunderbird, Chromium
* **Heavy Editors:** Emacs, Neovim *(users may install their personal preferred IDEs via APT or tarballs)*

---

## 🦜 The Quetz Programming Language

The flagship feature of this distribution is **Quetz**, a clean, multi-paradigm, interpreted programming language designed and implemented by Jalal Kouaki. Written in pure Python 3.11+ with zero third-party dependencies, Quetz provides expressive syntax, first-class functions, lexical closures, dynamic maps and lists, structured exceptions, and precise line-and-column error reporting.

The interpreter is integrated directly into Quetz GNU/Linux:
* The source tree is installed in `/opt/quetz`.
* The executable wrapper is globally available at `/usr/local/bin/quetz`.
* Quetz source scripts (`.qz`) have registered MIME types (`text/x-quetz`); double-clicking any `.qz` file executes it inside an XFCE terminal.
* Full Unix manual pages are available via `man quetz`, and extensive documentation resides in `/usr/share/doc/quetz-language/`.

### Code Example

Below is an example demonstrating higher-order functions, closures, dynamic maps, and string interpolation in Quetz:

```quetz
# Higher-Order Functions & Maps in Quetz
fn make_counter(start = 0) {
    let count = start;
    return fn() {
        count += 1;
        return count;
    };
}

let counter = make_counter(0);
print(counter());   # 1
print(counter());   # 2

let user = { "name": "Quetz", "level": 1 };
user["level"] += 5;
print("User status: ${user["name"]} (Level ${user["level"]})");
```

### Quetz CLI Usage

```bash
# Launch the interactive REPL
quetz

# Execute a Quetz script
quetz run program.qz

# Perform a parse-only syntax check
quetz check program.qz

# Display version information
quetz --version
```

---

## 💻 System Requirements

| Specification | Minimum Requirement | Recommended |
| :--- | :--- | :--- |
| **Processor** | 64-bit x86 dual-core processor (`amd64`) | Modern 64-bit quad-core processor |
| **System Memory (RAM)** | 2 GB RAM | 4 GB RAM or more |
| **Storage Capacity** | 20 GB free disk space (for installation) | 40 GB+ SSD |
| **Firmware Support** | Legacy BIOS or UEFI (64-bit) | UEFI with standard display resolution |
| **Display Resolution** | 1024 x 768 pixels | 1920 x 1080 pixels |
| **Network** | Offline installation supported (no internet needed) | Ethernet or Wi-Fi for package updates |

---

## 📥 Download

Quetz GNU/Linux 1.0-beta is available for download:

* **Archive.org:** [https://archive.org/details/quetz-1.0-beta](https://archive.org/details/quetz-1.0-beta)
* **Image size:** ~2.48 GB (Hybrid ISO: BIOS + UEFI bootable)
* **Architecture:** amd64 (x86_64)

> [!WARNING]
> Quetz GNU/Linux 1.0-beta is an early-access release. Features may change without notice. No formal support is provided. Use at your own risk.

---

## 🛠️ Building from Source

> [!IMPORTANT]
> Generating the ISO from source is intended for advanced Linux administrators. The build process must run within a native Linux environment (such as Debian 12) with root privileges and requires Debian's `live-build` framework.

High-level build sequence:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/jalalkouaki/quetz-os.git
   cd quetz-os
   ```

2. **Inspect Host Build Dependencies:**
   Ensure host build prerequisites (`live-build`, `debootstrap`, `xorriso`, `squashfs-tools`, `syslinux-utils`, `mtools`) are installed on a Debian 12 Bookworm system.

3. **Configure & Trigger the Live-Build Script:**
   ```bash
   sudo ./build_quetz.sh
   ```

4. **Retrieve Output Image:**
   Upon completion, the bootable hybrid ISO (`quetz.iso`) will be generated in your working directory. You can write this image to a USB flash drive using `dd` or flash it using tools like Ventoy or Rufus.

---

## ⚠️ Known Issues & Limitations

* **Single Maintainer Project:** Quetz GNU/Linux is developed and maintained independently by Jalal Kouaki. Response times for non-critical features or bespoke hardware requests may vary.
* **No Unattended Auto-Updates:** While standard Debian Bookworm APT repositories are configured, automatic background updates are disabled by default to maintain stability during live sessions.
* **No Containerized Application Stores:** Flatpak, Snap, and AppStream GUI catalogs are not bundled. Software additions must be installed via `apt`, language managers (`pip`, `cargo`, `go`), or native binaries.
* **Installer Launcher Hidden in Live Menu:** The Calamares installer `.desktop` file defaults to `NoDisplay=true` to prevent accidental execution in the live environment. To install to disk, invoke Calamares manually:
  ```bash
  sudo calamares
  ```
* **Proprietary Hardware Drivers:** While open non-free firmware packages (`firmware-linux`, `firmware-realtek`, `firmware-iwlwifi`, etc.) are included, proprietary GPU drivers (such as official Nvidia proprietary display drivers) are not pre-installed.
* **Mailto Links Do Nothing in Live Session:** The default handler for `mailto:` URIs is configured to Thunderbird, which is intentionally not shipped with the distribution. Clicking an email link from within the browser or other applications will not open anything. Users should use the Contact desktop shortcut, or manually compose an email to the maintainer. This will be corrected in a future build.

---

## 🗺️ Roadmap

- [ ] **v1.0 Final Release:** Publish SHA-256 checksums, release notes, and additional download mirrors.
- [ ] **Desktop Installer Shortcut:** Provide a safe, visible desktop launcher for Calamares during live boot.
- [ ] **Quetz Language Expansion:** Expand language standard libraries, optimize AST execution performance, and introduce debugger tooling for Quetz scripts.
- [ ] **Syntax Highlighting Add-ons:** Release official `.qz` syntax highlighting plugins for Mousepad, Nano, Vim, and VS Code.
- [ ] **Live Persistence Option:** Provide documented utilities for creating persistent live USB installations.
- [ ] **Automated CI/CD Workflows:** Implement GitHub Actions pipelines to automatically compile and verify ISO images from source recipes.

---

## 🤝 Contributing

Contributions, feedback, and bug reports are warmly welcome!

1. **Bug Reports:** If you encounter unexpected kernel panics, package conflicts, or language runtime errors, please open an issue on the repository describing your hardware and reproduction steps.
2. **Feature Discussions:** For ideas on additional developer tools or syntax suggestions for the Quetz programming language, feel free to open a GitHub Discussion.
3. **Pull Requests:** PRs improving build recipes, documentation, or the Quetz interpreter codebase are appreciated. Please ensure scripts remain clean and adhere to Debian packaging guidelines.

---

## 📄 License

* **Base Distribution:** Quetz GNU/Linux is a derivative of Debian GNU/Linux. Individual packages and binaries inherit their upstream Debian, GNU, Apache, BSD, or MIT licenses.
* **Build Recipes & Custom Scripts:** The orchestration scripts, branding assets, and helper utilities created specifically for Quetz GNU/Linux are published under the **MIT License**.
* **Quetz Programming Language:** The Quetz interpreter and standard libraries are released under the **MIT License**.

---

## 🙏 Credits & Acknowledgments

Quetz GNU/Linux stands on the shoulders of the open-source community:

* **[The Debian Project](https://www.debian.org/):** For providing the rock-solid Universal Operating System.
* **[The Debian Live Team](https://wiki.debian.org/DebianLive):** For the exceptional `live-build` framework.
* **[The XFCE Development Team](https://www.xfce.org/):** For engineering a lightning-fast, modular, and enduring desktop environment.
* **[The Calamares Team](https://calamares.io/):** For an installer framework that simplifies OS deployment.
* **[The Plymouth Project](https://www.freedesktop.org/wiki/Software/Plymouth/):** For enabling smooth graphical boot transitions.

---

## 📬 Contact & Maintainer

Quetz GNU/Linux and the Quetz programming language are developed and maintained by **Jalal Kouaki**.

* **Portfolio:** [https://jalalkouaki.co](https://jalalkouaki.co)
* **GitHub:** [@jalalkouaki](https://github.com/jalalkouaki)
* **LinkedIn:** [jalal-kouaki-a257033a0](https://www.linkedin.com/in/jalal-kouaki-a257033a0)
* **Email:** [jalalkouaki@outlook.com](mailto:jalalkouaki@outlook.com)

---

*Made with care by Jalal Kouaki — Fast, light, and rock-solid Debian workstation.*

