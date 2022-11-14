#udemy  #billennium  #python  #game #penny_de_by
#pygame


[[3 - Breakin'`Bricks]]


# Intro Pygame - Learn about Game Mechanics
## Pygame



## Four elements 
that the player will interact with during the challenge 
1. **rules**  - they restrict possible choices
2. **feedback** - is player doing the correct thing solving the right problem;
3. **tools** - that players can use
4. **actions** - what can a layer  do?

![[Game mechanic.excalidraw | 700]]

---
## List of game mechanics
- HITTING and SHOOTING
- SEARCHING
- MATCHING
- SORTING
- CHANCING
- MIXING - involves the action of combining objects or actions to produce an outcome unachievable otherwise
- TIMING (i.e. racing game)
- CAPTURING
- CONQUERING
- AVOIDANCE you are trying to avoid brcoming a victim
- COLLECTION
- PROGRESSING

### games
#### Breakout
- hitting 
- conquering 
- timing

#### Tetris
- sorting   
- matching
- timing
- searching
- mixing

#### Asteroids
- shooting
- avoiding
- conquering

#### Space Invaders
- shooting
- avoiding
- conquering
- chancing
- timing
- 
-----

## at the beginning 
### Sprite
```python
import pygame

# You can create ONLY ONE window
pygame.init()

# You can create may screens
# ((size), flags, buffer depth
screen = pygame.display.set_mode((800, 600), 0, 32)
pygame.display.set_caption("Hello Sprite")
sprite1 = pygame.image.load('./images/football.png')
screen.fill((0,0,0))

# every graphical element needs to have an endless loop
# to keep an application open
game_over = False
while not game_over:
    for event  in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True
    # Bit bLock transfer -> for drawing stuff onto displays
    screen.blit(sprite1, (784,584)) # to set in the center
    pygame.display.update()


pygame.quit()
```

### resizing
```python
import pygame

pygame.init()

screen = pygame.display.set_mode((500,500), 0, 32)
pygame.display.set_caption("ButterFly")
sprite2 = pygame.image.load('./images/butterfly.png')
sprite2 = pygame.transform.scale(sprite2, (50,50))
spriteWidth = sprite2.get_width()
spriteHeight = sprite2.get_height()

screen.fill((0,0,0))

game_over = False
while not game_over:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True

    screen.blit(sprite2, (screen.get_width()/2 - spriteWidth, screen.get_height()/2 - spriteHeight))
    pygame.display.update()

pygame.quit()



```

----
### keys
```python
import pygame
from pygame.locals import *

pygame.init()

screen = pygame.display.set_mode((500,500), 0, 32)
pygame.display.set_caption("ButterFly")
sprite2 = pygame.image.load('./images/butterfly.png')
sprite2 = pygame.transform.scale(sprite2, (50,50))
spriteWidth = sprite2.get_width()
spriteHeight = sprite2.get_height()

screen.fill((0,0,0))

game_over = False
x, y = (0,0)
while not game_over:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True
        pressed = pygame.key.get_pressed()
   # if these 'ifs' will be inside the loop
   # to move sprite press th button

    # 'Ifs' are outside the loop
    # sprite will move by holding a button
    if pressed[K_UP]:
        y -= 0.5
    if pressed[K_DOWN]:
        y += 0.5
    if pressed[K_LEFT]:
        x -= 0.5
    if pressed[K_RIGHT]:
        x += 0.5
    screen.blit(sprite2, (x,y))
    pygame.display.update()

pygame.quit()



```

----
### FRAMES
Frames get upadated in a game.
After you draw one frame (something new)
, you clear the screen.
In each loop we will clear the screen by `screen.fill(0,0,0)`

The game runs at a certain frame rate (like 100 frames per second). You can set this value.
Outside the loop:
`clock = pygame.time.Clock()`
and INSIDE the loop:
`td = clock.tick(100)`
and change:
` y -= 0.5 *dt` etc.

```python
import pygame
from pygame.locals import *

pygame.init()

screen = pygame.display.set_mode((500,500), 0, 32)
pygame.display.set_caption("ButterFly")
sprite2 = pygame.image.load('./images/butterfly.png')
sprite2 = pygame.transform.scale(sprite2, (50,50))
spriteWidth = sprite2.get_width()
spriteHeight = sprite2.get_height()

screen.fill((0,0,0))

game_over = False
x, y = (0,0)
clock = pygame.time.Clock()
while not game_over:
    dt = clock.tick(30)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True

    pressed = pygame.key.get_pressed()
   # if these 'ifs' will be inside the loop
   # to move sprite press th button

    # 'Ifs' are outside the loop
    # sprite will move by holding a button
    if pressed[K_UP]:
        y -= 0.5 * dt
    if pressed[K_DOWN]:
        y += 0.5 * dt
    if pressed[K_LEFT]:
        x -= 0.5 * dt
    if pressed[K_RIGHT]:
        x += 0.5 * dt
    if pressed[K_SPACE]:
        x = 0
        y = 0

    screen.fill((0,0,0))
    screen.blit(sprite2, (x,y))
    pygame.display.update()

pygame.quit()



```


----
### BUTTON CHANGES COLOUR
```python
import pygame

pygame.init()
screen = pygame.display.set_mode((500, 500), 0, 32)
pygame.display.set_caption("Hello Button")
text_color = (255, 255, 255)
button_colour = (0, 0, 170)
button_over_colour = (255, 50, 50)
button_width = 100
button_height = 50
x = (screen.get_width() - button_width)/2
y = screen.get_height()/2 - button_height/2
button_rect = [x, y, button_width, button_height]
button_font = pygame.font.SysFont('Arial', 20)
button_text = button_font.render('Quit', True, text_color)
screen.fill((100, 100, 100))
game_over = False
x, y = (0, 0)
while not game_over:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True
        if event.type == pygame.MOUSEBUTTONDOWN:
            x, y = event.pos
            # button_rect[0] -x     ,   button_rect[1] - y
            # button_rect[2] - width ,   button_rect[3] - height
            if(button_rect[0] <= x <= button_rect[0] + button_rect[2] and
               button_rect[1] <= y <= button_rect[1] + button_rect[3]):
                game_over = True
        if event.type == pygame.MOUSEMOTION:
            x, y = event.pos

    if(button_rect[0] <= x <= button_rect[0] + button_rect[2] and
       button_rect[1] <= y <= button_rect[1] + button_rect[3]):
        pygame.draw.rect(screen, button_over_colour, button_rect)
    else:
        pygame.draw.rect(screen, button_colour, button_rect)

    # pygame.draw.rect(screen, button_colour, button_rect)
    screen.blit(button_text, (button_rect[0] + button_width/2 - button_text.get_width()/2,
                              button_rect[1] + (button_height - button_text.get_height())/2))
    pygame.display.update()


pygame.quit()







```











