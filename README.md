# Nexus Compression & Recovery Studio

## [Try in your browser](<https://rdunbar01.github.io/Nexus-Little-Bit-Compression-Recovery-/Nexus_Compression_Recovery_Studio_v2_7_Browser.html>) · pending activation

**Pages is not activated or verified for this release yet.** The link above is its planned HTTPS launch address, not a claim that a live trial is available. The exact [single-file HTML](./Nexus_Compression_Recovery_Studio_v2_7_Browser.html) is in the repository root; GitHub's source viewer does not execute it.

Once published, open the link and choose **Check WebGPU adapter** to inspect the interface and browser capability. The first-10-seconds goal is to reach the UI and check capability, not to download a model, finish training or guarantee inference. Load time depends on your connection and device.

**Browser trial: no Python required. Native PyTorch backend: full download required.** Download every component in [releases/2.7.0](releases/2.7.0/), not just the HTML or installer. The browser does not contain or run Python/PyTorch. See [Python and native runtime requirements](#python-and-native-runtime-requirements).

## Current release licensing

This Nexus release is not offered under Apache License 2.0. Nexus-owned software may be used only for personal, non-commercial purposes. Any other use, including commercial use, modification or redistribution, requires express written consent from the rights holder. Third-party code, models, datasets and separately licensed components retain their own licenses and notices. Previously granted rights and rights that cannot lawfully be restricted remain unchanged.


> The reviewed source, installer components and single-file HTML are published on the main branch. GitHub Pages activation is separate and remains pending. Native Windows/Radeon qualification remains pending.

**Version 2.7.0 · published source and installer components · experimental software**

Explore low-bit factor compression and teacher-guided recovery of supported local language models.

Compression, successful inference and recovered language quality are separate milestones. Custom factor layouts require matching metadata, tokenizer and runtime support. A small packed file does not imply equally small training memory.

## Recorded recovery rate and research attribution

**2,500 tokens/second** is the developer-reported recorded recovery rate. It has not been independently reproduced in this documentation pass and is not autoregressive chat generation throughput or a guarantee for another model, corpus or GPU.

This is an independent Nexus adaptation inspired by Samsung Research LittleBit, not an official Samsung product. The custom recovery curriculum is a Nexus extension. Preserve the original research citations and upstream notices. Any SamsungLabs LittleBit code governed by CC BY-NC 4.0 retains those terms; another repository license cannot supersede them. Sub-1-bit packed storage does not imply sub-1-bit arithmetic, optimizer memory, full-model cache residency or stock llama.cpp compatibility.

Research credit: Banseok Lee, Dongkyu Kim, Youngcheon You and Youngmin Kim, [LittleBit: Ultra Low-Bit Quantization via Latent Factorization](https://arxiv.org/abs/2506.13771). The [official SamsungLabs implementation](https://github.com/SamsungLabs/LittleBit) is separately licensed. SmolLM2-derived weights retain credit to the Hugging Face SmolLM team and the upstream Apache 2.0 obligations; modified Nexus weights are not a newly pretrained model or an official upstream release.

For the browser edition, select the original recovery_corpus.zip through its local picker, which retains checksum verification, or use the existing custom corpus import. The original corpus ZIP is not embedded in the HTML; the small pinned knowledge-job payload is retained.

The desktop distribution is packaged with the Nexus AI-style installer: a consolidated change summary, one installation confirmation, determinate progress and reuse of compatible existing dependencies. Only verified completion should trigger app launch and installer closure; Windows launch behavior requires its own acceptance test.

## Browser capabilities and limits

Explore compression and recovery controls with supported local inputs. The original recovery_corpus.zip is not embedded; select it with the local picker for checksum verification or use the existing custom-corpus import.

Use a compatible WebGPU browser on HTTPS or a supported secure localhost origin. The single file includes its JavaScript, CSS and WGSL kernels without a runtime CDN dependency. Browser GPU work uses the custom JavaScript/WebGPU engine, not PyTorch. Online dataset downloads, server model bridges and native hardware monitoring are unavailable; runtime network requests are blocked. External documentation links open only when selected.

A WebGPU API or adapter check is not a successful arithmetic test, a model-fit result or a performance measurement. Physical Windows 11/Radeon/WebGPU execution remains a separate qualification step.

## Desktop package and installation

The desktop distribution contains the Python installer and its data parts in the versioned package directory below. Download all files together, preserving the supplied layout; if using a ZIP, extract it completely before launching the installer. Keep all parts beside the installer. Each distributed data component is at most 10,000,000 bytes; every individual distribution file is below 20,000,000 bytes. The reconstructed application, installed files, downloaded model weights and total ZIP can be larger.

The package entry point is `Start_Nexus.py`; keep `Nexus_payload.001.nxd`, `Nexus_payload.002.nxd` and all following parts alongside it. Run `python Start_Nexus.py` with the supported Python interpreter. The final package manifest is the authority for hashes and dependencies. Do not run an installer from a different release against these data parts. Read its change summary before confirming installation. Recorded package review and isolated extraction checks do not establish native Windows acceptance.

## Python and native runtime requirements

- **Recommended launcher: standard 64-bit CPython 3.12.** The installer advertises Python **3.11–3.14**, but the bootstrap itself does not enforce that version range. Opening the installer with another version is not evidence that the native backend is compatible.
- **New AMD runtime installation requires standard, non-free-threaded, 64-bit CPython 3.11–3.14** on Windows 11 **25H2**. Existing runtimes are tested before that installation gate and are reused only when the runtime probe passes; their Python must match their installed PyTorch wheels. No wider Python-version compatibility is certified here.
- The packaged native probe expects **PyTorch 2.14.0+rocm10.1.0**, HIP and the configured RX 7900 XT/XTX device, then performs a finite FP32 forward/backward check. Python, AMD drivers and compiler prerequisites are not installed or changed by this package. Check the [official AMD compatibility matrix](https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html) for the exact OS/GPU/driver combination.

These are installer/runtime conditions, not completed physical Windows, WebView2, Radeon or full-model qualification. A successful probe does not qualify every precision, compilation mode or workload. Recovery also provisionally admits Windows 11 **26H2 build 26300+**. That source-code allowance is not a completed platform qualification or an extension of AMD’s documented support matrix.

## Measurement and validation

Native PyTorch tests distinguish synthetic scratch fixtures from loaded-model/corpus workloads. Timed training, evaluation, warm-up/compilation, prompt processing and autoregressive generation are different measurements. Report valid target tokens, elapsed time, model, context, batch size, precision, backend and hardware alongside throughput; do not count padding as useful tokens or describe a CPU result as GPU performance.

The source handoff passed recorded CPU regression and frontend checks. Browser editions passed static/DOM checks, not physical GPU arithmetic or performance qualification. A clean scoped test run does not prove absence of bugs. No maximum speed, universal model support or Windows driver certification is promised.

## Project and licensing

Developed by Rich Dunbar / Nexus Emerging Technology using AI-assisted coding and an iterative build–measure–learn process. Existing repository licenses and third-party notices remain authoritative. Model, dataset and upstream-code terms apply separately; this README grants no new reuse rights.

[Previous README, including original research citations and credits](docs/README_PREVIOUS.md). Historical release details there are not claims about this edition.

## Wiki source

[English](docs/wiki/Home.md) · [Français](docs/wiki/Home.fr.md) · [日本語](docs/wiki/Home.ja.md) · [한국어](docs/wiki/Home.ko.md). These are reviewable repository files, not a claim that the live GitHub Wiki has been published.

## Included 2.7.0 package

[Installation guide](releases/2.7.0/README.md) · [Python installer](releases/2.7.0/Start_Nexus.py) · [All package components](releases/2.7.0).

Download the entire version directory together and run Start_Nexus.py with all five Nexus_payload data files beside it. The native installer validates the packaged data. The root browser HTML is a separate self-contained trial; GitHub's file viewer does not execute it and no live Pages deployment is claimed.
