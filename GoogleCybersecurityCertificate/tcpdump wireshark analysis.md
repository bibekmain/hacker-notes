### Scenario
You work as a security analyst for a travel agency that advertises sales and promotions on the company’s website. The employees of the company regularly access the company’s sales webpage to search for vacation packages their customers might like. 

One afternoon, you receive an automated alert from your monitoring system indicating a problem with the web server. You attempt to visit the company’s website, but you receive a connection timeout error message in your browser.

You use a packet sniffer to capture data packets in transit to and from the web server. You notice a large number of TCP SYN requests coming from an unfamiliar IP address. The web server appears to be overwhelmed by the volume of incoming traffic and is losing its ability to respond to the abnormally large number of SYN requests. You suspect the server is under attack by a malicious actor.

You take the server offline temporarily so that the machine can recover and return to a normal operating status. You also configure the company’s firewall to block the IP address that was sending the abnormal number of SYN requests. You know that your IP blocking solution won’t last long, as an attacker can spoof other IP addresses to get around this block. You need to alert your manager about this problem quickly and discuss the next steps to stop this attacker and prevent this problem from happening again. You will need to be prepared to tell your boss about the type of attack you discovered and how it was affecting the web server and employees.

Link to template: [Cybersecurity incident report](https://docs.google.com/document/d/1xEk_arFwlQOto7KEM6gN-sIYriXhP9-lY2ftpBXhS4M/template/preview?resourcekey=0-_ODneeo__mDgK7BTE1FkVA "template for cybersecurity incident report")
Links to supporting materials: 
- [Wireshark TCP/HTTP log](https://docs.google.com/spreadsheets/d/1enpRzrIao3J2Lp2tOI0hmu1Cu7D7CjLGhFAiTiR9J64/template/preview?gid=218501934#gid=218501934)
- [How to read a Wireshark TCP/HTTP log](https://docs.google.com/document/d/1JYyUPhfm2gwDellGRIcgItA3cZ7kz29xdYpVr1L_o9c/template/preview?usp=sharing)

### Notes
 Automated alert showed an issue with the server. Sniffing the network showed an unusually large number of TCP SYN requests from an unknown IP. A **Denial of Service** attack is underway. The server is taken offline and the IP is blocked. However this is temporary because the attacker can use another device or use **IP Spoofing** to disguise as a familiar IP. Objective is to create an analysis report of the incident and potential next steps.

### Analysis

**Section 1: Identify the type of attack that may have caused this network interruption**
One potential explanation for the website's connection timeout error message is that someone is attacking the web server.

The logs show that a single IP address `203.0.113.0` was sending TCP SYN packets without responding. It started out with a few requests which eventually saturated the ports available and made the server slow down enough that real employees were getting a 504 Gateway Timeout error because the gateway server saw that the web server was taking too long to respond.

This event could be a DoS attack, more specifically a TCP SYN flood attack.

**Section 2: Explain how the attack is causing the website to malfunction**
When website visitors try to establish a connection with the web server, a three-way
handshake occurs using the TCP protocol. Explain the three steps of the handshake:
1. SYN: Synchronize step is first sent by visitors to initiate a communication with a web server. This is letting the server know initially that you want to use it's service.
2. SYN/ACK: Synchronize/Acknowledge is then sent by the server to the visitor, acknowledging that the server has received their synchronization request.
3. ACK: Ultimately, the visitor sends an Acknowledgment stating that they received the Server's acknowledgment to the SYN request.
When a malicious actor sends a large number of SYN packets all at once, for all SYN requests the server sends a corresponding SYN/ACK request and opens a port for the final ACK it expects to receive from the client. However, if no ACK is received, the port on the server opened stays used up until the server's connection time out triggers it to reset. If someone sends more SYN packets than there are ports, in a faster interval than the timeout metric, the server can no longer function.

The logs indicate that initially the attacker established a TCP connection with the web server, meaning they sent a SYN request and an ACK request at the end of the handshake. This could be to establish themselves as a normal user to the server or just them visiting the site normally. Then the attacker starts flooding the server with only SYN requests every few hundred milliseconds. After a few seconds, the attacker has taken up about half of the traffic to the web server and normal clients' (employees') requests start getting throttled. This happens with a mix of RST/ACK packets being sent by the server, indicating that the server is not receiving the ACK by clients, probably due to port saturation, and a 504 Gateway Timeout which is essentially the same thing, indicating the gateway didn't receive a response from the web server.