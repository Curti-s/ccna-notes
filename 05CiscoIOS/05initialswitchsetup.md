- Understanding physical indicators
- Observing the boot process
- Performing the initial configuration

 
 - Physical indicators
 -----------------------
    * System
        - green --> good
        - amber --> something wrong with the switch
    
    * Redundant Power Supply (RPS)
        - green --> good
        
        Modes
        -----
    * STAT
        - status of the port
        - default mode
        - blinks upon network activity. If nothing is plugged, then it becomes dark. 

    * Util
        - utilization. Shows the current utilization.

    * Duplex
        - full duplex
        - half duplex

    * Speed


    - Booting up a switch
        - It stores its IOS in the flash filesystem.

        - It then takes the IOS from flash and copies it to the RAM while uncompressing it.



    - VLANs
        a group of devices on one or more LANs that are configured to communicate as if they were attached to the same wire, when in fact they are located  on a number of different LAN segements.
        The fabric in which all the switch ports are connected to.
         

    - Interface VLAN1
        virtual logical interface which every port in VLAN1 can access

    NB: the switch modes are very important to the commands that you are going to execute.

    no shutdown
    
- Saving switch configuration
--------------------------------
    show running-config
        will show literally every command typed in the switch.

    Save the configuration in a startup-config (stable memory)

    copy running-config startup-config
        - This will copy the running configuration from the RAM to NVRAM --> Non-Volatile RAM.

    show startup-config

    It is really benefitial to have the two configuration files.



- Show version
--------------------
    Displays what is going on within the switch generally.

    show version  