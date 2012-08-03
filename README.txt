Release Notes for MegaPirateNG 2.7 R3 (ArduCopter 2.7.1)

=== How to compile MegaPirateNG ===

1. Download and install Arduino 1.0.1!!!!
2. See additional requirements for BlackVortex boards in the release_notes_BlackVortex.txt
3. Delete original libraries folder in Arduino IDE folder
4. Copy libraries folder from MegaPirateNG distributive into Arduino IDE folder
5. Select your Frame, Sensor, Tranmitter type in the APM_config.h (Quad X, ALLINONE by default)


=== MPNG History ===
--- 2.6 R6
Added support for CRIUS All In One PRO v1 board

--- 2.6 R4
Improved I2c_spy.pde to catch 6050 I2c slave devices and also 5611 baro
Fixed bug in compass initialization for boards with MPU6050
Fixed bug in AP_GPS_NMEA

--- 2.6 R3
Fixed GPS initialization for BlackVortext boards

--- 2.6 R2
Added support for Drotek 10DOF IMU

--- 2.5.1 R3
Fixed compass initialization for MPU6050+HMC5883L
MT3329 initialization fixed in case of Cold start

--- 2.5.1 R2
Fixed compilation bug in BMP085 library

--- 2.5 R2
Fixed compass error
Fixed define redeclaration in APM_Config.h

--- 2.4.1 R2
Restored FastPWM, 400Hz by default, can be changed in APM Planner, RC_SPEED value
GPS Initialization fixed, at least my MTK16 protocol now work fine
Stability fix for InstantPWM

--- 2.4.1
Fixed bug in FFIMU sensor board, thanks to Thomas(thnilsen)
Fixed LED Sequencer initialization code, thanks to Thomas(thnilsen)

--- 2.3 rc1
TX configuration moved from APM_RC_PIRATES.cpp to common configuration file APM_config.h

--- 2.3
Version is compatible with Arduino IDE 1.0!

=== Arduino board pin mapping ===

*** RC channels (can be changed in APM_RC_PIRATES.cpp) ***
* PPM SUM signal must be connected to A8 pin
* Default is TX_mwi - MultiWii set
A8	- ROLL
A9	- THROTTLE
A10	- PITCH
A11	- YAW
A12	- AUX1
A13	- AUX2
A14	- CAMPITCH
A15	- CAMROLL

*** Camera stabilization ***
d32 - Camera stabilisation Roll servo
d33 - Camera stabilisation Pitch servo
For BlackVortex:
d44 - Camera stabilisation Roll servo
d45 - Camera stabilisation Pitch servo

*** GPS ***
RX2 - TX on GPS
TX2 - RX on GPS

*** Telemetry (XBee, APC220, Bluetooth)
RX3 - TX on XBee
TX3 - RX on XBee

*** CLI switch ***
a5 - Enter CLI switch (tie to ground to enter CLI) 

*** Sonar ***
d9 - Sonar Tx 
d10 - Sonar Echo 

*** Status LEDs ***
d13 - RED
d30 - YELLOW
d31 - GREEN

*** LED Sequencer ***
A1,A2,A3,A4 - default LED sequencer pins (read more in led.pde),

*** Motor mapping ***
motor mapping (maximize your text viewer or disable word wrapping to avoid line breaks)
======================================================
Pin     D2    D3    D5    D6    D7    D8    D11   D12   - Arduino pins
CH      3     4     1     2     7     8     10    11    - MegaPirate output channel
======================================================
TRI     S     BC    RC    LC    -     -     -     -
QuadX   LFW   RBW   RFC   LBC   -     -     -     -
Quad+   FW    BW    RC    LC    -     -     -     -
Hexa+   BLW   FRC   FW    BC    FLC   BRW   -     -
HexaX   FLW   BRC   RW    LC    FRC   BLW   -     -
Y6      LDW   BDW   RDW   LUC   RUC   BUC   -     -
Octo+   FRC   BRC   FW    BW    FLC   BLC   LW    LW    - Mapping changed since 2.0.39 version!!!
OctoX   RRFC  BBRC  FFRW  BBLW  FFLC  LLBC  LLFW  RRBW  - Mapping changed since 2.0.39 version!!!
Quad8X  BLUC  BLDW  BRUC  BRDW  FLUC  FLDW  FRUC  FRDW  - Support added in 2.0.36
Quad8+  BUC   BDW   RUC   RDW   LUC   LDW   FUC   FDW   - Support added in 2.0.36
======================================================

Motors description:
B- back
R- right
L- left
F- front
U- upper
D- lower
W- clockwise rotation
C- counter clockwise rotation (normal propeller)
S- servo (for tri)

Example: FLDW - front-left lower motor with clockwise rotation (Y6 or Y4)