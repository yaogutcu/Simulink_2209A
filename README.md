# TÜBİTAK 2209-A: Active Battery Balancing System

This project was initiated by **Yahya Ahmet Öğütcü** under the **TÜBİTAK 2209-A University Students Research Projects Support Program**, with the primary goal of designing a novel and highly efficient active battery balancing topology. 

Following a comprehensive literature review, three distinct active balancing topologies were selected for detailed analysis and comparison: Single-Tiered Switched Capacitor, Double-Tiered Switched Capacitor, and Single-Tiered Switched Inductor. The initial phase of the project focuses on modeling and evaluating these topologies using MATLAB/Simulink.

---

##  Simulated Topologies (Phase 1)

### 1. Single-Tiered Switched Capacitor
This topology stands out for its simplicity in control and cost-effectiveness. However, its primary drawback is the extended balancing time, as the energy transfer rate is strictly limited by the capacity of a single capacitor moving charge only between adjacent cells.

![Single Tiered Switched Capacitor](Part1_Figures/Figure1_Single%20Tiered%20Switched%20Capacitor%20Simulink%20SS.png)

### 2. Double-Tiered Switched Capacitor
To overcome the limitations of the single-tiered approach, the double-tiered topology was implemented. This architecture allows for energy transfer not just between adjacent neighbors, but also between non-adjacent cells. As a result, it significantly reduces the overall balancing time, offering a clear advantage over the single-switched method.

![Double Tiered Switched Capacitor](Part1_Figures/Figure2_Double%20Tiered%20Switched%20Capacitor%20Simulink%20SS.png)

### 3. Single-Tiered Switched Inductor
The switched-inductor topology offers the fastest balancing time among the three. However, this speed comes at a cost: inductors inherently suffer from higher energy dissipation compared to capacitors. These increased energy losses can render the overall system less efficient, making thermal management and efficiency a challenge.

![Single Tiered Switched Inductor](Part1_Figures/Figure3_Single%20Tiered%20Switched%20Inductor%20Simulink%20SS.png)
