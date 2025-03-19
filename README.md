# azure-network-protocols
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
- Ubuntu Server 20.04

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
