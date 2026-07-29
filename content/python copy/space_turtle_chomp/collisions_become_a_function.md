---
title: "Collisions become a function"
weight: 6
chapter: false
---

You have collision checking working but as we add more cabbages it makes the code easier if you convert your existing collision code to a function.

>**Step 1.**  To create as a function we will use the `isCollision` to return a True or False return, to do that type the following at the end of the `#Define functions` section:

```python {title="python"}
def isCollision(t1, t2):
       d = math.sqrt(math.pow(t1.xcor()-t2.xcor(),2) + math.pow(t1.ycor()-t2.ycor(),2))
       if d < 20:
           return True
       else:
           return False
```

So your function uses `t1` and `t2` as generic terms instead of turtle and food and uses the same collision formula as before with an if statement that returns a True value if they are in the same location \(collide\) and a False value when they don’t.

>**Step 2.**  Now you need to update the code within the while True loop \# Collision checking section to look like:

```python {title="python"}
# Collision checking
if isCollision(player, food):
    food.setposition(random.randint(-290, 290), random.randint(-290, 290))
```

>**Step 3.** Save your game as kbgame5 and run your module.

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

    #Collision checking

    if isCollision(player, food):
        food.setposition(random.randint(-290, 290), random.randint(-290, 290))

```

{{% notice style="tip" title="Time to celebrate" %}}

**Congratulations Module 5 Completed**

{{% /notice %}}