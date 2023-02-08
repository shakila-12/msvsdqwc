# Mixed-signal PD Research Program
# WEEK 0
## Day 1:  Open source tool installation
### How to install EDA tools for IC design and simulations?

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

### Steps to install Ubuntu 20.04:
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

### Steps to install open source EDA tools on Ubuntu 20.04:

1) sudo apt-get install git 
 
 ![image](https://user-images.githubusercontent.com/123575472/216808664-0e9ebc04-d999-467a-9378-70c4b043c98c.png)
 ```
  - sudo => To run cmd as a administrator(user"root")  we use this cmd.
  - apt-get => get the packages from the command line .
  - install => is used to install packages by name.
  - df => report file system disk space usage
  - -k => represents like block-size=1K
  - -h =>print sizes in human readable format (e.g., 1K 234M 2G)
 ```
 ## Day-2 : Install magic and SKY130 PDKs
 - Reference taken from [chapter 0 of PV GitHub repo](https://github.com/yathAg/Physical_Verification_SKY130A#Chapter-0---Getting-the-tools)
 - To know about Magic Layout tool, click [this](http://opencircuitdesign.com/magic/)
 - **Magic Installation steps:**
 
 ```
$  git clone git://opencircuitdesign.com/magic
$  cd magic
$	./configure
$  make
$  sudo make install
```
  ![image](https://user-images.githubusercontent.com/123575472/216885988-7d58dad5-6dd0-4e54-a720-e513323405e3.png)
  ![image](https://user-images.githubusercontent.com/123575472/216886142-e2f25aac-a1cc-46c5-bdcb-d18c1db26f38.png)
  
      ```
     The above error is due to missing C compiler . So, check whether compiler is installed or not.For that ,use the below command.
                   - $ gcc --version
                   - If no gcc, install it using  :$ sudo apt-get install gcc
                   - After this ,run the command i.e  $sudo apt-get install build-essential ``` 
  
 To know about this build-essential , click[here](https://itslinuxfoss.com/build-essential-package-ubuntu-install/#1).
                 
  
 ![image](https://user-images.githubusercontent.com/123575472/216886246-b134582a-e9b0-4b38-ac9f-1e1e7ceb2010.png)
 ![image](https://user-images.githubusercontent.com/123575472/216886393-568189b9-b74d-4500-97bd-ef842930e618.png)
 ![image](https://user-images.githubusercontent.com/123575472/216886475-15fe6b3b-8b56-45f5-9217-efdf1ffc6bcb.png)
 ![image](https://user-images.githubusercontent.com/123575472/216886597-f9e362cb-9f89-497c-859e-27fb9fddbe91.png)

- Again run ./configure 
 
  ![image](https://user-images.githubusercontent.com/123575472/216887242-12d340ea-b2f4-43ca-9872-2f6b09d0e005.png)
  ![image](https://user-images.githubusercontent.com/123575472/216889318-71898337-608a-46a7-bea1-d413e6a42085.png)
  ![image](https://user-images.githubusercontent.com/123575472/217119455-3788454e-b5b2-4878-9ef0-53a5af23abe1.png)
   To fix the above error ,i tried  to remove the directory as shown below and hence it worked.
   
   ![image](https://user-images.githubusercontent.com/123575472/217120672-bd013840-ee4e-4dd0-8f6a-d6d680fbef4a.png)
  ```
   sudo rm -rf /var/cache/apt/archives/
   sudo apt-get install libx11-dev
   sudo apt-get install freeglut3-dev
   sudo apt-get install libcairo2-dev
   (Note: Cairo is a multi-platform library providing anti-aliased vector-based rendering for multiple target backends.
     This package contains the development libraries, header files needed by programs that want to compile with Cairo.)
   sudo apt-get install tcl-dev
   sudo apt-get install tk-dev
   sudo apt-get install libxi-dev
  ```

![image](https://user-images.githubusercontent.com/123575472/217154080-eb2ff8d3-91f8-49b6-a5d4-4aaa8c52c0fc.png)

The above commands are used to fix some errors and then follow below commands.
                                
                                $ make 
                                $sudo make install
                                $magic gui 
                              
 ![image](https://user-images.githubusercontent.com/123575472/217190892-a8679fd5-4bcc-423e-99e2-ed320310aff5.png)
                             
 Thus ,Magic is installed.
![image](https://user-images.githubusercontent.com/123575472/217474536-0edbab43-3d6a-447d-861f-ea53511e9c08.png)


![image](https://user-images.githubusercontent.com/123575472/217480454-d7bb42c3-464e-4799-a0bc-53b1c1214a6b.png)

git clone https://github.com/StefanSchippers/xschem.git xschem-src
cd xschem-src/
 ./configure
 sudo apt-get install flex
     sudo apt-get install bison
   sudo apt-get install libxpm-dev
   sudo apt-get install libx11-xcb-dev 
sudo apt-get install libx11-6
   ./configure 
    make
    sudo make install
    xschem gui


![image](https://user-images.githubusercontent.com/123575472/217491023-f412d212-a73f-40cb-ab08-61715a99b820.png)

- **ngspice**:

learn tar from [here](https://linuxhint.com/linux-tar-command/)

mv /home/shakila12/Downloads/ngspice-39 /home/shakila12/Desktop/pd_rp/tools

![image](https://user-images.githubusercontent.com/123575472/217505868-9e7b5373-9dd0-4206-bf0b-a0538509d99c.png)

sudo apt-get install libxaw7-dev
