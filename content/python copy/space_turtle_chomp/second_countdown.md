---
title: "60 second, countdown!"
weight: 12
chapter: false
---

You have most of your Space Turtle Chomp game developed now, however at the moment it can go on forever, like most games what you can do is set a time limit for the game duration, again this is simple to do.

>**Step 1.**  Move to the top of your code and import the time function with the other imports:

```python {title="python"}
import time
```

>**Step 2.**  Move down to the just below the \# Set speed variable section and add:

```python {title="python"}
# Set game time limit for 1 minute (60 seconds)
timeout = time.time() + 10*6
```

{{% notice note %}}

**Note:** We set our game timeout to 6 lots of 10 second for a 1 minute game we could set it to 5 for 30 seconds or 5\*5 for 25 seconds.

{{% /notice %}}

>**Step 3.**  Move to the top of the while true section and add the following:

```python {title="python"}
    gametime = 0
    if gametime == 6 or time.time() > timeout:
        break
    gametime = gametime - 1
```

{{% notice note %}}

You set a variable called gametime and set it to 0, the if statement then runs the loop until gametime = 6.

{{% /notice %}}

>**Step 4.**  Save your game as kbgame11 and run your Module

You should now have 60 seconds to chomp more space cabbages than your computer opponent before the game ends. The last thing you can do for your game as part of this tutorial is have the game display who wins at the end of 60 seconds.

>**Step 5.**  Move to the very end of your code and add the following if statement and argument. This time the text is not indented until after the if statement:

```python {title="python"}
if (int(score) > int(comp_score)):
    mypen.setposition(0, 0)
    mypen.color("yellow")
    mypen.write("Game Over: You WIN", False, align="center", font=("Arial", 28, "normal"))
else:
    mypen.setposition(0, 0)
    mypen.color("yellow")
    mypen.write("Game Over: You LOSE", False, align="center", font=("Arial", 28, "normal"))
```

The if statement compares your score \(player\) against the opponent score \(comp\) and if your score is higher it prints the You Win message and if it is lower it prints the You Lose message.

If you run your code now, the game will quit before you can actually read the message. Let’s add a delay so we can see the message.

```python {title="python"}
delay = input("Press Enter to finish.")
```

Your code should look like this: 

{{< tabs groupid="a">}}
{{% tab title="_**Windows**_" %}}

Windows [kbgame11.py](/python/space_turtle_chomp/src/kbgame11_win.py)

{{% /tab %}}
{{% tab title="_**MacOS**_" %}}

Mac [kbgame11.py](/python/space_turtle_chomp/src/kbgame11.py)

{{% /tab %}}
{{< /tabs >}}

That is the end of today’s tutorial, if you got through all of it in 1 day well done that is an awesome effort but it doesn’t matter if you didn’t as the tutorial is online and you can still access it from home. Don't forget to join our [She Codes online community](https://join.slack.com/t/shecodesaus/shared_invite/zt-9jktxnlx-Rur3NGFSBFJ7LRwq7AV~ig) to keep in touch with your mentors and ask for help.

{{% notice style="info" title="Challenge!" icon="lightbulb" %}}

If you enjoyed this and wanted to continue practising, other things you might want to try is

* Making multiple opponents using the List \[\] function like you did for food
* Setting a start option at the beginning of the game
* Setting a play again option at the end
* Setting up a easy, medium and hard option for the game

{{% /notice %}}
