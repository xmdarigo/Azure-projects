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

Observe SSH traffic  
In Wireshark, filter traffic to view only SSH packets.  
From the windows VM, enter into the linux VM using the SSH command.  
Requires username, ip address, and password.  
Once inside, the command 'uname' will confirm access.  
Wireshark will also show the flow of packets using SSH as we interact with the command line of the Linux VM.  

Observe DHCP traffic
In Wireshark, filter traffic to view only DHCP packets.  
Open Notepad and create the file dhcp.bat containing two commands:  
`PS > ipconfig /release`  
`PS > ipconfig /renew`

This will release the IP address given, and renew it instantly.  
This has to be done through a .bat file because connection to the VM will be lost during the release phase.  
Once renewed, which happens very quickly, we can reconnect through RDP.  
Enter the command to run:  
`PS > .\dhcp.bat`

After logging back in, Wireshark will show the process the VM takes with the DHCP server to reobtain its IP addresses.  

Observe DNS traffic  
Enter `DNS` in the search bar of Wireshark to view only DNS packets.  
In PowerShell, enter the command `nslookup`  
Pick a website of your choice.  
See PS display the IP address.  
See Wireshark capture the packets being sent to the DNS server, and the return packets.  

Observe RDP traffic  
Enter `RDP` in the search bar of Wireshark.  
It will show the initial connection being made.  
Does not show the flow of traffic between your device and the VM however.  
To view that, enter `tcp.port==3389` in the search bar.  
RDP uses TCP over port 3389 which is why this is necessary.  
This shows the constant flow of packets between the two connected computers.  
