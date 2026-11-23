# Day 33 - 2026-11-23

## JavaScript: Simple Demo (TryHackMe)
Room completed: 100% (all 6 tasks)

## The idea
JavaScript is used in most web pages. It first ran only inside web browsers (client side), but **Node.js** lets it run on a server and from the command line too. The room built the same "guess the number" game as the Python room, so I could compare two languages doing the same job.

## What I learned

### Where JavaScript runs
- **In a browser:** open the developer tools (F12) and use the console to run code on a page.
- **With Node.js:** run a file from the terminal with `node filename.js`. This is how the room ran its code.
- **Client side vs server side:** client side runs on the user's device (the browser), and server side runs on the web server. JavaScript now does both.

### Variables and constants
- `let` declares a **variable**, a value that can change later.
- `const` declares a **constant**, a value that cannot change.
- Examples of my own:
  ```javascript
  let failedLogins = 0;
  const maxAttempts = 5;
  ```
- A good habit is to use `const` unless the value really needs to change.
- Comments start with `//`.
- `console.log()` displays output on the screen, like `print()` in Python.

### Getting input and converting it
- A user's input arrives as **text**, so it must be converted to a number before comparing, as in Python.
- `parseInt(text, 10)` converts text to a whole number (the `10` means base 10).
- Reading from the keyboard in Node.js needs extra libraries, because Node.js was built for web servers and not for typing into a terminal.
- `await` pauses the program until the user responds.
- `try` and `finally` run risky code safely and then clean up (such as closing the input channel) even if something goes wrong.

### Conditions
- JavaScript uses `if`, `else if` and `else`, and the conditions go in brackets with the code in curly braces:
  ```javascript
  if (failedLogins > 5) {
      console.log("Possible brute-force attack");
  } else if (failedLogins > 0) {
      console.log("A few failed logins");
  } else {
      console.log("No failed logins");
  }
  ```
- JavaScript checks the conditions in order and runs only the first one that is true.
- Operators: `||` or, `&&` and, `!` not, `<` `>` `<=` `>=`.
- **Equality:** `!==` means not equal, and `===` means equal. The three-character versions compare both the value and the type, and they are the safer choice.

### Loops
- A `while` loop repeats while its condition is true:
  ```javascript
  let attempts = 0;
  while (attempts < 3) {
      console.log("Try again");
      attempts = attempts + 1;
  }
  ```
- The loop must change something so it can end, otherwise it runs forever (an infinite loop).
- A random whole number in a range is made by combining `Math.random()` (a decimal below 1), multiplying, rounding down with `Math.floor()` and adding 1.

## Python vs JavaScript (same game, two languages)
| Idea | Python | JavaScript |
|------|--------|------------|
| Print | `print()` | `console.log()` |
| Variable | `count = 0` | `let count = 0;` |
| Constant | (by convention) | `const max = 5;` |
| Else if | `elif` | `else if` |
| Not equal | `!=` | `!==` |
| Or / and | `or` / `and` | `\|\|` / `&&` |
| Blocks | Indentation | Curly braces `{ }` |
| Comments | `#` | `//` |
| Convert to integer | `int()` | `parseInt()` |
- The logic is the same, and only the writing differs. Once I understand variables, conditions and loops, a new language is mostly new spelling.

## Connection to what I already know
- The Python room (variables, `if`, loops) is the same set of ideas.
- Text vs number input links to data representation and encoding.
- The browser developer tools I used for HTTP requests also run JavaScript.
- Web pages, servers and requests (HTTP, cookies) link to web security.

## Why this matters for security
- **JavaScript runs in the user's browser,** so web security depends on it.
- **Cross-site scripting (XSS):** an attacker gets their JavaScript to run in another user's browser, for example to steal a session cookie. This is why the HttpOnly cookie flag matters: it stops JavaScript from reading the cookie.
- **Never trust client-side checks alone.** A user can change anything that runs in their own browser, so the server must validate input again.
- **Node.js servers** run JavaScript on the server, so mistakes there can expose data and systems.
- **Malicious scripts** often hide in web pages and are sometimes obfuscated, so an analyst needs to read basic JavaScript to understand them.
- I only test web applications that I own or am authorised to test, and I never run unknown scripts outside a safe lab.

## Full forms
- **JS:** JavaScript
- **VM:** Virtual Machine
- **XSS:** Cross-Site Scripting
- **I/O:** Input / Output
- **stdin / stdout:** standard input / standard output

## Practice (from memory)
1. Write a JavaScript `if` / `else if` / `else` for three ranges of failed logins.
2. Write a `while` loop that counts from 1 to 5.
3. Write the same logic in Python, then compare the two.
4. Open the browser console (F12) and run `console.log("hello")`.

## Time and completion
- Time spent: 60 minutes
- Room completed: 100%
