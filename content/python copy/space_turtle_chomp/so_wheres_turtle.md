---
title: "So Where's our Turtle?"
weight: 5
chapter: false
---

So now we have our canvas. Now what? A blank coloured in square isn't anything much. Where's our turtle?
Well we got to add the turtle to the game. You'll notice that in your workspace there's an `images` folder. When you click on it there's pictures of the turtle and the seaweed that it'll chomp on. We'll be using these images for our game.

>**Step 1** Adding Images

To use any external files apart from the games source code, we need to allow the the program to detect and read the files. We do this using a `with open()` command.
```python {title = "python"}
turtle_height, turtle_width = 30, 30
turtle_x = WIDTH // 2 -  turtle_height // 2
turtle_y = HEIGHT - 25
seaweed_size = 15

with open("images/turtle.png", "rb") as f:
    turtle_img = Image(value = f.read(), format = "png", width = turtle_width, height = turtle_height)
with open("images/seaweed.png", "rb") as f:
    seaweed_img = Image(value = f.read(), format = "png", width = seaweed_size)
```
The code above identifies what the file should be treated as. Including the formatting, and how it's read. If the value `rb` (read-binary mode) was `r` instead, Python would treat the image file as a text file - which is obviously wrong.

> **Step 2.** Displaying the Image

Adding the image to the code doesn't actually make it automatically appear. We have to actually "draw it on."
```python {title = "python"}
canvas.draw_image(turtle_img, turtle_x, turtle_y, turtle_width, turtle_height)
```

{{% notice style="note" title="NOTE" icon="vial" %}}
This preview is an example of how your code should look like at this stage. To check or compare, take a look at the following Python code.

<details>
<summary><b>Python Code</b> <-- click to reveal</summary>

```python {title = "python"}
# Creating the game layout
    # Default game settings -> Step 1.1
WIDTH = 260
HEIGHT = 260
game_running = False
game_over = False
    # Game screen presets -> Step 1.2
canvas = Canvas(width = WIDTH, height = HEIGHT)
canvas.layout.width = "260px"
canvas.layout.height = "260px"
canvas.fill_style = "#426f9e"
canvas.fill_rect(0, 0, WIDTH, HEIGHT)
score_label = Label(value= "Score: 0")
help_label = Label(value= "Click game to start, then use ← → to move")

    # Adding your turtle and seaweed -> Step 2.1
turtle_height, turtle_width = 30, 30
turtle_x = WIDTH // 2 -  turtle_height // 2
turtle_y = HEIGHT - 25
seaweed_size = 15
    # Loading images -> Step 2.2
with open("images/turtle.png", "rb") as f:
    turtle_img = Image(value = f.read(), format = "png", width = turtle_width, height = turtle_height)
with open("images/seaweed.png", "rb") as f:
    seaweed_img = Image(value = f.read(), format = "png", width = seaweed_size)
canvas.draw_image(turtle_img, turtle_x, turtle_y, turtle_width, turtle_height)
display(canvas)
```

</details>
{{% /notice %}}