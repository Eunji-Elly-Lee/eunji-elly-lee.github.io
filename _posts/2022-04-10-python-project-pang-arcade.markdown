---
layout:     post
title:      "Python Project: Pang Arcade"
date:       2022-04-10
image:      python_code.jpg
categories: [Python]
---

<p class="intro"><span class="dropcap">P</span>ython's <strong>pygame</strong> is a free library for game development.</p>

We will learn the functions of **pygame** by creating a simple version of Pang which is a retro arcade game. Pang is a game in which a gamer moves a character from side to side, avoiding balloons, and firing weapons to eliminate balloons.

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

To be more clearly, let's create a test file to make sure that the installation is completed well. Import **pygame**, and press the triangle button in the upper right to run the file. If it runs well without any errors, we can go to the next step.

<div style="text-align:center">
<img src="/assets/img/python_img/pygame_import.png" width="80%">
</div>

For more information about **pygame**, please refer to the two links below.

<https://www.pygame.org/news>

<https://github.com/pygame/pygame>

### Basic Frame 

To use **pygame**'s modules, initialization and shutdown are essential. They are `pygame.init()` and `pygame.quit()`, and all the codes for the game will be written between these two.

To set the size of the game window, create variables for the width and height, and then put them in `set_mode` method of **display** module. Declare the object created to a variable so that it can continue to be used. Also, we can set the title of the game using the `set_caption` method.

Create a **time** object with **time** module and `clock()` method to set FPS (frames per second), the frame rate, and then set the value using the `tick` method. The higher the value, the faster the game running and feels more natural. 

We will prepare a **while** statement for game running and **for** statement for event handling. `update()` method of **display** module is required within the **while** statement because the screen must be drawn continuously during the game running.


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
6. Game over when the ball hits the character (mission failed)
7. If the time limit of 99 seconds is exceeded, the game ends (mission failed)

A game requires images for visible operation. At this stage, we will just use simple shapes to develop the game.

1. Background: 640 * 480
2. Stage: 640 * 50
3. Character: 33 * 60
4. Weapon: 20 * 430
5. Balloons: 160 * 160, 80 * 80, 40 * 40, 20 * 20

<div style="text-align:center">
<img src="/assets/img/python_img/simple_shapes.png" width="80%">
</div>

### Game Development

After placing the images in the **images** folder, import **os** module to find a path to use them. This module is a part of the standard library, so we can just get it using `import` keyword. Use `dirname` method, which is to obtain the directory name, using the special variable `__file__` to get the current path, and use `join` method to get the path of the folder containing the images.

```python
import os

# get the path of the current file
current_path = os.path.dirname(__file__)
# get the path of the images folder
image_path = os.path.join(current_path, "images")
```

Create the background, stage, and character on the screen using the path we got. To place the character on the stage, we will use `get_rect()` method so that we can obtain the height of the stage. `get_rect()` method returns a **Rect** object from an image and allows us to take its width and height and use them. **size** attribute of the **Rect** object is **Tuple**, and the first element stores the width and the second element stores the height. It is also used to place the character in the middle of the width of the screen.

```python
# create background
background = pygame.image.load(os.path.join(image_path, "background.png"))

# create stage
stage = pygame.image.load(os.path.join(image_path, "stage.png"))
stage_size = stage.get_rect().size
stage_height = stage_size[1]

# create character
character = pygame.image.load(os.path.join(image_path, "character.png"))
character_size = character.get_rect().size
character_width = character_size[0]
character_height = character_size[1]
character_x_pos = (screen_width / 2) - (character_width / 2)
character_y_pos = screen_height - character_height - stage_height
```

Use `blit` method to display the created background, stage, and character on the screen. These codes will be placed above `update()` method in the **while** statement. Set the background to (0, 0) which is the upper left position because it is the same size as the screen. Set the stage at the bottom of the screen and the character at the center just above the stage.

```python
# display images
screen.blit(background, (0, 0))
screen.blit(stage, (0, screen_height - stage_height))
screen.blit(character, (character_x_pos, character_y_pos))
```

Let's make the character move. The character will move on the x-axis which means from side to side and have the speed appropriately. The character's movement will take place in the events of the left and right keys. When the left key is pressed, it will move from the position on the x-axis to the left by the speed set, so use subtraction to adjust the position. For the right key, addition will be used to reposition the character to the right. Yes, the speed can actually be thought of as the unit of movement.

We also need to consider and handle the situations when the event that was pressing the key is released and when the character reaches both left and right ends.

```python
# direction of moving
character_to_x = 0
# speed of character
character_speed = 5

# event handling
for event in pygame.event.get(): 
    # close the window by clicking the X button of the game window
    if event.type == pygame.QUIT:
        # stop the game 
        running = False

    # pressing key event
    if event.type == pygame.KEYDOWN:
        # move character to the left using the left key
        if event.key == pygame.K_LEFT:
            character_to_x -= character_speed
        # move character to the left using the left key
        elif event.key == pygame.K_RIGHT:
            character_to_x += character_speed

    # releasing key event
    if event.type == pygame.KEYUP:
        if event.key == pygame.K_LEFT or event.key == pygame.K_RIGHT:
            character_to_x = 0

# reposition character
character_x_pos += character_to_x

# when character reaches left end
if character_x_pos < 0:
    character_x_pos = 0
# when character reaches right end
elif character_x_pos > screen_width - character_width:
    character_x_pos = screen_width - character_width
```

We will create a weapon and write a code to handle the event of the weapon. A weapon is fired when the space key is pressed, the x-axis position and y-axis position of the weapon are stored in **List** so that a number of weapons fired can be managed. Weapons automatically move up and then disappear when they reach the end. When displaying the weapons to the screen, the code of the weapons should be written before the stage's one because the layers of images follow the order of codes.

```python
# create weapon
weapon = pygame.image.load(os.path.join(image_path, "weapon.png"))
weapon_size = weapon.get_rect().size
weapon_width = weapon_size[0]

# weapon list
weapons = []
# speed of weapon
weapon_speed = 10

# pressing key event
if event.type == pygame.KEYDOWN:
    # move character to the left using the left key
    if event.key == pygame.K_LEFT:
        character_to_x -= character_speed
    # move character to the left using the left key
    elif event.key == pygame.K_RIGHT:
        character_to_x += character_speed
    # fire weapon from the center of character
    elif event.key == pygame.K_SPACE:
        weapon_x_pos = character_x_pos + (character_width / 2) - (weapon_width / 2)
        weapon_y_pos = character_y_pos
        weapons.append([weapon_x_pos, weapon_y_pos])

# move up weapons adjusting y position
weapons = [ [w[0], w[1] - weapon_speed] for w in weapons]
# when weapon reaches at top
# save only weapons whose y position is greater than 0
weapons = [ [w[0], w[1]] for w in weapons if w[1] > 0]

# display images
screen.blit(background, (0, 0))

for weapon_x_pos, weapon_y_pos in weapons:
    screen.blit(weapon, (weapon_x_pos, weapon_y_pos))

screen.blit(stage, (0, screen_height - stage_height))
screen.blit(character, (character_x_pos, character_y_pos))
```

