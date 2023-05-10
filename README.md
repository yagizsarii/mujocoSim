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
   </ul>
 </li>
 <li>
  <a href="#xml-file-preparation">XML File Preparation</a>
  <ul>
    <li><a href="#documentation">Documentation</a></li>
    <li><a href="#elements-and-subelements">Elements and SubElements</a></li>
  </ul>
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
   
# XML File Preparation

## Documentation

For detailed information, please visit the official [documentation link](https://mujoco.readthedocs.io/en/latest/XMLreference.html)

## Elements and SubElements 

There are elements and subelements on xml syntax. The common used elements are listed bellow as hierarchical.

- mujoco
  - asset
    - metarial
    - mesh
  - worldbody
    - light
    - geom
    - body
      - joint
      - geom
      - inertial
      - body (optional `related with upper body element`)
  - actuator
    - motor
    - position
    - velocity
  - sensor
    - jointpos
    - jointvel
  - keyframe
    - key

---

### mujoco

 mujoco is the main element which includes all sub elements together.

 
#### &nbsp; Attributes
  
  1. **model** : `string`
  
    The name of the model.

---

### asset

 This is a grouping element for defining assets.

#### &nbsp; No Attributes

---

### metarial

 Materials are useful for adjusting appearance properties beyond color

 
#### &nbsp; Attributes
  
  1. **name** : `string`
  
    Name of the material, used for referencing.
    
  2. **rgba** : `real(4)`

    Color and transparency of the material.

--- 

### mesh

  mesh can load  STL files, OBJ files or MSH files directly in the XML.
  
#### &nbsp; Attributes
  
  1. **name** : `string`
  
    Name of the mesh, used for referencing
    
  2. **file** : `string`

    The file name from which the mesh will be loaded.

--- 

### worldbody

   The element worldbody is used for the top-level body. It cannot have child elements inertial and joint, and also cannot have any attributes. It corresponds to the origin of the world frame
  
#### &nbsp; No Attributes
 
--- 

### light

  This element creates a light, which moves with the body where it is defined. If it defines on worldbody, it will be fixed.
  
#### &nbsp; Attributes
  
  1. **name** : `string`
  
    Name of the light.
    
  2. **pos** : `real(3)`

    Position of the light.

  3. **dir** : `real(3)`

    Direction of the light.

---

### geom

  This element creates a geom, and attaches it rigidly to the body within which the geom is defined.
  
#### &nbsp; Attributes
  
  1. **name** : `string` 
  
    Name of the geom.
    
  2. **type** : `plane, hfield, sphere, capsule, ellipsoid, cylinder, box, mesh)`

    Type of geometric shape

  3. **size** : `real(3)`

    Geom size parameters
   
  4. **pos** : `real(3)`

    Position of the geom, specified in the frame of the parent body.

---

### body

  This element is used to construct the kinematic tree. 
  
#### &nbsp; Attributes
  
  1. **name** : `string` 
  
    Name of the body.
    
  2. **pos** : `real(3)`

    The 3D position of the body frame, in the parent coordinate frame. If undefined it defaults to (0,0,0).

  3. **euler** : `real(3)`

    Rotation angles around three coordinate axes.
    
   4. **quat** : `real(3)`

    If the quaternion is known, this is the preferred was to specify the frame orientation because it does not involve conversions.

---

### joint

  This element creates a joint. A joint creates motion degrees of freedom between the body where it is defined and the body’s parent.
  
#### &nbsp; Attributes
  
  1. **name** : `string` 
  
    Name of the joint.
    
  2. **type** : `(free, ball, slide, hinge)`

    Type of the joint. 
    
    Free: Creates a free “joint” with three translational degrees of freedom followed by three rotational degrees of freedom. The rotation is represented as a unit quaternion. This joint type is only allowed in bodies that are children of the world body.
    
    Ball: Creates a ball joint with three rotational degrees of freedom. The rotation is represented as a unit quaternion.
    
    Slide: Creates a sliding or prismatic joint with one translational degree of freedom. Such joints are defined by a position and a sliding direction. 
    
    Hinge: Creates a hinge joint with one rotational degree of freedom. The rotation takes place around a specified axis through a specified position.

---

### inertial

  This element specifies the mass and inertial properties of the body. If this element is not included in a given body, the inertial properties are inferred from the geoms attached to the body.
  
#### &nbsp; Attributes
  
  1. **pos** : `real(3)` 
  
    Position of the inertial frame. This attribute is required.
    
  2. **mass** : `real`

    Mass of the body. Negative values are not allowed. 

  3. **diaginertia** : `real(3)`

    Diagonal inertia matrix, expressing the body inertia relative to the inertial frame. 

---

### actuator

  This element creates a general actuator, providing full access to all actuator components and allowing the user to specify them independently.
  
#### &nbsp; No Attributes

---

### motor

  This element creates a direct-drive actuator. 
  
#### &nbsp; Attributes
  
  1. **name** : `string` 
  
    Name of the actuator.
    
  2. **ctrllimited** : `false, true, auto`

    If true, the control input to this actuator is automatically clamped to ctrlrange at runtime.

  3. **ctrlrange** : `real(2)`

    Range for clamping the control input.  
    
  4. **joint** : `string`

    Name of the joint which is related to actuator.

---

### position

  This element creates a direct-drive actuator. 
  
#### &nbsp; Attributes
  
  1. **name** : `string` 
  
    Name of the actuator.
    
  2. **joint** : `string`

    Name of the joint which is related to actuator.
    
  3. **kp** : `real`

    Position feedback gain.
    
---
 
### velocity

  This element creates a direct-drive actuator. 
  
#### &nbsp; Attributes
  
  1. **name** : `string` 
  
    Name of the actuator.
    
  2. **joint** : `string`

    Name of the joint which is related to actuator.
    
  3. **kv** : `real`

    Velocity feedback gain.

---
 
### sensor

  This is a grouping element for sensor definitions.
  
#### &nbsp; No Attributes

---

### jointpos

  This element creates a direct-drive actuator. 
  
#### &nbsp; Attributes
  
  1. **name,** : `string` 
  
    Name of the sensor.
    
  2. **joint** : `string`

    Name of the joint which is related to actuator.
    
  3. **noise** : `real`

    The standard deviation of zero-mean Gaussian noise added to the sensor output, when the sensornoise attribute of flag is enabled.
    
---

### jointvel

  This element creates a direct-drive actuator. 
  
#### &nbsp; Attributes
  
  1. **name,** : `string` 
  
    Name of the sensor.
    
  2. **joint** : `string`

    Name of the joint which is related to actuator.
    
  3. **noise** : `real`

    The standard deviation of zero-mean Gaussian noise added to the sensor output, when the sensornoise attribute of flag is enabled.
    
---

   **An example which includes all elements is added as an pendulum. To check, click [the link](https://github.com/yagizsarii/mujocoSim/tree/main/projects/pendulum).**
   
   
   
   

















