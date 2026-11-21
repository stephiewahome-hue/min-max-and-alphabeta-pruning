# Lesson 4: Game Programming Using C++

## 1. Introduction to the Minimax Algorithm

The **Minimax Algorithm** is an Artificial Intelligence (AI) algorithm used in games such as chess, checkers and Tic-Tac-Toe.

It helps a computer choose the best possible move by examining different possible moves in a game.

Minimax involves two players:

- **MAX:** Tries to get the highest possible score.
- **MIN:** Tries to get the lowest possible score.

The two players take turns making decisions.

## 2. Understanding the Game Tree
<img src="path/to/image.png" alt="Alt text" width="300" />   

A game tree represents all the possible moves that players can make.

In the Minimax algorithm, we have three levels:

| Level | Player | Objective |
|---|---|---|
| Top level | MAX | Choose the highest value |
| Middle level | MIN | Choose the lowest value |
| Bottom level | MAX | Choose the highest value |

The algorithm starts calculating from the bottom of the tree and moves upwards until it reaches the root (top).

## 3. Step-by-Step Minimax Calculation

Using the example from the lecture, we have four groups of values at the bottom:

**Group 1:**

Values: -2, 2, 1

MAX chooses the largest value:

`MAX(-2, 2, 1) = 2`

**Group 2:**

Values: 1, 3, 4

`MAX(1, 3, 4) = 4`

**Group 3:**

Values: -1, 1, 0

`MAX(-1, 1, 0) = 1`

**Group 4:**

Values: 2, 5, 6

`MAX(2, 5, 6) = 6`

Therefore, the results from the bottom level are:

`2, 4, 1, 6`

### Moving to the MIN level

MIN chooses the smallest value from each pair.

Left branch:

`MIN(2, 4) = 2`

Right branch:

`MIN(1, 6) = 1`

### Moving to the MAX level

MAX chooses the largest value:

`MAX(2, 1) = 2`

**Final Minimax answer: 2**

This means MAX chooses the left branch because 2 is greater than 1.

## 4. What Is Alpha-Beta Pruning?

Alpha-Beta Pruning is an improvement to the Minimax algorithm.

It reduces the number of game-tree branches that need to be examined by ignoring branches that cannot affect the final decision.

This makes the search process more efficient.

### Understanding Alpha and Beta

**Alpha (α):**

- Represents the best value MAX can guarantee so far.
- Initially starts at negative infinity (-∞).

**Beta (β):**

- Represents the best value MIN can guarantee so far.
- Initially starts at positive infinity (+∞).

## 5. Alpha-Beta Pruning Using the Lecture Example

### Step A: Calculate the left branch

From the first two groups:

`MAX(-2, 2, 1) = 2`

`MAX(1, 3, 4) = 4`

MIN chooses:

`MIN(2, 4) = 2`

MAX can now guarantee a value of 2.

Therefore:

`Alpha = 2`

### Step B: Calculate the first group on the right branch

`MAX(-1, 1, 0) = 1`

MIN can now choose a value of 1 or something smaller.

Therefore:

`Beta = 1`

### Step C: Apply the pruning condition

The Alpha-Beta pruning rule is:

`Alpha >= Beta`

Substituting the values:

`2 >= 1`

This condition is TRUE.

Therefore, the remaining group `(2, 5, 6)` can be skipped.

Why?

Because MIN already has an option worth 1, while MAX already has an option worth 2. MIN will not allow MAX to obtain a better result through that branch.

**Important:** Alpha-Beta Pruning does not change the optimal decision made by Minimax. It simply avoids unnecessary calculations.

## 6. Difference Between Minimax and Alpha-Beta Pruning

| Minimax | Alpha-Beta Pruning |
|---|---|
| Examines all branches in the search tree. | Skips branches that cannot affect the decision. |
| Can require more calculations. | Reduces unnecessary calculations. |
| Finds the best possible move. | Finds the same best move more efficiently. |
| Does not use Alpha and Beta values. | Uses Alpha and Beta values. |

## 7. Advantages of Alpha-Beta Pruning

1. Reduces the number of nodes examined.
2. Makes the Minimax search more efficient.
3. Saves computational resources.
4. Allows the AI to search deeper into a game tree.
5. Preserves the optimal decision produced by Minimax.

## 8. Important Terms to Remember

- **Minimax:** An algorithm used to find the best move in a two-player game.
- **MAX:** The player who tries to maximize the score.
- **MIN:** The player who tries to minimize the score.
- **Game Tree:** A representation of possible moves in a game.
- **Alpha (α):** The best value MAX can guarantee so far.
- **Beta (β):** The best value MIN can guarantee so far.
- **Pruning:** Ignoring branches that cannot affect the final decision.

## 9. Conclusion

The Minimax algorithm helps Artificial Intelligence choose the best move by examining possible game outcomes.

Alpha-Beta Pruning improves Minimax by reducing unnecessary searches. It uses Alpha and Beta values to identify branches that can be ignored.

**Key takeaway:** Minimax finds the best move, while Alpha-Beta Pruning helps find it more efficiently.
