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

-** Steps to install**:
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

### TASK: CREATE INVERTER AMD PERFORM PRE-LAYOUT,POST-LAYOUT EXPERIMENT USING XCSHEM OR NGSPICE

### Inverter schematic using xschem:



![image](https://user-images.githubusercontent.com/123575472/218701852-88c08615-ae3e-432e-bffc-8fb82b51ed94.png)



at wp=wn=3

![image](https://user-images.githubusercontent.com/123575472/218878183-9d2a64fc-5f79-42f7-a724-9c6a9e38a7a0.png)

![image](https://user-images.githubusercontent.com/123575472/218874723-98bf03be-c42e-4726-a143-aeb067b6fa99.png)

@ DIFF WIDTHS:
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

![image](https://user-images.githubusercontent.com/123575472/218989745-3efc7deb-5454-498b-9f9a-9892aea82986.png)

![image](https://user-images.githubusercontent.com/123575472/218989331-de79eea1-95bf-4e43-a039-e6ada8ab07a5.png)
![image](https://user-images.githubusercontent.com/123575472/218993911-8fe42e2c-c5fd-4551-aa2e-ec2646ae743c.png)

![image](https://user-images.githubusercontent.com/123575472/218993805-51163b41-10b0-4045-a7ac-782c07d2e8ef.png)

![image](https://user-images.githubusercontent.com/123575472/218995517-d01f19ee-b37c-469d-8466-5a3309c947c7.png)
![image](https://user-images.githubusercontent.com/123575472/218996331-8c44652f-586f-472d-ae0f-53c38cf856cb.png)
![image](https://user-images.githubusercontent.com/123575472/218996472-0d1a50be-8883-47f0-a16b-7f54195c553f.png)




