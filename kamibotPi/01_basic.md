# Basic

## Move 

```python
from pyKamipi.pibot import *

# Connect to KamibotPi
kamibot = KamibotPi('COM9', 57600)

# -------------------------------------------------------------------------
# go_dir_speed(left wheel direction, speed, right-wheel direction, speed)
# -------------------------------------------------------------------------
# 앞으로
kamibot.go_dir_speed("f", 10, "f", 10)
kamibot.delay(3)

# 뒤로
kamibot.go_dir_speed("b", 10, "b", 10)
kamibot.delay(3)

# 왼쪽으로 돌기
kamibot.go_dir_speed("f", 0, "f", 50)
kamibot.delay(3)

# 오른쪽으로 돌기
kamibot.go_dir_speed("f", 50, "f", 0)
kamibot.delay(3)

kamibot.stop()

# 카미봇 연결 해제
kamibot.close()
```
