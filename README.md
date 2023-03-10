# VSD Mixed-signal PD Research Program
# WEEK 0
## Open source tool installation
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
    
### STEPS TO INSTALL OPEN SOURCE EDA TOOLS ON UBUNTU 20.04:
- Reference taken from [1.chapter 0 of PV GitHub repo](https://github.com/yathAg/Physical_Verification_SKY130A#Chapter-0---Getting-the-tools) and [2](https://github.com/sanampudig/OpenFASoC/tree/main/AUXCELL)
- **Install git**: git is a free and open-source distributed version control system used to handle  projects efficiently.

   $ sudo apt-get install git 
 
 ![image](https://user-images.githubusercontent.com/123575472/216808664-0e9ebc04-d999-467a-9378-70c4b043c98c.png)
 ```
  - sudo => To run cmd as a administrator(user"root")  we use this cmd.
  - apt-get => get the packages from the command line .
  - install => is used to install packages by name.
  - df => report file system disk space usage
  - -k => represents like block-size=1K
  - -h =>print sizes in human readable format (e.g., 1K 234M 2G)
 ```
## Magic 
 - To know about Magic Layout tool, click [this](http://opencircuitdesign.com/magic/)
 - **Installation steps:**
 
 ```
$  git clone git://opencircuitdesign.com/magic
$  cd magic
$ ./configure
$ make
$ sudo make install
$ magic gui 
```
  ![image](https://user-images.githubusercontent.com/123575472/216885988-7d58dad5-6dd0-4e54-a720-e513323405e3.png)
  ![image](https://user-images.githubusercontent.com/123575472/216886142-e2f25aac-a1cc-46c5-bdcb-d18c1db26f38.png)
  
      ```
     The above error is due to missing C compiler . So, check whether compiler is installed or not.For that ,use the below command.
                   - $ gcc --version
                   - If no gcc, install it using  :$ sudo apt-get install gcc
                   - After this ,run the command i.e  $sudo apt-get install build-essential 
                   ``` 
 
                 
 ![image](https://user-images.githubusercontent.com/123575472/216886246-b134582a-e9b0-4b38-ac9f-1e1e7ceb2010.png)
 ![image](https://user-images.githubusercontent.com/123575472/216886393-568189b9-b74d-4500-97bd-ef842930e618.png)
 ![image](https://user-images.githubusercontent.com/123575472/216886475-15fe6b3b-8b56-45f5-9217-efdf1ffc6bcb.png)
 ![csh](https://user-images.githubusercontent.com/123575472/218288607-fa2f9ee0-8a8e-4b2b-aa9c-8f85ab3cc0b9.png)

- Again run ./configure 
 
  ![image](https://user-images.githubusercontent.com/123575472/216887242-12d340ea-b2f4-43ca-9872-2f6b09d0e005.png)
  ![image](https://user-images.githubusercontent.com/123575472/217119455-3788454e-b5b2-4878-9ef0-53a5af23abe1.png)
   To fix the above error ,i tried  to remove the directory as shown below and hence it worked.
   
   ![image](https://user-images.githubusercontent.com/123575472/217120672-bd013840-ee4e-4dd0-8f6a-d6d680fbef4a.png)
  ```
   sudo rm -rf /var/cache/apt/archives/
   
  # Packages required to compile magic:
   $ sudo apt-get install m4
   $ sudo apt-get install tcsh
   $ sudo apt-get install csh
   $  sudo apt-get install libx11-dev
   $ sudo apt-get install freeglut3-dev
   $ sudo apt-get install libcairo2-dev
   $ sudo apt-get install tcl-dev
   $ sudo apt-get install tk-dev
   $ sudo apt-get install mesa-common-dev libglu1-mesa-dev
   $ sudo apt-get install libncurses-dev
   
  ```

![image](https://user-images.githubusercontent.com/123575472/217154080-eb2ff8d3-91f8-49b6-a5d4-4aaa8c52c0fc.png)
                                                          
![image](https://user-images.githubusercontent.com/123575472/217190892-a8679fd5-4bcc-423e-99e2-ed320310aff5.png)
                             
 Thus ,Magic is installed.
 
## Netgen

Visit the website for the [info](http://opencircuitdesign.com/netgen/index.html)
- ** Steps to install**:
```
 $  git clone git://opencircuitdesign.com/netgen
 $  cd netgen
 $ ./configure
 $  make
 $  sudo make install
```
![image](https://user-images.githubusercontent.com/123575472/217474536-0edbab43-3d6a-447d-861f-ea53511e9c08.png)


- Note: A similar behaviour can be replicated in magic as well as netgen by appending the respective open commands with -noconsole . Magic can even be run with no graphics by using [magic -dnull -noconsole]  and this mode of calling magic is especially used when running magic from a script. Refer this [repo](https://github.com/Avnish21/VSD-Physical-Verification-Using-Sky130/blob/main/README.md)
## Xschem


- **steps**:
   ```
    $ git clone https://github.com/StefanSchippers/xschem.git xschem-git
    $ cd xschem-git
    $ ./configure 
    $ make
    $ sudo make install
    $ xschem gui
   ```

![image](https://user-images.githubusercontent.com/123575472/217491023-f412d212-a73f-40cb-ab08-61715a99b820.png)
![image](https://user-images.githubusercontent.com/123575472/217480454-d7bb42c3-464e-4799-a0bc-53b1c1214a6b.png)

```
  $ sudo apt-get install flex
    $ sudo apt-get install bison
    $ sudo apt-get install libxpm-dev
    $ sudo apt-get install libx11-xcb-dev 
    $ sudo apt-get install libx11-6
 ```

## Ngspice:

Install steps:

After downloading the [tarball](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/old-releases/37/ngspice-37.tar.gz/download),extract it using below command and  also see the [manual](https://ngspice.sourceforge.io/ngspice-tutorial.html#downloadl) for instructions on compilation and installation of ngspice. 

```
 $ tar -zxvf ngspice-37.tar.gz            
 $ cd ngspice-37
 $ mkdir release
 $ cd release
 $ ../configure  --with-x --with-readline=yes --disable-debug 
 $ make
 $ sudo make install
 
```
![image](https://user-images.githubusercontent.com/123575472/217505868-9e7b5373-9dd0-4206-bf0b-a0538509d99c.png)

            ## Package dependencies shown below##
            $ sudo apt-get install libxaw7-dev
            $ apt-cache search readline (#used to look at the available libraries )
            $ sudo apt-get install libreadline8 libreadline-dev
            $ sudo apt-get update
            # to view simulation graphs
            $ sudo apt-get install xterm
 




## Open_PDK

Open_PDKs is distributed with files that support the Google/SkyWater sky130 open process description https://github.com/google/skywater-pdk. Open_PDKs will set up an environment for using the SkyWater sky130 process with open-source EDA tools and tool flows such as magic, qflow, openlane, netgen, klayout, etc.

Install steps:

```
$  git clone git://opencircuitdesign.com/open_pdks
$  open_pdks
$	./configure --enable-sky130-pdk
$  make
$  sudo make install

```

-**Note:**
- sudo make doesnot installed complete openpdk, so make distclean and sudo make uninstall. Then just run make. It uses around 80 gb.So,make sure, we have  around 150gb free space of drives
- For PDK manual installation ,reference to be the taken is given in  two links:
                 [link1](http://www.opencircuitdesign.com/open_pdks/install.html),
                 [link2](https://lootr5858.wordpress.com/2020/10/06/magic-vlsi-skywater-pdk-local-installation-guide/)

### Verifiying the open_pdk installation:
![image](https://user-images.githubusercontent.com/123575472/218292058-a580280d-5512-4406-8b51-b7761f997288.png)
![image](https://user-images.githubusercontent.com/123575472/218291924-7ccc8bd3-5965-44db-99f9-0ef28df726e6.png)
![image](https://user-images.githubusercontent.com/123575472/218292168-69c78a35-a972-4a76-bae1-0d0765bc0cf2.png)
![image](https://user-images.githubusercontent.com/123575472/218292250-53f731be-8347-4dd2-a193-324dca33c87e.png)



## ALIGN

To understand the flow, refer the following [repo,](https://github.com/sanampudig/OpenFASoC/tree/main/AUXCELL) and its [website](https://align-analoglayout.github.io/ALIGN-public/index.html)
      
**Steps followed to install ALIGN tool:**
- Prerequisites

gcc >= 6.1.0 (For C++14 support)
python >= 3.7
```
For Faster Installation ALIGN

sudo apt update
sudo apt install lp-solve
sudo apt-get install libboost-all-dev
export CC=/usr/bin/gcc
export CXX=/usr/bin/g++

git clone https://github.com/ALIGN-analoglayout/ALIGN-public
cd ALIGN-public
#Create a Python virtualenv
python -m venv general
source general/bin/activate
python -m pip install pip --upgrade

# Install ALIGN as a USER
pip install -v .
# Install ALIGN as a DEVELOPER
pip install -e .

pip install setuptools wheel pybind11 scikit-build cmake ninja
pip install -v -e .[test] --no-build-isolation
pip install -v --no-build-isolation -e . --no-deps --install-option='-DBUILD_TESTING=ON'
```
- **Making ALIGN Portable to Sky130 tehnology:**
Clone the following Repository inside ALIGN-public directory
```
git clone https://github.com/ALIGN-analoglayout/ALIGN-pdk-sky130

move SKY130_PDK folder to /ALIGN-public/pdks
```
- **Running ALIGN TOOL**
Everytime we start running tool in new terminal run following commands.
```
python -m venv general
source general/bin/activate
```
- Commands to run ALIGN (goto ALIGN-public directory)
```
mkdir work
cd work
```
- **General syntax to give inputs**
```
schematic2layout.py <NETLIST_DIR> -p <PDK_DIR> -c
Running a EXAMPLE:

schematic2layout.py ../examples/telescopic_ota -p ../pdks/FinFET14nm_Mock_PDK/
Running a EXAMPLE on Sky130pdk

schematic2layout.py ../ALIGN-pdk-sky130/examples/five_transistor_ota -p ../pdks/SKY130_PDK/
```
![image](https://user-images.githubusercontent.com/123575472/221388152-991e78ea-56b0-44ab-bd03-b6328e7d0512.png)
![image](https://user-images.githubusercontent.com/123575472/221388314-6dc477f4-9fad-4e5b-8957-6f671f30c04a.png)


  ---------------------------------------------------------------------------------------------------------------------------------------------------------


### TASK: CREATE INVERTER AND PERFORM PRE-LAYOUT,POST-LAYOUT EXPERIMENT USING XCSHEM /NGSPICE ,MAGIC
### Pre-layout :
### Inverter schematic using xschem:




![image](https://user-images.githubusercontent.com/123575472/218880868-8044f410-1772-4498-8445-52793e1511d3.png)

![image](https://user-images.githubusercontent.com/123575472/218882340-456db836-e6ea-473a-a9bb-ffcd5a9a959a.png)

![image](https://user-images.githubusercontent.com/123575472/218882628-32991dab-4ea8-4f5d-a8db-44a2aff02496.png)

### DC analysis:

![image](https://user-images.githubusercontent.com/123575472/220120225-8b092da1-8d7a-41d2-b3ec-25e54b191d44.png)

- **Netlist:**
```
** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/invert_dc_tb.sch
**.subckt invert_dc_tb Vin Vout
*.ipin Vin
*.opin Vout
XM1 Vout Vin GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM2 Vout Vin VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
Vdd VDD GND 1.8
.save i(vdd)
Vin Vin GND 0
.save i(vin)
**** begin user architecture code

.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt


.dc Vin 0 1.8 0.01
.save all

**** end user architecture code
**.ends
.GLOBAL GND
.GLOBAL VDD
.end
```


![image](https://user-images.githubusercontent.com/123575472/220120599-15884e0b-54a6-4dca-b244-13d4955ad650.png)
### Transient analysis:-
![image](https://user-images.githubusercontent.com/123575472/220127621-b7498353-1a9d-46f0-996e-e1ddc3e4b312.png)
![image](https://user-images.githubusercontent.com/123575472/220127319-95b4970c-3749-4f6b-9d5b-010bad58b8b5.png)
![image](https://user-images.githubusercontent.com/123575472/220130973-149b1287-3b02-42c1-a585-5b7038ada8ed.png)
- **Rise transition**: Output transition from 20% to 80% [ voltage=1.8v => , 20% of 1.8 is 0.36 and 80%of 1.8 is 1.44 ]

- **Fall transition**: Output transition from 80% to 20%

- **Rise Delay**: delay between 50%(1.8V) of input to 50%(1.8V) of output 

- **Fall Delay**:

**Generated spice netlist:**
```

** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/invert_tran.sch
.subckt invert_tran VDD GND Vin Vout
*.PININFO VDD:B GND:B Vin:I Vout:O
XM1 Vout Vin GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 m=1
XM2 Vout Vin VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 m=1
VDD VDD GND 1.8
.save i(vdd)
Vin Vin GND pulse(0 1.8 1ns 1ns 1ns 4ns 10ns)
.save i(vin)
**** begin user architecture code

.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt


.tran 0.01n 50n
.save all

**** end user architecture code
.ends
.GLOBAL VDD
.GLOBAL GND
.end
````


### Post layout:
**Steps**:
![image](https://user-images.githubusercontent.com/123575472/219266814-75bb3be1-90c2-44f5-af03-6e306d67a6c8.png)
![image](https://user-images.githubusercontent.com/123575472/220135071-e066b976-5862-4ed9-86e5-a00715a24dfc.png)


After importing the generated spice netlist , (go to file ->IMPORT NETLIST ....in layout window)the following image appears..
![image](https://user-images.githubusercontent.com/123575472/220136800-8fb1e4c4-f597-4fb4-8208-36ae237a47bf.png)

- For the steps to import refer [this](https://github.com/Avnish21/VSD-Physical-Verification-Using-Sky130/blob/main/README.md)
- TO  UNDERSTAND THE LAYOUT PROCESS ,REFER https://www.udemy.com/course/vlsi-academy-custom-layout/
     
``` 
Note:  
      1. The below INVERTER layout is drawn , just a  to learn layout diag. and its spice netlist generated from layout is shown.
      2. Note before routing: 
             - In layout window,select the FET, press i and the move to the wanted area. 
              - Select the pin  ->go to edit ->select area ->then move .
      3. The extracted netlist which you get from magic does not contain the control statements(plots, sources, etc). It's just a bare subckt(black box or an IC). You            must add the .control statements(power it) by pasting them from the pre-layout and get a similar output
```      

![image](https://user-images.githubusercontent.com/123575472/220508613-e160800c-c573-4d70-a2c3-5942cbf463b9.png)
![image](https://user-images.githubusercontent.com/123575472/220509920-1043be9d-8b74-476c-b140-0a3411e68877.png)

- **After routing:**
![image](https://user-images.githubusercontent.com/123575472/220532630-77927ded-0bd1-400c-a58c-7bf7ed49dd87.png)
![image](https://user-images.githubusercontent.com/123575472/220580202-a5345892-2565-4ea3-a72a-769e0093b871.png)
![image](https://user-images.githubusercontent.com/123575472/220607657-b7b014d2-76ed-49dc-9c64-ecaa29153517.png)

![image](https://user-images.githubusercontent.com/123575472/220606941-31ac1b40-491e-4418-8ba5-b0d296f3db8f.png)

![image](https://user-images.githubusercontent.com/123575472/220638465-510eef26-8b1b-4b85-999b-2685fca8792d.png)

![image](https://user-images.githubusercontent.com/123575472/220640680-dd631ae8-cb99-486b-afbb-2a1793f4f40c.png)
- **Extracted spice netlist:**
```
* NGSPICE file created from invert_tran.ext - technology: sky130A

.subckt sky130_fd_pr__nfet_01v8_648S5X a_n73_n100# a_n33_n188# a_15_n100# a_n175_n274#
X0 a_15_n100# a_n33_n188# a_n73_n100# a_n175_n274# sky130_fd_pr__nfet_01v8 ad=2.9e+11p pd=2.58e+06u as=2.9e+11p ps=2.58e+06u w=1e+06u l=150000u
C0 a_n33_n188# a_15_n100# 0.03fF
C1 a_n73_n100# a_15_n100# 0.16fF
C2 a_n73_n100# a_n33_n188# 0.03fF
C3 a_15_n100# a_n175_n274# 0.08fF
C4 a_n73_n100# a_n175_n274# 0.11fF
C5 a_n33_n188# a_n175_n274# 0.30fF
.ends

.subckt sky130_fd_pr__pfet_01v8_XGS3BL a_n73_n100# a_15_n100# w_n211_n319# a_n33_n197#
+ VSUBS
X0 a_15_n100# a_n33_n197# a_n73_n100# w_n211_n319# sky130_fd_pr__pfet_01v8 ad=2.9e+11p pd=2.58e+06u as=2.9e+11p ps=2.58e+06u w=1e+06u l=150000u
C0 w_n211_n319# a_15_n100# 0.06fF
C1 w_n211_n319# a_n73_n100# 0.09fF
C2 a_n33_n197# a_15_n100# 0.03fF
C3 a_n33_n197# a_n73_n100# 0.03fF
C4 a_15_n100# a_n73_n100# 0.16fF
C5 a_n33_n197# w_n211_n319# 0.26fF
C6 a_15_n100# VSUBS 0.02fF
C7 a_n73_n100# VSUBS 0.02fF
C8 a_n33_n197# VSUBS 0.05fF
C9 w_n211_n319# VSUBS 1.07fF
.ends

.subckt invert_tran VDD GND Vin Vout
XXM1 GND Vin Vout VSUBS sky130_fd_pr__nfet_01v8_648S5X
XXM2 VDD Vout XM2/w_n211_n319# Vin VSUBS sky130_fd_pr__pfet_01v8_XGS3BL
C0 GND XM2/w_n211_n319# 0.00fF
C1 XM2/w_n211_n319# VDD 0.08fF
C2 Vin Vout 0.06fF
C3 XM2/w_n211_n319# Vout 0.11fF
C4 GND Vout 0.00fF
C5 Vout VDD 0.00fF
C6 Vin XM2/w_n211_n319# 0.13fF
C7 GND Vin 0.11fF
C8 Vin VDD 0.10fF
C9 Vin VSUBS 0.38fF
C10 VDD VSUBS 0.25fF
C11 XM2/w_n211_n319# VSUBS 1.13fF
C12 Vout VSUBS 0.56fF
C13 GND VSUBS 0.38fF
.ends


***pre layout simulation netlist that needs to be included***
** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/invert_tran.sch
**.subckt invert_tran VDD GND Vin Vout
*.iopin VDD
*.iopin GND
*.ipin Vin
*.opin Vout
XM1 Vout Vin GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM2 Vout Vin VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
VDD VDD GND 1.8
.save i(vdd)
Vin Vin GND pulse(0 1.8 1ns 1ns 1ns 4ns 10ns)
.save i(vin)
**** begin user architecture code

.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt


.tran 0.01n 50n
.save all

**** end user architecture code
**.ends
.GLOBAL VDD
.GLOBAL GND
.end
```
![image](https://user-images.githubusercontent.com/123575472/220755714-ca1ea4e9-01a7-41b1-8d87-b8e48cf95484.png)

```
Note: When we compare pre-layout  and postlayout,there is no change in dc analysis. Change is at transient analysis ,because of capacitances that included after layout.
```
![image](https://user-images.githubusercontent.com/123575472/220733708-edf68540-1fd6-46fa-b88a-e10e996841ba.png)

Rise transition:
![image](https://user-images.githubusercontent.com/123575472/220739788-2b7b3faf-36bf-40b6-857f-935b19561e36.png)

fall:![image](https://user-images.githubusercontent.com/123575472/220740085-bd3b52c0-0993-4639-a2f4-7cee0616de93.png)

rise delay :![image](https://user-images.githubusercontent.com/123575472/220740692-2d5164c1-60ea-48e7-811d-4a93e5ea17c3.png)

fall delay: ![image](https://user-images.githubusercontent.com/123575472/220740907-8997b27d-4482-4305-b9c6-8b6cedee2abe.png)
### Comparison of Pre-layout and Post-layout timing parameters:


### LVS report:
Layout Versus Schematic (LVS) verification is the process of determining whether a particular integrated circuit layout corresponds to the original schematic or circuit diagram of the design.

The schematic netlist and layout netlist can be compared using LVS(layout vs schematic) by netgen
```
Format to check LVS: $ netgen -batch lvs "postlayout spice netlist" "prelayout spice netlist"
netgen -batch lvs "../mag/invert_tran.spice" "../xschem/simulation/invert_tran.spice" 

```
![image](https://user-images.githubusercontent.com/123575472/220869667-065c2e32-97a7-4e1c-a78b-54f4e7c7003b.png)

![image](https://user-images.githubusercontent.com/123575472/220842444-9633ab47-3d97-4b3a-9fcf-b56da2d1c775.png)
Note: A small change in names, etc would also give an error. Hence, current cell that is not matching is shown.
To understand all this ,refer http://opencircuitdesign.com/netgen/ .
## Task: To perform simulation of the below function:
### Pre-layout Simulation of the function using Magic and Ngspice :
![image](https://user-images.githubusercontent.com/123575472/220867893-6ebbe148-d81c-4a5a-bd9f-ee46d4f00db3.png)


![image](https://user-images.githubusercontent.com/123575472/220959062-9625b3a2-3447-407c-bdda-ece40df2b05c.png)

***Netlist description***
```
M1 3 a vdd vdd pmos W=2.125u L=0.25u
M2 2 b vdd vdd pmos W=2.125u L=0.25u
M3 4 d 2 2 pmos W=2.125u L=0.25u
M4 4 c 3 3 pmos W=2.125u L=0.25u
M5 out e 4 4 pmos W=2.125u L=0.25u
M6 out f 4 4 pmos W=2.125u L=0.25u

M7 out a 6 6 nmos W=2.125u L=0.25u
M8 out c 6 6 nmos W=2.125u L=0.25u
M9 out e 7 7 nmos W=2.125u L=0.25u
M10 6 b 0 0 nmos W=2.125u L=0.25u
M11 6 d 0 0 nmos W=2.125u L=0.25u
M12 7 f 0 0 nmos W=2.125u L=0.25u

cload out 0 10f

Vdd vdd 0 2.5
V1 a 0 0 pulse 0 2.5 0.1n 10p 10p 1n 2n
V2 b 0 0 pulse 0 2.5 0.2n 10p 10p 1n 2n
V3 c 0 0 pulse 0 2.5 0.3n 10p 10p 1n 2n
V4 d 0 0 pulse 0 2.5 0.4n 10p 10p 1n 2n
V5 e 0 0 pulse 0 2.5 0.5n 10p 10p 1n 2n
V6 f 0 0 pulse 0 2.5 0.6n 10p 10p 1n 2n

***Simulation commands***
.op
.tran 10p 4n

*** .include model file ***
.LIB "my_model_file.tech" CMOS_MODELS
.end
```
![image](https://user-images.githubusercontent.com/123575472/220961944-cf6da65b-0567-4144-9de4-81483334f0c3.png)

### Post-layout Simulation of function  using Magic and Ngspice :

![image](https://user-images.githubusercontent.com/123575472/220975943-a142680c-e755-4416-854d-9bff34450751.png)
**Netlist:**
```
* SPICE3 file created from fn1.ext - technology: min2

.option scale=0.09u

M1000 a_46_38# d a_22_38# vdd pmos w=17 l=2
+  ad=102 pd=46 as=204 ps=92
M1001 out c a_14_9# gnd nmos w=17 l=2
+  ad=204 pd=92 as=204 ps=92
M1002 vdd b a_46_38# vdd pmos w=17 l=2
+  ad=204 pd=92 as=0 ps=0
M1003 gnd f a_30_9# gnd nmos w=17 l=2
+  ad=204 pd=92 as=102 ps=46
M1004 gnd b a_14_9# gnd nmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
M1005 out e a_22_38# vdd pmos w=17 l=2
+  ad=102 pd=46 as=0 ps=0
M1006 a_14_38# a vdd vdd pmos w=17 l=2
+  ad=102 pd=46 as=0 ps=0
M1007 a_14_9# a out gnd nmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
M1008 a_30_9# e out gnd nmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
M1009 a_22_38# f out vdd pmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
M1010 a_22_38# c a_14_38# vdd pmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
M1011 a_14_9# d gnd gnd nmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
C0 a_30_9# gnd 3.37fF 
C1 a_14_9# gnd 6.82fF
C2 out gnd 8.40fF 
C3 a_22_38# gnd 3.02fF 
C4 vdd gnd 9.58fF 

Vdd vdd 0 2.5
V1 a 0 0 pulse 0 2.5 0.1n 10p 10p 1n 2n
V2 b 0 0 pulse 0 2.5 0.2n 10p 10p 1n 2n
V3 c 0 0 pulse 0 2.5 0.3n 10p 10p 1n 2n
V4 d 0 0 pulse 0 2.5 0.4n 10p 10p 1n 2n
V5 e 0 0 pulse 0 2.5 0.5n 10p 10p 1n 2n
V6 f 0 0 pulse 0 2.5 0.6n 10p 10p 1n 2n

***Simulation commands***
.op
.tran 10p 4n

*** .include model file ***
.LIB "my_model_file.tech" CMOS_MODELS
.end
```
![image](https://user-images.githubusercontent.com/123575472/220979528-47ba871e-e2d0-479a-a8de-ed0156a65ea7.png)
### LVS check: 

![image](https://user-images.githubusercontent.com/123575472/221087387-e0392c38-f282-4e98-b314-5ff5f82673b7.png)
Mismatch occurs due to the extracted parasitic capacitances generated in the post layout spice netlist.

![image](https://user-images.githubusercontent.com/123575472/221081045-6c83e6d1-fead-424c-90a8-49183f042dfc.png)

**comp.out report**:

![image](https://user-images.githubusercontent.com/123575472/221086596-a3193dfc-77e1-4416-8a38-1ad1d817d62f.png)
![image](https://user-images.githubusercontent.com/123575472/221086905-cf1cfcc0-763a-41d4-b46a-1a478a7be46a.png)
# WEEK-1
- **Installation of ALIGN is completed( steps are given above).**
- Note: Follow the rules in the below link , which helps to complete the task.
        
        https://docs.google.com/document/d/1RldOLssqc29qNuLmmlAmxlnkeW40NMr4uQ9kXzd2MMI/edit
       
- **Need of ALIGN**:As analog circuits contains trasistors, so for transistor level routing we need this.(Though we know openroad flow does routing but ,this openroad doesnt do transistor level routing).        
### Inverter post-layout characterization using ALIGN tool:
- **steps to be followed**:
```
- 1.Create a build directory in ALIGN-public folder.
  2.Make sure you have the inv_tb.spice file (created from lvs netlist in xschem) in that folder and rename it to .sp (Align reads .sp files) 
        =>set netlist Dir = /home/shakila12/Desktop/pd_rp/tools/ALIGN-public/build/inv/inv.sp
```
![image](https://user-images.githubusercontent.com/123575472/221476694-70929109-4bfb-4c51-a213-d3d3dca5c125.png)
![image](https://user-images.githubusercontent.com/123575472/221496322-494d1baa-2f3e-4eb5-9596-b88ca8dea59a.png)

![image](https://user-images.githubusercontent.com/123575472/221494718-fa3bc040-7690-4f03-9133-e7d9fe32814b.png)

- **.gds in klayout**

![image](https://user-images.githubusercontent.com/123575472/221497058-4e2d5ad4-ce59-4ebd-9a8b-47b4566cf61d.png)
- **.lef in klayout**

 ![image](https://user-images.githubusercontent.com/123575472/221500073-7ca81c1e-8865-4e39-88b8-7637462cacdf.png)

- Now, open the magic (magic -T sky130A.tech) and read GDS file.

   Now, in layout window, go to file->Read GDS ->open the gds file.(Note: if only black box appears, click s(selects top cell in window) and then press x.)
   ![image](https://user-images.githubusercontent.com/123575472/221524653-6287cf76-8542-4237-8f9b-007bf1035bf8.png)
- Extract the netlist using below commands:
  ```
  extract do local
  extract all
  ext2spice cthresh 0 rthresh 0
  ext2spice
  ```
- **Extracted netlist:**
```
  * SPICE3 file created from INV_0.ext - technology: sky130A

X0 VOUT VIN GND GND sky130_fd_pr__nfet_01v8 ad=2.352e+11p pd=2.24e+06u as=4.452e+11p ps=4.42e+06u w=840000u l=150000u
X1 GND VIN VOUT GND sky130_fd_pr__nfet_01v8 ad=0p pd=0u as=0p ps=0u w=840000u l=150000u
X2 VOUT VIN PMOS_S_36030836_X1_Y1_1677500379_0/w_0_0# PMOS_S_36030836_X1_Y1_1677500379_0/w_0_0# sky130_fd_pr__pfet_01v8 ad=2.352e+11p pd=2.24e+06u as=4.452e+11p ps=4.42e+06u w=840000u l=150000u
X3 VIN VOUT PMOS_S_36030836_X1_Y1_1677500379_0/w_0_0# sky130_fd_pr__pfet_01v8 ad=0p pd=0u as=0p ps=0u w=840000u l=150000u
C0 VOUT PMOS_S_36030836_X1_Y1_1677500379_0/w_0_0# 0.83fF
C1 VIN VOUT 0.24fF
C2 VIN PMOS_S_36030836_X1_Y1_1677500379_0/w_0_0# 0.94fF
C3 VIN GND 0.78fF **FLOATING
C4 VOUT GND 0.57fF **FLOATING
C5 PMOS_S_36030836_X1_Y1_1677500379_0/w_0_0# GND 3.26fF **FLOATING

*****simulation added *****

** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/invert_tran.sch
.subckt invert_tran VDD GND Vin Vout
*.PININFO VDD:B GND:B Vin:I Vout:O
XM1 Vout Vin GND GND sky130_fd_pr__nfet_01v8 
XM2 Vout Vin VDD VDD sky130_fd_pr__pfet_01v8 
VDD VDD GND 1.8
.save i(vdd)
Vin Vin GND pulse(0 1.8 1ns 1ns 1ns 4ns 10ns)
.save i(vin)
**** begin user architecture code

.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
.control
run
tran 0.01n 50n
save all
.endc
**** end user architecture code
.ends
.GLOBAL VDD
.GLOBAL GND
.end

```
- Run the netlist: $ngspice INV_0 .txt
- **Output:
![image](https://user-images.githubusercontent.com/123575472/221811232-7688c8d4-ddef-4192-97b2-3a12527b347e.png)

- OBSERVATIONS:
![image](https://user-images.githubusercontent.com/123575472/221825147-4de69073-f4bb-46cb-84ee-a643e6df80a2.png)


## Design the below function using SKY130 PDKS and perform prelayout ,postlayout characterisation using Ngspice and Magic
![image](https://user-images.githubusercontent.com/123575472/220867893-6ebbe148-d81c-4a5a-bd9f-ee46d4f00db3.png)
![image](https://user-images.githubusercontent.com/123575472/221280812-91355ab2-7e1f-4452-8ba2-145d6e08b435.png)
- **Netlist**
```
** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/func_sky_tb.sch
**.subckt func_sky_tb A B C E D F A B C D E F out A B C D E F
*.ipin A
*.ipin B
*.ipin C
*.ipin E
*.ipin D
*.ipin F
*.ipin A
*.ipin B
*.ipin C
*.ipin D
*.ipin E
*.ipin F
*.opin out
*.ipin A
*.ipin B
*.ipin C
*.ipin D
*.ipin E
*.ipin F
XM1 out A net4 net4 sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM9 net2 B VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM7 net1 A VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM8 net3 C net1 net1 sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM10 net3 D net2 net2 sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM11 out E net3 net3 sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM12 out F net3 net3 sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM2 out C net4 net4 sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM3 net4 B GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM4 net4 D GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM5 out E net5 net5 sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM6 net5 F GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
VDD VDD GND 1.8
.save i(vdd)
VDD1 A GND pulse(0 1.8 0.1n 10p 10p 1n 2n)
.save i(vdd1)
VDD2 B GND pulse(0 1.8 0.2n 10p 10p 1n 2n)
.save i(vdd2)
VDD3 C GND pulse(0 1.8 0.3n 10p 10p 1n 2n)
.save i(vdd3)
VDD4 D GND pulse(0 1.8 0.4n 10p 10p 1n 2n)
.save i(vdd4)
VDD5 E GND pulse(0 1.8 0.5n 10p 10p 1n 2n)
.save i(vdd5)
VDD6 net6 GND pulse(0 1.8 0.6n 10p 10p 1n 2n)
.save i(vdd6)
**** begin user architecture code

.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
.tran 10p 4n
.save all

**** end user architecture code
**.ends
.GLOBAL VDD
.GLOBAL GND
.end
```
![image](https://user-images.githubusercontent.com/123575472/221281642-037968b1-19fa-432f-88b1-69a86ad797c9.png)
- **Post-layout:**
![image](https://user-images.githubusercontent.com/123575472/221465862-1e986666-e99c-4437-8f41-fcb4fbbeb008.png)

![image](https://user-images.githubusercontent.com/123575472/221431078-684e6c38-8c6b-4b47-be59-069b0bd13722.png)

![image](https://user-images.githubusercontent.com/123575472/221431138-a3bbd1d9-3de0-4685-8947-01fc96e264a6.png)

- **Netlist:**
```
* NGSPICE file created from func_sky_tb.ext - technology: sky130A

.subckt sky130_fd_pr__pfet_01v8_XGS3BL a_n73_n100# a_15_n100# w_n211_n319# a_n33_n197#
+ VSUBS
X0 a_15_n100# a_n33_n197# a_n73_n100# w_n211_n319# sky130_fd_pr__pfet_01v8 ad=2.9e+11p pd=2.58e+06u as=2.9e+11p ps=2.58e+06u w=1e+06u l=150000u
C0 w_n211_n319# a_n33_n197# 0.26fF
C1 a_n73_n100# a_n33_n197# 0.03fF
C2 a_15_n100# a_n33_n197# 0.03fF
C3 w_n211_n319# a_n73_n100# 0.09fF
C4 a_15_n100# w_n211_n319# 0.06fF
C5 a_15_n100# a_n73_n100# 0.16fF
C6 a_15_n100# VSUBS 0.02fF
C7 a_n73_n100# VSUBS 0.02fF
C8 a_n33_n197# VSUBS 0.05fF
C9 w_n211_n319# VSUBS 1.07fF
.ends

.subckt sky130_fd_pr__nfet_01v8_648S5X a_n73_n100# a_n33_n188# a_15_n100# a_n175_n274#
X0 a_15_n100# a_n33_n188# a_n73_n100# a_n175_n274# sky130_fd_pr__nfet_01v8 ad=2.9e+11p pd=2.58e+06u as=2.9e+11p ps=2.58e+06u w=1e+06u l=150000u
C0 a_n33_n188# a_n73_n100# 0.03fF
C1 a_15_n100# a_n73_n100# 0.16fF
C2 a_n33_n188# a_15_n100# 0.03fF
C3 a_15_n100# a_n175_n274# 0.08fF
C4 a_n73_n100# a_n175_n274# 0.11fF
C5 a_n33_n188# a_n175_n274# 0.30fF
.ends

.subckt func_sky_tb VDD GND out A C E F D B
XXM12 out m1_1170_550# XM12/w_n211_n319# m1_2440_770# VSUBS sky130_fd_pr__pfet_01v8_XGS3BL
XXM1 out m1_400_n60# m1_490_n280# VSUBS sky130_fd_pr__nfet_01v8_648S5X
XXM2 m1_490_n280# m1_1080_n60# out VSUBS sky130_fd_pr__nfet_01v8_648S5X
XXM3 m1_490_n280# out GND VSUBS sky130_fd_pr__nfet_01v8_648S5X
XXM4 GND out m1_490_n280# VSUBS sky130_fd_pr__nfet_01v8_648S5X
XXM5 out m1_1760_n60# m1_1850_n280# VSUBS sky130_fd_pr__nfet_01v8_648S5X
XXM6 m1_1850_n280# m1_2440_n60# GND VSUBS sky130_fd_pr__nfet_01v8_648S5X
XXM7 VDD m1_490_550# w_414_440# m1_400_780# VSUBS sky130_fd_pr__pfet_01v8_XGS3BL
XXM9 m1_3210_550# VDD XM9/w_n211_n319# out VSUBS sky130_fd_pr__pfet_01v8_XGS3BL
XXM8 m1_490_550# m1_1170_550# w_1080_460# a_1080_460# VSUBS sky130_fd_pr__pfet_01v8_XGS3BL
XXM10 m1_1170_550# m1_3210_550# XM10/w_n211_n319# out VSUBS sky130_fd_pr__pfet_01v8_XGS3BL
XXM11 m1_1170_550# out XM11/w_n211_n319# m1_1760_770# VSUBS sky130_fd_pr__pfet_01v8_XGS3BL
C0 m1_1760_770# E 0.07fF
C1 C m1_1080_n60# 0.06fF
C2 m1_490_n280# F 0.02fF
C3 A m1_1080_n60# 0.00fF
C4 XM11/w_n211_n319# F 0.01fF
C5 XM10/w_n211_n319# F 0.01fF
C6 GND m1_1760_770# 0.00fF
C7 a_1080_460# VDD 0.01fF
C8 B m1_1170_550# 0.00fF
C9 m1_1170_550# m1_490_550# 0.00fF
C10 m1_2440_770# F 0.07fF
C11 C m1_400_780# 0.00fF
C12 out a_1080_460# 0.02fF
C13 D m1_490_n280# 0.19fF
C14 m1_400_n60# VDD 0.00fF
C15 A m1_400_780# 0.07fF
C16 D XM10/w_n211_n319# 0.04fF
C17 m1_1760_n60# VDD 0.00fF
C18 m1_3210_550# m1_490_n280# 0.00fF
C19 w_414_440# E 0.00fF
C20 E F 0.09fF
C21 out m1_400_n60# 0.03fF
C22 m1_3210_550# XM10/w_n211_n319# 0.06fF
C23 m1_1760_n60# out 0.03fF
C24 D m1_2440_770# 0.00fF
C25 m1_2440_n60# F 0.07fF
C26 XM9/w_n211_n319# XM10/w_n211_n319# 0.04fF
C27 w_1080_460# VDD 0.06fF
C28 GND F 0.08fF
C29 C m1_490_n280# 0.14fF
C30 out w_1080_460# 0.26fF
C31 XM11/w_n211_n319# C 0.01fF
C32 A m1_490_n280# 0.17fF
C33 XM12/w_n211_n319# VDD 0.00fF
C34 A XM11/w_n211_n319# 0.00fF
C35 m1_2440_n60# D 0.00fF
C36 VDD m1_1080_n60# 0.00fF
C37 m1_1760_770# m1_1170_550# 0.03fF
C38 out XM12/w_n211_n319# 0.25fF
C39 GND D 0.07fF
C40 B F 0.00fF
C41 w_414_440# m1_490_550# 0.05fF
C42 out m1_1080_n60# 0.03fF
C43 a_1080_460# w_1080_460# 0.01fF
C44 C E 0.08fF
C45 out m1_1850_n280# 0.09fF
C46 VDD m1_400_780# 0.02fF
C47 m1_2440_n60# C 0.00fF
C48 A E 0.00fF
C49 D B 0.07fF
C50 out m1_400_780# 0.02fF
C51 GND C 0.00fF
C52 m1_3210_550# B 0.07fF
C53 A GND 0.00fF
C54 a_1080_460# m1_1080_n60# 0.00fF
C55 w_414_440# m1_1170_550# 0.00fF
C56 m1_1170_550# F 0.07fF
C57 XM9/w_n211_n319# B 0.03fF
C58 VDD m1_490_n280# 0.00fF
C59 m1_400_n60# m1_1080_n60# 0.01fF
C60 C m1_490_550# 0.08fF
C61 w_414_440# m1_1760_770# 0.00fF
C62 m1_1760_770# F 0.00fF
C63 XM11/w_n211_n319# VDD 0.00fF
C64 VDD XM10/w_n211_n319# 0.05fF
C65 m1_1760_n60# m1_1080_n60# 0.01fF
C66 out m1_490_n280# 0.22fF
C67 a_1080_460# m1_400_780# 0.01fF
C68 A m1_490_550# 0.08fF
C69 D m1_1170_550# 0.08fF
C70 out XM11/w_n211_n319# 0.22fF
C71 m1_1760_n60# m1_1850_n280# 0.00fF
C72 out XM10/w_n211_n319# 0.13fF
C73 m1_2440_770# VDD 0.00fF
C74 w_1080_460# m1_1080_n60# 0.00fF
C75 m1_3210_550# m1_1170_550# 0.00fF
C76 m1_400_n60# m1_400_780# 0.00fF
C77 out m1_2440_770# 0.04fF
C78 XM9/w_n211_n319# m1_1170_550# 0.00fF
C79 VDD E 0.00fF
C80 a_1080_460# m1_490_n280# 0.00fF
C81 C m1_1170_550# 0.07fF
C82 m1_2440_n60# VDD 0.00fF
C83 w_1080_460# m1_400_780# 0.00fF
C84 out E 0.32fF
C85 a_1080_460# XM11/w_n211_n319# 0.00fF
C86 A m1_1170_550# 0.00fF
C87 out m1_2440_n60# 0.03fF
C88 m1_400_n60# m1_490_n280# 0.00fF
C89 m1_1760_770# C 0.00fF
C90 a_1080_460# m1_2440_770# -0.00fF
C91 m1_1760_n60# m1_490_n280# 0.00fF
C92 out GND 0.30fF
C93 A m1_1760_770# 0.00fF
C94 m1_1760_n60# XM11/w_n211_n319# 0.00fF
C95 D F 0.08fF
C96 w_1080_460# m1_490_n280# 0.01fF
C97 B VDD 0.07fF
C98 VDD m1_490_550# 0.05fF
C99 a_1080_460# E 0.00fF
C100 w_1080_460# XM11/w_n211_n319# 0.04fF
C101 out B 0.26fF
C102 out m1_490_550# 0.08fF
C103 XM9/w_n211_n319# F 0.00fF
C104 a_1080_460# GND 0.00fF
C105 XM12/w_n211_n319# m1_490_n280# 0.01fF
C106 m1_1760_n60# E 0.07fF
C107 m1_1080_n60# m1_490_n280# 0.01fF
C108 w_414_440# C 0.01fF
C109 XM12/w_n211_n319# XM11/w_n211_n319# 0.04fF
C110 XM12/w_n211_n319# XM10/w_n211_n319# 0.04fF
C111 m1_1760_n60# m1_2440_n60# 0.01fF
C112 D m1_3210_550# 0.08fF
C113 A w_414_440# 0.04fF
C114 m1_400_n60# GND 0.01fF
C115 m1_1850_n280# m1_490_n280# 0.03fF
C116 XM9/w_n211_n319# D 0.01fF
C117 XM12/w_n211_n319# m1_2440_770# 0.01fF
C118 w_1080_460# E 0.01fF
C119 m1_1760_n60# GND 0.01fF
C120 VDD m1_1170_550# 0.47fF
C121 a_1080_460# m1_490_550# -0.00fF
C122 XM9/w_n211_n319# m1_3210_550# 0.06fF
C123 out m1_1170_550# 0.29fF
C124 XM11/w_n211_n319# m1_400_780# 0.00fF
C125 m1_1760_770# VDD 0.00fF
C126 XM12/w_n211_n319# E 0.01fF
C127 m1_1080_n60# E 0.00fF
C128 XM12/w_n211_n319# m1_2440_n60# 0.00fF
C129 out m1_1760_770# 0.03fF
C130 m1_1850_n280# E 0.08fF
C131 GND m1_1080_n60# 0.01fF
C132 w_1080_460# m1_490_550# 0.05fF
C133 m1_2440_n60# m1_1850_n280# 0.00fF
C134 a_1080_460# m1_1170_550# 0.01fF
C135 E m1_400_780# 0.00fF
C136 XM11/w_n211_n319# m1_490_n280# 0.01fF
C137 A C 0.07fF
C138 GND m1_1850_n280# 0.06fF
C139 XM10/w_n211_n319# m1_490_n280# 0.01fF
C140 XM12/w_n211_n319# B 0.00fF
C141 m1_2440_770# m1_490_n280# 0.00fF
C142 a_1080_460# m1_1760_770# 0.01fF
C143 VDD F 0.00fF
C144 w_414_440# VDD 0.20fF
C145 m1_1760_n60# m1_1170_550# 0.00fF
C146 GND m1_400_780# 0.00fF
C147 XM11/w_n211_n319# m1_2440_770# 0.00fF
C148 m1_2440_770# XM10/w_n211_n319# 0.00fF
C149 out w_414_440# 0.26fF
C150 out F 0.24fF
C151 m1_1850_n280# B 0.00fF
C152 w_1080_460# m1_1170_550# 0.08fF
C153 E m1_490_n280# 0.02fF
C154 m1_1760_n60# m1_1760_770# 0.00fF
C155 XM11/w_n211_n319# E 0.05fF
C156 m1_2440_n60# m1_490_n280# 0.00fF
C157 XM10/w_n211_n319# E 0.00fF
C158 D VDD 0.00fF
C159 m1_490_550# m1_400_780# 0.01fF
C160 GND m1_490_n280# 2.64fF
C161 w_1080_460# m1_1760_770# 0.00fF
C162 m1_3210_550# VDD 0.05fF
C163 out D 0.34fF
C164 XM12/w_n211_n319# m1_1170_550# 0.19fF
C165 m1_2440_770# E 0.00fF
C166 XM9/w_n211_n319# VDD 0.12fF
C167 a_1080_460# w_414_440# 0.00fF
C168 m1_2440_n60# m1_2440_770# 0.00fF
C169 out m1_3210_550# 0.09fF
C170 XM9/w_n211_n319# out 0.14fF
C171 GND m1_2440_770# 0.00fF
C172 XM12/w_n211_n319# m1_1760_770# 0.00fF
C173 C VDD 0.00fF
C174 B m1_490_n280# 0.13fF
C175 m1_400_n60# w_414_440# 0.00fF
C176 m1_490_550# m1_490_n280# 0.00fF
C177 A VDD 0.07fF
C178 m1_1760_n60# F 0.00fF
C179 m1_2440_n60# E 0.00fF
C180 out C 0.31fF
C181 m1_1170_550# m1_400_780# 0.00fF
C182 B XM10/w_n211_n319# 0.01fF
C183 A out 0.19fF
C184 GND E 0.00fF
C185 B m1_2440_770# 0.00fF
C186 w_1080_460# w_414_440# 0.04fF
C187 m1_2440_n60# GND 0.02fF
C188 m1_1760_770# m1_400_780# 0.00fF
C189 a_1080_460# C 0.08fF
C190 XM12/w_n211_n319# F 0.04fF
C191 m1_1170_550# m1_490_n280# 0.00fF
C192 m1_2440_n60# B 0.00fF
C193 XM11/w_n211_n319# m1_1170_550# 0.15fF
C194 A a_1080_460# 0.00fF
C195 m1_1170_550# XM10/w_n211_n319# 0.09fF
C196 m1_1850_n280# F 0.07fF
C197 GND B 0.08fF
C198 m1_400_n60# C 0.00fF
C199 m1_1760_770# m1_490_n280# 0.00fF
C200 m1_2440_770# m1_1170_550# 0.03fF
C201 m1_1760_n60# C 0.00fF
C202 A m1_400_n60# 0.06fF
C203 XM11/w_n211_n319# m1_1760_770# 0.02fF
C204 XM12/w_n211_n319# D 0.01fF
C205 w_414_440# m1_400_780# 0.01fF
C206 w_1080_460# C 0.04fF
C207 m1_1760_770# m1_2440_770# 0.01fF
C208 m1_1170_550# E 0.07fF
C209 out VDD 0.18fF
C210 A w_1080_460# 0.01fF
C211 m1_2440_n60# m1_1170_550# 0.00fF
C212 B VSUBS 0.30fF
C213 D VSUBS 0.13fF
C214 F VSUBS 0.20fF
C215 E VSUBS 0.20fF
C216 C VSUBS 0.18fF
C217 A VSUBS 0.27fF
C218 m1_2440_n60# VSUBS 0.27fF
C219 m1_1760_n60# VSUBS 0.27fF
C220 m1_1080_n60# VSUBS 0.27fF
C221 m1_400_n60# VSUBS 0.28fF
C222 m1_2440_770# VSUBS 0.00fF
C223 m1_1760_770# VSUBS -0.00fF
C224 m1_400_780# VSUBS 0.02fF
C225 a_1080_460# VSUBS 0.03fF
C226 XM11/w_n211_n319# VSUBS 1.10fF
C227 m1_3210_550# VSUBS 0.05fF
C228 XM10/w_n211_n319# VSUBS 1.10fF
C229 m1_1170_550# VSUBS 0.08fF
C230 w_1080_460# VSUBS 0.96fF
C231 XM9/w_n211_n319# VSUBS 1.10fF
C232 m1_490_550# VSUBS 0.06fF
C233 VDD VSUBS 0.90fF
C234 w_414_440# VSUBS 1.02fF
C235 GND VSUBS 1.43fF
C236 m1_1850_n280# VSUBS 0.20fF
C237 m1_490_n280# VSUBS 1.14fF
C238 out VSUBS -0.42fF
C239 XM12/w_n211_n319# VSUBS 1.10fF
.ends

** Simulation commands added manually**

** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/func_sky_tb.sch
**.subckt func_sky_tb A B C E D F A B C D E F out A B C D E F
*.ipin A
*.ipin B
*.ipin C
*.ipin E
*.ipin D
*.ipin F
*.ipin A
*.ipin B
*.ipin C
*.ipin D
*.ipin E
*.ipin F
*.opin out
*.ipin A
*.ipin B
*.ipin C
*.ipin D
*.ipin E
*.ipin F
XM1 out A net4 net4 sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM9 net2 B VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM7 net1 A VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM8 net3 C net1 net1 sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM10 net3 D net2 net2 sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM11 out E net3 net3 sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM12 out F net3 net3 sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM2 out C net4 net4 sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM3 net4 B GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM4 net4 D GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM5 out E net5 net5 sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM6 net5 F GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
VDD VDD GND 1.8
.save i(vdd)
VDD1 A GND pulse(0 1.8 0.1n 10p 10p 1n 2n)
.save i(vdd1)
VDD2 B GND pulse(0 1.8 0.2n 10p 10p 1n 2n)
.save i(vdd2)
VDD3 C GND pulse(0 1.8 0.3n 10p 10p 1n 2n)
.save i(vdd3)
VDD4 D GND pulse(0 1.8 0.4n 10p 10p 1n 2n)
.save i(vdd4)
VDD5 E GND pulse(0 1.8 0.5n 10p 10p 1n 2n)
.save i(vdd5)
VDD6 net6 GND pulse(0 1.8 0.6n 10p 10p 1n 2n)
.save i(vdd6)
**** begin user architecture code

.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
.tran 10p 4n
.save all

**** end user architecture code
**.ends
.GLOBAL VDD
.GLOBAL GND
.end
```
![image](https://user-images.githubusercontent.com/123575472/221345409-3a07e199-df71-494d-81ef-baf526616606.png)

![image](https://user-images.githubusercontent.com/123575472/221468816-d86f3e0b-93f7-41e3-bb78-30766f2b7cb2.png)

![image](https://user-images.githubusercontent.com/123575472/221470489-c8afc07f-b5a5-4dd9-96cb-e4823fa39844.png)

![image](https://user-images.githubusercontent.com/123575472/221470853-459d3ce0-0f80-444a-a99b-555a28da44d2.png)




## Design of the function and to perform postlayout characterisation using  ALIGN:
- **Design using xschem**:
![image](https://user-images.githubusercontent.com/123575472/222297538-ed433efa-9ad2-4c5b-ad13-c1c1c727f05a.png)


- **Netlist**
```
** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/fun_tb.sch
**.subckt fun_tb A B C E D F out VDD GND
*.ipin A
*.ipin B
*.ipin C
*.ipin E
*.ipin D
*.ipin F
*.opin out
*.ipin VDD
*.ipin GND
XM7 net1 A VDD VDD sky130_fd_pr__pfet_01v8 L=0.18 W=1.68 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM1 out A net4 net4 sky130_fd_pr__nfet_01v8 L=0.18 W=0.84 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM3 net4 B GND GND sky130_fd_pr__nfet_01v8 L=0.18 W=0.84 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM4 net4 D GND GND sky130_fd_pr__nfet_01v8 L=0.18 W=0.84 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM5 out E net5 net5 sky130_fd_pr__nfet_01v8 L=0.18 W=0.84 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM6 net5 F GND GND sky130_fd_pr__nfet_01v8 L=0.18 W=0.84 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM8 net3 C net1 net1 sky130_fd_pr__pfet_01v8 L=0.18 W=1.68 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM9 net2 B VDD VDD sky130_fd_pr__pfet_01v8 L=0.18 W=1.68 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM10 net3 D net2 net2 sky130_fd_pr__pfet_01v8 L=0.18 W=1.68 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM11 out E net3 net3 sky130_fd_pr__pfet_01v8 L=0.18 W=1.68 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM12 out F net3 net3 sky130_fd_pr__pfet_01v8 L=0.18 W=1.68 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM2 out C net4 net4 sky130_fd_pr__nfet_01v8 L=0.18 W=0.84 nf=2 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
VDD VDD GND 1.8
.save i(vdd)
VDD1 A GND pulse(0 1.8 0.1n 10p 10p 1n 2n)
.save i(vdd1)
VDD2 B GND pulse(0 1.8 0.2n 10p 10p 1n 2n)
.save i(vdd2)
VDD3 C GND pulse(0 1.8 0.3n 10p 10p 1n 2n)
.save i(vdd3)
VDD4 D GND pulse(0 1.8 0.4n 10p 10p 1n 2n)
.save i(vdd4)
VDD5 E GND pulse(0 1.8 0.5n 10p 10p 1n 2n)
.save i(vdd5)
VDD6 F GND pulse(0 1.8 0.6n 10p 10p 1n 2n)
.save i(vdd6)
**** begin user architecture code

.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
.tran 10p 4n
.save all

**** end user architecture code
**.ends
.GLOBAL VDD
.GLOBAL GND
.end
```

![image](https://user-images.githubusercontent.com/123575472/222296427-f0e2242a-a38c-42ba-ae71-19f010e518cd.png)
![image](https://user-images.githubusercontent.com/123575472/222304652-6112d8af-bf27-4b27-a10b-6c928153d53d.png)
**Netlist (.sp)**
```
.subckt fun1_tb A B C E D F out VDD GND
XM7 net1 A VDD VDD sky130_fd_pr__pfet_01v8 L=180n W=1680n nf=2 m=1
XM1 out A net4 net4 sky130_fd_pr__nfet_01v8 L=180n W=840n nf=2 m=1
XM3 net4 B GND GND sky130_fd_pr__nfet_01v8 L=180n W=840n nf=2 m=1
XM4 net4 D GND GND sky130_fd_pr__nfet_01v8 L=180n W=840n nf=2 m=1
XM5 out E net5 net5 sky130_fd_pr__nfet_01v8 L=180n W=840n nf=2 m=1
XM6 net5 F GND GND sky130_fd_pr__nfet_01v8 L=180n W=840n nf=2 m=1
XM8 net3 C net1 net1 sky130_fd_pr__pfet_01v8 L=180n W=1680n nf=2 m=1
XM9 net2 B VDD VDD sky130_fd_pr__pfet_01v8 L=180n W=1680n nf=2 m=1
XM10 net3 D net2 net2 sky130_fd_pr__pfet_01v8 L=180n W=1680n nf=2 m=1
XM11 out E net3 net3 sky130_fd_pr__pfet_01v8 L=180n W=1680n nf=2 m=1
XM12 out F net3 net3 sky130_fd_pr__pfet_01v8 L=180n W=1680n nf=2 m=1
XM2 out C net4 net4 sky130_fd_pr__nfet_01v8 L=180n W=840n nf=2 m=1
.ends fun1_tb
```
![image](https://user-images.githubusercontent.com/123575472/222416639-4bb0064a-6004-4826-a0bd-ffe1fdd0a7bc.png)

- **.lef**
![image](https://user-images.githubusercontent.com/123575472/222414002-f4f068f3-abe6-4660-b517-577e0884d15c.png)
- **.gds**
![image](https://user-images.githubusercontent.com/123575472/222414450-7cbfc382-c1ed-4d41-99f5-10a1914b19f1.png)
![image](https://user-images.githubusercontent.com/123575472/222415274-cbfd646f-42b8-4fa9-bb26-1e2c9dd81cbd.png)

- **Magic layout**
![image](https://user-images.githubusercontent.com/123575472/222415009-b5351427-6be3-4322-8e4a-0d335d50e2b3.png)
- Use the following commands to extract spice netlist
```
extract do local
excract all
ext2spice hierarchy on
ext2spice scale off
ext2spice cthresh 0 rthresh 0
ext2spice 
```
- **spice netlist**
```
* NGSPICE file created from FUN1_TB_0.ext - technology: sky130A

.subckt PMOS_S_95137167_X1_Y1_1677731921_1677731924 a_200_252# a_230_399# w_0_0# SUB
X0 a_230_399# a_200_252# w_0_0# w_0_0# sky130_fd_pr__pfet_01v8 ad=4.704e+11p pd=3.92e+06u as=8.904e+11p ps=7.78e+06u w=1.68e+06u l=150000u
X1 w_0_0# a_200_252# a_230_399# w_0_0# sky130_fd_pr__pfet_01v8 ad=0p pd=0u as=0p ps=0u w=1.68e+06u l=150000u
C0 a_200_252# w_0_0# 0.66fF
C1 a_200_252# a_230_399# 0.10fF
C2 w_0_0# a_230_399# 0.78fF
C3 a_230_399# SUB -0.03fF
C4 a_200_252# SUB 0.06fF
C5 w_0_0# SUB 2.97fF
.ends

.subckt NMOS_S_54129001_X1_Y1_1677731920_1677731924 a_200_252# a_230_483# a_147_483#
X0 a_230_483# a_200_252# a_147_483# a_147_483# sky130_fd_pr__nfet_01v8 ad=2.352e+11p pd=2.24e+06u as=4.452e+11p ps=4.42e+06u w=840000u l=150000u
X1 a_147_483# a_200_252# a_230_483# a_147_483# sky130_fd_pr__nfet_01v8 ad=0p pd=0u as=0p ps=0u w=840000u l=150000u
C0 a_230_483# a_200_252# 0.11fF
C1 a_230_483# a_147_483# 0.74fF
C2 a_200_252# a_147_483# 0.89fF
.ends

.subckt INV_45746474_0_0_1677731924 m1_312_1400# PMOS_S_95137167_X1_Y1_1677731921_1677731924_0/w_0_0#
+ li_405_571# SUB
XPMOS_S_95137167_X1_Y1_1677731921_1677731924_0 li_405_571# m1_312_1400# PMOS_S_95137167_X1_Y1_1677731921_1677731924_0/w_0_0#
+ SUB PMOS_S_95137167_X1_Y1_1677731921_1677731924
XNMOS_S_54129001_X1_Y1_1677731920_1677731924_0 li_405_571# m1_312_1400# SUB NMOS_S_54129001_X1_Y1_1677731920_1677731924
C0 li_405_571# PMOS_S_95137167_X1_Y1_1677731921_1677731924_0/w_0_0# 0.34fF
C1 li_405_571# m1_312_1400# 0.10fF
C2 PMOS_S_95137167_X1_Y1_1677731921_1677731924_0/w_0_0# m1_312_1400# 0.01fF
C3 m1_312_1400# SUB 0.70fF
C4 li_405_571# SUB 1.48fF
C5 PMOS_S_95137167_X1_Y1_1677731921_1677731924_0/w_0_0# SUB 3.02fF
.ends

.subckt DP_PMOS_83764739_X1_Y1_1677731925 a_372_252# a_200_252# a_230_399# a_402_399#
+ SUB
X0 w_0_0# a_372_252# a_402_399# w_0_0# sky130_fd_pr__pfet_01v8 ad=1.3608e+12p pd=1.17e+07u as=4.704e+11p ps=3.92e+06u w=1.68e+06u l=150000u
X1 a_230_399# a_200_252# w_0_0# w_0_0# sky130_fd_pr__pfet_01v8 ad=4.704e+11p pd=3.92e+06u as=0p ps=0u w=1.68e+06u l=150000u
X2 w_0_0# a_200_252# a_230_399# w_0_0# sky130_fd_pr__pfet_01v8 ad=0p pd=0u as=0p ps=0u w=1.68e+06u l=150000u
X3 a_402_399# a_372_252# w_0_0# w_0_0# sky130_fd_pr__pfet_01v8 ad=0p pd=0u as=0p ps=0u w=1.68e+06u l=150000u
C0 a_230_399# a_402_399# 0.06fF
C1 a_230_399# w_0_0# 0.72fF
C2 a_230_399# a_200_252# 0.10fF
C3 a_372_252# a_402_399# 0.10fF
C4 w_0_0# a_402_399# 0.91fF
C5 a_402_399# a_200_252# 0.01fF
C6 a_372_252# w_0_0# 0.57fF
C7 a_372_252# a_200_252# 0.21fF
C8 w_0_0# a_200_252# 0.56fF
C9 a_402_399# SUB -0.05fF
C10 a_230_399# SUB -0.10fF
C11 a_372_252# SUB 0.04fF
C12 a_200_252# SUB -0.00fF
C13 w_0_0# SUB 3.45fF
.ends

.subckt NMOS_S_54129001_X1_Y1_1677731926 a_200_252# a_230_483# a_147_483#
X0 a_230_483# a_200_252# a_147_483# a_147_483# sky130_fd_pr__nfet_01v8 ad=2.352e+11p pd=2.24e+06u as=4.452e+11p ps=4.42e+06u w=840000u l=150000u
X1 a_147_483# a_200_252# a_230_483# a_147_483# sky130_fd_pr__nfet_01v8 ad=0p pd=0u as=0p ps=0u w=840000u l=150000u
C0 a_200_252# a_230_483# 0.11fF
C1 a_230_483# a_147_483# 0.74fF
C2 a_200_252# a_147_483# 0.89fF
.ends

.subckt PMOS_S_95137167_X1_Y1_1677731927 a_200_252# a_230_399# w_0_0# SUB
X0 a_230_399# a_200_252# w_0_0# w_0_0# sky130_fd_pr__pfet_01v8 ad=4.704e+11p pd=3.92e+06u as=8.904e+11p ps=7.78e+06u w=1.68e+06u l=150000u
X1 w_0_0# a_200_252# a_230_399# w_0_0# sky130_fd_pr__pfet_01v8 ad=0p pd=0u as=0p ps=0u w=1.68e+06u l=150000u
C0 a_230_399# w_0_0# 0.78fF
C1 a_230_399# a_200_252# 0.10fF
C2 w_0_0# a_200_252# 0.66fF
C3 a_230_399# SUB -0.03fF
C4 a_200_252# SUB 0.06fF
C5 w_0_0# SUB 2.97fF
.ends

.subckt FUN1_TB_0 A B C E D F out VDD GND
XINV_45746474_0_0_1677731924_0 OUT m1_828_56# E GND INV_45746474_0_0_1677731924
XDP_PMOS_83764739_X1_Y1_1677731925_0 m1_2462_2492# A VDD VDD SUB DP_PMOS_83764739_X1_Y1_1677731925
XNMOS_S_54129001_X1_Y1_1677731926_0 F SUB SUB NMOS_S_54129001_X1_Y1_1677731926
XNMOS_S_54129001_X1_Y1_1677731926_1 D SUB SUB NMOS_S_54129001_X1_Y1_1677731926
XPMOS_S_95137167_X1_Y1_1677731927_0 li_1953_907# m1_828_56# VDD SUB PMOS_S_95137167_X1_Y1_1677731927
XPMOS_S_95137167_X1_Y1_1677731927_1 F OUT m1_828_56# SUB PMOS_S_95137167_X1_Y1_1677731927
XNMOS_S_54129001_X1_Y1_1677731926_2 m1_2462_2492# SUB SUB NMOS_S_54129001_X1_Y1_1677731926
XPMOS_S_95137167_X1_Y1_1677731927_2 D m1_828_56# VDD SUB PMOS_S_95137167_X1_Y1_1677731927
XNMOS_S_54129001_X1_Y1_1677731926_3 li_1953_907# OUT SUB NMOS_S_54129001_X1_Y1_1677731926
XNMOS_S_54129001_X1_Y1_1677731926_4 A OUT SUB NMOS_S_54129001_X1_Y1_1677731926
C0 m1_2462_2492# F 0.00fF
C1 B F 0.00fF
C2 VDD F 0.01fF
C3 OUT li_1953_907# 0.01fF
C4 A li_1953_907# 0.15fF
C5 D li_1953_907# 0.05fF
C6 m1_828_56# li_1953_907# 0.00fF
C7 A OUT -0.01fF
C8 D OUT 0.00fF
C9 D A 0.01fF
C10 m1_2462_2492# li_1953_907# 0.00fF
C11 OUT m1_828_56# 0.30fF
C12 OUT E 0.01fF
C13 A E 0.01fF
C14 VDD li_1953_907# 0.01fF
C15 C OUT 0.04fF
C16 D m1_828_56# 0.00fF
C17 C A 0.26fF
C18 C D -0.00fF
C19 m1_828_56# E 0.04fF
C20 C m1_828_56# 0.02fF
C21 C E 0.00fF
C22 F li_1953_907# 0.00fF
C23 A m1_2462_2492# 0.00fF
C24 A B 0.01fF
C25 OUT VDD 0.05fF
C26 D m1_2462_2492# 0.03fF
C27 D B 0.12fF
C28 A VDD -0.01fF
C29 D VDD 0.48fF
C30 m1_828_56# VDD 1.27fF
C31 C B 0.00fF
C32 OUT F 0.31fF
C33 A F 0.01fF
C34 C VDD 0.77fF
C35 m1_828_56# F 0.59fF
C36 E F 0.06fF
C37 C F 0.00fF
C38 VDD m1_2462_2492# 0.00fF
C39 VDD B 0.22fF
C40 C SUB 0.24fF
C41 B SUB 0.47fF
C42 li_1953_907# GND 1.80fF
C43 D SUB 2.33fF
C44 F SUB 0.75fF
C45 VDD SUB 6.17fF
C46 m1_2462_2492# GND 1.68fF
C47 A SUB 1.44fF
C48 DP_PMOS_83764739_X1_Y1_1677731925_0/w_0_0# GND 3.45fF 
C49 OUT SUB 1.88fF
C50 E SUB 1.18fF
C51 m1_828_56# GND 3.20fF
.ends

*****sim added**
** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/fun_tb.sch
**.subckt fun_tb A B C E D F out VDD GND
XM7 net1 A VDD VDD sky130_fd_pr__pfet_01v8 
XM1 out A net4 net4 sky130_fd_pr__nfet_01v8  
XM3 net4 B GND GND sky130_fd_pr__nfet_01v8 
XM4 net4 D GND GND sky130_fd_pr__nfet_01v8 
XM5 out E net5 net5 sky130_fd_pr__nfet_01v8 
XM6 net5 F GND GND sky130_fd_pr__nfet_01v8 
XM8 net3 C net1 net1 sky130_fd_pr__pfet_01v8 
XM9 net2 B VDD VDD sky130_fd_pr__pfet_01v8 
XM10 net3 D net2 net2 sky130_fd_pr__pfet_01v8  
XM11 out E net3 net3 sky130_fd_pr__pfet_01v8 
XM12 out F net3 net3 sky130_fd_pr__pfet_01v8  
XM2 out C net4 net4 sky130_fd_pr__nfet_01v8 
VDD VDD GND 1.8
.save i(vdd)
VDD1 A GND pulse(0 1.8 0.1n 10p 10p 1n 2n)
.save i(vdd1)
VDD2 B GND pulse(0 1.8 0.2n 10p 10p 1n 2n)
.save i(vdd2)
VDD3 C GND pulse(0 1.8 0.3n 10p 10p 1n 2n)
.save i(vdd3)
VDD4 D GND pulse(0 1.8 0.4n 10p 10p 1n 2n)
.save i(vdd4)
VDD5 E GND pulse(0 1.8 0.5n 10p 10p 1n 2n)
.save i(vdd5)
VDD6 F GND pulse(0 1.8 0.6n 10p 10p 1n 2n)
.save i(vdd6)
X1 A B C E D F out VDD GND FUN1_TB_0 
**** begin user architecture code

.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
.tran 10p 4n
.save all

**** end user architecture code
**.ends
.GLOBAL VDD
.GLOBAL GND
.end

```
![image](https://user-images.githubusercontent.com/123575472/222420973-8585c26e-2e7e-4f55-bcfc-bd081402719d.png)


# WEEK-2
### OPENROAD installation:
Refer the following link https://theopenroadproject.org/resources/ and the git repo https://github.com/The-OpenROAD-Project
![image](https://user-images.githubusercontent.com/123575472/222634309-270cc874-0175-4152-b787-d601c6d35017.png)
- **Steps to install:**
```
cd
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD.git
cd OpenROAD
sudo ./etc/DependencyInstaller.sh
cd
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
cd OpenROAD-flow-scripts
./build_openroad.sh –local
export OPENROAD=~/OpenROAD-flow-scripts/tools/OpenROAD
export PATH=~/OpenROAD-flow-scripts/tools/install/OpenROAD/bin:~/OpenROAD-flow-scripts/tools/install/yosys/bin:~/OpenROAD-flow-scripts/tools/install/LSOracle/bin:$PATH
```
![image](https://user-images.githubusercontent.com/123575472/222922963-61b1d0c7-ec82-472e-844b-b3ffe28a0d6d.png)
![image](https://user-images.githubusercontent.com/123575472/222923066-b9ff31d3-7f0d-4ab2-b1f5-f8c4a0cbd421.png)
![image](https://user-images.githubusercontent.com/123575472/222923117-5b7dd011-e4a7-40ab-ab6f-29d786c6bd82.png)
![image](https://user-images.githubusercontent.com/123575472/222941662-3c9c4255-bca7-4644-b2af-b3d315dde4af.png)

### OpenFASoC Installation :

OpenFASOC is focused on open-source automate analog generation from user specification to GDSII with fully open-sourced tools.
The tool is comprised of analog and mixed-signal circuit generators, which automatically create a physical design based on user specifications.
Reference taken from the given [repo](https://github.com/sanampudig/OpenFASoC/tree/main/Temp_sence_gen%20FLOW)
- Read the official document of OpenFASoC [here](https://openfasoc.readthedocs.io/en/latest/getting-started.html) and [git repo](https://github.com/idea-fasoc/openfasoc) to understand in detail. 
- **Steps to install:**
```
cd
git clone https://github.com/idea-fasoc/openfasoc
cd openfasoc
sudo ./dependencies.sh
```
- After running the above commands ,we get the following result.
![image](https://user-images.githubusercontent.com/123575472/222942802-35d35f45-2b99-4735-8647-597007951149.png)
![image](https://user-images.githubusercontent.com/123575472/222690031-435951c1-85d2-4ad4-b8af-e9a208009687.png)
### Eg.Temperature Sensor Auxilary cells:
![image](https://user-images.githubusercontent.com/123575472/222708361-d178fea5-c56c-44d0-94bb-26dc6290c203.png)
This generator creates a compact mixed-signal temperature sensor based on the topology based on https://ieeexplore.ieee.org/document/9816083 It consists of a ring oscillator whose frequency is controlled by the voltage drop over a MOSFET operating in subthreshold regime, where its dependency on temperature is exponential.

The physical implementation of the analog blocks in the circuit is done using two manually designed standard cells:

HEADER cell, containing the transistors in subthreshold operation;

SLC cell, containing the Split-Control Level Converter.

- Now,view the gds and lef file of the auxilary cell.
![image](https://user-images.githubusercontent.com/123575472/222712156-0034c7e4-23d5-4249-a1e3-9af31dda081b.png)
![image](https://user-images.githubusercontent.com/123575472/222712469-be980da1-71a1-419f-a0b6-2aea8c770a14.png)

![image](https://user-images.githubusercontent.com/123575472/222712344-93b2ff2f-1bbd-4414-9a3b-537b900d6f17.png)
## Run OpenFASoC Flow
```
First cd into the directory where the OpenFASoC repository was cloned;
Now edit the platform_config.json file, replacing the open_pdks value with the path to the sky130A/ directory;
Export the PDK_ROOT environment variable to your skywater-pdk location until the sky130A/ directory (not required if the dependencies are installed via the dependencies.sh script);
Now go to one of the generators with cd openfasoc/generators/<generator_name> and run make to list down all the generator specific targets;
Run make <library>_<generator>_<mode> to begin the flow.
Below is an example of options for the temp-sense generator:
```
![image](https://user-images.githubusercontent.com/123575472/222943455-9356cdb6-cf78-4c1e-8722-b0f462ebb142.png)
- The default circuit's physical design generation can be divided into three parts:
          1. Verilog generation
          2. RTL-to-GDS flow
          3. Post-layout verification
     
### Verilog generation:
Run the follwing command,which runs verilog files.
```
make sky130hd_temp_verilog
```
![image](https://user-images.githubusercontent.com/123575472/222943601-c13b1193-1cbb-4ce4-b6ad-85fe29554902.png)
- The input for verilog generation is user specification(which tells user requirement to analog generator )i.e is present in the form of .json file and the output is verilog files.
 ![image](https://user-images.githubusercontent.com/123575472/222772423-a5cb5bd7-61fc-4004-adc8-956016ef9e6d.png)
- The experimental data used to optimise the design as per the user requirement is given as model.csv file..
 ![image](https://user-images.githubusercontent.com/123575472/222775451-5aab0f30-1cde-47fe-9016-d85d3f5e3327.png)
 ![image](https://user-images.githubusercontent.com/123575472/222776178-f1e1fcf1-48c6-4dc6-ad2b-5abcce92c47e.png) 

-The  directory of verilog file is shown below
![image](https://user-images.githubusercontent.com/123575472/222779691-f64a407d-8c89-48f8-8026-a389840203ba.png)
![image](https://user-images.githubusercontent.com/123575472/222778214-a02c3632-b31d-411e-be0c-56bd3a9eb982.png)

![image](https://user-images.githubusercontent.com/123575472/222778567-0f1c5f84-e87a-4a5c-9f58-9e08aabde157.png)
### Synthesis
The OpenROAD Flow starts with a flow configuration file config.mk, the chosen platform (sky130hd, for example) and the Verilog files are generated from the previous part.
- Note:OpenROAD flow has diff.tools to implement RTL2GDS(synthesis,floorplan,placement.....)
![image](https://user-images.githubusercontent.com/123575472/222782891-7d9bd719-c1ef-40ba-979b-5639fee9755e.png)

![image](https://user-images.githubusercontent.com/123575472/222783885-d6495bee-7862-46e7-beec-e02a57c4aa0f.png)
- Run the synthesis: Tool used -> yosys (tech. mapping done by ABC);inputs are -> config.mk,and verilog file
```
make sky130hd_temp
```
![image](https://user-images.githubusercontent.com/123575472/222786208-1be803e0-c98e-4cd4-bde5-74680e5c2eaf.png)
If we get OpenROAD path error, run the below commands:
```
export OPENROAD=~/OpenROAD-flow-scripts/tools/OpenROAD
export PATH=~/OpenROAD-flow-scripts/tools/install/OpenROAD/bin:~/OpenROAD-flow-scripts/tools/install/yosys/bin:~/OpenROAD-flow-scripts/tools/install/LSOracle/bin:$PATH
export PDK_ROOT=/usr/local/share/pdk
```

![image](https://user-images.githubusercontent.com/123575472/223457787-1c806c69-02cf-4339-a5e4-df15b50114e0.png)
- The above command (make sky130hd_temp) will run the complete flow from verilog generation to the final GDS.
- ![image](https://user-images.githubusercontent.com/123575472/223881676-ff2b8925-be26-426d-9a9a-d3cad5ee0a2f.png)
- The snap of synthesized netlist is shown below, which contains standard cells of sky130hd library and auxilary cells(header and slc)
 ![image](https://user-images.githubusercontent.com/123575472/223882967-b931a8f6-c322-40fb-b575-bcae45de5129.png)
### Floorplan
The floorplan for the physical design is generated with OpenROAD, which requires a description of the power delivery network in pdn.cfg.
![image](https://user-images.githubusercontent.com/123575472/223884116-0586895f-3900-4668-8602-a29a85165e63.png)
The floorplan report is shown below:

![image](https://user-images.githubusercontent.com/123575472/223885094-49760f2b-ed3a-4b8e-8517-e9410a2ffcc2.png)
### Placement
Placement is of 2 types , i.e.,Global and Detail
![image](https://user-images.githubusercontent.com/123575472/223887226-88f6fca3-34a4-427d-956e-25428127ad84.png)
Area utilisation and power consumption has been increased.
![image](https://user-images.githubusercontent.com/123575472/223887719-ab8eeea9-db1a-45e9-91b6-a7369940e8c3.png)
### Routing
Routing is also divided into two phases: global routing and detailed routing. Right before global routing, OpenFASoC calls /openfasoc/openfasoc/generators/temp-sense-gen/flow/scripts/openfasocpre_global_route.tcl:

![image](https://user-images.githubusercontent.com/123575472/223890299-ccfb61d3-675f-408f-9285-f834cd322505.png)
![image](https://user-images.githubusercontent.com/123575472/223890661-42f4d910-5037-47ee-9420-e36d90da0205.png)

### Final Layout
![image](https://user-images.githubusercontent.com/123575472/223891977-69b1c517-e7b8-4cc4-9088-d89b494efc91.png)
![image](https://user-images.githubusercontent.com/123575472/223891522-29a195a1-8474-4283-91b3-3af1c946276b.png)
 - **Layout by magic:**
    ![image](https://user-images.githubusercontent.com/123575472/224007714-b6fde6cd-2b79-4796-9efd-3429629fb310.png)


# WEEK 3
## TASK: To draw a circuit of RING OSCILLATOR and perform its characteristics
A ring oscillator is a device composed of an odd number of NOT gates in a ring, whose output oscillates between two voltage levels, representing true and false. The NOT gates, or inverters, are attached in a chain and the output of the last inverter is fed back into the first.
![image](https://user-images.githubusercontent.com/123575472/223944696-2b5926af-59cb-4ee6-a26c-f630a5b3072a.png)

## 3.1.Three-stage ring oscillator in Xschem
![image](https://user-images.githubusercontent.com/123575472/224225268-b91aaa7c-2989-4d7b-9ac4-22dde58290ed.png)
![image](https://user-images.githubusercontent.com/123575472/224223595-55183fa4-db9f-4567-8529-093eef9ce76c.png)
![image](https://user-images.githubusercontent.com/123575472/224094977-ded56ef8-f1ee-4e42-9787-06a2636eb248.png)
- **Prelayout netlist**:
```
** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/ring_osc/ring_osc_tb.sch
**.subckt ring_osc_tb Y VDD GND
*.opin Y
*.iopin VDD
*.iopin GND
x1 VDD Y GND ring_osc
V1 VDD GND 1.8
.save i(v1)
**** begin user architecture code

.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt


.tran 0.01n 5n
.save all

**** end user architecture code
**.ends

* expanding   symbol:  ring_osc/ring_osc.sym # of pins=3
** sym_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/ring_osc/ring_osc.sym
** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/ring_osc/ring_osc.sch
.subckt ring_osc VDD Y GND
*.iopin VDD
*.iopin GND
*.opin Y
XM1 net1 Y VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM2 net2 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM3 Y net2 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM4 net1 Y GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM5 net2 net1 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM6 Y net2 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
.ends

.GLOBAL GND
.end
```
## Post-layout using magic
GO to xschem_tb.sch -> simulation-> LVS netlist. Now,open magic folder and run magic -Tsky130A.tech => layout window appears. Go to File->IMPORT SPICE-> open the spice netlist folder and then press V .After checking drcs and routing the final layout is shown below.
![image](https://user-images.githubusercontent.com/123575472/224224833-cfdef6e4-e268-4f9a-a35d-4500dc6a1862.png)

- **postlayout netlist**
```
* NGSPICE file created from ring_osc.ext - technology: sky130A

.subckt sky130_fd_pr__pfet_01v8_XGS3BL a_n73_n100# a_15_n100# a_n33_n197#
X0 a_15_n100# a_n33_n197# a_n73_n100# w_n211_n319# sky130_fd_pr__pfet_01v8 ad=2.9e+11p pd=2.58e+06u as=2.9e+11p ps=2.58e+06u w=1e+06u l=150000u
.ends

.subckt sky130_fd_pr__nfet_01v8_648S5X a_n73_n100# a_n33_n188# a_15_n100# a_n175_n274#
X0 a_15_n100# a_n33_n188# a_n73_n100# a_n175_n274# sky130_fd_pr__nfet_01v8 ad=2.9e+11p pd=2.58e+06u as=2.9e+11p ps=2.58e+06u w=1e+06u l=150000u
.ends

.subckt ring_osc VDD Y GND
XXM1 VDD m1_284_866# Y sky130_fd_pr__pfet_01v8_XGS3BL
XXM2 VDD m1_1778_1068# m1_284_866# sky130_fd_pr__pfet_01v8_XGS3BL
XXM3 VDD Y m1_1778_1068# sky130_fd_pr__pfet_01v8_XGS3BL
XXM4 GND Y m1_284_866# VSUBS sky130_fd_pr__nfet_01v8_648S5X
XXM5 GND m1_284_866# m1_1778_1068# VSUBS sky130_fd_pr__nfet_01v8_648S5X
XXM6 GND m1_1778_1068# Y VSUBS sky130_fd_pr__nfet_01v8_648S5X
.ends

** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/ring_osc/ring_osc_tb.sch
*.subckt ring_osc_tb Y VDD GND
*.PININFO Y:O VDD:B GND:B
x1 VDD Y GND ring_osc
V1 VDD GND 1.8
.save i(v1)
**** begin user architecture code

.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt


.tran 0.01n 5n
.save all

**** end user architecture code
*.ends

* expanding   symbol:  ring_osc/ring_osc.sym # of pins=3
** sym_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/ring_osc/ring_osc.sym
** sch_path: /home/shakila12/Desktop/pd_rp/week0/inverter/xschem/ring_osc/ring_osc.sch
.subckt ring_osc VDD Y GND
*.PININFO VDD:B GND:B Y:O
XM1 net1 Y VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 m=1
XM2 net2 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 m=1
XM3 Y net2 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 m=1
XM4 net1 Y GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 m=1
XM5 net2 net1 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 m=1
XM6 Y net2 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 m=1
.ends

.GLOBAL GND
.end
```

![image](https://user-images.githubusercontent.com/123575472/224223415-c4ac0974-fba6-466f-ad74-aa47c37cb973.png)
