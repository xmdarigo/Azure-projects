# Azure-projects

Created a subscription in Azure.  
Created a resource group within the subscription.  
Created a storage account within the resource group.  
Uploaded a file to the storage account.  
Deleted the resource group which deletes everything within it and starts fresh.  

Network Testing  
Created a new resource group.  
Created one windows VM and one linux VM.  
Created a virtual cloud network and subnets as a result.  
Logged into the windows VM using RDP.  
Logged into the linux VM using SSH.  
Downloaded Wireshark to capture network packet information.  
From the windows VM, sent ping requests to the private IP of the linux VM and viewed packets being sent in Wireshark.  

Firewall testing  
In Powershell, set a continuous ping to the linux VM.  
Returned to the Azure portal and navigated to Network Security Groups.  
Entered into the group for the linux VM and navigated to Incoming Rules.  
Added a rule to block all ICMP connections from all sources to any destination.  
Returned to the windows VM and waited for the ping connections to begin dropping.  
Success.  
Returned to the Azure portal and removed the rule blocking ICMP connections.  
After some time, the packets being sent between the two VMs continued.  
