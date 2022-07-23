<h1>Implement network attacks</h1>

<h2>Description</h2>
The project consists applying the knowledge gained during university, in a real world scenario. The task was to create a network topology, run and observe the normal traffic within the topology, and then launch network attacks and observe the impact on the network performance. In this scenario, DOS, TCP SYN and IP spoofing attacks have been implemented. In the final stage, network defense mechanisms to protect the network and observe the effectiveness have been implemented.
<br />

<h2>Environments Used </h2>

- <b>Mininet</b>
- <b>VMware</b>
- <b>Wireshark</b>

<h2>Program walk-through:</h2>

<p align="center">
Build a network and test its connectivity: <br/>

- <b>Created a tree topology with two levels and two hosts attached to each switch that have been situated on the second level. </b> <br />
- <b>Each host has its own IP address as shown in the image</b> <br />
- <b>The diagram has been developed with the help of the Mininet Topology Visualiser provided on the Spear website</b> <br />

<p align="center">
<img src="https://i.imgur.com/37BVTOo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The model of the switches s1, s2, s3, s4 are of the type OVSSwitches</b> <br />
- <b>The model includes two controllers: c0 and c1</b> <br />
- <b>c0 is an OVSController</b> <br />
- <b>c1 is a RemoteController</b> <br />

<p align="center">
<img src="https://i.imgur.com/xDndcAP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Those are the links created within the servers, between server and hosts</b> <br />

<p align="center">
<img src="https://i.imgur.com/Msfjn7K.png" height="40%" width="60%" alt="Disk Sanitization Steps"/>
<br />
<br />
Test the connectivity of the hosts:  <br/>

- <b>This is an overall ping, displaying the connectivity of all the hosts within the network topology, as well as informing us regarding which host is connected to what host</b>

<p align="center">
<img src="https://i.imgur.com/UTpH1ta.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />

- <b>A few separate pings of the host 1 to other hosts have been performed, transmitting 1 package only</b>
- <b>h1 sends its ping towards the other hosts by using the ICMP Echo Request, as it knows the MAC address of the other hosts</b>
- <b>The images represents the requests of h1, and thre replies offered by the other hosts that have been captured by the controller which sends a flow entry</b>

<p align="center">
<img src="https://i.imgur.com/BkbM4gy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/mBINnMS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Generate and analyse traffic on the network: (TCP traffic) <br/>

- <b>The iperf creates a basic TCP and UDP data transmission while measuring the throughput of the network</b>
- <b>Here we started the TCP server (-s) before the client, at host 2, where the result setting is using TCP at the port 81 (-p), displayed after each second (-i)</b>

<p align="center">
<img src="https://i.imgur.com/TIKJWtZ.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />

- <b>The connections started at TCP client (-c) at host1 towards h2 (10.0.1.2) at port 81 (-p) for a transmission duration of 10 seconds (-t)</b>

<p align="center">
<img src="https://i.imgur.com/5qllX4J.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />

- <b>Same principle has been applied for the other switches (s3 and s4)</b>
- <b>For s3, the TCP server started at host 4 and the TCP client at host 3</b>

<p align="center">
<img src="https://i.imgur.com/97yYguG.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/hRCVF9W.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />

- <b>For s4, the TCP server started at host 6 and the TCP client at host 5</b>

<p align="center">
<img src="https://i.imgur.com/j3ifMju.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/oT1Itua.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
<br />
Generate and analyse traffic on the network: (UDP traffic):  <br/>

- <b>In s2 we started UDP (-u) server (-s) at host 2 with the result setting at port (-p) 81, every second (-i)</b>
- <b>The UDP (-u) client (-c) starts at host 1 towards host 2 (10.0.1.2) on port (-p) 81, with sending rate (-b) of 10M during the interval (-t) of 10 seconds</b>

<p align="center">
<img src="https://i.imgur.com/oXS1mL7.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/atRGesD.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />

