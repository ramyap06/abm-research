# 🧠 Overall Goal of the Project

The main goal is to build a computer simulation called an **Agent Based Model** that represents how the immune system inside **lymph nodes** reacts to a tumor or to a treatment.  

The project focuses on something called the **abscopal effect**.  

The **abscopal effect** happens when treating one tumor somehow also causes other tumors far away to shrink, even though those were not treated directly.  

Scientists know this effect sometimes happens, but often it fails.  

The project asks one main question:  

**Why does the abscopal effect fail even when tumor antigens are present?**  

The idea is that the problem may not be in the tumor itself but in the **lymph nodes**, which are like control centers of the immune system.  

---

# 🧬 What Is Being Modeled

The model represents **two lymph nodes**.  

One is a **primary lymph node** that is directly connected to the tumor and receives antigen signals.  

The other is a **distant lymph node** that only receives signals that spread through the body.  

The simulation shows how immune cells behave in both places and how their communication might succeed or fail to spread the immune response.  

It focuses on how **dendritic cells** bring antigen to the lymph node, how **T cells** get activated, multiply, become exhausted, or turn into memory cells, and how **cytokines** control these processes.  

---

# ⚙️ What Happens During Each Step of the Simulation

Each time step, or tick, represents a small amount of biological time.  

1. Dendritic cells arrive at the lymph node carrying antigen. After a delay they can activate T cells.  
2. Cytokines at the lymph node make activation stronger or weaker.  
3. T cells change states over time.  
   - They can go from naive to activated.  
   - Activated cells can multiply.  
   - Some become effector cells that attack the tumor.  
   - Some become exhausted and stop working well.  
   - Some become memory cells that stay around for a long time.  
4. A portion of the effector T cells leave the lymph node and go attack the tumor.  

---

# ☢️ Important Cytokines and What They Do

Cytokines are small molecules that cells use to communicate. They tell the immune system when to attack and when to calm down.  

| Cytokine or Molecule | Abbreviation | Simple Explanation |
|-----------------------|--------------|--------------------|
| Type I Interferon | IFN I | A strong alarm signal. It helps dendritic cells get licensed, which means they become able to activate T cells. It is a pro inflammatory signal. |
| Interleukin 12 | IL 12 | A booster signal. It helps activated T cells grow and fight better. |
| Interleukin 10 | IL 10 | A calming signal. It reduces activation and keeps the immune system from overreacting. |
| Transforming Growth Factor Beta | TGF β | Another calming signal. It supports suppression and tolerance. |
| Programmed Death 1 and its partner PD L1 | PD 1 and PD L1 | A checkpoint system that turns off T cells when they are overstimulated. Blocking PD 1 can keep T cells active for longer. |
| Sphingosine 1 Phosphate Receptor 1 | S1P1 | A molecule that controls when T cells can leave the lymph node and travel to the tumor. |

---

# 🧩 Main Biological Agents in the Model

| Agent Type | What It Does |
|-------------|--------------|
| Dendritic Cells | These bring antigen from the tumor to the lymph node. They activate T cells. |
| T Cells | These are the soldiers of the immune system. They start untrained, get activated, attack, may get tired, or turn into memory cells. |

T cells can be in five states.  

1. Naive, meaning they have never seen the antigen.  
2. Activated, meaning they are responding.  
3. Effector, meaning they are ready to kill tumor cells.  
4. Exhausted, meaning they have been stimulated too long and stop working well.  
5. Memory, meaning they stay around for a long time in case the antigen appears again.  

---

# 🧮 Main Parameters You Will See in the Model

| Parameter | What It Represents |
|------------|--------------------|
| dwell_steps | How long dendritic cells stay in the lymph node before they can activate T cells. |
| k_prime | How strongly antigen presentation activates T cells. |
| ctx_ifnI_gain and ctx_il12_gain | How much pro inflammatory cytokines increase activation. |
| ctx_il10_penalty and ctx_tgfb_penalty | How much suppressive cytokines reduce activation. |
| pd1_on and pd1_blockade_strength | Whether checkpoint blockade therapy is used and how effective it is. |
| egress_rate | The rate at which effector T cells leave the lymph node to attack the tumor. |
| homing_primary_bias | The percentage of effector T cells that go back to the original tumor instead of traveling to distant areas. |

---

# 🧠 What the Simulation Measures

The model runs many simulations while changing parameters such as cytokine levels, timing, and spatial patterns.  

It measures:  
- Activation score, showing how strong the immune activation is.  
- Egress percentage, showing how many T cells successfully leave the lymph node.  
- Exhaustion ratio, showing how many activated T cells get burned out.  
- Amplification index, a combined measure of how well the local immune response spreads systemically.  

After collecting data, the team uses methods such as principal component analysis, clustering, and sensitivity analysis to find which conditions lead to success or failure of the immune response.  

---

# 🧭 Simplified Summary

This project is like creating a virtual immune system to find out what makes a local tumor treatment sometimes trigger a full body immune response and why it often fails.  

The simulation models how cells and cytokines interact and how timing, strength, and balance of these signals can make the difference between success and failure of systemic immunity.  