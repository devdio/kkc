# Basic

# Check COM Port  
```shell
pip install pyKamipi
```
  
```python
import serial.tools.list_ports

ports = serial.tools.list_ports.comports()
print([port.name for port in ports])
```


## Move   
  
```python
from pyKamipi.pibot import *

# Connect to KamibotPi
kamibot = KamibotPi('COM3', 57600)

# -----------------------------------------------------------------------------------------------
# go_dir_speed(left_wheel_direction, left_wheel_speed, right_wheel_direction, right_wheel_speed)
# -----------------------------------------------------------------------------------------------
# move forward
kamibot.go_dir_speed("f", 10, "f", 10)
# wait 3 second
kamibot.delay(3)

# move backward 3 sec
kamibot.go_dir_speed("b", 10, "b", 10)
kamibot.delay(3)

# turn left
kamibot.go_dir_speed("f", 0, "f", 50)
kamibot.delay(3)

# turn right
kamibot.go_dir_speed("f", 50, "f", 0)
kamibot.delay(3)

# stop all action
kamibot.stop()

# disconnect to KamibotPi
kamibot.close()
```

## Move with precision  
  
```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

# ------------------------------------------------
# move_forward_unit
# ------------------------------------------------
kamibot.move_forward_unit(10, "-l") # 10cm
kamibot.delay(1)

kamibot.move_forward_unit(3, "-t") # 3sec
kamibot.delay(1)

kamibot.move_forward_unit(50, "-s") # 50 step
kamibot.delay(1)

# ------------------------------------------------
# move_backward_unit
# ------------------------------------------------
kamibot.move_backward_unit(10, "-l") # 10cm
kamibot.delay(1)

kamibot.move_backward_unit(3, "-t") # 3sec
kamibot.delay(1)

kamibot.move_backward_unit(50, "-s") # 50 step
kamibot.delay(1)

kamibot.close()
```

## Rotate in place  
  
```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

# ------------------------------------------------
# turn_right_speed(degree)
# ------------------------------------------------
kamibot.turn_right_speed(360) # 360 degrees
kamibot.turn_left_speed(90)  # 90 degrees

kamibot.close()
```

## LED  
  
```python
from pyKamipi.pibot import *

# 카미봇 연결
kamibot = KamibotPi('COM3', 57600)

# ------------------------------------------------
# turn_led(red-value, green-value, blue-value)
# ------------------------------------------------
kamibot.turn_led(255, 0, 0)     # RED
kamibot.delay(1)                # wait 1 sec
kamibot.turn_led(0, 255, 0)
kamibot.delay(1)
kamibot.turn_led(0, 0, 255)
kamibot.delay(1)

kamibot.close()
```

## Display Random Color

```python
import random
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

for i in range(1000):
    red_value = random.randrange(0,255)
    green_value = random.randrange(0,255)
    blue_value = random.randrange(0,255)
    kamibot.turn_led(red_value, green_value, blue_value)
    kamibot.delay(0.1)

kamibot.close()
```

## Check distance from obstacles  
  
- The closer the obstacle is, the larger the value.  
```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

# -----------------------------------------------------
# left_distance, right_distance = get_object_detect()
# -----------------------------------------------------
while True:
    left, right = kamibot.get_object_detect()
    print(f"left={left}, right={right}")

# stop checking    
kamibot.get_object_detect(False)

kamibot.close()
```

## Line Sensor 

- 1 if the bottom is black, otherwise 0
```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

# ------------------------------------------------------
# left_val, center_val, right_val =  get_color_sensor()
# -----------------------------------------------------
for i in range(1000):
    color = kamibot.get_color_sensor()
    print(f"color={color}")
    

# stop checking  
kamibot.get_color_sensor(False)

kamibot.close()
```

## Color Sensor
**Color recognition is not perfect.**
```
0: Black
1: Red
2: Orange
3: Yellow
4: Green
5: Blue
6: Sky Blue
7: Purple
8: White
```

```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

# ------------------------------------------------
# color_value = get_color_sensor()
# ------------------------------------------------
for i in range(1000):
    color = kamibot.get_color_sensor()
    print(f"color={color}")
    

# Stop Checking
kamibot.get_color_sensor(False)

kamibot.close()
```

## Melody
```
The first argument can be any number from 0 to 83. For example,

36 : 4-Octave Do
37 : 4-Octave Do#
38 : 4-Octave Re
39 : 4-Octave Re#
40 : 4-Octave Mi
41 : 4-Octave Fa
42 : 4-Octave Fa#
43 : 4-Octave Sol
44 : 4-Octave Sol#
45 : 4-Octave Ra
46 : 4-Octave Ra#
47 : 4-Octave Si
48 : 5-Otave Do
```

```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)
#----------------------------------------------
#  melody(pitch, sec)
#----------------------------------------------
while True:
  kamibot.melody(36, 1)
  kamibot.melody(38, 1)
  kamibot.melody(40, 1)

kamibot.close()

```

## Top Motor (Degree)

```python
import random
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

# ------------------------------------------------
# top_motor_degree(direction, degrees)
# ------------------------------------------------
kamibot.top_motor_degree("l", 180)  # turn left
kamibot.delay(1)

kamibot.top_motor_degree("r", 180)  # turn right
kamibot.delay(1)

kamibot.close()
```
  
## Top Motor (Absolute Position)
```python
import random
from pyKamipi.pibot import *

# 카미봇 연결
kamibot = KamibotPi('COM3', 57600)

#----------------------------------------------------
# top_motor_abspos(asolute-position)
#--------------------------------------
kamibot.top_motor_abspos(0)
kamibot.delay(1)

kamibot.top_motor_abspos(90)
kamibot.delay(1)

kamibot.top_motor_abspos(180)
kamibot.delay(1)

kamibot.close()

```

## Top Motor (Time Duration)
```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

# ---------------------------------------------
# top_motor_time(direction, sec)
#--------------------------------------------
kamibot.top_motor_time("l", 5)
kamibot.delay(1)

kamibot.top_motor_time("r", 5)
kamibot.delay(1)

kamibot.close()

```
