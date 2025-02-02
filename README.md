# Network-Traffic-Analysis-with-Wireshark
<p>Network traffic analysis is a crucial part of cybersecurity. Wireshark is a popular network protocol analyzer used to capture and analyze network traffic, which I will do in this project. I will play around with and configure display/capture filters.  </p>
<h2>Utilities Used</h2>
</p>- Ubuntu </p>
</p>- UTM VM setup </p>
</p>- Wireshark </p>
<h2>Step-by-Step Walkthrough</h2>
</p> I open Wireshark and view the available network interfaces. For this example, I will be capturing trafiic on enp0s1.</p>
<img width="915" alt="Screenshot 2024-07-09 at 8 34 15 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/f7a6cbbf-23b5-4557-a44e-3dbe5cca7148">
</p> After clicking on enp0s1, I observe packets being listed in real time. </p>
<img width="962" alt="Screenshot 2024-07-15 at 2 50 50 PM" src="https://github.com/user-attachments/assets/873a3a86-310c-4ac9-b75b-8e57e6fdaed3">
</p> In order to generate some traffic, I open Firefox within my Ubuntu server and navigate to LinkedIn.com </p>
<img width="922" alt="Screenshot 2024-07-09 at 8 45 09 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/cc6141ab-96cd-4372-907a-0f52089a45cf">
</p> In Wireshark, I stop packet capturing and use the dislay filter to show  details of the LinkedIn packet capture. The filter will display all HTTP traffic where the host header contains "linkedin.com". HTTP traffic includes web browsing and can show details of interactions with LinkedIn's servers. </p> To see the entire conversation, I right-click the packet and select "follow" --> "HTTP Stream" </p>
<img width="1042" alt="Screenshot 2024-07-15 at 2 55 48 PM" src="https://github.com/user-attachments/assets/2e16ad3d-4ddd-48af-88ae-f6eca5197591">
</p> I can now expand the packet details to inspect the headers and payload of each layer
<img width="634" alt="Screenshot 2024-07-15 at 2 56 53 PM" src="https://github.com/user-attachments/assets/679a1db5-e5d6-46b0-abe0-ba9289ba481a">
</p> To save the packet capture for later analysis, I navigate to file -> save as, and then save it as a pcap extension </p>
<img width="957" alt="Screenshot 2024-07-09 at 9 05 21 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/15aae68c-8c72-4765-baf5-43bfc8a14886">
</p> Wireshark includes built-in tools for analysis, which we can observe in the Statistics menu. These tools include: protocol hierarchy (to view a breakdown of protocols used in the capture, conversations (to see communication pairs and their traffic statistics), and endpoints (to view traffic statistics for individual endpoints (IP addresses)
<img width="1081" alt="Screenshot 2024-07-09 at 9 09 03 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/8dc0d296-aa27-4092-ab07-fa6b4bddc44b">
</p> I can use the display filter to output source/destination ip addresses and specific protocols using logical operators. First, I ping google's public ip address (8.8.8.8) and then search for it in Wireshark using the following terminology: </p>
<img width="1212" alt="Screenshot 2024-07-15 at 3 11 01 PM" src="https://github.com/user-attachments/assets/d2105755-c23f-4099-81ba-97dcbaba181e">
</p> Another important piece of information that you would typically look for within a local network is DHCP data. I can do this by performing an op scan or network discovery scan using nmap or netdiscover (utility that allows you to discover other ip addresses or hosts on a local network by sending ARP requests and determining whether device is online/offline or on the network/off). From there, I can see the actual arp packet details which include the type of request, hardware type, etc.
<img width="877" alt="Screenshot 2024-07-15 at 3 54 25 PM" src="https://github.com/user-attachments/assets/a0ec6dfe-d547-4179-a303-44f01ff71af4">
<img width="1251" alt="Screenshot 2024-07-15 at 4 02 15 PM" src="https://github.com/user-attachments/assets/ab1c35e3-5de8-44a3-8f54-274dde8a12b3">
</p> I can also use the display filter to specify specific ip ranges and destination port numbers. </p> 
<img width="1217" alt="Screenshot 2024-07-15 at 4 17 27 PM" src="https://github.com/user-attachments/assets/9370b66a-5804-40b9-9caa-57798e4e235a">
</p> As an example, if I want to analyze what happened on a network and identify injections via malicious documents that came through a particular website/attachment, I can use the following display filter: </p>
<img width="1213" alt="Screenshot 2024-07-15 at 4 26 49 PM" src="https://github.com/user-attachments/assets/d6700453-5fca-4e66-8c9b-034a2d6d9ea0">
</p> You can also filter based on mac address using the following:</p>
<img width="1282" alt="Screenshot 2024-07-15 at 4 32 15 PM" src="https://github.com/user-attachments/assets/35bc863e-21ad-4a4b-b6ef-34f3f76dc6aa">
</p> Filtering based on specific protocols is also possible. I have a vulnerable linux server running ftp within the same subnet. I run ftp along with the target ip address and port number (21). I connect and purposely enter the incorrect credentials.
<img width="737" alt="Screenshot 2024-07-16 at 2 34 41 PM" src="https://github.com/user-attachments/assets/ba8a7da2-6d09-4de4-a273-31fa6eb129ce">
</p> If I head back into Wireshark, I can filter to show FTP packets. Because FTP is not encrypted, the passwords can be identified in the details. This method is important because we can identify BRUTE FORCE attacks whereby an attacker is trying to gain access.
<img width="1239" alt="Screenshot 2024-07-16 at 2 39 48 PM" src="https://github.com/user-attachments/assets/7b986756-c628-4744-a785-bbac8740fc21">
</p> <img width="1255" alt="Screenshot 2024-07-16 at 3 32 30 PM" src="https://github.com/user-attachments/assets/c8ba401c-e3c7-45e4-a171-23b2863c8c25">
</p> I can also explore SSH traffic between my two machines with the following: </p>
<img width="734" alt="Screenshot 2024-07-16 at 3 31 05 PM" src="https://github.com/user-attachments/assets/143510dc-9c91-4af5-bcc0-33a273a084e6">
</p> The encrypted packets can now be viewed in Wireshark. Unlike, ftp, unless we have the SSH key pair, we cannot decrypt these packets. 
</p> I can also configure capture filters, using logical operators to combine multiple filters together. For the below example, I am configuring the filter where the source ip address is set to my ubuntu ip, and the type of packet is icmp </p> 
<img width="1202" alt="Screenshot 2024-07-14 at 7 32 14 PM" src="https://github.com/user-attachments/assets/bbcbd72d-053b-4253-8956-f3d228bbbd32">
</p> To test that the packets are being captured, I perform a ping (ping uses icmp protocol) from my terminal on google.com. The packets are now visible in Wireshark. </p>
<img width="1003" alt="Screenshot 2024-07-14 at 7 56 28 PM" src="https://github.com/user-attachments/assets/54d9a9b0-3a56-477f-a78c-264e017fb85d">




