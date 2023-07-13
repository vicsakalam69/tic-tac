# tic-tac
/**
 * Function to create a tic-tac-toe game.
 * 
 * @returns {object} - The tic-tac-toe game object.
 */
function createTicTacToeGame() {
  // Initialize the game board
  const board = [
    ['', '', ''],
    ['', '', ''],
    ['', '', '']
  ];

  /**
   * Function to make a move in the tic-tac-toe game.
   * 
   * @param {number} row - The row index of the move.
   * @param {number} col - The column index of the move.
   * @param {string} player - The player making the move ('X' or 'O').
   * @returns {boolean} - True if the move is valid and made successfully, false otherwise.
   */
  function makeMove(row, col, player) {
    // Check if the move is valid
    if (row < 0 || row >= board.length || col < 0 || col >= board[0].length || board[row][col] !== '') {
      return false;
    }

    // Make the move
    board[row][col] = player;
    return true;
  }

  /**
   * Function to check if the game has been won.
   * 
   * @returns {string|null} - The winning player ('X' or 'O') if the game has been won, null otherwise.
   */
  function checkWin() {
    // Check rows
    for (let row = 0; row < board.length; row++) {
      if (board[row][0] !== '' && board[row][0] === board[row][1] && board[row][0] === board[row][2]) {
        return board[row][0];
      }
    }

    // Check columns
    for (let col = 0; col < board[0].length; col++) {
      if (board[0][col] !== '' && board[0][col] === board[1][col] && board[0][col] === board[2][col]) {
        return board[0][col];
      }
    }

    // Check diagonals
    if (board[0][0] !== '' && board[0][0] === board[1][1] && board[0][0] === board[2][2]) {
      return board[0][0];
    }
    if (board[0][2] !== '' && board[0][2] === board[1][1] && board[0][2] === board[2][0]) {
      return board[0][2];
    }

    return null;
  }

  // Return the tic-tac-toe game object
  return {
    makeMove,
    checkWin
  };
}

// Usage example:
const game = createTicTacToeGame();
game.makeMove(0, 0, 'X');
game.makeMove(0, 1, 'O');
game.makeMove(1, 1, 'X');
game.makeMove(1, 0, 'O');
game.makeMove(2, 2, 'X');
console.log(game.checkWin()); // Output: 'X'
