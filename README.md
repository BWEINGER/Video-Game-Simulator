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

Sets up the interface for the simulator - basic functionality is a form that, when submitted, runs the JavaScript code with the appropriate values entered into the fields. Includes user-friendly options such as checkboxes, radio buttons, clickable images, etc. which call JavaScript functions and update the interface accordingly.

# CSS

Ensures proper formatting and page alignment of the HTML form, and allows for smooth transition between the user interface and the results screens. Alters fonts, background and button images, and other important cosmetic features.

# JS

The core of the simulation algorithm, attempts to model an instance of combat with the highest possible accuracy. Table of contents restated here with further elaboration on each section.

 Line 24 - UI FUNCTIONS:
  Functions called when the user alters the interface (i.e. clicks a button, unchecks a box, resets the simulator, etc.). While does not   directly impact how the code runs, ensures the user is aware of precisely what paramaters they are entering and how they will impact     the combat algorithm.

  Line 430 - CHANGE EPIC ABILITY RANKS:
   "Epic abilities" are a core element of combat, defined as attacks that trigger under specific circumstances. Mousing over an epic        ability image on the interface displays when it can be used. The interface allows the user to toggle the "rank" (primarily indicating    the number of times an ability can activate per instance of combat) by clicking on the image of an epic ability, and so this section    of the code modifies the image clicked on based on the previous one and the "class" the user selects (each class has a different set    of epic abilities).
   
  Line 735 - INITIALIZE UNIT NAME, CLASS, & LEVEL:
   Important variables that will impact what variables are used in the combat algorithm.
   
  Line 753 - DEFAULT STAT CALCULATIONS (BEST FIT TRENDS):
   If the user does not customize their statistics (i.e. accuracy affecting the likelihood of an attack succeeding, dodge affecting the    likelihood of an opponent's attack missing, armor affecting damage calculations, etc.), a regression algorithm will determine default    ones based on inputted class and level. This was created using a large pool of data from game wikipedia sources (taken with
   permission), and while not completely accurate, it does provide a useful model with minimal margin of error.
   
  Line 1122 - REPLACE APPLICABLE STATS WITH USER INPUTS:
   If any statistics were entered by the user, they will be prioritized over ones calculated via the default algorithm.
   
  Line 1200 - INITIALIZE ENEMY NAME, CLASS, & LEVEL:
   See Line 735 note.
   
  Line 1217 - ENEMY DEFAULT STAT CALCULATIONS:
   See Line 753 note.
   
  Line 1582 - REPLACE APPLICABLE ENEMY STATS WITH USER INPUTS:
   See line 1122 note.
   
  Line 1660 - CONFIRMATION MESSAGES:
   Alterts the user to ensure statistics fields are completed as desired before running any combat simulations. Returns if the user does    not confirm.
   
  Line 1686 - EPIC ABILITY RANKS:
   Creates variables for epic abilities depending on the images the user toggled to.
   
  Line 1818 - ENEMY EPIC ABILITY RANKS:
   See Line 1686 note.
   
  Line 1950 - OTHER VARIABLES:
   Important variables for running option analysis after completing the simulations.
   
  Line 1969 - WEAPON TYPE:
   Used to determine what epic abilities can respond to each other (i.e. so an enemy attacking at a distance is not attacked with a        close-range ability).
   
  Line 1984 - ENEMY WEAPON TYPE:
   See Line 1969 note.
   
  Line 1999 - POWER FUNCTIONS:
   "Powers" are special attacks that have added functionality, such as altering the value of a statistic to gain an advantage or giving    the enemy a disadvantage. Implements major powers that have substantial impact on combat.
   
  Line 2255 - UNITS WITH AVAILABLE POWERS:
    If the user enters the name of an in-game unit who possesses a power, a prompt will appear asking whether or not to use it. Some         units have multiple powers, though only one can be used per instance of combat.
    
  Line 2302 - COMBAT SIMULATOR:
    The main algorithm of the code; the player's unit will attack the enemy unit, and any epic abilities will trigger. The "health" of       both parties are kept track of, and combat will end either when either health value reaches zero or the chain of attacks comes to an     end. Prints out a sample simulation when requested by the user.
    
  Line 5226 - OPTION ANALYSIS:
    Loops the combat algorithm, with the amount of iterations dependant on the number of options available (this is determined by which     epic abilities the user selects, providing benefits from alternatives other than a standard attack, such as disengaging, approaching     with another unit, etc. Keeps track of number of "successful" and "unsuccessful" simulations, rated by comparing the proportion of       health each party has remaining at the end of an instance of combat.  
    
  Line 5287 - CALCULATE RESPONSE:
    The option with the highest success rate will be determined, and if it is greater than or equal to 50%, it will be recommended to       the user. Other alternatives are included with their probability of success as well. The user will be informed if all options are       likely to fail (i.e. probability of success is less than 50%) and that engaging in combat is not recommended.
    
  Line 5340 - NOTES:
    Specifications on the nature of calculations, rules of combat, and important assumptions made in the combat algorithm.
