# TÜBİTAK 2209-A: Active Battery Balancing System
> This project was initiated by **Yahya Ahmet Öğütcü** under the **TÜBİTAK 2209-A University Students Research Projects Support Program**, with the primary goal of designing a novel and highly efficient active battery balancing topology. 
Following a comprehensive literature review, three distinct active balancing topologies were selected for detailed analysis and comparison: Single-Tiered Switched Capacitor, Double-Tiered Switched Capacitor, and Single-Tiered Switched Inductor. The initial phase of the project focuses on modeling and evaluating these topologies using MATLAB/Simulink.
---
## Phase 1: Simulated Topologies
### 1. Single-Tiered Switched Capacitor
This topology stands out for its simplicity in control and cost-effectiveness. However, its primary drawback is the extended balancing time, as the energy transfer rate is strictly limited by the capacity of a single capacitor moving charge only between adjacent cells.
<p align="center">
  <img src="Part1_Figures/Figure1_Single%20Tiered%20Switched%20Capacitor%20Simulink%20SS.png" alt="Single Tiered Switched Capacitor">
  <br>
  <em><b>Figure 1:</b> Simulink subsystem model of the Single-Tiered Switched Capacitor topology.</em>
</p>
### 2. Double-Tiered Switched Capacitor
To overcome the limitations of the single-tiered approach, the double-tiered topology was implemented. This architecture allows for energy transfer not just between adjacent neighbors, but also between non-adjacent cells. As a result, it significantly reduces the overall balancing time, offering a clear advantage over the single-switched method.
<p align="center">
  <img src="Part1_Figures/Figure2_Double%20Tiered%20Switched%20Capacitor%20Simulink%20SS.png" alt="Double Tiered Switched Capacitor">
  <br>
  <em><b>Figure 2:</b> Simulink subsystem model of the Double-Tiered Switched Capacitor topology.</em>
</p>
### 3. Single-Tiered Switched Inductor
The switched-inductor topology offers the fastest balancing time among the three. However, this speed comes at a cost: inductors inherently suffer from higher energy dissipation compared to capacitors. These increased energy losses can render the overall system less efficient, making thermal management and efficiency a challenge.
<p align="center">
  <img src="Part1_Figures/Figure3_Single%20Tiered%20Switched%20Inductor%20Simulink%20SS.png" alt="Single Tiered Switched Inductor">
  <br>
  <em><b>Figure 3:</b> Simulink subsystem model of the Single-Tiered Switched Inductor topology.</em>
</p>
---
## Phase 2: Topology Selection & Battery Modeling
Based on the preliminary analysis, the **Double-Tiered Switched Capacitor (DTSC)** topology was selected for further development due to its superior design flexibility and high potential for scalability.
Following the topology selection, research was conducted on State of Charge (SoC) and State of Health (SoH) estimation techniques. Given the high complexity of accurate SoH estimation, it was excluded from the current scope of this project. To estimate the SoC accurately, the **2nd-Order Equivalent Circuit Model (ECM)** was selected among various methods. The dynamic parameters for this model were derived from Arzu Türksoy's doctoral thesis, which enabled the creation of a highly precise battery cell model in MATLAB/Simulink.
<p align="center">
  <img src="Part2_Figures/Figure1_Current%20Path.png" alt="Current Path Simulation">
  <br>
  <em><b>Figure 1:</b> Internal current path simulation and parameters of the battery model.</em>
</p>
Once the accurate battery model was established, the focus shifted to the control logic of the DTSC topology. The control mechanism is intentionally straightforward but highly effective: it operates by driving the upper and lower balancing switches at a fixed **50% duty cycle**.
<p align="center">
  <img src="Part2_Figures/Figure2_Current%20Path.png" alt="Alternative Current Path">
  <br>
  <em><b>Figure 2:</b> Switch activation and alternative current path visualization.</em>
</p>
Finally, by integrating the advanced 2nd-order ECM battery model with the 50% duty cycle DTSC control strategy, full-scale system simulations were executed. The simulation results were then thoroughly analyzed to evaluate the balancing performance and overall energy transfer efficiency across the battery pack.
<p align="center">
  <img src="Part2_Figures/Figure3_Simulation%20Topology.png" alt="Complete Simulation Topology">
  <br>
  <em><b>Figure 3:</b> The complete integrated simulation topology in Simulink.</em>
</p>
---
## Phase 3: Quasi-Resonant Topology & Prototyping
To more easily determine the optimal switching frequency of the DTSC topology, minimize switching losses, and maximize energy transfer efficiency, inductors were added in series with the capacitors. This modification upgrades the design into a **Quasi-Resonant Double-Tiered Switched Capacitor** topology.
<p align="center">
  <img src="Part3_Figures/Figure1_Quasi.png" alt="Quasi-Resonant Topology">
  <br>
  <em><b>Figure 1:</b> Architecture of the Quasi-Resonant Double-Tiered Switched Capacitor.</em>
</p>
After determining the optimal circuit parameters, the system was simulated for a highly unbalanced scenario where the initial states were **SoC1 > SoC2 > SoC3**. The resulting balancing waveforms successfully demonstrate the dynamic energy transfer between the cells.
<p align="center">
  <img src="Part3_Figures/Figure2_Balancing%20Waves.png" alt="Balancing Waves">
  <br>
  <em><b>Figure 2:</b> Scope outputs showing successful energy transfer and cell balancing over time.</em>
</p>
Because the system operates at a high switching frequency of **50 kHz**, simulating the entire balancing process until full convergence required excessive computational time in Simulink. To resolve this bottleneck, average balancing current data for various SoC states were extracted, and a **reduced-order mathematical model** was designed utilizing data interpolation.
<p align="center">
  <img src="Part3_Figures/Figure3_Reduced%20Model.png" alt="Reduced Order Model">
  <br>
  <em><b>Figure 3:</b> Derivation of the reduced-order mathematical model via interpolation.</em>
</p>
Using this reduced-order model, the total balancing time could be calculated rapidly and accurately through pure mathematical computations, bypassing the need to simulate the high-frequency switching dynamics over long periods. The projected total balancing time is illustrated below.
<p align="center">
  <img src="Part3_Figures/Figure4_Balancing%20Time.png" alt="Total Balancing Time">
  <br>
  <em><b>Figure 4:</b> Total calculated balancing time required for full cell convergence.</em>
</p>
Finally, based on the validated simulation models, the physical prototype of the active balancing circuit was designed and routed using **KiCad**, paving the way for hardware manufacturing and real-world experimental testing.
<p align="center">
  <img src="Part3_Figures/Figure5_Prototype.jpeg" alt="PCB Prototype Design">
  <br>
  <em><b>Figure 5:</b> Final PCB layout and prototype design rendered in KiCad.</em>
</p>
