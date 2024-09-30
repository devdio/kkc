# HelloAI

## Basic Flows 
  
```python
from helloai import *

# ---------------------------------------
# Global Variable
# ---------------------------------------
msg = 'hello ai'
num = 0

def setup():
    # Initializing variables 
    # When you run a program, run it only once.
    print('>>>>> SETUP <<<<<')

def loop():
    global num

    # run infinitely  
    print('MSG---> ', msg, '+', num)
    num = num + 1
    delay(1000)

    if num > 5:
        stop()

def end():
    # Run when the program exits  
    print('***** END *****')

# ---------------------------------------
# To run helloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```

## Using HelloAI and KamibotPi together  
  
```python

from helloai import *
from pyKamipi.pibot import *

# ---------------------------------------
# Global Variable
# ---------------------------------------
# Connect to KamibotPI
kamibot = KamibotPi('COM3', 57600)

def setup():
    # Initializing variables 
    # When you run a program, run it only once.
    print('>>>>> SETUP <<<<<')

def loop():
    print('***** LOOP *****')
    kamibot.turn_led(255, 0, 0) 
    kamibot.delay(1) 
    kamibot.turn_led(0, 255, 0)
    kamibot.delay(1)
    kamibot.turn_led(0, 0, 255)
    kamibot.delay(1)

def end():
    # Run when the program exits  
    print('***** END *****')
    kamibot.close()

# ---------------------------------------
# To run helloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```


