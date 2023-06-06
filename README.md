This repository acts as a knowledge base for the [SeQuenC project](sequenc.de) that aims to provide a technical methodology and a platform for uniform design and execution of quantum applications for different quantum service providers.
As multiple pre- and post-processing steps in quantum programs are implemented on classical hardware, the emphasis is put on the workflow-based design and execution of quantum applications.
This repository intends to provide a comprehensive overview of the supported scenarios and involved actors, the SeQuenC platform architecture and the tools it encompasses.

# Table of Contents
* [SeQuenC Actors and Scenarios](#sequenc-actors-and-scenarios)
* [SeQuenC Platform Architecture](#sequenc-platform-architecture)
* [SeQuenC Tools](#sequenc-tools)
  * [Modeling and Execution of Quantum Workflows](#modeling-and-execution-of-quantum-workflows)
  * [Unification Layer](#unification-layer)
  * [Quantum Service Store](#quantum-service-store)  
  * [Deployment Automation](#deployment-automation)  

# SeQuenC Actors and Scenarios

The SeQuenC actors are as follows:

* Quantum Software Developer: responsible for implementation of quantum programs and testing.
* Workflow Modeler: responsible for modeling the workflow-based integration of classical and quantum parts that can be automatically enacted using a compatible workflow engine.
* Operations Engineer (Ops): responsible for delivery on the infrastructure and infrastructure testing.


Scenarios TBD

# SeQuenC Platform Architecture

The SeQuenC project aims to provide a platform covering both the design and runtime phases for unified execution of quantum applications on heterogeneous quantum cloud services.

![#sequenc-architecture](SeQuenC-Architecture.png)

The Architecture Diagram depicts the connections among the SeQuenC components. 


# SeQuenC Tools


## Modeling and Execution of Quantum Workflows
Quantum applications are inherently hybrid as they comprise both classical and quantum-specific parts.
For example, the input for quantum algorithms may need to be pre-processed using classical hardware.
Furthermore, post-processing steps may be needed too, e.g., error mitigation methods may need to be utilized due to the error-proneness of contemporary quantum devices.
Therefore, the SeQuenC architecture emphasizes the role of workflows for development of quantum applications and incorporates tools for graphical modeling of quantum workflows and their automated execution.

### Quantum Workflows Modeling Tool

| Items | Contents |
| --- | --- |
| **Short Description** | The Quantum Workflows Modeling Tool in SeQuenC is implemented using QuantME, a modeling and transformation framework that extends Camunda modeler to enable creating quantum workflow models. Specifically, it provides a graphical BPMN modeler supporting Quantum4BPMN modeling extension to ease the modeling of quantum workflows by providing explicit modeling constructs for the execution of quantum circuits and frequently-occurring pre- and post-processing tasks. Furthermore, it enables transforming quantum workflows using Quantum4BPMN modeling constructs to native BPMN workflows to retain their portability between different workflow engines. |
| **Documentation** | [Documentation](https://github.com/UST-QuAntiL/QuantME-TransformationFramework/tree/develop/docs) |
| **Repository** | <https://github.com/UST-QuAntiL/QuantME-TransformationFramework> |
| **Licence**| Licensed under the MIT License. |

### Workflow Engine

| Items | Contents |
| --- | --- |
| **Short Description** | The Workflow Engine in SeQuenC is based on Camunda Engine, a state-of-the-art BPMN workflow engine that runs inside the Java Virtual Machine and can be embedded inside any Java application and any Runtime Container. |
| **Documentation** | [Documentation](https://docs.camunda.org/get-started/) |
| **Repository** | <https://github.com/camunda/camunda-bpm-platform> |
| **Licence**| Licensed under the Apache License 2.0. |


## Unification Layer
Quantum computers are not commodity hardware and offered as cloud services by various providers including general-purpose cloud providers such as IBM and AWS, and specialized providers focusing on quantum computing use cases such as Rigetti or IonQ. 
One of the core requirements in SeQuenC is, therefore, to provide uniform mechanisms for executing quantum applications on various quantum cloud services overcoming their heterogeneous requirements and feature sets.
These uniform mechanisms for handling different quantum execution tasks, monitoring their status, etc. consitute the so-called Unification Layer in the SeQuenC platform architecture.

| Items | Contents |
| --- | --- |
| **Short Description** | The Unification Layer in SeQuenC is a new middleware component called Qunicorn that provides a uniform API for management and execution of quantum jobs on different service providers. |
| **Documentation** | [Documentation](https://qunicorn-core.readthedocs.io/en/latest/#) |
| **Repository** | <https://github.com/qunicorn/qunicorn-core> |
| **Licence**| Licensed under the Apache License 2.0. |


## Quantum Service Store

To facilitate the management and reuse of developed quantum programs and workflow models, the SeQuenC architecture incorporates a service store and management tool, which is integrated with other components of the platform.
For examples, quantum algorithm implementations can be referenced as parts of quantum workflows using the SeQuenC workflow modeling environment. 
Furthermore, to enable modeling custom provisioning requirements, the deployment automation tools in SeQuenC can be used to create custom executable deployment models for the quantum artifacts in the Service Store.

| Items | Contents |
| --- | --- |
| **Short Description** | The Service Store and Service Registry in SeQuenC are implemented based on the QC Atlas, an open source platform for sharing quantum software developed as part of the project PlanQK. Service Store enables the collection and management of information about quantum algorithms, available implementations, publications, available software platforms, cloud services, and their offered compute resources such as quantum computers and simulators. |
| **Documentation** | [Documentation](https://quantil.readthedocs.io/en/latest/user-guide/qc-atlas/) |
| **Repository** | <https://github.com/UST-QuAntiL/qc-atlas> / <https://github.com/UST-QuAntiL/qc-atlas-ui> |
| **Licence**| Licensed under the Apache License 2.0. |




## Deployment Automation
The SeQuenC platform architecture incorporates tools for modeling and enacting the automated deployment of quantum applications. 
Since the current prototype relies on TOSCA for deployment automation, to facilitate graphical creation of TOSCA models, the platform incorporates a GUI-based deployment modeling tool based on Eclipse Winery. 
The produced models can be enacted by TOSCA-compliant orchestrators such as OpenTOSCA Container, which is integrated in the prototype too.

### Deployment Modeling Tool

| Items | Contents |
| --- | --- |
| **Short Description** | The Deployment Modeling Tool in SeQuenC is developed based on Eclipse Winery, which is a web-based environment to graphically model TOSCA-based application topologies. It includes (i) a Management GUI for managing TOSCA types and templates, (ii) a Topology Modeler GUI that enables to graphically compose application topologies and specify configuration properties, and (iii) a file-based backend to store, import, and export TOSCA models. |
| **Documentation** | [Documentation](https://winery.readthedocs.io/) |
| **Repository** | <https://github.com/OpenTOSCA/winery> / <https://github.com/eclipse/winery> |
| **Licence**| Dual licensed under the Apache License 2.0 and Eclipse Public License 2.0. |


### Deployment Orchestrator

| Items | Contents |
| --- | --- |
| **Short Description** | The Deployment Orchestrator in SeQuenC is based on the OpenTOSCA Container, a TOSCA deployment automation engine that enables automatic provisioning of cloud applications by analyzing the TOSCA model and invoking the Build Plan to instantiate a new application instance. If there is no Build Plan available, the container generates a Build Plan on its own. To enable the management of a certain application instance during its lifetime, the OpenTOSCA Container is able to execute arbitrary Management Plans, which can be modeled manually or generated for provisioning. |
| **Documentation** | [Documentation](https://opentosca.github.io/container/) |
| **Repository** | <https://github.com/OpenTOSCA/container/> |
| **Licence**| Licensed under the Apache License 2.0. |
