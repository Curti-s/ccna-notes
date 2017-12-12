- What is the Cisco IOS?
- How to get help in the IOS
- Understanding the IOS modes


- What is the Cisco IOS?
-------------------------
    Internetwork Operating System

    A command line method of configuring a cisco networking devices

    More powerful than any graphic device. Learn it once, use it many times.
 
 - Connecting to a Cisco switch
 ----------------------------------
    * Get a console cable
    * Plug the serial end into the back of your pc
    * Plug the RJ45 end to the console port on switch
    * Terminal programs for programming cisco device
        - hyperterm -> worst program, comes with windows.
        - teraterm
        - minicom
        - putty
        - securecrt -> not free

    * Set it to connect via the com port with:
        - band rate: 9600
        - data bits: 8
        - parity: none
        - stop bits: 1
        - flow control: none 

        NB:: parity bit sets the parity of transmitted data for the purpose of error detection.

    Hit the (?) command to get help 
        eg cl?
            **clear** **clock**
            clock?
                **set** **set time and date**
    Capital letters are variables requiring input

    <cr> carriage return means you have finished typing the command.
    -  Saving configuration made in global configuration:
        * first downgrade to privilege exec mode
        * run: copy running-config startup-config
    
    - Show history
    - Show running-config  file.

- Understanding IOS command modes
------------------------------------
    switch>   :User mode (user exec) 
    switch#   :Privilege mode (privilege exec) 
        - cannot configure a switch.
    switch(config)#  :Global configuration mode

        * switch from user exec to privilege exec using ``` enable``` command
        * switch from privilege exec to configuration mode using <configure terminal>
        * downgrade from one mode to another using (ctrl+z)  or (exit)

        help 
            (?)


- Additional info
-----------------------
    Get a list of open ports in linux machine
        netstat -lntu
            -l = only services which are listening to some port
            -n = show port number, dont try to resolve host names
            -t = tcp ports
            -u = udp ports
            -p = name of the program
