### Google Cloud Platform

This repository will have important concepts related to Google Cloud Platform.

Organization ==========> Folder  ==========> Project

![image](https://user-images.githubusercontent.com/21220549/207267758-287a7329-1189-425f-99d5-ef3a112228d8.png)

Global, regional, and zonal resources in GCP: https://cloud.google.com/compute/docs/regions-zones/global-regional-zonal-resources

Global resources are accessible by any resource in any zone within the same project. Following is the list of GCP global resources:

1. Images
2. Snapshots
3. Network
4. Firewalls
5. Routes
6. Global Operations (operations on global resources)


#### *1. Compute Engine*

i. A zone is a deployment area for Google Cloud resources within a region. 

ii. To deploy fault-tolerant applications with high availability and help protect against unexpected failures, deploy your applications across multiple zones in a region.

iii. Machine Family [GCP]

    a. General Purpose      ==============>         E2, N2, N2D etc based on memory and processors.
    
    b. Compute Optimized      ==============>       Most intensive workloads, C2, C2D
    
    c. Memory Optimized      ==============>        RAM in terabytes, highly expensive servers for memory intensive applications.
    
    d. GPU      ==============>     Compute Engine provides graphics processing units (GPUs), good for machine learning and data processing workloads.
    
    
Confidential VM service is for end to end encryption. 

We can even deploy a Docker container with the *Deploy Container* option. We can set the default location of instances in the **Settings** option down at the bottom.


#### *2. Boot Disk*

If we deploy a container, then by the default the container images are selected with Docker Engine pre-installed. Otherwise, we can use any other official image from GCP images section.

#### *3. Instance Deletion Protection*

1. Instance Deletion Protection: Deletion rule   ===========>  Go to management down below while creating the instance and enable the Deletion Protection. You have to disable it to delete the instance. Edit the instance and disable it.

2. When deleting instance, "Delete Boot Disk" is Enabled by default which means your disk will be deleted automatically after the instance is deleted. Select "Keep Boot Disk" if you want to keep the disks even after deleting the instance for creating new instances.

3. Data is encrypted automatically by GCP, but we have the choice by using our own keys for the encryption as known as Customer Supplied Encryption Keys.

4. SSD persistent disks are expensive, just keep that in mind.

#### *3.1. Instance Templates*
Create instance templates of your choice and save them. These instance templates will be used to create VMs using a single click. Instance templates are free and can save a lot of time while creating new VMs. The VMs are created according to the machine family of the instance template.

#### *3.2 Deploy Container*

1. Processes in a privileged container are equivalent to processes running as root on the host.
2. The OS will have Docker pre-installed on that instance.

========================================================================

#### *Important Commands for GCP*

a. Sample of gcloud command to connect via GCP Shell: 

gcloud compute ssh --zone "us-central1-a" "jazavm-1"  --project "terraform-354707"

b. The following command will revoke the account access on your personal machine

gcloud auth revoke --all

gcloud auth application-default revoke

Credentials are saved in: 

/root/.config/gcloud/application_default_credentials.json

./google-cloud-sdk/bin/gcloud init

c. Sign in to the gcloud CLI, open the URL in the browser to get the code, copy the code on your VM and you will be logged in.

gcloud auth application-default login --no-launch-browser

d. Set the project ID 

gcloud config set project PROJECT_ID

e. My project ID is terraform-354707, the command will be executed like:

gcloud config set project terraform-354707

========================================================================

#### *SSH Connectivity with a VM*

Run these commands on your local machine to access a GCP VM from Ubuntu machine:

a. which gcloud

b. gcloud config configurations list

c. gcloud compute instances list

d. gcloud compute ssh jazavm-1 --zone=us-central1-a

========================================================================

#### *Tenant Nodes*

Large servers with huge specs to create multiple VMs, good for huge workloads.

========================================================================

#### *Machine Images*

Create your own images with default configurations and save as machine images. Once you'll create new VM instances, the configurations will be automatically replicated in the new instance from those machine images.

#### *Google TPU*

TPUs stand for Tensor Processing Units, these are circuits developed by Google for Machine Learning stuff.

========================================================================

#### *Committed use discounts*

Just like reserved instances in AWS, you can purchase Compute Engine resources in GCP for an affordable price and on discounted rates for a term of 1-3 years.

#### *VM Migration API*

It is used to migrate virutal machines from your on-premise datacenter to the Google Cloud.

========================================================================

#### *Disks*

A. Standard persistent disks  ===>  minimum 10 GB

B. Balanced persistent disks  ===>  minimum 10 GB

C. SSD persistent disks   ===>  minimum 10 GB

D. Extreme persistent disks  ===>  minimum 500 GB

1. A disk can be created in a single zone or regional.

2. While creating a disk, we can create a failover replica in the same region for high availability which is **Regional**, created in multiple zones like us-central1-a, us-central1-c. We can create blank disks and snapshots in regional locations, images can not be created in that option.

3. Snapshot schedule will create automatic disk backups. 

4. We can change the boot disk from "boot disk" option, we can also attach existing disk to a new VM. SSD disks are expensive. 

5. Create disks, snapshots and images and from each one of them, we can launch a new VM. Snapshots are backups of persistent disks. We cannot delete a disk that is attached to a VM.

6. The **Snapshot schedule** option helps to regularly and automatically back up persistent disks.

7. We can not change/edit a snapshot schedule after creating it.

========================================================================

#### *GCP Bare Metal Servers [Bare Metal Solution]*

1. These servers are offered by Google to handle special workloads for highly intensive traffic or applications. Servers with upto 112 cores and 3TB of RAM can be ordered.

2. We need to order Volumes, NFS storage, Networks and Servers via contacting the GCP team.

========================================================================

#### *Instance Groups*

1. An instance group is a collection of VMs which we can manage as a single entity. 

2. In managed instance groups, we get the features like auto-healing, auto-scalaing and multi-zone deployments. Whereas, in un-managed instance groups, we do not get the features like that and we have to manage those VMs ourselves.

3. Stateless Managed Groups are for applications that don't need any data, like website frontend where the server does not store any data.

4. Stateful Managed Groups are for applications that save data and require database.

5. Auto-scaling automatically adds and removes instances to the instance group for high and low loads, cpu usage. 

6. Auto-healing adds new instances if a certain health check is failing. Therefore, we add certain health checks for the webserver on port 80 with necessary thresholds. 

7. We can create a load balancer and use our instance group with instances to balance the traffic as per: https://www.youtube.com/watch?v=304n_19cdoc&t=360s

8. For higher availability, select multiple zones in a region instead of a single zone while creating the MIG.

9. The **cool down period** is also known as the **application initialization period**.

10. Check interval means after every 5 or 10 seconds [depending on your threshold], a health check is triggered. If the timeout is set to 5 seconds and we don't get a response from the server, it will be considered as failure. 

11. 3 consecutive successes mean the instance is in a healthy state and 3 consecutive failures mean the instance is not in a health state.

12. Initial delay means giving the application to be on the track in autohealing. If we give 60 seconds, it means the web service or any service for which the health check is created will take a minute to be fully functional.

========================================================================

#### *OS Patch Management*

1. In GCP, OS patch management helps to apply operating system patches on VMs. The VMs that are running for a long time need system updates and **OS patch management** helps to protect them from vulnerabilities via patch deployment.

That's it for the GCP Compute Engine, we'll move to the next sections. 

========================================================================

### IAM and Admin

1. For the proper hierarchy, we should create an organization in our account. The resources are grouped into a single node. 
The good structure should look as: ****"My Organization =========> Folders =========> Project =========> Resources." ****

2. IAM stands for Identity and Access Management. 

3. There'll be a main account like "faisal.rehman22@gmail.com" and multiple service accounts. The service accounts are different and not like the actual account. The service account is created by GCP so that we can access particular GCP services using that service account. You can say it's a non-human user.

4. Permissions to the GCP resources are given in the form of roles. **Roles are "viewer, editor and owner".** We can create our own roles known as customer roles.

5. Add "service account user" for a certain user to grant access for creating resources. 

### GCP IAM change

    1. Go to https://console.cloud.google.com
    2. Go to IAM
    3. Find your email address
    4. Member -> Edit -> Add Another Role -> type in the role name Service Account User -> Add

6. The principal means the username or Google account whom you want to give access, in my case, I've shared the access with softwarespice2020@gmail.com account.
7. Compute Admin Role gives "Full control of all Compute Engine resources." 

## Roles:

1. **Browser**:    Access to browse GCP resources.
2. **Editor**:     View, create, update and delete most Google Cloud resources. See the list of included permissions.
3. **Owner**:      Full access to most Google Cloud resources.
4. **Viewer**:     View most Google Cloud resources.

In my example, I've set a condition to allow the GCP user(softwarespice2020) to use the compute resources only on Weekdays and not on weekends.

## Cloud Identity:

GCP Cloud Identity is a service to manage users, apps and devices from the GCP console.

## Cloud Storage:

Just like AWS S3, simple storage service, GCP storage is known as Google Cloud Storage. Bucket name should be globally unique. 

There are 3 location types while creating our bucket:
1. Multi Region ====> The bucket will be created across multiple regions.
2. Dual Region ====> The bucket will be created across 2 regions.
3. Region ====> The bucket will be created in a single region. 

The prices will vary according to the regions. Obviously multi-region buckets will cost a little more as compared to the single region.

### Storage Classes

There are 4 types of storage classes in GCP Cloud Storage.

1. Standard
2. Nearline
3. Coldline
4. Archive

### Access Control Lists

1. **Unfiorm**      ====>   Its about bucket-level permissions, IAM permissions are set on the whole bucket.
2. **Fine-grained** ====>   If we want to set the object level permissions, setting permissions on each object individually. It is basically enhancement of the bucket-level permissions.

### Protection/Life-cycle Rules

GCP takes a lot of care of our data protection with the help of the following 2 methods also known as life-cycle rules.

1. **Object versioning**    ===>    Simply, multiple copies of the same file/image/object created to avoid deletion or over-writing. Later on, we can restore the specific version of that file.
2. **Retention**            ===>    Let's suppose we create a bucket and I set that the bucket and it's object **CAN NOT be deleted in 60 days**, it will be called as our retention policy and it'll protect our bucket and it's objects for the next 60 days.

Object versioning and retention policies cannot be on at the same time.

### Manage Holds

1. Temporary Holds      ====> It will protect your files from getting deleted. When you'll impose the temporary hold, you will NOT be able to delete a certain object.
2. Event-based Holds    ====> An event-based hold resets the object's time in the bucket for the purposes of the retention period.

### Private/Public Access

If you want your objects to be accessed publically, click on the 3 dots at the end of that object ====> Edit Access ===> Add new Entry ====> Select Public ===> All Users ===> Reader Access. After that save and check the image/file again in the browser, it should be publically accessible. Remember, you can do that in Fine-grained access control policy.

A retention policy protects objects in this bucket from being deleted or overwritten.

![When public access is prevented forcely on the bucket](https://user-images.githubusercontent.com/21220549/187438213-1a2d32b9-6ccd-4110-b674-35da8580b55b.PNG)

When we allow the public access to the object, it is possible in Fine-grained access control list.

I have set the retention policy as "One Day", it means we will be able to delete the bucket after one day.

![image](https://user-images.githubusercontent.com/21220549/187439559-183ee1e5-d902-49fd-82c8-5e267062b2d1.png)

## VPC Network:

VPC is a global resource, a VPC is software defined network. We will keep the IPv6 range disabled. Ingress means incoming traffic and egress means outgoing traffic.

### Subnets:

We can create more than ONE subnet per region.

There are 2 types of subnets:
1. **Custom**       =====> If we want to create our own customized subnet in a single or all regions. For instance, if we create a subnet in European region, then we would not be able to create a Compute Engine instance in the Asian/US or other regions until and unless we have the subnets for those regions.
2. **Automatic**    =====> Therefore, in Automatic subnets, a subnet is automatically created in all of the GCP regions.

### IP Stack Types:

There are 2 types of IP stacks.

1. Single stack means there will be only IPv4 IP range.
2. Dual stack means there will be both IPv4 and IPv6 ranges.

### Firewall Rules:

Ingress applies to incoming traffic. Egress applies to outbound traffic. Target can be set as all instances in the network. 0.0.0.0/0 means we are allowing the traffic from anywhere. Traffic rule applies only for the  protocols and ports we explicitly mention like 22, 443, 80 etc.

### Reserving External Static IPs:

There are 2 network service tiers, the premium network tier provides quality network over the standard tier. When we reserve a certain static IP, it will be charged on an hourly bases. Additional costs will be added if it's not used by any instance or a load balancer. You can reserve static private IP ranges like 20.0.0.0/24 etc. for your own VPC. 

For my own info, I have created the custom VPC in one region like us-east-1 and I will be able to create instances in this region only. The automatic subnetting creates subnets in every GCP region.

**The firewall rules with lower numbers get prioritised first.**
![rule1](https://user-images.githubusercontent.com/21220549/187945021-88637402-e199-4fab-b9b8-6ffda347e2de.PNG)

![rule 2](https://user-images.githubusercontent.com/21220549/187945059-04f88f98-db9d-4c2f-944f-da952cca03c6.PNG)

![image](https://user-images.githubusercontent.com/21220549/193213650-402ffc25-5ebf-4744-a1de-4a77c586f460.png)


We can add multiple rules in a single firewall policy and attach that firewall policy to service targets, all instances etc.

In the following diagram, you can see we have created a network policy on GCP with a single rule of allowing 22,80,443 ports from anywhere and attached it to the VPC network.

![policy](https://user-images.githubusercontent.com/21220549/187946117-280d0c2b-7f6e-472e-bcf1-102fbdfa5694.PNG)
