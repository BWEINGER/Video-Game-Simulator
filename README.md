# Video Game Combat Simulator
Starting the summer after my junior year, I began to practice the programming techniques I learned by simulating the logic-based combat system of a somewhat complex video game I used to play. And in-depth overview of the code's functionality is detailed below.

Combat Simulator interface available for public use here:
http://adventuresofthespiral.com/battle-sim/
*Created and distributed with permission from KingsIsle Entertainment, Inc.

Brief user guide located here:
http://adventuresofthespiral.com/pirate101/introducing-battle-simulator/

This project was undertaken as a cooperative effort with an excellent friend, Alex Nichols. It would not have been possible without his collaboration on the code (particularly the HTML and CSS files, and ensuring the JS interacted correctly to build the interface). He is aware of the code's public distribution and does not claim any ownership.

# Overview

To generalize, combat in this game is intriguing in that one action can set off a unique chain of other actions based on probability (i.e. missing an attack could trigger an opponent's ability, which, in turn, triggers one of the player's, and successful completion of that attack could trigger a subsequent one, etc.). Since the outcomes become extraordinarily complex with so many variables (which can be customized or automatically calculated using a regression algorithm), the simulator can tell the user what the statistically "best" course of action is when it may appear unclear. In this sense, it functions as an AI of sorts, simulating tens of thousands of outcomes and making a decision based on the data it collects.

# HTML

Sets up the interface for the simulator - basic functionality is a form that, when submitted, runs the JavaScript code with the appropriate values entered into the fields. Includes user-friendly 


# CSS

# JS
