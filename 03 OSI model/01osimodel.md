Request for Comments RFC
TCP windowing technique

### Functions of Open Systems Interconnect
-----------------------------------------------
- Helps break down network functions
- Create standards for equipment manufacturers
- Allow vendors to focus in specialized areas of the network.

### OSI Model
-----------------
    Application

        - Interfaces with the applications and allows their communication.  eg web browser
        - Provide networks access to apps 

    Presentation

        - Generifying data.  Data becomes formatted in a generic format, understandable by the recepient. eg web browser format data in html format. 
        - Encryption services. Generic encryption services in the sense that both the client and web server will be  able to do it together.

    Session

        - Start and end sessions and privatizes sessions.
        - Logically keeps sessions separate.

         NB :
            Application layer, Presentation layer and session layer are least important in Cisco since it is handled by the operating system. Cisco devices never look past the transport layer... secure foundations.

           Most important
    Transport 

        - Most important layer of them all
        - Dictates how data is sent.
        - Choose to send data either reliably or unreliably
            - Reliable data transport (TCP)
                If the application chooses this mode, when it sends a packet to the server, it expects back an acknowledgement packet.

                It's benefitial in case where you are tranferring huge file across the network and when packets are dropped, they are re-transmitted.

            - Unreliable data transport (UDP)
                Typically used for realtime application, for instance Voice Over IP(VoIP).

                Also Video Over IP, watch tv or movie online in realtime.

                If packets are dropped,they aren't transmitted over again. It makes no sense to transmitt them over again.

        - Defines well-known services (port)
            Port numbers, allow you to designate what service you are trying to access.

            Eg a client wants to access a webpage from a webserver, transport layer ensures that the request goes to the designated web server not any other server. Therefore it partners with the Session layer. 
            The computer still defines the source port number which will distinguish the web application from the others , which accesses the server.

    Network

        - Provides logical addressing --> IP address
        - Finds the best path to a destination

    Data link

        - Provides Physical addressing --> MAC add
        - Ensure data is error free.

    Physical
        - Provides physical access to the cable
        - Generates electrical signals, (0,1) 
    

    OSI in the real world
    ---------------------------
        - Client sends a request to www.cicso.com, >> by default the computer sends the message to a DNS (Domain Name Service) server, which transforms the url into IP. eg (200.1.1.1)

        The application makes a http request for the cisco webpage.

        The presentation layer packages the webpage data into HTML format

        The session layer creates a private session for the webpage request.

        At the transport layer, 2 choices are made:
            - need for reliablity, (TCP)
            - need for realtime (UDP) 

            Hardcoding of source and destination numbers at the transport layer, meaning transport layer partners with session layer in keeping things private. 

            In this case, the browser harcodes a destination port 80 where the request should be sent. 
            
            The comp will assign a source port number that will distinguish the web browser from others.(dynamic source port number).
                * used netstat to view ftp connections to cisco.com
                * ftp ftp cisco.com
        
        Network layer provides logical addressing, by defining source IP address and Destination IP address.

        Data link layer provides physical addressing. 
            Destination and Source MAC addressing are identified.

            In order for a client to send a request to a server, which isn't connected to its own network, it will have to send  to it through its default gateway --> (router). However, IP address, from end to end doesn't change unlike MAC address which is bound to change all the time.

            When a message is sent through a gateway, the MAC address of the router is identified as destination address, but the data link layer looks up the network layer for the destination IP and routes it there. 

            This is an overview describing why we need 2 addresses.

        The physical layer, where data is received at the NIC card.
        

 
Ethernet RJ45 connectivity

 similar --> crossover
 unsimilar --> straight-through