- <b>The same principle has been applied for s3 and s4</b>
- <b>In s3, the UDP server starts at host 4 and the client at host 3</b>

<p align="center">
<img src="https://i.imgur.com/ePtpvL9.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/dcpxCI8.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />

- <b>In s4, the UDP server starts at host 6 and the client at host 5</b>

<p align="center">
<img src="https://i.imgur.com/Q5mWT9j.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/35UVTC6.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
<br />
Traffic analysis:  <br/>

- <b>ARP request analyses the captured traffic in Wireshark</b>
- <b>The image bellow represents all the requests made by the hosts to search for the MAC addresses of the targeted host</b>
- <b>Host 3 (10.0.2.3) searches for the host 2 (10.0.1.2) as it already knows its IP address</b>

<p align="center">
<img src="https://i.imgur.com/BR1D8a9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The packets contain the source IP address but no destination IP address as it doesn't have a destination set</b>
- <b>The sender MAC and IP addresses, also the target IP address are known, but the target MAC is unavailable at the request packet stage</b>
- <b>Host 5 (10.0.3.5) is trying to learn the host 2 (10.0.1.2) MAC address</b>

<p align="center">
<img src="https://i.imgur.com/3qWjx3J.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>In the response packet it can be observed the change in source MAC, where specific source MAC is assigned to each host IP</b>
- <b>Everything else stays the same althoguh now the sender and target places have switched and the previous target MAC address, which was all 0's before, now is the reqested host's MAC</b>

<p align="center">
<img src="https://i.imgur.com/1FNiES0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>ICMP echo-request will verify if the data arrives after we ping (www.google.com)</b>
- <b>In the source we notice the requester IP address and in the destination, the www.google.com IP address</b>
- <b>When analysing the details, we can check the checksum, identifier number and sequence number</b>

<p align="center">
<img src="https://i.imgur.com/nbKJSIt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>In the response packet, the source and destination IP's addresses switched, and the details mentioned in the request remain the same in the response</b>

<p align="center">
<img src="https://i.imgur.com/uEak1ok.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/spCnbEu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/FBaslwK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Network performance analysis:  <br/>

- <b>UDP traffic is captured on all the server hosts, with packets that went towards port 81</b>
- <b>The communication is one way, from the client host (10.0.1.1) towards the server host (10.0.1.2)</b>
- <b>The protocol type can be noticed, time to live and total length of each packet</b>

<p align="center">
<img src="https://i.imgur.com/usj1FNo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/MjbnEPr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Server h4 (10.0.2.4) and client h3 (10.0.2.3)</b>

<p align="center">
<img src="https://i.imgur.com/riTRRSv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/K31HrZ4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Server h6 (10.0.3.6) and client h5 (10.0.3.5)</b>

<p align="center">
<img src="https://i.imgur.com/bijDjvY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/KHa8uh9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Analyse TCP network traffic:  <br/>

- <b>Here we analysed the TCP network traffic on the www.google.com on port 81 to capture wireshark traffic</b>
- <b>Because we haven't been provided with internet connection (due to isolation practice only), it didn't succeed</b>

<p align="center">
<img src="https://i.imgur.com/z9ncVwq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/uHFEFUW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/leDMJEo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/ikGRcOo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/LUZuwi6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Network attacks: (TCP SYN attack)  <br/>

- <b>TCP SYN attack happens when the attacker h1 (10.0.1.1) spams the target h5 (10.0.3.5) with a high amount of SYN packets</b>

<p align="center">
<img src="https://i.imgur.com/N3No6tm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/CWuP5na.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/hVFUSgD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/uOmpmvy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/ZBzNBK5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/FnRuT4t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/CL5H4o4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/f1PtTES.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/8kRkuY3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/ZRzvXCl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Network attacks: (IP Spoofing)  <br/>

- <b>The command bellow prints the current flow-rules within the switch 3</b>

