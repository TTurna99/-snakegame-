# -snakegame-
import turtle
import time
import random

hiz = 0.15


pencere = turtle.Screen()
pencere.title('Snake Game')
pencere.bgcolor('Black')
pencere.setup(width=1920, height=1080)
pencere.tracer(0)

kafa = turtle.Turtle()
kafa.speed(0)
kafa.shape('square')
kafa.color('white')
kafa.penup()
kafa.goto(0, 100)
kafa.direction = 'stop'

yemek = turtle.Turtle()
yemek.speed(0)
yemek.shape('circle')
yemek.color('red')
yemek.penup()
yemek.goto(0, 0)
yemek.shapesize(0.80, 0.80)

kuyruklar = []



def move():
    if kafa.direction == 'up':
        y = kafa.ycor()
        kafa.sety(y + 30)

    if kafa.direction == 'down':
        y = kafa.ycor()
        kafa.sety(y - 30)

    if kafa.direction == 'right':
        x = kafa.xcor()
        kafa.setx(x + 30)

    if kafa.direction == 'left':
        x = kafa.xcor()
        kafa.setx(x - 30)

def goUp():
    if kafa.direction != 'down':
        kafa.direction = 'up'
def goDown():
    if kafa.direction != 'up':
        kafa.direction = 'down'
def goRight():
    if kafa.direction != 'left':
        kafa.direction = 'right'
def goLeft():
    if kafa.direction != 'right':
        kafa.direction = 'left'

pencere.listen()
pencere.onkey(goUp, 'Up')
pencere.onkey(goDown, 'Down')
pencere.onkey(goRight, 'Right')
pencere.onkey(goLeft, 'Left')

while True:
    pencere.update()


    if kafa.distance(yemek) < 20:
        x = random.randint(-250, 250)
        y = random.randint(-250, 250)
        yemek.goto(x, y)

        yeniKuyruk = turtle.Turtle()
        yeniKuyruk.speed(0)
        yeniKuyruk.shape('square')
        yeniKuyruk.color('white')
        yeniKuyruk.penup()
        kuyruklar.append(yeniKuyruk)

      for i in range(len(kuyruklar) - 1, 0, -1):
          x = kuyruklar[i - 1].xcor()
          y = kuyruklar[i - 1].ycor()
          kuyruklar[i].goto(x, y)

      if len(kuyruklar) > 0:
         x = kafa.ycor()
         y = kafa.ycor()
         kuyruklar[0].goto(x, y)

    move()
    time.sleep(hiz)

