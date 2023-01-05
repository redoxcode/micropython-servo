## Description
A micropython library to control rc servos in a tidy way. 

This uses hardware PWM as an efficient way to generate the ouput signal. 
But therefore servos need to be connected to pins with PWM functionallity.

The servos can be calibrated using 2 points (min / max position).
The default values should work for most servos, but won't set the servo to the exact position, as these values are different for each servo model.

## Examples
### Move servo
```Python
import time
from servo import Servo
my_servo = Servo(pin_id=28)
my_servo.write(30)
time.sleep(2.0)
my_servo.write(60)
time.sleep(2.0)
my_servo.write(90)

```

## API
### class Servo(pin_id,min_us=544.0,max_us=2400.0,min_deg=0.0,max_deg=180.0,freq=50)
- pin_id: id of the pin connected to the servo
- min_us: minimal pulse width (calibration point 1 / there is no clipping if you try to set the servo to a lower value)
- max_us: maximal pulse width (calibration point 2 / there is no clipping if you try to set the servo to a higher value)
- min_deg: minimal position in degrees (calibration point 1 / there is no clipping if you try to set the servo to a lower value)
- max_deg: maximal position in degrees (calibration point 2 / there is no clipping if you try to set the servo to a higher value)

```write(deg)```
- move the servo to the given position
- deg: Position in degrees

```read()```
- returns the position last set in degrees

```write_rad(rad)```
- move the servo to the given position
- rad: Position in radians

```read_rad()```
- returns the position last set in radians

```write_us(us)```
- set the pulse width for the servo
- us: Pulse width in us

```read_us()```
- returns the last set puls width

```off()```
- disables the output
