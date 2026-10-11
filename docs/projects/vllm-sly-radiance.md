<!-- GENERATED from catalog/projects/vllm-sly-radiance.yaml by scripts/build.py — do not edit. -->

# SlyBase/vllm-sly-radiance

**The fastest single-card R9700 image — vLLM with hand-written MXFP4 kernels, DFlash2 and full 262k context on one 32 GB RDNA4 card.**

**Use it if:** You have one R9700 and want the single-card MXFP4 setup with the highest reported decode and prefill numbers, without tuning kernels yourself.

| Field | Value |
|---|---|
| Status | `unverified` — Submitted but not yet reproduced by a maintainer or community volunteer. |
| Verification | `author_reported` — The author published the setup and results; not independently reproduced. |
| Kind | A prebuilt container image and its build sources. |
| Hardware | RDNA4 (gfx1201); tested on Radeon AI PRO R9700 |
| Software | ROCm 10.1; Docker; As stated by the author (image 1.1.0): ROCm 10.1, torch 2.13.0 / triton 3.8.0 / torchvision 0.28.0 (AMD +rocm10.1.0 wheels), vLLM 0.31.0 built from source, aiter 0.1.23, transformers 5.17.0; libr4d kernels plus this repo's MXFP4 W4A8 GEMM and attention tunes. |
| Runtime | vLLM |
| Models tested | Qwen3.8-27B (Quark-AWQ-MXFP4), syvai/Qwen3.8-27B-DFlash2-W4A16 (drafter) |
| Quantization | mxfp4, nvfp4, w4a16 |
| Provides | `openai_api`, `continuous_batching`, `speculative_decoding`, `dflash`, `custom_kernels`, `long_context` |
| Topology | single_gpu |
| Not suitable for | GPUs outside RDNA4 (e.g. RDNA2, RDNA3, RDNA3.5) |
| Audience | `operator` — Comfortable with Docker, drivers and launch flags. |
| Last verified | 2026-10-07 |
| Last commit checked | — |
| Listed since | 2026-10-11 |

Built by **tf1rst**.

A vLLM image for gfx1201 (RDNA4) built to make one 32 GB card with one MXFP4 model as fast as it gets: native MXFP4 W4A8 GEMM, fused norm/quant, DFlash2 speculative decoding with a W4A16 drafter, and the full 262k context on a single R9700. Reference run (image 1.0.0, 300 W): ~136 tok/s single-stream decode, ~3,100 tok/s prefill (2,635 at 47k), 461 tok/s at 8 concurrent requests, 437k-token KV pool. Every number measured with BetterBench.


**Builds on:** [StillDeadcode/vllm-radiance](vllm-radiance.md)

**Quick start:**

```sh
docker pull ghcr.io/slybase/vllm-sly-radiance:1.1.0-rocm10.1

```

**Known issues:** 

- TP 2/3/4/8 paths are included in the image but untested (single-card focus).

**Notes:** Also serves NVFP4, compressed-tensors INT4, ParoQuant, AutoRound and escha checkpoints on the same card (see docs/BENCHMARKS.md). Multi-GPU guidance in docs/MULTI-GPU.md.


## Evidence

No benchmark records yet. Run [BetterBench](betterbench.md) and submit the result.

## Links

[Repository](https://github.com/SlyBase/vllm-sly-radiance) · [Docker image](https://ghcr.io/slybase/vllm-sly-radiance) · [Record](../../catalog/projects/vllm-sly-radiance.yaml)
