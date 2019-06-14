<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"

 

      "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

 

      <!-- Fig. 9.6: Craps.html -->

 

      <!-- Craps game simulation. -->

 

      <html xmlns = "http://www.w3.org/1999/xhtml">

 

      <head>

 

      <title>Program that Simulates the Game of Craps</title>

 

<style type = "text/css">

table {        text-align: right }

body {        font-family: arial, sans-serif }

        div.red { color: red }

 

        </style>

 

        <script type = "text/javascript">

        <!--

 

        // variables used to test the state of the game

        var WON = 0;

        var LOST = 1;

 

        var CONTINUE_ROLLING = 2;

        // other variables used in program

 

        var firstRoll = true; // true if current roll is first

 

        var sumOfDice = 0; // sum of the dice

 

        var myPoint = 0; // point if no win/loss on first roll

 

        var gameStatus = CONTINUE_ROLLING; // game not over yet

 

        // process one roll of the dice

 

        function play()

{

// get the point field on the page

var point = document.getElementById( "pointfield" );

 

// get the status div on the page

var statusDiv = document.getElementById( "status" );

if ( firstRoll ) // first roll of the dice

{

sumOfDice = rollDice();     

                       

switch ( sumOfDice )          

{                      

case 7: case 11: // win on first roll

            gameStatus = WON;           

            // clear point field     

            point.value = "";       

            break;

case 2: case 3: case 12: // lose on first roll

            gameStatus = LOST;          

            // clear point field     

            point.value = "";       

            break;

default:           // remember point

            gameStatus = CONTINUE_ROLLING;

            myPoint = sumOfDice;       

            point.value = myPoint;       

            firstRoll = false;       

} // end switch          

} // end            if         

else                

{                      

sumOfDice = rollDice();     

                       

if ( sumOfDice == myPoint ) // win by making point

gameStatus = WON;           

else                

if          ( sumOfDice == 7 )   // lose by rolling 7

            gameStatus = LOST;          

} // end            else    

                       

if ( gameStatus == CONTINUE_ROLLING )

statusDiv.innerHTML = "Roll again";

else                

{                      

if ( gameStatus == WON )  

statusDiv.innerHTML = "Player wins. " +

            "Click Roll Dice to play again.";

else                

statusDiv.innerHTML = "Player loses. " +

            "Click Roll Dice to play again.";

                       

firstRoll = true;         

        } // end else

 

        } // end function play

 

        // roll the dice

 

        function rollDice()

{

var die1;

var       die2;

var       workSum;

die1 = Math.floor( 1 + Math.random() * 6 );         

die2 = Math.floor( 1 + Math.random() * 6 );         

workSum = die1 + die2;     

           

document.getElementById( "die1field" ).value = die1; 

document.getElementById( "die2field" ).value = die2; 

document.getElementById( "sumfield" ).value = workSum;   

           

        return workSum;

 

        } // end function rollDice

        // -->

 

        </script>

 

        </head>

        <body>

        <form action = "">

 

        <table>

 

        <caption>Craps</caption>

 

        <tr><td>Die 1</td>

 

        <td><input id = "die1field" type = "text" />

 

        </td></tr>

 

        <tr><td>Die 2</td>

 

        <td><input id = "die2field" type = "text" />

 

        </td></tr>

 

        <tr><td>Sum</td>

 

        <td><input id = "sumfield" type = "text" />

 

        </td></tr>

 

        <tr><td>Point</td>

 

        <td><input id = "pointfield" type = "text" />

 

        </td></tr>

 

        <tr><td /><td><input type = "button" value = "Roll Dice"

 

        onclick = "play()" /></td></tr>

 

        </table>

 

        <div id = "status" class = "red">

 

        Click the Roll Dice button to play</div>

 

        </form>

 

        </body>

 

</html>
