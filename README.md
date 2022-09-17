# Flet Cheatsheet - snippets to boost productivity

**Essential daily links**
|    |   |
| ------------- | ------------- |
| [Getting started guide](https://flet.dev/docs/guides/python/getting-started)  | [Controls Reference](https://flet.dev/docs/controls)  |
| [Flet Github Repo](https://github.com/flet-dev/flet) | [Flet issues](https://github.com/flet-dev/flet/issues) |
| [Flet Examples Repo](https://github.com/flet-dev/examples/tree/main/python) | [Youtube Flet Videos](https://www.youtube.com/results?search_query=flet+python) |


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
# name: Import kitchen sink

import flet
from flet import *
from flet import icons, dropdown, colors
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

**Memes**

![i-flet-therefore-i-can](https://user-images.githubusercontent.com/11970940/190875624-9cb08001-309a-4839-a3d7-ccf2716c0b53.png | width=400)

![what-good-shall-flet-today](https://user-images.githubusercontent.com/11970940/190875488-27a18f9b-19e3-4cc9-ba5c-5cdbeb7ad2c7.png)

![thats-the-power-of-flet](https://user-images.githubusercontent.com/11970940/190875493-50f3f94a-5642-4cd7-9f45-56525d24419d.jpeg)

![Hololeo Labs](https://user-images.githubusercontent.com/11970940/190875540-d45afb9a-9d09-44b0-93c4-8159b28ea6df.png)

