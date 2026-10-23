# Nexus Compression & Recovery Studio

**Version 2.7.1**

Compress supported language models into low-bit factor representations, then use recovery training to assess how much language quality can be restored.

**[Try in your browser](https://rdunbar01.github.io/Nexus-Little-Bit-Compression-Recovery-/Nexus_Compression_Recovery_Studio_v2_7_Browser.html)** · [Download the desktop components](releases/2.7.1/) · [Wiki](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki)

Open the trial to inspect the interface and choose **Check WebGPU adapter**. No Python installation is needed. The aim is a quick first look, not a promise that a model will load or finish a workload in seconds.

## What it does

- Low-bit factor compression with local model and corpus inputs.
- Teacher-guided recovery controls and evaluation of supported models.
- Separate browser WebGPU and installed PyTorch workflows.
- Progress, timing and diagnostic records for comparing recovery runs.

## Engineering contribution

An independent implementation of a compression-and-recovery workflow that makes low-bit model experiments accessible through a local graphical interface. The Nexus recovery curriculum extends the workflow rather than reproducing an official Samsung product.

## Research and recorded result

The design is inspired by [LittleBit: Ultra Low-Bit Quantization via Latent Factorization](https://arxiv.org/abs/2506.13771), by Banseok Lee, Dongkyu Kim, Youngcheon You and Youngmin Kim. Credit also belongs to the [SamsungLabs implementation](https://github.com/SamsungLabs/LittleBit) and the Hugging Face SmolLM team for SmolLM2-derived models. Their licenses and notices remain applicable.

The developer reports a recorded recovery rate of **2,500 tokens/second**. This is recovery throughput, not chat-generation speed, and was not independently reproduced in this documentation review.

Packed model size, runtime memory and recovered quality are separate measurements. Sub-1-bit storage does not establish sub-1-bit arithmetic, L3-cache residency or compatibility with stock llama.cpp. Custom factors need matching tokenizer, metadata and runtime support.

## Why a single HTML file?

The browser edition packages its interface, JavaScript, CSS and WGSL kernels in one HTML file. This makes online trials easy to open, share as a link and inspect without a build step or runtime CDN. The monolithic file is a distribution choice for accessible trials, not a claim that every model or native dependency fits inside it.

Use a compatible WebGPU browser over HTTPS. The trial uses the custom browser engine, not PyTorch. Runtime network requests, native hardware monitoring and local-server bridges are disabled. Select your recovery_corpus.zip with the local picker, which checks its checksum, or import a custom corpus. The original corpus ZIP is not embedded.

## Full application and Python

**The native PyTorch backend requires the full download.** Get every file in [releases/2.7.1](releases/2.7.1/), keep the numbered data parts beside [Start_Nexus.py](releases/2.7.1/Start_Nexus.py), and run `python Start_Nexus.py`. Review the installation plan before confirming. Do not mix release components.

Use standard **64-bit CPython 3.12** for the launcher. The advertised installer range is 3.11–3.14; actual native compatibility also depends on the selected Python/PyTorch runtime and its probe. The new AMD-runtime installation path checks standard, non-free-threaded x64 CPython 3.11–3.14 and Windows 11 25H2; an existing runtime must pass its probe. See the [runtime and validation notes](docs/TECHNICAL_NOTES.md) and [package guide](releases/2.7.1/README.md) for exact conditions. Python, GPU drivers and compilers are not silently replaced.

Each data part is at most 10,000,000 bytes; each individual distribution file is below 20,000,000 bytes. Reconstructed files, installed files and model weights can be larger.

## Validation

Recorded CPU regressions, frontend checks and package-integrity checks cover the published sources. Browser launch checks establish that the interface opens; they do not establish full-model correctness or physical Windows/Radeon performance. A WebGPU adapter check is only a capability check.

## Use and attribution

Developed by Rich Dunbar / Nexus Emerging Technology. Personal use and internal commercial testing and evaluation are permitted for Nexus-owned material. Distribution, modification, production deployment and other commercial use require express written consent. Third-party licenses and previously granted rights remain unchanged. See the [license](LICENSE) and [evaluation permission](COMMERCIAL_EVALUATION_PERMISSION.md).
