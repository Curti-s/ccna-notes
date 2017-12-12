- Understanding the difference between TCP and UDP
- The (secret) TCP 3-way handshake
- TCP sequence numbers and acknowledgements
- TCP windowing


A network communicates in layers. 

- Difference between TCP and UDP
---------------------------------------

TCP protocol at the transport layer
    - Builds connections  (connection-oriented)
    - Session
    - Uses sequence numbers
            > All sent packets are tagged with sequence numbers
    - Reliable (uses acknowledgement (ack))

UDP protocol at the transport layer
    - Connectionless 
    - Best-effort delivery
    - Unreliable : great for realtime traffic eg VoIP


- How TCP and UDP work
--------------------------
    - Secret TCP 3-way handshake
        * Computer sends a (SYN) Synchronized packet to the Server
        * Server receives the packet and replies with a (SYN-ACK)
        * Computer will send an ACK and data will be transmitted.
        * The session will be maintained as long as the client queries requests from the server.

        How the sequence number concept works
            client  >> router -->> router >> Server
            
            example 1

            seq 10 ------------------------->
                    <------------------------seq 5 | ack 11
            seq 11 | ack 6 ------------------>
                    <------------------------- seq 6 | ack 12

            example 2
            seq 100 ------------------------------->
                    <------------------------------ seq 300 | ack 101
            seq 101 | ack 301 ------------------------------->
                    <--------------------------------- seq 302 | ack 102

    NB:: not all efficient


- Tcp windowing
------------------
    TCP window scale option is the option to increase the receive window size allowed in Transmission Control Protocol above its maximum value of 65535 bytes. It is defined in IETF RFC 1323

    It increases how much data is sent based on how reliable a connection is.

    Upon unreliability, the packet window size is reduced. The dropped packets are re-transmitted. 

    When starting a TCP connection, the host will use a receive buffer where data is stored temporarily before application can process it.

    When the receiver sends an acknowledgement, it will tell the sender how much data it can transmit before the receiver sends another acknowledgement. This is the window size; indicating size of the receive-buffer.  

    Typically TCP will start with a small window size and increase with a successful acknowledgement.

        example
        Host1               Host2
                segment 1
                ---------->
                <----------
                ACK 2
    The host is sending a single segment and receives a single acknowledgement

                segment 2
                ----------->
                segment 3
                ------------>
                <-----------
                ACK 4
    The host is sending 2 segements and  receives a single acknowledgement; window size will increase

                segement 4
                ---------->
                segement 5
                ---------->
                segment 6
                ----------->
                segement 7
                ----------->
                < ----------
                ACK 8
    The host is sending 4 segments and receives a single acknowledgment; everything is fine.


    When the window size hits a maximum limit; i.e when the receiver doesn't send an acknowledgement within a certain period of time called the round-trip time, the window will be reduced.

    When an interface has congestion, it is possible that TCP packets are dropped. TCP has a number of algorithms to deal with congestion control.
        -> Slow start 

