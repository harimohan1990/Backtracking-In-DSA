# Backtracking-In-DSA

Imagine you're trying to **find your way out of a maze**.

### 🧠 Backtracking is like:

1. You try one path.
2. If you hit a dead end, you **go back (backtrack)** to the last decision point.
3. Then you try a different path.
4. You keep doing this until you **find the exit or try all paths**.

---

### 🍕 Real-life example:

You're ordering a pizza with toppings. You try:

* Cheese → Yes
* Paneer → Yes
* Jalapeno → No → go back → try Olives instead!

---

### In DSA:

Backtracking =
**Try → Check → Backtrack (undo)** → Try next

---

### ✨ Used In:

* Sudoku Solver
* N-Queens Problem
* Word Break
* Maze Problems
* Generate all permutations or combinations

---

🧩 **Simple logic**:
Try every possible option, and **go back** if it doesn’t work.

Here’s a **simple school-kid level explanation** of **Backtracking vs Recursion**:

---

### 🔁 What is **Recursion**?

> A function that **calls itself** to solve smaller parts of the problem.

🧠 Like climbing stairs:

* To reach the top, you say:
  “I’ll climb one step, then **let recursion handle the rest**.”

---

### 🔙 What is **Backtracking**?

> It's **recursion + undoing** wrong choices.

🧠 Like a maze:

* Try a path → if wrong, **go back** → try another path.

---

### 📊 Key Difference:

| Feature   | Recursion                       | Backtracking                        |
| --------- | ------------------------------- | ----------------------------------- |
| Purpose   | Break problem into smaller ones | Try all possible solutions smartly  |
| Undo step | ❌ Not always needed             | ✅ Always undo after trying a choice |
| Used in   | Fibonacci, Tree Traversal       | N-Queens, Sudoku, Maze, Word Break  |

---

### 🍩 Analogy:

* **Recursion**: Baking a cake layer by layer.
* **Backtracking**: Trying all cake designs, undoing bad ones, keeping the best!

In **DSA (Data Structures & Algorithms)**, here’s how **Recursion vs Backtracking** work:

---

### 🔁 **Recursion in DSA**

* A problem is broken into **smaller subproblems**.
* It’s used when the solution **depends on previous smaller solutions**.

🧠 Examples:

* Fibonacci Series
* Factorial
* Tree Traversal (Inorder, Preorder, Postorder)
* Binary Search

---

### 🔙 **Backtracking in DSA**

* A special kind of **recursive algorithm**.
* It **tries all possibilities** and **removes (undoes)** the ones that don’t work.
* It's used when we need to **build combinations or paths** under **constraints**.

🧠 Examples:

* N-Queens
* Sudoku Solver
* Word Break
* Rat in a Maze
* Subsets, Permutations, Combinations

---

### 🧩 Summary Table:

| Feature   | Recursion              | Backtracking                              |
| --------- | ---------------------- | ----------------------------------------- |
| Type      | Basic concept          | Advanced form of recursion                |
| Goal      | Solve subproblems      | Explore all paths under constraints       |
| Undo Step | ❌ Not required         | ✅ Must undo before trying next option     |
| Used For  | Calculation, traversal | Problem-solving with multiple valid paths |



### ✅ Algorithm for "77. Combinations" using Backtracking:

1. **Initialize** an empty result array `res` to store all combinations.
2. Define a **backtrack function**:

   * Takes `start` (current number to consider) and `path` (current combination).
   * If `path.length == k`, push a copy of `path` to `res` and return.
3. **Loop** from `start` to `n`:

   * Add current number `i` to `path`.
   * Recursively call `backtrack(i + 1, path)`.
   * Remove last element from `path` (backtrack).
4. Start the process with `backtrack(1, [])`.
5. Return the `res` array.

This ensures:

* Each combination is of size `k`.
* No duplicates due to increasing start index.


function combine(n: number, k: number): number[][] {
  const result: number[][] = [];

  function backtrack(start: number, path: number[]) {
    if (path.length === k) {
      result.push([...path]);
      return;
    }

    for (let i = start; i <= n; i++) {
      path.push(i);
      backtrack(i + 1, path);
      path.pop(); // backtrack
    }
  }

  backtrack(1, []);
  return result;
}

### ✅ Time and Space Complexity of **"77. Combinations"**

#### **Time Complexity: O(C(n, k) × k)**

* There are **C(n, k)** combinations (n choose k).
* Each combination takes **O(k)** time to build/copy.
* So total time: **O(C(n, k) × k)**

#### **Space Complexity: O(k + C(n, k) × k)**

* **O(k)** for recursion stack (max depth of k).
* **O(C(n, k) × k)** for storing the result (all combinations).

👉 For `n = 4, k = 2`: C(4, 2) = 6, each of length 2 → Output space = 6 × 2 = 12 units.


Here’s a **backtracking** solution for **"46. Permutations"**:

### ✅ TypeScript Code:

```ts
function permute(nums: number[]): number[][] {
  const result: number[][] = [];

  function backtrack(path: number[], used: boolean[]) {
    if (path.length === nums.length) {
      result.push([...path]);
      return;
    }

    for (let i = 0; i < nums.length; i++) {
      if (used[i]) continue;

      used[i] = true;
      path.push(nums[i]);
      backtrack(path, used);
      path.pop();
      used[i] = false;
    }
  }

  backtrack([], Array(nums.length).fill(false));
  return result;
}
```

