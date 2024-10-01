# Follow hands 

# Check distance
```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)
# ------------------------------------------------
# left_val, right_val =  get_object_detect()
# ------------------------------------------------
while True:
    left, right = kamibot.get_object_detect()
    print(f"left={left}, right={right}")
    
kamibot.get_object_detect(False)
kamibot.close()
```

## Follow hands

```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)
# ------------------------------------------------
# get_object_detect
# ------------------------------------------------
while True:
    left, right = kamibot.get_object_detect()
    print(f"left={left}, right={right}")

    if left > 0 or right > 0:
        kamibot.go_forward_speed(50, 50)
    else:
        kamibot.go_backward_speed(50, 50)

kamibot.close()
```
