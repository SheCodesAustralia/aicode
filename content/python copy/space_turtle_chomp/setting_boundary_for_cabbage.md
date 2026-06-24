---
title: "Setting the boundaries for cabbage"
weight: 7
chapter: false
---

So what you will do next is make the food move around the screen, this is fairly easy to do by using the same forward option we used for your player.

>**Step 1.**  Within the While Loop add the following code after the #Boundary Checking Player y coordinate code:

```python {title="python"}
    # Boundary Player Checking y coordinate
    if player.ycor() > 290 or player.ycor() < -290:
        player.right(180)

    # Move food around
    food.forward(1)
```

>**Step 2.**  Save your game as kbgame6 and run the module.

>**Step 3.**  Now your cabbage moves across the screen but at the moment it always moves to the right, so let make the game more interesting by using the random function again by adding the following to the end of the # Collision checking section:

```python {title="python"}
    food.right(random.randint(0, 360))
```

>**Step 4.**  The food is moving rather slow so let’s speed it up by changing the forward speed to 3 by updating food.forward with:

```python {title="python"}
# Move food around
    food.forward(3)
```

>**Step 5.**  Save and run your module, have a play with different speeds. Your food is now moving around the screen in a random direction. The only problem we have is that it can move off the screen. This is an easy fix as you can cut and paste the same code you wrote for your turtle for border checking and modify it for the food.

>**Step 6.**  Cut the following code and paste it directly underneath making sure the indents are aligned

```python {title="python"}
    # Boundary Player Checking x coordinate
    if player.xcor() > 290 or player.xcor() < -290::
        player.right(180)

    # Boundary Player Checking y coordinate
    if player.ycor() > 290 or player.ycor() < -290:
        player.right(180)  
```

>**Step 7.** Edit the pasted code to change player to food:

```python {title="python"}
    # Boundary Food Checking x coordinate
    if food.xcor() > 290 or food.xcor() < -290:
        food.right(180)

    # Boundary Food Checking y coordinate
    if food.ycor() > 290 or food.ycor() < -290:
        food.right(180) 
```

Now when your space cabbage hits the boundary it will bounce of the wall at 180&deg; just like your turtle

>**Step 7.**  Save and run your module.

Before moving on have a play at modify your code changing the bounce angle and speed of the space cabbage.

Your code should now look like this:

```python {title="python"}
#Turtle Graphics Game
import turtle
import math
import random

#Set up screen
turtle.setup(650,650)
wn = turtle.Screen()
wn.bgcolor("Navy")

#Draw border
mypen = turtle.Turtle()
mypen.color("white")
mypen.penup()
mypen.setposition(-300,-300)
mypen.pendown()
mypen.pensize(3)
for side in range(4):
    mypen.forward(600)
    mypen.left(90)
mypen.hideturtle()

#Create player turtle
player = turtle.Turtle()
player.color("darkorange")
player.shape("turtle")
player.penup()
player.speed(0)

#create food
food = turtle.Turtle()
food.color("lightgreen")
food.shape("circle")
food.penup()
food.speed(0)
food.setposition(random.randint(-290, 290), random.randint(-290, 290))

#Set speed variable
speed = 1

#Define  functions

def turn_left():
    player.left(30)

def turn_right():
    player.right(30)

def increase_speed():
    global speed
    speed += 1

def isCollision(t1, t2):
       d = math.sqrt(math.pow(t1.xcor()-t2.xcor(),2) + math.pow(t1.ycor()-t2.ycor(),2))
       if d < 20:
           return True
       else:
           return False

#Set keyboard bindings
turtle.listen()
turtle.onkey(turn_left, "Left")
turtle.onkey(turn_right, "Right")
turtle.onkey(increase_speed, "Up")


while True:
    player.forward(speed)

    #Boundary Checking x coordinate
    if player.xcor() > 290 or player.xcor() <-290:
        player.right(180)
    #Boundary Checking y coordinate
    if player.ycor() > 290 or player.ycor() <-290:
        player.right(180)

    #Boundary Food Checking x coordinate
    if food.xcor() > 290 or food.xcor() <-290:
        food.right(180)

    #Boundary Food Checking y coordinate
    if food.ycor() > 290 or food.ycor() <-290:
        food.right(180)

    #Move goal around
    food.forward(3)

    #Collision checking
    if isCollision(player, food):
        food.setposition(random.randint(-290, 290), random.randint(-290, 290))
        food.right(random.randint(0, 360))

```

{{% notice style="tip" title="Time to celebrate" %}}

**Congratulations Module 6 Completed**

{{% /notice %}}