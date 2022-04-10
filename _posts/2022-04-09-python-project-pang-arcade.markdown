---
layout:     post
title:      "Python Project: Pang Arcade"
date:       2022-04-09
image:      python_code.jpg
categories: [Python]
---

<p class="intro"><span class="dropcap">P</span>ython's <strong>pygame</strong> is a free library for game development.</p>

We will learn the functions of pygame by creating a simple version of Pang which is a retro arcade game. Pang is a game in which a gamer moves a character from side to side, avoiding balloons, and firing weapons to eliminate balloons.

<div style="text-align:center">
<img src="https://blog.kakaocdn.net/dn/wbylH/btqEq7mRkqZ/6ZNFUVAMiNR4bWccWMrbmk/img.gif" width="80%">
</div>

<!-- <div style="text-align:center">
<video width="65%" controls>
<source src="/assets/video/python_video.mp4" type="video/mp4">
</video>
</div> -->

### Pygame Installation

First, open a terminal window in VS Code and run `pip install pygame`. If we can see a statement "Successfully installed pygame," it means that the installation has been done well. It is very simple and easy.

<div style="text-align:center">
<img src="/assets/img/python_img/pygame_install.png" width="80%">
</div>

To be more clearly, let's create a test file to make sure that the installation is completed well. Import pygame, and press the triangle button in the upper right to run the file. If it runs well without any errors, we can go to the next step.

<div style="text-align:center">
<img src="/assets/img/python_img/pygame_import.png" width="80%">
</div>

For more information about pygame, please refer to the two links below.

<https://www.pygame.org/news>

<https://github.com/pygame/pygame>

### Basic Frame 

To use pygame's modules, initialization and shutdown are essential. They are `pygame.init()` and `pygame.quit()`, and all the codes for the game will be written between these two.

To set the size of the game window, create variables for the width and height, and then put them in `set_mode` method of **display** module. Declare the object created to a variable so that it can continue to be used. Also, we can set the title of the game using the `set_caption` method.

Create a time object with **time** module and `clock()` method to set FPS (frames per second), the frame rate, and then set the value using the `tick` method. The higher the value, the faster the game running and feels more natural. 

We will prepare **while** statement for game running and **for** statement for event handling. `update()` method of **display** module is required within the **while** statement because the screen must be drawn continuously during the game running.


```python
import pygame

# initialization
pygame.init()

# screen setting
screen_width = 640
screen_height = 480
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Simple Pang Arcade")

# create time object
clock = pygame.time.Clock()

# game running
running = True 
while running:
    # set FPS
    clock.tick(30) 
    
    # event handling
    for event in pygame.event.get(): 
        # close the window by clicking the X button of the game window
        if event.type == pygame.QUIT:
            # stop the game 
            running = False
    
    # update screen continuously
    pygame.display.update() 

# shut down
pygame.quit()
```

We have completed the basic frame for game development, and we will be able to reuse it for other games as well.

### Game Setup

Before writing code, let's set the conditions for the game.

1. A character is located at the bottom of the screen and can only be moved from side to side
2. Press the space key to fire a weapon
3. A big ball appears and bounces
4. When the weapon touches the ball, the ball is divided into two smaller sizes and the smallest size ball disappears
5. Game over when all balls are eliminated (mission complete) 
6. Game over when the ball hits the character. (mission failed)
7. If the time limit of 99 seconds is exceeded, the game ends (mission failed)

A game requires images for visible operation. At this stage, we will just use simple shapes to develop the game.

1. Background: 640 * 480
2. Stage: 640 * 50
3. Character: 33 * 60
4. Weapon: 20 * 430
5. Balls: 160 * 160, 80 * 80, 40 * 40, 20 * 20

<div style="text-align:center">
<img src="/assets/img/python_img/simple_shapes.png" width="80%">
</div>

### Game Development


