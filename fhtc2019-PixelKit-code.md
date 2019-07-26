# PixelKit Library Code

## Make rectangle move 1

```
import PixelKit as kit
import time
red = [10, 0, 0]
green = [0,10,0]

kit.clear()

kit.set_background(green)

def rectangle(x, y, width, height, color):
  for i in range(0, width):
    for j in range(0,height):
      kit.set_pixel(x+i, y+j, color)

for bounce in range(0,5):
  for num in range(0,12):
    kit.set_background(green)

    rectangle(num,3,5,3,red)
    kit.render()
    time.sleep(.05)

  for numb in reversed(range(0,12)):
    kit.set_background(green)

    rectangle(numb,3,5,3,red)
    kit.render()
    time.sleep(.05)

kit.set_background(green)
kit.render()
```

## PixelKit smile

```
import PixelKit as kit

kit.clear()
green = [0, 5, 0]
red = [10, 0, 0]
kit.set_background(green)

for j in [2,3,8,9]:
  kit.set_pixel(j, 2, red)

for k in [2,3,5,6,8,9]:
  kit.set_pixel(k, 3, red)

for l in [5,6]:
  kit.set_pixel(l, 4, red)

for m in [2,9]:
  kit.set_pixel(m, 5, red)

for n in [3,4,5,6,7,8]:
  kit.set_pixel(n, 6, red)

kit.render()
```

## Show lists - demonstrate for/in

```
import time

for count in range(2,10):
  time.sleep(.25)
  print(count)

dudes = ["Jason", "Isaiah", "Joseph"]

for dude in dudes:
  print(dude)

laydeez = ["Jasmin", "Jazmine", "Jocelyn", "Alynna", "Trinity", "Vilma", "Marcella"]

for lady in laydeez:
  time.sleep(.25)
  print(lady)
  if lady == "Marcella":
    print("  Hey " + lady)
```

## Make american flag

```
import time
import PixelKit as kit

red = [10, 0, 0]
green = [0, 10, 0]
white = [10,10,10]
blue = [0, 0, 10]

kit.clear
kit.set_background(white)

def makeLine(therow):
  for col in range(0,16):
    kit.set_pixel(col, therow, red)

makeLine(0)
makeLine(2)
makeLine(4)
makeLine(6)

for i in range(0,6):
  for j in range(0,4):
    kit.set_pixel(i, j, blue)

kit.render()
```

## Make rectangle move 2

```
import time
import PixelKit as kit

white = [10,10,10]
blue = [0, 0, 10]

kit.clear
kit.set_background(white)

def makeRectangle(width,height,xpos,ypos):
  for i in range(0,width):
    for j in range(0,height):
      kit.set_pixel(xpos+i, ypos+j, blue)

def makeIt(pos,row):
  kit.set_background(white)
  makeRectangle(3,3,pos,row)
  kit.render()
  time.sleep(.05)

def bounceIt(row):
  for pos in range(0,14):
    makeIt(pos,row)
  for pos in reversed(range(0,14)):
    makeIt(pos,row+1)

while True:
  for i in [0,2,4,6]:
  bounceIt(i)
```

## Make pixel move using dial

```
import PixelKit as kit
import time

position = 15

def change_position(dial_value):
global position
if position > 0:
position = int(dial_value / 4096 \* 15)

kit.on_dial = change_position

while True:
kit.check_controls()
kit.set_background([1,7,4])
kit.set_pixel(position,4,[6,1,10])
kit.render()
sleep(.1)
```

## Use dial to move square across the screen

```
import PixelKit as kit
import time

# clear the screen
kit.clear()

# set initial position
position = 0

# function to change the position based on the dial position
def changePosition(dial_value):
  global position
  position = int(dial_value / 4096 * 15)

# event listener for the dial change
kit.on_dial = changePosition

# function to make the square
def makeSquare(column,row):
  # set color
  color = [10,5,18]

  # check if column/row are out of bounds
  if column > 14:
    column = 14

  if column < 0:
    column = 0

  if row > 6:
    row = 6

  if row < 0:
    row = 0

  # draw square
  kit.set_pixel(column,row,color)
  kit.set_pixel(column+1,row,color)
  kit.set_pixel(column,row+1,color)
  kit.set_pixel(column+1,row+1,color)

  kit.render()

while True:
  kit.check_controls()
  kit.clear()
  makeSquare(position, 3)
  time.sleep(.1)
```

## Drawing using the joystick and buttons

```
# imports
# set initial column and row positions variables “col” and “row”
# define the 4 movement functions and how they change the col and row variables
#

import PixelKit as kit
import time
import random

col = 8
row = 4

kit.clear()

def moveLeft():
  global col
  col = col - 1
  if col < 0:
    col = 0

def moveRight():
  global col
  col = col + 1
  if col > 15:
    col = 15

def moveDown():
  global row
  row = row + 1
  if row > 7:
    row = 7

def moveUp():
  global row
  row = row - 1
  if row < 0:
    row = 0

def clearKit():
  kit.clear()

def colorChange():
  r = random.randint(0,20)
  g = random.randint(0,20)
  b = random.randint(0,20)
  global color
  color = [r,g,b]

colorChange()

kit.on_joystick_left = moveLeft
kit.on_joystick_right = moveRight
kit.on_joystick_up = moveUp
kit.on_joystick_down = moveDown
kit.on_button_a = clearKit
kit.on_button_b = colorChange

while True:
  kit.check_controls()
  kit.set_pixel(col,row,color)
  kit.render()
  sleep(.1)
```
