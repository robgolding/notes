.. _G54ACCDOWN03:

=======================
IP & Down 03 - Physical
=======================

Modulation
----------

* Amplitude modulation
* Frequency modulation
* Phase shift modulation
* Amplitude *and* phase modulation
* Amplitude/frequency/phase shift *keying*
    * Discrete set of levels/frequencies used to encode digital data

Quadrature Amplitude Modulation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If we combine phase-shift keying with amplitude modulation, we can encode more
bits with each phase. This is called *Quadrature Amplitude Modulation*.

High-speed modems use QAM64, and digital television now uses QAM256 (i.e. 256
different code-points that are possible to encode with each wave phase).

Telephones
----------

Original telephone network was designed to carry human voice, at 0-5KHz.

The digital telephone netwoek started by digitizing the voice signal. It is
sampled at 12 bits (compressed to 8) at 8KHz.

Decoding
--------

To decode the bits at the other end, the phase receivers must learn the phase,
and the amplitude receivers must deal with attenuation. QAM receivers must do
*both* of these things.

Another problem to overcome is that if we send a constant signal (i.e. all
zeroes), the receiver may not be able to tell if they are in phase or not (or
whether they are seeing a stream of ones or a stream of zeroes).

To deal with this, scramblers are used to make sure that the bits are changing
often. The scrambler is a pseudo-random bit sequence, which is then XORed with
the data stream at the sender and at the receiver. These are widely used in the
traditional digital phone network.

Block Codes
^^^^^^^^^^^

Map single bit or bits to be transmitted as more bits. This guarantees that the
bit transitions take place on the wire, so that the signal does not stay
"empty", and confuse the receiver.
