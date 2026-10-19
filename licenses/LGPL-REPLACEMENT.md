# LGPL libraries: source and replacement

Qt for Python (PySide6/Shiboken), Qt and pynput are unmodified upstream components.
The exact versions, source archives and SHA-256 digests are recorded in sources.json.
The official AutoFlow release provides AutoFlow-ThirdParty-Sources-0.1.0.zip beside
the executable downloads at https://github.com/bonolabs/autoflow/releases .
This archive contains the corresponding LGPL source archives, license texts,
upstream build instructions and any Qt third-party attribution files. It does
not contain the proprietary AutoFlow application source. Keep source access
available for at least as long as the associated binaries are distributed.

AutoFlow uses a PyInstaller onedir bundle, not statically linked Qt. Quit the app
and back up the installation before replacing libraries. A writable copy can be
made by extracting the portable ZIP into a directory you control.

* Qt/PySide/Shiboken: shared libraries are under AutoFlow/_internal/PySide6/ and
  AutoFlow/_internal/shiboken6/. Rebuild compatible replacements from the supplied
  sources with upstream build instructions (PySide's README and build_scripts/;
  Qt's README.md/configure and CMake tooling). Match the original Qt/PySide version,
  Windows x64, CPython 3.12 ABI and compatible compiler/runtime. Replace the relevant
  .dll/.pyd files and plugins with your rebuilt versions; keep the ABI-compatible
  names and directory layout. Qt for Python build documentation:
  https://doc.qt.io/qtforpython-6/building_from_source/index.html
* pynput: Python source is shipped OUTSIDE the PYZ archive in
  AutoFlow/_internal/pynput/. Edit/replace those .py files with a compatible version.
* No signature, application entitlement check or embedded secret prevents using
  compatible replacements. The AutoFlow EULA explicitly permits reverse engineering
  needed to debug changes to LGPL libraries. ABI-breaking changes are not promised
  to be compatible. Restore your backup if a replacement fails to load.

Unneeded MouseInfo (GPL), tkinter, and the optional OpenCV FFmpeg video DLL are
excluded; AutoFlow does not use those tools/video features. Only LGPL Qt runtime
modules/plugins needed by the widget application are bundled. A license text
mentioning GPL as an alternative does not mean that alternative was selected.
