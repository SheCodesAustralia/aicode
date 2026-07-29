---
title: "Creating space & sounds"
weight: 9
chapter: false
---

So you now have your space turtle running around the screen chasing and chomping moving space cabbages. Now you want to add a nice background and sounds to your game

>**Step 1.**  The first we want to do is download the background image and sound files into the folder where your kbgame files are stored. You can do this by selecting the image file here: 

[kbgame-bg.gif](/python/space_turtle_chomp/src/kbgame-bg.gif)

{{< tabs groupid="a">}}
{{% tab title="_**Windows**_" %}}

**Step 2.** For Windows users download the following .wav files:

* [bounce.wav](/python/space_turtle_chomp/src/bounce.wav)
* [chomp.wav](/python/space_turtle_chomp/src/chomp.wav)
{{% /tab %}}

{{% tab title="_**MacOS**_" %}}
**Step 2.** For Apple Mac users download the following .mp3 files:

* [bounce.mp3](/python/space_turtle_chomp/src/bounce.mp3)
* [chomp.mp3](/python/space_turtle_chomp/src/chomp.mp3)

{{% /tab %}}
{{< /tabs >}}

>**Step 3.**  You load the background image by adding the wn.bgpic to the \#Set up screen section after wnbgcolor\('navy'\) :

```python {title="python"}
wn.bgpic('kbgame-bg.gif')
```

>**Step 4.**  The space cabbages currently are the same size as your turtle lets makes them smaller and add a few more. 
 
You can add more by tweaking the `maxFoods` variable that you defined earlier: 

```python {title="python"}
# Create food
maxFoods = 10
```

and then to change the size we set their `shapesize` in the for loop that creates them:

```python {title="python"}
for count in range(maxFoods):
    new_food = turtle.Turtle()
    new_food.shapesize(.5)
```

>**Step 5.**  Save your game as kbgame8 and run your module.

{{% notice note %}}

If you want to use your own background image you simply need to create an image in your favourite image editor and save it as a 600 by 600 .gif file.

{{% /notice %}}

Now we need to add the sound this again is fairly simple but we use a different function depending on whether you are using a Windows or Apple Mac operating system.

{{< tabs groupid="a">}}
{{% tab title="_**Windows**_" %}}

**Step 6.**  For Windows you need to inform the Python program to use the audio features of
 your Windows computer you do this by importing the winsound commands by typing
 the following at the top of your application with the other import's::

```python {title="python"}
import winsound
```

**Step 7.**  Now in the \#boundary checking section we type the following
 winsound.PlaySound... code at the end of each boundary and collision
 checking section

```python {title="python"}
    # Boundary Player Checking x coordinate
    if player.xcor() > 290 or player.xcor() < -290:
        player.right(180)
        winsound.PlaySound('bounce.wav', winsound.SND_ASYNC)

    # Boundary Player Checking y coordinate
    if player.ycor() > 290 or player.ycor() < -290:
        player.right(180)
        winsound.PlaySound('bounce.wav', winsound.SND_ASYNC)

    # Move Food around
    for count in range(maxFoods):
        food.forward(3)

        #  Boundary Food Checking x coordinate
        if food.xcor() > 290 or food.xcor() < -290:
           food.right(180)
           winsound.PlaySound('bounce.wav', winsound.SND_ASYNC)

        # Boundary Food Checking y coordinate
        if food.ycor() > 290 or food.ycor() < -290:
           food.right(180)
           winsound.PlaySound('bounce.wav', winsound.SND_ASYNC)

        # Collision checking
        if isCollision(player, food):
           food.setposition(random.randint(-290, 290), random.randint(-290, 290))
           food.right(random.randint(0,360))
           winsound.PlaySound('chomp.wav', winsound.SND_ASYNC)
```

{{% notice note %}}

We are playing the bounce sound when either your turtle or the cabbages bounce of the boundary and the chomp sound when you collide with a cabbage.

{{% /notice %}}
 
The SND\_ASYNC tells the computer to play the sound in the background so the game doesn’t stop until the sound finishes, the technical term for this is Asynchronous.

{{% /tab %}}
{{% tab title="_**MacOS**_" %}}

**Step 6.**  For Apple Mac you need to inform the Python program to use the audio features of your Apple Mac you do this by importing the OS \(operating system\) commands by typing the following at the top of your application with the other import's:

```python {title="python"}
import os
```

**Step 7.**  Now in the \#boundary checking section we type the following os.system...
 code at the end of each boundary and collision checking section:

```python {title="python"}
    # Boundary Player Checking x coordinate
    if player.xcor() > 290 or player.xcor() < -290:
        player.right(180)
        os.system('afplay bounce.mp3&')

    # Boundary Player Checking y coordinate
    if player.ycor() > 290 or player.ycor()  <-290:
        player.right(180)
        os.system('afplay bounce.mp3&')

    # Move Food around
    for food in foods:
        food.forward(3)

        # Boundary Food Checking x coordinate
        if food.xcor() > 290 or food.xcor() < -290:
           food.right(180)
           os.system('afplay bounce.mp3&')

        # Boundary Food Checking y coordinate
        if food.ycor() > 290 or food.ycor() < -290:
           food.right(180)
           os.system('afplay bounce.mp3&')

        # Collision checking
        if isCollision(player, food):
           food.setposition(random.randint(-290, 290), random.randint(-290, 290))
           food.right(random.randint(0,360))
           os.system('afplay chomp.mp3&')
```

{{% notice note %}}

We are playing the bounce sound when either your turtle or the cabbages bounce of the boundary and the chomp sound when you collide with a cabbage.

{{% /notice %}}

The little ‘&’ after .mp3 tells the computer to play the sound in the background so the game doesn’t stop until the sound finishes, the technical term for this is Asynchronous.

{{% /tab %}}
{{< /tabs >}}

>**Step 8.**  Save and run your module

>**Step 9.**  Now you can change the background to black to make the game look better by editing the wn.bgcolor.. to:

```python {title="python"}
wn.bgcolor('black')
```

>**Step 10.**  Save and Run your model.

Your code should look like this: 

{{< tabs groupid="a">}}
{{% tab title="_**Windows**_" %}}

Windows [kbgame8.py](/python/space_turtle_chomp/src/kbgame8_win.py)

{{% /tab %}}
{{% tab title="_**MacOS**_" %}}

Mac [kbgame8.py](/python/space_turtle_chomp/src/kbgame8.py)

{{% /tab %}}
{{< /tabs >}}

{{% notice style="tip" title="Time to celebrate" %}}

**Congratulations Module 8 Completed**

{{% /notice %}}