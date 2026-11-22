# Project Artifacts: Index & Navigation Guide

**Undergraduate Capstone Project (BTP Phase 1)**  
*Department of Computer Science and Engineering, Indian Institute of Technology Guwahati*  
**Author:** Maneesh S. Kolekar  
**Faculty Supervisor:** Prof. Sukumar Nandi  

---

### Quick Access
- [🎥 **Presentation Video Walkthrough (YouTube)**](https://youtu.be/zbq2NdZPaV8) — Complete architecture & empirical results walkthrough
- [📄 **Primary Conference Paper (PDF)**](paper/btp_report.pdf) — 8-Page IEEE camera-ready publication
- [📊 **Empirical Artifact Portfolio (Markdown)**](ARTIFACT_PORTFOLIO.md) — Comprehensive numbers, diagrams, and math
- [📈 **Benchmark Figures & Visuals**](results/figures/) — High-resolution Pareto plots and visual samples
- [📑 **Raw Empirical Data (CSVs)**](results/tables/) — Complete benchmark metrics across all evaluated models

---

## 1. Master Telemetry Quick Reference

| Architecture / Model | Parameters | INT8 Footprint | DRAM Bandwidth | Line Buffer SRAM | Flight Latency | Accuracy | Escape Rate (FNR) | Overkill Rate (FPR) | Micro-Crack Recall (<3px) | Frame Drops ($P_{\text{drop}}$) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **SmallNet-v3 (Proposed)** | **15,043** | **14.69 KB** | **0.0 GB/s** | **< 5 KB** | **34.50 $\mu$s** | **97.63%** | **2.87%** | **1.78%** | **82.35%** | **0.0%** |
| SmallNet-v2 (Dual Pool) | 13,986 | 13.66 KB | 0.0 GB/s | < 5 KB | 34.50 $\mu$s | 97.24% | 2.90% | 2.15% | 76.47% | 0.0% |
| **PhiNet-15K** (*ACM TECS '22*) | 15,120 | 14.76 KB | 1.20 GB/s | Frame-Buffered | 16,700 $\mu$s | 96.41% | 3.77% | 3.39% | 47.06% | > 1.2% |
| PhiNet-31K (*Paper Default*) | 30,995 | 30.27 KB | 1.20 GB/s | Frame-Buffered | 16,700 $\mu$s | 94.28% | 7.09% | 4.10% | 52.94% | > 1.2% |
| MobileNetV2 (Linear RGB) | 2.22 M | 2,174 KB | 1.20 GB/s | Frame-Buffered | 18,200 $\mu$s | 98.94% | 1.66% | 0.36% | 88.24% | > 1.5% |
| MobileNetV2 (sRGB Baseline) | 2.22 M | 2,174 KB | 1.20 GB/s | Frame-Buffered | 18,200 $\mu$s | 98.61% | 2.11% | 0.53% | 70.59% | > 1.5% |
| ResNet-18 (Heavyweight) | 11.17 M | 10,915 KB | 3.80 GB/s | Frame-Buffered | 35,400 $\mu$s | 98.69% | 2.11% | 0.36% | 76.47% | > 3.0% |
| Otsu Morphological Baseline | 8 | < 0.1 KB | 0.0 GB/s | 2.4 KB | 20.00 $\mu$s | 49.59% | 87.63% | 6.42% | 17.65% | 0.0% |
| Mahalanobis Linear Baseline | 1,368 | 1.34 KB | 0.0 GB/s | 2.4 KB | 20.00 $\mu$s | 78.02% | 39.37% | 1.43% | 11.76% | 0.0% |

---

## 2. Primary Publication & Manuscripts

| Artifact Reference | File Path | Format | Description |
| :--- | :--- | :---: | :--- |
| **IEEE Conference Paper** | [`paper/btp_report.pdf`](paper/btp_report.pdf) | PDF | Final 8-page IEEE conference paper with complete theorems, proofs, and benchmarks. |
| **LaTeX Source Code** | [`paper/btp_report.tex`](paper/btp_report.tex) | TeX | Camera-ready LaTeX document source. |
| **BibTeX Database** | [`paper/references.bib`](paper/references.bib) | BibTeX | 26 verified bibliographic reference citations. |
| **Empirical Portfolio** | [`ARTIFACT_PORTFOLIO.md`](ARTIFACT_PORTFOLIO.md) | Markdown | Self-contained quantitative data, architecture diagrams, tables, and algorithms. |

---

## 3. Empirical Benchmark Tables (CSV Registry)

| Benchmark Identifier | File Path | Scope & Sample Volume | Key Metrics Reported |
| :--- | :--- | :---: | :--- |
| **Master In-Domain AOI** | [`results/tables/table2_in_domain_aoi_with_phinet.csv`](results/tables/table2_in_domain_aoi_with_phinet.csv) | 8,163 Real Photos (Casting + Fasteners) | Accuracy, Precision, Recall, F1, FNR (Escape), FPR (Overkill), ROC-AUC |
| **Defect Physics Breakdown** | [`results/tables/table3_defect_physics_with_phinet.csv`](results/tables/table3_defect_physics_with_phinet.csv) | Granular Defect Taxonomy | Micro (<3px), Macro (>10px), Structural, Cavity, Spectral Oxidation Recall |
| **Hardware Footprint** | [`results/tables/table1_hardware_footprint.csv`](results/tables/table1_hardware_footprint.csv) | 12 Models / Configurations | Parameter counts, INT8 footprint, SRAM line buffers, DRAM bandwidth, Latency |
| **Pareto Frontier Points** | [`results/tables/table6_pareto_frontier.csv`](results/tables/table6_pareto_frontier.csv) | Efficiency Frontier Evaluation | Latency vs. FLOPs vs. Accuracy vs. Memory Bandwidth trade-offs |
| **Cross-Domain Evaluation** | [`results/tables/table_in_domain_6k_comparison_with_phinet.csv`](results/tables/table_in_domain_6k_comparison_with_phinet.csv) | 26,800 Photos across 4 SKUs | PCB, Pill, Transistor, Zipper generalization benchmarks |
| **Spatial Reduction Ablation**| [`results/tables/table_stem_v2_ablation_6k.csv`](results/tables/table_stem_v2_ablation_6k.csv) | Fine-Pitch Micro-Defect Domain | GAP vs. Dual Pooling (GAP+GMP) vs. Streaming Attention Pooling |
| **FPGA Synthesis Telemetry** | [`results/hardware_synthesis_utilization.csv`](results/hardware_synthesis_utilization.csv) | AMD Zynq-7020 Synthesis | Subsystem LUTs, Flip-Flops, BRAM36K, DSP48E1 utilization |
| **Hardware Bit-Exactness** | [`results/multi_sample_verification_report.csv`](results/multi_sample_verification_report.csv) | Photographic Test Vectors | MSE ($0.000$), PSNR ($99.99\text{ dB}$), SSIM ($1.000$), Exact Match ($100\%$) |

---

## 4. Benchmark Visualizations & Figures

| Figure Name | File Path | Modality | Content & Takeaway |
| :--- | :--- | :---: | :--- |
| **Master Pareto Frontier** | [`results/figures/fig1_pareto_frontier.png`](results/figures/fig1_pareto_frontier.png) | Vector Plot | Accuracy vs. Latency (log scale) showing SmallNet Pareto dominance over PhiNet. |
| **Defect Physics Recall** | [`results/figures/fig2_stem_ablation_physics.png`](results/figures/fig2_stem_ablation_physics.png) | Bar Chart | Micro-crack sensitivity (<3px flaws) comparing linear stem vs. sRGB baselines. |
| **Cross-Domain Transfer** | [`results/figures/fig3_unseen_transfer_comparison.png`](results/figures/fig3_unseen_transfer_comparison.png) | Grouped Chart | Comparison across Regime 0 (Zero-Shot), Regime 1 (Head Calib), Regime 2 (Fine-Tuning). |
| **Scratch vs. Fine-Tuned** | [`results/figures/fig4_6k_scratch_vs_finetune.png`](results/figures/fig4_6k_scratch_vs_finetune.png) | Distribution | Accuracy distributions across out-of-domain industrial components. |
| **Pipeline Dataflow** | [`results/figures/isp_pipeline.png`](results/figures/isp_pipeline.png) | Diagram | Visual comparison of DDR frame buffering vs. inline streaming line buffering. |
| **Visual Inspection Samples**| [`results/figures/visual_samples/`](results/figures/visual_samples/) | Directory | Side-by-side photographic comparisons and 4-stage feature activation breakdowns. |

---

## 5. Silicon Hardware Characterization Reports

| Report Identifier | File Path | Target Architecture | Contents & Key Telemetry |
| :--- | :--- | :---: | :--- |
| **FPGA Resource Utilization**| [`results/fpga_resource_utilization_breakdown.md`](results/fpga_resource_utilization_breakdown.md) | AMD Zynq-7020 / Gowin Tang Nano | Post-synthesis place-and-route resource table ($3,021$ LUTs, $5.5$ BRAMs, $27$ DSPs). |
| **Timing & Fmax Analysis** | [`results/timing_and_fmax_characterization.md`](results/timing_and_fmax_characterization.md) | $148.5\text{ MHz}$ Pixel Clock | Critical path analysis, hold/setup slack, and maximum operating frequency ($F_{\max}$). |
| **ASIC Silicon Projection** | [`results/asic_gate_count_and_area_estimation.md`](results/asic_gate_count_and_area_estimation.md) | 28nm Standard-Cell CMOS | Gate count equivalent ($142\text{K}$ NAND2 gates) and die area projection ($<0.4\text{ mm}^2$). |

---

## 6. Dataset Manifests & Direct Ingestion Links

| Dataset Identifier | Public Repository Link | Sample Volume | Inspected Part Geometry | Primary Defect Types |
| :--- | :--- | :---: | :--- | :--- |
| **Pilot Technocast Casting** | [Kaggle Portal](https://www.kaggle.com/datasets/ravirajsinh45/real-life-industrial-dataset-of-casting-product) | 7,348 Photos | Cast Iron Submersible Pump Impellers | Casting blowholes, shrinkage cavities, mechanical fractures |
| **MVTec AD Fasteners** | [MVTec Portal](https://www.mvtec.com/company/research/datasets/mvtec-ad) | 815 Photos | M8 Threaded Metal Nuts & M6 Metal Screws | Thread deformation, pitch stripping, scratches, oxidation |
| **MVTec AD Transfer SKUs** | [MVTec Portal](https://www.mvtec.com/company/research/datasets/mvtec-ad) | 6,700 / SKU | Transistor Leads, PCB, Pill, Zipper Teeth | Bent leads, hairline shorts, edge chips, broken teeth |

---

## 7. Core Algorithmic Formulations Index

All algorithms are mathematically formulated in [Section 6 of `ARTIFACT_PORTFOLIO.md`](ARTIFACT_PORTFOLIO.md#6-algorithmic-formulations-exact-mathematical-pseudocode):

| Algorithm | Focus Area | Mathematical Essence | Silicon Property |
| :--- | :--- | :--- | :--- |
| **Algorithm 1** | Parameterized Circular Line Buffering | $ptr_{\text{wr}} = t \pmod W$, $ptr_{\text{rd}} = (t+1) \pmod W$ | 2 Line Buffers, $0.0\text{ GB/s}$ DRAM |
| **Algorithm 2** | Shift-and-Add Hardware Stem | $\mathbf{T}_{\text{HW}} = \{Y_{\text{linear}}, \|G_x\|, \|G_y\|, \|R-G\|\}$ | Zero DSP Multipliers |
| **Algorithm 3** | Batch Normalization Weight Folding | $W_{\text{fold}} = W \cdot \frac{\gamma}{\sqrt{\sigma^2 + \epsilon}}$, $b_{\text{fold}} = (b - \mu)\frac{\gamma}{\sqrt{\sigma^2 + \epsilon}} + \beta$ | Zero runtime normalization latency |
| **Algorithm 4** | Streaming Attention Pooling | $\alpha_{i,j} = \text{Softmax}(e_{i,j})$, $\mathbf{v}_{\text{fused}} = [\mathbf{v}_{\text{attn}} \parallel \mathbf{v}_{\text{max}}]$ | $+6.0\%$ micro-crack recall |
| **Algorithm 5** | De-ISP Sensor Inversion Pipeline | $\mathbf{I}_{\text{lin}} = (\mathbf{I}_{\text{sRGB}})^{2.4} \to \mathbf{M}_{\text{RGB}\to\text{CAM}} \mathbf{I}_{\text{lin}} \to \text{Bayer}$ | Physically grounded sensor simulation |

---

## 8. Bibliographic Citation

```bibtex
@inproceedings{kolekar2026unified,
  title={Unified Streaming Vision Architecture: Structural Co-Design of Line-Buffered ISP and Early Convolutional Feature Stem with Autonomous Sensor Feedback},
  author={Kolekar, Maneesh S. and Nandi, Sukumar},
  booktitle={Undergraduate Capstone Project (BTP Phase 1), Department of Computer Science and Engineering, Indian Institute of Technology Guwahati},
  year={2026}
}
```
