<div align="center">

# Leo Camus — @Dev-next-gen

**Agent pipeline architecture · AI infrastructure · ROCm multi-GPU**

Paris, France · Self-taught

<a href="https://www.credly.com/badges/c81bf14d-d935-41ca-828d-4a48d8bd3704/linked_in_profile">
  <img width="120" alt="AMD ROCm Certified Associate" src="https://github.com/user-attachments/assets/7c85969d-d465-4195-9b19-f7b25e69699f" />
</a>

</div>

---

I build systems that find things people missed, and I make infrastructure run where the tooling says it shouldn't. Two examples. An agent pipeline that opened 181 proven fixes across 102 open-source repositories in one week, and got them merged into V8, NASA flight software, LLVM, React and Tokio. And AMD GPUs doing tensor-parallel diffusion inference that the ecosystem assumes needs NVIDIA.

I don't write the patches by hand. I design the system that produces them, and the gates that decide what is allowed to leave it. I own the machine it all runs on, so every number here is measured, not estimated.

---

## The pipeline, and what it shipped

I built a system that hunts defects in large codebases, proves them, and prepares the fix for review. Two rules decide what is allowed to leave it: nothing ships without a reproduction that fails before the patch and passes after, and nothing ships until the target project's own contribution rules are satisfied. Everything else is engineering around those two. The search is not deterministic; the gate is — the full write-up, the evidence and what I still don't know are in **[defect-hunting-pipeline](https://github.com/Dev-next-gen/defect-hunting-pipeline)**.

What that produces, measured:

| | |
|---|---|
| **357 agent runs over 151 hours** | 10–16 September 2026, one week |
| **181 pull requests opened, proven and written up** | across 102 repositories |
| **83 merged, 7 closed** without merging | in 44 projects I don't maintain |
| **$909 total — $10.95 per merged fix** | failed runs included; nearly a third find nothing |

Seven rejections against eighty-three merges is the number I care about, because that ratio is what the proof requirement is for. Automated reviewers land the same way — Copilot's reviewer returned *approval recommended* on the WSL parser fix, CodeRabbit called the cuDF one *suitable for merge*.

The hardest review it has passed is the **[JavaScript engine v8/v8](https://chromium.googlesource.com/v8/v8/+/refs/heads/main/AUTHORS)**: two CLs through Gerrit, CLA and committer review, into the ECMA-262 implementation behind Chrome and Node.js. My name is in the AUTHORS file.

The fixes I would point to first:

| | |
|---|---|
| **[NASA F´](https://github.com/nasa/fprime/pull/5972)** · C++ · flight software | `SpacePacketFramer` dropped its status signal when a buffer allocation failed, so the component below it waited forever and the downlink chain stalled instead of reporting the error. |
| **[tokio](https://github.com/tokio-rs/tokio/pull/8459)** · Rust · 33k★ | `copy_buf` never touched the coop budget, so a task copying in a loop never yielded back to the runtime. The cooperativeness test never finishes without the fix. |
| **[React](https://github.com/react/react/pull/37608)** · 250k★ | Flight and DevTools only stripped part of the `async ` prefix V8 puts on stack frame names, so server-component frames came out malformed. |
| **[celery](https://github.com/celery/celery/pull/10620)** · Python · 29k★ | `AzureBlockBlobBackend.as_uri` leaked the SAS token and the account key into logs and error messages. |
| **[swc](https://github.com/swc-project/swc/pull/12353)** · Rust · 34k★ | The TypeScript parser ignored a line break after `declare`, accepting code `tsc` rejects. Needed the `tsc-references` snapshots regenerated too. |
| **[MAME](https://github.com/mamedev/mame/pull/16112)** · C++ · 10k★ | Several WE32100 mnemonics were wrong in the disassembler. Proven against the AT&T instruction set manual, without a full MAME build. |
| **[LLVM](https://github.com/llvm/llvm-project/pull/222742)** · 40k★ | `cmake_format.py` in libc wrote CRLF on Windows, so formatting a file changed every line of it. |
| **[three.js](https://github.com/mrdoob/three.js/pull/34542)** · 116k★ | `NURBSCurve` never overrode `copy()`, so `clone()` returned a curve with no degree, knots or control points — a different shape from the original. |

Both counts are checkable, and the public search covers the whole account rather than this one week: [100 merged](https://github.com/pulls?q=is%3Amerged+author%3ADev-next-gen) · [13 closed without merging](https://github.com/pulls?q=is%3Apr+is%3Aclosed+is%3Aunmerged+author%3ADev-next-gen).

<details>
<summary><b>The rest</b></summary>

<br>

**Systems and infrastructure** — [Tailscale](https://github.com/tailscale/tailscale/pull/21308) (Go, an over-long name crashed the peerAPI DNS debug endpoint) and [#21232](https://github.com/tailscale/tailscale/pull/21232) (`Payload` panicked when the data offset ran past the length) · [GoBGP](https://github.com/osrg/gobgp/pull/3613) (Go, BGP daemon: socket address handling) · [Apache Maven](https://github.com/apache/maven/pull/13139) · [Mesa](https://github.com/mesa/mesa/pull/3860) · [ROS 2 rcutils](https://github.com/ros2/rcutils/pull/593) · [kubescape](https://github.com/kubescape/kubescape/pull/3820) (Go, `/dev/stdout` and `/dev/null` in `diff --output`) · [authentik](https://github.com/goauthentik/authentik/pull/25993) (translate before interpolating in SMS blueprints) · [nginx-ui](https://github.com/0xJacky/nginx-ui/pull/1890) (bracket IPv6 hosts for the default gRPC port) · [termux-packages](https://github.com/termux/termux-packages/pull/31608) · [uWebSockets.js](https://github.com/uNetworking/uWebSockets.js/pull/1307) · [sea-orm](https://github.com/SeaQL/sea-orm/pull/3199) (Rust, multi-hop `left_join_linked` aliasing) · [OpenSandbox](https://github.com/opensandbox-group/OpenSandbox/pull/1826)

**ML and AMD** — [pytorch/ao](https://github.com/pytorch/ao/pull/4297) (propagate `non_blocking` in `TorchAOBaseTensor._to_copy`) · [pytorch/ao](https://github.com/pytorch/ao/pull/4876) (invalid escape sequences, W605 enabled so they stay fixed) · [llama.rn](https://github.com/mybigday/llama.rn/pull/390) · [agent-framework](https://github.com/microsoft/agent-framework/pull/8206) (reset `$LASTEXITCODE` per command in persistent PowerShell sessions)

**Editors, UI and desktop** — [Dioxus](https://github.com/DioxusLabs/dioxus/pull/5836) (Rust) · [lexical](https://github.com/facebook/lexical/pull/9162) (TextNode setters read the latest state) · [AFFiNE](https://github.com/toeverything/AFFiNE/pull/15595) (accumulate overlapping doc priority requests) · [MarkText](https://github.com/marktext/marktext/pull/5320) (exported links from folders named with `#`, `?` or `%`) · [Sparkle](https://github.com/sparkle-project/Sparkle/pull/2921) (Objective-C, release-notes content length from the appcast) · [mango](https://github.com/mangowm/mango/pull/1388) (keycode-only modifiers in `parse_mod`)

**Emulation and low level** — [MAME](https://github.com/mamedev/mame/pull/16103) (`fs_prodos`: zero master index entries in tree files are sparse) · [xiaozhi-esp32](https://github.com/78/xiaozhi-esp32/pull/2256) and [#2257](https://github.com/78/xiaozhi-esp32/pull/2257) (C++ on ESP32: don't abort on short theme colors, free cJSON strings)

**Web and developer tooling** — [Puppeteer](https://github.com/puppeteer/puppeteer/pull/15451) · [orval](https://github.com/orval-labs/orval/pull/4123) (three merges) · [xmake](https://github.com/xmake-io/xmake/pull/7765) · [Raycast extensions](https://github.com/raycast/extensions/pull/31158) · [EspoCRM](https://github.com/espocrm/espocrm/pull/3790) (three merges) · [teamai-cli](https://github.com/Tencent/teamai-cli/pull/595)

**French public service** — [rdv-service-public](https://github.com/betagouv/rdv-service-public/pull/6695) · [b3desk](https://github.com/numerique-gouv/b3desk/pull/426) · [beta.gouv.fr](https://github.com/betagouv/beta.gouv.fr/pull/21678)

**Tools** — [davinci-resolve-mcp](https://github.com/samuelgursky/davinci-resolve-mcp/pulls?q=is%3Amerged+author%3ADev-next-gen) (twelve merges on LUT install and media analysis) · [pyvideotrans](https://github.com/jianchang512/pyvideotrans/pull/1207) · [QuantDinger](https://github.com/OpenByteInc/QuantDinger/pull/243) (infer exchange precision from the `Decimal` exponent) · [diagram-design](https://github.com/cathrynlavery/diagram-design/pull/201)

</details>

---

## Projects

**[Orodruin](https://github.com/Dev-next-gen/orodruin)** · live at [orodruin.dev](https://orodruin.dev) — Open-source intelligence platform, a self-hostable alternative to Palantir Gotham. 30+ live public sources (GDELT, NASA FIRMS, USGS, AIS vessels, ADS-B aircraft, submarine cables, power grid, cyber threats, satellites) fused onto a 2D/3D map and an actor graph, with an AI analyst that queries every source and drives the interface. FR/EN/AR/RU · AGPL-3.0.

**[Excalibur](https://github.com/Dev-next-gen/excalibur)** · demo at [excalibur.nextgen-labs.net](https://excalibur.nextgen-labs.net) — Active-defense deception middleware. Serves booby-trapped data to attackers, then traces and geolocates them through canary tokens. One-line integration · Rust SDK · ML scoring (PASS/CANARY/DECEIVE) · forensic tracer with Merkle log and STIX export · real-time SOC dashboard. AGPL-3.0.

**[flux-amd-rocm](https://github.com/Dev-next-gen/flux-amd-rocm)** — FLUX.1-dev at NVIDIA parity on AMD RDNA3. Megatron-style tensor parallelism across 4 GPUs, 51 s per 1024² image at 11 GB per GPU. Int8 quantization with async group offloading brings it down to a single RX 7800 XT: 80 s, 12.5 GB VRAM.

**[diffusers-rocm-parallel](https://github.com/Dev-next-gen/diffusers-rocm-parallel)** — Multi-GPU inference stack for AMD. Tensor-parallel FLUX on gfx1101, ring attention LSE shape fix, Ulysses context parallel.

**[openclaw](https://github.com/Dev-next-gen/distributed-agent-runtime)** — Autonomous security research pipeline. Multi-agent orchestration on Qwen3 80B + 14B, fully local, recon → scan → CVSS → report.

<details>
<summary><b>Client work</b> — systems I was paid to build, and still operate</summary>

<br>

**Self-hosted email infrastructure** — SMTP on my own IPs with full SPF, DKIM and DMARC alignment and automated warm-up, scoring 10/10 on Mail-Tester from the first send. Deliverability is an infrastructure problem, not a template problem. In production.

**Cross-asset atomic swap** — proof of concept on Daml/Canton for a client: the contract model, a 7/7 test suite, a web interface and bilingual documentation. Delivered.

**Production hosting I run myself** — client sites and apps on my own VPS fleet, provisioned and maintained end to end (nginx, pm2, certbot, PostgreSQL, Supabase). Among them [rim-phone.com](https://rim-phone.com), a bilingual FR/AR storefront with full RTL and cash-on-delivery, and a booking system still in daily use.

Python · Node.js · Rust · Next.js · React · FastAPI · PostgreSQL · Daml/Canton · Docker

</details>

---

## Research

**[CAMUS Theory](https://zenodo.org/search?q=metadata.creators.person_or_org.name%3A%22CAMUS%2C%20Leo%22)** — Graft-based temporal cognition in frozen LLMs. A TemporalAdapter under 0.6% of parameters, grafted at mid-depth through a forward pre-hook, decodes log-time with R² ≈ 0.9 from 1B parameters. The subspace is roughly 5-dimensional and holds across model sizes. Validated on TinyLlama-1.1B and Qwen2.5-14B in under 30 minutes, for $0.83.

Published independently on Zenodo.

---

## Background

**2022 – now** · Freelance AI infrastructure, security research, independent publication.

**2020 – 2022** · On-site GPU infrastructure engineer, 300+ GPU production facility, Kyiv, Ukraine. Hardware deployment, network architecture, 24/7 uptime under real production constraints.

**2019** · Founded and shipped a repair-management SaaS solo — 350+ pages, logistics, billing, payments. Closed by Covid.

---

## My infrastructure

```
CPU       2× Intel Xeon E5-2698 v4 — 40 cores / 80 threads
RAM       512 GB ECC
GPU       6× AMD RX 7800 XT (gfx1101) — 96 GB VRAM
NVMe      Multi-drive array
Net       10 GbE, self-hosted services
OS        Ubuntu · ROCm 7.2.2 — custom builds: rocWMMA, FA_ALL_QUANTS, HIP_GRAPHS
```

Qwen3-Coder-Next 80B runs on it at 42 t/s with a 262K context. Everything above was built and measured here.

**Inference** PyTorch · diffusers · torchao · llama.cpp · vLLM
**ML** tensor parallelism · group offloading · int8/int4 · Triton kernels
**Security** nuclei · subfinder · katana · httpx · Burp Suite Pro · responsible disclosure
**Systems** Python · Rust · Node.js · Next.js · FastAPI · PostgreSQL · Docker

---

<div align="center">

Open to research collaborations, freelance infrastructure work, and projects that shouldn't exist yet.

**[leo.camus23@gmail.com](mailto:leo.camus23@gmail.com)**

</div>
