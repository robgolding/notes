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

Error Detection
---------------

If, for example, ``10001`` is received in a 4b5 coding system. This could
have been a 1 bit error from ``10101`` or ``10011`` (as ``10001`` is not
a valid bit pattern for 4b5 coding).

Parity
^^^^^^

A simple parity bit for every byte/word spots odd numbers of bit flips. A 2D
parity can correct single bit errors.

There are many more types of parity/code checks. For example, Hamming codes
- with (7,4) being the canonical, and SECDED - a (72,64) Hamming code used in
DRAM.

CRCs
^^^^

CRCs view the data as a binary polynomial (call it :math:`D`). Then, choose
a *generator* polynomial :math:`G`, of length :math:`r+1`.

Then, calculate the remainder :math:`R=D*2^r/G`.

Then transmit :math:`D*2^r+R`.

At the receiver, if :math:`(D*2^r+R)/g = 0` then there are no errors.

CRCs have good *provable* properties of error detection, and it is easy to
build hardware to implement the algorithm. It is, however, slow to calculate
CRCs in software.

CRCs are very popular - CRC32 is used in all 802.3s (Ethernet, WiFi).

Reed Solomon
^^^^^^^^^^^^

Message is a binary polynomial of length :math:`k`. Polynomial is evaluated at
:math:`n` distinct points :math:`(n>k)`, and :math:`n` values are sent.

Message can be recovered if the receiver receives any :math:`k`.

The Hamming distance is :math:`n-k+1`.

CDs use RS codes - (32, 28) and (28, 24) and interleave the results. This means
a bit error of 4000 bits can be recovered from - or a scratch of 2.5mm on the
CD.

RS coding is also used for deep space transmissions to spacecraft.
