# Sensor

### Eye Color

```python
# Red, Orange, Yellow, Green, Sky_blue
eye(color)
eye(left_color, right_color)
left_eye(color)
right_eye(color)
```
```python
albert.eyes(255, 0, 0, 0, 255, 0) # left: red and right: green
wait(500) # 0.5 seconds

albert.eyes(0, 0, 255) # both: blue
wait(500) # 0.5 seconds

albert.eyes("off") # turn off both eyes
```

### Proximity sensor
```python
# 0 ~ 255
left_proximity()
righ_proximity()
```

### light sensor
```python
light()

```

### sound
```python
sound(s_id)
sound(s_id, count)
```
s_id : BEEP, RANDOM BEEP, NOISE, DIBIDIBIDIP, SIREN, ENGINE, ROBOT, MARCH, GOODJOB

```python
from roboid import *

albert = AlbertAi()

# play sound and wait until done
albert.sound_until_done("siren")

# random beep: 3 times
albert.sound_until_done("random beep", 3)

albert.sound_until_done("robot")
```
