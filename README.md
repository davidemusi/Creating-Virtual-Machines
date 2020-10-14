arrow_back
Creating Virtual Machines
avatar image
15/15
Checkpoints
Create a utility virtual machine

Check my progress
5 / 5

Create a Windows virtual machine

Check my progress
5 / 5

Create a custom virtual machine

Check my progress
5 / 5

00:35:23
Caution: When you are in the console, do not deviate from the lab instructions. Doing so may cause your account to be blocked. Learn more.

Username
student-04-92e8fdec65f6@qwiklabs.net
Password
rG3Zxq5dpsNJ
GCP Project ID
qwiklabs-gcp-04-64fecb7cf953
Overview
Objectives
Task 1: Create a utility virtual machine
Task 2: Create a Windows virtual machine
Task 3: Create a custom virtual machine
Task 4: Review
End your lab
Creating Virtual Machines
1 hour
Free
Rate Lab
Overview
In this lab, you will explore the Virtual Machine instance options and create several VMs with different characteristics.

Objectives
In this lab, you explore the available options for VMs and see the differences between locations.

In this lab, you learn how to perform the following tasks:

Create several standard VMs

Create advanced VMs

Qwiklabs setup
For each lab, you get a new GCP project and set of resources for a fixed time at no cost.

Make sure you signed into Qwiklabs using an incognito window.

Note the lab's access time (for example, img/time.png and make sure you can finish in that time block.

There is no pause feature. You can restart if needed, but you have to start at the beginning.

When ready, click img/start_lab.png.

Note your lab credentials. You will use them to sign in to Cloud Platform Console. img/open_google_console.png

Click Open Google Console.

Click Use another account and copy/paste credentials for this lab into the prompts.

If you use other credentials, you'll get errors or incur charges.

Accept the terms and skip the recovery resource page.
Do not click End Lab unless you are finished with the lab or want to restart it. This clears your work and removes the project.

Task 1: Create a utility virtual machine
Create a VM
In the Cloud Console, on the Navigation menu (7a91d354499ac9f1.png), click Compute Engine > VM instances.
Click Create.
For Name, type a name for your instance. Hover over the question mark icon for advice about what constitutes a properly formed name.
For Region and Zone select us-central1 and us-central1-c respectively.
For Machine configuration, select Series as N1.
For Machine type, examine the options.
Notice that the menu lists the number of vCPUs, the amount of memory, and a symbolic name such as n1-standard-1. The symbolic name is the parameter you would use to select the machine type if you were creating a VM using the gcloud command. Notice to the right of the zone and machine type that there is a per-month estimated cost.

Click Details to the right of the Machine type list to see the breakdown of estimated costs.
For Machine type, click n1-standard-4 (4 vCPUs, 15 GB memory). How did the cost change?
For Machine type, click n1-standard-1 (1 vCPUs, 3.75 GB memory).
For Boot disk, click Change.
Click Version and select Debian GNU/Linux 10 (buster).
Click Select.
Click Management, security, disks, networking, sole tenancy.
Click Networking.
For Network interfaces, click the Edit icon (Edit).
Select None for External IP.
Click Done.
Leave the remaining settings as their defaults, and click Create. Wait until the new VM is created.
External IP addresses that don’t fall under the Free Tier will incur a small cost.
Explore the VM details
On the VM instances page, click on the name of your VM.
Locate CPU platform and note the value. Click Edit.
Notice that you can't change the machine type, the CPU platform, or the zone.

You can add network tags and allow specific network traffic from the internet through firewalls.

Some properties of a VM are integral to the VM, are established when the VM is created, and cannot be changed. Other properties can be edited. You can add additional disks and you can also determine whether the boot disk is deleted when the instance is deleted. Normally the boot disk defaults to being deleted automatically when the instance is deleted. But sometimes you will want to override this behavior. This feature is very important because you cannot create an image from a boot disk when it is attached to a running instance. So you would need to disable Delete boot disk when instance is deleted to enable creating a system image from the boot disk.

Examine Availability policies.
You can't convert a non-preemptible instance into a preemptible one. This choice must be made at VM creation. A preemptible instance can be interrupted at any time and is available at a lower cost.

If a VM is stopped for any reason, (for example an outage or a hardware failure) the automatic restart feature will start it back up. Is this the behavior you want? Are your applications idempotent (written to handle a second startup properly)?

During host maintenance, the VM is set for live migration. However, you can have the VM terminated instead of migrated.

