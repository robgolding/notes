.. _G54ACCDOWN02:

===========================
IP & Down 02 - Multiplexing
===========================

**Space division multiplexing**
    Reuse of a channel in different places (e.g. terrestrial TV)

**Frequency division multiplexing**
    Use of different frequencies within a channel (e.g. terrestrial TV also!)

**Time division multiplexing**

**Code division multiplexing**

Multiplexing (STM)
------------------

Telephone network is referred to as STM (*Synchronous Transfer Mode*).

Links are shared with a fixed cyclical schedule, so bandwidth is fixed and is
used even if the link is idle (silence on the phone line, for example).

The destination of the data is decided based upon where it came from, and
*when* it came.

Hardware is simple, so very high speed.

Multiplexing (PTM)
------------------

The internet uses PTM (*Packet Transfer Mode*).

Packets have a header that defines the destination of the packet, and packets
can be of an **arbitrary size**.

Hardware is more complex (as it has to lookup the label in the packet header),
so is slower.

Multiplexing (ATM)
------------------

*Asynchronous Transfer Mode* is like PTM in that the destination of data is
determined by the header of a packet, however all packets are the **same
size** and the label is very small (so lookup is much faster). The label
refers to a virtual circuit that only exists on a particular router/switch, so
it has to be altered at every hop.

Statistical Multiplexing
------------------------

If an application uses 1Mbps of a 10Mpbs link, 10% of the time, then with STM
1Mb of bandwidth must be allocated to each user of the application - so it
could support 10 at a time.

With PTM/ATM however, it could support between 10 and 100 users (depending on
luck, delay etc.).

Randomness
^^^^^^^^^^

To calculate the probability that more than 10 users talk at once (and hence
the probability that we loose packets), me must understand the random
transmission of packets (or the *stochastic* process). This has been a research
topic for the last 30 years, and is still so.

It was first applied to the early telephony network by a mathematician
called Erlang, and is still an issue today with MPEG encoding on digital TV
networks.

Managing Queues
^^^^^^^^^^^^^^^

Queueing theory usually involves a Poisson process, though it is difficult to
apply this to network queues, as they typically have a dependency on the hosts
that are communicating, or the network itself.

Code Division Multiple Access (CDMA)
------------------------------------

Allows multiple users to coexist within the same frequency space, with minimal
interference.

Each user is assigned a unique code, which allows them to receive the data
being transmitted. It is very difficult to receive the signal (or indeed
interfere with it) if you do not know the code.

When data is transmitted, it is "hopped" around on different frequencies, the
order of which is determined by the code. This makes it very difficult to
intercept transmissions, and also hard to jam them (as you would have to jam
*all* the frequencies that are being used, which is very difficult).

Direct Sequence CDMA
^^^^^^^^^^^^^^^^^^^^

* Code is called the *chip sequence*
* The data is XORed with the chip sequence at the transmitter
* The data is then XORed again with the chip sequence at the receiver

CDMA is the basis for 3G mobile technology, and GNSS/GPS also. It allows
multiple data streams to be encoded onto one frequency, which can all then be
extracted with their unique chip sequences. This is how GPS transmitters
& receivers work.
