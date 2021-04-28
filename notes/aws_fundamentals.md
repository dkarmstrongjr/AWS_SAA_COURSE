AWS Fundamentals
=================

AWS Global Infrastructure
--------------------------
- Geographic Separation - Isolated Fault Domain
- Geopolitical Separation - Different governance
- Location Control - Performance. Can place infrastructure to your customers close as possible and duplicate infrastructure for demand if necessary
- **Service Resilience** - 1) Global resilient, would take world to fail for service to have an outage. 2) Region resilient, operate as seperate service in each region. If an AZ in a region fails a service can still operate. 3) AZ resilient, are prone to failuire if you have in problems in that AZ. 

Virtual Private Cloud (VPC) Basics
-----------------------------------
- A VPC = A virtual network inside AWS - Are regionally resilient
- A VPC is within 1 account and 1 region 
- Private and Isolated unless you decide otherwise
- Two types - Default VPC and Custom VPCs - **can only have 1 default VPC per region**, can have many custom VPC
- Every VPC is allocated a range of IPs called the VPC CIDR - defines the start and end range that VPC can use
- Custom VPC can have multiple CIDR ranges but default can only get 1 
**Default VPC Facts**
  - One per region - can be removed and recreated
  - Default VPC cidr is always 172.31.0.0/16
  - /20 subnet in each AZ in the region
  - Internet Gateway, Security Group and NACL
  - Subnets assign public IPv4 addresses

Simple Storage Service (S3 basics)
----------------------------------
- Global Storage Platform - regional based/resilient
- Public service, unlimited data & multi-user
- Perfect for hosting large amounts of data - Movies, Audio, Photos, Text, Large Data sets
- Economical & accessed via UI/CLI/API/HTTP
- Objects and buckets 
- Bucket names are globally unique
- 3 - 63 characters, all lowercase, no underscores
- cant be IP formatted 
- Buckets - 100 soft limit, 1000 hard per account
- Unlimited objects in a bucket, 0 bytes to 5TB
- Key = Name, Value = data
- S3 is an object store - not file or block
- You **cant Mount** an s3 bucket as (K:\ or /images)
- Great for large scale data storage, distribution or upload
- Great for offload

Shared Responsibility Model
----------------------------
Customer - Responsible for security in the cloud
AWS - Responsible for security of the cloud

High Availability vs Fault Tolerance vs Disaster Recovery
----------------------------------------------------------

**High Availability** (HA) - Aims to ensure an agreed level of operational performance usually uptime, for a higher than normal period.
- Maximizing a systems online time. Minimizing any outages.
**Fault Tolerance (FT)** - The property that enables a system to continue operating properly in the event of the failure of some (one or more faults within) of it components
- Operate thru faults
**Disaster Recovery (DR)** - a set of policies, tools and procedures to enable the recovery or continuation of vital technology infrastructure and systems following a natural or human induced disaster
- What we do when HA and FT dont work

Domain Name System (DNS) Fundamentals
--------------------------------------
- DNS is a discovery service 
- Translates machine into human and vice versa
- amazon.com => 104.98.34.131
- Its huge and has to be distributed 
- **DNS Client** - your laptop, phone, tablet, pc
- **Resolver** software on your device, or a server which queries DNS on your behalf
- **DNS Zone** - a part of the DNS database
- **Zonefile** - a physical database for a zone
- **DNS Nameserver** where zonefiles are hosted
- **Root Hints** - config points at the root servers IPs and addresses.
- **Root Server** - hosts the DNS root zone
- **Root Zone** - points at the TLD authoritative servers
- **gTLD** - generic top level domain (.com .org)
- **ccTLD** - country-code top level domain (.uk .eu etc)
