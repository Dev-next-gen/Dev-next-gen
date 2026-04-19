<div align="center">

# Leo Camus — @Dev-next-gen

**AI Infrastructure · Multi-GPU ROCm · Independent Research · Offensive Security**

Paris, France · Self-taught · No degree · Full stack from silicon to inference.

</div>

---

I build systems that run at the edge of what's technically possible — locally, at scale, without compromise. No cloud dependency, no abstraction layers hiding the truth. Every component understood, every parameter owned.

From founding a SaaS startup at 26, to operating a 300+ GPU farm on-site in Ukraine, to deploying 80B LLMs on self-hosted ROCm infrastructure and publishing independent AI research — every step was built from scratch, under real constraints.

---

## Projects

**[flux-amd-rocm](https://github.com/Dev-next-gen/flux-amd-rocm)** — FLUX.1-dev at parity with NVIDIA on AMD RDNA3

4-GPU Megatron-style tensor parallelism · 51 s/image @ 1024² · 11 GB/GPU. Int8 quantization + async group offloading on a single RX 7800 XT · 80 s · 12.5 GB VRAM.

**[diffusers-rocm-parallel](https://github.com/Dev-next-gen/diffusers-rocm-parallel)** — Multi-GPU inference stack for AMD

Tensor parallel FLUX on 5× RX 7800 XT (gfx1101) · ring attention LSE shape fix · Ulysses context parallel.

**[openclaw](https://github.com/Dev-next-gen/distributed-agent-runtime)** — Autonomous bug bounty pipeline

Multi-agent orchestration · Qwen3 80B + 14B · fully local · recon → scan → CVSS → report.

**[CAMUS Theory](https://zenodo.org/search?q=metadata.creators.person_or_org.name%3A%22CAMUS%2C%20Leo%22)** — Independent AI Research

Graft-based temporal cognition in frozen LLMs. TemporalAdapter (<0.6% params) grafted at mid-depth via forward pre-hook. R² ≈ 0.9 for log-time decoding from 1B parameters. ~5-dimensional subspace invariant across model sizes. Validated on TinyLlama-1.1B and Qwen2.5-14B in under 30 minutes for $0.83.

---

## Background

- **2020–2022** — On-site GPU infrastructure engineer, 300+ GPU production facility, Kyiv, Ukraine. End-to-end hardware deployment, network architecture, 24/7 uptime under real production constraints.
- **2019** — Founded and shipped a full SaaS repair management platform solo (350+ pages, logistics, billing, payments). Shut down by Covid.
- **2022–now** — Freelance AI infra, security research, independent publications.

---

## Stack

```
Compute       5× AMD RX 7800 XT (gfx1101) · 80 GB VRAM · ROCm 7.1
              Custom builds: rocWMMA · FA_ALL_QUANTS · HIP_GRAPHS
Inference     PyTorch · diffusers · torchao · llama.cpp · vLLM · 38 t/s @ 80B ctx 262K
ML            Tensor parallelism · group offloading · int8/int4 · Triton kernels
Security      nuclei · subfinder · katana · httpx · Burp Suite Pro · responsible disclosure
Systems       Python · Rust · Node.js · Next.js · FastAPI · PostgreSQL · Supabase · Docker
```

---

*Open to research collabs, freelance infra missions, or projects that shouldn't exist yet.*
