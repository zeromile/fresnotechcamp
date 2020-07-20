# Day 08 - Python Challenge #

Open up your Journal file in WordPad; go to the bottom and add an entry for today:
### Thursday, July 25th, AM Challenge ###
Write out the COMPLETE code to make a function called `makeSquare(column,row)` that uses the `PixelKit` library to draw a square 2 px by 2 px at any column/row coordinate supplied when the function is called. The function must use `if` statements to check if the column/row coordinates are out of range (past column 15, row 7, or less than 0 row or column) AND adjust the coordinates so that the square is drawn at the nearest edge INSTEAD of off the screen. When you think you have the solution connect your Pixel Kits and run the code!

- HINT 1: Do not overthink this one. It's very basic, nothing fancy :)
- HINT 2: Basic math (addition and subtraction) will come in very handy...

## Code you will need... ##
```
- if True :
- import PixelKit as kit
- render()
- kit.set_pixel(x, y, color)
- def function name() :
```

## Solution ##
```
import PixelKit as kit

kit.clear()

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
  
  # render the screen
  kit.render()

# create a square, test the out-of-bounds code
makeSquare(-2,-3)
```
