# Nexus Compression & Recovery Studio — Home

## [Try in your browser](<https://rdunbar01.github.io/Nexus-Little-Bit-Compression-Recovery-/Nexus_Compression_Recovery_Studio_v2_7_Browser.html>) · published browser entry

The HTTPS browser entry is published and its initial screen has been checked. This is not full WebGPU, Windows or Radeon workload qualification. GitHub’s HTML source viewer does not execute the application.

The native **2.7.1** package is published on main. This startup hotfix prevents native title updates from starving interface timers. Browser **2.7.1** is live at the stable v2_7_Browser link; its residency panel waits for the workflow controls and remains behind the startup notice. The initial screen was checked without accepting that notice or running a model. Prior releases remain available; do not mix their components. Package review and extraction checks passed, but physical Windows, WebView2, Radeon and full-model qualification remain outstanding.

Open the link and choose **Check WebGPU adapter**. The first-10-seconds goal is to inspect the UI and capability, not to download a model or guarantee training/inference. Loading depends on the connection and device.

**No Python is required for the HTML trial. A full download is required for the native PyTorch backend.** Keep the Python installer and every matching data part together. Python and PyTorch do not run in the HTML. WebGPU support, local inputs and model compatibility checks still apply.

## Python and native runtime requirements

- **Recommended launcher: standard 64-bit CPython 3.12.** The installer advertises Python **3.11–3.14**, but the bootstrap itself does not enforce that version range. Opening the installer with another version is not evidence that the native backend is compatible.
- **New AMD runtime installation requires standard, non-free-threaded, 64-bit CPython 3.11–3.14** on Windows 11 **25H2**. Existing runtimes are tested before that installation gate and are reused only when the runtime probe passes; their Python must match their installed PyTorch wheels. No wider Python-version compatibility is certified here.
- The packaged native probe expects **PyTorch 2.14.0+rocm10.1.0**, HIP and the configured RX 7900 XT/XTX device, then performs a finite FP32 forward/backward check. Python, AMD drivers and compiler prerequisites are not installed or changed by this package. Check the [official AMD compatibility matrix](https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html) for the exact OS/GPU/driver combination.

These are installer/runtime conditions, not completed physical Windows, WebView2, Radeon or full-model qualification. A successful probe does not qualify every precision, compilation mode or workload. Recovery also provisionally admits Windows 11 **26H2 build 26300+**. That source-code allowance is not a completed platform qualification or an extension of AMD’s documented support matrix.

**2.7.1 · English**

Published release documentation. See the evidence and limits below.

[English](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home) · [Français](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.fr) · [日本語](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.ja) · [한국어](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.ko)

## Purpose

Explore low-bit factor compression and teacher-guided recovery. Compression, successful inference and recovered quality are separate milestones. Select a compatible local model and corpus; the original corpus ZIP is selected locally and checksum-verified, not embedded in the HTML.

## Choose an edition

### Browser edition

[HTML](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/Nexus_Compression_Recovery_Studio_v2_7_Browser.html) · [README](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/README.md)

Use a compatible WebGPU browser on HTTPS or a supported secure localhost origin. The single HTML file contains the custom JavaScript/WGSL engine. Import supported local files. No Python, PyTorch, native service, online dataset download or native GPU telemetry is available; runtime network requests are blocked. GitHub’s source viewer is not an executable trial.

### Installed edition

Download every file in the [2.7.1 package](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/tree/main/releases/2.7.1) together, retaining the supplied layout. Keep all numbered `.nxd` data parts beside [Start_Nexus.py](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/releases/2.7.1/Start_Nexus.py) and run `python Start_Nexus.py` with the supported interpreter. Read the [matching guide](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/releases/2.7.1/README.md) and installation summary before confirming. Each `.nxd` part is at most **10,000,000 bytes**; each individual distributed file, before installation, is smaller than **20,000,000 bytes**. The complete archive, reconstructed application, installed files and downloaded models can be larger. Do not mix releases. Native PyTorch settings and tests belong to the installed edition, not the HTML-only trial.

## Evidence and limits

CPU regression and static/DOM checks are not physical Windows/Radeon/WebGPU validation. Compare only equivalent model, corpus, context, batch, precision and backend conditions. Training/recovery, prompt processing and token generation rates are different measurements. No universal compatibility or maximum speed is guaranteed.

Developer-reported recorded recovery rate: **2,500 tokens/second**. Not independently reproduced here and not chat-generation speed. This independent Nexus work is inspired by Samsung Research LittleBit, not an official Samsung release. Sub-1-bit storage does not mean sub-1-bit training memory or proven L3-cache residency. Preserve applicable upstream licensing, including CC BY-NC 4.0 for SamsungLabs LittleBit code.

## Credits and licensing

Rich Dunbar / Nexus Emerging Technology, developed with AI-assisted coding. Existing licenses and third-party research, code, model and dataset terms remain in force. This page grants no additional license.

## Current release licensing

This Nexus release is not offered under Apache License 2.0. Nexus-owned software may be used only for personal, non-commercial purposes. Any other use, including commercial use, modification or redistribution, requires express written consent from the rights holder. Third-party code, models, datasets and separately licensed components retain their own licenses and notices. Previously granted rights and rights that cannot lawfully be restricted remain unchanged.

