# Hand Pose
  
<img src="https://camo.githubusercontent.com/cc87e384b553a0f19dcf8a36341b37a7081edc0b21b0d0ac364200b9e3bb98a1/68747470733a2f2f6d65646961706970652e6465762f696d616765732f6d6f62696c652f68616e645f6c616e646d61726b732e706e67" />

## Detect Hand and get information  
  
```python
from helloai import *

wnd = Window('wnd')

# Using Camera
camera = Camera()

# Create and initialize Object 
detector = HandsDetector()

# Infinite Loop
def loop():
    # Get From Camera
    img = camera.read()

    # Recognize hand
    img, landmarks = detector.process(img, draw=True)

    # Display information about recognized hand
    print(landmarks)
    
    # Display images read from the camera 
    wnd.show(img)

# ---------------------------------------
# For HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```

```
For exit the program:
1. click on the screen 
2. type `q` key 
```

## Measure the distance between your thumb and index finger 

```python
from helloai import *

wnd = Window('wnd')
camera = Camera()

detector = HandsDetector()

def loop():
    img = camera.read()
    img, landmarks = detector.process(img, draw=True)
   
    if len(landmarks) > 0:
        length, img, _ = detector.distance(landmarks[4], landmarks[8], img, draw=True)
        print(length)

    wnd.show(img)

# ---------------------------------------
# For HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```

- excercise) Adjusting Robot Speed Proportional to Distance
