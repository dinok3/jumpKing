# My Project
## Description
[Jump King](https://en.wikipedia.org/wiki/Jump_King) game made in Jack programming language of nand2tetris project.
## Limitation
1. No floating point numbers
2. Integer values (-32768..32767)

## Optimization
Poking memory from Jack OS Memory class is used to draw objects instead of using 
implemented Jack OS class Screen which provides with a method setPixel(int x, int y).

## Main loop
60 FPS => each frame is showed in (1000/60) = 16.67 ms. In the game FPS is also game speed and
king's jump height because jump is not calculated based on frame time but fixed negative number
so less frames means less height.

## Movement
King moves 2 pixels to side on each side arrow pressed.His x coord is tracked as well as offset number from 0..7.
On direction change, symmetry is applied to offset and x coord is updated accordingly.
For vertical movement, depending on space hold king is moved at a rate of 4 px per frame(3,2,1,0).
Gravity is applied.

Out of screen bounds movement:
    1. Horizontal - each draw to side function which erases previous pixels and draws parts to
                    next memory location is moved up(new memory location - 32) when moving out of bounds
    2. Vertical   - when detected, king is drawn to opposite side and screen is refreshed(level is updated)

Erasing residue:
    1. Horizontal - i-th drawing function erases 2*i pixels behind king, changing direction works properly becasue of that
    2. Vertical   - white rectangle is drawn, high as much as king is moved vertically and wide as king is, other pixels
                    are erased by poking same memory locations with new draw function

## Physics
Gravity is implemented with airCounter variable which tracks how many frames king is in the air.
With equation for displacement downwards: g = (airTime * gravity) / FPS, where gravity is constant.
g = gravity when airTime = FPS which is always in 1s(frames per second). new_y is then currY + dy + g. For gravity = dy
king is at the highest point in 1s.

## Map
Map is an array of levels.Level is an array of Platforms. Platforms are rectangles.

## Game initialization
A game object is initialized on heap in main() function of Main class to not overload stack
which is very limited.