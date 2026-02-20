# Let's understand our compelete tic tac toe project step by step:

1. Firstly we need access of our all cells, where we want to play game
2. So, we will use query selector which give us access of board.
3. Then we will apply add-event listener on that board.
4. event listener listen our event, which is "click" in this case
5. and event listener takes one more parameter "callback fn".
6. Now, will use "event" object to know about which cells are targeting,
7. So, will use "event.target", and put it into a variable, let "element".
8. Now, we can easily use element.innerHTML = "X" or "O", here "X"
9. & "O" are our two players who are playing this game.
10. Now, we can firtly fix our first player turn, means whom will start to play game firstly.
11. So, will write on top of code, let turn = "O", this means first turn is for "O" player.
12. Now we can easily use if-else statement to give turn to both player.
13. we can now write: 

let turn = "O";

if(turn==="O")
{
    element.innerHTML = "O";
    turn = "X';
}
else{

    element.innerHTML = "X";
    turn = "O";
}

14. Now on frontend we can write turn wise "O" & "X", but main logic starts from here:
15. Now, if we think logically then we can assume our board as an array which have there id's from 0 to 8, same like an array index no from 0 to 8 having 9 elments:
16. So, now let make an array having 9 elments, but in starting that board cells will be empty, means our array should also be empty: 

let board_array = new Array(9).fill("E");
["E","E","E","E","E","E","E","E","E",]

17. Now, we know that we have total 8 possible ways for a winner reusult, so let put them also in an array:

let winner = [
    [0,1,2],[3,4,5],[6,7,8],
    [0,3,6],[1,4,7],[2,5,8],
    [0,4,8],[2,4,6]
];

18. Now we have to match this 2d array conditions with our board array for a winner
19. We also knows that when we firstly click on any cell, then it will become "O".
20. So, our board array will also change from "E" value to that filled value:
    ["O","O","E","E","E","E","E","E","E",] 
21. So, we have to fill that board array also with our "O" & X" in place of "E"
22. So, we will write:

  let turn = "O";

if(turn==="O")
{
    element.innerHTML = "O";
 #   board_array[element.id] = "O";
    turn = "X';
}
else{

    element.innerHTML = "X";
#     board_array[element.id] = "X";
    turn = "O";
}

23. Now, we have to check our board array with winner array to declare a winner,
 so we need a funtion for this logic, let named fn as "checkWinner()":

   let turn = "O";

   let winner = [
    [0,1,2],[3,4,5],[6,7,8],
    [0,3,6],[1,4,7],[2,5,8],
    [0,4,8],[2,4,6]
];

let board_array = new Array(9).fill("E");

if(turn==="O")
{
    element.innerHTML = "O";
      board_array[element.id] = "O";
       if(checkWinner())
      {
        
      }
    turn = "X';
}
else{

    element.innerHTML = "X";
      board_array[element.id] = "X";
      if(checkWinner())
      {

      }
    turn = "O";
}

24. Let's make our checkWinner function above this if-else condition:

    let turn = "O";

   let winner = [
    [0,1,2],[3,4,5],[6,7,8],
    [0,3,6],[1,4,7],[2,5,8],
    [0,4,8],[2,4,6]
];

let board_array = new Array(9).fill("E");

# function checkWinner(){

#    for(let [index0,index1,index2] of winner)
#    {
#        if(board_array[index0]!="E"&&board_array[index0]===board_array[index1]&&  board_array[index1]===board_array[index2])
#            return 1;
#    }
#    return 0;
# }

if(turn==="O")
{
    element.innerHTML = "O";
      board_array[element.id] = "O";
       if(checkWinner())
      {
        
      }
    turn = "X';
}
else{

    element.innerHTML = "X";
      board_array[element.id] = "X";
      if(checkWinner())
      {

      }
    turn = "O";
}

