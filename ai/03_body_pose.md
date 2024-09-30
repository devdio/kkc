# Body Pose

<img src="https://camo.githubusercontent.com/d3afebfc801ee1a094c28604c7a0eb25f8b9c9925f75b0fff4c8c8b4871c0d28/68747470733a2f2f6d65646961706970652e6465762f696d616765732f6d6f62696c652f706f73655f747261636b696e675f66756c6c5f626f64795f6c616e646d61726b732e706e67" />

```python
from helloai import *

wnd = Window('wnd')
camera = Camera()

detector = PoseDetector()

def loop():
    img = camera.read()

    # detect Pose 
    img, landmarks = detector.process(img, draw=True)
    print(landmarks)

    # update image 
    wnd.show(img)

# ---------------------------------------
# for HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```

## Draw Landmark

```python
from helloai import *

wnd = Window('wnd')
camera = Camera()

detector = PoseDetector()

def loop():
    img = camera.read()
    img, landmarks = detector.process(img, draw=True)
    
    if(len(landmarks) > 30):
        # Right shoulder  
        x1, y1, z1 = landmarks[11]
        # Draw Circle
        img = img.ellipse((x1, y1), 10, 10, outline=(0, 255, 0), fill=(0, 255, 0), thickness=3)
        
        # Right wrist 
        x2, y2, z2 = landmarks[15]
        img = img.ellipse((x2, y2), 10, 10, outline=(0, 255, 0), fill=(0, 255, 0), thickness=3)
    
    # Update Image
    wnd.show(img)

# ---------------------------------------
# For HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```

