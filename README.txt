VERSION 1.0

Play:
Open the "ASCII Adventure Manager" executable within.
This should upon up your terminal!

You can input numbers or the name of a choice to make decisions!


+============================================================================+


Builder:
Every line in ASCII Adventure Manager file represents a Screen in the game. The starting screen of the game must ALWAYS be labeled "start":

Screens are composed of four sections:
-Name
-Art
-Text
-Choices

these files are separated by the special character "¦" as such:
Name¦Art¦Text¦Choices

All of these elements are represented with text only. Let's go through each to see how it works:

**Name**
The name of a screen is how other screens reference it and allow you to make choices from one screen to another.
End screens are unique in that they require a special tag at the very start. by adding an "@" character to the front of a screen's name then it declares this screen as the end of the adventure!

@end¦ART¦TEXT¦[LEAVE BLANK HERE + NO BRACKETS]


**Art**
The art is exactly that! ASCII art (though technically I believe you can use unicode characters as well)
Since everything is stored on one line you have to use the escape code "\n" any time you want to start a new line of your art:

Input: KEY¦&&&¦TEXT¦CHOICES

Art Output: &&& 

Input: KEY¦&\n&\n&¦TEXT¦CHOICES

Art Output: &
            &
            & 


**Text**
Text is similar to art, but its just designed to be textual!
You can break up lines of text just like you can lines of art using "\n"
To make a full line-break use "\n\n"

Input: KEY¦ART¦Test 1,2,3¦CHOICES

Text Output: Test 1,2,3

Input: KEY¦ART¦Test \n1,\n2,\n3¦CHOICES

Text Output: Test
             1,
             2,
             3


**Choices**
Choices are what allow you to navigate through the game. They are made of two parts: a description and a key
A description is simply the decision text that appears when you run your game, and a key is the pointer to the next screen!

Input: KEY¦ART¦TEXT¦Go to Room A#roomA

Choices Output: 1. Go to Room A



Choices are split from key to decision with "#" and you can add a new decision with the "&" character following a key!

Input: KEY¦ART¦TEXT¦Go to Room A#roomA&Go to Room B#roomB

Choices Output: 1. Go to Room A
                2. Go to Room B

IMPORTANT NOTE!!! MAKE SURE THAT YOUR KEY (roomA and roomB in these examples POINTS TO THE NAME OF ANOTHER SCREEN!!!)
EX:
start¦:)¦You're in a room with two doors.¦Go to Room A#roomA&Go to Room B#room
roomA¦:D¦sYou're in room A!¦CHOICESGOHERE
roomB¦:/¦You're in room B!¦CHOICESGOHERE

