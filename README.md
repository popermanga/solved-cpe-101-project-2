Download Link: https://assignmentchef.com/product/solved-cpe-101-project-2
<br>
<strong>Moonlander – Lunar Lander Simulator</strong>

<strong>Objectives: </strong>




<ul>

 <li>Practice on making decisions in python.</li>

 <li>To Practice writing loops in python.</li>

 <li>To experience some of the issues and subtleties involved with solving problems that include repetitive tasks.</li>

 <li>To practice writing and calling functions that you have written.</li>

 <li>To practice testing your code.</li>

 <li>To appreciate the benefits of modular development.</li>

</ul>




<strong>Required File Header:</strong>




All students are required to have the following header comment at the top of their source files. Note that the stuff to the right of the colon in red is information for an imaginary example student. (Please put YOUR appropriate information. Also, your header comment is not expected to have red text.) All program files require this header.




# Project 2 – Moonlander

#

# Name: Your Name

# Instructor: S. Einakian

# Section: Your Section

<strong> </strong>

<strong>Resources: </strong>




<ul>

 <li>Your instructor, via office hours, email, etc.</li>

 <li>Free tutoring Sunday-Thursday, 7-9 PM, 14-302</li>

 <li>Your TA</li>

</ul>




<ul>

 <li><strong>Given Codes and Files: </strong>

  <ul>

   <li>List of functions that you need to implement are in the landerFuncs.py. o Unit Test for all implemented functions, funcs_tests.py.</li>

   <li>A starting tester file for your program I/O functions, ioTests.py.</li>

   <li>Two executable file moonlanderInst and ioInst, which you can run to find out how your program should work. (Same as skaterInst in Project 1)</li>

  </ul></li>

</ul>




Download these files from PolyLearn to your directory.

<strong>Ground Rules:</strong>

<ul>

 <li>You may not discuss this project with anyone other than your instructor or the tutors.</li>

 <li>Your program must not use any global data (that is, all data must be declared within some function).</li>

 <li>Your program must implement the required functions as specified, including function names and input parameters.</li>

 <li>Your program must use the required functions appropriately. That is, it’s not enough to create the functions, you must also use them.</li>

 <li>Your program must mimic the sample program’s behavior <strong><em>exactly </em></strong>and in all cases.</li>

</ul>




<strong>Description:</strong>




You are part of a team writing a program that simulates landing the Lunar Module (LM) from the Apollo space program on the moon. The simulation picks up when the retrorockets cut off and the pilot/astronaut takes over control of the LM. The user of the simulator specifies the initial amount of fuel and initial altitude. The LM starts at a user-specified altitude with an initial velocity of zero meters per second and has a user-specified amount of fuel on board.




The manual thrusters are off and the LM is in free-fall — meaning that lunar gravity is causing the LM to accelerate toward the surface according to the gravitational constant for the moon. The pilot can control the rate of descent using the thrusters of the LM. The thrusters are controlled by entering integer values from 0 to 9 which represent the rate of fuel flow. A value of 5 maintains the current velocity, 0 means free-fall, 9 means maximum thrust — all other values are a variation of those possibilities and can be calculated with an equation that is provided below.




To make things interesting (and to reflect reality) the LM has a limited amount of fuel — if you run out of fuel before touching down you have lost control of the LM and it freefalls to the surface.  The goal is to land the LM on the surface with a velocity between 0 and -1 meters per second, inclusive, using the least amount of fuel possible. A landing velocity between -1 meters per second and -10 meters per second (exclusive) means you survive but the LM is damaged and will not be able to leave the surface of the moon — you will be able to enjoy the surface of the moon as long as your oxygen lasts but you will not leave the moon alive. Velocities faster than (less than) or equal to -10 meters per second mean the LM sustains severe damage and you die immediately.




The initial conditions of 1300 meters altitude and 500 liters of fuel were used in the original, and were chosen so that an optimal landing should use approximately 300 liters of fuel. It’s a considerable challenge at first, and you may enjoy trying it.




