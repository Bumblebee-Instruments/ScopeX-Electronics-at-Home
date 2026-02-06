# Scope App – Run Package

This folder contains a **sharing version** of the Scope application: everything needed to run it on another Linux machine (same architecture) without installing Qt. **Qt 6 is included** (Widgets, SerialPort, PrintSupport and required plugins), so you do not need to install Qt on the other device.

## Contents

- **scope_app** – the application executable  
- **lib/** – Qt 6 libraries (Core, Gui, Widgets, SerialPort, PrintSupport, DBus)  
- **plugins/** – Qt plugins (platforms, xcbglintegrations, printsupport)  
- **run_scope_app.sh** – run script that uses the bundled Qt

## How to run

1. Copy this **entire folder** to the other device (same architecture, e.g. x86_64 Linux).
2. Open a terminal in this folder and run:
   ```bash
   ./run_scope_app.sh
   ```
   Or run the executable directly with the environment set:
   ```bash
   export LD_LIBRARY_PATH="$(pwd)/lib:$LD_LIBRARY_PATH"
   export QT_PLUGIN_PATH="$(pwd)/plugins"
   ./scope_app
   ```

## Requirements on the other device

- Linux, same architecture (e.g. x86_64) as the build machine.  
- Standard system libraries (X11, OpenGL, fontconfig, etc.) are still required; install them if needed (e.g. Fedora: `dnf install libX11 libxcb mesa-libGL`).

You do **not** need to install Qt 6 on the other device; the needed Qt libraries and plugins are in this folder.
