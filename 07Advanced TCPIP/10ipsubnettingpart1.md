- Subnetting based on network requirements
-----------------------------------------------------------------------
	Subnetwork is the logical division of an IP network
	- Network Scenarion #1
	--------------------------------
		An organization with class C address 216.21.5.0, subnetmask 255.255.255.0

		Steps of subnetting
		--------------------
			Network requirements:
				 5 networks
				 216.21.5.0, subnetmask 255.255.255.0

			* Determine the number of networks and convert to binary
				-> 5 networks:
					128 64 32 16 8 4 2 1
					0	0	0  0 0 1  0 1
  
					= 00000101

			* Reserve bits in a subnet mask and find your increment
				 NB::
				 	subnet mask is used to divide the IP address into network and host addresses.

					 3bits required for 5 networks

					 255.255.255.11100000
					 	:
						 128 + 64 + 32 = 224

					 subnet mask = 255.255.255.224

			* Use increment to find your network ranges	
				The increment is the lowest network bit converted to decimal

				216.21.5.0 - 216.21.5.31
				216.21.5.32 - 216.21.5.63 
				216.21.5.64 - 216.21.5.95  
				216.21.5.96



	CIDR notation:
		class A 255.0.0.0 -> /8
		class B 255.255.0.0 - > /16
		class C 255.255.255.0 - > /24

			NB::
				How many ones within the subnet mask

				