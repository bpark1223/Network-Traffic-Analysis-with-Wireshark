# Network-Traffic-Analysis-with-Wireshark
<p>Network traffic analysis is a crucial part of cybersecurity. Wireshark is a popular network protocol analyzer used to capture and analyze network traffic, which I will do in this project. I will also configure display and capture filters </p>
<h2>Utilities Used</h2>
</p>- Ubuntu </p>
</p>- UTM VM setup </p>
</p>- Wireshark </p>
<h2>Step-by-Step Walkthrough</h2>
</p> I open Wireshark and view the available network interfaces. For this example, I will be capturing trafiic on enp0s1.</p>
<img width="915" alt="Screenshot 2024-07-09 at 8 34 15 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/f7a6cbbf-23b5-4557-a44e-3dbe5cca7148">
</p> After clicking on enp0s1, I observe packets being listed in real time. </p>
<img width="985" alt="Screenshot 2024-07-09 at 8 41 48 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/a003fb4e-2f54-45cc-b312-9bf4bb3db57b">
</p> In order to generate some traffic, I open Firefox within my Ubuntu server and navigate to LinkedIn.com </p>
<img width="922" alt="Screenshot 2024-07-09 at 8 45 09 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/cc6141ab-96cd-4372-907a-0f52089a45cf">
</p> In Wireshark, I stop packet capturing and use the dislay filter to show  details of the LinkedIn packet capture. The filter will display all HTTP traffic where the host header contains "linkedin.com". HTTP traffic includes web browsing and can show details of interactions with LinkedIn's servers.</p>
<img width="1440" alt="Screenshot 2024-07-09 at 8 50 04 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/1dde196d-2017-4f9c-be30-cb1a51c837a6">
</p> To see the entire conversation, I right-click the packet and select "follow" --> "HTTP Stream"
<img width="1049" alt="Screenshot 2024-07-09 at 8 52 40 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/004983af-46f6-4c30-b0a4-893f60256264">
</p> I can now expand the packet details to inspect the headers and payload of each layer
<img width="1084" alt="Screenshot 2024-07-09 at 9 01 49 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/a17702e1-5c32-47b9-b7f0-8d1d6bacb3ec">
</p> To save the packet capture for later analysis, I navigate to file -> save as, and then save it as a pcap extension </p>
<img width="957" alt="Screenshot 2024-07-09 at 9 05 21 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/15aae68c-8c72-4765-baf5-43bfc8a14886">
</p> Wireshark includes built-in tools for analysis, which we can observe in the Statistics menu. These tools include: protocol hierarchy (to view a breakdown of protocols used in the capture, conversations (to see communication pairs and their traffic statistics), and endpoints (to view traffic statistics for individual endpoints (IP addresses)
<img width="1081" alt="Screenshot 2024-07-09 at 9 09 03 PM" src="https://github.com/bpark1223/Network-Traffic-Analysis-with-Wireshark/assets/77799235/8dc0d296-aa27-4092-ab07-fa6b4bddc44b">
</p> I can also configure capture filters, using logical operators to combine multiple filters together. For the below example, I am configuring the filter where the source ip address is set to my ubuntu ip, and the type of packet is icmp </p> 
<img width="1202" alt="Screenshot 2024-07-14 at 7 32 14 PM" src="https://github.com/user-attachments/assets/bbcbd72d-053b-4253-8956-f3d228bbbd32">
</p> To test that the packets are being captured, I perform a ping (ping uses icmp protocol) from my terminal on google.com. The packets are now visible in Wireshark. </p>
<img width="1003" alt="Screenshot 2024-07-14 at 7 56 28 PM" src="https://github.com/user-attachments/assets/54d9a9b0-3a56-477f-a78c-264e017fb85d">




