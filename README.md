# Mixed-signal PD Research Program
# WEEK 0
## Day 1: 
## Open source tool installation
### How to install EDA tools for IC design and simulations?

### Components of IC design flow (RTL2GDS):
1. Logic synthesis: Converts RTL netlist into synthesized gate level netlist.
   - Tool used : Yosys
   - Yosys not only takes RTL but also timing libs.
     
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

### Steps to install open source EDA tools on Ubuntu 20.04:
1. Go to google -> Virtual box -> Downloads -> Windows host -> download and save the file in the driver -> Click on the saved file ,proceed with default steps and install it. 
  ![image](https://user-images.githubusercontent.com/123575472/216793173-636a1c5d-c407-45a5-81f7-4e6be1bfc956.png)
 
2. Go to google -> Linux ubuntu iso -> Click on download link shown over there ->Download ubuntu-20.04.5-desktop-amd64.iso (see alternative downloads ,if wanted version is not present) and save in the same driver.
  - Note: Right click -This PC -> Click on properties -> keep a note on the device specifications like installed RAM , system type. In my case it is : 8GB RAM,64-bit operating system, x64-based processor.
3. Open vitualbox -> Click on NEW.The following image appears.Next, make sure we goahead with atleast 4GB RAM and create virtual harddisk with 50GB.
  
  ![image](https://user-images.githubusercontent.com/123575472/216797280-d88da843-3269-47b4-be26-9886e4bfc00b.png)

4. Choose disk image to the optical drive(it is a pointer to ubuntu iso) as shown below.
  ![image](https://user-images.githubusercontent.com/123575472/216799977-69e2e3e2-b420-4ece-adff-cabe53653bdd.png)

5. Click on START .It starts machine which has Linux OS inside windows.
  
  ![image](https://user-images.githubusercontent.com/123575472/216800125-21172f37-071d-49eb-b522-69f692e91ea6.png)

6. Once the above step is done, the below image appears.Click on Install ubuntu.
  
  ![image](https://user-images.githubusercontent.com/123575472/216800533-29571a01-8991-4aa1-b434-60dbebcd2d16.png)

7. Next ,test the keyboard(English US) and then continue.
 
 ![image](https://user-images.githubusercontent.com/123575472/216800622-9a421ec4-c4fa-43d9-a569-f94455763af3.png)

8. Click on install now
   -  Note: Go with default step as shown in picture.
 
    ![image](https://user-images.githubusercontent.com/123575472/216800851-dae7a929-4648-4c92-a890-b8bdd31a385a.png)

9. Fill the user name ,password details and click on continue.It will continues to copy files,download packages and finally installation is complete.
    - Note :we can change the display resolution according to our available screen.
### Setup ubuntu ,Launch terminal and install git:
- Reference for the below steps are taken from [here](https://github.com/kunalg123/vsdflow)

- **Steps to install and run on UBUNTU:**

1) sudo apt-get install git
  ![image](https://user-images.githubusercontent.com/123575472/216808664-0e9ebc04-d999-467a-9378-70c4b043c98c.png)

  - sudo => To run cmd as a administrator(user"root")  use this cmd.
  - apt-get => get the packages from the command line .
  - install => is used to install packages by name.
2) git clone https://github.com/kunalg123/vsdflow.git
3) cd vsdflow
4) chmod 777 opensource_eda_tool_install.sh
5) ./opensource_eda_tool_install.sh 
**NOTE for freshers : This has been tested on a fresh UBUNTU installtion
**NOTE for experienced UNIX users : It has lot of sudo apt-get and sudo remove commands, so you might want to review before running
6) ./vsdflow spi_slave_design_details.csv
7) ./vsdflow picorv32_design_details.csv



 
