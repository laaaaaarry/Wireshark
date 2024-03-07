# Wireshark Network Analysis

## Objective

The Wireshark Network Analysis project aimed to Utilize Wireshark to analyze network traffic & detect SYN flood attack

## Skills Learned

- Open & Analyze PCAP files in wireshark.
- Creating useful filters for threat & attack detection.
- Visualise attacks coming from different locations in Map format for better understanding.
- Gained understanding of TCP & IP protocols & how to detect suspicious traffic.

## Tools Used

- Wireshark for Network Analysis.
- PCAP file for simulating SYN flood attack

## Steps

* **As soon as we open the PCAP in Wireshark we can see that a lot of traffic coming from wide range of IP addresses on port 80. All this packets are SYN packets coming in very short time frame, also the source port is in similar range for all requests indicating of an attack.**

![1](https://github.com/laaaaaarry/Wireshark/assets/125237930/c08b73ac-1f52-4c87-8bfe-b07363822d4a)


* **In statistics pane, we can see in IPv4 column in endpoints that most of this requests are single SYN requests.**

![2](https://github.com/laaaaaarry/Wireshark/assets/125237930/88aa0485-cba5-46b6-8745-18eaac382ca6)


* **By creating a specific rule & colour rule for the suspicious attack countries we can see that a lot of traffic is coming from there : Rule - ==ip.geoip_src_country_iso in {GB IN US} (suspicious countries)==.**

![Screenshot 2024-03-06 004446](https://github.com/laaaaaarry/Wireshark/assets/125237930/29e001e4-8768-46c0-b9cd-95d9e3345f0b)



* **As we further analyse we find that all the SYN conversations have very low sequence number usually its in billions & also all have similar range of sequence numbers**

![3](https://github.com/laaaaaarry/Wireshark/assets/125237930/18a4a3f0-b37a-4dbf-83e3-a4ff8249a8e2)
![4](https://github.com/laaaaaarry/Wireshark/assets/125237930/9df2a903-320f-473c-bb5d-008a4b0af8fc)




* **The SYN's coming in do not have options which are generally present for a genuine communications instead they only have bare minimum for valid SYN request that too from so many communications & locations which is a indicator of an attack.**

![5](https://github.com/laaaaaarry/Wireshark/assets/125237930/42fdfd43-5f4b-43b9-9060-d5fa62abd01d)
![6](https://github.com/laaaaaarry/Wireshark/assets/125237930/04e4c855-1b5b-45e7-9726-1a8462db3d8a)


* **Because no options are selected the Header size of these SYN's are too small which is very suspicious.**

![7](https://github.com/laaaaaarry/Wireshark/assets/125237930/317269f1-4ad5-4be7-9b27-6d74ca296eee)
![8](https://github.com/laaaaaarry/Wireshark/assets/125237930/f2bf7ca1-53dd-4564-a367-c0c5cdf8a9c3)



* **All these SYN packets have very small & same Window size which is very suspicious, usually they are high & different from each other for every conversation.**


![9](https://github.com/laaaaaarry/Wireshark/assets/125237930/52e27367-6596-4591-8220-3d19a1d1f325)


* **Now if we see TTL's, we can notice that all the conversations have same starting TTL value i.e. 128 which indicates that all these conversations are from same type of OS or Device & is highly unlikely for genuine traffic as normally TTL's start from 64, 128 & 255 for different OS's.**

![10](https://github.com/laaaaaarry/Wireshark/assets/125237930/4eb1c43d-f382-4cf5-af12-c6073b39cfb1)



* **Also we see that all these TTL's are varying in counts which is a indicator of a botnet attack instead of spoofed attack, because spoofed attack generally has same TTL values for all the conversations**

![10](https://github.com/laaaaaarry/Wireshark/assets/125237930/ad3c36c1-21e8-412a-abeb-d04fd145cf30)


## Documentation 

* **Most requests coming to port 80 with SYN flag in very short time period.**
* **All this requests are from different IP addresses but all have similar source port range.**
* **All this different IP's have sent only SYN requests.**
* **Lot of traffic is coming from unusual countries.**
* **Sequence numbers offered in the conversations are very low & are in similar range instead of being in billions which is normal.**
* **Genuine SYN conversations normally have options which are required for the conversation but in this PCAP none of SYN's have those options.**
* **Header sizes of these SYN's are too small to be genuine due to absence of options.**
* **All conversations have same & very low Window sizes.**
* **All TTL's from PCAP are starting from 128 which is a indicator that all are from same type of OS or Device.**
* **TTL's are varying in count which is a indicator of Botnet attack instead of being a spoofed attack.**
