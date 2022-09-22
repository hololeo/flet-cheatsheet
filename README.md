# Flet Cheatsheet - snippets to boost productivity

If you find this cheatsheet useful, you can support it for free by clicking ⭐ Star repo.

**Essential daily links**
|    |   |
| ------------- | ------------- |
| [Getting started guide](https://flet.dev/docs/guides/python/getting-started)  | [Controls Reference](https://flet.dev/docs/controls)  |
| [Flet Github Repo](https://github.com/flet-dev/flet) | [Flet issues](https://github.com/flet-dev/flet/issues) |
| [Flet Examples Repo](https://github.com/flet-dev/examples/tree/main/python) | |

<a id="install"></a>
<a id="upgrade"></a>
**Install / Upgrade Flet via pip**
```
pip3 install flet

# upgrade

pip3 install flet --upgrade
```

<a id="hotreload"></a>
**Hot reload**
```
# watch all files in directory

flet main.py -d

# watch current and sub-directories

flet main.py -r
```

<a id="boilerplate"></a>
**Quick Boilerplate - Essential Imports**

```python
# Essential imports

import flet
from flet import Page, Column, Row, Container, Text, Stack, TextField, Image ElevatedButton 
from flet import icons, dropdown, colors, padding, alignment, border_radius, theme

def main(page: Page):
  page.title = "My Awesome Flet Appname"
  page.add (Text ("Hello Fletizen!"))
  page.update()

flet.app(target=main, assets_dir="assets")
# flet.app(target=main, view=flet.WEB_BROWSER)
```

**Deep work mode: Import \***

```python 
# 'bad practice' https://www.geeksforgeeks.org/why-import-star-in-python-is-a-bad-idea/

import flet
from flet import *
from flet import icons, dropdown, colors, padding, alignment, border_radius, theme
```
<a id="button"></a>
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

<a id="textfield"></a>
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

<a id="image"></a>
**Images**

```python
import flet
from flet import Page, Image, border_radius

# load local image inside assets folder
def main(page: Page):
    page.add (Image( src="photo.jpg"))
flet.app( target=main, assets_dir="assets")

# load remote image
img = Image(
    src=f"https://picsum.photos/200/200",
    width=200,
    height=200,
    fit="none", # none, contain, cover, fill, fitHeight, fitWidth, scaleDown
    repeat="noRepeat", # noRepeat, repeat, repeatX, repeatY
    border_radius=border_radius.all(10),
    tooltip= "text displayed on hover image"
)
page.add (img)

# cache buster
import time
img = Image(src=f"https://picsum.photos/200/200?ts={time.time()}")
page.add (img)

# display Base-64 encoded image
page.add(Image(src_base64 = "iVBORw..."))
```

<a id="logging"></a>
**Logging**

```python
import logging
logging.basicConfig(level=logging.DEBUG)
```

<a id="keyboard"></a>
**Keyboard**

```python
# https://flet.dev/docs/guides/python/keyboard-shortcuts
import flet
from flet import Page, KeyboardEvent

def main (page:Page):
    def on_keyboard (e: KeyboardEvent):
        keypressed = f"Key: {e.key}, Shift: {e.shift}, Control: {e.ctrl}, Alt: {e.alt}, Meta: {e.meta}"
        print (keypressed)

    page.on_keyboard_event = on_keyboard
    page.update()

flet.app (target=main)
```

<a id="page"></a>
**Page**

```python
# scroll page as items added
page.scroll = "auto"
page.auto_scroll  = True

# open url in browser
page.launch_url (url)

# go to route 
page.go (route)

# set clipboard
page.set_clipboard ("This paste comes from flet!")

# window resize handler
def page_on_resize(e):
    print (f"Resize {page.window_width},{page.window_height}")

page.on_resize = page_on_resize
```

<a id="layout"></a>
**Layout**

*padding*
```python
# left indent
padding = padding.only (left=43)
# top and left indent
padding=padding.only (left=8, right=8),
# no spacing between children
control.spacing = 0
```

*page vertical/horizontal*
```python
# start (left), end (right), center, spaceBetween, spaceAround, spaceEvenly
page.vertical_alignment = "center" 
page.horizontal_alignment = "center"  
```

*expand*
```python
# expand = True will expand item to fill available space in its parent layout control
col = Column ([Text ("Im at top", expand=True), Text ("Im at bottom")], expand=True)   
row = Row ([Text ("Im at left", expand=True), Text ("Im at right")], expand=True) 
```

*Absolute position*

[see: Absolute positioning inside Stack](https://flet.dev/docs/controls/stack#absolute-positioning-inside-stack)

**User Control**

[see: User control docs](https://flet.dev/docs/guides/python/user-controls)

<a id="usercontrol">

```python
import flet
from flet import Page, Text, UserControl

class HelloWorld (UserControl):
    
    def __init__(self, text='Hello Fletizen!'):
        super().__init__()
        self.text = Text(value=text)

    def build(self):
        return self.text

def main(page: Page):
    page.add (HelloWorld())
    page.update()

flet.app (target=main)        
```

<a id="winmethods"></a>
**App Window methods**

```python
# center window
page.window_center()

# close window
page.window_close()

# window_destroy()
page.window_destroy()

# window resize handler
def page_on_resize(e):
    print (f"Resize {page.window_width},{page.window_height}")

page.on_resize = page_on_resize

# window event listener
def win_on_event (e):
    print (f"win_event: {e.data}")
    page.add (Text (e.data))
    page.update()

page.on_window_event = win_on_event
page.scroll = "auto"
page.update()


```
<a id="winprops"></a>
**App Window Properties**

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

<a id="memes"></a>
**Memes**

<img src="https://user-images.githubusercontent.com/11970940/190875624-9cb08001-309a-4839-a3d7-ccf2716c0b53.png" width=400 align=left/>
<br><br>
<img src="https://user-images.githubusercontent.com/11970940/190875488-27a18f9b-19e3-4cc9-ba5c-5cdbeb7ad2c7.png" width=400 align=left/>
<br><br>
<img src="https://user-images.githubusercontent.com/11970940/190875493-50f3f94a-5642-4cd7-9f45-56525d24419d.jpeg" width=400 align=left/>
<br><br>
<img src= "https://user-images.githubusercontent.com/11970940/190927669-e4237735-422b-4afb-a184-6e8350a2bc77.png" width=300 align=left/>
<br><br>

<img src= "https://user-images.githubusercontent.com/11970940/190932508-3d1a4d6d-1948-4a10-9c69-26783a6590a4.png" width=400 align=left/>
<br><br>

<img src= "https://user-images.githubusercontent.com/11970940/191278415-2c6a67da-5fd7-4231-8eb6-0952fc12268c.png" width=400 align=left/>
<br><br>

<img src= "https://user-images.githubusercontent.com/11970940/191359269-4fba4ee1-5e79-473a-bb9d-1733d796af5e.png" width=400 align=left/>
<br><br>

<img src= "https://user-images.githubusercontent.com/11970940/191648035-3b9abb94-caf1-49da-a425-d92010afe478.png" width=400 align=left/>
<br><br>

<a id="sponsor"></a>
**Sponsors**

<img src="https://user-images.githubusercontent.com/11970940/190875540-d45afb9a-9d09-44b0-93c4-8159b28ea6df.png" width=300 align=left>
<br>


