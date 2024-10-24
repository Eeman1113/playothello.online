## What are you up against?

### 1. Beginner (makeBeginnerAIMove):
- Uses a completely random selection from available valid moves
- No evaluation or strategy - just picks randomly from legal moves
- This is the simplest possible AI implementation

### 2. Intermediate (makeIntermediateAIMove):
- Uses a single-depth evaluation (looks only at the immediate next move)
- Evaluates positions using several metrics:
  - Coin parity (piece count difference)
  - Mobility (number of possible moves)
  - Corner control
  - Edge/stability analysis
- Picks the move that gives the best immediate score
- No look-ahead/tree search

### 3. Advanced (makeAdvancedAIMove):
- Uses the Alpha-Beta pruning algorithm (a variant of Minimax)
- Looks 4 moves ahead (depth=4)
- Uses the same evaluation metrics as Intermediate:
  - Coin parity
  - Mobility
  - Corner control
  - Edge/stability
- Implements pruning to efficiently search the game tree
- Can anticipate opponent responses and plan multiple moves ahead

The main difference between these implementations is their search depth and complexity:
- Beginner: No search (depth 0)
- Intermediate: Depth 1 search with position evaluation
- Advanced: Depth 4 search with Alpha-Beta pruning and the same position evaluation

## **Main Features:**
1. **Game Board Initialization:**
   - The board is an 8x8 grid initialized with a starting position (two black and two white pieces in the center).
   - The `initializeBoard()` function sets this up at the start of the game.
   
2. **Move Validation and Rendering:**
   - The game checks for valid moves by examining whether a player’s move can outflank at least one opponent’s piece, following Othello rules.
   - Valid moves are highlighted with a dot (`•`), and the `makeMove()` function handles piece placement and flipping.
   - The `renderBoard()` function dynamically updates the HTML to reflect the current state of the game.

3. **Player Turn Management:**
   - The game alternates between black (`B`) and white (`W`) turns.
   - If a player cannot make a valid move, the turn is automatically skipped, and the status reflects this.
   - Players are provided a visual representation of whose turn it is and the current score (black and white pieces).

4. **AI Mode:**
   - When AI mode is enabled, the AI makes decisions based on a minimax algorithm with alpha-beta pruning.
   - The `makeAIMove()` function triggers the AI's decision-making process, with `alphabeta()` used to evaluate potential moves by simulating multiple turns ahead.

5. **Move History and Status:**
   - A move history is displayed to keep track of recent moves, along with the number of pieces for each color.
   - The game status shows the current score and whose turn it is, and announces the winner or a tie when the game ends.

6. **Instruction Toggle:**
   - A clickable section provides instructions for how to play the game and offers strategy tips. This helps beginners understand the rules.
   - The content can be toggled on and off to avoid cluttering the interface.

## **Additional Details:**
- **AI Evaluation Function:**
  - The AI uses heuristics to evaluate the board: coin parity, mobility, corner control, and stability (edge control). This helps the AI make smarter decisions.
  
- **Animations:**
  - There is an animation for flipping pieces when a move is made, adding a smooth visual effect that enhances the user experience.

- **Responsive Design:**
  - The CSS ensures the game board and text adapt to different screen sizes, with slightly smaller cells and text on smaller devices.

## **Suggestions for Further Development:**
1. **Difficulty Levels:**
   - You could add varying levels of AI difficulty by adjusting the search depth in the minimax algorithm (e.g., deeper searches for higher difficulty).
   
2. **Undo Functionality:**
   - Implementing an "undo move" button could enhance the gameplay, allowing users to rethink their strategies.

3. **Piece Animation:**
   - The piece flipping animation could be made smoother by utilizing 3D transformations or adjusting the transition timing.

4. **Save/Load Game:**
   - A save and load feature could allow players to return to their game later, especially in AI mode.
