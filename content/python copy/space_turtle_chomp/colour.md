---
title: "Let There be Colour"
weight: 4
chapter: false
---

Colour is something that can easily change the tone and feel of your work. We can give our game some colour by assigning some to our canvas. There are lots to pick from including...
![Colour Names](../images/100_Color_names_python.png)


So we can add to our code the following...
```python {title = "python"}
canvas.fill_style = "blue" 
canvas.fill_rect(0, 0, WIDTH, HEIGHT)
```

The 100 colour names may be too limiting for some people. So alternatively, we can use something called hex codes to fully customise the colours. You can do this by visiting the [Google Colour Picker](https://share.google/AlzroUnU7TVllo0mj).

So our overly saturated pure blue can now be more subtle for our eyes.
```python {title = "python"}
canvas.fill_style = "#426f9e" # Replace "blue" with the hex code
```
{{% notice note %}}
You'll notice the full sentence after the "#" in the code above. That sentence doesn't get registered as code by the program. Instead it is looked as a note - like a editors message. This is beneficial for all developers, to help understand what is going on in their work. It also helps developer teams collaborate.
{{% /notice %}}