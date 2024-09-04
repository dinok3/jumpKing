# My Project
## Description
[Jump King](https://en.wikipedia.org/wiki/Jump_King) game made in Jack programming language of nand2tetris project.
## Limitation
1. No floating point numbers
    => numerator has to be bigger then denominator
    => multiply dividend by 10 to some power to get "decimal numbers"
2. Integer values (-32768..32767)
    => after divison again multiply with whats left
## Optimization
Poking memory from Jack OS Memory class is used to draw objects instead of using 
implemented Jack OS class Screen which provides with a method setPixel(int x, int y).
## Physics

## Animation
