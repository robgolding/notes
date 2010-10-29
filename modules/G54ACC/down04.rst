.. _G54ACCDOWN04:

======================
IP & Down 04 - Optical
======================

Ethernet Optical
----------------

10BaseFL
    850nm light wave, could transmit over 2km
100BaseFX
    1300nm over 2km
100BaseSX
    850nm
100BaseLX
    1300nm over 10/20/40km - "single mode" fibra

Loads more standards for 1G and 10G speeds...

Optical Fiber
-------------

A light source generates continuous light (LEDs, lasers for example). The
signal is then modulated onto this light, and then transmitted.

This is received by a photodetector, over long distances (>1000km) and at very
high speeds (>40Gbps/wavelength) - and nearly error free!

Optical fiber has had a profound influence on network architecture. They
dominate long-distance transmission, and allow for plentiful bandwidth.

Multi/Single Mode Fiber
^^^^^^^^^^^^^^^^^^^^^^^

In multimode fiber, multiple rays follow different paths down the fiber, which
is "wider", so the light can reflect off the edges. LEDs or lasers can be used
with multimode fiber.

In single mode fiber, there is only one direct path that the light can take,
which results in a tighter pulse width. Only lasers can be used with single
mode fiber.

Properties of Optical Fibre
^^^^^^^^^^^^^^^^^^^^^^^^^^^

======================================== ======================================
Advantages                               Disadvantages
======================================== ======================================
Very low attenuation                     New types of signal impairments/dispersion
Noise immunity                           Limited bend radius (can break)
Extremely high bandwidth                 Difficult to "splice"
No corrosion                             Mechanical vibration causes noise
More compact/lighter than copper         
Long distances (>1000km)                 
High speeds (>40Gbps/wavelength)         
Nearly error free (BER of :math:`10^-15` 
======================================== ======================================

Wavelength Division Multiplexing
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

We can use a single fiber to carry multiple wavelengths, with each wavelength
carrying a separate signal.

If a single fiber can carry 160 wavelengths, with 10Gbps on each wavelength,
that equals 1.6Tbps. Whoosh.

Regenerators and Amplifiers
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Optical amplifiers amplify the optical signal (without equalizing it or
regenerating it). They also amplify the noise, however - but we can get across
the atlantic using just amplifiers.

If we need to regenerate the signal, it must be converted to an electrical
signal first, then retransmitted as an optical signal.
