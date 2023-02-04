# Mixed-signal PD Research Program
# WEEK 0
## Day 1: 
## Open source tool installation
### How to install EDA tools for IC design and simulations?

**Components of IC design flow (RTL2GDS):**
1. Logic synthesis: Converts RTL netlist into synthesized gate level netlist.
   - Tool used : Yosys
   - Yosys not only takes RTL but also timing libs.
 ![image](https://user-images.githubusercontent.com/123575472/216769865-836318e9-893e-4fd1-8e8b-342ec6e895a0.png)
2. Floorplan : We do place preplaced cells and perfom powerplanning.
3. Placement :In this step we place physical view of logical cells that we get from synthesis.
4. CTS : Routes the clock to get skew that is specified by the design.
   - Tool used for 2,3,4 (pnr): Graywolf
 ![image](https://user-images.githubusercontent.com/123575472/216771311-f6777699-d090-4cab-9fa0-e539dc5b482f.png)
5. Routing : Routes all the components placed in placement stage.(e.g. Maze routing)
 ![image](https://user-images.githubusercontent.com/123575472/216771643-79112f8a-f938-4566-b91d-c3d77a4e5da7.png)
6. STA: This is the common step perfomed at every stage (2,3,4,5).
   - Tool: Open timer
 ![image](https://user-images.githubusercontent.com/123575472/216771845-b7c984e6-33b3-465b-81b3-490c37886124.png)

 
