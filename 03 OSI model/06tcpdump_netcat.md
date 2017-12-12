- Introduction to tcpdump
----------------------------
    syntax : tcpdump [options] [protocol] [type]

    options:    -n : do not convert addresses (i.e host addresses, port numbers etc) to names.
                -nn : number for machine and ports. Do not resolve host names or port names.
                -i : sniff packets from a particular interface.
                -v : verbose(-vv or -vvv)
                -w : dump packets in a file
                -r : read packets from a file
                -x : print hex
                -X : print hex and ascii
                -A : print ASCII
                -s : define the snaplength (size) of the capture in bytes. Use -s 0 to capture everything unless you are intentionally capturing less. Default 68bytes.
                -S : print absolute sequence numbers
                -c : get x number of packets then stop.
                -t : give human readable timestamp output.
                -ttt : give maximally human-reaable timestamp output.
                -q : be less verbose with output
                -D : show list of available  interface.
                -e : get ethernet header as well.
                -E : decrypt IPSEC traffic by providing encryption key

    protocol: ether, ip, ip6, arp, rarp, tcp, udp

    type:   host : packets to and from host
            net :  packets to and from network
            port : packets to and from port
            portrange : packets to and from range of ports.
            src : packets from this source only
            dst : packets to this dest only.


There are 3 types of expressions used: type, dir and proto
    * Type options:
        - host 
        - net
        - port
    * Directions lets you do src,dst and combinations thereof.
    * Proto(col) lets you designate : tcp, udp,ah, icmp etc

- Combine using logical expressions
-----------------------------------------
    "and" "or"

    eg  tcpdump -nn -X -s 0 tcp and dst 192.168.0.101
            -- means grab all tcp packets going to dest 192.168.0.101
            
        tcpdump -X tcp and port 80 and host 192.168.0.101


- Netcat
-----------