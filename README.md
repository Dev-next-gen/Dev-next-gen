<div align="center">

# Leo Camus — @Dev-next-gen

**AI Infrastructure · Multi-GPU ROCm · Independent Research · Offensive Security**

**Full Stack Development**

Paris, France · Self-taught · No degree · Full stack from silicon to inference.

</div>

---

I build systems that run at the edge of what's technically possible — locally, at scale, without compromise. No cloud dependency, no abstraction layers hiding the truth. Every component understood, every parameter owned.

From founding a SaaS startup at 26, to operating a 300+ GPU farm on-site in Ukraine, to deploying 80B LLMs on self-hosted ROCm infrastructure and publishing independent AI research — every step was built from scratch, under real constraints.

---

## Projects

**[Orodruin](https://github.com/Dev-next-gen/orodruin)** — Open-source intelligence platform · live at [orodruin.dev](https://orodruin.dev)

A self-hostable Palantir Gotham alternative. 30+ live public sources (GDELT, NASA FIRMS, USGS, AIS vessels, ADS-B aircraft, submarine cables, power grid, cyber threats, weather, satellites) fused onto a 2D/3D map and an actor graph, with an AI analyst that queries every source and drives the interface. FR/EN/AR/RU · AGPL-3.0.

**[Excalibur](https://github.com/Dev-next-gen/excalibur)** — Active-defense deception middleware · live demo at [excalibur.nextgen-labs.net](https://excalibur.nextgen-labs.net)

Serves booby-trapped fake data to attackers, then traces and geolocates them via canary tokens. One-line integration · Rust SDK · ML scoring (PASS/CANARY/DECEIVE) · forensic tracer (Merkle log, STIX export) · real-time SOC dashboard. AGPL-3.0.

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

## Products

Production SaaS, mobile apps and full-stack web — shipped end to end, most of it self-hosted. Selected deliveries:

- **Email marketing platform** — self-hosted SMTP with full SPF/DKIM/DMARC, automated IP warm-up, 10/10 on Mail-Tester on the first send. In production.
- **E-commerce store** ([rim-phone.com](https://rim-phone.com)) — Next.js + Prisma, bilingual FR/AR with full RTL, cash-on-delivery checkout. Live on HTTPS (VPS · nginx · pm2 · certbot).
- **Atomic swap PoC** — cross-asset atomic swap on Daml/Canton, 7/7 test suite, custom web UI, bilingual docs. Delivered to client.
- **Yoga studio app** — React/Vite, Supabase auth, full booking system. Deployed in production.
- **Hyperlocal marketplace** — mobile app, real-time geolocation, neighbor-to-neighbor listings.

Stack: Python · Node.js · Rust · Next.js · React · FastAPI · PostgreSQL · Supabase · Daml/Canton · Docker · Stripe · REST APIs

## Infrastructure

```
CPU     2× Intel Xeon E5-2698 v4 — 80 threads
RAM     512 GB ECC
GPU     5× AMD RX 7800 XT (gfx1101) — 80 GB VRAM total
NVMe    Multi-drive storage array
OS      Ubuntu · ROCm 7.1
Net     10 GbE local · self-hosted services
```

---

<div align="center">

<a href="https://www.credly.com/badges/c81bf14d-d935-41ca-828d-4a48d8bd3704/linked_in_profile">
  <img width="130" alt="AMD ROCm Certified Associate" src="https://github.com/user-attachments/assets/7c85969d-d465-4195-9b19-f7b25e69699f" />
</a>

*Open to research collabs, freelance infra missions, or projects that shouldn't exist yet.*

</div>
