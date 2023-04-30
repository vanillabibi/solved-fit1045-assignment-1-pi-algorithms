Download Link: https://assignmentchef.com/product/solved-fit1045-assignment-1-pi-algorithms
<br>
<h1>Task 1: Race to Pi</h1>

<table width="647">

 <tbody>

  <tr>

   <td width="647"><strong>Background</strong>The ratio of a circle’s circumference to its diameter, usually denoted by the Greek letter <em>π</em>, is an extremely important constant in mathematical computations. Unfortunately, the exact value of <em>π </em>cannot be stored explicitly in a computer, because it is <em>irrational</em>, i.e., it does not correspond to any ratio between two integer values. To help us out, there are many different ways to <em>approximate π</em>, most of which based on computing a finite prefix of an infinite sum or product. For instance:1.    via a solution to the <strong>basel </strong>problem:2.    derived from the <strong>taylor </strong>expansion of 13.    via the <strong>wallis </strong>algorithm:4.    via the <strong>spigot </strong>algorithm:Each of these sums (or the product in case of 3.) <em>converges </em>to the respective value on the left-hand-side of the equals sign. That is for every desired precision <em> &gt; </em>0, the absolute difference between the left-hand-side and the sum/product on the right-hand-side is guaranteed to be less than <em> </em>if a sufficient number of terms is computed. Thus, they are all valid ways to compute <em>π</em>. However, the <em>speed of convergence</em>, i.e., the number of terms that have to be computed to reach a desired precision is different for each method. (Note that in case of <em>wallis </em>and <em>spigot </em>every expression in parenthesis is considered one term; e.g., the first term of the wallis product equals <sup>4</sup><em>/</em>3, the third term of the spigot sum equals <sup>2</sup><em>/</em>15.) In this task, we will determine which of the above methods is preferable from this perspective.</td>

  </tr>

 </tbody>

</table>

<h2>Instructions</h2>

Create a Python module called pi.py. Within that module:

<ol>

 <li>Write four different functions for approximating <em>π </em>corresponding to the four different approaches listed above (the functions must be called basel, taylor, wallis, and spigot). Each of these functions must obey the following input/output specification:</li>

</ol>

<strong>Input</strong>: a float parameter precision which specifies the precision to which <em>π </em>should be calculated, i.e., the absolute difference of the approximation to the Python constant pi.

<strong>Output</strong>: two values (x,n) such that x is the first approximation to <em>π </em>with an absolute difference from pi of at most precision, and n is the number of terms of the sum/product that were computed in the process.

For example, if the input was 0<em>.</em>1, then the function should continue to compute terms of the series until the approximation x to <em>π </em>is less than 0<em>.</em>1 away from the Python constant pi (see more detailed examples below).

<ol>

 <li>Write another function called race(precision, algorithms) that can be used to compare the convergence speed of different approximation algorithms via the following input/output specification:</li>

</ol>

<strong>Input</strong>: a float parameter precision and a list of Python functions algorithms.

<strong>Output: </strong>a list of integer pairs [(i1, n1), (i2, n2),…, (ik,nk)] such that

<ul>

 <li>for each pair (i,n) in the list, n is the number of steps that the i-th algorithm takes to approximate <em>π </em>within the given precision</li>

 <li>the list is in <em>ascending order </em>with respect to the number of steps (the second number of the pair) with ties resolved arbitrarily.</li>

</ul>

Note that the input to race are functions and not strings. That is, in principle race can be used for evaluating arbitrary functions for approximating <em>π</em>, not only the four covered here.

<ol>

 <li>Write a function print results which takes as input the output of the function race and prints the results in a human readable format. Each line of the output should be “Algorithm i finished in n steps” where i is first element of the integer pair, and n is the second.</li>

</ol>

The only two import statements allowed in your module are from math import pi and from math import sqrt. Note that the subtasks can be solved independently and the given order (a, b, c) is only a recommendation.

<h2>Examples</h2>

<ol>

 <li>Calling wallis(0.2) returns (2.972154195011337, 4) as the result of approximating <em>π </em>with</li>

</ol>

2<em>.</em>

<ul>

 <li>terms</li>

</ul>

using 4 terms because pi – 2.972154195011337 &lt; 0.2 and non of the three prior wallis approximations satisfies this condition.

<ol>

 <li>Calling basel(0.1) returns (3.04936163598207, 10) as the result of approximating <em>π </em>with</li>

</ol>

3<em>.</em>

t

10 terms

using 10 terms because pi – 3.04936163598207 &lt; 0.1 and non of the nine prior basel approximations satisfies this condition.

