# Tryhackme - Introductory Networking
* Date - 27-11-25
* Topics covered - The OSI Model, TCP/IP Model, How these models look in practice, An introduction to basic networking tools

## The OSI Model: An Overview
The Open System Interconnection (OSI) Model is a standardised model which we use to demonstrate the theory behind computer networking.
The OSI model consists of seven layers:
7. Application layer - The layer you see (browsers, email apps, Whatsapp, Instagram etc.). Provides network services to the user. Data is created in this layer. When data is given to the application layer, the data is passed down to the presentation layer.
6. Presentation layer - The presentation layer receives data from the application layer, converts data into a form the receiving system can understand. Handles encryption, compression and data formatting. With this complete, the data is passed down to the session layer.
5. Session layer - When the session layer receives the correctly formatted data from the presentation layer, it looks to see if it can set up a connection with the other computer across the network, if it can't then it sends an error and the process goes no further. when 
                   the session layer has successfully logged a connection between the host and remote computer, the data is passed down to Layer 4: transport layer.
4. Transport Layer - Its first purpose is to chose the protocol over which the data is to be transmitted. Two main protocols TCP and UDP. TCP would usually be choosen where accuracy is favoured over speed (e.g. file transefer, or loading a webpage), and udp would be used in
                     situatuions where speed is more important (e.g, video streaming). With a protocol selected, the transport layer then divide the transmission up into byte-sized pices (over TCP these are called segments, over UDP they're called datagrams), which makes
                     it easier to transmit the message successfully.
3. Network Layer - Decides which path your data should take to reach the destination. For example, the internet is a huge network; when you want to request information from a webpage, it's the network layer that takes the IP address for the page and figures out the best 
                  route.
2. Data Link - The data link focuses on the physical addressing (MAC address) of the transmission. It receives a packet from the network layer (that includes the IP address for the remote computer) and adds in the physical (MAC) address of the receiving endpoint. The data 
              link layer also serves an important function when it receives data, as it checks the received information to make sure that it hasn't been corrupted during transmission, which could well happen when the data is transmitted by layer 1: the physical layer.
1. Physical - The physical layer is right down to the hardware of the computer. This is the actual cable, Wi-Fi radio, waves, light pulses, electrical signals. It's the job of the physical layer to convert the binary data of the transmission into signals and transmit them
               across the networ, as well as receiving incoming signals and converting them into binary

## Encapsulation
Encapsulation is the process of wrapping data with header information at each layer of the OSI model so the network knows how to deliver it.

| Layer | What it adds |
| ----- | ------------ | 
| Application Layer | Header | 
| Presentation Layer | Header | 
| Session Layer | Header |
| Transport Layer | Data (Segments/Datagrams) | 
| Network Layer | Data (Packets) |
| Data Link Layer | Data (Frames) |
| Physical Layer | Data Stream (bits) |


## De-encapsulation
De-encapsulation is the reverse process of encapsulation. Each layer removes its own header.

### How it works in Networking
When data reaches the receiving device (like your phone or laptop), it goes up the OSI model from Layer 1 to Layer 7.
Step-by-Step
* Physical Layer - Receives bits (0s and 1s) and rebuilds them into a frame
* Data Link Layer - Removes MAC address header, now it becomes a packet.
* Network layer - Removes IP address layer, now it becomes a segment
* Transport layer - Removes port number header - now it becomes data.
* Session / Presentation / Application Layers - Prepare and show the final message to the user

## TCP/IP Model
The TCP/IP model is, in many ways, very similar to the OSI model. It's a few years older, and serves as the basis for real-world networking. The TCP/IP model consists of four layers:
* Applicaion
* Transport
* Internet
* Network Interface

Note: When asked to justify why we bother with the OSI model if it's not actually used for anything in the real-world. The answer to that is simply because the OSI model tends to be easier for learning the initial theory of networking.
The processes of encapsulation and de-encapsulation work in exactly the same way with the TCP/IP model as they do with the OSI model.

## Lab (Wireshark)
In this task we're going to look at some captured network traffic to see the advantages of understanding the OSI and TCP/IP models.
Wireshark is a tool used to capture and analyse packets of data.
<img width="963" height="521" alt="image" src="https://github.com/user-attachments/assets/6446ed6c-4490-46fb-9360-34fe8f1d69cd" />

There are 5 pieces of information here:
* Frame 1 - this is showing details from the physical layer of the OSI model (Network Interface layer of the TCP/IP model): the size of the packet received in terms of bytes).
* Ethernet II - This is showing details from the data link layer of the OSI model (Network Interface Layer of the TCP/IP model): the transmission medium (in this cas an Ethernet cable), as well as the source and destination MAC addresses of the request.
* Transmission Control Protocol - This is showing data from the transport layer of the OSI and TCP/IP models: In this case it's telling us that the protocol was TCP, along with a few other things that we're not covering here.
* Hypertext Transfer Protocol - This is showing details from the Application layer of the OSI and TCP/IP models: Specifically, this is a HTTP GET request, which is requesting a web page from a remote server.

## Networking Tools - Ping
The ping command is used when we want to test whether a connection to a remote source is possible. Ping works using the ICMP protocol.
<img width="594" height="332" alt="image" src="https://github.com/user-attachments/assets/73142b5f-01a4-4a84-86b9-ece2170d59b8" />
<img width="576" height="214" alt="image" src="https://github.com/user-attachments/assets/51af1bc5-7794-4cdd-a626-7cb2653cf949" />

Notice that the ping command for google actually returned the IP address for the Google server that it connected to.

## Traceroute 
The logical follow up command is "traceroute". The easiest way to understand what traceroute does is to think of your home network. Say, for example, that you have a wireless router. Your phone is connected to it, as is your computer. What happens if you want to send 
something to your phone from your computer? You can't just send stuff directly to your phone -- not without directly connecting them, so how would the information get across? The request would be first sent to your router which acts as a gateway. The router knows every
device that's connected to it, ergo, it knows how to get to your phone. The return then forwards your request to your phone and facilitates the return connection in the same way. Traceroute can be used to map the path your request takes as it heads to the target machine.

Traceroute allows you to see every intermediate step between your computer and the resource that you requested.

<img width="754" height="432" alt="image" src="https://github.com/user-attachments/assets/0a72b4f2-1ad8-49fa-b4ce-e919dcb990d3" />

## Whois
Whois essentially allows you to query who a domain name is registered to.
Note: You may need to install whois before using it. On Debian based systems this can be done with <em><i>sudo apt update && sudo apt-get install whois</i></em>

## DIG
Ever wondered how a URL gets cnverted into an IP address that your computer can understand? 
The answer is a TCP/IP protocol called DNS (Domanin Name System)
At the most basic level, DNS allows us to ask a special server to give us the IP address of the website we're trying to access. If we made a request to www.google.com, our computer would first send a request to a special DNS server (which your computer knows how to find). 
The server would then go looking for the IP address for Google and send it to us. Our computer could then send the request to the IP of the Google server.

Dig allows us to manually query recursive DNS servers of our choice for information about domains. It is a very useful tool for networking.
Another piece of information that dig gives us is the TTL (Time To Live) of the queried DNS record.





