# Day 18 - 2026-10-27

## HTTP in Detail (TryHackMe)
Room completed: 100% (all 7 tasks)

## What I learned

### What is HTTP(S)?
HTTP (HyperText Transfer Protocol) is the set of rules a browser uses to
request web pages from a server and get them back.
- **HTTPS** is HTTP with encryption (TLS), so nobody in the middle can
  read or change the content. The padlock in the browser shows it.
- Limit: someone watching the network can still see **which site
  (domain) I connect to**, just not what I send or receive.
- Example: HTTP is a postcard anyone can read on the way. HTTPS is the
  same message in a sealed, locked envelope. The envelope still shows
  the destination address.

### Requests and Responses
- The browser sends a **request**, and the server sends back a
  **response**.
- A request has: a method, a path (like `/login`), headers, and
  sometimes a body.
- A response has: a status code, headers, and usually content (the page).
- Example: a restaurant. The request is my order, and the response is
  the food (or "sorry, we're out").

### HTTP Methods
| Method | What it does | Example |
|--------|--------------|---------|
| **GET** | Asks for data | Opening a page |
| **POST** | Sends new data to the server | Submitting a login form |
| **PUT** | Updates or replaces existing data | Changing a username |
| **DELETE** | Removes data | Deleting a user |

Parameters can go in the URL (like `?id=1`) or in the **body** of the
request. Passwords should never be sent in the URL, because URLs get
saved in history and logs.

### HTTP Status Codes
The first digit tells the category:
| Range | Meaning | Example |
|-------|---------|---------|
| 1xx | Information | 100 Continue (rare) |
| 2xx | Success | 200 OK |
| 3xx | Redirect | 301 Moved Permanently |
| 4xx | Client error (my request was wrong) | 404 Not Found, 401 Unauthorized, 403 Forbidden |
| 5xx | Server error (the server has a problem) | 500 Internal Server Error |

- **401:** not logged in, or wrong credentials.
- **403:** the server knows who I am (or doesn't care), but I'm not
  allowed to access this.

On Day 1, `dirb` showed 200 and 301,

### Headers
Headers are extra information sent with requests and responses, as
name and value pairs.
- Request examples: `Host` (which site), `User-Agent` (which browser),
  `Cookie`.
- Response examples: `Content-Type` (what kind of data), `Set-Cookie`,
  `Server`.

### Cookies
HTTP forgets who I am after each request (it is "stateless"). Cookies
fix this: the server gives my browser a small piece of data, and the
browser sends it back each time, so the site knows it is still me.
- Example: a wristband at a festival. Show it, and you don't have to
  prove who you are every time.
- Cookies are used for logins, shopping carts, and settings.
- Sites protect session cookies with flags:
  - **Secure:** the cookie is only sent over HTTPS
  - **HttpOnly:** JavaScript on the page cannot read it, which makes
    it harder to steal

### Making Requests
In the emulator I practised building requests: choosing the method,
the page, and the parameters (in the URL or in the body). I made GET,
POST, PUT and DELETE requests and watched the responses.

## Connection to earlier days
- Day 1: `dirb` tested many pages and showed status codes like 200 and 301.
- Day 15: HTTP is an Application layer protocol and runs over TCP.
- Day 15: HTTP is like Telnet in that both send plain text. HTTPS and
  SSH are the secure versions.
- Day 17: DNS finds the server's IP address first, then HTTP asks it
  for the page.

## Why this matters for security
- **HTTP vs HTTPS:** plain HTTP can be read or changed on the way, so
  logins must only happen over HTTPS.
- **Status codes in logs:** many 404s from one address can mean
  someone is scanning for hidden pages (like `dirb`). Many 401s from
  one address is a strong sign of password guessing. Many 403s can
  mean someone is probing for pages they shouldn't reach.
- **Methods:** a server that lets anyone use DELETE or PUT without
  checking permission is a serious weakness.
- **Cookies:** if an attacker steals a session cookie, they may be able
  to act as me without a password. The Secure and HttpOnly flags help
  protect them.
- **Headers:** the `User-Agent` and other headers show up in logs and
  help defenders investigate.
  
## Time and completion
- Time spent: 30 minutes
- Room completed: 100%
