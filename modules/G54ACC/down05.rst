.. _G54ACCDOWN05:

=======================
IP & Down 05 - Ethernet
=======================

10Base5 and 10Base2 are "broadcast" networks, where 10BaseT with hubs were the
same, but just a simpler form of "star" wiring.

CSMA-CD protocol is used, so a host transmits if the wire is free, and
collisions are detected if multiple hosts transmit at the same time and backup
exponentially if more collisions occur.

Aloha
-----

Developed for radio-based comms. in Hawaii in 1970.

The basic idea is that when you're ready, transmit. The receivers send ACK for
data, and collisions are detected by timing out for ACK.

Collisions are recovered from by trying again after a random delay. If this
delay is too short then a large number of collisions may occur, and if it is
too long then the link may be underutilized.

Slotted Aloha
-------------

Time is divided into equal size slots (packet transmission time). A node
transmits a packet at the beginning of the next slot. If a collision occurs,
retransmit that packet in future slots with probability :math:`p` until
successful transmission occurs.

Efficiency
^^^^^^^^^^

Suppose N stations have packets to send. Each transmits in a slot with
probability :math:`p`, and the probabilit of successful transmission :math:`S`
is:

by single node: :math:`S = p(1-p)^{(N-1)}`

by any of N nodes: :math:`S = N p(1-p)^{(N-1)}`

To be stable (:math:`p \leq 1/N`): :math:`1/e = 0.37..~~as N \to \infty`

Therefore at best, the channel is useful for transmissions 37% of the time. Not
so good!

CSMA/CD
-------

CSMA/CD can be seen as Aloha with slot size :math:`2t` which then reserves the
channel for many slots.

:math:`2t` is the "collision window" - the time for a packet to propagate all
the way across the network and someone else to just start sending as it arrives.

Interval between successful packets:

.. math::

    I = (e-1)2t + T + t

where
* T = time taken to transmit packet
* t = diameter of the network (time for a packet to go from one side to the
      other) - so 2t is the time there and back

Efficiency
^^^^^^^^^^

As the speed of Ethernet networks increases, the network becomes less efficient
(due to the number of packets in flight when a collision occurs increasing). To
mitigate this, the network diameter could be made smaller, but this isn't
always feasible.

Switches
^^^^^^^^

CSMA/CD works well for certain packet sizes and physical network sizes, but
100Mbps for normal network traffic profile started to stress CSMA/CD in larger
LAN deployments.

So we needed to move away from pure CSMA/CD.

This started with "bridges" to partition CSMA/CD into smaller segments
- bridges originally connected two CSMA/CD segments. Then we moved to
full-blown switching.

Switches use buffering with FIFO queues on each interface, so that a single
packet is only ever on each Ethernet at a time, eliminating collisions
altogether.

Switches with buffers also allow the different interfaces to have different
speeds, so that switches can have faster "uplinks" to the backbone network.
