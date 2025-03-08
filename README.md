﻿# My Project
## Description
[Jump King](https://en.wikipedia.org/wiki/Jump_King) game made in Jack programming language of nand2tetris project.
## Limitation
1. No floating point numbers
2. Integer values (-32768..32767)

## Optimization
Poking memory from Jack OS Memory class is used to draw objects instead of using 
implemented Jack OS class Screen which provides with a method setPixel(int x, int y).

https://github.com/user-attachments/assets/c0ad0333-6015-4034-893c-e60ae975836c
