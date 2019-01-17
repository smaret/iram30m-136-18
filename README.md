README file for project 136-18
==============================

Project summary
---------------

This project aims at mapping the C18O (2-1) and N2H+ (1-0) line
emission in the Class I protostar L1489 with the IRAM-30m.

Observation setup
-----------------

We use the EMIR receivers together with the FTS backend at 50 kHz
resolution. The two lines are observed simulateously, in dual band
mode (E090 and E230). The FTS backend at a 50 kHz is used in parallel
with VESPA.

We use the OTF PSW observing mode to cover a region of ~ 2' x 2'. The
target sensitivity is 40 mK per 0.14 km s-1 channel at 1mm, which
should be reached in ~21 hours of telescope time, assuming average
winter conditions (4.0 mm of PWV).

Typical PAKO session
--------------------

```
! Startup
!--------

@ ini

! Select a planet, set the receivers and backend and do a calibration
! to send the receiver setup. This also moves the telescope to the
! planet.

source mars
@ receiver-c18o
@ backend-c18o
calibrate /default
start
pause "Ready to tune the receivers."

! Do another calibration to check if the system temperatures are OK

calibrate /default
start
pause "Please check that the system temperatures are OK."

! Do a pointing and a focusing on Mars

set focus -2       ! a good starting point
@ pointing-mars
pause "Please enter the pointing corrections."
set point  YY XX

@ focus
pause "Please enter the focus corrections."
set focus FF

! Do a pointing on a strong quasar close to L1489

@ pointing-quasar
pause "Please enter the pointing corrections."

set point  YY XX


! C18O (2-1) and N2H+ (1-0) map 
!------------------------------

! Make 2 maps (each map takes about 30min)

@ otfmap-c18o
@ otfmap-c18o

! Make a pointing 

@ pointing-quasar
pause "Please enter the pointing corrections."

! Make 2 more maps

@ otfmap-c18o
@ otfmap-c18o
```
