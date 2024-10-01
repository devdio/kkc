# Line Tracer

## Line Sensor
```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

# ------------------------------------------------
# left, center, right = get_line_sensor()
# ------------------------------------------------
while True:
    left, center, right = kamibot.get_line_sensor()
    print(f"left={left}, center={center}, right={right}")
    
kamibot.close()
```

## Line Tracer
```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

kamibot.go_forward_speed(50, 50)
flag = True

while flag:
    left, center, right = kamibot.get_line_sensor()
    print(f"left={left}, center={center}, right={right}")

    if center == 1:
        kamibot.go_forward_speed(10, 20)
    elif left == 1:
        kamibot.go_forward_speed(10, 70)

    elif right == 1:
        kamibot.go_forward_speed(70, 10)
    else:
        pass

kamibot.close()
```

## Line-Tracer On/Off
  
```python
# ------------------------------------------------
# Line-Tracer On/Off
# ------------------------------------------------
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

kamibot.toggle_linetracer(True, 100)
kamibot.delay(10)
kamibot.toggle_linetracer(False)

kamibot.close()

```





