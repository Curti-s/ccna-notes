### Understanding physical connections
---------------------------------------------------------

- View of network cards on pcs and cisco devices
- Understanding ethernet cabling
- Two type of ethernet cables

-----------------------------------------

     CAT5 cable disected
        8 colored wired twisted into 4 pairs
            - brown pair
            - green pair
            - blue pair
            - orange pair

        cables are twisted in order to reduce the amount of electromagnetic interference and cross-talk.

        orange and green wires send and receive data respectively.

        striped wire -> positive
        solid wire -> negative

        blue and brown wires are reserved for future bandwith capacity

        Bandwith tells us how much data can flow through the wires on the cable.
        Network speed tells us at what rate can data move  on a wire.

        T-568A wire order
            striped green,green,striped orange,solid blue,striped blue,solid orange,striped brown,brown

        T-568B wire order
        striped orange,orange,striped green,blue,striped blue,green,striped brown,brown

        Cabling standards
        -----------------
        T568A + T568A = straight-through
        T568A + T568B = crossover

            - straight-through is used for unsimilar network devices. eg pc to switch
            - crossover is used for similar network devices. eg router to hub or pc to pc without a switch or a hub

        Reallife cabling
        ----------------
            from wall jack --> patch panel --> switch
            patch panel - intermediary device to allow connections to the switch using patch cables.

        Understanding ethernet cable
        ----------------------------
            cat5 utp
                max distance 100meters
                connector RJ45
                
            multimode fiber
                max distance 275 meters to a few miles
                
                allows for multiple signals to be sent across the fibre strand
                
                connection varies

                it can work with cheaper equipment.

                have greater bandwith compare to single mode fibre

            single fiber
                max distance 1 mile to many miles
                connection varies
                expensive connectors which could be proprietary
                can in between states.

                it uses a thinner core compared to multimode

        

