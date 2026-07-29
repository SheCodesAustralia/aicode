---
title: "Creating our Canvas"
weight: 3
chapter: false
---

Before we can even begin to let our turtle roam free, we need to give it a space to swim around. To do this, we will write down the code to create the user interface of our game. This requires the understanding of how variables work, along with how computers interpret code to turn it into something we can see.

>**Step 1.** Creating game variables
In order to create the canvas, we need to set its dimensions. Through the canvas library, Python reads the numbers we provide as pixels in order to determine how large our canvas will be.
```python {title = "python"}
WIDTH = 260
HEIGHT = 260
game_running = False
game_over = False
```
For now we'll keep the size something reasonable so it doesn't take up the entire space. However you are free to change things up if you wish.
You can click the "▶︎" on the top the tool bar to run the code. However, you'll notice that nothing has happened yet. Don't worry, we're getting there!

>**Step 2.** Drawing our canvas
Now we'll finally start putting those libraries and variables to use.
```python {title = "python"}
canvas = Canvas(width = WIDTH, height = HEIGHT)
canvas.layout.width = "260px"
canvas.layout.height = "260px"
score_label = Label(value= "Score: 0")
help_label = Label(value= "Click game to start, then use ← → to move")
```
The code above sets the actual canvas itself. However, in order for it to show, we need to actually display it using another line of code.
```python {title = "python"}
display(canvas)
```
Once you run that, you'll notice how a large empty cell appeared. That's because we haven't set the colour of our canvas yet. So let's add a splash of colour in the next part of the workshop.
