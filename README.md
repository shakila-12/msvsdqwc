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
### Note:
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

To understand the flow, refer the following [repo.](https://github.com/sanampudig/OpenFASoC/tree/main/AUXCELL)
      
  **Steps followed to install ALIGN tool:**
```
export CC=/usr/bin/gcc
export CXX=/usr/bin/g++
git clone https://github.com/ALIGN-analoglayout/ALIGN-public
cd ALIGN-public

#Create a Python virtualenv
python3 -m venv general
source general/bin/activate
python -m pip install pip --upgrade

#Install ALIGN as a USER
pip install -v .

#Install ALIGN as a DEVELOPER
pip install -e .

pip install setuptools wheel pybind11 scikit-build cmake ninja
pip install -v -e .[test] --no-build-isolation
pip install -v --no-build-isolation -e . --no-deps --install-option='-DBUILD_TESTING=ON'

```

```
   - Note:Make sure that you installed pip and venv packages:

      $ sudo apt install python3-pip
      $ sudo apt install python3-venv
      
  ```
  
 ![ALIGN](https://user-images.githubusercontent.com/123575472/218288296-e0d9ed1d-0b11-4ea1-ba30-047fc93216b3.png)

### TASK: CREATE INVERTER AND PERFORM PRE-LAYOUT,POST-LAYOUT EXPERIMENT USING XCSHEM /NGSPICE ,MAGIC
### Pre-layout :
### Inverter schematic using xschem:




![image](https://user-images.githubusercontent.com/123575472/218880868-8044f410-1772-4498-8445-52793e1511d3.png)

![image](https://user-images.githubusercontent.com/123575472/218882340-456db836-e6ea-473a-a9bb-ffcd5a9a959a.png)

![image](https://user-images.githubusercontent.com/123575472/218882628-32991dab-4ea8-4f5d-a8db-44a2aff02496.png)

- **Rise transition**: Output transition from 20% to 80% [ voltage=1.8v => , 20% of 1.8 is 0.36 and 80%of 1.8 is 1.44 ]
![image](https://user-images.githubusercontent.com/123575472/218892997-981fd2fb-d5e7-4de9-bf38-4ebc2d6f3616.png)
![image](https://user-images.githubusercontent.com/123575472/218893309-c0c26dcc-d63c-4bc8-a4c0-a1330f58eb16.png)

- **Fall transition**: Output transition from 80% to 20%

![image](https://user-images.githubusercontent.com/123575472/218894529-72e6a23e-8d68-4215-b9b7-d7762572cd51.png)

- **Rise Delay**: [delay between 50%(1.8V) of input to 50%(1.8V) of output]:


![image](https://user-images.githubusercontent.com/123575472/218896861-5ecba6b3-e6a2-4feb-a59e-1b64036608a8.png)

- **Fall Delay **: [delay between 50%(1.65V) of input to 50%(1.65V) of output]:
![image](https://user-images.githubusercontent.com/123575472/218898200-5ef114df-33d0-49de-a925-ac4aed5b8d1f.png)

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
### Transient analysis:
![image](https://user-images.githubusercontent.com/123575472/220127621-b7498353-1a9d-46f0-996e-e1ddc3e4b312.png)
![image](https://user-images.githubusercontent.com/123575472/220127319-95b4970c-3749-4f6b-9d5b-010bad58b8b5.png)
![image](https://user-images.githubusercontent.com/123575472/220130973-149b1287-3b02-42c1-a585-5b7038ada8ed.png)

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
**Steps **:
![image](https://user-images.githubusercontent.com/123575472/219266814-75bb3be1-90c2-44f5-af03-6e306d67a6c8.png)
![image](https://user-images.githubusercontent.com/123575472/220135071-e066b976-5862-4ed9-86e5-a00715a24dfc.png)


After importing the generated spice netlist , (go to file ->IMPORT NETLIST ....in layout window)the following image appears..
![image](https://user-images.githubusercontent.com/123575472/220136800-8fb1e4c4-f597-4fb4-8208-36ae237a47bf.png)

- For the steps to import refer [this](https://github.com/Avnish21/VSD-Physical-Verification-Using-Sky130/blob/main/README.md)
- TO  UNDERSTAND THE LAYOUT PROCESS ,REFER https://www.udemy.com/course/vlsi-academy-custom-layout/
     
``` 
Note:  
      1. The below INVERTER layout is drawn , just a curiosity to learn layout diag. and its spice netlist generated from layout is shown.
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




