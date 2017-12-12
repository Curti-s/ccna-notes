- Configuring passwords on a cisco switch
- Understanding ssh
- Setting up port security -> (covered in next session)


- Configuring passwords in a cisco switch
------------------------------------------ 
    command::
        telnet 172.30.2.180

            password required but none set
            Connection to host lost
    
    If passwords aren't set in a cisco switch, it's not going to allow telnet.

    command::
        enable
        configure terminal
        enable password cisco 
    This form of setting up passwords is considered legacy. Because it can easily seen in the running-config.
 
    command::
        enable secret cisco1
    Performs secure password creation through encryption.

    NB::
        Negating enable password in global conf ig mode
        command::
            no enable password



- Configuring console security
---------------------------------
    command::
        enable
        configure terminal
        line console 0 -> (now in line configuraition)
        password cisco
        login

This will propmt a password upon login into the console.


- Line vty  
------------
    Virtual Terminal
    Virtual teletype ports 
    They are the ports that accept telnet connections.

    - Enable vty security
    ---------------------
        command:: 
            enable
            configure terminal
            line vty 0 1
            login
            password cisco

        Remote management is much faster than console connection.

    - Encrypt all passwords
    --------------------------
        With 1 command, you can encrypt all cisco passwords.
        
        It provides level 7 password encryption which is weak.
        
        However it doesn't provide much processor consumption as compared to level 5 (MD5-encryption)encryption.
        
        Level 7 encryption helps to eliminate line of sight password creation.

        command::
            service password-encryption    

- Banner configuration
-------------------------
    Setting up log on banners. 

        command::
            enable
            configure terminal
            banner ?
                motd - set the Message of the Day banner
                login - set login banner
            banner motd ?
                 LINE c banner-text c, where 'c' is a delimiting charater.
            banner motd [ ******************************************** DO NOT LOG ON *****************************************]


- Setting up ssh
--------------------
    Telnet only supports clear text security.
    
    In order to setup, first you require username and password. 
    
    Then a domain  name is required in order to generate encryption certificates.

    Thereafter, generate the encryption keys.

    Define the version of ssh which you would want to use.

    Get into line configuration and allow only ssh transport input

        command::
            username Jeremy password cisco
            ip domain-name cbtnuggets.com
            crypto key generate rsa 1024
            ip ssh version 2
            line vty 0 4
            transport input ssh
            
- Setting up port security
-------------------------------
    A way to lockdown how many/what devices can connect to your switch.

        command::
            show ip interface brief
                A command showing all quick view of the IP address of the router and a table list of the interfaces and their status.

    Switches learn mac addresses 

        command::
            terminal monitor
                A command that allows one to see all the messages that come from the switch from a telnet session.

        command::
            show mac address-table
                A command that shows all mac addresses within the switch.

        - Configure fastEthernet 0/5 to only accept a specific mac address
        -------------------------------------------------------------
            * Literally port 5 on the switch.

            Q. How is it that there can be more that one mac address connected to a fastEthernet port within a switch?
            A. Because it is a trunk port.

            Enable mac address security for fastEthernet 0/5
            
            Enable port security

            Enable violation policy if another device connects to the fastEthernetport 0/5

            Hardcode the mac address which will only connect through the port.

                command::
                    enable
                    configure terminal
                    interface fastEthernet 0/5
                    switchport mode access
                        * it hard codes the port connecting to an end device.
                        * access port means that it is connected to an end device (pc,server,router, but most def not another switch).
                    switchport port-security maximum 1
                        * only allow one mac address
                        * it will only show in the running- config if the maximum is set to beyond 1.
                    switchport port-security violation
                        * by default is shutdown. Therefore --
                    switchport port-security violation shutdown 
                    switchport port-security mac-address 0015.o5af.ca37 / sticky
                        * H.H.H 48 bit mac address
                        * sticky configure dynamix addresses as sticky.
                        * sticky will automatically hardcode the mac addresses assigned to the ports and copy to the running configuration.

        - Showing the port security for interface fastEthernet 0/5
        ------------------------------------------------------------- 
            command::
                show port-security interface fastEthernet 0/5

        - Configure port security for all switch ports at once
        ---------------------------------------------------------
            command::
                interface range fastEthernet 0/2 - 24

                    This will configure all 24 interfaces.