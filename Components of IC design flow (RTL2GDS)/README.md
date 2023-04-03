### Components of IC design flow (RTL2GDS):
1. Logic synthesis: Converts RTL netlist into synthesized gate level netlist.
   - Tool used : Yosys
     
     ![image](https://user-images.githubusercontent.com/123575472/216773174-3187b947-de2f-4d97-ae14-03ee67120d0d.png)
2. Floorplan : We do place preplaced cells and perfom powerplanning.
3. Placement :In this step we place physical view of logical cells that we get from synthesis.
4. CTS : Routes the clock to get skew that is specified by the design.
   - Tool used for 2,3,4 (pnr): Graywolf
   ![image](https://user-images.githubusercontent.com/123575472/216773265-0497a5b7-3738-4f70-98a9-87d0670b407b.png)

5. Routing : Routes all the components placed in placement stage.(e.g. Maze routing)
   - Tool : Qrouter
   
   ![image](https://user-images.githubusercontent.com/123575472/216773297-6e1bcd7d-c0b3-4052-855c-890fcafa2efe.png)

6. STA: This is the common step perfomed at every stage of IC design flow.
   - Tool: Open timer = Open-source high performance timing analysis tool.

   ![image](https://user-images.githubusercontent.com/123575472/216773325-5a10f57c-94b4-4b33-8103-f3587559bc4f.png)
   
-  To understand above steps, click [HERE](https://github.com/shakila-12/Physical-design-workshop-using-openlane)

### Necessary EDA tools for IC design :
- **Virtual box :** It is used only for windows user , to install Linux OS.
   - Advantage of installing tools in Linux OS: Tools setup are written based on linux environment. 
- **Magic :** At every stage we can view Layout ,its DRC and routes.Hence ,it is VLSI layout editor,extraction and DRC tool.

  ![image](https://user-images.githubusercontent.com/123575472/216772470-9a139254-48ed-4af1-992b-e50370f2ef06.png)   
- **Ngspice :** It is used for spice simulation and checks impact of parasitics. Also , we can extract netlist and check the diferences present in pre-layout and post-layout spice simulation.(Linear and No-linear analyses can be done).

  ![image](https://user-images.githubusercontent.com/123575472/216772791-deff5888-0045-4d0a-b1ac-18be94e07d0a.png)
     - Note: Synaptic package manager is present in linux ,which contain tool packages .
- **Schematic editor/esim :** Used to edit schematic with complext circuits like 100's of MOSFETs .Used for spice simulation ,analysis and can handle till PCB deisgn.
  
  ![image](https://user-images.githubusercontent.com/123575472/216772868-a4e31003-44ca-4061-b91b-bd6919c0432f.png)
- **Qflow :** Tool chain for complete RTL2GDS flow.