---

### ✅ Algorithm:

1. Use a `backtrack` function with `path` (current permutation) and `used` (flags).
2. If `path.length == nums.length`, store it.
3. Loop through each index:

   * Skip if already used.
   * Mark as used, push to path.
   * Recurse and then backtrack (pop and unmark).
4. Start with empty path and used flags.

---

### ✅ Time Complexity: **O(n × n!)**

* Total permutations: **n!**
* Each copy of path: O(n)




### ✅ Space Complexity: **O(n × n!)**



Here’s a **backtracking** solution for **"39. Combination Sum"**:

### ✅ TypeScript Code:

```ts
function combinationSum(candidates: number[], target: number): number[][] {
  const result: number[][] = [];

  function backtrack(start: number, path: number[], sum: number) {
    if (sum === target) {
      result.push([...path]);
      return;
    }

    if (sum > target) return;

    for (let i = start; i < candidates.length; i++) {
      path.push(candidates[i]);
      backtrack(i, path, sum + candidates[i]); // i instead of i+1 for reuse
      path.pop();
    }
  }

  backtrack(0, [], 0);
  return result;
}
```

---

### ✅ Algorithm:

1. Use backtracking with `start`, `path`, and `sum`.
2. If sum matches target, push the path.
3. If sum exceeds target, backtrack.
4. Reuse the same number by calling `backtrack(i, ...)`.

---

### ✅ Time Complexity: **O(2^t)**

* Worst case explores all subsets summing to `target`.

### ✅ Space Complexity: **O(t)** (recursion depth)

* Result space: Depends on number of combinations (≤150 given).


* Result stores n! arrays of size n
* Recursion stack: O(n)
* Used array: O(n)

Here's a **backtracking** solution for **"22. Generate Parentheses"**:

---

### ✅ TypeScript Code:

```ts
function generateParenthesis(n: number): string[] {
  const result: string[] = [];

  function backtrack(open: number, close: number, current: string) {
    if (current.length === 2 * n) {
      result.push(current);
      return;
    }

    if (open < n) backtrack(open + 1, close, current + "(");
    if (close < open) backtrack(open, close + 1, current + ")");
  }

  backtrack(0, 0, "");
  return result;
}
```

---

### ✅ Algorithm:

1. Use `open` and `close` counters to track parentheses.
2. Add `'('` if `open < n`.
3. Add `')'` if `close < open`.
4. Add to result if `current.length === 2 * n`.

---

### ✅ Time Complexity: **O(2^2n)** (bounded by Catalan number `C(n)`)

### ✅ Space Complexity: **O(2n)** (call stack + result storage)



Here’s a **backtracking** solution for **"79. Word Search"**:

---

### ✅ TypeScript Code:

```ts
function exist(board: string[][], word: string): boolean {
  const rows = board.length;
  const cols = board[0].length;

  function backtrack(r: number, c: number, index: number): boolean {
    if (index === word.length) return true;
    if (
      r < 0 || c < 0 || r >= rows || c >= cols ||
      board[r][c] !== word[index]
    ) return false;

    const temp = board[r][c];
    board[r][c] = "#"; // mark as visited

    const found = backtrack(r + 1, c, index + 1) ||
                  backtrack(r - 1, c, index + 1) ||
                  backtrack(r, c + 1, index + 1) ||
                  backtrack(r, c - 1, index + 1);

    board[r][c] = temp; // backtrack
    return found;
  }

  for (let r = 0; r < rows; r++) {
    for (let c = 0; c < cols; c++) {
      if (backtrack(r, c, 0)) return true;
    }
  }

  return false;
}
```

---

### ✅ Algorithm:

1. Try to start DFS from each cell.
2. If character matches, explore 4 directions.
3. Mark visited cells temporarily.
4. Backtrack if path fails.

---

### ✅ Time Complexity: **O(m × n × 4^L)**

* `L = word.length`, `m × n` = grid size
* Each cell can branch up to 4 directions.

### ✅ Space Complexity: **O(L)**

* Call stack up to length of the word.


Here’s a **backtracking** solution for **"52. N-Queens II"** (counting total distinct solutions):

---

### ✅ TypeScript Code:

```ts
function totalNQueens(n: number): number {
  let count = 0;
  const cols = new Set<number>();
  const diag1 = new Set<number>();
  const diag2 = new Set<number>();

  function backtrack(row: number) {
    if (row === n) {
      count++;
      return;
    }

    for (let col = 0; col < n; col++) {
      if (cols.has(col) || diag1.has(row - col) || diag2.has(row + col)) continue;

      cols.add(col);
      diag1.add(row - col);
      diag2.add(row + col);

      backtrack(row + 1);

      cols.delete(col);
      diag1.delete(row - col);
      diag2.delete(row + col);
    }
  }

  backtrack(0);
  return count;
}
```

---

### ✅ Algorithm:

1. Place queens row by row.
2. Track used columns, `\` diagonals (`row - col`), and `/` diagonals (`row + col`).
3. If all rows are filled, increment count.
4. Backtrack after each placement.

---

### ✅ Time Complexity: **O(n!)** (worst case)

### ✅ Space Complexity: **O(n)** (sets + recursion depth)

