# Create Melody

```python
from pyKamipi.pibot import *

kamibot = KamibotPi('COM3', 57600)

HALF = 0.25
ONE = 0.5
TWO = 1

notes = [36, 40, 43, 36, 40, 43, 45, 45, 45,  43, 41, 41, 41, 40, 40, 40, 38, 38, 38, 36]
pitch = [ONE, ONE, ONE, ONE, ONE, ONE, ONE, ONE, ONE, TWO, ONE, ONE, ONE, ONE, ONE, ONE, ONE, ONE, ONE, ONE]

for i in range(len(notes)):
    print(i)
    kamibot.melody(notes[i], pitch[i])

kamibot.close()
```
