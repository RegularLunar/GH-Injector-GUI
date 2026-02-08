# GH Injector GUI

This repository contains the Qt-based GUI interface for the [Guided Hacking DLL Injector](https://guidedhacking.com/resources/guided-hacking-dll-injector.4/).

Originally prototyped in AutoIt, the front end was ported to C++ (Qt Framework) in 2020 by [Kage](https://guidedhacking.com/members/kage.109622/) and [Multikill](https://github.com/multikill) to improve performance and compatibility. It is currently maintained by Broihon.

**Compatibility:** MSVC 2019 / MSVC 2022 and Qt 5.15.2.

## Preview
![image](https://github.com/guided-hacking/GH-Injector-Library/assets/15186628/d5c6670c-538f-4a48-a565-bb277e4dc46e)
![image](https://github.com/guided-hacking/GH-Injector-Library/assets/15186628/3ca83e0f-0e8b-4bc9-a101-0bb28e105698)![image](https://github.com/guided-hacking/GH-Injector-Library/assets/15186628/d070f0f0-8469-48f1-9744-6b199f0d1b73)

## Features
*   **UIPI Bypass:** Implements intelligent drag-and-drop to interact with processes at higher integrity levels.
*   **Command Line Interface:** Supports argument-based execution for automation.
*   **Auto Injection:** Watchdog functionality for automatic injection into target processes.
*   **Shortcut Generator:** Built-in tool to create launch parameters.

## Build Instructions

This project requires a specific environment configuration involving both dynamic and static Qt builds. Follow these steps sequentially to ensure the project links correctly.

### 1. Prerequisites
*   **Visual Studio 2019 or 2022**: [Download](https://visualstudio.microsoft.com/vs/)
*   **Qt VS Tools Extension**: [Marketplace Link](https://marketplace.visualstudio.com/items?itemName=TheQtCompany.QtVisualStudioTools2022)

### 2. Qt Framework Setup
Two versions of Qt 5.15.2 are required: standard (dynamic) and static.

**A. Standard Installation**
1.  Download the [Qt Online Installer](https://www.qt.io/download-qt-installer).
2.  Install the following components:
    *   `Qt 5.15.2` -> `MSVC 2019 32-bit`
    *   `Qt 5.15.2` -> `MSVC 2019 64-bit`

**B. Static Build Installation**
1.  Download the **Qt 5.15.2 Static** release from [martinrotter/qt5-minimalistic-builds](https://github.com/martinrotter/qt5-minimalistic-builds/releases).
2.  Extract the archive to a clean path (Project defaults expect the path below):
    ```text
    C:\Qt\5.15.2\qt-5.15.2-static-msvc2019-x86_64
    ```

### 3. Visual Studio Configuration

**Register Qt Versions:**
1.  In Visual Studio, go to **Extensions** -> **Qt VS Tools** -> **Qt Versions**.
2.  Add the following paths (adjust if your installation path differs):
    *   `C:\Qt\5.15.2\msvc2019`
    *   `C:\Qt\5.15.2\msvc2019_64`
    *   `C:\Qt\5.15.2\qt-5.15.2-static-msvc2019-x86_64`

**Project Properties:**
1.  Right-click the Project in Solution Explorer -> **Properties**.
2.  Navigate to **Qt Project Settings** -> **Qt Installation**.
3.  Map the configurations as follows:
    *   `x86` configuration: Select `msvc2019`
    *   `x64` configuration: Select `msvc2019_64`
    *   `x64_static` configuration: Select `qt-5.15.2-static-msvc2019-x86_64`
4.  Restart Visual Studio to force Intellisense re-indexing.

### 4. Dependencies
1.  Download the [GH-Injector-Library](https://github.com/Broihon/GH-Injector-Library).
2.  Set the C++ Language Standard to `std:c++20`.
3.  Build the library.
4.  Copy the compiled library files to the GH Injector GUI project folder.

## Credits

*   **Logic/Maintenance:** [Broihon](https://github.com/Broihon)
*   **Initial Qt Port:** [Kage](https://guidedhacking.com/members/kage.109622/) and [Multikill](https://github.com/multikill)
*   **Third-party:**
    *   [Qt-Frameless-Window-DarkStyle](https://github.com/Jorgen-VikingGod/Qt-Frameless-Window-DarkStyle)
