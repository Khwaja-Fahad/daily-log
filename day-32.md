# Day 33 - 2026-11-22

## Python: Simple Demo (TryHackMe)
Room completed: 100% (all 5 tasks)

## The idea
Python is a **high-level, general-purpose** programming language. High-level means it hides most of the low-level details, and general-purpose means it is used for web apps, automation scripts, data science and machine learning. The room built a small "guess the number" game to show three core ideas: **variables, conditions and loops**.

## What I learned

### Variables
- A **variable** is a named box that stores a value, for example a number, a piece of text or a counter.
- Example of my own:
  ```python
  failed_logins = 0
  username = "admin"
  ```
- A good habit is to give a variable a starting value before using it, like a counter that begins at zero.
- **Libraries** add ready-made tools. Importing one (for example the `random` library for random numbers) saves me from writing it myself.
- **Functions** do a job when I call them: one shows text on the screen, one reads what the user types, and one converts a value to another type.
- **Input is always text.** What a user types arrives as a string, even if it looks like a number, so it must be converted before comparing numbers. This links to data types and encoding: text and numbers are stored differently.
- To add to a counter: `count = count + 1`.
- Comments start with `#` and explain the code to humans.

### Conditional statements (making decisions)
- A program asks yes/no questions and runs different code for each answer.
- Python uses `if`, then `elif` (else if) for further cases, then `else` for everything left.
- Example of my own:
  ```python
  if failed_logins > 5:
      print("Possible brute-force attack")
  elif failed_logins > 0:
      print("A few failed logins")
  else:
      print("No failed logins")
  ```
- Python checks the conditions **in order** and runs only the first one that is true.
- Comparison operators: `<` less than, `>` greater than, `==` equal, `!=` not equal, `<=` and `>=`.
- Combine conditions with `and`, `or` and `not`.
- **Indentation matters.** The indented lines belong to the condition above them.
- Be careful: `=` stores a value, and `==` compares two values.

### Loops (repeating work)
- A loop repeats a block of code. The `while` loop keeps going **as long as its condition is true**, and stops when it becomes false.
- Real-life comparison: searching a car park row by row until I find a space.
- Example of my own:
  ```python
  attempts = 0
  while attempts < 3:
      print("Try again")
      attempts = attempts + 1
  ```
- A loop must change something so that it can end. If the condition never becomes false, the program runs forever (an **infinite loop**).
- A `for` loop is the other main type. It repeats the code once for each item in a list, for example each line of a log file.

### Reading the example session
The program picked a secret number, took guesses, and gave a hint ("too low" or "too high") until the user was right, counting the tries. Reading code line by line, and predicting what it will print for a given input, is the skill to practise.

## Connection to what I already know
- **Logic and conditions** are the same thinking behind alert rules: if there are more than N failed logins from one IP, raise an alert.
- **Loops** are how a script goes through thousands of log lines automatically.
- **Password guessing** is also a loop: try a value, check the result, repeat. The defence is limiting the number of tries, which is a counter and a condition.
- **Data types:** text vs number, as in data representation and encoding.
- **Command line:** scripts run from the terminal, like the other commands I use.
- My earlier Python work (pandas and NumPy for data) builds on exactly these basics.

## Why this matters for security
- The ExxonMobil job ad lists **basic scripting or automation with Python or PowerShell** as an advantage.
- Analysts use Python to **parse logs**, count events, filter suspicious activity, check IP addresses against lists and automate repeated tasks.
- Understanding code helps me read and judge scripts, including ones an attacker might write, and also AI-written scripts (always read and test before running).
- Attackers also automate with loops (for example password guessing), so knowing how they work helps me defend against them.
- I only run scripts on my own machines or lab machines.

## Full forms
- **VM:** Virtual Machine
- **IDE / editor:** the room used Visual Studio Code (VS Code), a code editor
- **int:** integer (a whole number)
- **str:** string (text)

## Practice (from memory, in my own editor)
1. Write a script with a variable `failed_logins` and an `if` / `elif` / `else` that prints a message for three different ranges.
2. Write a `while` loop that counts from 1 to 5.
3. Change the idea: allow only 3 guesses, then print "Locked out".
4. Next step: write a script that reads a text file of fake log lines and counts the lines containing the word "Failed".

## Time and completion
- Time spent: 60 minutes
- Room completed: 100%
