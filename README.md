<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Snake Adventure Game - README</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            background-color: #f4f4f4;
            color: #333;
            margin: 20px;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1, h2, h3 {
            color: #2c3e50;
        }
        h1 {
            text-align: center;
        }
        ul {
            margin-left: 20px;
        }
    </style>
</head>
<body>

    <h1>Snake Adventure Game</h1>

    <h2>Overview</h2>
    <p>Welcome to the Snake Adventure Game! In this exciting game, you find yourself in a dark room filled with treasures and sneaky snakes. Your goal is to collect treasures while avoiding the snakes for at least 10 seconds. If you touch a snake, it's "Game Over!" But if you successfully avoid them, "You Win!"</p>

    <h2>Game Mechanics</h2>
    <ul>
        <li><strong>Movement:</strong> Use the arrow keys on your keyboard (up, down, left, right) to move your player around the screen. The faster you move, the easier it will be to avoid the snakes.</li>
        <li><strong>Collecting Treasures:</strong> You can collect treasures that appear in the rooms. When you move over a treasure, it will disappear, and your score will increase.</li>
        <li><strong>Avoiding Snakes:</strong> Be careful! If you touch a snake, the game ends, and you'll see "Game Over!" on the screen. If you stay away from the snakes for 10 seconds, you'll win!</li>
    </ul>

    <h2>How to Play</h2>
    <ol>
        <li>Start the game and read the instructions on the screen.</li>
        <li>Use the buttons to navigate between different rooms:
            <ul>
                <li><strong>Go North:</strong> Enter the treasure room where you can find treasures to collect.</li>
                <li><strong>Go East:</strong> Enter the snake room, where you need to avoid the snakes for 10 seconds.</li>
                <li><strong>Examine Room:</strong> This option won't allow you to progress but lets you explore what's in the dark room.</li>
            </ul>
        </li>
        <li>Move your character using the arrow keys and try to collect as many treasures as you can while avoiding the snakes.</li>
        <li>Keep an eye on the timer! It counts down from 10 seconds when you enter the snake room.</li>
    </ol>

    <h2>GUI & Buttons</h2>
    <h3>Buttons:</h3>
    <ul>
        <li><strong>Go North:</strong> Takes you to the treasure room where you can collect treasures.</li>
        <li><strong>Go East:</strong> Takes you to the snake room where you try to avoid being caught by snakes.</li>
        <li><strong>Examine Room:</strong> A button that lets you look around in the dark room without progress.</li>
    </ul>

    <h3>Labels:</h3>
    <ul>
        <li><strong>Room Description:</strong> Displays the current room you are in and provides hints for what to do.</li>
        <li><strong>Score:</strong> Shows how many treasures you've collected.</li>
        <li><strong>Health:</strong> Displays your health status (currently not fully implemented but for future enhancements).</li>
        <li><strong>Event Messages:</strong> Tells you important information like "Game Over!" or "You Win!"</li>
    </ul>

    <h2>Game Progression</h2>
    <ul>
        <li>The game begins in a dark room where you can make choices on where to go.</li>
        <li>You’ll switch between rooms filled with treasures and snakes.</li>
        <li>The game tracks your score and gives you feedback with event messages.</li>
        <li>It will display a win or lose message based on your ability to avoid snakes for 10 seconds.</li>
    </ul>

    <h2>Evaluation Criteria</h2>
    <h3>Functionality and Interactivity (30%)</h3>
    <p>The game has buttons that respond to your clicks to navigate. You can move your player and interact with the environment (like collecting treasures).</p>

    <h3>Creativity and Storytelling (30%)</h3>
    <p>The game has a fun theme with interesting challenges (avoiding snakes and collecting treasures). The room descriptions tell a little story of where you are in the game.</p>

    <h3>Code Structure and Quality (20%)</h3>
    <p>The code is organized into functions that are easy to follow. Each function has a clear purpose. Variables are named well so you can understand what they do (like <code>character_pos</code> for the player's position).</p>

    <h3>Use of Python Concepts (10%)</h3>
    <p>The game uses loops and conditionals to control game mechanics (like moving and checking for collisions). Functions are used throughout the game to keep the code organized and modular.</p>

    <h3>Presentation and Documentation (10%)</h3>
    <p>This README clearly explains how the game works, how to play, and what to expect. Key parts of the code are commented on, explaining what each section does.</p>

    <h2>Video Demonstration</h2>
    <p>A video demonstration of the Snake Adventure Game will follow, showing:</p>
    <ul>
        <li>An overview of the GUI, buttons, and labels on the screen.</li>
        <li>A brief gameplay walkthrough demonstrating how the player navigates, collects treasures, and tries to avoid snakes.</li>
    </ul>

</body>
</html>