<ol>

 <li>Calling taylor(0.2) returns (3.3396825396825403, 5) as the result of approximating <em>π </em>with</li>

</ol>

3<em>.</em>

5 terms

using 5 terms because pi – 3.3396825396825403 &lt; 0.2 and non of the four prior taylor approximations satisfies this condition.

<ol>

 <li>Calling spigot(0.1) returns (3.0476190476190474, 4) as the result of approximating <em>π </em>with</li>

</ol>

3<em>.</em>

<ul>

 <li>terms</li>

</ul>

using 4 terms because pi – 3.0476190476190474 &lt; 0.1 and non of the prior three spigot approximations satisfies this condition.

<ol>

 <li>Calling race(0.01, [taylor, wallis, basel]) returns [(2,78),(3,96),(1,100)] because functions taylor, basel, and wallis need 100, 96, and 78 terms, respectively, to approximate <em>π </em>within the required precision of 0<em>.</em></li>

 <li>Calling print results([(2,78),(3,96),(1,100)]) prints</li>

</ol>

Algorithm 2 finished in 78 steps

Algorithm 3 finished in 96 steps

Algorithm 1 finished in 100 steps

<h2>Marking Guide</h2>

Marks are given for the correct behaviour of the different functions:

<ul>

 <li>2 marks each for basel, taylor, wallis, and spigot</li>

 <li>3 marks for race</li>

 <li>1 mark for print results</li>

</ul>

All functions are assessed independently. For instance, even if function race does not always produce the correct output, function print results can still be marked as correct.

<h1>Task 2: Reversi</h1>

<table width="647">

 <tbody>

  <tr>

   <td colspan="5" width="647"><strong>Background</strong>Reversi is a game for two players (Black and White), which is played on a squared board of 8 rows/columns with stones that are white on one side and black on the other. In the beginning of the game, stones of Player 1 (B) and Player 2 (W) are placed in a cross arrangement at the center of the board as shown in Table <strong>??</strong>. Then the players take turns placing stones on empty fields on the board with their colour facing up according to the following rules:1.    All opponent’s stones that are enclosed in a straight line (horizontal, vertical, or diagonal) between the newly placed stone and another stone of the same color are flipped (see Table <strong>??</strong>).2.    A move is only valid if it turns at least one opponent’s stone.3.    If a player has no valid moves, their turn is skipped (see example in Table <strong>??</strong>).4.    The game ends when both players have no legal moves.When the game ends, each player scores points equal to the number of stones which have their colour face up, and the player with a higher score wins (draw if scores equal). In this task you will create a Python program that allows one or two players to play a game of Reversi.</td>

  </tr>

  <tr>

   <td width="50"> </td>

   <td width="272">


    <table width="210">

     <tbody>

      <tr>

       <td width="23">1</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">2</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">3</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">4</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">W</td>

       <td width="23">B</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">5</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">B</td>

       <td width="23">W</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">6</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">7</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">8</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23"> </td>

       <td width="23">a</td>

       <td width="23">b</td>

       <td width="23">c</td>

       <td width="23">d</td>

       <td width="23">e</td>

       <td width="23">f</td>

       <td width="23">g</td>

       <td width="23">h</td>

      </tr>

     </tbody>

    </table></td>

   <td colspan="2" width="272">


    <table width="210">

     <tbody>

      <tr>

       <td width="23">1</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">2</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">3</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">4</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">W</td>

       <td width="23">B</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">5</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">B</td>

       <td width="23">B</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">6</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">B</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">7</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">8</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23"> </td>

       <td width="23">a</td>

       <td width="23">b</td>

       <td width="23">c</td>

       <td width="23">d</td>

       <td width="23">e</td>

       <td width="23">f</td>

       <td width="23">g</td>

       <td width="23">h</td>

      </tr>

     </tbody>

    </table></td>

   <td width="54"> </td>

  </tr>

  <tr>

   <td width="0"> </td>

   <td colspan="2" width="334">Table 1: Initial board state at the beginning of game. Player 1 (B) has the first move.</td>

   <td width="308">Table 2: Board state after Player 1 (B) played “e6” as her first move.</td>

   <td width="4"> </td>

  </tr>

  <tr>

   <td width="50"> </td>

   <td width="272">


    <table width="210">

     <tbody>

      <tr>

       <td width="23">1</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">2</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">3</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">4</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">W</td>

       <td width="23">B</td>

       <td width="23">•</td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">5</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">B</td>

       <td width="23">B</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">6</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">•</td>

       <td width="23">B</td>

       <td width="23">•</td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">7</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">8</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23"> </td>

       <td width="23">a</td>

       <td width="23">b</td>

       <td width="23">c</td>

       <td width="23">d</td>

       <td width="23">e</td>

       <td width="23">f</td>

       <td width="23">g</td>

       <td width="23">h</td>

      </tr>

     </tbody>

    </table></td>

   <td colspan="2" width="272">


    <table width="210">

     <tbody>

      <tr>

       <td width="23">1</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">2</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">3</td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23">B</td>

      </tr>

      <tr>

       <td width="23">4</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23"> </td>

       <td width="23">B</td>

      </tr>

      <tr>

       <td width="23">5</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23">W</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23">B</td>

      </tr>

      <tr>

       <td width="23">6</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">7</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23">8</td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

       <td width="23"> </td>

      </tr>

      <tr>

       <td width="23"> </td>

       <td width="23">a</td>

       <td width="23">b</td>

       <td width="23">c</td>

       <td width="23">d</td>

       <td width="23">e</td>

       <td width="23">f</td>

       <td width="23">g</td>

       <td width="23">h</td>

      </tr>

     </tbody>

    </table></td>

   <td width="54"> </td>

  </tr>

  <tr>

   <td width="0"> </td>

   <td colspan="2" width="334">Table 3: Valid moves (indicated by •) for Player 2 (W) following “e6” from Player 1.</td>

   <td width="308">Table 4: Board state with no valid move for Player 2 (W), who, in case it is her turn, has to pass back to Player 1 (B), whose only valid move is “e1”.</td>

   <td width="4"> </td>

  </tr>

  <tr>

   <td width="0"></td>

   <td width="210"></td>

   <td width="102"></td>

   <td width="566"></td>

   <td width="0"></td>

  </tr>

 </tbody>

