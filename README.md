NEXUS LittleBit Experimental Pack
By Nexus Emerging Technology · v11 application and implementation notes · 8 October 2026
Free to use under Apache 2.0 for NEXUS-owned contributions. See the separate Apache license and academic-credits document for scope and
upstream/data terms.
Experimental use
This is a research and prototyping toolkit. It is not a validated production
inference or training system, and it is not equivalent to the complete llama.cpp
implementation. The developer reports a 10-million-token Radeon recovery below. Independent
reproduction, recovery quality improvement and measured GPU performance remain
unverified. Experimental is a readiness statement, not an
additional restriction on the Apache license.
Separate downloads
`NEXUS_WebGPU_Complete_v11.zip`: the unchanged original v11 application.
`README_NEXUS_v11.md`: this current README.
`NEXUS_v11_Academic_References_and_Author_Credits.md`: credits, academic
references, implementation differences and engineering solutions.
`Nexus_Web_LLM_Apache_2.0_License.txt`: the standard Apache 2.0 license
with NEXUS attribution and scope.
`NEXUS_v11_Experimental_Use.txt`: experimental-use statement.
The original ZIP contains 54 files, totalling 37,929,629 bytes
uncompressed. No outer ZIP, launch-page wrapper or extra folder pack is used
for these downloads. No model weights are supplied.
Start v11
Extract `NEXUS_WebGPU_Complete_v11.zip`. Open its
`NEXUS_LittleBit_Recovery_Studio` folder.
Open `Nexus_Web_LLM.html` in a WebGPU-capable browser. Check GPU status.
For baseline chat, load a compatible local SmolLM2-135M-Instruct Q8_0 GGUF.
For compression, open `NEXUS_LittleBit_Recovery_Studio.html` in that folder.
Follow the compression/recovery workflow below, saving checkpoints regularly.
If local-file opening is blocked, serve the extracted folder using
`python3 -m http.server 8000 --bind 127.0.0.1` and open the HTML through localhost.
This command only serves files; it does not run a Python training backend.
Developer-reported Radeon recovery
The NEXUS project developer reports using an AMD Radeon 7900 to run a
10-million-token recovery through the browser-native WebGPU backend.
This statement records the developer's reported hardware run. The exact
Radeon variant, driver/browser versions, elapsed time, throughput, settings,
final loss and before/after quality metrics were not supplied with this update.
The run is not being represented as an independently reproduced benchmark.
The embedded curriculum defines 10 million token exposures: 8 million selected
source-token positions and 2 million replay positions. "10-million-token
recovery" therefore does not mean 10 million unique new training tokens.
The historical validation shipped inside v11 predates this report and says
that no complete Radeon recovery was performed in that test environment;
this newer developer report is recorded separately rather than rewriting
those historical results.
Separate adaptive inference work
The repaired adaptive companion was delivered earlier and is not added to the
unchanged v11 ZIP. Its following capabilities are distinct from v11 recovery.
The companion reads GGUF metadata, checks the tensor graph, chooses supported
tokenization/chat formatting and estimates configuration limits. Its 100 model
profiles are configuration suggestions, not a popularity ranking or a promise
that 100 models are supported. Use Settings → Detect hardware / Auto tune;
the measured speed tuner uses this browser and loaded model.
WebGPU exposes adapter limits and sometimes adapter information; it does not
provide a reliable inventory of your whole computer or free VRAM. Estimates
must leave room for browser/driver overhead. Lower context or use a smaller
model after an allocation failure. Metadata and runtime checks take priority
over preset names. Consult the companion README for architecture and tensor
support. Some Llama/Mistral and Qwen variants work; Gemma, Phi, MoE and other
unsupported graphs are rejected. ChatGPT is a service, not a downloadable GGUF;
GPT-oss presets are marked unsupported. This pack contains no OpenAI weights.
v11 compression and recovery
Start with a matching SmolLM2-135M-Instruct Q8_0 GGUF in
`Nexus_Web_LLM.html` for baseline chat.
Open `NEXUS_LittleBit_Recovery_Studio.html`, load that same original
model, and export a packed LittleBit-factor GGUF. Default targets are 0.5
projection BPW and 2 embedding/head BPW; actual storage includes scales and
representable rank overhead. Optional ALS/ITQ/back-fitting are off by default.
Reload the v11 chat page and open Recovery before loading a chat model.
Select the Q8 teacher and the matching packed student.
Begin with sequence length 32, evaluation cap 1,024 tokens and allocation
ceiling 4,096 MiB. These are conservative starting values, not guaranteed
fit. Training uses FP32 masters, gradients and optimizer state, which can
greatly exceed packed inference size. The ceiling excludes driver overhead.
Use Stop after update regularly to download a `.nqat` checkpoint.
Completion exports a checkpoint, recovered GGUF and measurement report.
There is no automatic background checkpoint persistence.
Reload before chat with recovered weights. Compare pre/post metrics under
the same evaluation settings; compression alone does not establish quality.
Exact resume needs the same teacher/student sources, settings and `.nqat`.
Another cycle preserves learned factors and resets Adam. Python `.pt`
checkpoints cannot be imported as browser `.nqat` checkpoints.
Browser recovery enforces the SmolLM2-135M profile: 30 layers, width 576,
9 query / 3 KV heads, head width 64, vocabulary 49,152, Q8_0 teacher matrices
and unscaled RoPE. Its custom factor GGUF is not directly compatible with
stock llama.cpp. The wider companion inference support does not widen recovery.
Embedded corpus
The v11 HTML includes 10M training-token exposures: 2M general language
(DCLM-Edu/FineWeb-Edu), 2M structured text/code (Cosmopedia V2/Stack-Edu),
2M mathematics (FineMath/InfiMM-WebMath), 2M Smol-SmolTalk instructions, and
2M replay of those four stages. That is 8M selected source-token positions
plus 2M replay, with a separate 32,768-token WikiText-2 validation stream.
Large budgets recycle these samples; they do not add new training data.
The manifest records revisions and hashes. Near-duplicate contamination has
not been audited. Dataset terms remain separate from the NEXUS license.
WebGPU and the backend
WebGPU lets JavaScript allocate GPU buffers and dispatch WGSL compute shaders.
Inference performs embeddings, projections, attention and output scoring on
the GPU. Packed factor projections use two matrix-vector stages instead of
reconstructing every full dense matrix. JavaScript handles parsing, scheduling,
tokenization, UI and downloads. Browser compression accelerates randomized-SVD
matrix products, while QR/eigensolves and optional fitting still use CPU workers.
Browser recovery adds forward/backward operations and Adam for factor masters
and scales; other dense tensors remain frozen. See the backend file guide below.
Research credit
Credit for the LittleBit research belongs to Banseok Lee, Dongkyu Kim,
Youngcheon You and Youngmin Kim [1]. The NEXUS workflow is an independent,
experimental adaptation. Its Q8 teacher, curriculum and objectives differ from
the paper. Read `NEXUS_v11_Academic_References_and_Author_Credits.md` for academic context,
citations, differences and attribution.
Evidence and limits
The supplied v11 validation records CPU logit/tokenizer comparisons, native
software-adapter WGSL tests and tiny-model gradient/optimizer comparisons.
They do not establish successful full 10M-token browser recovery or hardware
performance. This download preserves executable source bytes and checks ZIP integrity
and actual contents; these document updates add no independently measured GPU
benchmark. See the historical `VALIDATION.md` inside the extracted v11 folder and the
developer report above.
Optional Python workflow
Read `PYTORCH_STUDIO_README.md` and `requirements.txt` before
installing dependencies. Install PyTorch separately for a supported backend.
`launch.py` starts the optional local app at `http://127.0.0.1:8765`.
Its existing README's statement that recovery is only PyTorch is historical:
the v11 browser recovery lives in `Nexus_Web_LLM.html`, `browser_recovery.js`
and `webgpu_autograd.js`. Neither workflow validates all GPUs automatically.
License and attribution
The branded Nexus Web LLM License includes the unchanged Apache License,
Version 2.0. Retain that license and applicable attribution when redistributing.
The official SamsungLabs LittleBit repository uses CC BY-NC 4.0, not Apache.
Models, datasets and other third-party material retain their own licenses.
This pack cannot grant rights its authors do not control.
[1] Lee et al., LittleBit: Ultra Low-Bit Quantization via Latent Factorization,
NeurIPS 2025. https://arxiv.org/abs/2506.13771
Backend and associated files
File in the extracted v11 folder	Role
`Nexus_Web_LLM.html`	Standalone v11 inference UI, embedded WGSL, corpus and browser recovery controls
`NEXUS_LittleBit_Recovery_Studio.html`	Standalone factor compressor, settings and corpus export
`smol_integration.js`	Editable SmolLM2 tokenizer/ChatML and packed-factor runtime extensions
`webgpu_backend.js`	Compression's WebGPU matrix-product backend
`webgpu_autograd.js`	GPU tensors, differentiable operations, gradients and optimizer
`browser_recovery.js`	Curriculum, teacher/student runner, evaluation, `.nqat` and GGUF export
`build_bundle.py`	Re-embeds editable runtime scripts/UI/corpus into the chat HTML; JS edits require rebuilding
`local_ui.js`	Optional local Python API bridge at localhost/127.0.0.1:8765
`launch.py`	Optional Python local server and backend checks
`torch_compress.py`	Optional PyTorch factor initialization/compression
`recovery.py`	Optional PyTorch recovery, evaluation and `.pt` checkpoints
`gguf_factors.py`	Factor GGUF parsing/packing and CPU helpers
`corpus_builder.py`	Optional corpus selection/download/rebuild workflow
`compile_embedded_corpus.py`	Tokenizer streams and corpus provenance creation
`embed_corpus.py`	Embeds corpus payloads into HTML
`embedded_corpus.py`	Extracts/verifies embedded data; refuses nonidentical overwrites
`corpus/manifest.json`	Source revisions, counts and tokenizer identity
`corpus/README.txt`	Corpus directory usage notes
`models/README.txt`, `runs/README.txt`	Placeholders for local models and generated runs; weights not supplied
`requirements.txt`	Python dependencies; compatible PyTorch must be installed separately
`tests/`	Numerical reference code, recorded results, shaders, token IDs and browser/source regressions
`VALIDATION.md`	Historical v11 evidence and its limitations
`PYTORCH_STUDIO_README.md`	Optional Python setup; some browser-recovery descriptions predate v11

ZIP SHA-256: `c62308f9dcba0f071b0592567632599c6c855f1b1bec71409b25726ac4ca8e02`.