<p align="center">
<img src="https://i.imgur.com/1D6fR3n.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The results after the attack are presented bellow</b>
- <b>After implementing the DoS attack, it will be noticeble that the recovery was faster in the IP spoofing attack rather than DoS attack </b>

<p align="center">
<img src="https://i.imgur.com/HCkTUEe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>This is the current flow-rules within switch 4 </b>

<p align="center">
<img src="https://i.imgur.com/W3nJ6Hb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>This is the current flow-rules within switch 4 during the attack</b>

<p align="center">
<img src="https://i.imgur.com/2vZz782.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The implementation of the attack</b>

<p align="center">
<img src="https://i.imgur.com/JVa2oKN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Host 3 (10.0.2.3) is trying to communicate with host 6 (10.0.3.6) although it cannot reach it even though host 6 is reaching out to host 3</b>

<p align="center">
<img src="https://i.imgur.com/5Vzuj6t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/DdaZKMZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/iwjSYfH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Is constantly trying to reach host 6 (10.0.3.6) back although failing to do so</b>

<p align="center">
<img src="https://i.imgur.com/WlWyQPS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Network attacks: (DoS attack)  <br/>

- <b>Prints the current flow-rules within the switch 3</b>

<p align="center">
<img src="https://i.imgur.com/z8vtPO7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The following command floods (--flood) 10000 packets (-c) towards host 3 (10.0.2.3) using hping3</b>
- <b>Sends SYN packets (-S) towards the port (-p) 22 (allows SSH connection) with random IP addresses (--rand-source -V)</b>
- <b>Can be noticed that all the packets have been transmitted, creating a 100% packet loss</b>

<p align="center">
<img src="https://i.imgur.com/9DfLgEx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The entire switch is affected, even when only 1 host is attacked within the same server</b>
- <b>The source IP address is noticed, and the destination is broadcast (asks for the MAC address from different sources), which will eventually flood the victim (10.0.2.3) with replies of the MAC addresses</b>

<p align="center">
<img src="https://i.imgur.com/BTwtOVz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/ZltWPTR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The main switch (s1) is affected by the attack undergoing is its sub-switch (s3), being populated by different source IP addresses, all targetting host 3 (10.0.2.3) by sending SYN packages</b>
- <b>Same goes for switch 4, witnessing the flooding attack going in the switch 3</b>

<p align="center">
<img src="https://i.imgur.com/V3dQlzd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/XMhyotS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The flow-entries in switch 3 during and right after the attack</b>

<p align="center">
<img src="https://i.imgur.com/nMpD4j9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>If we try to get to a host within the same switch to check for connectivity, we will not be able to reach the host 3</b>

<p align="center">
<img src="https://i.imgur.com/Hcd7NnE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>Same goes for a host within the switch that carried the attack</b>

<p align="center">
<img src="https://i.imgur.com/tYgrknX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>This shows that the entire network is unreachable after and during the attack</b>
- <b>However, the hosts within the switch that didn't participate to the attack are still able to communicate with eachother (h5 to h6 and viceversa), however the communication might be delayed at the beginning, taking longer to establish the connection</b>

<p align="center">
<img src="https://i.imgur.com/AAq70VM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/L7ooI06.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The reason why new connectivitys were impossible during and right after the attack is because when the flow table of the switches is full, and we try to implement new flow-rules by pinging the hosts within the affected switch, it will be failing because there is no space left in the flow table and is constantly being already populated</b>
- <b>It results in dropping the packets since it cannot receive additional information on how to install the flow-entry</b>
- <b>This image represents the flow entries in switch 3 few minutes after the attack</b>
- <b>It can be noticed that the availability for new connections is slowly getting back to normal</b>

<p align="center">
<img src="https://i.imgur.com/EJQoqoS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

- <b>The bellow image displays the results after at least 5 minutes since the attack </b>
- <b>Now we are finally able to establish new connections </b>

<p align="center">
<img src="https://i.imgur.com/wGSV8js.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Network defence: (Firewall)  <br/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