</table>

<h2>Instructions</h2>

Create a python module reversi.py. The only import statement allowed in your module is import copy. Your module must at least contain the nine functions described in the subtasks below, but you are allowed, and in fact, encouraged, to implement additional functions as you deem appropriate.

<ol start="2">

 <li>Create three functions new board(), print board(board), and score(board) that represent the basic elements of Reversi as follows. The function new board() takes no parameters and returns a fresh board configuration representing the Reversi starting position. The other two functions each take as input a board configuration. The function score(board) returns as output a pair of integers (s1, s2) where s1 represents the number of stones of Player 1 in the given board configuration and s2 represents the number of stones of Player 2. The function print board(board) has no return value but prints the given board configuration in human-readable form to the console (in particular, all rows of the board must be printed in separate lines of the console and labelled by their names 1, 2, …and all columns must be properly aligned and labelled by their names a, b, …— similar to the illustrations above). For these and all other functions of this task, a <strong>board configuration </strong>must be represented as a list of lists in the following way:

  <ul>

   <li>A board configuration is a list of length 8, the elements of which represent the rows of the board from top to bottom: the first element represents the topmost row of the board, row 1, the second represents row 2, etc..</li>

   <li>Each row, i.e., each element of a list representing a board configuration, is also a list of length 8. These inner lists represent the rows of the board from left to right: the first element represents the field in the leftmost column, Column A, the second element represents the field in second column, Column B, etc.</li>

   <li>Each field, i.e., each element of the inner lists representing the rows, is an integer from the set {0<em>,</em>1<em>,</em>2} representing the state of that field: 0 represents an empty square, 1 represents a square with a Black stone, and 2 represents a square with a White stone.</li>

  </ul></li>

</ol>

See example <strong>?? </strong>for an illustration of this representation of a board configuration.

<ol>

 <li>Create three functions enclosing(board, player, pos, direct), valid moves(board, player), and next state(board, player, pos) that represent the rules of Reversi according to the following specifications.

  <ul>

   <li>A board <strong>position </strong>is represented by a pair (r, c) where r and c are each integers from the range range(8) representing a row index and a column index, respectively. For instance, the position “b3” is represented by (2, 1). The row and column order of the “b3” style and the specification of position is reversed. This is because it is natural to constuct lists of lists in such a way that the outer lists correspond to rows, and the inner list positions corerspond to column positions, so we reference them with row first, then column. This row, column convention is quite common across maths and computer science.</li>

   <li>A <strong>direction </strong>is represented by a pair (dr, dc) where dr and dc are each integers from the set {-1, 0, 1}. For instance, “horizontal to the left” is described by (0, -1), “diagonal to the right and down” is described by (1, 1), and so on).</li>

   <li>The function enclosing(board, player, pos, dir) represents whether putting a player’s stone on a given position would enclose a straight line of opponent’s stones in a given direction:</li>

  </ul></li>

</ol>

<strong>Input</strong>: A board configuration board, an integer player from the set {1, 2}, a board position pos and a direction dir.

