![image](https://github.com/user-attachments/assets/c0b3a74a-ba74-4ee4-8e95-ee5a732b4e2c)# azure-network-protocols
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>



<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark and experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>


- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
- Ubuntu Server 22.04

<h2>High-Level Steps</h2>


- Step 1 - Have your Windows VM and Linux VM running on Microsoft Azure
- Step 2 - Remotely connect to your Windows VM, open up Edge, and search and download "Wireshark"
- Step 3 - Install packet capturing software "Wireshark"
- Step 4 - Analyze some packets

<h2>Actions and Observations</h2>

<h3>Installating Wireshark</h3>


<p>
<img src="https://i.imgur.com/0245HNh.png" height="80%" width="80%"
</p>
<p>
Log in to your Windows VM and open up "Microsoft Edge"
</p>
<br />

<p>
<img src="https://i.imgur.com/RMdFRJJ.png" height="60%" width="60%" 
</p>
<p>
From there, search "Wireshark" Download this version of it.
</p>
<br />

<p>
<img src="https://i.imgur.com/5y0QMUZ.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/kGZiea6.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/Bx49QXR.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/yLVMgw9.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/If7a47q.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/pjFmuYx.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/RZzPgCh.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/zFS7pyY.png" height="20%" width="20%"
</p>
<p>
Open the file and go through the installer.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/V1m6cOS.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/YFxKLTy.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/8xU1XLZ.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/xGXfbSO.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/DR0ibkJ.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/YG7vYF0.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/V1m6cOS.png" height="20%" width="20%" <p>
</p>
<p>
Now, you'll be prompted to install "Ncap". Go through the setup just like Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%"
</p>
<p>
At this point, Wireshark should be installed. Go ahead and open it up using the search bar.
</p>
<br />

<p>
<img src="https://i.imgur.com/O1BFj3u.png" height="60%" width="60%"
</p>
<p>
When first opening up Wireshark, a screen like this one should appear. Select "Ethernet" and continue. Note the constant influx of packets being received and sent. We are now ready to filter some packets.
</p>
<br />


<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
In the Wireshark search bar, write down "ICMP" (Internet Control Message Protocol) to filter for ICMP traffic only. As you can see, there's nothing showing up, this is because there is no ICMP traffic at the moment. We will be creating some shortly.
</p>
<br />


<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
On Azure find the private address of the linux vm. To do, goto virtual machines → [your linux machine name] → Overview. There should be a networking tab. Grab the private ip adress.
<img src="https://i.imgur.com/5y0QMUZ.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/kGZiea6.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/Bx49QXR.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/yLVMgw9.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/If7a47q.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/pjFmuYx.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/RZzPgCh.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/zFS7pyY.png" height="20%" width="20%"
</p>
<p>
Once you have the ip adress open up "Powershell" and "ping [private address]". You'll notice that while you're pinging the linux VM, Wireshark is also working in the background, capturing those packets. You should be able to see the packets in Wireshark.
</p>
<br />


<p>
<img src="https://i.imgur.com/SgJZs3g.png" height="80%" width="80%" 
</p>
<p>
You can explore ICMP traffic further by pinging random sites. For example, let's try to ping "www.google.com". Just like the ping to the Linux Virtual machine, Wireshark is receiving the requests and replies of from the pings. Feel free to experiment with any other sites if you wish.
</p>
<br />

<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
When you're done filtering for ICMP, make sure to reset the capturing software. This should give you a cleared screen.
<p>
</p>
<br />

<p>
</p>
Next, let's try to filter for SSH (Secure Shell). Just like ICMP, enter "SSH" in the filter bar.
<p>
</p>
<p>
<img src="https://i.imgur.com/ZySst6H.png" height="60%" width="60%" 
</p>
Then, go back to powershell and connect to the linux VM from the windows VM by typing “ssh labuser@[private ip address of the linux]" and pressing "enter". So in my case it would look like this: ssh labuser@10.0.0.7. You'll then be prompted to enter your password. Note that you won't be able to see your password as you type it for security reasons but it is being typed so make sure that you type it correctly.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
As you can see, wireshark is already showing stuff as we try to connect to the Linux VM.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
You should eventually see a screen that looks like this. You'll know you're connected to the VM when you see "[your username]@Linux". The text should also be colored.
</p>
<br />

<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
From here, you can type in commands as you would on a Linux computer. As you type commands on PowerShell, you'll see them translated into Wireshark. Once you're done experimenting on Linux, you can switch back to Windows by typing "Exit"
</p>
<br />

<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
Next, we will be observing DHCP (Dynamic Host Configuration Protocol). Just like in SSH, restart the packet-capturing software. To observe DHCP traffic, we must set things up. First, on the bar, type "udp.port == 67 udp.port == 68"
</p>
<br />

<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
Open notepad, enter “ipconfig /release” and ipconfig /renew; name it "Dhcp.bat" and save it "as all files" for the file type. Save the file in <i>programdata</i>. In order to do so, you'll have to access throught the c:\ drive. It should look like this: ”c:\programdata”.
</p>
<br />


<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
You can use command “ls” to list the file contents of the folder; check to see if the bat file created earlier is present.
</p>
<br />


<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
Once you've located the file, you can run it by using “./Dhcp.bat”. You'll notice that the VM will restart; this is normal as it is releasing and rewewing the IP address. Once the VM has been restarted, go ahead and log back in; you'll see everything was left the same prior to the restart. Furthermore, you should now see that Wireshark actually displayed new entries.
</p>
<br />


<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
Next, we shall observing DNS traffic, which uses both TCP and DNS port 53. As always, please restart the capturing software. To filter for dns, type in "dns" in the filter bar.
</p>
<br />


<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
To see the DNS packets, simply switch over to powershell and use command "nslookup [Website]". With this, you'll be able to obtain the IP adress of any site you look up. For this example, we'll search for google's. You should be able to see stuff happening in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
Finally, let's explore RDP (Remote dekstop protocol). Just like usual, restart the packet capturing service and then enter “tcp.port== 3389” for traffic in the bar. You should be able to notice the constant spam due to data being transmitted from a VM. The RDP filter is essentially every action that we produce from the VM, from clicking on an icon to simply moving the mouse. This protocol is most-likely resposible for most of the spam that occurs when you first boot up Wireshark.
</p>
<br />


<p>
</p>
<p>
To conclude, we've learned how to install Wireshark. From there, we've explored the different types of packets including ICMP, SSH, DHCP, DNS AND RDP. Congratulations, you should now have a slightly better understanding of how different packets circulate from the source to it's destination!
</p>
<br />
