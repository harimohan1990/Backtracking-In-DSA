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

