Download Link: https://assignmentchef.com/product/solved-comp90041-project-c
<br>



<h1>1        Mandatory Assignment</h1>

<h2>1.1       Introduction</h2>

The aim of this project is to add some more advanced features to the system developed in Project B. The features to be added are:

<ul>

 <li>Sort the players with more specific rules</li>

 <li>Handling of invalid input via Exceptions</li>

 <li>Write (read) the game statistics into (from) a file, i.e., one which is stored on the hard disk between executions of Nimsys</li>

 <li>A new type of player – an AI (Artificial Intelligence) player, whose moves are automatically determined by the computer rather than a game user</li>

</ul>

The system should still operate as specified in Project B, but with additional functionality, due to the addition of the aforementioned features. Thus, it is advised that you use your Project B solution as a starting point for implementing Project C.

<strong>Knowledge Coverage</strong>

<ul>

 <li>Exceptions</li>

 <li>File I/O operations</li>

 <li>Polymorphism, you may use either inheritance or interface to design the AI player in addition to the human player</li>

</ul>

<h2>1.2       Requirements</h2>

In the following description, all command line displays are put in a box. This is only for easier understanding the format. <strong>The box should NOT be printed out by your program, only the contents in the box should be printed. </strong>The command prompt is illustrated below:

<strong>1.2.1           Sort the players with more specific rules</strong>

In Project B, when two players had the same winning ratio, you were required to sort the players by username in either ascending alphabetical order or descending alphabetical order.

In this project, <strong>the ranking should still be based on the winning ratio first (i.e., the percentage of games won)</strong>. If there is a tie (two or more players with the same winning ratio), sort all players by their <strong>username </strong>in <strong>ONLY </strong>ascending alphabetical order.

Example Execution:

Suppose we have three players in (username, First Name, Last Name) format as follow: (LS, Luke, Skywalker), (HS, Han, Solo), (DV, Darth, Vader). They all have the same wining ratio.

<ol>

 <li>rank all users (default, i.e., descending order)</li>

</ol>

$rankings

0% | 00 games | Darth Vader

0% | 00 games | Han Solo

0% | 00 games | Luke Skywalker

$

<ol start="2">

 <li>rank all users in descending order</li>

</ol>

$rankings desc

0% | 00 games | Darth Vader

0% | 00 games | Han Solo

0% | 00 games | Luke Skywalker

$

<ol start="3">

 <li>rank all users in ascending order</li>

</ol>

$rankings asc

0% | 00 games | Darth Vader

0% | 00 games | Han Solo

0% | 00 games | Luke Skywalker

$

<strong>1.2.2           Invalid input handling via Exceptions</strong>

The system should check inputs for validity. For this task, you will not be required to implement exception handling for all possible invalid inputs – just a subset of them. The range of potential invalid inputs you are <strong>required </strong>to address by Exceptions (<strong>not </strong>via if-then statements) are listed below, along with the required behaviour of your program. Note that some of this input checking was also a requirement in Project B. Where this is the case, you need to modify your code so that the invalid input is handled via

Exceptions. The rest of the invalid input handling cases described in Project B do <strong>not </strong>need modification.

<ul>

 <li>Invalid command – The user enters a command which is not a valid Nimsys command. Here, invalid command suggests the input command is not among the specified commands, i.e., addplayer, editplayer, removeplayer, displayplayerresetstats, rankings, startgame, and exit. Example:</li>

</ul>

$createplayer lskywalker,Skywalker,Luke ‘createplayer’ is not a valid command.

$

<ul>

 <li>Invalid number of arguments – The user enters a valid Nimsys command, but does not provide the correct number of arguments. <strong>Note: </strong>You only need to check for insufficient number of arguments, and simply ignore any extra arguments, i.e., an insufficient argument count will generate an Exception while an excessive count will not. Different commands may have different number of arguments; your program should be able to check invalid number of arguments for <strong>all </strong> Example:</li>

</ul>

$addplayer lskywalker Incorrect number of arguments supplied to command.

$

<ul>

 <li>Invalid move (during a game) – The player tries to remove an invalid number of stones from the game. For the move to be valid, it must be an integer between 1 and N inclusive, where N is the minimum of the upper bound and the number of stones remaining. Any other inputs (e.g. fractions, decimals, non-numeric entries) should be detected as invalid. Example (Upper bound is 3 stones here):</li>

</ul>

7 stones left: * * * * * * * Han’s turn – remove how many?

4 Invalid move. You must remove between 1 and 3 stones.

7 stones left: * * * * * * * Han’s turn – remove how many?

After implementing the invalid input checking, the scenarios detailed above should <strong>not </strong>cause your program to crash – rather, your program should display the appropriate error message, and continue execution, as illustrated in the examples. You may assume that, aside from the cases explicitly mentioned above, the input to your program will be valid.

<strong>1.2.3         The player statistics file</strong>

