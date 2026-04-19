<div align="center">

# Leo Camus — @Dev-next-gen

**AI Infrastructure Engineer · AMD ROCm Contributor · Open Source**

Paris, France · Self-taught · No degree · Full stack from silicon to inference.

</div>

---

## Projects

**[flux-amd-rocm](https://github.com/Dev-next-gen/flux-amd-rocm)** — FLUX.1-dev at parity with NVIDIA on AMD RDNA3

- 4-GPU Megatron-style tensor parallelism · 51.5 s/image @ 1024² · 11 GB/GPU
- Int8 quantization + async group offloading · single GPU 82 s · 12.5 GB VRAM
- 3 upstream-ready patches for torchao + diffusers (pin_memory, non_blocking, stream sync)

**[diffusers-rocm-parallel](https://github.com/Dev-next-gen/diffusers-rocm-parallel)** — Multi-GPU inference stack for AMD

- Tensor parallel FLUX on 5× RX 7800 XT (gfx1101)
- Ring attention LSE shape fix · Ulysses context parallel
- Drop-in bench scripts, no NVIDIA required

**[openclaw](https://github.com/Dev-next-gen/distributed-agent-runtime)** — Autonomous bug bounty pipeline

- Multi-agent orchestration · Qwen3 80B + 14B · fully local
- recon → scan → analysis → CVSS report pipeline

---

## Stack

```
Compute     AMD ROCm 7.1 · 5× RX 7800 XT (gfx1101) · 80 GB VRAM total
Inference   PyTorch 2.7 · diffusers · torchao · llama.cpp · Qwen3 80B ctx 262K
ML          Tensor parallelism · group offloading · int8/int4 quantization · flash attention
Security    Bug bounty · nuclei · subfinder · katana · autonomous pipelines
Systems     Linux · Python · Node.js · Rust · PostgreSQL · Supabase
```

---

<div align="center">

*Building the AMD side of the AI stack — one upstream PR at a time.*

</div>
