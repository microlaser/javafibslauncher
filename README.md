# JavaFIBS Linux Launcher

[![Platform: Linux](https://img.shields.io/badge/Platform-Linux-lightgrey.svg)](https://kernel.org)

## 🎲 Overview

This project is a lightweight Linux launcher for JavaFIBS (Free Internet Backgammon Server client).

The original JavaFIBS application is broken on Linux due to hardcoded **absolute paths** for image assets compiled into the binary. This results in missing textures and an unusable interface.

This repository provides a simple, practical workaround that makes JavaFIBS fully playable on Linux.

---

## ❌ The Problem

JavaFIBS uses **absolute filesystem paths** instead of relative paths for its resources.

Because of this:
- Images fail to load
- The board renders incorrectly
- The application becomes unusable on modern Linux systems

Since the application is closed-source, this cannot be fixed directly.

---

## ✅ The Solution

This launcher works by:

- Forcing the correct working directory via a shell script
- Aligning the runtime environment with what the application expects
- Restoring proper asset resolution without modifying the binary

This effectively makes a broken legacy application usable again on Linux.

---

## ⚠️ Configuration Required (IMPORTANT)

This project is **not plug-and-play**.

The included files contain **hardcoded paths from my system**, and you **must update them** to match your own filesystem.

If you skip this step, it will not work.

---

## 🛠 1. Edit the Shell Script (`fibs.sh`)

### Original script:

```bash
#!/bin/bash

cd /home/michael/JavaFIBS2001/

java -jar JavaFIBS-1.0.11_JDK16.jar
```

### What you need to do:

Change this line:

```
cd /home/michael/JavaFIBS2001/
```

To match your actual install location, for example:

```
cd /home/YOUR_USERNAME/JavaFIBS2001/
```

---

## 🖥 2. Edit the Desktop Launcher (`fibs.desktop`)

### Original file:

```ini
[Desktop Entry]

Name=Fibs

Comment=javafibs

Exec=sh /home/michael/fibs.sh

Icon=/home/michael/JavaFIBS2001/JavaFIBS.ico

Terminal=false

Type=Application

StartupNotify=true
```

### What you need to do:

Update BOTH of these lines:

```
Exec=sh /home/michael/fibs.sh
Icon=/home/michael/JavaFIBS2001/JavaFIBS.ico
```

Example:

```
Exec=sh /home/YOUR_USERNAME/path/to/fibs.sh
Icon=/home/YOUR_USERNAME/JavaFIBS2001/JavaFIBS.ico
```

If these paths are wrong, the launcher will fail silently or not appear correctly.

---

## 🔐 3. Set Permissions

Make the script executable:

```bash
chmod +x fibs.sh
```

---

## 🚀 Usage

1. Install a Java Runtime Environment (JRE)
2. Place your JavaFIBS `.jar` and `images` folder in your chosen directory
3. Update paths in:
   - `fibs.sh`
   - `fibs.desktop`
4. Run manually:

```bash
./fibs.sh
```

5. (Optional) Add to application menu:

```bash
mv fibs.desktop ~/.local/share/applications/
```

---

## 📁 Repository Contents

- `fibs.sh` — Shell launcher that fixes working directory issues
- `fibs.desktop` — Desktop integration file
- `fibsREADME` — Original notes and setup details

---

## 🧠 Skills Demonstrated

- Linux systems troubleshooting (diagnosing runtime path issues in a closed-source application)
- Reverse-engineering behavior from broken binaries
- Bash scripting and environment control
- Desktop integration on Linux (XDG `.desktop` entries)
- Practical problem-solving for real-world usability issues
- Supporting legacy software without source code access

---

## 🛠 Development Approach

This project was written manually to solve a real problem on a live system.

No code generation tools or AI-assisted coding were used — this reflects hands-on debugging, experimentation, and iterative testing to reach a working solution.

---

## 💡 Why This Exists

This was built to make JavaFIBS usable for a non-technical end user.

It is intentionally simple, transparent, and easy to modify — prioritizing reliability over abstraction.

---

## 👤 Author

Michael Lazin  
Security Engineer | Linux Specialist | Systems Thinker
