---
title: "Move turtle move!"
weight: 7
chapter: false
---
```python {title = "python"}
# Keyboard inputs
def on_key_down(key, shift_key, ctrl_key, meta_key):
    global turtle_x

    if not game_running:
        return
    if key == "ArrowLeft" and turtle_x > 0:
        turtle_x -= 15
    elif key == "ArrowRight" and turtle_x < WIDTH - turtle_width:
        turtle_x += 15
canvas.on_key_down(on_key_down)
```
{{% notice style="note" title="NOTE" icon="vial" %}}
This preview is an example of how your code should look like at the end. To check or compare, take a look at the following Python code.

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
score_label = Label(value= "Score: 0")
help_label = Label(value= "Click game to start, then use ← → to move")

    # Running the game graphics -> Step 1.3
def draw_start_screen():
    canvas.clear()
    canvas.fill_style = "#426f9e"
    canvas.fill_rect(0, 0, WIDTH, HEIGHT)

    canvas.fill_style = "white"
    canvas.font = "16px sans-serif"
    canvas.fill_text("CLICK START", 83, 128)

    canvas.font = "12px sans-serif"
    canvas.fill_text("Then click again if needed for arrows", 28, 160)

    # Adding images to the canvas  -> Step 2.2
    canvas.draw_image(turtle_img, turtle_x, turtle_y, turtle_width, turtle_height)



# Adding your turtle and seaweed -> Step 2.1
turtle_height, turtle_width = 30, 30
seaweed_size = 15

    # Sprite settings - location/ placement
turtle_x = WIDTH // 2 -  turtle_height // 2
turtle_y = HEIGHT - 25
seaweed_x = random.randint(0, WIDTH - seaweed_size)
seaweed_y = 0
seaweed_speed = 5

    # Loading images
with open("images/turtle.png", "rb") as f:
    turtle_img = Image(value = f.read(), format = "png", width = turtle_width, height = turtle_height)
with open("images/seaweed.png", "rb") as f:
    seaweed_img = Image(value = f.read(), format = "png", width = seaweed_size)

# Game start
def on_canvas_click(x, y):
    global game_running, game_over
    global turtle_x, seaweed_x, seaweed_y, score

    if game_running:
        return

    turtle_x = WIDTH // 2 -  turtle_height // 2
    seaweed_x = random.randint(0, WIDTH - seaweed_size)
    seaweed_y = 0
        
    score = 0
    score_label = Label(value= "Score: 0")

    game_running = True
    game_over = False
    asyncio.create_task(game_loop())
    
canvas.on_mouse_down(on_canvas_click)

# Game over
def draw_game_over():
    canvas.fill_style = "white"
    canvas.font = "20px sans-serif"
    canvas.fill_text("GAME OVER", 55, HEIGHT // 2 - 10)
    canvas.font = "12px sans-serif"
    canvas.fill_text("Click to play again", 78, HEIGHT // 2 + 20)

# Keyboard inputs
def on_key_down(key, shift_key, ctrl_key, meta_key):
    global turtle_x

    if not game_running:
        return
    if key == "ArrowLeft" and turtle_x > 0:
        turtle_x -= 15
    elif key == "ArrowRight" and turtle_x < WIDTH - turtle_width:
        turtle_x += 15
canvas.on_key_down(on_key_down)

# Game loop
async def game_loop():
    global seaweed_x, seaweed_y, score, game_running
    while game_running:
        with hold_canvas(canvas):
            canvas.clear()
            canvas.fill_style = "#426f9e"
            canvas.fill_rect(0, 0, WIDTH, HEIGHT)

            canvas.draw_image(turtle_img, turtle_x, turtle_y, turtle_width, turtle_height)
            canvas.draw_image(seaweed_img, seaweed_x, seaweed_y, seaweed_size, seaweed_size)

            seaweed_y += seaweed_speed
        
            # Updating the score
            if seaweed_y >= turtle_y and (seaweed_x <= turtle_x + turtle_width):
                score += 1
                score_label.value = f"Score: {score}"
                # Reset seaweed for next point(s)
                seaweed_y = 0
                seaweed_x = random.randint(0, WIDTH - seaweed_size)
            # Ending the game
            elif seaweed_y > HEIGHT:
                game_running = False
                game_over = True
                draw_game_over()
                break

            await asyncio.sleep(0.05)

# Launching the game
game_ui = VBox([score_label, help_label, canvas])
display(game_ui)
draw_start_screen()
```

</details>
{{% /notice %}}