FYI: This program is modeled after a version that was popular on HP-28S programmable calculators in the 1970s. It is interesting to note that the desktop computers you are working on cost about the same amount (unadjusted for inflation) as the calculators did but are quite a bit more powerful (more memory, storage, computational power, not to mention more sophisticated display, keyboard, mouse, et cetera). This program took approximately 90 seconds to load on the calculator — virtually instantaneous on the machines you are running on today. Credits to Dick Nungester of HP for the provided equations.

<strong>Before you begin, take a look at the sample solution program by copying it to your account and running it. First log on to the Unix servers and then navigate to the directory where you would like to copy the file through PolyLearn. </strong><strong>./moonlanderInst  </strong>

Start at 1300 meters with 200 liters of fuel, and see how you do.




<strong>The project has two parts:  </strong>

<strong> </strong>

<ol>

 <li>In Part 1, your manager asks you to write a group of functions that will eventually be used to complete the finished Moonlander Project. Your task for Part 1 is to write and <strong>test </strong>the functions you’ve been asked to implement. Your function definitions will be written in their own file called <strong>py</strong>. This file has already been started for you. The functions you write will fall into two categories, functions that calculate and functions that do I/O (input/output). Test your functions that calculate using the unit testing tools that we have been using all quarter in a file called <strong>funcs_tests.py</strong>. This file has also already been started for you. You will test your functions that do I/O using a file that has already been <em>completely </em>written for you called <strong>ioTests.py</strong>.</li>

</ol>




<ol start="2">

 <li>In Part 2 (start this after you have written and <em>tested </em>your functions), your boss is so impressed with your work on the functions that you will be asked to complete the</li>

</ol>

Moonlander Project. Believe it or not, completing Part 1 of the project is the majority of the work. Developing your code this way allows you to test your functions before moving on to code the main game loop. <strong>NOTE: </strong>The ioTests.py from Part 1 does <strong>not </strong>do moon landings — all it does is to test that your functions exist, work correctly, and they can be called without crashing the program. Moon landings have to wait for Part 2.




<h1>Part 1: Functions</h1>

<ul>

 <li>You must implement the following functions in a file called landerFuncs.py. I have started this file for you. It contains “stubs” for all the functions. That is, the functions are all in the file, but are <em>empty </em>except for the keyword pass. Remove the word pass as you implement a function. This way, the entire file can be run and tested incrementally as you start to complete the individual functions.</li>

</ul>




<ul>

 <li>Note that input and output occur only in the functions which specifically have that job. The functions that calculate <em>do not </em>do I/O, and vice versa.</li>

</ul>




<ul>

 <li>References to <strong>tp0</strong> indicate the immediately previous time period (1 second ago) and references to <strong>tp1</strong> indicate the current time period.</li>

</ul>




<strong>CAUTION</strong>: Pay attention to the data types involved in these equations and be sure you are not losing any necessary precision due to Python’s rules for dealing with mixed-type expressions.

<strong> </strong>

<strong>NOTE</strong>: The “<strong>tp</strong>” (time period) subscripts are intended to show how the state at each new second of time (tp1) depends on the state at the current second (tp0) plus the newly entered rate of fuel consumption (marked as tp1). These formulas must be re-evaluated for every second of the simulation.







<strong>Functions that perform I/O:  </strong>




<ol>

 <li><strong>showWelcome() </strong></li>

</ol>

Display the welcome message. See the sample program for the exact text.




<ol start="2">

 <li><strong>getFuel() </strong></li>

</ol>

This function has <em>no parameters </em>and a <em>return type of int. </em>This function must prompt a user for positive integer value and return it. It must display an error message if the user enters a negative or zero value and re-prompt for a valid value. See the sample program for the exact text of the prompt and error message.




<ol start="3">

 <li><strong>getAltitude() </strong></li>

</ol>

This function must prompt a user for a real value between 1 and 9999, inclusive. It must display an error message if the user enters a value outside this range and re-prompt for a valid value. See the sample program for the exact text of the prompt and any error message(s).