<strong>Output</strong>: True if board contains a stone of player in direction dir from position pos and all positions on the straight line between that stone and pos contain stones of the other player, and there is at least one stone belonging to the other player on the straight line; False otherwise.

<ul>

 <li>The function valid moves(board, player) has:</li>

</ul>

<strong>Input</strong>: A board configuration board as well as an integer player from the set {1, 2}.

<strong>Output</strong>: A list of board positions (represented as pairs of integers as described above) [(r1, c1), (r2, c2), …, (rk, ck)] such that the elements of that list correspond to all valid positions that Player player is allowed to drop a stone on in the given input configuration board (in particular, the list is empty if the player has not valid moves in the given board).

<ul>

 <li>The function next state(board, player, pos) has:</li>

</ul>

<strong>Input</strong>: A board configuration board as well as an integer player from the set {1, 2} and a board position representing the move of Player player to place one of their stones on the board configuration board on the field described by pos.

<strong>Output</strong>: A pair (next board, next player) such that next board is the board configuration resulting from Player player placing a stone on position pos on the input board configuration board, and next player is an integer from the set {0, 1, 2} corresponding to the player who gets to move next or 0 in case the game ends after the input move is carried out.

<ol>

 <li>Create functions position(string), run two players() and run single player() that put all of the above together and that allow one or two players to play a game of Reversi through the console as follows.

  <ul>

   <li>The function position(string) accepts as input any string string (e.g., “b5” or “Genghis Khan”) and has as output the board position (r, c) described by the string or None in case the string does not correspond to a valid board position.</li>

   <li>Running run two players() should repeatedly do the following until the user selects to stop:</li>

  </ul></li>

</ol>

1: Print the current board state

2: Ask the player whose turn it is to input a position to drop a stone (in the format “d4”). The player can also choose to quit by entering “q”

3: Your program should then respond in one of the following ways:

<ul>

 <li>If the move is not valid, print “invalid move”</li>

 <li>If the move is valid, place the move on the board.</li>

</ul>

4: If the game ended (no valid move remaining for either player), print the game result and exit

5: If the game did not end, the current player’s turn is over. It is now the other player’s turn

<ul>

 <li>Running run single player() should behave identical to run two players() except that all moves of Player 2 are carried out automatically such that the resulting board configuration has the <em>maximal score </em>for Player 2 (among all their valid moves).</li>

</ul>

<h2>Examples</h2>

<ol>

 <li>Calling score(new board()) returns (2, 2) because the score in the starting configuration is 2 for Player 1 (B) and 2 for player 2 (W).</li>

 <li>Calling enclosing(new board(), 1, (4, 5), (0, -1)) returns True because Player 1 can enclose one opponent’s stone to the left when placing a stone on field “f5”. In contrast, there is no straight line of opponent’s stones to enclose on the diagonal line to the bottom right. Therefore, enclosing(new board(), 1, (4, 5), (1, 1)) returns False.</li>

 <li>Calling next state(new board(), 1, (4, 5)) will return (next board, 2) where next board is the board configuration</li>

</ol>

[[0,0,0,0,0,0,0,0],

[0,0,0,0,0,0,0,0],

[0,0,0,0,0,0,0,0],

[0,0,0,2,1,0,0,0],

[0,0,0,1,1,1,0,0],

[0,0,0,0,0,0,0,0],

[0,0,0,0,0,0,0,0],

[0,0,0,0,0,0,0,0]]

because that is the configuration resulting from Player 1 putting a stone on field “f5” (encoded by integer pair (4, 5)) in the starting configuration, and Player 2 has the next move afterwards.

<ol>

 <li>Calling valid moves(next state(new board(), 1, (4, 5))[0], 2) returns the list [(3, 5), (5, 3), (5, 5)] or any of its permutations (list with same elements but different order) because the valid moves of Player 2 after Player 1 played “f5” in Turn 1 are “d6”, “f4”, and “f6”.</li>

 <li>Calling position(“e3”) returns the pair (2, 4) because that is the internal representation of board position “e3”. Calling position(“l1”), position(“a0”), or position(“Genghis Khan”) all return None because all these input do not correspond to valid board positions.</li>

</ol>

<strong>Marking Guide </strong>Marks are given for the correct behaviour of the different functions:

<ol>

 <li>1 mark each for new board, print board, and score</li>

 <li>4 marks for enclosing, 3 marks for validmoves, and 2 marks next state</li>

 <li>1 mark for position, 2 marks for run twoplayers and 3 marks for run single player</li>

</ol>

All functions are assessed independently to the degree possible. For instance, even if function valid moves does not always produce the correct output, function run two players can still be marked as correct.