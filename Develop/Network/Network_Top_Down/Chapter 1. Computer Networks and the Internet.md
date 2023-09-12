#Network 

- [[#1.1 What Is the Internet?|1.1 What Is the Internet?]]
	- [[#1.1 What Is the Internet?#1.1.1 A Nuts-and-Bolts Description|1.1.1 A Nuts-and-Bolts Description]]
	- [[#1.1 What Is the Internet?#1.1.2 A Services Description|1.1.2 A Services Description]]
	- [[#1.1 What Is the Internet?#1.1.3 What Is a Protocol?|1.1.3 What Is a Protocol?]]
- [[#1.2 The Network Edge|1.2 The Network Edge]]
	- [[#1.2 The Network Edge#1.2.1 Access Networks|1.2.1 Access Networks]]
	- [[#1.2 The Network Edge#1.2.2 Physical Media|1.2.2 Physical Media]]
- [[#1.3 The Network Core|1.3 The Network Core]]
	- [[#1.3 The Network Core#1.3.1 Packet Switching|1.3.1 Packet Switching]]
	- [[#1.3 The Network Core#1.3.2 Circuit Switching|1.3.2 Circuit Switching]]
	- [[#1.3 The Network Core#1.3.3 A Network of Networks|1.3.3 A Network of Networks]]
- [[#1.4 Delay, Loss, and Throughput in Packet-Switched Networks|1.4 Delay, Loss, and Throughput in Packet-Switched Networks]]
	- [[#1.4 Delay, Loss, and Throughput in Packet-Switched Networks#1.4.1 Overview of Delay in Packet-Switched Networks|1.4.1 Overview of Delay in Packet-Switched Networks]]
	- [[#1.4 Delay, Loss, and Throughput in Packet-Switched Networks#1.4.2 Queuing Delay and Packet Loss|1.4.2 Queuing Delay and Packet Loss]]
	- [[#1.4 Delay, Loss, and Throughput in Packet-Switched Networks#1.4.3 End-to-End Delay|1.4.3 End-to-End Delay]]
	- [[#1.4 Delay, Loss, and Throughput in Packet-Switched Networks#1.4.4 Throughput in Computer Networks|1.4.4 Throughput in Computer Networks]]
- [[#1.5 Protocol Layers and Their Service Models|1.5 Protocol Layers and Their Service Models]]
	- [[#1.5 Protocol Layers and Their Service Models#1.5.1 Layered Architecture|1.5.1 Layered Architecture]]
	- [[#1.5 Protocol Layers and Their Service Models#1.5.2 Encapsulation|1.5.2 Encapsulation]]
- [[#1.6 Networks Under Attack|1.6 Networks Under Attack]]
- [[#1.7 History of Computer Networking and the Internet|1.7 History of Computer Networking and the Internet]]
	- [[#1.7 History of Computer Networking and the Internet#1.7.1 The Development of Packet Switching: 1961–1972|1.7.1 The Development of Packet Switching: 1961–1972]]
	- [[#1.7 History of Computer Networking and the Internet#1.7.2 Proprietary Networks and Internetworking: 1972–1980|1.7.2 Proprietary Networks and Internetworking: 1972–1980]]
	- [[#1.7 History of Computer Networking and the Internet#1.7.3 A Proliferation of Networks: 1980–1990|1.7.3 A Proliferation of Networks: 1980–1990]]
	- [[#1.7 History of Computer Networking and the Internet#1.7.4 The Internet Explosion: The 1990s|1.7.4 The Internet Explosion: The 1990s]]
	- [[#1.7 History of Computer Networking and the Internet#1.7.5 The New Millennium|1.7.5 The New Millennium]]
- [[#1.8 Summary|1.8 Summary]]
- [[#Homework Problems and Questions|Homework Problems and Questions]]
	- [[#Homework Problems and Questions#Chapter 1 Review Questions|Chapter 1 Review Questions]]
	- [[#Homework Problems and Questions#Problems|Problems]]

## 1.1 What Is the Internet?
### 1.1.1 A Nuts-and-Bolts Description

### 1.1.2 A Services Description

### 1.1.3 What Is a Protocol?

## 1.2 The Network Edge

### 1.2.1 Access Networks

### 1.2.2 Physical Media

## 1.3 The Network Core

### 1.3.1 Packet Switching

### 1.3.2 Circuit Switching

### 1.3.3 A Network of Networks

## 1.4 Delay, Loss, and Throughput in Packet-Switched Networks

### 1.4.1 Overview of Delay in Packet-Switched Networks

### 1.4.2 Queuing Delay and Packet Loss

### 1.4.3 End-to-End Delay

### 1.4.4 Throughput in Computer Networks

## 1.5 Protocol Layers and Their Service Models

### 1.5.1 Layered Architecture

### 1.5.2 Encapsulation

## 1.6 Networks Under Attack

## 1.7 History of Computer Networking and the Internet

### 1.7.1 The Development of Packet Switching: 1961–1972

### 1.7.2 Proprietary Networks and Internetworking: 1972–1980

### 1.7.3 A Proliferation of Networks: 1980–1990

### 1.7.4 The Internet Explosion: The 1990s

### 1.7.5 The New Millennium

## 1.8 Summary

## Homework Problems and Questions

### Chapter 1 Review Questions

### Problems

SECTION 1.1

1. R1.  What is the difference between a host and an end system? List several differ- ent types of end systems. Is a Web server an end system?
    
2. R2.  Describe the protocol that might be used by two people having a telephonic conversation to initiate and end the conversation, i.e., the way that they talk.
    
3. R3.  Why are standards important for protocols?
    

SECTION 1.2

4. R4.  List four access technologies. Classify each one as home access, enterprise access, or wide-area wireless access.
    
5. R5.  Is HFC transmission rate dedicated or shared among users? Are collisions possible in a downstream HFC channel? Why or why not?
    
6. R6.  What access network technologies would be most suitable for providing internet access in rural areas?
    
7. R7.  Dial-up modems and DSL both use the telephone line (a twisted-pair copper cable) as their transmission medium. Why then is DSL much faster than dial- up access?
    
8. R8.  What are some of the physical media that Ethernet can run over?
    
9. R9.  HFC, DSL, and FTTH are all used for residential access. For each of these access technologies, provide a range of transmission rates and comment on whether the transmission rate is shared or dedicated.
    
10. R10.  Describe the different wireless technologies you use during the day and their characteristics. If you have a choice between multiple technologies, why do you prefer one over another?

SECTION 1.3

11. R11.  Suppose there is exactly one packet switch between a sending host and a receiving host. The transmission rates between the sending host and the switch and between the switch and the receiving host are R1 and R2, respectively. Assuming that the switch uses store-and-forward packet switching, what is the total end-to-end delay to send a packet of length L? (Ignore queu- ing, propagation delay, and processing delay.)
    
12. R12.  What advantage does a circuit-switched network have over a packet-switched net- work? What advantages does TDM have over FDM in a circuit-switched network?
    
13. R13.  Suppose users share a 2 Mbps link. Also suppose each user transmits contin- uously at 1 Mbps when transmitting, but each user transmits only 20 percent
    

of the time. (See the discussion of statistical multiplexing in Section 1.3.)

1. When circuit switching is used, how many users can be supported?
    
2. For the remainder of this problem, suppose packet switching is used. Why will there be essentially no queuing delay before the link if two or fewer users transmit at the same time? Why will there be a queuing delay if three users transmit at the same time?
    
3. Find the probability that a given user is transmitting.
    
4. Suppose now there are three users. Find the probability that at any given time, all three users are transmitting simultaneously. Find the fraction of time during which the queue grows.
    

14. R14.  Why will two ISPs at the same level of the hierarchy often peer with each other? How does an IXP earn money?
    
15. R15.  Why is a content provider considered a different Internet entity today? How does a content provider connect to other ISPs? Why?
    

SECTION 1.4

16. R16.  Consider sending a packet from a source host to a destination host over a fixed route. List the delay components in the end-to-end delay. Which of these delays are constant and which are variable?
    
17. R17.  Visit the Transmission Versus Propagation Delay interactive animation at  
    the Companion Website. Among the rates, propagation delay, and packet sizes available, find a combination for which the sender finishes transmitting before the first bit of the packet reaches the receiver. Find another combination for which the first bit of the packet reaches the receiver before the sender finishes transmitting.
    
18. R18.  A user can directly connect to a server through either long-range wireless or a twisted-pair cable for transmitting a 1500-bytes file. The transmission rates of the wireless and wired media are 2 and 100 Mbps, respectively. Assume that the propagation speed in air is 3 * 108 m/s, while the speed in the twistedpair is 2 * 108 m/s. If the user is located 1 km away from the server, what is the nodal delay when using each of the two technologies?

19. R19.  SupposeHostAwantstosendalargefiletoHostB.ThepathfromHostAtoHost Bhasthreelinks,ofratesR1 = 500kbps,R2 = 2Mbps,andR3 = 1Mbps.
    
    1. Assuming no other traffic in the network, what is the throughput for the file transfer?
        
    2. Suppose the file is 4 million bytes. Dividing the file size by the through- put, roughly how long will it take to transfer the file to Host B?
        
    3. Repeat (a) and (b), but now with R2 reduced to 100 kbps.
        
20. R20.  Suppose end system A wants to send a large file to end system B. At a very high level, describe how end system A creates packets from the file. When one of these packets arrives to a router, what information in the packet does the router use to determine the link onto which the packet is forwarded? Why is packet switching in the Internet analogous to driving from one city to another and asking directions along the way?
    
21. R21.  Visit the Queuing and Loss interactive animation at the Companion Website. What is the maximum emission rate and the minimum transmission rate? With those rates, what is the traffic intensity? Run the interactive animation with these rates and determine how long it takes for packet loss to occur. Then repeat the experiment a second time and determine again how long it takes for packet loss to occur. Are the values different? Why or why not?
    

SECTION 1.5

22. R22.  Iftwoend-systemsareconnectedthroughmultipleroutersandthedata-link level between them ensures reliable data delivery, is a transport protocol offering reliable data delivery between these two end-systems necessary? Why?
    
23. R23.  What are the five layers in the Internet protocol stack? What are the principal responsibilities of each of these layers?
    
24. R24.  What do encapsulation and de-encapsulation mean? Why are they needed in a layered protocol stack?
    
25. R25.  Which layers in the Internet protocol stack does a router process? Which lay- ers does a link-layer switch process? Which layers does a host process?
    

SECTION 1.6

26. R26.  What is self-replicating malware?
    
27. R27.  DescribehowabotnetcanbecreatedandhowitcanbeusedforaDDoSattack.
    
28. R28.  Suppose Alice and Bob are sending packets to each other over a computer network. Suppose Trudy positions herself in the network so that she can capture all the packets sent by Alice and send whatever she wants to Bob; she can also capture all the packets sent by Bob and send whatever she wants to Alice. List some of the malicious things Trudy can do from this position.