<ol start="4">

 <li><strong>displayLMState(elapsedTime, altitude, velocity, fuelAmount, fuelRate) </strong></li>

</ol>

This function must display the state of the LM as indicated by the parameters. The parameters are:

<ul>

 <li>an int representing the elapsed time the LM has been flown;</li>

 <li>a double representing the LM’s altitude;</li>

 <li>a double representing the LM’s velocity; 4) an int representing the amount of fuel on the LM;  5) an int representing the current rate of fuel usage.</li>

</ul>

See the sample program for the exact text and format of the display.




<ol start="5">

 <li><strong>getFuelRate(currentFuel) </strong></li>

</ol>

I/O – The parameter is an int representing the current amount of fuel in the LM. The function prompts the user for an integer value and makes sure it is between 0 and 9, inclusive. It must display an error message if the user enters a value outside this range and re-prompt for a valid value. <em>The function must return the lesser of the user-entered value or the amount of fuel remaining on the LM (value passed in as a parameter). The user cannot use more fuel than is left on the lunar lander! </em>See the sample program for the exact text and formatting of the prompt and any error message(s).




<ol start="6">

 <li><strong>dispalyLMLandingStatus(velocity) </strong></li>

</ol>

This function, as its name implies, displays the status of the LM upon landing. There are three possible outputs depending of the velocity of the LM at landing, they are:

Status at landing – The eagle has landed!

Status at landing – Enjoy your oxygen while it lasts!

Status at landing – Ouch – that hurt!

<ol>

 <li>Print the first message if the final velocity is between 0 and -1 meters per second, inclusive.</li>

 <li>Print the second message if the final velocity is between -1 and -10 meters per second, exclusive</li>

 <li>Print the third message if the final velocity is &lt;= -10 meters per second See the sample program for the exact text and formatting.</li>

</ol>




<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong>Functions that Calculate: </strong>

<ol>

 <li><strong>updateAcceleration(gravity, fuelRate) </strong>The parameters are:

  <ul>

   <li>a float representing the gravitational constant for the moon (i.e., 1.62).</li>

   <li>an int representing the current rate of fuel usage</li>

  </ul></li>

</ol>

The function calculates and returns the acceleration using the formula  accelerationtp1 = gravitational constant * ((rate of fuel consumptiontp1 / 5) – 1)




<ol start="2">

 <li><strong>updateAltitude(altitude, velocity, acceleration) </strong>The parameters are:</li>

</ol>

1) a double representing the current altitude;  2) a double representing the current velocity;  3) a double representing the current acceleration.

The function calculates and returns the new altitude based on the provided inputs and the formula

altitudetp1 = altitudetp0 + velocitytp0 + (accelerationtp1 / 2)




<em>Remember, however, that the surface of the moon stubbornly limits the altitude to non-negative values, and your code must do the same</em>.




<ol start="3">

 <li><strong> updateVelocity(velocity, acceleration) </strong>The parameters are:</li>

</ol>

1) a double representing the current velocity;  2) a double representing the current acceleration.

The function calculates and returns the new velocity based on the provided inputs and the formula  velocitytp1 = velocitytp0 + accelerationtp1




<ol start="4">

 <li><strong> updateFuel(fuel, fuelRate) </strong>The parameters are:</li>

</ol>

1) an int representing the current amount of fuel on the LM;  2) an int representing the current rate of fuel usage.

The function calculates the remaining fuel. Note: This is a trivial function as long as your getFuelRate function behaves correctly.  fueltp1 = fueltp0 – rate of fuel consumptiontp1

<strong> </strong>

<h1>Part 2: Moonlander Simulation</h1>




Do NOT begin work on the actual Moonlander simulator yet. Instead, funcs_tests.py and ioTests.py will solely be responsible for testing the functions you have written. You want to assure that they are perfect before you hand them over to your manager (me).

<strong> </strong>

<h1>Testing (READ CAREFULLY)</h1>