In Project B, no program data are stored to disk, so all player data are lost when exiting the program. Here, the task is to store these data upon exiting the program, and to restore them on subsequent executions. Thus, if one was to exit your program (using the ‘exit’ command), and then start it again (by running ‘java Nimsys’ at the shell prompt), your program should be restored to the state it was in immediately before exiting. That is, it should be as if the program never exited at all.

This can be achieved by storing your player data in a file. At the beginning of the execution of your program, if the file exists, it is opened and its contents loaded into the system. When your program exits, this file will be updated with new/modified players, and then closed. If the file does not already exist, it will need to be created. It is up to you to decide the most appropriate format, e.g., text or binary, of this file. The name of the file should be <strong>players.dat</strong>, and it should be stored in the same directory as your program.

All player information should be stored, i.e., usernames, given / family names, and number of games played / won. Note that you do not need to store information about games in progress, since a game should never be in progress when the program exits properly, i.e., via the ‘exit’ command.

<strong>1.2.4            The AI (Artificial Intelligence) player</strong>

Here, a new type of player is to be added – an AI player. This player type should be controlled by the program, not by a human player. Aside from this, an AI player should be the same as a human player. That is, they should have all the same information associated with them (i.e., username, given/family names, and number of games played/won), and they should be stored in the system and appear in player lists/rankings, just as human players are. They should also be manipulated via all the same commands (with the exception of ‘addplayer’, since we now need to indicate whether we are adding a human player or an AI player to the system – see below).

The only difference between a human player and an AI player is in the way that they make a move. Instead of prompting for a move to be entered via standard input, the AI player should choose their own move, based on the state of the game. Thus, the only difference between a human player and an AI player should be in the method used to make a move. This suggests that the object-oriented principle of polymorphism should be applied here. Java offers polymorphism via two main avenues – inheritance, and interfaces. In this case, inheritance is the more appropriate choice. Conceptually speaking, we can think of human players and AI players as specialized players, i.e., a human player <em>is a </em>player, and an AI player <em>is a </em>player. They are identical in almost every way, and so most of their attributes and methods can be inherited – the only exception to this is the method used to make a move, which will need to be rewritten to act autonomously. You can add an abstract NimPlayer class, which will be used to represent the behaviour/attributes common to both Human and AI players. You can modify your original NimPlayer class used in Project B to be the new abstract NimPlayer class, and the human player class (NimHumanPlayer) and AI player class (NimAIPlayer) can extend the abstract player class.

Part of your mark for this project will be based on how well you apply polymorphism in your implementation of the human and the AI player, so it is important that you do use the principle of polymorphism in your design.

To allow for AI players to be added to the system, you should create a new command – ‘addaiplayer’. This command should operate in exactly the same way as ‘addplayer’ (refer to Project B for details). The only difference is that the resulting player is an AI player. Note that all other commands, e.g., ‘removeplayer’ and ‘editplayer’ should work for both human players and AI players. Provided below is an example of the use of the ‘addaiplayer’ command:

$addaiplayer artoo,D2,R2

$

In this task you need to modify the provided <strong>NimAIPlayer.java </strong>to implement the AI player functionality. Note that this file and <strong>Testable.java </strong>are provided to you for auto-testing the task of Section 2.6. You do NOT need to modify the advancedMove() method until you work on the task of Section 2.6.

After implementing the AI player, the ‘startgame’ command should allow games to be started with one or both players being AI players. The game should proceed exactly as per the Project B spec, except that when it comes to an AI player’s turn, there should be no reading of input from standard input – instead, the move should be immediately made by the AI. Provided below is an example execution. Here, Luke is a human player, and R2 D2 is an AI player:

$startgame 10,3,lskywalker,artoo

Initial stone count: 10

<table width="601">

 <tbody>

  <tr>

   <td width="601">Maximum stone removal: 3Player 1: Luke Skywalker Player 2: R2 D210 stones left: * * * * * * * * * *Luke’s turn – remove how many?37 stones left: * * * * * * * R2’s turn – remove how many?5 stones left: * * * * *Luke’s turn – remove how many?32 stones left: * *R2’s turn – remove how many?1 stones left: *Luke’s turn – remove how many?1Game OverR2 D2 wins!$</td>

  </tr>

 </tbody>

</table>

The move an AI player makes given a specific situation shall follow certain strategy such that the victory is guaranteed for the AI player if it holds the ability to win when the game commences. For details, please see the following section.

<h1>2        Checklist For Solution</h1>

<ul>

 <li><strong>Blank line and whitespace related issues </strong>Make sure in terms of format, your output matches with the expected output on the submission system.</li>

 <li><strong>File I/O mechanism related issues</strong></li>

</ul>

Make sure your program runs fine no matter whether the players.dat file exists.

Make sure every exit command triggers data to be written to the players.dat file.

<ul>

 <li><strong>Polymorphism related issues</strong></li>

</ul>

Make sure the AI player is implemented using inheritance mechanism.  Make sure you are leveraging the polymorphism to invoke the methods, i.e., using object declared in parent class to invoke methods overridden in the child class.

If attempting for bonus marks, make sure the advanced game is implemented using either inheritance or interface mechanism