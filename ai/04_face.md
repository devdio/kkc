# Face Detector

```python

from helloai import *

wnd = Window('wnd')
camera = Camera()

# Initialize face detector
detector = FaceDetector()

def loop():
    img = camera.read()

    # detect face 
    img, landmarks = detector.process(img, draw=True)
    print(landmarks)

    # Update Image 
    wnd.show(img)

# ---------------------------------------
# For HelloAI
# ---------------------------------------
if __name__ == '__main__':
    run()
```
