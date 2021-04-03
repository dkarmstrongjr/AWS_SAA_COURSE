Cloud Computing Fundamentals
============================
------------------------------

Cloud Computing Definition:
------------------------------

1) On demand self service 
  - Provision and terminate using a UI/CLI without human interaction.

2) Broad Network Access
  - Capabilities are available over the network and accessed through standard mechanisms.
  - Accessed services over standard network like http, https, ssh, or vpn

3) Resource Pooling
  - There is a sense of location independence, no control or knowledge over the exact location of the resources
  - Resources are pooled to serve multiple consumers using a multi-tenant model
  - Economies of scale, cheaper service
  
4) Rapid Elasticity
  - Capabilities can be elastically provisioned and released to scale rapidly outward and inward with demand
  - To the consumer, the capabilities available for provisioning often appear to be unlimited
  - Scale UP(OUT) and DOWN(IN) automatically in response to system load

5) Measured Service
  - Resource usage can be monitored, controlled, reported and billed
  - Usage is measured. Pay for what you consume


Public vs Private vs Multi vs Hybrid Cloud
--------------------------------------------

Public cloud - A cloud environment that is accessible to the public, using 1 public cloud
Multi cloud - Using multiple cloud providers, more than 1 public cloud
Private cloud - Using a cloud provider that stores your resources offline, on prem equipmen. Using on premises real cloud
Hybrid cloud - Using private and public cloud. Hybrid cloud is **not** public cloud + legacy on-premises

Cloud Service Models
---------------------

**Infrastructure stack** or **Application stack** - collection of things which that an application needs all stack onto each other
- Facilities - Building with power, with air condition, with physical security 
- Infrastructure - storage and networking
- Servers - an app generally requires one or more physical servers. These servers run virtualization, which allows them to be carved into VMs
- Virtualization - These virtual machines run Operating Systems,
- O/S
- Container
- Runtime - Every app is written in a language such as python etc, an all have an environement that they need to run in. This is called a runtime environment
- Data - An app needs data to work on, which it creates or consumes
- Application

Parts that you manage 
Parts managed by the vendor 
Unit of consumption 

**IAAS:**
You manage:
- OS
- Container
- Runtime
- Data
- App

Vendor Manages:
- Facilities
- Infrastructure
- Servers
- Virtualization

**PAAS**
You manage:
- Runtime
- Data
- App

Vendor manages everything else

**SAAS**
Consume Application 
e.g Netflix, dropbox 

  
