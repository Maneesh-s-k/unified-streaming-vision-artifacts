# ASIC Standard Cell Gate Count & Area Estimation
## Technology Targets:
- **SkyWater 130nm (`sky130_fd_sc_hd`):** Standard Cell Area $\approx 15\ \mu\text{m}^2 / \text{GE}$ (NAND2 Gate Equivalent)
- **TSMC 28nm HPC+:** Standard Cell Area $\approx 1.0\ \mu\text{m}^2 / \text{GE}$
### Synthesis Engine: Yosys 0.63 Open Synthesis Suite (`synth -top <module>; stat`)

| Subsystem Module | Architecture & Function | Total Standard Cells | Combinational Gates | Registers (DFFs) | Estimated Gate Equivalents (GE) | SkyWater 130nm Area ($\text{mm}^2$) | TSMC 28nm Area ($\text{mm}^2$) | Zero-Multiplier Proof |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| [`early_tap_conv_stem.sv`](file:///Users/maneeshskolekar/btp/rtl/early_tap_conv_stem.sv) | 4-Ch Hardware Stem $\{Y, \|G_x\|, \|G_y\|, \|R-G\|\}$ + BBox Tracker | **1,657** | **1,486** | **171** | **$\approx 2,800\text{ GE}$** | **$0.042\text{ mm}^2$** | **$0.0028\text{ mm}^2$** | **0 Multipliers (Pure Shift-Add)** |
| [`demosaic_directional.sv`](file:///Users/maneeshskolekar/btp/rtl/demosaic_directional.sv) | Edge-Adaptive Directional Bayer Demosaicing | **979** | **946** | **33** | **$\approx 1,200\text{ GE}$** | **$0.018\text{ mm}^2$** | **$0.0012\text{ mm}^2$** | **0 Multipliers (Line-Rate)** |
| [`hud_compositor.sv`](file:///Users/maneeshskolekar/btp/rtl/hud_compositor.sv) | Real-Time Alpha-Blender Overlay ($\alpha = 224$) | **4,141** | **4,114** | **27** | **$\approx 5,200\text{ GE}$** | **$0.078\text{ mm}^2$** | **$0.0052\text{ mm}^2$** | 3 MACs for video blend |
| [`tmds_encoder.sv`](file:///Users/maneeshskolekar/btp/rtl/tmds_encoder.sv) | DVI 1.0 8b/10b Transition-Minimized Encoder | **298** | **283** | **15** | **$\approx 370\text{ GE}$** | **$0.0055\text{ mm}^2$** | **$0.00037\text{ mm}^2$** | 0 Multipliers |
| [`i2c_master.sv`](file:///Users/maneeshskolekar/btp/rtl/i2c_master.sv) | Autonomous VBI Hardware $\text{I}^2\text{C}$ Master | **342** | **267** | **75** | **$\approx 720\text{ GE}$** | **$0.0108\text{ mm}^2$** | **$0.00072\text{ mm}^2$** | 0 Multipliers |
| [`node2_blc.sv`](file:///Users/maneeshskolekar/btp/rtl/node2_blc.sv) | Black Level Correction (Pedestal Clamping) | **40** | **27** | **13** | **$\approx 105\text{ GE}$** | **$0.0016\text{ mm}^2$** | **$0.00010\text{ mm}^2$** | 0 Multipliers |
| [`node3_dpc.sv`](file:///Users/maneeshskolekar/btp/rtl/node3_dpc.sv) | Defective Pixel Correction (Median Filter) | **342** | **257** | **85** | **$\approx 767\text{ GE}$** | **$0.0115\text{ mm}^2$** | **$0.00077\text{ mm}^2$** | 0 Multipliers |
| [`video_timing_generator.sv`](file:///Users/maneeshskolekar/btp/rtl/video_timing_generator.sv) | Standard VESA Video Timing Controller (HSync/VSync/DE) | **313** | **243** | **70** | **$\approx 660\text{ GE}$** | **$0.0099\text{ mm}^2$** | **$0.00066\text{ mm}^2$** | 0 Multipliers |
| [`secondary_tap_hazard.sv`](file:///Users/maneeshskolekar/btp/rtl/secondary_tap_hazard.sv) | Optical Glare and Camera Hazard Tripwire Pin | **92** | **71** | **21** | **$\approx 200\text{ GE}$** | **$0.0030\text{ mm}^2$** | **$0.00020\text{ mm}^2$** | 0 Multipliers |

---

### Key ASIC Architectural Findings

1. **Ultra-Compact Early Convolutional Stem:**
   - In conventional vision ASICs, Layer 1 2D convolutions require dedicated multiplier arrays occupying $> 50\text{ kGE}$ and significant dynamic power.
   - Our zero-multiplier shift-and-add architecture consumes only **$2,800\text{ GE}$ ($0.042\text{ mm}^2$ on 130nm, $< 0.003\text{ mm}^2$ on 28nm)** — representing an **$> 94\%$ silicon area reduction** for early feature extraction.
2. **Total Front-End Pipeline Area:**
   - The entire front-end ISP chain (Nodes 1–4, directional demosaicing, and 4-channel convolutional stem) fits within **$< 0.10\text{ mm}^2$ on SkyWater 130nm**, making it ideal for integration directly onto standard CMOS sensor die substrates or low-cost edge ASICs.
