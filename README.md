# Flet Cheatsheet - snippets to boost productivity

**Essential daily links**
|    |   |
| ------------- | ------------- |
| [Getting started guide](https://flet.dev/docs/guides/python/getting-started)  | [Controls Reference](https://flet.dev/docs/controls)  |
| [Flet Github Repo](https://github.com/flet-dev/flet) | [Flet issues](https://github.com/flet-dev/flet/issues) |
| [Flet Examples Repo](https://github.com/flet-dev/examples/tree/main/python) | |


**Install Flet via pip**
```
pip3 install flet

# upgrade

pip3 install flet --upgrade
```

**Hot reload**
```
# watch all files in directory

flet main.py -d

# watch current and sub-directories

flet main.py -r
```


**Flet boilerplate Startup - Essential Imports**

```python
# name: Flet Boilerplate startup

import flet
from flet import Page, Text, Column, Row, alignment, colors
from flet import ElevatedButton, Container, Image

def main(page: Page):
  page.title = "My Awesome Flet Appname"
  page.add (Text ("Hello Fletizen!"))
  page.update()

flet.app(target=main, assets_dir="assets")
# flet.app(target=main, view=flet.WEB_BROWSER)
```

**Import \***

```python
# name: Import kitchen sink, 'bad practice'

import flet
from flet import *
from flet import icons, dropdown, colors
```

**Buttons**

```python
import flet
from flet import Page, ElevatedButton

def main (page:Page):
    def on_click_btn (e):
        print ("i was clicked!")
    def on_hover_btn (e):
        print ("why you hovering on me!")
    def on_longpress_btn (e):
        print ("you pressed me so long!")                

    btn = ElevatedButton (
        text="Click Me", 
        on_click = on_click_btn,
        on_hover = on_hover_btn,
        on_long_press = on_longpress_btn 
    )
    page.add (btn)
flet.app (target=main)
```


**Multiline Textfield**

```python
textfield = TextField (
    value = "Look at me!\n\nI am a multiline Textfield!",
    min_lines = 3,
    max_lines = 3,
    multiline = True,
    border_width= 2,
    color = "white",
    text_size = 15     
)
page.add (textfield)
```
![multiline-textfield](https://user-images.githubusercontent.com/11970940/190867558-2fdfef39-0bd8-4354-a116-42e85eb9691e.png)


**Logging**

```python
import logging
logging.basicConfig(level=logging.DEBUG)
```

**Keyboard**

```python
# https://flet.dev/docs/guides/python/keyboard-shortcuts
from flet import Page, KeyboardEvent

def on_keyboard (e: KeyboardEvent):
    keypressed = f"Key: {e.key}, Shift: {e.shift}, Control: {e.ctrl}, Alt: {e.alt}, Meta: {e.meta}"
    print (keypressed)
)    
page.on_keyboard_event = on_keyboard
```


**App Window**

```python
# title
page.window_title = "Flet Rocks!" # set app window title (desktop and web)

# window position on desktop
page.window_top = 0
page.window_left = 0

# window size
page.window_width = 500 
page.window_height = 500   

# locking in place and always on top
page.window_always_on_top = True 
page.window_movable = True 

# window min and max resize  
page.window_resizable = True # False prevents resizing
page.window_min_width = 200  # resizing window limit
page.window_min_height = 200     
page.window_max_width = 500  # resizing window max
page.window_max_height = 500

# minimize or maximize window  
page.window_minimized = False # True = minimizes, False = restores
page.window_maximized = True # False = unmaximize

# customize window chrome
page.window_frameless = True
page.window_opacity = 0.5 # 0.0 (fully transparent) 1.0 (fully opaque)
page.window_title_bar_hidden = True # see also WindowDragArea
page.window_title_bar_buttons_hidden = True # macOS only 
page.window_minimizable = True # show or hide minimize button

# showing / hiding window
page.window_visible = True # True = show app window. False = hide
flet.app(target=main, view=flet.FLET_APP_HIDDEN) # start app hidden

# misc
page.window_full_screen = True # switch to fullscreen mode
page.window_focused = True
page.window_title_bar_hidden = True
page.window_skip_task_bar = True # hide app from the Task Bar / Dock
page.window_progress_bar = 0.5 # show half a proress bar on Task Bar / Dock
page.window_prevent_close = True # intercept native close signal 
```

**Memes**

<img src="https://user-images.githubusercontent.com/11970940/190875624-9cb08001-309a-4839-a3d7-ccf2716c0b53.png" width=400 align=left/>
<br><br>
<img src="https://user-images.githubusercontent.com/11970940/190875488-27a18f9b-19e3-4cc9-ba5c-5cdbeb7ad2c7.png" width=400 align=left/>
<br><br>
<img src="https://user-images.githubusercontent.com/11970940/190875493-50f3f94a-5642-4cd7-9f45-56525d24419d.jpeg" width=400 align=left/>
<br><br>


**Sponsors**

<img src="https://user-images.githubusercontent.com/11970940/190875540-d45afb9a-9d09-44b0-93c4-8159b28ea6df.png" width=300 align=left>
<br>

