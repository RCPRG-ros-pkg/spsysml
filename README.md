# Repository content
* Simulation-Physical System meta-model -- Simulation-Physical System MOdeling Language (SPSysML), 
* Simulation-Physical System Development Procedure (SPSysDP), 
* Example robot system model developed with SPSysML and SPSysDP.

# Simulation-Physical System (SPSys)
 This kind of system consists of at least one embodiment physical/simulated and a shared controller. If it has both embodiments, a simulated part can be a Digital Twin (DT) of a physical part. If it has only the physical embodiment, it is a Cyber-Physical System (CPS), and if it has only the simulated embodiment, it is a simulator.
 
## SPSys Concept
<p align="center">
<img src="https://user-images.githubusercontent.com/7499883/223860003-b54a8238-6fe2-45c9-9df6-2c7b507df481.png"  width="400">
</p>

## SPSys Modeling Language (SPSysML)
SPSysML defines the taxonomy of a Simulation-Physical System (SPSys) and relationships between its parts. SPSysML models constraints in this kind of systems and enables structure optimisation using proposed design evaluation factors. 

### SPSysML usage

## SPSys Development Procedure (SPSysDP)
<p align="center">
<img src="https://github.com/RCPRG-ros-pkg/spsysml/raw/main/spsysdp-radmap.png"  width="600">
</p>

# Novelty
The key novel features delivered by SPSysML and SPSysDP are:
* Integrity evaluation with quantitative factors,
* SysML-based structure model and system development procedure,
* System design optimisation considering simulation and physical embodiments of the system,
* Multiple system execution and testing setups specification,
* Forcing simulation-based testing prior to physical embodiment development,
* Specification of Simulation-Physical System including multiple physical and simulated parts and multiple Digital Twins,
* Reflection of the dynamic environment in simulation to enable Digital Twins to observe exogenous actions
