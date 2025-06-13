# 📘 kernel_diary

Welcome! This is my personal documentation of learning and writing **high-performance kernels** across different hardware platforms — including NVIDIA A800, RTX 4090, H800, and NPUs.

I’ve had some experience with CUDA programming in the past, but it was mostly focused on “getting things to run.” When porting a computationally intensive but logically simple CPU program to the GPU, it’s often possible to achieve tens or even hundreds of times speedup with minimal tuning.

However, increasingly, I find myself needing to **take over existing GPU kernels and make them better**. This is a much more challenging task — one that demands a much deeper understanding of the kernel itself and the underlying hardware. I realized how little I still know.

This repository is my attempt to document what I’m learning, step by step. I hope it will keep me consistent, and I’d love to connect with new friends who are also on this journey.

---

## 🗺️ Learning Plan & Objectives

Below are the goals I’ve set for myself as part of this journey:

### 0. Master GPU Profiling Tools
- Learn to use **Nsight Compute** and **Nsight Systems** effectively.
- Understand and interpret performance metrics.
- Identify bottlenecks, inefficiencies, and estimate performance ceilings from reports.

### 1. High-Performance Dense Matrix Multiplication on A800 / RTX 4090
- Implement a highly optimized dense matmul kernel.
- Benchmark and analyze performance across two platforms.

### 2. Dense Matrix Multiplication on H800
- Port and tune the matmul kernel to H800.
- Study architecture-specific tradeoffs and performance behavior.

### 3. High-Performance Sparse Matrix Multiplication on A800 / RTX 4090
- Implement a performant sparse matmul kernel using structured/block sparsity.
- Explore sparsity-aware memory layouts and scheduling.

### 4. Sparse Matrix Multiplication on H800
- Adapt the sparse kernel for H800 and evaluate scalability.

### 5. Custom Kernels on NPU
- Start writing low-level kernels on NPUs.
- Explore toolchains and memory models beyond CUDA.

### 6. High-Performance Quantization Kernels on A800 / RTX 4090
- Implement quantization and dequantization kernels (e.g.,FP32, FP16, BF16, INT8, FP8, FP6，INT4).
- Optimize for memory bandwidth and compute throughput.

### 7. Quantization Kernels on H800
- Adapt and optimize for H800-specific execution pipelines and bandwidth constraints.

### 8. Quantization–Communication Overlap Kernels
- Build fused kernels that integrate quantization with collective communication.
- Follow approaches like [`Triton-distributed`](https://github.com/ByteDance-Seed/Triton-distributed).

### 9. Compression Kernels on A800 / RTX 4090
- Optimize lossy and lossless compression kernels (e.g., cusz-i, cuSZp, cuSZ).
- Focus on memory bandwidth and GPU throughput.

### 10. Compression Kernels on H800
- Tune and scale compression kernels on H800 for cross-platform validation.

---

## 🧩 References & Acknowledgments

This project is deeply inspired by the following amazing open-source projects:

- [ByteDance-Seed/Triton-distributed](https://github.com/ByteDance-Seed/Triton-distributed)
- [KnowingNothing/MatmulTutorial](https://github.com/KnowingNothing/MatmulTutorial)
- [ByteDance-Seed/SDP4Bit - jet_quant_cuda tools](https://github.com/ByteDance-Seed/SDP4Bit/tree/main/tools/jet_quant_cuda)

Special thanks to **Jinda Jia**, **Size Zheng**, and **Kaige Zhang** for sharing their insights and work. I’m learning from their excellent implementations and will build on top of them in this diary.

If you are the author of any of the above works and have concerns about how they are cited or referenced here, please feel free to contact me and I will make corrections or remove the content as needed.

---

## 🧪 Sections in Progress

I'll be maintaining topic-specific notes and benchmarking reports in the following areas:

###  `GEMM/`
Dense matrix multiplication kernel tuning and profiling.

###  `spMM/`
Sparse matrix multiplication techniques: format conversions, tiling, and coalesced loads.

###  `NPU/`
Experiments with custom kernels on NPUs and non-CUDA hardware.

###  `stochastic_quant/`
Stochastic rounding and noise-injected quantization kernels.

###  `triton-distributed/`
Custom kernels that overlap quantization and communication, inspired by Triton-distributed.

###  `compression/`
Optimized compression kernels—both lossy and lossless—targeting large-scale scientific simulations and distributed machine learning.
---

## 💡 Philosophy

> *To write great kernels, we must understand not just code, but how memory moves, how hardware stalls, and where throughput is lost.*

Performance tuning is as much about insight and measurement as it is about code. This project is where I try to combine all three.

---

Feel free to watch this repository or open a discussion if you’re on a similar journey!
