# Nexus Compression & Recovery Studio — Home

**2.7.0 · English**

This is the reviewable Wiki source for the next release, not a claim that the live Wiki or browser trial is already published.

[English](Home.md) · [Français](Home.fr.md) · [日本語](Home.ja.md) · [한국어](Home.ko.md)

## Purpose

Explore low-bit factor compression and teacher-guided recovery. Compression, successful inference and recovered quality are separate milestones. Select a compatible local model and corpus; the original corpus ZIP is selected locally and checksum-verified, not embedded in the HTML.

## Choose an edition

### Browser edition

[HTML](../../Nexus_Compression_Recovery_Studio_v2_7_Browser.html) · [README](../../README.md)

Use a compatible WebGPU browser on HTTPS or a supported secure localhost origin. The single HTML file contains the custom JavaScript/WGSL engine. Import supported local files. No Python, PyTorch, native service, online dataset download or native GPU telemetry is available; runtime network requests are blocked. GitHub’s source viewer is not an executable trial.

### Installed edition

Extract the complete release ZIP and keep the installer with all data parts. Every distributed component must be smaller than 20,000,000 bytes; reconstructed files and model downloads can be larger. Follow the matching package manifest and installer summary. Native PyTorch settings and tests belong to the installed edition, not the HTML-only edition.

## Evidence and limits

CPU regression and static/DOM checks are not physical Windows/Radeon/WebGPU validation. Compare only equivalent model, corpus, context, batch, precision and backend conditions. Training/recovery, prompt processing and token generation rates are different measurements. No universal compatibility or maximum speed is guaranteed.

Developer-reported recorded recovery rate: **2,500 tokens/second**. Not independently reproduced here and not chat-generation speed. This independent Nexus work is inspired by Samsung Research LittleBit, not an official Samsung release. Sub-1-bit storage does not mean sub-1-bit training memory or proven L3-cache residency. Preserve applicable upstream licensing, including CC BY-NC 4.0 for SamsungLabs LittleBit code.

## Credits and licensing

Rich Dunbar / Nexus Emerging Technology, developed with AI-assisted coding. Existing licenses and third-party research, code, model and dataset terms remain in force. This page grants no additional license.

## Current release licensing

This Nexus release is not offered under Apache License 2.0. Nexus-owned software may be used only for personal, non-commercial purposes. Any other use, including commercial use, modification or redistribution, requires express written consent from the rights holder. Third-party code, models, datasets and separately licensed components retain their own licenses and notices. Previously granted rights and rights that cannot lawfully be restricted remain unchanged.
