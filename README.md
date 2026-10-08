# NEXUS LittleBit Compression & Recovery

**An experimental WebGPU-based LLM compression, inference, and recovery toolkit**\
**Developer:** NEXUS Emerging Technology · **Release:** v11 · **Date:** 8 October 2026

**Important**

**Research software, not a production-ready inference or training system.** NEXUS is an independent adaptation inspired by LittleBit research; it is not the official LittleBit implementation or a complete replacement for `llama.cpp`. Claims about recovered model quality and hardware performance require independent benchmarking.

## Overview

NEXUS explores aggressive quantization of local language models and the recovery of capabilities lost during compression. Its v11 browser workflow combines:

- **LittleBit-inspired factor compression** of GGUF model matrices, with default targets of **0.5 bits per weight (BPW)** for projections and **2 BPW** for embeddings and output heads. Actual storage also includes rank, scales, and other overhead.
- **Custom WebGPU inference** with GPU-resident projections, attention, and output scoring.
- **Five-stage recovery curriculum** totalling **10 million token exposures** (not 10 million distinct tokens).
- **Browser-native recovery**, with `.nqat` checkpoints and experimental recovered GGUF exports.
- **Optional Python/PyTorch workflow** for alternative compression and recovery operations.

**Supported browser recovery profile:** SmolLM2-135M, with a matching Q8_0 teacher and NEXUS-packed student. Other model presets or experimental sub-1-bit targets should not be interpreted as verified universal compatibility.

## Included model: NEXUS SmolLM2 Q0.691

