import simplegui
import random

# Global variables
current_room = "dark_screen"
character_pos = [50, 200]  # Initial position of the player
snakes = []  # List to store snake attributes
character_speed = 12  # Increased speed for movement
is_game_over = False
is_game_won = False  # Flag to track if the player has won
is_timer_running = False  # Flag to track if the timer is active
score = 0
health = 100
timer = None
treasures = []  # List to store treasure positions

def create_snakes(num_snakes):
    """Creates a number of snakes with random positions, directions, and speeds."""
    return [{"x": random.randint(20, 380),
             "y": random.randint(20, 380),
             "direction": (random.choice([-1, 1]), random.choice([-1, 1])),
             "speed": random.randint(1, 1)} for _ in range(num_snakes)]  # Speed decreased to 1

# Create a dark screen handler
def start_game():
    global current_room, score, health, is_game_won, is_timer_running, snakes
    current_room = "dark_screen"
    score = 0
    health = 100
    is_game_won = False  # Reset win status
    is_timer_running = False  # Reset timer status
    snakes = create_snakes(10)  # Create 10 snakes
    update_game()

# Game Commands
def go_north():
    global current_room, score, timer, treasures
    current_room = "treasure_room"
    score = 0  # Reset score when entering
    treasures = [(random.randint(50, 350), random.randint(50, 350)) for _ in range(10)]  # Create 10 treasures
    timer.start()  # Start the timer
    update_game()

def go_east():
    global current_room, character_speed, is_game_over, is_timer_running
    current_room = "snake_room"
    character_speed = 12  # Set speed to 12 for the snake room
    is_game_over = False  # Reset is_game_over flag
    is_timer_running = True  # Start the 10-second timer
    timer.start()  # Start the timer for avoiding snakes
    update_game("Avoid being caught by snakes for 10 seconds!")

def examine_room():
    global current_room
    current_room = "examine_room"
    update_game("Not welcomed here.")

def timer_handler():
    global is_game_over, is_game_won, is_timer_running
    # Check if the timer is running
    if is_timer_running:
        is_game_won = True  # The player wins if they avoid snakes for 10 seconds
        is_timer_running = False  # Stop the timer
        update_game("Congratulations! You avoided the snakes! You win!")

# Update the game state and GUI
def update_game(event_message=""):
    global is_game_over, is_game_won, is_timer_running

    # Update the GUI elements based on current_room
    room_label.set_text(get_room_description())
    score_label.set_text("Score: " + str(score))
    health_label.set_text("Health: " + str(health))
    
    if event_message:
        event_label.set_text(event_message)

    if is_game_over:
        event_label.set_text("Game Over!")

    if is_game_won:
        event_label.set_text("You Win!")

# Room descriptions
def get_room_description():
    if current_room == "dark_screen":
        return "You are in a dark place. What would you like to do?"
    elif current_room == "treasure_room":
        return "You are in a room filled with treasures! Collect as many as you can!"
    elif current_room == "snake_room":
        return "You have entered the snake's territory! Be careful! Use arrow keys to avoid getting caught."
    return ""

# Draw the game screen
def draw(canvas):
    global current_room, is_game_over, is_game_won, snakes, character_pos, treasures
    
    # Draw background
    canvas.draw_polygon([(0, 0), (400, 0), (400, 400), (0, 400)], 1, "black", "black")
    canvas.draw_text("A Dark Place", (130, 30), 24, "White")

    if is_game_over:
        canvas.draw_text("Game Over!", (150, 200), 40, "Red")
        return

    if is_game_won:
        canvas.draw_text("You Win!", (150, 200), 40, "Green")
        return

    if current_room == "snake_room":
        draw_snakes(canvas)  # Call to draw snakes
        draw_player(canvas)   # Draw the player
        
        # Check if the timer is running and check for collisions
        for snake in snakes:
            head_x = snake["x"]
            head_y = snake["y"]
            if (character_pos[0] - head_x) ** 2 + (character_pos[1] - head_y) ** 2 < 10 ** 2:  # Check if player is in collision with a snake
                is_game_over = True
                is_timer_running = False  # Stop the timer
                update_game("You got caught by a snake!")
                return
        
        # Move snakes
        for snake in snakes:
            snake["x"] += snake["direction"][0] * snake["speed"]
            snake["y"] += snake["direction"][1] * snake["speed"]

            # Bounce off walls
            if snake["x"] < 10 or snake["x"] > 390:  # Check if snake has reached the edges
                snake["direction"] = (-snake["direction"][0], snake["direction"][1])  # Bounce off the edges
            if snake["y"] < 10 or snake["y"] > 390:  # Check if snake has reached the edges
                snake["direction"] = (snake["direction"][0], -snake["direction"][1])  # Bounce off the edges

    if current_room == "treasure_room":
        draw_treasures(canvas)

    if current_room == "dark_screen":
        canvas.draw_text("You are in a dark place. What would you like to do?", (50, 100), 18, "White")

