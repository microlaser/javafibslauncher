# JavaFIBS Linux Launcher

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Platform: Linux](https://img.shields.io/badge/Platform-Linux-lightgrey.svg)](https://kernel.org)

## 🎲 The Problem
[JavaFIBS](http://www.fibs.com/) is a popular interface for the Free Internet Backgammon Server. However, the closed-source Java package is plagued by a significant bug on Linux: it utilizes **absolute paths** instead of relative paths for its image assets. 

Because these paths are hardcoded/compiled into the package, the interface typically loads with broken textures and missing board elements, rendering it unplayable on modern Linux distributions.

## 🛠 The Workaround
I designed this launcher to bridge the gap between the legacy Java application and the Linux filesystem. By utilizing a specific directory structure and a shell-based environment wrapper, this workaround "tricks" the application into finding its assets correctly without requiring access to the original source code.

This project was built manually—**without AI assistance (vibe coding)**—specifically to ensure a seamless, "just works" experience for end-users who want to enjoy backgammon on Linux.

## 📁 Repository Contents
* `fibs.sh`: The core shell script that sets the environment and executes the Java package.
* `fibs.desktop`: A Linux desktop entry file for integration with application launchers (GNOME, KDE, etc.).
* `fibsREADME`: Original setup instructions and technical notes.

## 🚀 Installation & Usage
1.  Ensure you have a **Java Runtime Environment (JRE)** installed on your Linux system.
2.  Clone this repository or download the script files.
3.  Place your `JavaFIBS.jar` and the accompanying `images` folder in the directory specified in the `fibs.sh` script.
4.  Make the script executable:
    ```bash
    chmod +x fibs.sh
    ```
5.  Run `./fibs.sh` or move the `.desktop` file to `~/.local/share/applications/` to launch from your menu.

---
**Author:** [Michael Lazin](https://github.com/microlaser)  
*Security Engineer | Debian Developer | Systems Philosopher*
