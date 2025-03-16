# azure-network-protocols
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>



<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>


- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>


- Step 1 - Have your Windows VM and Linux VM running on Microsoft Azure
- Step 2 - Remotely connect to your Windows VM, open up Edge, and search and download "Wireshark"
- Step 3 - Install packet capturing software "Wireshark"
- Step 4 - You are now ready to analyze some packets

<h2>Actions and Observations</h2>

<h3>Installating Wireshark</h3>


<p>
<img src="https://i.imgur.com/0245HNh.png" height="80%" width="80%"
</p>
<p>
Login to your Windows VM and open up "Microsoft Edge"
</p>
<br />

<p>
<img src="https://i.imgur.com/RMdFRJJ.png" height="60%" width="60%" 
</p>
<p>
From there, search up "Wireshark" Download this version of it.
</p>
<br />

<p>
<img src="https://i.imgur.com/5y0QMUZ.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/kGZiea6.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/Bx49QXR.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/yLVMgw9.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/If7a47q.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/pjFmuYx.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/RZzPgCh.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/zFS7pyY.png" height="20%" width="20%"
</p>
<p>
Open the file and go through the installer.
<p>
<img src="https://i.imgur.com/0245HNh.png" height="80%" width="80%"
</p>
<br />

<p>
<img src="https://i.imgur.com/V1m6cOS.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/YFxKLTy.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/8xU1XLZ.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/xGXfbSO.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/DR0ibkJ.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/YG7vYF0.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/V1m6cOS.png" height="20%" width="20%" <p>
</p>
<p>
Now, you'll be promtpted to install "Ncap". Go through the setup just like Wireshark.

</p>
<br />

<p>

<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
At this point, Wireshark should be installed. Go ahead and open it up using the search bar.
<img src="https://i.imgur.com/RMdFRJJ.png" height="60%" width="60%" 
</p>
<p>
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
In the Wireshark search bar, write down "ICMP" to filter for ICMP traffic only.
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
Open the file and go through the installer.
</p>
<br />

<p>
<img src="https://i.imgur.com/V1m6cOS.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/YFxKLTy.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/8xU1XLZ.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/xGXfbSO.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/DR0ibkJ.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/YG7vYF0.png" height="20%" width="20%" <p> <img src="https://i.imgur.com/V1m6cOS.png" height="20%" width="20%" <p>
</p>
<p>
Now, you'll be promtpted to install "Ncap". Go through the setup just like Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/snhWpOP.png" height="80%" width="80%" 
</p>
<p>

</p>
<br />

<p>
<img src="https://i.imgur.com/snhWpOP.png" height="60%" width="60%" 
</p>
<p>
Once you have the ip adress open up "Powershell" and "ping [private address]". You'll notice that while you're pinging the linux VM, Wireshark is also working in the background, capturing those packets. You should be able to see the packets in Wireshark.
</p>
<br />
