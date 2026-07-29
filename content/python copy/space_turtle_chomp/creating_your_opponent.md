---
title: "Creating your opponent"
weight: 11
chapter: false
---

In general games are more fun if you get to compete against an opponent, for Space Turtle Chomp this is very easy to do as we have already written all the code we just need to create an opponent section and cut and paste then modify our existing code.

>**Step 1.**  First we need to create a new turtle object as the opponent, move to the end of  \#Create player turtle section and add:

```python {title="python"}
# Create opponent turtle
comp = turtle.Turtle()
comp.color('red')
comp.shape('turtle')
comp.penup()
comp.setposition(random.randint(-290, 290), random.randint(-290, 290))
```

>**Step 2.**  Save your game as kbgame10 and run your module.

You now have a red opponent space turtle now, but you'll notice it doesn't move. Let’s make it move around the screen and add the boundary checking so it doesn’t run away.

>**Step 3.** To move your opponent turtle add the following code to the while True loop under player.forward\(speed\)

```python {title="python"}
    comp.forward(12)
```

>**Step 4.** Next copy the following text and paste it directly underneath. Note, the below example is in the format for Mac, if you are on Windows yours will look slightly different:

```python {title="python"}
    # Boundary Player Checking x coordinate
    if player.xcor() > 290 or player.xcor() < -290:
        player.right(180)
        os.system('afplay bounce.mp3&')

    # Boundary Player Checking y coordinate
    if player.ycor() > 290 or player.ycor() < -290:
        player.right(180)
        os.system("afplay bounce.mp3&")
```

>**Step 5.** Edit the pasted text to:

```python {title="python"}
    # Boundary Comp Checking x coordinate
    if comp.xcor() > 290 or comp.xcor() < -290:
        comp.right(180)
        os.system('afplay bounce.mp3&')

    # Boundary Comp Checking y coordinate
    if comp.ycor() > 290 or comp.ycor() < -290:
        comp.right(180)
        os.system('afplay bounce.mp3&')
```

{{% notice note %}}

You can make the comp.forward speed faster or slower by changing the number within the brackets.

{{% /notice %}}

>**Step 6.**  Save and run your module.

Now your opponent turtle is moving around the screen and bouncing of the walls, next we want to give them a score.

>**Step 7.**  Within the \# Create variable score section add:

```python {title="python"}
comp_score = 0
```

>**Step 8.** Now you create your competition score just under your \# Create opponent turtle section by adding:

```python {title="python"}
# Create competition score
mypen2 = turtle.Turtle()
mypen2.color('red')
mypen2.hideturtle()
```

>**Step 9.** Now copy the player collision checking section and paste direct below. Note: this example code is the version for Windows, if you are on a mac yours will look slightly different:

```python {title="python"}
    # Collision checking
    if isCollision(player, food):
        food.setposition(random.randint(-290, 290), random.randint(-290, 290))
        food.right(random.randint(0,360))
        winsound.PlaySound('chomp.wav', winsound.SND_ASYNC)
        score +=1
        mypen.penup()
        mypen.hideturtle()
        mypen.setposition(-290, 305)
        scorestring ="Score: %s" % score
        mypen.write(scorestring, False, align='left', font=('Arial', 14, 'normal'))
```

>**Step 10.**  Edit the pasted code, changing player to comp, score to comp_score, mypen to mypen2 and setting the position of the comp score. It should look something like the below:

```python {title="python"}
    # Comp Collision checking
    if isCollision(comp, food):
        food.setposition(random.randint(-290, 290), random.randint(-290, 290))
        food.right(random.randint(0,360))
        winsound.playSound('chomp.wav', winsound.SND_ASYNC)
        comp_score+=1
        # Draw the Comp score on the screen
        mypen2.undo()
        mypen2.penup()
        mypen2.hideturtle()
        mypen2.setposition(200, 305)
        scorestring ="Score: %s" % comp_score
        mypen2.write(scorestring, False, align='left', font=('Arial', 14, 'normal'))
```

>**Step 11.** Save and run your module.

Your code should look like this: 

{{< tabs groupid="a">}}
{{% tab title="_**Windows**_" %}}

Windows [kbgame10.py](/python/space_turtle_chomp/src/kbgame10_win.py)

{{% /tab %}}
{{% tab title="_**MacOS**_" %}}

Mac [kbgame10.py](/python/space_turtle_chomp/src/kbgame10.py)

{{% /tab %}}
{{< /tabs >}}

{{% notice style="tip" title="Time to celebrate" %}}

**Congratulations Module 10 Completed**

{{% /notice %}}