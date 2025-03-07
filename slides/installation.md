---
theme: uncover
_class: lead
paginate: true
backgroundColor: #fff
marp: true
# backgroundImage: url('https://marp.app/assets/hero-background.svg')
<style>
:root {
  font-family: 'Roboto', 'Segoe UI', 'Liberation Sans', 'Helvetica', 'Arial', sans-serif;
}
</style>
section {
  width: 960px;
  height: 720px;
}
---
## **Geant4 installation and overview**

Deepak Samuel
Central University of Karnataka

<!-- > *NEUS 2024* -->

---
## **About Geant4**

-  Propagates particles through matter
    - Given a particle with 
        - ($x_i$,$y_i$,$z_i$,$t_i$,$p_{xi}$,$p_{yi}$,$p_{zi}$) 
        - material
    - predicts 
        - ($x_f$,$y_f$,$z_f$,$t_f$,$p_{xf}$,$p_{yf}$,$p_{zf}$)
    - Creates other daughter particles and propogates them as well
- Used in most nuclear and particle physics experiments for prototyping and benchmarking
    - Used in medical physics, space sciences   
- *Considered an important skill for researchers in these fields*
    
---

## **Plan**

- 8 March:
    - Installation and C++ concepts
    - Testing of installation, running basic examples and overview
    - Geometry building

- 9 March:
    - User actions
    - Particle Gun
    - Readout
    - Simulating simple experiments
---
## **Prerequisites**
- None
- Good to haves:
    - Basic c++ programming
    - Basic python 
    - Basic linux commands (cd, ls, mkdir, cp, rm, rm -r, ~, LD_LIBRARY_PATH)



---
## **Download links/commands for Windows users**
| Software          | Command/Source                                              |
|-------------------|-------------------------------------------------------------|
| WSL2*             | https://learn.microsoft.com/en-us/windows/wsl/install       |
| Ubuntu 24*        | Windows store (Search for WSL Ubuntu)                       |
| VSCode (Windows)  | Windows: https://code.visualstudio.com/Download             |
| Jupyter extension | On VSCode, click extensions, search ```Jupyter```, install       |
| WSL extension | On VSCode, click extensions, search ```WSL```,  install       |


---

## **Download links/commands on the Linux system**
| Software          | Command/Source                                              |
|-------------------|-------------------------------------------------------------|
| Snap              | ```sudo apt update && sudo apt install snapd   ```                |
| VSCode (if not using WSL)   | ```sudo snap install --classic code       ```                     |
| Jupyter extension | On VSCode, click extensions, search ```Jupyter```, install       |
| WSL extension | On VSCode, click extensions, search ```WSL```,  install       |
| Build tools       | ```sudo apt-get update && sudo apt-get install build-essential``` |
| CMake             | ```sudo snap install cmake  -classic```                         |


---
## **Other software and libraries**
- ```sudo apt-get install qtbase5-dev```
- ```sudo apt-get install libxmu-dev```
- ```sudo apt-get install libexpat-dev```
---

## **Geant4 installation and initialization**
- ```sudo snap install gate```
- Thereafter, whenever you start a new terminal (for using Geant4):
    - ```source /snap/gate/45/usr/local/bin/geant4.sh```  
    - If you are running a G4 code from a VSCode terminal, in some cases you will get the following error:
        - ```symbol lookup error: /snap/core20/current/lib/x86_64-linux-gnu/libpthread.so.0: undefined symbol: __libc_pthread_init, version GLIBC_PRIVATE```
        - In this case, type:
            - ```unset GTK_PATH``` and rerun the code
            - https://github.com/ros2/ros2/issues/1406 shows how to permanently set this on VSCode

