network analysis using arp-scan nmap

### Basic TCP/IP
-----------------------------
##### Addressing fundamentals
-------------------------------

    - How OSI and TCP/IP relate
    - Understanding the two address concept
    - IP address format
    - Default IP address classes
    - Public vs Private addresses


    - How OSI and TCP/IP relate:

                OSI                                 TCP/IP
                --------------------------------------------

       04 Application, Presentation, Session -->    Application

        03 Transport   -->                          Transport

        02 Network     -->                          Internet

        01 Datalink, Physical     -->               Network Access

    TCP superseeded OSI however OSI is widely used to describe networking. TCP/IP is how the network happens.

    TCP/IP is a suite of protocols which make communication happen.
        Application layer 
            example of applications found here Telnet,Ftp,SMTP,DNS,SNMP,RIP

        Host-to-Host Transport layer 
            examples of applications 
                TCP,UDP
        
        Internet layer
            example of application working here 
                ICMP,IGMP 
                IP,
                ARP
        
        Network Interface Layer
            examples of applications working here
                Ethernet, Token Ring, Frame Relay, ATM


### IP Address formatting
----------------------------
    - 4 numbers/octets, each from 0 to 255
            eg 172.30.5.82

    - always combined with a subnet mask and typically a default gateway
            ip      :172.30.5.82
            mask    :255.255.255.0
            gw      :172.30.5.1 

    - the subnet mask dictates which portions of the IP address defines the network and the host
    
    NB:
        255 represents network
        0 represents host 
        It is best to break up a network when it grows larger to avoid congestion. 



- Understanding the two address concept
------------------------------------------
     
     Network     IP Address (x.x.x.x)
     Datalink    Ethernet MAC address(xx:xx:xx:xx:xx:xx)
     Physical    electrical bits

    Every interface of a router represents a new network. It breaks collision and broadcast domains.  

     Address Resolution Protocol (ARP) 
        -> a broadcast message between connected clients within the same network. 
        When a client broadcasts an ARP to a client connected within the same network, it responds with its MAC address
            10.1.1.10 --> (send ARP request) --> 10.1.1.11 
        The client will then transmit data to the other client by talking to its MAC address. (local communication)

        Computers never speak directly through the IP address but through the MAC address (Datalink address).
        

        (internet communication)
        client1(10.1.1.10) -------> server(10.5.5.100)

            Different networks are involved here.... 
            Routers break broadcast domains and provide a default gateway.

### ARP basics
---------------- 
    Address Resolution Protocol

    Systems keep an ARP look-up table where they store information about what IP addresses are associated with what MAC addresses.

    When trying to send a packet to an IP add, the system performs an ARP lookup to see if its MAC add is already known/cached.

    If the IP add is not found in the ARP table, the system will send a broadcast packet to the network using ARP protocol to ask "who has 192.168.1.1". Since it is a broadcast packet, it is sent to a special MAC add that causes all machines on the network to receive it.

    The machine with the requested IP will reply with an ARP packet saying "i am 192.168.1.1" and this includes a MAC add that can receive packets for that IP.

### ARP table
    If there are multiple similar IP addresses, there may be multiple responses.
    
    Once the the IP is in the ARP table,the MAC add is cached to be used in the future until the entry expires or forcibly cleared.

        Listing MAC addresses
            arp -an
            sudo tcpdump -lni any arp

    When sending a packet to a machine on the public internet, the packet is sent to the MAC address of the router interface which is the default gateway (layer 2). IP address is used to figure out the MAC address to send using ARP.

    The machine will send an ARP request to the gateway which will respond with its MAC address as it overwrites the existing source MAC address and the destination MAC address after doing an ARP request . The information will then be given to the gateway to deliver to the destination IP address. 


### Default address classes
    3 usable classes of addresses
        - class A:
            > First octet of IP address 1-126
            > eg 10.5.1.1
            > Has the subnet mask 255.0.0.0
            > 2^24 hosts = 16,777,214

        - class B
            > First octet of IP addresses 128-191
            > eg 150.51.233.1
            > Has the subnet mask 255.255.0.0
            > 2^16 hosts = 65536

        - Class C
            > First octet of IP address 192-223
            > eg 220.1.50.63
            > Has the subnet mask 255.255.255.0
            > 2^8 hosts = 256 

    NB: 
        Cisco recommends that you shouldn't go above 500 hosts per network since the broadcast traffic may affect perfomance of the pc attached to the network.  

        Any address that starts with 127.x.x.x is preserved for loopback


### Public and Private Addresses

    Public address
        - Usable on the internet and internal networks
    Private address
        - Usable only in the internal networks

        Ranges of private networks
            > class A
                10.0.0.0 - 10.255.255.255
            > class B
                172.16.0.0 - 172.31.255.255
            > class C
                192.168.0.0 - 192.168.255.255
            
            Default IP classes
            Loopback range used for testing - 127.x.x.x
            Auto-configuration range - 169.254.x.x   
                If a host cannot obtain an IP address
                (kinda like help i need an IP address :))

                