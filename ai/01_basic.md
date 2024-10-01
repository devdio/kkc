# HelloAI

## Display Window

```python
from helloai import *

win = Window('helloAI')
win.show()


if __name__ == '__main__':
    run()
```

## Draw Line with random color
```python
from helloai import *

win = Window('helloAI')

# Infinite loop
def loop():
    # start point
    x1 = random(win.width)
    y1 = random(win.height)
    
    # end point
    x2 = random(win.width)
    y2 = random(win.height)

    # random color
    color = (random(246), random(246), random(246))
    win.line((x1, y1), (x2, y2), color, 1)
    win.show()

#--------------------------------------------------
# for helloai
#--------------------------------------------------
if __name__ == '__main__':
    run()
```

## Draw Circle

```python
from helloai import *

win = Window('helloAI')

def loop():
    center = (win.width/2, win.height/2)
    #-------------------------------------------------------------------
    # ellipse(center, width, height, border color, color, border width)
    #-------------------------------------------------------------------
    win.ellipse(center, 100, 100)
    win.show()

if __name__ == '__main__':
    run()
```

## Circle Animation

```python
from helloai import *

win = Window('helloAI')

def loop():
    x = random(win.width)
    y = random(win.height)
    color = (random(256), random(256), random(256))
    win.ellipse((x, y), 100, 100, fill=color)
    win.show()

if __name__ == '__main__':
    run()
```

## Draw a rectangle  
  
```python
from helloai import *

win = Window('helloAI')

def setup():
    win.background((0,0,0))

def loop():
    size = 100
    x0 = random(win.width)
    y0 = random(win.height)
    x1 = x0 + size
    y1 = y0 + size
    color = (random(256), random(256), random(256))
    #----------------------------------------------------------------------
    # rectangle(starter, end, border color, color, fillcolor)
    #----------------------------------------------------------------------
    win.rectangle((x0, y0), (x1, y1), fill=color)
    win.show()

if __name__ == '__main__':
    run()
```

## Text
```python
from helloai import *

win = Window('helloAI')

def loop():
    #-------------------------------------------------
    # text(starter, text, font-size, color)
    #-------------------------------------------------
    win.text((0, 0), 'Hello', 100, Color.AZURE)
    win.show()


if __name__ == '__main__':
    run()
```

## Count-Down
```python
from helloai import *

win = Window('helloAI')
num = 9

def loop():
    global num

    win.background(Color.BACKGROUND)
    win.text((win.width/2 - 50, win.height/2 - 50), str(num), 100, Color.AZURE)
    win.show()
    delay(1000)

    num -= 1
    if num < 0:
        num = 9


if __name__ == '__main__':
    run()
```

## Program Flows 
  
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


