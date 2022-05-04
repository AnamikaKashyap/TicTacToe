# TicTacToe
a simple mobile game
https://anamikakashyap.github.io/TicTacToe/

<!DOCTYPE html>
<html lang="en">
<head>
  <title>Bootstrap Example</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
<style>
.square {
    float:left;
    position: relative;
    width:30%;
    padding-bottom:30%; /* it equals width for a 1:1 aspect ratio */
    margin:1.66%;
    background-color:white;
}

.content {
    position:absolute;
    height:100%;
    width:100%;
    font-size:19.0vw;
}

body {
    color:#000;
    text-align:center;
    background:#ECECEC;
}

th, td {
    text-align:center;
}
</style>

<script>
function putSign(e) {
    if (e.innerHTML === "") {
      e.innerHTML = turn;
      turn = next;
      next = e.innerHTML;
      header.innerHTML = turn;
      var result = null;
      if (!isOver) {
          result = getWinner();
      }
      if (result === "draw" && isOver === false) {
          isOver = true;
          document.getElementById("newGame").style.visibility = "visible";
          alert("Draw");
      }
      if (result === "X" && isOver === false) {
          xScore.innerHTML++;
          isOver = true;
          document.getElementById("newGame").style.visibility = "visible";
      }
      if (result === "O" && isOver === false) {
          oScore.innerHTML++;
          isOver = true;
          document.getElementById("newGame").style.visibility = "visible";
      }
    }
  }
  
  function getWinner() {
    if (elements[0].innerHTML == elements[1].innerHTML && 
        elements[0].innerHTML == elements[2].innerHTML &&
        elements[0].innerHTML !== "") {
        colorBackground(elements[0]);
        colorBackground(elements[1]);
        colorBackground(elements[2]);
        return elements[0].innerHTML;
    }
    if (elements[3].innerHTML == elements[4].innerHTML && 
        elements[3].innerHTML == elements[5].innerHTML &&
        elements[3].innerHTML !== "") {
        colorBackground(elements[3]);
        colorBackground(elements[4]);
        colorBackground(elements[5]);
        return elements[3].innerHTML;
    }
    if (elements[6].innerHTML == elements[7].innerHTML && 
        elements[6].innerHTML == elements[8].innerHTML &&
        elements[6].innerHTML !== "") {
        colorBackground(elements[6]);
        colorBackground(elements[7]);
        colorBackground(elements[8]);
        return elements[6].innerHTML;
    }
    if (elements[0].innerHTML == elements[3].innerHTML && 
        elements[0].innerHTML == elements[6].innerHTML &&
        elements[0].innerHTML !== "") {
        colorBackground(elements[0]);
        colorBackground(elements[3]);
        colorBackground(elements[6]);
        return elements[0].innerHTML;
    }
    if (elements[1].innerHTML == elements[4].innerHTML && 
        elements[1].innerHTML == elements[7].innerHTML &&
        elements[1].innerHTML !== "") {
        colorBackground(elements[1]);
        colorBackground(elements[4]);
        colorBackground(elements[7]);
        return elements[1].innerHTML;
    }
    if (elements[2].innerHTML == elements[5].innerHTML && 
        elements[2].innerHTML == elements[8].innerHTML &&
        elements[2].innerHTML !== "") {
        colorBackground(elements[2]);
        colorBackground(elements[5]);
        colorBackground(elements[8]);
        return elements[2].innerHTML;
    }
    if (elements[0].innerHTML == elements[4].innerHTML && 
        elements[0].innerHTML == elements[8].innerHTML &&
        elements[0].innerHTML !== "") {
        colorBackground(elements[0]);
        colorBackground(elements[4]);
        colorBackground(elements[8]);
        return elements[0].innerHTML;
    }
    if (elements[2].innerHTML == elements[4].innerHTML && 
        elements[2].innerHTML == elements[6].innerHTML &&
        elements[2].innerHTML !== "") {
        colorBackground(elements[2]);
        colorBackground(elements[4]);
        colorBackground(elements[6]);
        return elements[2].innerHTML;
    }
    var filled = 0;
    for (var i = 0; i < elements.length; i++) {
        if (elements[i].innerHTML == "X" || elements[i].innerHTML == "O") {
            filled++;
        }
        if (filled == 9) {
            return "draw";
        }
    }
    return false;
  }
  
  function colorBackground(el) {
      el.style.backgroundColor = "#b3ffb3";
  }
  
  function startNewGame() {
    for (var i = 0; i < elements.length; i++) {
      elements[i].innerHTML = "";
      elements[i].style.backgroundColor = "#FFF";
    }
    turn = "X";
    next = "O";
    header.innerHTML = turn;
    isOver = false;
    document.getElementById("newGame").style.visibility = "hidden";
  }
</script>
</head>
<body>

<div class="container">
  <table class="table">
    <thead>
      <tr>
        <th>X</th>
        <th>Turn</th>
        <th>O</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><span id="xScore">0</span></td>
        <td id="header">X</td>
        <td><span id="oScore">0</span></td>
      </tr>
    </tbody>
  </table>
  <!-- 1st row -->

  <div class="square">
      <div class="content" onclick="putSign(this)"></div>
  </div>
  <div class="square">
      <div class="content" onclick="putSign(this)"></div>
  </div>
  <div class="square">
      <div class="content" onclick="putSign(this)"></div>
  </div>
  <!-- 2nd row -->

  <div class="square">
    <div class="content" onclick="putSign(this)"></div>
  </div>
  <div class="square">
    <div class="content" onclick="putSign(this)"></div>
  </div>
  <div class="square">
    <div class="content" onclick="putSign(this)"></div>
  </div>
  <!-- 3rd row -->

  <div class="square">
    <div class="content" onclick="putSign(this)"></div>
  </div>
  <div class="square">
    <div class="content" onclick="putSign(this)"></div>
  </div>
  <div class="square">
    <div class="content" onclick="putSign(this)"></div>
  </div>
  
  <div>
    <button id="newGame" class="btn btn-info" onclick="startNewGame()">New game</button>
  </div>
  <div class="panel panel-default" style="margin-top:5px">
    <div class="panel-body">Made by <a href="https://www.myvegeto.com">Vegeto</a></div>
  </div>
</div>

<script>
  var turn = "X";
  var next = "O";
  var isOver = false;
  var header = document.getElementById("header");
  var xScore = document.getElementById("xScore");
  var oScore = document.getElementById("oScore");
  var elements = document.getElementsByClassName("content");
  document.getElementById("newGame").style.visibility = "hidden";
</script>
</body>
</html>