If you make changes, they can sometimes take several minutes to be implemented, especially if they involve networking changes like adding firewalls or changing the external IP.

Click Cancel.

Explore the VM logs
On the VM instance details page for your VM, click Cloud Logging.
Notice that you have now navigated to the Cloud Logging page.

This is a structured log view. At the top you can filter by using the pull-down menus, and there is a search box for searching based on labels or text.

Click the small triangle to the left of one of the lines to see the kind of information it contains.
On the far right, click View Options > Expand All.
Click Check my progress to verify the objective.

Create a utility virtual machine
Task 2: Create a Windows virtual machine
Create a VM
On the Navigation menu (7a91d354499ac9f1.png), click Compute Engine > VM instances.
Click Create instance.
Specify the following, and leave the remaining settings as their defaults:
Property	Value (type value or select option as specified)
Name	Type a name for your VM
Region	europe-west2
Zone	europe-west2-a
Series	N1
Machine type	n1-standard-2(2 vCPUs, 7.5 GB memory)
Boot disk	Change
Public Images > Operating system	Windows Server
Version	Windows Server 2016 Datacenter Core
Boot disk type	SSD persistent disk
Size (GB)	100
Click Select.
For Firewall, enable Allow HTTP traffic and Allow HTTPS traffic.
Click Create.
When the VM is running, notice that the connection option in the far right column is RDP, not SSH. RDP is the Remote Desktop Protocol. You would need the RDP client installed on your local machine to connect to the Windows desktop.

Note: Installing an RDP client on your local machine is outside the scope of this lab and of the class. For this reason, you will not be connecting to the Windows VM during this lab. However, you will step through the usual procedures up to the point of requiring the RDP client.

Instructions for connecting to Windows VMs are here:

https://cloud.google.com/compute/docs/instances/windows/connecting-to-windows-instance

Set the password for the VM
Click on the name of your Windows VM to access the VM instance details.
You don't have a valid password for this Windows VM: you cannot log in to the Windows VM without a password. Click Set Windows password.
Click Set.
Copy the provided password, and click CLOSE.
You will not connect to the Windows VM during this lab. However, the process would look something like the following (depending on the RDP client you installed). The RDP client shown can be installed for Chrome here:

https://chrome.google.com/webstore/detail/chrome-rdp-for-google-clo/mpbbnannobiobpnfblimoapbephgifkm?hl=en-US

On the VM instances page, you would click RDP for your Windows VM and connect with the password copied earlier.

Click Check my progress to verify the objective.

Create a Windows virtual machine
Task 3: Create a custom virtual machine
Create a VM
On the Navigation menu (7a91d354499ac9f1.png), click Compute Engine > VM instances.
Click Create instance.
Specify the following, and leave the remaining settings as their defaults:
Property	Value (type value or select option as specified)
Name	Type a name for your VM
Region	us-west1
Zone	us-west1-b
Series	N1
Machine type	Custom
Cores	6 vCPU
Memory	32 GB
Boot disk	Debian GNU/Linux 10 (buster)
Click Create.

Connect via SSH to your custom VM
For the custom VM you just created, click SSH.

To see information about unused and used memory and swap space on your custom VM, run the following command:

free
To see details about the RAM installed on your VM, run the following command:

sudo dmidecode -t 17
To verify the number of processors, run the following command:

nproc
To see details about the CPUs installed on your VM, run the following command:

lscpu
To exit the SSH terminal, run the following command:

exit
Click Check my progress to verify the objective.

Create a custom virtual machine
Task 4: Review
In this lab, you created several virtual machine instances of different types with different characteristics. One was a small utility VM for administration purposes. You also created a standard VM and a custom VM. You launched both Windows and Linux VMs and deleted VMs.

End your lab
When you have completed your lab, click End Lab. Qwiklabs removes the resources you’ve used and cleans the account for you.

You will be given an opportunity to rate the lab experience. Select the applicable number of stars, type a comment, and then click Submit.

The number of stars indicates the following:

1 star = Very dissatisfied
2 stars = Dissatisfied
3 stars = Neutral
4 stars = Satisfied
5 stars = Very satisfied
You can close the dialog box if you don't want to provide feedback.

For feedback, suggestions, or corrections, please use the Support tab.

Copyright 2020 Google LLC All rights reserved. Google and the Google logo are trademarks of Google LLC. All other company and product names may be trademarks of the respective companies with which they are associated.


