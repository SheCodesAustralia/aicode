---
title: "Functioning Game (?)"
weight: 6
chapter: false
---

So we have a cute turtle on the screen. Great. But it's not doing anything. Well that's because we haven't taught the game what to do with our turtle. First we need to register when the game is running, and when it ends. So let's create our first defined function of the day!
>**Step 1.** Game start screen

{{% notice style="warning" title="Delete this code" %}}
```python {title = "python"}
canvas.fill_style = "#426f9e"
canvas.fill_rect(0, 0, WIDTH, HEIGHT)
```
{{% /notice %}}

{{% notice style="tip" title="Add this code" %}}

```python {title = "python"}
def draw_start_screen():
    canvas.clear()
    canvas.fill_style = "#426f9e"
    canvas.fill_rect(0, 0, WIDTH, HEIGHT)

    canvas.fill_style = "white"
    canvas.font = "16px sans-serif"
    canvas.fill_text("CLICK START", 83, 128)

    canvas.font = "12px sans-serif"
    canvas.fill_text("Then click again if needed for arrows", 28, 160)

    canvas.draw_image(turtle_img, turtle_x, turtle_y, turtle_width, turtle_height)

draw_start_screen()
```
{{% /notice %}}
- `def()` is referred to as a *defined function*. It is a task that runs only when it's called/ asked to. If you create this game entirely without functions, it wouldn't run as needed. Things would either run once or continuously. Or maybe even break.
>**Step 2.** Create a start game function

We have our starting screen, now we need a function to initiate the start of the game.
```python {title = "python"}
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
```
- `if` statements are a form of conditional expression. Where certain requirements are needed in order for a specific segment of code to run.
- `asyncio` allows the game to run continuously alongside other functions. In this case, the game will continuously until the game is over.
- `global` allows a function to use outside variables. Without it, our `on_canvas_click()` function won't be able to use variables like `turtle_x` or `score`.

>**Step 3.** Create an end game function

When there's a Start There's an End. Let's create a game over screen.
```python {title = "python"}
# Game over
def draw_game_over():
    canvas.fill_style = "white"
    canvas.font = "20px sans-serif"
    canvas.fill_text("GAME OVER", 55, HEIGHT // 2 - 10)
    canvas.font = "12px sans-serif"
    canvas.fill_text("Click to play again", 78, HEIGHT // 2 + 20)
```
Have you tried running the code while developing? At this stage you'll notice that the game doesn't appear anymore, even with the `draw_start_screen()` function. That's because `display` calling the function isn't enough anymore. We could use `display` but then the game will be displayed two times instead of how we want it.
So let's try add the following to fix this.
```python {title = "python"}
game_ui = VBox([score_label, help_label, canvas])
display(game_ui)
draw_start_screen()
```
{{% notice style="info" title="Do you know the answer?" icon="lightbulb" %}}
Why do we include both `display(game_ui)` and `draw_start_screen` as opposed to just using `display(canvas)`?
{{% /notice %}}

>**Step 4.** Running the game

So... Now the game can start and end. But... Nothing is happening?
Well that's because we don't have any tasks for when `asyncio.create_task(game_loop())` runs. So let's add that!


```python {title = "python"}
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
```
We've now created tasks for the async function, which does the following:
- `while` is a loop statement that allows the game to continuously run while `game_running` is set to `True` which happens when you click start.
- `elif` sets alternative results depending on different scenarios from `if`. In this case, we are using it to end the game. And using the `break` function to end the loop. Therefore, ending the game.