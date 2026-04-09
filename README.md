# JavaFIBS Linux Launcher

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Platform: Linux](https://img.shields.io/badge/Platform-Linux-lightgrey.svg)](https://kernel.org)

## 🎲 The Problem
[JavaFIBS](http://www.fibs.com/) is a popular interface for the Free Internet Backgammon Server. However, the closed-source Java package has a significant bug on Linux: it utilizes **absolute paths** instead of relative paths for its image assets. 

Because these paths are compiled into the package, the interface typically loads with missing textures and broken board elements.

## 🛠 The Workaround
I designed this launcher to bridge the gap between the legacy Java application and the Linux filesystem. By forcing the working directory through a shell wrapper, the application can correctly map its assets.

This project was built manually—**without AI assistance**—specifically to ensure a seamless experience for Linux users.

---

## ⚠️ Configuration Required (Critical)
Both the shell script and the desktop launcher contain paths specific to my local environment. **You must modify both files** to match your own filesystem.

### 1. Update the Shell Script (`fibs.sh`)
Open `fibs.sh` and change the directory path to your local JavaFIBS folder:
```bash
#!/bin/bash
cd /home/YOUR_USERNAME/JavaFIBS2001/
java -jar JavaFIBS-1.0.11_JDK16.jar
