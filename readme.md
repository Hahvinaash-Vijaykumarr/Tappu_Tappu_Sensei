[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/5YTzVbxp)
## 50.002 1D Project Group 14

Hahvinaash Vijaykumarr      1006631  
Thirunavukkarasu Harshini   1007009  
Shrinidhi Arul Prakasam     1007007  
Harsh Hareendran Kalinkeel  1007116  
Sushmitha Elangovan         1007050  
Pea Jun Hao Darren          1006859  

### Project

The game is designed as a readaptation of the idea of Taiko no Tatsujin, where players must follow the falling musical notes in the right sequence. This aims to train players on their hand-eye coordination, and also what notes correspond to what sound, like C, D, E, etc. Players would be required to use a drumstick to hit the corresponding notes whenever the falling musical notes passes below a certain line to gain points. If they hit a note at the wrong time, they would lose a point. A 16 x 16 ws2812b LED display is used to display the falling notes.

### User Manual

1. Players can select a song from 2 different songs using 2 song selection buttons.
2. Players can select a speed (fast or slow) using 2 speed selection buttons.
3. Press 'OK' button to begin the game.
4. Game starts and player has to hit the corresponding notes when it reaches the bottom of the LED.
5. At the end of the game, press 'OK' to play again.

### Prototype
![Protoype design](https://github.com/50002-computation-structures/1d-project-14/blob/master/images/Prototype.jpg)

### ALU

#### Manual mode
The ALU begins in manual mode, where the io_dip[2] and io_dip[1] are used to generate a 16 bit number. After setting the 16 bit number, io_button[0] and io_button[1] is used to assign the value to A and B respectively. io_dip[0][5:0] is used to set the ALUFN signal, where different functions are represented in the table below, then io_button[2] is used to store the value of ALUFN.

The io_led[1] and io_led[0] would display the 16 bits output after A, B and ALUFN signal is inputted. io_led[2][2:0] would display z, v and n respectively, where z = 1 when output = 0, v = 1 if there is overflow and n = 1 when the 16th bit = 1.

#### Auto-testing mode
From the Manual mode, users can flip the io_dip[0][7] switch to 1 to activate/deactivate the auto-tester. To begin, press io_button[3] to start the auto-tester.  

It would iterate through 50 test cases of different functions and display the 16 bit output on io_led[1] and io_led[0]. The test cases are labelled  using the 3 rightmost 7-segment led "XX.Y", where XX is the hex value of the function and Y is the #test_case_number of the function XX.  

For simulating error cases, io_dip[0][6] can be flipped to 1 to inverse the least significant bit, resulting in the wrong output. This will stop the test cases from running further until io_dip[0][6] is flipped back to 0, before continuing to run the following test cases. io_led[2][7] will be lit if the test case is correct and unlit if it is wrong. The leftmost 7-segment LED will also display "J" if the test case is correct and "X" if the test case is wrong.

After running all test cases, "...." will be displayed on the 7-segment led and to restart the auto-tester, io_dip[0][6] can be flipped to return to the first test case.

#### Functionality for proposed multiplication game
From Manual and Auto-testing mode, users can press io_button[4] activate the game function and io_button[2] to return to Manual mode.

Users are posed with multiplication questions in the form of "XX.YY" on the 7-segment led, where XX is the first number and YY is the second number. Users would have to enter the answer in binary using io_dip[2] and io_dip[1] to generate a 16 bit answer. Users can submit their answer by pressing io_button[0]. If the user submits a wrong answer, he will be expected to provide the correct answer before moving on to the next question.  

After finishing all the questions, "g.o.o.d." will be displayed on the 7-segment LED.

#### ALU Reference
io_button[0] -> top button   
io_button[1] -> centre button  
io_button[2] -> down button            
io_button[3] -> left button  
io_button[4] -> right button

![Picture](https://github.com/50002-computation-structures/1d-project-14/assets/122805747/929f3786-eac3-42f6-b950-190cca37507e)
