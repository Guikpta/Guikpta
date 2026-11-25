### PC Hardware & Emulation Performance QA

Performance QA & Systems Diagnostics contributor focused on GPU/CPU profiling, VRAM bottleneck analysis, and telemetry-driven optimizations for modern console emulation (Vulkan / C++).

- **Test Rig:** AMD Ryzen 5 5500 (6c/12t) · 16 GB DDR4-3200 · NVIDIA GeForce GTX 1660 Super (6 GB GDDR6)
- **Workflow:** Controlled A/B frametime benchmarking, custom C++ telemetry instrumentation, and AI-assisted patch validation (`Clang-cl` / `Ninja` / `CMake`)

---

### Featured Open-Source Contributions ([zortos293/Lichii](https://github.com))

- **[PR #2556 — Batch readback `CopyBuffer` calls per `BufferId`](https://github.com/pull/2556):** Grouped per-slice GPU-to-CPU readback submissions into single batched `runtime.CopyBuffer` calls per buffer, cutting peak reader fence wait by **38.5%** (`473.8 ms/s` → `291.5 ms/s`) with zero readback verification mismatches.
- **[Issue #2477 — Render pass split & CPU serialization profiling](https://github.com/issues/2477):** Instrumented `vk_buffer_cache` and `vk_scheduler` (`EDEN_NX2_UPLOAD_SPLIT_TRACE`) to classify ~2,400 render-pass-breaking uploads/sec during particle bursts, ruling out held-pass hoisting (`1.2%` of breaks) and isolating tick-level read hazards.
- **[Issue #2444 — Buffer cache VRAM pressure regression on 6 GB GPUs](https://github.com/issues/2444):** Ran clean-cache A/B build comparisons on Turing 6 GB hardware, isolating `935 MiB` buffer cache growth (`947` buffers) triggering `1.27 GiB` host memory spill.
- **[Issue #2365 — 6 GB VRAM host spill & memory pressure triage](https://github.com/issues/2365):** Isolated `915 MiB` image allocations triggering `1.25 GiB` host memory spill on Turing 6 GB GPUs and validated pre-release memory fixes.
