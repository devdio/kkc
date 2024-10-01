# Save Image

```python
from helloai import *

img_dir = 'C:\\Users\\user\\Downloads\\allimsges'
wnd = Window('mask-nomask')
camera = Camera(1)

def loop():
    img = camera.read()
    wnd.show(img)
    
    print(mouse_pressed)
    if mouse_pressed:
        # click on the window
        img.save(img_dir)

if __name__ == '__main__':
    run()
```
