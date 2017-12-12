- Styles of and facts about wireless networks
- World of radio-frequency
- Wireless network standards and organizations

- Types of wireless networks
******************************
    Personal Area Network (PAN)
        - eg bluetooth headset

    Local Area Network (LAN)
        - 

    Metropolitan Area Network (MAN)
        - point to point wireless bridges
    
    Wide Area Network (WAN)
        - leads to Cellular

- Wireless LAN facts
-----------------------
    (WAP) Wireless Network Access Point
        - Operates and Communicates like a hub.
        - Involves sharing signals and half duplex speeds.
        - The more clients joining a wireless access point, the less the bandwith. The speed reduces to half duplex, since there is no way to send and receive data at the same time.

        - WAP uses unlicensed bands of radio frequency.
            * Unlicensed RF means that RF(s) which are unmanaged.
        
        - Wireless is a physical and data link standard.
        - Uses CSMA/CA instead of CSMA/CD.
            * Differences
                1. CSMA CD takes effect after collision while CSMA CA takes effect before collision.
                2. CSMA CA reduces the possibility of a collision while CSMA CD only minimizes recovery time.
                3. CSMA CD is typically used in wired connections while CSMA CA is used in wireless networks.

        - It faces connectivity issues because of interference.

- Unlicensed frequencies
---------------------------

    - Think like free parking spots.
    - RF waves are absorbed by passing through walls or reflected by metal.
    - Higher data rates have shorter ranges. The further I move from the Access Point, the slower the data rate.
    - Higher frequencies of RF have higher data rates and shorter ranges.

    ** Check out cisco wireless explorer game.

    900 MHz
        range: 902 - 928

    2.4GHz 
        range: 2.400 - 2.483

    5GHz
        range: 5.150 - 5.350

- 802.11 Lineup
-------------------
    - The de facto wireless standard.
    
    - 802.11a 
    -------------
        * Official as of Sept 1999
        * Up to 54mbps
        * Not cross-compatible with 802.11b/g
        * 12 to 23 clean channels.
        * 5.8GHz Frequency 

    - 802.11b
    ------------
        * Official as of september 1999
        * Up to 11 mbps 
        * Most popular
        * Frequency 2.4GHz
        * Has 14 channels with 3 clean channels.
        * 22MHz wide spaced at 5MHz intervals


    - 802.11g
    -------------  
        * Official as of June 2003
        * Backwards compatible with 802.11b
        * up to 54 mbps (12 data rates)
        * 3 clean channels
        * 2.4GHz frequency
        

- Undestanding wireless channels
------------------------------------
    - Channels are ranges of frequency.   
    - IEEE standards for wireless networking are worldwide bearing difference in speed,distance, channels and frequencies.

    - 5GHz     
         For 802.11a and 802.11n standards
         
         802.11a uses Dynamic Frequency Selection (DFS) in order to avoid interference with weather and military satelites.

        These standards use Orthogonal Frequency Division Multiplexing; 
                    - To transmit data streams over a given bandwith
                    - Provide 23 non-overlapping channels, where diff channels are used in differen countries.
        
        802.11n adds MIMO (miltiple input and multiple output), where;
                - supports more than 1 antenna
                - supports up to 4 transmit and 4 receive data streams.

    - 2.4GHz
        802.11b
        Uses Direct Sequence Spread Spectrum (DSS)

        Data is "chipped" and transmitted across different frequencies in predefined order.

        802.11g and 802.11n
        Uses Orthogonal Frequency Division Multiplexing (OFDM)

- Powers over the wireless world
--------------------------------------
    International Telecommunication Union - Radio Communication Sector (ITU-R)
        - It regulates the radio frequencies used for wireless transmission.

    Institute of Electrical and Electronic Engineering (IEEE)
        - Maintains the 802.11 wireless transmission standards.

    WiFi Alliance:
        - Ensures certified interoperability  between 802.11 wireless technologies.
         