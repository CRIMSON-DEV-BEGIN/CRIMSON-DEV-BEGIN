## Hi there 👋

<!--
**CRIMSON-DEV-BEGIN/CRIMSON-DEV-BEGIN** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
--> import turtle
import random

# Set up the screen
screen = turtle.Screen()
screen.title("Spinning Wheel")
screen.bgcolor("white")

# Create a turtle for the wheel
wheel = turtle.Turtle()
wheel.speed(0)
wheel.hideturtle()

# Draw the wheel
wheel.penup()
wheel.goto(0, -150)
wheel.pendown()
wheel.circle(150)

# Draw the segments of the wheel
colors = ['red', 'blue', 'green', 'yellow', 'purple', 'orange']
num_segments = len(colors)
angle = 360 / num_segments

for color in colors:
    wheel.fillcolor(color)
    wheel.begin_fill()
    wheel.penup()
    wheel.goto(0, 0)
    wheel.pendown()
    wheel.forward(150)
    wheel.left(90)
    wheel.circle(150, angle)
    wheel.left(90)
    wheel.forward(150)
    wheel.left(180)
    wheel.end_fill()

# Create a turtle for the arrow
arrow = turtle.Turtle()
arrow.shape("triangle")
arrow.color("black")
arrow.shapesize(1, 3)
arrow.penup()
arrow.goto(0, 160)
arrow.setheading(270)
arrow.pendown()

# Function to spin the wheel
def spin_wheel():
    spin_angle = random.randint(360, 3600)
    wheel.right(spin_angle)
    selected_color = colors[(spin_angle // int(angle)) % num_segments]
    print(f"The wheel landed on: {selected_color}")
    screen.ontimer(spin_wheel, 2000)

# Spin the wheel every 2 seconds
screen.ontimer(spin_wheel, 2000)

# Start the main loop
turtle.done()