**This repository includes an experimental compressed version of [SmolLM2-135M-Instruct](https://huggingface.co/HuggingFaceTB/SmolLM2-135M-Instruct), released here as NEXUS SmolLM2 Q0.691.** It is a **modified, ultra-low-bit student model derived from Hugging Face's original SmolLM2 weights**, not a newly pretrained model and not an official Hugging Face or Samsung release.

| **Item** | **Details** |
| --- | --- |
| Original model | [HuggingFaceTB/SmolLM2-135M-Instruct](https://huggingface.co/HuggingFaceTB/SmolLM2-135M-Instruct) |
| Original developer | **Hugging Face SmolLM team and contributors** |
| Included NEXUS derivative | **SmolLM2 Q0.691** — experimental LittleBit-inspired, low-bit compression |
| Recovery status | **Five-stage NEXUS recovery still required**; restored accuracy and instruction-following have not been independently demonstrated |
| Original model license | **Apache License 2.0**; retain applicable upstream attribution and notices |
| Original Q8_0 teacher | **Not included**; obtain and, if necessary, convert a compatible original checkpoint separately |

The **Q0.691** designation identifies this NEXUS experimental compressed build; it is **not a validated claim** of 0.691 effective bits per weight across every tensor, or of parity with Q4/Q8 or the original model. The included packed artifact may require the custom NEXUS factor-aware runtime and is **not directly compatible with unmodified `llama.cpp`**. Run the NEXUS recovery curriculum and compare it against a matching teacher before drawing quality conclusions.

**Credit and upstream links:**

- **Original SmolLM2 weights and model card:** [Hugging Face — SmolLM2-135M-Instruct](https://huggingface.co/HuggingFaceTB/SmolLM2-135M-Instruct)
- **Original source and training project:** [huggingface/smollm](https://github.com/huggingface/smollm)
- **Research paper:** Loubna Ben Allal et al. (2025), [*SmolLM2: When Smol Goes Big — Data-Centric Training of a Small Language Model*](https://arxiv.org/abs/2502.02737)
- **Upstream model license:** [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)

NEXUS Emerging Technology is responsible for its compression, model-format adaptations, experimental recovery workflow and integration—not for the original SmolLM2 pretraining or instruction tuning. The upstream model's Apache 2.0 attribution and license obligations continue to apply to distributed modified weights.

## Quick start

1. **Extract the entire distribution ZIP.** Do not launch the HTML files from within the archive.
2. Enter the `NEXUS_LittleBit_Recovery_Studio/` folder. Keep `nexus_corpus_payload.js` next to both HTML files; the size-optimized release shares this payload.
3. Open **`Nexus_Web_LLM.html`** in a WebGPU-capable version of Edge or Chrome and check GPU initialization.
4. Find the **included NEXUS SmolLM2 Q0.691 compressed student model** among the repository model artifacts. It is an experimental compression output, **not a fully recovered or quality-validated model**.
5. For baseline testing and recovery, obtain a compatible **SmolLM2-135M-Instruct Q8_0 GGUF teacher** separately, starting from the [official Hugging Face model](https://huggingface.co/HuggingFaceTB/SmolLM2-135M-Instruct). The upstream repository does not necessarily provide the required Q8_0 GGUF directly.
6. **Optional:** To create a new student instead of using the included one, open **`NEXUS_LittleBit_Recovery_Studio.html`**, load the Q8_0 teacher, and export a packed factor GGUF.
7. Reopen or reload `Nexus_Web_LLM.html`, choose **Recovery** before loading a chat model, then select the **Q8 teacher** and the included or newly created **packed student**.
8. Start with conservative settings, save checkpoints frequently, and compare the original and recovered models using identical evaluation settings.

**Initial settings:** sequence length **32**, evaluation cap **1,024 tokens**, and application allocation ceiling **4,096 MiB**. These are starting points, not guaranteed hardware-fit limits. Driver and browser overhead are additional.

If your browser blocks local-file access, serve the extracted application folder over localhost:

```
cd NEXUS_LittleBit_Recovery_Studio
python3 -m http.server 8000 --bind 127.0.0.1
```

Then open `http://127.0.0.1:8000/Nexus_Web_LLM.html`. This command only serves local files; it **does not** start a Python training backend.

## Compression and recovery workflow

| **Stage**  | **Purpose**             | **Key details**                                                                                               |
| ---------- | ----------------------- | ------------------------------------------------------------------------------------------------------------- |
| Baseline   | Establish a reference   | Use the matching SmolLM2-135M-Instruct Q8_0 GGUF and record outputs.                                          |
| Compress (optional) | Pack a new factorized student | Skip this step when using the bundled Q0.691 student; otherwise the default targets are 0.5 BPW projections and 2 BPW embeddings/head. |
| Recover    | Train factor parameters | Uses the Q8 teacher, packed student, browser WebGPU backend, and a staged curriculum.                         |
| Checkpoint | Preserve work           | Use **Stop after update** and download a `.nqat`; checkpoints are **not** persisted automatically.            |
| Evaluate   | Compare before/after    | Keep prompts, evaluation settings, and baselines consistent. Export measurement reports.                      |

Recovery maintains FP32 masters, gradients, and optimizer state. **Training memory can be much larger than the packed model size.** For exact resumption, retain the original teacher and student files, settings, and matching `.nqat` checkpoint. Restarting another cycle retains learned factors but resets Adam. Python `.pt` checkpoints are **not interchangeable** with browser `.nqat` files.

The exported NEXUS factor GGUF is **not directly supported by stock `llama.cpp`**.

### Browser recovery model constraints

| **Parameter**       | **v11 recovery profile** |
| ------------------- | ------------------------ |
| Architecture        | SmolLM2-135M             |
| Layers              | 30                       |
| Hidden width        | 576                      |
| Query / KV heads    | 9 / 3                    |
| Head width          | 64                       |
| Vocabulary size     | 49,152                   |
| Teacher matrices    | Q8_0                     |
| Positional encoding | Unscaled RoPE            |

The separate adaptive inference companion has broader, but still limited, compatibility. Its presets are configuration suggestions, **not a claim that all listed models are supported**. It is not part of the v11 distribution.

## Recovery corpus: 10 million token exposures

| **Curriculum stage**     | **Budget** | **Source families**                                |
| ------------------------ | ---------- | -------------------------------------------------- |
| General language         | 2M         | DCLM-Edu / FineWeb-Edu                             |
| Structured text and code | 2M         | Cosmopedia V2 / Stack-Edu                          |
| Mathematics              | 2M         | FineMath / InfiMM-WebMath                          |
| Instruction tuning       | 2M         | Smol-SmolTalk                                      |
| Replay                   | 2M         | Reuse of the previous four stages                  |
| **Total**                | **10M**    | **8M selected source-token positions + 2M replay** |

A separate **32,768-token WikiText-2** validation stream is included. Budgets may reuse samples; they do not imply 10 million unique training tokens. The corpus manifest records relevant revisions and hashes. Near-duplicate contamination has not been independently audited, and underlying dataset licenses remain in force.

## WebGPU architecture

The browser uses **WebGPU** for GPU buffer management and **WGSL compute shaders** for model operations. Packed-factor projections use two matrix-vector passes instead of reconstructing an entire dense matrix. JavaScript coordinates model parsing, tokenizer selection, job scheduling, UI, and downloads.

- **Inference:** embeddings, projection layers, attention, and output scoring on the GPU where supported.
- **Compression:** WebGPU-accelerated randomized-SVD matrix products, with some QR/eigensolver and optional fitting work on CPU workers.
- **Recovery:** forward/backward computations and Adam updates for factor masters and scales; other dense tensors stay frozen in this workflow.

WebGPU may expose adapter limits, but does not reliably report total computer memory or free VRAM. Hardware compatibility, throughput and quality require testing on the specific browser, driver and GPU.

## Developer-reported Radeon run

The NEXUS developer reports running a **10-million-token recovery** using an AMD Radeon 7900 GPU and the browser-native WebGPU backend. This is a developer report, **not an independently reproduced benchmark**. Exact model-quality changes, throughput, elapsed time, driver/browser versions and final loss have not been established from the supplied evidence.

Historical validation in `VALIDATION.md` predates the developer's report. It includes CPU logit/tokenizer comparisons, software-adapter shader tests, and tiny-model gradient/optimizer checks, **not** a completed independent hardware recovery benchmark.

## Project files

The runtime files below are located inside `NEXUS_LittleBit_Recovery_Studio/` in the distribution ZIP. The included compressed model is a separate repository artifact; its exact filename and location must be checked against the published repository contents.

| **File**                                                              | **Role**                                                             |
| --------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Included **NEXUS SmolLM2 Q0.691** model artifact                     | Compressed derivative of Hugging Face SmolLM2; recovery pending       |
| `Nexus_Web_LLM.html`                                                  | Browser inference UI and recovery controls                           |
| `NEXUS_LittleBit_Recovery_Studio.html`                                | Factor compression UI and corpus export                              |
| `nexus_corpus_payload.js`                                             | Shared recovery corpus payload in the under-25-MB distribution       |
| `smol_integration.js`                                                 | SmolLM2 tokenizer/ChatML and factor runtime integration              |
| `webgpu_backend.js`                                                   | GPU matrix-product acceleration for compression                      |
| `webgpu_autograd.js`                                                  | GPU tensors, gradients, and optimizer operations                     |
| `browser_recovery.js`                                                 | Teacher/student recovery, evaluation, `.nqat` and GGUF exports       |
| `build_bundle.py`                                                     | Rebuilds embedded runtime scripts/UI; source edits may need bundling |
| `local_ui.js`, `launch.py`                                            | Optional local Python interface                                      |
| `torch_compress.py`, `recovery.py`                                    | Optional PyTorch compression and recovery                            |
| `gguf_factors.py`                                                     | Factor GGUF packing and CPU helpers                                  |
| `corpus_builder.py`                                                   | Optional corpus selection and rebuilding                             |
| `compile_embedded_corpus.py`, `embed_corpus.py`, `embedded_corpus.py` | Corpus creation, embedding, extraction, and checks                   |
| `corpus/manifest.json`                                                | Corpus provenance and token-count metadata                           |
| `tests/`                                                              | Numerical fixtures and regression tests                              |
| `VALIDATION.md`                                                       | Historical verification and limitations                              |
| `PYTORCH_STUDIO_README.md`, `requirements.txt`                        | Optional Python setup and dependencies                               |
| `PACKAGE_NOTES_UNDER_25MB.md`                                         | Distribution-specific shared-payload instructions                    |

### Optional Python interface

Read `PYTORCH_STUDIO_README.md` and `requirements.txt` before installing dependencies. Install a supported PyTorch build separately. `python launch.py` runs the optional local application at `http://127.0.0.1:8765`. Older Python documentation may predate v11 browser recovery; the browser implementation is in the HTML application, `browser_recovery.js`, and `webgpu_autograd.js`.

## Research attribution and implementation differences

**SmolLM2:** The underlying pretrained and instruction-tuned model was developed by the **Hugging Face SmolLM team**, including Loubna Ben Allal, Anton Lozhkov, Elie Bakouch, Gabriel Martín Blázquez and their coauthors. See the [official SmolLM2-135M-Instruct model card](https://huggingface.co/HuggingFaceTB/SmolLM2-135M-Instruct), [upstream repository](https://github.com/huggingface/smollm) and [SmolLM2 paper](https://arxiv.org/abs/2502.02737). **NEXUS SmolLM2 Q0.691 is a modified compressed derivative, not an original NEXUS-trained foundation model.**

**LittleBit:** This independent NEXUS experiment is inspired by **Banseok Lee, Dongkyu Kim, Youngcheon You, and Youngmin Kim**, *LittleBit: Ultra Low-Bit Quantization via Latent Factorization* (NeurIPS 2025). It adapts the underlying idea to a different Q8-teacher compression/recovery workflow, browser-native inference, a **NEXUS-designed** five-stage token curriculum, custom factor GGUF representations, and experimental WebGPU recovery. The five-stage curriculum is a NEXUS extension, **not a five-stage method prescribed by Samsung's paper**.

**Reference:** [Lee et al. — LittleBit (arXiv:2506.13771)](https://arxiv.org/abs/2506.13771)

Research credit belongs to the original authors. The official SamsungLabs LittleBit repository is separately licensed under **CC BY-NC 4.0**; this project's license does not supersede that or any third-party model and dataset terms.

## License and usage

- NEXUS-owned contributions are intended to be distributed under the **Apache License 2.0**, subject to the applicable license file and notices.
- This is **experimental software**. That status describes its readiness; it is **not an additional restriction** on the Apache license.
- **A compressed, modified SmolLM2 model artifact (NEXUS SmolLM2 Q0.691) is included in this repository.** The unmodified SmolLM2 model and the Q8_0 teacher required for baseline/recovery are **not included**; obtain them separately from the [official SmolLM2 source](https://huggingface.co/HuggingFaceTB/SmolLM2-135M-Instruct).
- **Original model copyright and license:** Hugging Face SmolLM team and contributors; [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0). Preserve original attribution and applicable notices when redistributing the compressed derivative, and identify it as modified.
- Upstream code, model artifacts, and datasets may carry their own permissions and obligations.

**NEXUS Emerging Technology · Experimental research release · 2026**
