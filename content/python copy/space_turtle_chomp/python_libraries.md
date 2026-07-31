---
title: "Python Libraries"
weight: 2
chapter: false
---

We'll officially start creating our turtle chomping game!
>**Step 1.** Open the file named "turtle_chomp.ipynb"

You'll notice that the file isn't a `.py` file which is used for Python files. Instead it is an `.ipynb` file, which is referred to as a computational notebook document (AKA IPython Notebook). Allowing people to code without necessarily installing Python on their devices.

Due to the workshop being conducted on a web-based interface, there comes limitations to what can be done with Python. For full use of Python, refer to our regular [One-Day Workshop content](https://tutorials.shecodes.com.au/).

>**Step 2.** Check your Python libraries

You'll notice how there's some pre-loaded code on the file. These lines of code are referred to libraries. The purpose of these libraries is to provide us with reusable code developed by others, so that we don't have to create everything from scratch.
To be able to reuse these libraries, they have to be imported through a series of code.
```python {title = "python"}
%pip install -q ipycanvas
import asyncio
import random
import math
from ipycanvas import Canvas, hold_canvas
from ipywidgets import VBox, Label, Image
```
The libraries above provide us with resources to help create the digital interface for our game. For this workshop, we will be using the libraries `Canvas`, `asyncio`, `random`, and `math`.

{{% notice style="info" %}}
To check out what other libraries Python has to offer, check out this link [Python Library](https://docs.python.org/3/library/index.html)!
{{% /notice %}}