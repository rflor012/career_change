# career_change
A learning journey and transition from being a lawyer to a computer programmer

# June 24, 2018 - It Begins
So apparently on April 20, 2017, I created my github account with the focus in mind that one day I will transition from my full time legal career to a change in computer programming/coding.
Fast forward to today, June 24, 2018 and I think I am already a few 'baby' steps closer to that dream of mine. As I am going through IronHack I figured that I could use this READ ME file
as a way to track my learning and experiences as I go along these next 8 weeks.

There's also something seemingly nostalgic from writing in these READ me files. Makes me think of being younger and messing around with my fathers 40 pound Macbook "laptop" which was basically the size
of a small refrigerator. So today I've been working on our first game Project. Chad Barcelo is my partner and we've decided that we are going to make a TOP down, grid game where we can select objects and move them
around this grid. The objective is to kill the opponent using your character objects and not die to the opponent. Very basic idea, so coding it should be simple right? (spoiler, its probably not going to be that simple)
lets take a look:

````
var testMap = [
  [3, 3, 3, 3, 3],
  [3, 4, 4, 3, 3],
  [3, 4, 4, 3, 1],
  [3, 4, 2, 3, 3],
  [3, 4, 3, 3, 1]
  ];

function createGameBoard() {
  for (var r = 0; r < testMap.length; r++) {

    var row = testMap[r];

    for (var c = 0; c < row.length; c++) {
      var column = row[c];

      if (column == "3") {
        console.log("This is a grass tile");
      } else if (column == "4") {
        console.log("This is a dirt tile");
      } else if (column == "1") {
        console.log("This is a stone tile");
      } else if (column == "2") {
        console.log("This is a geyser tile");
      } else {}
    }
  }
}

function randomTileSet() {
  return Math.floor(Math.random() * 5);
}

function addSprite(num){}

console.log(testMap[randomTileSet()][randomTileSet()]);
````

So we have a two dimensional array that stores values that each will correspond to a "sprite" tile, im guessing that each "tile" object is going to have to store values within it. Which is why I think objects would be the way to go. Essentially, even the character should be an object of type TILE because thats essentially where he will be moving along. Every object should inherit basic properties such as passable or not passable. Maybe we can switch/toggle that on and off using DOM and Jquery. So far the code atleast iterates through every object from left to right and prints them out the correct number of times. We can even get a random tile from the entire test map. Thatll probably go into a randomMapGenerate function. probably on every newGame(); So far having fun and learning which is the key. I'll take a break for now and come back to this in a few. I think I can get a game of League in for now. This is probably super easy, but remember Im moving away from Law to this, go easy on me ;) 06/24/2018 - 1:04pm

### Slight Update

So I kept during the day, Colombia played against Poland, and won 3 - 0 , WOOP. Some comfort after Peru's defeat... anyways, I finally got this thing to actually go through every single column and row. Chad had the good idea of decrementing instead of incrementing. I really need to read up on loops, it just looks weird to me even though I technically understand what its doing. (but not well I guess.) Here's what came next. Made gameBoard a variable with an anonymous function. We declared a variable result in there thats just an empty arraw that gonna house our random numbers (0-4) to represent items/sprites that are gonna go onto the grid. I guess the next step is to create a function or improve on this one to grab actual sprites
and populate the board. i think thats DOM or JQuery stuff, but I need to read up more on that.  

````
var gameBoard = function createGameBoard(width, height){
      var result = [];
      for (var i = 0 ; i < width; i++) {
          result[i] = [];
          for (var j = 0; j < height; j++) {
              result[i][j] = Math.floor(Math.random() * 5);
          }
      }
      this.gameBoard = result;
      return this.gameBoard;
  };

var gameBoard;

function checkGameBoard(theBoard) {
  for (var r = gameBoard.length; r > 0; r--) {
    var row = gameBoard[r-1];
    for (var c = row.length; c > 0; c--) {
      var column = row[c-1 + 0];
      if (column === 1) {
        console.log("This is a grass tile " + "[Row " + row + " , Column " + column + " ]");
      } else if (column === 2) {
        console.log("This is a dirt tile " + "[Row " + row + " ,Column " + column + " ]");
      } else if (column === 3) {
        console.log("This is a stone tile " + "[Row " + row + " ,Column " + column + " ]");
      } else if (column === 4) {
        console.log("This is a geyser tile" + "[Row " + row + " ,Column " + column + " ]");
      } else if(column === 0){
        console.log("This tile has a 0 " + "[Row " + row + " ,Column " + column + " ]");
      }
    }
  }
}


function randomTileSet() {
  return Math.floor(Math.random() * 5);
}

function addSprite(num){}

// console.log(gameBoard[randomTileSet()][randomTileSet()]);
````
So this checkGameBoard part took longer than it should, apparently after testing and testing I found out that line ```` var column = row[c-1 + 0];````
was returning every column but those that would be found on the 0 index. The first entry in the row column. I added the + 0 and bam, all the rows and columns are accounted for. Pretty cool... -06/24/2018 -- 5:30pm
