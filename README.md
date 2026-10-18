# Quetz GNU/Linux 1.0

A lightweight, developer-focused Debian 12 derivative featuring out-of-the-box multi-language runtimes and native integration with the Quetz programming language.

**Download:** https://archive.org/details/quetz-1.0-beta

---

## What it is

Quetz GNU/Linux is an independent desktop operating system built on Debian 12 (Bookworm) using Debian's native live-build tooling. It pairs a polished, dark-themed XFCE 4.18 desktop with pre-configured developer toolchains and an offline-first installation experience. Most notably, it serves as the reference platform for Quetz, a pure-Python multi-paradigm interpreted programming language.

## Highlights

- **Debian 12 (Bookworm) foundation** with Linux 6.1 LTS
- **XFCE 4.18** desktop with Arc-Dark and Papirus-Dark theming
- **Native Quetz language support** — REPL, `.qz` file associations, man page, and offline documentation
- **Pre-configured runtimes:** Python 3.11, Node.js 18, Go 1.19, Rust 1.63, Java 17 LTS, C/C++ (GCC 12), Ruby 3.1, PHP 8.2, Perl 5.36, Lua 5.4
- **Curated CLI suite:** ripgrep, fd-find, fzf, bat, jq, tmux, htop, and classical Unix diagnostics
- **Calamares graphical installer** for permanent deployment
- **Fully offline-capable** — the live system, compilers, runtimes, and documentation work without a network connection
- **Custom Plymouth boot splash** with a branded spinner, backed by ISOLINUX (BIOS) and GRUB (UEFI)
- **Deliberately minimal** — no office suites, no games, no Snap/Flatpak layers, no background bloat

## The Quetz programming language

Quetz is a clean, multi-paradigm, interpreted programming language written in pure Python 3.11+ with zero third-party dependencies. It features expressive syntax, first-class functions, lexical closures, dynamic maps and lists, structured exceptions, and precise line-and-column error reporting. The interpreter is installed at `/opt/quetz` with a global wrapper at `/usr/local/bin/quetz`.

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
print(counter());
print(counter());

let user = { "name": "Quetz", "level": 1 };
user["level"] += 5;
print("User status: ${user["name"]} (Level ${user["level"]})");
```

## System requirements

- 64-bit x86 processor (amd64)
- 2 GB RAM minimum; 4 GB recommended
- 20 GB free disk space for installation
- Legacy BIOS or 64-bit UEFI firmware
- 1024 x 768 display minimum; 1920 x 1080 recommended
- Network optional — installation works fully offline

## Download

https://archive.org/details/quetz-1.0-beta

- Image size: ~2.6 GB
- Format: Hybrid ISO (BIOS + UEFI bootable)
- Architecture: amd64 (x86_64)

## The mascot — Oxcy

Quetz GNU/Linux uses Oxcy, the Kiss Land mascot, as part of its visual identity. The mascot is used purely out of personal appreciation for the artwork and its aesthetic, and no copyright infringement is intended.

This is an independent personal portfolio project and is not affiliated with, endorsed by, sponsored by, or associated with the original creators, artists, labels, or any rights holders connected to Kiss Land, Oxcy, The Weeknd, XO, or Republic Records.

All trademarks and copyrights related to Oxcy and Kiss Land remain the property of their respective owners. If any rights holder has concerns about the use of the mascot in this project, please open an issue on the project repository and it will be addressed promptly.

## License

- **Base distribution:** Quetz GNU/Linux is a derivative of Debian GNU/Linux. Individual packages and binaries inherit their upstream Debian, GNU, Apache, BSD, or MIT licenses.
- **Build recipes, custom scripts, and the Quetz programming language:** MIT License.

## Credits

Quetz GNU/Linux stands on the shoulders of the open-source community. Special thanks to:

- **The Debian Project** — for providing the rock-solid Universal Operating System.
- **The Debian Live Team** — for the exceptional live-build framework.
- **The XFCE Development Team** — for a lightning-fast, modular, and enduring desktop environment.
- **The Calamares Team** — for an installer framework that simplifies OS deployment.
- **The Plymouth Project** — for enabling smooth graphical boot transitions.

## Author

**Jalal Kouaki**

- GitHub: https://github.com/jalalkouaki
- LinkedIn: https://www.linkedin.com/in/jalal-kouaki-a257033a0
- Portfolio: https://jalalkouaki.co
- Contact: jalalkouaki@outlook.com
