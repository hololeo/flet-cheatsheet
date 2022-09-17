# flet-cheatsheet
Flet code snippets to boost productivity

Flet boilerplate 1

```python
# name: Flet Boilerplate 1

import flet
from flet import Page, Text, Column, Row, Container, alignment, colors

def main(page: Page):
  page.add (Text ("Hello Fletizen!"))
  page.update()

flet.app(target=main, assets_dir="assets")
```
