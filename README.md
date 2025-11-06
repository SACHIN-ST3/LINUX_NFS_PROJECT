#                  RedHat NFS Project

# **🎯 Objective:**

Set up an NFS Server to share a directory and mount it on one or more NFS Clients. NFS allows users to access shared directories and files over a network.

# **🧱 STEP 1: NFS Server Installation (on Server Machine)**

* Install NFS utilities:

  ***sudo dnf install nfs-utils \-y***
  
 ![image alt](https://github.com/SACHIN-ST3/LINUX_NFS_PROJECT/blob/56db528592ac52d726ddc9f935cdc27d35ae3750/NFS_PROJECT/Screenshot%202025-11-06%20215738.png)

  

* Enable and start NFS services:

  ***sudo systemctl enable  nfs-server***  
  ***sudo systemctl start nfs-server***  
  ***sudo systemctl status nfs-server***
 ![image alt](https://github.com/SACHIN-ST3/LINUX_NFS_PROJECT/blob/56db528592ac52d726ddc9f935cdc27d35ae3750/NFS_PROJECT/Screenshot%202025-11-06%20215917.png)

  


# **📁 STEP 2: Create and Export a Shared Directory**

* Create and set permissions:

  ***sudo mkdir \-p /mnt/nfs\_share***  
  ***sudo chown \-R nobody:nogroup /mnt/nfs\_share***  
  ***sudo chmod 777 /mnt/nfs\_share*** 

  ***Cd  /mnt/nfs\_share/ —\> make (mkdir)  sachin-bro33***
  ![image alt](https://github.com/SACHIN-ST3/LINUX_NFS_PROJECT/blob/56db528592ac52d726ddc9f935cdc27d35ae3750/NFS_PROJECT/Screenshot%202025-11-06%20220044.png)

* Configure /etc/exports:

  ***sudo vim  /etc/exports***  
  ***Add: /mnt/nfs\_share   192.168.161.133:(rw,sync,no\_root\_squash,no\_subtree\_check)***  
  ***sudo exportfs \-a***
  ![image alt](https://github.com/SACHIN-ST3/LINUX_NFS_PROJECT/blob/56db528592ac52d726ddc9f935cdc27d35ae3750/NFS_PROJECT/Screenshot%202025-11-06%20220151.png)

# 

# **🔥 STEP 3: Configure Firewall (on Server)**

***sudo firewall-cmd \--permanent \--add-service=nfs***  
***sudo firewall-cmd \--reload***
![image alt](https://github.com/SACHIN-ST3/LINUX_NFS_PROJECT/blob/56db528592ac52d726ddc9f935cdc27d35ae3750/NFS_PROJECT/Screenshot%202025-11-06%20220228.png)

# 

# **💻 STEP 5: NFS Client Configuration (on Client Machine)**

* Install NFS utilities:

  ***sudo dnf install nfs-utils \-y***
  
![image alt](https://github.com/SACHIN-ST3/LINUX_NFS_PROJECT/blob/56db528592ac52d726ddc9f935cdc27d35ae3750/NFS_PROJECT/Screenshot%202025-11-06%20220328.png)

→ Create a mount point and mount:

***sudo mkdir \-p /mnt/nfs\_client***  
***sudo mount \-t nfs 192.168.161.128:/mnt/nfs\_share   /mnt/nfs\_client***
![image alt](https://github.com/SACHIN-ST3/LINUX_NFS_PROJECT/blob/56db528592ac52d726ddc9f935cdc27d35ae3750/NFS_PROJECT/Screenshot%202025-11-06%20220358.png)

# **📌 STEP 6:  *Test Access   //*  Verify Mount**

 ***cd /mnt/nfs\_client*** 

***ls  \-l***

***This is the same directory that we have created on the server pc, and now this is on the client pc***
![image alt](https://github.com/SACHIN-ST3/LINUX_NFS_PROJECT/blob/56db528592ac52d726ddc9f935cdc27d35ae3750/NFS_PROJECT/Screenshot%202025-11-06%20220427.png)


***THIS IS A COMPLETED PROJECT***
