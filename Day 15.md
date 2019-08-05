# **Cloud Computing**
**Computing:-** CPU + RAM

* Traditional name of Cloud Computing is **Virtual Computing**.
* We say Virtual, because we does not have that in real.

Branch or Categories of Cloud Computing:-
* **SAAS (Software as a Service) ->** Ex:- Google (GDrive), Microsoft (OneDrive), etc

* **STAAS (Storage as a Service) ->** Google Drive, OneDrive, etc

* **IAAS (Infrastructure as a Service)**

* **PAAS (Platform as a Service)**
* **DBAAS (Database as a Service)**
* **NAAS (Network as a Service)**

**Cloud Providers:-**
* AWS (Amazon Web Services) -> 
    * 61% of worldwide population used this
* Azure
* Google
* Openstack
* IBM

## **AWS**
1. IAAS -> ec2 (ELastic Compute Cloud)

**Need to know in AWS for AWS Certification Exam:-**
* Hardware ->
    * A physical Resource which is a combination of RAM, CPU, HDD and Networking Equipments
* Hypervisor ->
    * A program or a software which provides a service to host multiple OS on the free h/w resources
    * VMM (Virtual Machine Manager) 
    * Divides the RAM and CPU not the HDD in the Racks
    * Ex -> VMware, Virtual Box
    * Types:-
        * Type 1 or Bare Metal
            * Installed directly on the Hardware which don't need an OS to run on.
            * Ex ->
                * ESXI -> VMWare
                * XEN Server -> Citrix -> Used by AWS
                * RHEVH -> Redhat
                * Hyper-V -> Microsoft
                * Virtual Box -> Oracle

        * Type 2 or Hosted Hypervisor
            * Levels:-
                * Hardware
                * OS
                * Hypervisor
                * OS
            * Ex -> 
                * VMWare/ VMP -> VMWare
                * XEN -> Citrix -> Used by AWS
                * KVM -> Redhat
                * Virtual PC-> Micrsoft
                * VM -> Oracle

* Racks
    * Includes only Mother Board in Racks
    * **NOTE:-** It doesn't contain any HDD or SSD in computation Racks.
    * Smallest unit is Hardware then Rack then Cluster the Data Center then all Data Centers includes in Region as said by Amazon.
    * And Amazon said Data Center as Availability Zone
* Data Center
    * Atleast 2 Data Centers are placed in a Region by Amazon
    * Regions are basically the physical space (City or a Country)

* In Amazon, we say combination of RAM and CPU as ECU (Elastic Compute Unit)
* And for HDD we take it from EBS (Elastic Block Storage)
* And for OS Image it is AMI (Amazon Machine Images)
* And for Network it is VPC (Virtual Private Cloud)

### [Advanced Details] **Boot Straping:-**
* Does job whenever we launch an instance like create a user and set a password



## Tasks
* How much Maximum we can choose instances and why
Spot Instances
* Can we change Subnet Avaliabilty zone after launch and can we change it before launch
* What are the shutdown behaviours :- Stop, Terminate
* What is Tenancy
* T2/T3 Unlimited -> for using internet having very fast speed