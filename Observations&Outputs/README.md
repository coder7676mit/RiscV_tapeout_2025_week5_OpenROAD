## OpenROAD Flow

### 🧩 Major Stages in the OpenROAD Flow

| Stage | Description | Output |
|--------|--------------|---------|
| *1. Synthesis* | Converts RTL (Verilog) into a gate-level netlist using logic synthesis tools (e.g., Yosys). | netlist.v |
| *2. Floorplanning* | Defines chip *die area, **core area, and **I/O pin* locations; sets up *power grid* and *placement rows*. | floorplan.def |
| *3. Placement* | Arranges standard cells within the core area to minimize wirelength and congestion. | placement.def |
| *4. Clock Tree Synthesis (CTS)* | Inserts buffers and inverters to distribute the clock signal uniformly with minimal skew. | cts.def |
| *5. Routing* | Connects all signal and clock nets using metal layers while avoiding design rule violations (DRC). | route.def |
| *6. Optimization* | Performs timing, power, and area optimizations post-route to ensure closure. | Updated .def & reports |
| *7. GDSII Generation* | Exports final *GDSII* file for fabrication after all checks are clean. | final.gds |


##### Glimpses of the flow.tcl file

![alt](flow.tcl.png)


![alt](flow_tcl2.png)


---

### 🧱 Floorplan and Placement in OpenROAD

After successfully setting up OpenROAD, the next steps involve performing *Floorplanning* and *Placement*.  
These are the initial stages of physical design where the logical netlist is translated into a preliminary physical layout.


### ⚙️ 1. Floorplanning Stage

*Purpose:*  
Floorplanning defines the physical boundaries of the chip — determining the *die area, **core area, **I/O pin locations, and **power grid structure*.

*Key Operations Performed:*
- Define chip size and aspect ratio.  
- Set *core utilization* (typically 60–70%).  
- Place I/O pins around the periphery.  
- Generate *power rings* and routing tracks.  
- Create a base for placement and routing stages.

*Commands Used:*
```bash
cd OpenROAD-flow-scripts/flow
make DESIGN_CONFIG=./designs/nangate45/gcd/config.mk floorplan
```
![alt](floorplan.png)


![alt](floorplan2.png)

#### Die area

![alt](die.png)


#### Cell Report

![alt](cell_report.png)

---



