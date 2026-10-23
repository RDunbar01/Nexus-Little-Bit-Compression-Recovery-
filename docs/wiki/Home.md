# Nexus Compression & Recovery Studio

**Version 2.7.1**

Compress supported language models into low-bit factor representations, then use recovery training to assess how much language quality can be restored.

**[Try in your browser](https://rdunbar01.github.io/Nexus-Little-Bit-Compression-Recovery-/Nexus_Compression_Recovery_Studio_v2_7_Browser.html)** · [Download the desktop components](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/tree/main/releases/2.7.1) · [README](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/README.md)

Open the trial to inspect the interface and choose **Check WebGPU adapter**. No Python installation is needed. The aim is a quick first look; loading a model or completing a workload depends on the inputs and device.

Native package 2.7.1; browser edition 2.7.1.

## What it does

- Low-bit factor compression with local model and corpus inputs.
- Teacher-guided recovery controls and evaluation of supported models.
- Separate browser WebGPU and installed PyTorch workflows.
- Progress, timing and diagnostic records for comparing recovery runs.

## Engineering contribution

An independent implementation of a compression-and-recovery workflow that makes low-bit model experiments accessible through a local graphical interface. The Nexus recovery curriculum extends the workflow rather than reproducing an official Samsung product.

## Why a single HTML file?

The browser edition packages its interface, JavaScript, CSS and WGSL kernels in one HTML file. This makes online trials easy to open, link to and inspect without a build step or runtime CDN. The file contains the browser engine, not model weights or the native PyTorch backend.

Use a compatible WebGPU browser over HTTPS. Runtime network requests, native hardware monitoring and local-server bridges are disabled. Actual training or evaluation requires supported inputs. The native PyTorch backend requires the full download.

[English](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home) · [Français](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.fr) · [日本語](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.ja) · [한국어](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.ko)

## Python and native runtime requirements

- **Recommended launcher: standard 64-bit CPython 3.12.** The installer advertises Python **3.11–3.14**, but the bootstrap itself does not enforce that version range. Opening the installer with another version is not evidence that the native backend is compatible.
- **New AMD runtime installation requires standard, non-free-threaded, 64-bit CPython 3.11–3.14** on Windows 11 **25H2**. Existing runtimes are tested before that installation gate and are reused only when the runtime probe passes; their Python must match their installed PyTorch wheels. No wider Python-version compatibility is certified here.
- The packaged native probe expects **PyTorch 2.14.0+rocm10.1.0**, HIP and the configured RX 7900 XT/XTX device, then performs a finite FP32 forward/backward check. Python, AMD drivers and compiler prerequisites are not installed or changed by this package. Check the [official AMD compatibility matrix](https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html) for the exact OS/GPU/driver combination.

These are installer/runtime conditions, not completed physical Windows, WebView2, Radeon or full-model qualification. A successful probe does not qualify every precision, compilation mode or workload. Recovery also provisionally admits Windows 11 **26H2 build 26300+**. That source-code allowance is not a completed platform qualification or an extension of AMD’s documented support matrix.


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

## Use and attribution

Rich Dunbar / Nexus Emerging Technology. Personal use and internal commercial testing and evaluation are permitted for Nexus-owned material. Distribution, modification, production deployment and other commercial use require express written consent. Third-party licenses and previously granted rights remain unchanged. [license](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/LICENSE) · [evaluation permission (English)](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/COMMERCIAL_EVALUATION_PERMISSION.md).
