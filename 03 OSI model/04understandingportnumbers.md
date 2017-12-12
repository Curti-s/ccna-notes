- How port numbers work
- Well known port numbers

- Port numbers
------------------------
    - Each time an application communicates across the network, it not only chooses which protocol (tcp\udp) it will use but also it has to generate port numbers; destination port and source port.
    
    - By combining the IP address and the port number, you generate a socket or a session.
        eg 10.5.1.100:80    ---> tcp port 80 for http connection.

    - they separate different applications on our network.
    - destination port numbers dictate what service your are trying to reach.
    - source port numbers provide the service you are trying to reach a way to communicate with your pc.
    - well known ports 0 -1023

HTTP uses TCP port 80 for the world wide web.
HTTP reserves also a port 80 for udp connections

NB:
    0 - 1023 are considered as well-known/reserved ports. Anything after that are considered registered port numbers.

TCP and UDP each have 65535 reserved port numbers. However, they work differently across the protocols. eg port 900 works differently compared between UDP and TCP.

    Examples of well-known port numbers

        TCP <0-65535>
            21 - ftp 
                - used to send files back and forth to the server.
            
            22 - ssh 
                - encrypted version of telnet.
                - cryptographic network protocol for operating network devices securely over unsecure network eg managing cisco devices
                
            23 - telnet
                - provides bidirectional interactive text-oriented communication facility using a virtual terminal connection. No security.

            25 - smtp
                - sending email, when mail servers send and receive emails.

            53 - dns server
                - dns servers resolve names to IP addresses. eg google.com (216.58.223.78). dns servers use that port when they need to send dns records to each other.

            80 - http

            110 - pop3
                - post office protocol. For receiving email.

            443 - https
                - secure web surfing

        UDP <0 - 65535>
            53 - DNS client
                - for resolving IP addresses and url names

            69 - TFTP
                - Trivial file transfer protocol. Used to send and receive files to and from cisco devices.