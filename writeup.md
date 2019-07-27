# Writeup

The 3D Drone exercise from the classroom is a very good starting point for most
of the functions, although there are some calculations involved.

<p align="center">
<img src="misc/control1_mod.png" width="500"/>
</p>
<p align="center">
<img src="misc/control2.png" width="500"/>
</p>

## Animation result:
<p align="center">
<img src="animations/scenarios.gif" width="500"/>
</p>

## Scenario 1
A simple tune of the `Mass` parameter will be enough to pass.

## Scenario 2
### 1. Body rate control:

Function `BodyRateControl()`: [source code](./src/QuadControl.cpp#L92-L117)
Calculate the moments with the help of the following equation:
<p align="center">
<img src="misc/bodyrate.png" width="500"/>
</p>


Function `GenerateMotorCommands()` [source code](./src/QuadControl.cpp#L56-L90)
Calculate the desired thrust for each motor with the help of the following equations:
<p align="center">
<img src="misc/propellers.forces.png" width="500"/>
</p>
<p align="center">
<img src="misc/propellers.moments.png" width="500"/>
</p>

Parameter tuning:
`kpPQR`

### 2. Roll / Pitch control:
Function `RollPitchControl()`: [source code](./src/QuadControl.cpp#L120-L165)
It involves some calculations as well:
<p align="center">
<img src="misc/rollpitch.png" width="500"/>
</p>

Parameter tuning:
`kpBank`

## Scenario 3

### Position and Altitude:
Function `LateralPositionControl()`: [source code](./src/QuadControl.cpp#L214-L262)
<p align="center">
<img src="misc/lateralpos.png" width="500"/>
</p>


Function `AltitudeControl()`: [source code](./src/QuadControl.cpp#L167-L211)
Solving the equation:
<p align="center">
<img src="misc/altitude.png" width="500"/>
</p>

Parameter tuning:
`kpPosZ`, `kpPosZ`, `kpVelXY` and `kpVelZ`

### Yaw:
Function `YawControl`: [source code](./src/QuadControl.cpp#L265-L293)
<p align="center">
<img src="misc/yaw.png" width="500"/>
</p>

### Parameters tuning:
`kpYaw` and `kpPQR`

## Scenario 4
Function `AltitudeControl()`: [source code](./src/QuadControl.cpp#L167-L211)
Added the integratedAltitudeError, storing the error over time.

## Scenario 5-8:
WIP still need some parameter tuning.