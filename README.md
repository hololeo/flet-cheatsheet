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
```

**Import \***

```python
# name: Import kitchen sink

import flet
from flet import *
from flet import icons, dropdown, colors
```



