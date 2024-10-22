+++
title = 'Exercise 4.3'
date = 2024-10-22
draft = false
math = true
+++
Wrtie a function which draws a polygon of given sides and size, then dividite in slices
```
import turtle
import math
def ngon(radius, sides):
    for x in range(int(sides)):
        # drawing outside polygon
        turtle.forward(radius)
        turtle.left(360 / sides)

        # function stops at every point in order to draw the slices
        turtle.left((((sides - 2)*180) / sides) / 2)
        turtle.forward((radius/2) / math.sin(math.radians((360/sides / 2))))    # angle is calculated using trig functions 
        turtle.backward((radius/2) / math.sin(math.radians((360/sides /2) ))) 
        turtle.right((((sides - 2)*180) / sides) / 2)
    
ngon(60, 13) # polygon of side = 60 with 13 sides
turtle.mainloop()

```