25. Let explain each and every line of our "checkWinner" fn:

    function checkWinner(){

   # for(let [index0,index1,index2] of winner):

   Here in above line we are using for of loop for our 2d array.

   If, we write: for(let checkWinner of winner) --> This will written us entire each array as an elements like: [0,1,2], [,,,].....

   But, we need to compare those array inside value, so will destructure it:
   We will write: [index0,index1,index2] --> index0,1,2 are just names we had given for our array values.

  #  {
        if(board_array[index0]!="E"&&board_array[index0]===board_array[index1]&&board_array[index1]===board_array[index2])
            return 1;
   # }

    Here, we are just comparing our board_array inside values with our winner array condiitons values which we are getting from above for of loop one by one.
    So, firstly our board_array should not have any "E" value bcoz we are comparing here our array values, so will write -- > board_array[index0]!="E"

    Now, We have to compare all those three value (index0,1,2) with eachother of all those 8 arrays which are our wiining conditions, means those index0, index1, index 2 should be equal to eachother to winn the game.

    So, will write -->  &&board_array[index0]===board_array[index1]&&board_array[index1]===board_array[index2]

    Our combined both conditions:  board_array[index0]!="E" && board_array[index0]===board_array[index1]&&board_array[index1]===board_array[index2];

    Now, we only need to return 1 --> for true, means if conditions matched
    & 0 --> for false, means if no winning conditions will match.
    
    # So, this is the entire exaplanation of our "checkWinning() fn".

    26. Now we need to use that fn with our if-else conditions and
        to print winning message.

     if(turn==="O")
{
    element.innerHTML = "O";
      board_array[element.id] = "O";
       if(checkWinner())
      {
          document.getElementById('winningMessage').innerHTML = "Winner is X";
      }
    turn = "X';
}
else{

    element.innerHTML = "X";
      board_array[element.id] = "X";
      if(checkWinner())
      {
          document.getElementById('winningMessage').innerHTML = "Winner is Y";
      }
    turn = "O";
}

# Now we had done our 80% project till now, if any these 
  conditions satisfy then "O" & "X" will win.

27. Now we need to write a condition for draw situation also.
    means, if now one win after completing all the truns.

    For this, we need to delare a varaible total turns above the all code,
    like turn varaible and a if conditon with draw messeage at the last.

   # let total_turn = 0;

    let turn = "O";

   let winner = [
    [0,1,2],[3,4,5],[6,7,8],
    [0,3,6],[1,4,7],[2,5,8],
    [0,4,8],[2,4,6]
];

let board_array = new Array(9).fill("E");

function checkWinner(){

    for(let [index0,index1,index2] of winner)
    {
        if(board_array[index0]!="E"&&board_array[index0]===board_array[index1]&&board_array[index1]===board_array[index2])
            return 1;
    }


    return 0;

}
   
       if(turn==="O")

# total_turn++;

{
    element.innerHTML = "O";
      board_array[element.id] = "O";
       if(checkWinner())
      {
          document.getElementById('winningMessage').innerHTML = "Winner is X";
      }
    turn = "X';
}
else{

    element.innerHTML = "X";
      board_array[element.id] = "X";
      if(checkWinner())
      {
          document.getElementById('winningMessage').innerHTML = "Winner is Y";
      }
    turn = "O";
}

# if(total_turn==9){

#    document.getElementById('winningMessage').innerHTML = "Match is draw";

# }

28. Now we had to write condition for not to overwritte on click, means
    id the cell is empty then only we can use our turn on that cell otherwise not:

    We can put all these above code in a if statmenet, like
    if(turn === "E){

        Only in this condition we can use next turn, otherwise not.
    }

  #  So, entire code till now:
   
   let total_turn = 0;
   let turn = "O";

   let winner = [
    [0,1,2],[3,4,5],[6,7,8],
    [0,3,6],[1,4,7],[2,5,8],
    [0,4,8],[2,4,6]
];

let board_array = new Array(9).fill("E");

function checkWinner(){

    for(let [index0,index1,index2] of winner)
    {
        if(board_array[index0]!="E"&&board_array[index0]===board_array[index1]&&board_array[index1]===board_array[index2])
            return 1;
    }


    return 0;

}

#   if(board_array[element.id]==="E")

{
       if(turn==="O")

total_turn++;

{
    element.innerHTML = "O";
      board_array[element.id] = "O";
       if(checkWinner())
      {
          document.getElementById('winningMessage').innerHTML = "Winner is X";
      }
    turn = "X';
}
else{

    element.innerHTML = "X";
      board_array[element.id] = "X";
      if(checkWinner())
      {
          document.getElementById('winningMessage').innerHTML = "Winner is Y";
      }
    turn = "O";
}

}

29. Now we need to do logic for restart button, we have to clear all the values,
    event listener and again to start listening event all all things clear.

    So, for that we have write --> board.removeEventListener("event", "callback fn");
 
30. But, here we need a "callback fn", so for this we can do one thing:
    We can write all our above turn condiiton code in a separte fn, then we can use 
    that fn as a "callback fn" in removeEventListener & again addEventListener:

    So, will write:

    let turn = 'O';
let total_turn = 0; 

let winner = [
    [0,1,2],[3,4,5],[6,7,8],
    [0,3,6],[1,4,7],[2,5,8],
    [0,4,8],[2,4,6]
];

let board_array = new Array(9).fill("E");
// ["E","E","E","E","E","E","E","E","E",]

function checkWinner(){

    for(let [index0,index1,index2] of winner)
    {
        if(board_array[index0]!="E"&&board_array[index0]===board_array[index1]&&board_array[index1]===board_array[index2])
            return 1;
    }


    return 0;

}

#
    const printer = (event)=>{

      const element = event.target;

if(board_array[element.id]==="E")
    
{

    total_turn++;

if(turn==='O')
{
    element.innerHTML = "O";
    board_array[element.id] = "O";
    if(checkWinner())
    {
        document.getElementById('winningMessage').innerHTML = "Winner is O";
#    board.removeEventListener('click',printer); --> to remove event listener when we click on restart btn
#        return;  --> bcoz agar 9th turn pr koi winner aarha h to return ho jaaye yhi se, win k baad hum nhi chaate ki draw aaye message pr 9th turn pr.

    }
    turn = 'X';
}
else{

    element.innerHTML = "X";
    board_array[element.id] = "X";
    if(checkWinner())
    {
        document.getElementById('winningMessage').innerHTML = "Winner is X";
#        board.removeEventListener('click',printer);
#        return;

    }
    turn = "O";
}

if(total_turn==9){

    document.getElementById('winningMessage').innerHTML = "Match is draw";

}

}

}

    } 

31. # Now Restart btn logic: saare cell clear ho jaaye:

// Firstly get accees of btn & all cells:
const Restart = document.getElementById("restartButton");
Restart.addEventListener('click',()=>{

    const cell = document.getElementsByClassName('cell'); // Now hume yhe saare div aa a node list or as a html collection mila hoga

/* Ab, agar mujhe inn saare node pr iterate krna h toh hum usko array m convert kr denge,
and easily foreach ka use krke uss array pr iterate kr lenge:*/
    Array.from(cell).forEach((value)=>{
        value.innerHTML = "";
    })

    // Ab apne turn or total turn ko bhi fix krna padega fhir se:

    turn = "O";
    total_turn = 0;
    board_array = new Array(9).fill("E");
    document.getElementById('winningMessage').innerHTML = "";

    // Listen krna bhi fhr se suru krna padega:
    board.addEventListener('click',printer);

})    


    
