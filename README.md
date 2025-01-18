# Network-Level-Analysis

Brief: - The activity comprises of analyzing  DNS and ICMP traffic in transit using data from a network protocol analyzer tool. The goal is to identify which network protocol was utilized in assessment of the cybersecurity incident. 
In the internet layer of the TCP/IP model, the IP formats data packets into IP datagrams. The information provided in the datagram of an IP packet can provide security analysts with insight into suspicious data packets in transit.

Scenario : -  Several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, and saw the error “destination port unreachable” after waiting for the page to load.
              The task is to analyze the situation and determine which network protocol was affected during the incident.

Analysis Perfomed :- To troubleshoot the issue, the network analyzer tool (tcpdump) was loaded and an attempt was made to login to the webpage. The analyzer revealed that when an UDP packet is sent to the DNS server an ICMP packet is received containing
                    an error message :-  “udp port 53 unreachable.” 

TCPDUMP LOG:   The first two lines of the log file show the initial outgoing request from your computer to the DNS server requesting the IP address of yummyrecipesforme.com. This request is sent in a UDP packet.
              The third and fourth lines of the log show the response to your UDP packet. In this case, the ICMP 203.0.113.2 line is the start of the error message indicating that the UDP packet was undeliverable to port 53 of the DNS server.
              In front of each request and response, you find timestamps that indicate when the incident happened. In the log, this is the first sequence of numbers displayed: 13:24:32.192571. This means the time is 1:24 p.m., 32.192571 seconds.
              After the source and destination IP addresses, there can be a number of additional details like the protocol, port number of the source, and flags. In the first line of the error log, the query identification number appears as: 35084. The    plus sign after the query identification number indicates there are flags associated with the UDP message. The "A?" indicates a flag associated with the DNS request for an A record, where an A record maps a domain name to an IP address. 
The error message, "udp port 53 unreachable" is mentioned in the last line. Port 53 is a port for DNS service. The word "unreachable" in the message indicates the UDP message requesting an IP address for the domain "www.yummyrecipesforme.com" did not go through to the DNS server because no service was listening on the receiving DNS port.
![image](https://github.com/user-attachments/assets/674fc51f-de8c-4a63-9ea8-e9c6ce905720)
