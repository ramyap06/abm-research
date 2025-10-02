# 🎯 Overall Project Goals

The big picture is to use **agent-based modeling (ABM)** to understand why the **abscopal effect** (systemic immune response after local tumor therapy) often fails, even when tumor antigens are present.

- Reframe the **tumor-draining lymph node (tdLN)** as the decision point.  
- Explore **four mechanistic gates of failure**:  
  1. Threshold (too few licensed DCs)  
  2. Temporal misalignment (IFN-I vs DC arrival)  
  3. Spatial bias (FRC topology effects)  
  4. Checkpoint dominance (PD-1/PD-L1 exhaustion)  
- Perform **factorial & sampling experiments** (972 possible conditions → reduced via LHS).  
- Quantify **raw outputs** (T cell counts, cytokines, exhaustion, egress, contact metrics).  
- Derive **composite features** (amplification index, licensing efficiency, checkpoint pressure, etc.).  
- Identify **transition zones and bifurcation points** where immune success flips to failure.  
- Ultimately: Map conditions → endpoints (abscopal success vs failure, systemic potency score).  

---

# 💻 Software Goals (Green = Data/Analysis Pipelines)

These are the computational objectives you’ll implement in code.

1. **Sampling**
   - Latin Hypercube Sampling (LHS) to efficiently select parameter sets.  
   - Split into **Block A (Licensing ON)** and **Block B (Licensing OFF)**.  
   - Generate JSON configs for ABM runs from YAML templates.  

2. **YAML → JSON Conversion**
   - Parse `blockA.yaml`, `blockB.yaml`, and `block*_highvar.yaml`.  
   - Output run configs like:  
     ```
     configs/LN_ABM_BlockA_empirical_A_sample000_rep1.json
     ```
   - Automate replication structure (3 replicates in phase 1, 16 for high-variance points).  

3. **Feature Extraction**
   - From raw HDF5/CSV logs, extract:  
     - Primary features (T cell counts, cytokine dynamics, exhaustion ratio).  
     - Derived composite features (amplification index, licensing efficiency, checkpoint pressure).  
   - Store results in structured CSV files.  

4. **High-Variance Detection**
   - For each parameter point: compute **mean + SD** of replicates.  
   - Flag points with high variance → trigger Phase 2 (16 replicates).  
   - Link flagged points back to configs for reruns.