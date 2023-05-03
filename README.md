# MuJoCo 2.2.1

This repository has been created for explaining how to work on the MuJoCo simulation program and share custom example projects for `LINUX USERS`. 

The study has been carried out with reference from : https://github.com/deepmind/mujoco

The version that worked on is 2.2.1

To check more detail please visit referred link above.

And also during the study the Pranav Bhounsule's YouTube playlist was utilized. 

Link: https://youtube.com/playlist?list=PLc7bpbeTIk758Ad3fkSywdxHWpBh9PM0G

---
<!-- TABLE OF CONTENTS -->
# Contents

<ol>
 <li>
   <a href="#getting-started">Getting Started</a>
   <ul>
     <li><a href="#installation">Installation</a></li>
     <li><a href="#system-preparation">System Preparation</a></li>
     <li><a href="#system-test">System Test</a></li>
       <ul>
         <li><a href="#simulation-gui-test">Simulation GUI Test</a></li>
         <li><a href="#template-project-test">Template Project Test</a></li>
       </ul>
   </ul>
 </li>
 <li>
   <a href="#working-on-projects">Working On Projects</a>
   <ul>
     <li><a href="#custom-project-preparation">Custom Project Preparation</a></li>
 </li>
</ol>

---

# Roadmap

- [x] Run the Simulation
- [x] Create Your Own Project
- [x] Examine xml Syntax
    - [ ] Create a Manipulator
    - [ ] Create Two Manipulators Together
- [x] Examine Main Code
    - [ ] Design Controller
- [ ] Use Jacobinan for Inverse Kinematics

# Getting Started

## Installation

   1. Clone the repository
```bash
git clone https://github.com/yagizsarii/mujocoSim.git
```
   
2. Install the prerequisites
```bash
sudo apt install libglfw3-dev
```
   
## System Preparation
   1. Run a terminal
``` bash
sudo -H nautilus
```
   2. Press CTRL+L and change directory as /url/lib
   
   3. Copy and paste two files from mujocoSim/lib to /usr/lib (libmujoco.so & libmujoco.so.2.2.1)
   
## System Test
 
#### Simulation GUI Test
   1. Locate terminal to mujocoSim/bin
   
   2. Run simulation
```sh
./simulate
```

   3. Drop the xml file from mujocoSim/model/humanoid/humanoid.xml on simulation screen.
   
   `If it works, simulation setuped well.`

#### Template Project Test
   
   1. Locate terminal to mujocoSim/projects/template/
```sh
cd ~/mujocoSim/projects/template/
```  

   2. Make the run_linux file executable
```sh
chmod +x run_linux
```  
   
   3. Run the compiler
```sh
./run_linux
```  

   `If it works, you can create and compile your custom project on next steps successfully.`
   
# Working On Projects
   
## Custom Project Preparation

   1. Copy and paste the template folder and rename. (e.g. myProject)
   
   2. Rename the hello.xml file. (e.g. firstproject.xml)
   
   3. Edit the main.c file: The filename should be set the same as xml file. (e.g., char filename[] = "firstproject.xml";
   
   4. Locate terminal to mujocoSim/projects/myProject/
```sh
cd ~/mujocoSim/projects/myProject/
``` 
  
  5. Run the compiler
```sh
./run_linux
``` 

   `If it worked, you could create and compile your custom project.`
   


   
   
   
   
   

















