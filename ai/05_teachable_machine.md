# Teachable Machine
- [TeachableMachine Site](https://teachablemachine.withgoogle.com/)

```python 
from helloai import *

wnd = Window('wnd')
camera = Camera()

# for Image Project
detector = TMImageModel()
# read from path (keras model)
detector.load_model('C:\\Users\\user\\Downloads\\converted_keras')

def loop():
    img = camera.read()

    label = detector.process(img)
    img = img.text((5,5), text=label, size=40, color=(255, 0, 0))
    print('LABEL >>> ', label)
        
    wnd.show(img)

# ---------------------------------------
# for HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```


## Mask

```python 
from helloai import *
from pyKamipi.pibot import KamibotPi

kamibot = KamibotPi('COM3', 57600)

wnd = Window('main')
model = TMImageModel()

camera = Camera(num=0, crop=True, flip=1)

def setup():
    model.load_model('C:/workspace/model/mask')
    model.summary()

def loop():
    img = camera.read()
    lbl = model.process(img)
    print(lbl)

    wnd.show(img)

    if lbl == "Masked":
        kamibot.turn_led(0,0,255)
        kamibot.top_motor_abspos(0,7,2)
   
    elif lbl == "NoMasked":
        kamibot.turn_led(255, 0, 0)
        kamibot.top_motor_abspos(180,7,2)

if __name__ == '__main__':
    run()
```

