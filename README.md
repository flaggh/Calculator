# Calculator
CS 480 - Lab3

## Overview
This program is a text based program that allows users to type in an equation and then will return the answer to the equation if the equation is a valid one.

## Files
There are four source files in this project.
They are BST.java, Calculator.java, Main.java, and Command.java.
Both BST and Calculator are for constructing and using the data structures that are made in them.
Main was the original driver class that was being used to use and test my program but because of errors that were occuring I made a new driver class.
This is why we have the Command file which for users is what should be used.
For java compiling in the windows command prompt all of the before mentioned files and there contents are copied onto the Command file.

## How To Use
To use the Command file and therfore the program itself, users should first locate themselves to the correct directory.
Once there, users can then compile the file by entering the command "javac Command.java".
Once the program has been compiled the program can then be run using the command "java Command.java".
After this command the program will begin running and asking the user for math equations.
To quit the program users can type "quit", which the program does tell users.

## input
The program requires users to type in the equation using their keyboard. 
The equation is read in as a string but it can include numbers and some operators.
The operators that can be included are +, -, *, /, ^, sin, cos, tan, cot, ln, and log10.
Like with a calculator the trig and log functions must be followed by an opening paretheses and a closing parentheses. Example: ln(2*2).
Minus signs can be used as both binary and urnary operator. Example: -1 or 1-1.
If the given equation has parentheses in it then it must have them correctly formatted like, (), in order for the equation to be read correctly.
Like with an actual calculator numbers cannot be placed before or after a parentheses without an operator in between them. Example: 1(-1).
For multiplication it needs to entered like a calculator. Example: 1*(-1).
This calculator only handles log10 and no other log bases.
If an incorrect number of parentheses are entered or if parentheses are used incorrectly the equation will be called invalid and the code will ask for another equation.
If a word or letter is entered into the equation and is not part of the valid trig or log expressions then the equation will be called invalid and the code will ask for another equation.
If spaces are entered in between operators or operands then the program will auto-correct this and solve the equation like they weren't there.
Users may enter an equal sign into their equation if they want to. 
The program will recognize the equation either way but the equal sign must be at the end of the equation and there can be nothing to the right of it.


## output
If the user given equation is invalid then a message will appear stating this.
Otherwise if the equation is valid then the program will proceed by printing a message that 'user input' = 'answer'. Example: 1+1 = 2.0
The answer output of the equation will always be returned as a double even if only integers were used.
The output will always be in a simplified answer. Meaning only doubles, either positive or negative and if negative will only have one negative sign.
When handeling a negative minus a negative the answer will be printed with multiple zeroes and a final number depending on the two numbers be substracted from eachother.
If a number greater than 10^8 is the answer to the equation then the printed answer will be something followed by E to the whatever power. Example: 1.11111111111E10.

## Node class
This class is for the data object that will be used in BST object.
It holds a priority and value field which will represent the order of operations and operand or operator in the equation respectively.
The Node class has no methods because both of its fields are public and can be manipulated whenever.

## BST class
This class is a Binary tree like object which uses the Node class as its object type.
Unlike what may be assumed because of its name BST is not a binary search tree it is just a binary tree.
This object has three fields a current Node, a left BST, and a right BST.
This class was created so that it would be easier to solve the equation using order of operation which can be accomplished using a postOrder like treaversal.
The methods in this class are getLeft, getRight, getCurrent, add, toString, setLeft, and setRight.

### getLeft and getRight
Like the names suggest these to methods return the left and right BST children respectively.

### getCurrent
returns the current Node of the BST

### add
Takes in a root BST as a paremeter and then adds it to the object depeding one the root's current priority.
if the main BST is null then the root becomes the main BST.
Otherwise root is added like normal.
A lower priority moves the root further down the tree, while a higher or equal priority will move everything else down and have root take its place.

### toString
returns the BST object as a string.
This should look like a math equation without any parentheses.
This doesn't have any use in the final program but was helpful for testing issues that were occuring.

### setLeft and setRight
like the names suggest these two methods place the given BST as the left or right child respectively.
they also return the new left or right node respectively.

## Calculator class
This is the main class that performs the bulk of my program.
It has four methods, toBinaryTree, simplify, solve, and checkValidity.

### toBinaryTree
This method takes in the equation as a string parameter.
Using this string the method then performs a forloop going through each character in the string.
as it goes through the string it finds each part of the equation and sperates these parts into Node objects for the BST object and then inserts them where needed.
The parts of the equation are split up by numbers, parentheses, and operators.
When they are placed in Nodes the Nodes are given two values that are a priority representing and equations order of operations and another value representing the number or operator.
The higher the priority the higher later in the order of operations that node is.
For example, + and - are 4, * and / are 3, ^ is 2, trig and log are 1, and numbers are 0.
Binary minus signs are interpreted as a part of a number an therefore do not have a priority until the number itself is given one.
parentheses and everything in them are simplified using the simplify method.
After all of the equation has been read through the method then returns the equation as a BST object. (read more about BST objects on line)

### simplify
This method takes in a string that represents part of the eqation as a parameter and reads through it with a forloop.
The main use of this method is to solve parts of the original equation that are in parentheses.
When this equation finds a closing parethese it will return a string of everything in the parenthese pair after it has been solved using the solve and toBinary method followed by the rest of the equation.
If another opening parethese has been found then once again the simplify method will be called using the rest of the equation as the paremeter.
If the forloop reaches the end of the equation without seeing a closing parenthese then it will throw an exception because this means that the equation has an odd pair of matching parentheses.

### solve
This method takes in a BST object as a paremeter and solves the equation the it represents.
This is done by reading the value of the given root's current Node and determining what its value is.
If its a number then that number is returned
If the value is an operator or other function then it performs that mathmatical operation on the given root's children or child depending on the root.
If the root is null or if the value is not a number or one of the accepted operators then an exception is thrown since this means that the equation is invalid.
The solve method will also throw an exception if the equation tries to divide by 0.

### checkValidity
This method uses the given equation as a parameter and checks to make sure that parentheses are used correctly for trig and log functions and parentheses are paired correctly.
It will also throw an Exception if numbers are placed outside and next to parentheses. Example: 1(10).
















