- Configuring speed and duplex
- The place of the spanning-tree protocol
- Using show commands to troubleshoot networks.

- Configuring speed and duplex
--------------------------------
    Every port on a cisco switch has both the speed and duplex set to auto.
    
    That means that the ports will auto-detect everything that plugs in. i.e speed of their network cards and what duplex.

    However, auto-detect mechanism are obsolete and mostly result to duplex mismatch.

    For instance resolving duplex mismatch between a half-duplex router and full-duplex switch at interface fastEthernet 0/2

        Connect to the switch
        Connect to the fastEthernet interface 0/2

            command::
                interface fastEthernet 0/2 
                duplex half
                    * will shutdown the port temporarily
                speed 10


    NB::
        Success rate for auto detection --> 90% - 95%

- Tips
---------------
    * Fixing spontaneous occurrence of messages on the console and virtual terminal.
 
    * Indicate either the console or vty interfaces to allow for configuration.
        command::
            enable
            configure terminal
            line console 0
            logging synchronous
            exit


        command::
            enable
            configure terminal
            line vty 0 4
            logging synchronous
            exit
              
    * Execution timeout; by default the idle time is set to 5min. However that can be modified in global line configuration mode
        command::
            enable
            configure terminal
            line con 0
            exec-timeout 30 0
                * means for 30 min and 0 sec

        * Also this can be configured for vty
            command::
                enable
                configure terminal
                vty 0 4
                exec-timeout 30 0

    * Domain lookup for wrongly typed commands; for instance when typing and you accidentally type a wrong command, most def the cisco IOS will perform a domain lookup. Negate it
        command::
            enable
            configure terminal
            no ip domain-lookup

    * Setting up short-cut/aliases for commonly typed commands
        command::
            enable
            configure terminal
            alias exec s show ip interface 
            
- Spanning tree protocol
------------------------------
    * Friday night fun *
    ---------------------
    - STP is a layer 2 protocol that runs on bridges and switches.
    - STP specification D.
    - Main purpose, to ensure that you don't create loops when you have redundant paths in your network. Loops are deadly to a network.


    - Creating redundant links
    ***************************
            single link         redundant link           single link
        PC  ----------- SWITCH <----------------> SWITCH ------------- PC

        - There exist 2 links, i.e redundant links connected using 2 crossover cables between the 2 switches.
        - If a pc sends a broadcast, the lights in the switch will blink (like maad) because there will be loop in the broadcast.
        - This is because the switch will send the broadcast to all its ports, forwarding it the next switch which will also send the broadcast to all its ports.
        - A loop will occur between the 2 switches hence the pcs will freeze due to too many broadcast messages hitting them. i.e broadcast storm.

        - By design switches forward broadcast packets to all ports.
        - The solution is not terminating the redundant paths.
        - Redundant connections are necessary in business networks.

        - The place of the Spanning tree protocol is to drop trees on redundant links until they are needed.
        - The redundant link will be blocked, meaning that there will not be any broadcast storms in the network. It will only be revived when the active link goes down.

        - The Spanning Tree Protocol will watch upon the active link, whether it is forwading and receiving packets until when it goes down, then the redundant link will be activated.

- Troubleshooting
********************
    * Demistifying information on a fastEthernet Interface
    ---------------------------------------------------------
        command::
            enable
            show interface fastEthernet 0/2
            output::
                FastEthernet0/2 is up -> Physical layer.
                line protocol is up -> Data link layer.
                (bia 000c.854b.ee82) -> built in address
                MTU 1500bytes -> Maximum Transmission Unit
                BW 10000 Kbit -> Bandwith
                DLY 1000 usec -> Delay
                reliability 255/255, -> 100% reliability
                txload 1/255 -> how much is being transmitted   
                rxload 1/255 -> how much is being received
                Half-duplex,
                10Mb/s
                media type is 10/1000BaseTX
                0 runts -> a packet that is just too small; it doesn't have too much information.
                0 giants -> a packet that is too large compared to an normal packet. They get dropped.
                0 collisions -> can be due to duplex mismatch
                0 late collisions -> due to long cables,or rather a very long distance between the source to the destination, where there exists switches in between them.

            command::
                enable
                show running-config

