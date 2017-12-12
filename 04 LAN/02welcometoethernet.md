- Evolution of the Ethernet
- CSMA/CD - essence of ethernet technology
- Methods of communicating in the LAN
- Official explanation of a MAC address


#### Ethernet (fabric of networks)
------------------------------------ 
    1973: Xerox invents Ethernet (3Mbps)

    1982: Standardization of Ethernet between vendors (10Mbps)

    1995: Fast Ethernet emerges (100Mbps)

    2000: Gigabit Ethernet emerges (1000Mbps)

    2002: 10 Gigabit Ethernet emerges (10000Mbps)

    2007: 100 Gigabit Ethernet emerges (100000Mbps)


### Understanding speed and size in Networks
--------------------------------------------------
    1 Byte is relatively equivalent to 1 character.

    ( Storage ) Byte --- KiloByte --- Megabyte --- Gigabyte --- Terabyte

    ( Network speed) bit

    ** _8bits -> 1byte_ **


    Ethernet is found in layer 1 and 2 of the OSI layer
        Data link layer is divided into:
            * Logical link control layer
            * Media Access Control layer

### Fabric of networks:: Ethernet
--------------------------------------
    Ethernet to the OSI layer. It matches to the bottom 2 layers of the OSI model. (data link and physical layer)

    Data link
        * Media Access Protocol
                - Defines the addressing that ethernet uses and defines the standards that each computer needs to have a MAC address that ties to an Ethernet network.

        * Logical Link Control
                - Picks what direction it is going to go in the network layer(houses IP addresses). 
                - Provides multiplexing mechanisms that make it possible for several network protocols (eg IP,IPX,Decnet and AppleTalk) to co-exist within a multipoint network and to be transported over the same network media.
                 - Also provides flow and error controls


                
### Carrier Sense, Multiple Access with Collision Detection
-------------------------------------------------------------- 
    - set of rules governing how you communicate on an Ethernet network.
        - Carrier: network signal
        - Sense: ability to detect a carrier signal at the time
        - Multiple access: all devices have equal access to the ethernet work. They  have to wait when one device is transmitting.
        - Collision: what happens when devices send at once.
        - Detection: How computers will handle collision when it happens.

        NB:
            Token ring uses CSMA/CA; a token passed among devices in a ring topology network.
            
            The problem with CSMA/CA only reaches maximum speed of 33Mbps and cannot superseed that. 
            
            Also it doesn't deal with data recovery and retransmission after a collision.
            
            Therefore CSMA/CD by Ethernet was adopted.
            
            CSMA/CD is typically used in wired connections because it is possible to detect whether a collision occured. It minimizes recovery time. Wireless installations typically use CSMA/CA.


### Methods of communication
--------------------------------
    * Unicast
        - single point to single point communication

    * Broadcast
        - single point to multiple points communication (all devices in the network).
        - Floods the network stream, whereby computers may choose whether to receive the data or not.

    * Multicast
        - single point to a group communication.
        

### MAC address (official explanation)
---------------------------------------
    - Hexadecimal characters (12)
    - Divided into 6,6
    
    - First 6 --> Organizational Unique Identifiers (OUI) (24 bits) 00:91:01

    - Second 6 --> Vendor assigned (24 bits) 22:DC:F3 ds for "NOT ON