## Incident
You are a cybersecurity analyst working at a company that specializes in providing IT services for clients. Several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, and saw the error “destination port unreachable” after waiting for the page to load. 

You are tasked with analyzing the situation and determining which network protocol was affected during this incident. To start, you attempt to visit the website and you also receive the error “destination port unreachable.” To troubleshoot the issue, you load your network analyzer tool, tcpdump, and attempt to load the webpage again. To load the webpage, your browser sends a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name; this is part of the DNS protocol. Your browser then uses this IP address as the destination IP for sending an HTTPS request to the web server to display the webpage The analyzer shows that when you send UDP packets to the DNS server, you receive ICMP packets containing the error message: “udp port 53 unreachable.”

![[Pasted image 20260622125101.png]]
## notes:
**Resources**
- [Cybersecurity incident report template](https://docs.google.com/document/d/1hwjSRYalxGd-qyRIXWz8LBVuSAgEq0AHXOF_BB7DdrI/template/preview?usp=sharing)
- [Example of a Cybersecurity Incident Report](https://docs.google.com/document/d/17-l7_zLY9fWiS4lGemxqgbnfSe8KG_OqM_PMfZA_gp4/template/preview "Example of a Cybersecurity Incident Report")


## Incident Report:

### Part 1
**Provide a summary of the problem found in the DNS and ICMP traffic log.**
*The UDP protocol reveals that:* the DNS server's udp port 53 is unreachable, DNS server not listening on said port. 

*This is based on the results of the network analysis, which show that the ICMP echo reply*
*returned the error message:* ICMP [SERVER IP] udp port 53 unreachable length 254
This means the DNS server is not listening on UDP port 53

*The port noted in the error message is used for:* DNS query service

*The most likely issue is:* The DNS server is temporarily down
### Part 2
**Explain your analysis of the data and provide at least one cause of the incident.**
*Time incident occurred:* 13:24:32.192571 -> 1:24:32

*Explain how the IT team became aware of the incident:* Several customers filed a complaint when trying to access the website www.yummyrecipesforme.com as it did not load and after some time displayed an error message `destination port unreachable`.

*Explain the actions taken by the IT department to investigate the incident:* Running a `tcpdump` analysis when accessing the website resulted in more information about what was happening.

*Note key findings of the IT department's investigation (i.e., details related to the port affected, DNS server, etc.):* Analysis of the `tcpdump` shows the website throwing an error with an ICMP echo message stating UDP port 53 on the DNS server is unreachable. 

*Note a likely cause of the incident:* DNS server is temporarily down.

## Final
### Part 1
**Provide a summary of the problem found in the DNS and ICMP traffic log**
The network protocol analyzer (packet sniffer) logs indicate that there is an issue with UDP Port 53 on the DNS server being queried to resolve the IP for the web address  
www.yummyrecipesforme.com. The ICMP echo message indicates that the port is unreachable which could mean the server is down.

### Part 2
**Explain your analysis of the data and provide at least one cause of the incident**
The initial incident occurred at 1:24 PM when customers complained their inability to access the website www.yummyrecipesforme.com. Because the DNS server's udp port 53 was unreachable, it indicates that the DNS server is not listening for traffic on that port. This most likely means the DNS server is overloaded or temporarily down.

## Exemplar
[Cybersecurity incident report exemplar](https://docs.google.com/document/d/11YIrN6R3fTqw7AWeh_4YCB4QXK8VnO4_CYPSK2MU5xc/edit?usp=sharing "Cybersecurity incident report exemplar")

[Cybersecurity incident report exemplar explained](https://docs.google.com/document/d/19kE466MVHdIRk86EOkUFvbepahRIMMIu5lDDgCBkg0E/template/preview#heading=h.rkogpw759h9x "cybersecurity incident report exemplar explained")
