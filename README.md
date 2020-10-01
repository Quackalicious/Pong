	#In my pong game there is a problem where the paddles can phase through walls. The multiline comment at the end is what i tried but didn't work so if you can fix it then please comment the solution.
import turtle
import time

wnd = turtle.Screen()
wnd.title("Pong")
wnd.bgcolor("black")
wnd.setup(width=800, height=600)
wnd.tracer(0)

scoreA = 0
scoreB = 0

paddleA = turtle.Turtle()
paddleA.speed(0)
paddleA.shape("square")
paddleA.color("white")
paddleA.shapesize(stretch_wid=5,stretch_len=1)
paddleA.penup()
paddleA.goto(-350, 0)

paddleB = turtle.Turtle()
paddleB.speed(0)
paddleB.shape("square")
paddleB.color("white")
paddleB.shapesize(stretch_wid=5,stretch_len=1)
paddleB.penup()
paddleB.goto(350, 0)

Ball = turtle.Turtle()
Ball.speed(0)
Ball.shape("square")
Ball.color("white")
Ball.penup()
Ball.goto(0, 0)
Ball.dx = 0.5
Ball.dy = 0.5

Pen = turtle.Turtle()
Pen.speed(0)
Pen.shape("square")
Pen.color("white")
Pen.penup()
Pen.hideturtle()
Pen.goto(0, 260)
Pen.write("Player A: 0  Player B: 0", align="center", font=("Courier", 24, "normal"))

def paddle_a_up():
		y = paddleA.ycor()
		y += 70
		paddleA.sety(y)

def paddle_a_down():
		y = paddleA.ycor()
		y -= 70
		paddleA.sety(y)

def paddle_b_up():
		y = paddleB.ycor()
		y += 70
		paddleB.sety(y)

def paddle_b_down():
		y = paddleB.ycor()
		y -= 70
		paddleB.sety(y)

wnd.listen()
wnd.onkeypress(paddle_a_up, "w")
wnd.onkeypress(paddle_a_down, "s")
wnd.onkeypress(paddle_b_up, "Up")
wnd.onkeypress(paddle_b_down, "Down")

time.sleep(5)

while True:
		wnd.update()
		Ball.setx(Ball.xcor() + Ball.dx)
		Ball.sety(Ball.ycor() + Ball.dy)

		if Ball.ycor() > 290:
				Ball.sety(290)
				Ball.dy *= -1

		elif Ball.ycor() < -290:
				Ball.sety(-290)
				Ball.dy *= -1

		if Ball.xcor() > 350:
				scoreA += 1
				Pen.clear()
				Pen.write("Player A: {}  Player B: {}".format(scoreA, scoreB), align="center", font=("Courier", 24, "normal"))
				Ball.goto(0, 0)
				Ball.dx *= -1

		elif Ball.xcor() < -350:
				scoreB += 1
				Pen.clear()
				Pen.write("Player A: {}  Player B: {}".format(scoreA, scoreB), align="center", font=("Courier", 24, "normal"))
				Ball.goto(0, 0)
				Ball.dx *= -1

		if Ball.xcor() < -340 and Ball.ycor() < paddleA.ycor() + 50 and Ball.ycor() > paddleA.ycor() - 50:
				Ball.dx *= -1 
    
		elif Ball.xcor() > 340 and Ball.ycor() < paddleB.ycor() + 50 and Ball.ycor() > paddleB.ycor() - 50:
				Ball.dx *= -1
		"""
		if paddleA.ycor() > 400:
				paddleA.goto(-350,400)
		if paddleB.ycor() > 400:
				paddleB.goto(350,400)
		if paddleA.ycor() > -400:
				paddleA.goto(-350,-400)
		if paddleB.ycor() > -400:
				paddleB.goto(350,-400)
		"""