This part will describe in detail how to test your moonlander functions that you have written. You are responsible for ensuring they are completely correct before handing them in to your manager.

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong>Testing your functions that calculate: </strong>




Test these functions using the unit testing techniques we have been using all quarter. You must provide at least two tests per function. Each test should be written in its own testing function. Be sure give your tests descriptive function names indicating which function is being tested. I provide you with a starting funcs_tests.py file. Add additional tests to this file.

<strong> </strong>

<strong>Testing your functions that do Input/Output: </strong>




Testing functions that do I/O is a little trickier. To assist you, I have written a file called ioTests.py that calls each of your I/O functions in order. Do NOT change this file. I also provide you with an instructor executable called ioInst that calls the same functions in the same order with the same input parameters. Play with the instructor executable until you understand how each of the I/O functions should behave.

Additionally, I provide you with one sample input file (in1) to test the output from your ioTests.py versus the output from my instructor executable (much the same way you tested your skater.py program). To get the instructor executable and the input file copy them from PolyLearn.




<strong>To test your I/O functions using ioTests.py follow these steps:  </strong>

<ul>

 <li>Run the instructor executable until you are sure familiar with how the code should behave. Then run your code by typing the command below. Be sure your landerFuncs.py file is in the same directory.</li>

</ul>




<strong>python3 ioTests.py  </strong>




If your version does not behave the same as the instructor, modify the appropriate function in landerFuncs.py and test some more. Once you are confident that your code behaves just like the instructor version, move on to step two.

<ul>

 <li>Run the ioInst executable with the in1 input file and save the results in a file called inst1 (short for instructor test 1):</li>

</ul>




<strong>./ioInst &lt; in1 &gt; inst1  </strong>

<ul>

 <li>Run the ioTests.py module with the in1 test file and save the results in a file called my1:</li>

</ul>




<strong>python3 ioTests.py &lt; in1 &gt; my1  </strong>

<strong> </strong>

<ul>

 <li>Diff the output of both executables to see if they match:</li>

</ul>




<strong>diff my1 inst1  </strong>




Be sure to make your own additional input files to tests your I/O functions. I recommend testing with invalid input for initial altitude and initial fuel amount. For example, try entering a negative number for the initial altitude. (You need NOT test with input other than integers.)




<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<h1>Part 2: Moonlander Simulation</h1>

<ul>

 <li>Begin this part with your fully tested <strong>py</strong> file.</li>

</ul>




<ul>

 <li>Now you must write a <strong>py</strong> that runs the full lunar lander simulation. I recommend that you run the instructor version of the fully functioning program <strong>moonlanderInst</strong> until you are familiar with how the program behaves.</li>

</ul>




<ul>

 <li>In your moonlander.py, you must code a simulator-loop that advances the LM from time period zero to landing, and calls to the functions of Part 1 along with minimal code to “glue” it together. One of the challenges in this project will be the understanding of the overall structure that has been provided to you. Don’t hesitate to ask your instructor questions early in the process to help make sure you understand what you are supposed to be doing. You will probably go down some dead ends and need to remove and/or rewrite code. This is part of the process so enjoy the ride!</li>

</ul>




<ul>

 <li>You do <em>not </em>need to write nested loops in this part. Nor do you need to write a loop followed by another loop. The problem may be solved in both of those ways, but it can be solved more simply by writing a single loop.</li>

</ul>




<h1>Testing</h1>

Diff your output versus the <strong>moonlanderInst</strong> executable as you have with your other projects. I provide you with three sample test cases (moon1, moon2, moon3). Be sure to test with some of your own. My “final” tester has 8 test cases.

<strong> </strong>

<h1>Grading</h1>

Your program will be graded based on correct implementation of the moonlander functions in landerFuncs.py, my function tests passed, your function tests in funcs_tests.py, finished moonlander simulator tests passed with your moonlander.py, code style, and adherence to the specification.




<strong>Submission: </strong>




Submit the following files:  landerFuncs.py

<ul>

 <li>py</li>

 <li>py to the PolyLearn</li>

</ul>