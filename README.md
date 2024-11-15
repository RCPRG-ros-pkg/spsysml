# Repository content
* Simulation-Physical System meta-model: Simulation-Physical System MOdeling Language (SPSysML), 
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
Aa SPSysML bases on SysML, to start working with SPSysML it is convenient to:
1.	Learn basics of SysML as a MBSE tool, e.g.:
* Friedenthal, Sanford, Alan Moore, and Rick Steiner. A practical guide to SysML: the systems modeling language. Morgan Kaufmann, 2014.
* Delligatti, Lenny. SysML distilled: A brief guide to the systems modeling language. Addison-Wesley, 2013.
2.	Choose the development software that supports SysML projects (e.g. Enterprise Architect, Visual Paradigm),
3.	The [SPSysML](spsys-profile.xml) profile, that defines SPsysML stereotypes, and [SPsysML project documentation](spsys-doc.pdf) can be helpful.


## SPSys Application Procedure (SPSysAP)
<p align="center">
<img src="https://github.com/RCPRG-ros-pkg/spsysml/raw/main/spsysdp-radmap.png"  width="600">
</p>

## The example procedure for the evaluation factors calculation
Popular tools for SysML modelling implement the model as an SQL database and supply request interface to the database. The tool for automating the review process should utilise the interface to the SQL server. The following procedure is the minimum viable product easing evaluation factor calculation:
1. In the Enterprise Architect modelling tool, execute the following SQL request to the database:\\
```sql
select o.ea_guid as CLASSGUID, o.Object_Type as CLASSTYPE, 
       o.name as Name ,package.name as 'Package Name'
from ((t_object o
    left join t_xref stereo on stereo.Client = o.ea_guid)
    inner join t_package package on o.package_id = package.package_id)
where 
    o.Stereotype like '#WC#<Search Term>#WC#' and
    stereo.description like '@STEREO;Name=#WC#<Search Term>#WC#;#WC#' and
    package.name = '<Evaluation scope>' and
    o.Object_type = 'Class'
```
Use each parameter from the evaluation factor equations as the 'Search term', e.g. 'SimPhyContSubsys' and 'ContSubsys' for the Controller integrity factor. The search must be filtered for the framed-scope evaluation factor, such as the mirror integrity factor. The system model can be filtered by a package name. If the system model is decomposed to packages containing separate DT/PT pairs, the package name can be set as the 'Evaluation scope' in line 9 of the above listing.  

2. Count rows for each parameter from the evaluation factor equations or use the SQL 'COUNT' function.
3. Put the count result to the equations defining the evaluation factors.

# Novelty
The key novel features delivered by SPSysML and SPSysDP are:
* Integrity evaluation with quantitative factors,
* SysML-based structure model and system development procedure,
* System design optimisation considering simulation and physical embodiments of the system,
* Multiple system execution and testing setups specification,
* Forcing simulation-based testing prior to physical embodiment development,
* Specification of Simulation-Physical System including multiple physical and simulated parts and multiple Digital Twins,
* Reflection of the dynamic environment in simulation to enable Digital Twins to observe exogenous actions