# Draw the player using shapes
def draw_player(canvas):
    # Draw player (simple stick figure)
    x, y = character_pos
    canvas.draw_circle((x, y - 10), 10, 1, "blue", "lightblue")  # Head
    canvas.draw_line((x, y), (x, y + 30), 3, "blue")  # Body
    canvas.draw_line((x, y), (x - 10, y + 20), 3, "blue")  # Left arm
    canvas.draw_line((x, y), (x + 10, y + 20), 3, "blue")  # Right arm
    canvas.draw_line((x, y + 30), (x - 10, y + 50), 3, "blue")  # Left leg
    canvas.draw_line((x, y + 30), (x + 10, y + 50), 3, "blue")  # Right leg

# Draw the snakes
def draw_snakes(canvas):
    for snake in snakes:
        head_x = snake["x"]
        head_y = snake["y"]
        canvas.draw_circle((head_x, head_y), 10, 1, "green", "lightgreen")  # Head
        canvas.draw_line((head_x, head_y),
                         (head_x + snake["direction"][0] * 20, head_y + snake["direction"][1] * 20), 3, "green")  # Body
        eye_x = head_x + snake["direction"][0] * 15
        eye_y = head_y + snake["direction"][1] * 15
        canvas.draw_circle((eye_x, eye_y), 2, 1, "red", "red")  # Eye

# Draw treasures
def draw_treasures(canvas):
    global score, treasures
    for treasure in treasures:
        x, y = treasure
        canvas.draw_circle((x, y), 10, 1, "gold", "yellow")  # Draw treasures as circles
        canvas.draw_text("Treasure!", (x - 30, y - 15), 12, "White")

# Handle treasure click
def mouseclick(pos):
    global score, treasures
    for treasure in treasures[:]:  # Copy the list to avoid modifying while iterating
        if (pos[0] - treasure[0]) ** 2 + (pos[1] - treasure[1]) ** 2 < 10 ** 2:  # Check if clicked on a treasure
            score += 10
            treasures.remove(treasure)  # Remove the collected treasure
            score_label.set_text("Score: " + str(score))  # Update score label immediately

# Handle keyboard input for character movement
def keydown(key):
    if not is_game_over and not is_game_won:  # Prevent movement if game is over or won
        if key == simplegui.KEY_MAP['up']:
            character_pos[1] -= character_speed
        elif key == simplegui.KEY_MAP['down']:
            character_pos[1] += character_speed
        elif key == simplegui.KEY_MAP['left']:
            character_pos[0] -= character_speed
        elif key == simplegui.KEY_MAP['right']:
            character_pos[0] += character_speed

# GUI elements
frame = simplegui.create_frame("Text-Based Adventure Game", 400, 400)
frame.set_canvas_background("black")  # Set background color

room_label = frame.add_label(get_room_description())
event_label = frame.add_label("")
score_label = frame.add_label("Score: " + str(score))
health_label = frame.add_label("Health: " + str(health))

# Create buttons
frame.add_button("Go North", go_north, 100)
frame.add_button("Go East", go_east, 100)
frame.add_button("Examine Room", examine_room, 100)

# Set timer for 10 seconds
timer = simplegui.create_timer(10000, timer_handler)

# Set the draw and keyboard handlers
frame.set_draw_handler(draw)
frame.set_mouseclick_handler(mouseclick)
frame.set_keydown_handler(keydown)

# Start the game
start_game()
frame.start()
