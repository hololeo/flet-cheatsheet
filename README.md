# flet-cheatsheet
Flet code snippets to boost productivity

Flet boilerplate  - Essential Imports

```python
# name: Flet Boilerplate 1

import flet
from flet import Page, Text, Column, Row, alignment, colors
from flet import ElevatedButton, Container, Image

def main(page: Page):
  page.title = "My Awesome Flet Appname"
  page.add (Text ("Hello Fletizen!"))
  page.update()

flet.app(target=main, assets_dir="assets")
```
