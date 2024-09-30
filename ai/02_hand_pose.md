# Hand Pose

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
