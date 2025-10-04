
# OpenLane

OpenLane is an open-source, automated RTL-to-GDSII flow for digital integrated circuit design.
It’s built on top of tools like:
- Yosys – synthesis
- OpenROAD – floorplanning, placement, CTS, routing
- Magic / KLayout – DRC/LVS checking
- Netgen – LVS
- OpenSTA – static timing analysis

It takes Verilog RTL as input and produces GDSII (the layout file sent for fabrication).

### rvmyth core simulation output

![myth_core_test_wave](images/mythcore_test.png)

### avsdac simulation output

![avsdac_sim_out](images/avsdac_sim.png)

### rvmyth_avsdac Pre-Routing simulation output

![rvmyth_avsdac_interface](images/pre_routing_sim.png)

### rvmyth_avsdac Post-Routing simulation output

![rvmyth_avsdac_interface_after](images/post_routing_sim.png)

### VSDBabySoC Top Module Simulation Output

![BabySoC_top_module_sim](images/Wave%201.jpg)