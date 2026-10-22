# Nexus Compression & Recovery Studio

> Draft documentation staging: application packages and browser HTML are pending a later verified commit. Any proposed version or trial path below is not a shipped release or live trial. Do not merge until package and link checks pass.

**Version 2.7.0 · next-release staging · experimental software**

Explore low-bit factor compression and teacher-guided recovery of supported local language models.

Compression, successful inference and recovered language quality are separate milestones. Custom factor layouts require matching metadata, tokenizer and runtime support. A small packed file does not imply equally small training memory.

## Recorded recovery rate and research attribution

**2,500 tokens/second** is the developer-reported recorded recovery rate. It has not been independently reproduced in this documentation pass and is not autoregressive chat generation throughput or a guarantee for another model, corpus or GPU.

This is an independent Nexus adaptation inspired by Samsung Research LittleBit, not an official Samsung product. The custom recovery curriculum is a Nexus extension. Preserve the original research citations and upstream notices. Any SamsungLabs LittleBit code governed by CC BY-NC 4.0 retains those terms; another repository license cannot supersede them. Sub-1-bit packed storage does not imply sub-1-bit arithmetic, optimizer memory, full-model cache residency or stock llama.cpp compatibility.

Research credit: Banseok Lee, Dongkyu Kim, Youngcheon You and Youngmin Kim, [LittleBit: Ultra Low-Bit Quantization via Latent Factorization](https://arxiv.org/abs/2506.13771). The [official SamsungLabs implementation](https://github.com/SamsungLabs/LittleBit) is separately licensed. SmolLM2-derived weights retain credit to the Hugging Face SmolLM team and the upstream Apache 2.0 obligations; modified Nexus weights are not a newly pretrained model or an official upstream release.

For the browser edition, select the original recovery_corpus.zip through its local picker, which retains checksum verification, or use the existing custom corpus import. The original corpus ZIP is not embedded in the HTML; the small pinned knowledge-job payload is retained.

The desktop release is being packaged with the Nexus AI-style installer: a consolidated change summary, one installation confirmation, determinate progress and reuse of compatible existing dependencies. Only verified completion should trigger app launch and installer closure; Windows launch behavior requires its own acceptance test.

## Browser trial: staged, not yet published

[Open the single-file browser edition](./Nexus_Compression_Recovery_Studio_v2_7_Browser.html). This relative link names the bundled HTML source; GitHub's file viewer does not execute it. An instant browser-trial link will be added only after an HTTPS Pages deployment has been approved and verified. No live deployment is claimed here.

Use a compatible browser with WebGPU on HTTPS or a supported secure localhost origin. Select local inputs through the file pickers. The edition includes its JavaScript, CSS and WGSL kernels in one HTML file, with no runtime CDN dependency. Online dataset downloads, server model bridges, Python, PyTorch and native hardware monitoring are not available in this browser-only build. Runtime network requests are blocked. External documentation links are opened only when selected.

GPU API availability is not a successful arithmetic test or proof that a model fits. Physical Windows 11/Radeon/WebGPU execution remains a separate qualification step.

## Desktop package and installation

The staged desktop distribution is one ZIP containing the Python installer and its data parts. Extract the entire ZIP together before launching the installer; keep all parts beside the installer in the layout supplied by the package. Each distributed data component must be smaller than 20,000,000 bytes. The reconstructed application, installed files, downloaded model weights and total ZIP can be larger.

The package entry point is `Start_Nexus.py`; keep `Nexus_payload.001.nxd`, `Nexus_payload.002.nxd` and all following parts alongside it. Run `python Start_Nexus.py` with the supported Python interpreter. The final package manifest is the authority for hashes and dependencies. Do not run an installer from a different release against these data parts. Read its change summary before confirming installation. Packaging and Windows acceptance are release gates, not implied by this README.

### Desktop prerequisites

The current AMD installer gate targets Windows 11 **25H2**, an existing compatible AMD driver, and standard x64 CPython **3.11–3.14**. Do not generalize this gate to every Windows 11 release. Physical Windows/WebView2/Radeon acceptance remains pending. No global drivers, compiler or PATH changes are part of this installer.

The installer probes and reuses compatible existing PyTorch unchanged. If no runtime passes, only the product-owned pinned AMD dependencies are eligible for installation. Missing desktop dependencies are app-local.

## Measurement and validation

Native PyTorch tests distinguish synthetic scratch fixtures from loaded-model/corpus workloads. Timed training, evaluation, warm-up/compilation, prompt processing and autoregressive generation are different measurements. Report valid target tokens, elapsed time, model, context, batch size, precision, backend and hardware alongside throughput; do not count padding as useful tokens or describe a CPU result as GPU performance.

The source handoff passed recorded CPU regression and frontend checks. Browser editions passed static/DOM checks, not physical GPU arithmetic or performance qualification. A clean scoped test run does not prove absence of bugs. No maximum speed, universal model support or Windows driver certification is promised.

## Project and licensing

Developed by Rich Dunbar / Nexus Emerging Technology using AI-assisted coding and an iterative build–measure–learn process. Existing repository licenses and third-party notices remain authoritative. Model, dataset and upstream-code terms apply separately; this README grants no new reuse rights.

[Previous README, including original research citations and credits](docs/README_PREVIOUS.md). Historical release details there are not claims about this staged edition.

## Wiki source

[English](docs/wiki/Home.md) · [Français](docs/wiki/Home.fr.md) · [日本語](docs/wiki/Home.ja.md) · [한국어](docs/wiki/Home.ko.md). These are reviewable repository files, not a claim that the live GitHub Wiki has been published.
