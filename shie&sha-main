import os, random, time, string
from turtle import Turtle, Screen
from Basket import Write_Score, Trapper

window = Screen()
window.bgcolor('black')
window.title('Shield and Shapes ')
window.setup(width=1000, height=550)
window.tracer(0)

Score = Write_Score()
hammer = Trapper()

window.listen()
window.onkey(hammer.go_left, "d")
window.onkey(hammer.go_right, "k")
        
default_speed = 0.02
def game():
    on_go = True
    while on_go:
        x_value = random.choice((-400,-300,200,100,0,-100,-200,300,400,))
        omer = Turtle()
        omer.penup()
        window.update()
        time.sleep(0.6)

        # توليد الأشكال العشوائية
        omer.shape(random.choice(('turtle', 'square', 'circle', 'triangle', 'classic', 'arrow')))
        omer.color(random.choice(('white', 'cornsilk1', 'DarkSeaGreen2', 'yellow', 'red', 'lightblue','chartreuse1', 'cyan', 'cornflowerblue', 'deepskyblue', 'azure4')))
        omer.shapesize(random.choice((1.3, 1.6, 2, 2.4)))
        omer.goto(x_value,200)
        omer.right(90)
        
         # الرحلة من والى
        reached = True
        while reached:
            window.update()
            global default_speed
            time.sleep(default_speed)
            omer.forward(10)
            
             # الاصطدام بالمحظور
            if omer.pencolor() == 'red' and omer.distance(hammer) <= 50 and omer.shape() == 'turtle':
                on_go = False
                time.sleep(2)
                window.clear()
                window.bgcolor('cornsilk4')
                omer.penup()
                omer.goto(0,50)
                omer.hideturtle()
                omer.color('orange')
                omer.write("Game over !", align='center', font=('arial', 29, 'bold'))
                omer.goto(0,-50)
                omer.write(f"Final Score: {Score.score}", align='center', font=('arial', 19, 'bold'))

             # الإصطدام بالطعام والإضافات المعينة
            if omer.distance(hammer) <= 50 and omer.shape() in ['circle','arrow', 'classic']:
                Score.update_score(given_number=1)
                default_speed *= 0.93

            if omer.distance(hammer) <= 50 and omer.shape() == 'square':
                Score.update_score(given_number=2)
                default_speed *= 0.93

            if omer.distance(hammer) <= 50 and omer.shape() == 'turtle':
                Score.update_score(5)
                default_speed *= 0.93

            if omer.distance(hammer) <= 50 and omer.shape() == 'triangle':
                Score.update_score(given_number=0)
                default_speed = 0.08
                
            if omer.ycor() <= -250 or omer.distance(hammer) <= 50:
                omer.hideturtle()
                reached = False
                
game()

window.exitonclick()
