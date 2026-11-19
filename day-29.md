# Day 29 - 2026-11-19

## Client-Server Basics (TryHackMe)
Room completed: 100% (all 4 tasks)

## What I learned

### Introduction
- The **client-server model** splits work between two roles:
  - **Client:** asks for something (a browser, a phone app, an email program)
  - **Server:** waits for requests and provides the service (web, email, files, DNS)
- Servers are usually always on, and many clients can use one server at the same time.
- One device can be both: my laptop is a client when it opens a website, and a server if it hosts a page.

### Pizza Delivery (the analogy)
| In the analogy | In the real world |
|----------------|-------------------|
| Customer | Client (browser or app) |
| Pizzeria | Server |
| Phone number or address | IP address and domain name |
| The order | Request |
| The pizza arriving | Response |
| Delivery route and driver | Network (routers, cables, Wi-Fi) |
| "Sorry, we are closed" or "wrong address" | Error response (for example 404 or 500) |
- The pizzeria does not start the conversation. It only answers when a customer orders. That is why servers **listen** and clients **connect**.
- If the order is unclear, the pizzeria cannot do the right thing, so requests must follow agreed rules (a **protocol**).

### Web Communication in Practice
What happens when I open a website:
1. I type a name in the browser (the client).
2. **DNS** turns the name into the server's IP address.
3. The browser connects to the server, using **TCP** and a **port** (usually 80 for HTTP or 443 for HTTPS).
4. The browser sends an **HTTP request**, for example GET for a page.
5. The server processes it and sends back an **HTTP response** with a status code (such as 200) and the content.
6. The browser reads the response and shows the page, and may send more requests for images, scripts and styles.
- **Ports** let one server run many services at once: the IP address finds the machine, and the port finds the service.
- HTTP is **stateless**, so cookies help the server remember who I am.
- **HTTPS** adds encryption, so the content cannot be read on the way.

### Common server types
| Server | Typical port | Job |
|--------|--------------|-----|
| Web (HTTP / HTTPS) | 80 / 443 | Web pages |
| SSH | 22 | Encrypted remote command line |
| DNS | 53 | Names to IP addresses |
| Mail (SMTP) | 25 | Sending email |
| File and others | varies | Shared files, databases |

## Connection to what I already know
- DNS, HTTP, status codes, cookies and HTTPS all fit into this one picture.
- The OSI and TCP/IP layers explain how each step travels: the application talks HTTP, TCP delivers it, IP routes it, and the network carries it.
- SSH is another client-server pair: an SSH client connects to an SSH server.
- A directory scanner like dirb is a client that sends many requests, and a web server shows each one in its log.

## Why this matters for security
- **Every server is exposed to requests,** so every open port is a possible way in. Defenders keep only the needed ports open and check them (for example with `ss -tulpn` on Linux).
- **Servers log requests.** A SOC analyst reads those logs: a flood of failed logins or hundreds of 404s from one IP is a client behaving suspiciously.
- **Never trust the client.** Attackers can send anything in a request, so servers must check and validate input.
- **Servers are attractive targets** because they hold data and serve many users, so they need patching, strong authentication and monitoring.
- **Denial of service** attacks work by overloading a server with requests, which hits availability.
- I only send requests to systems I own or am authorised to test.

## Time and completion
- Time spent: 1 hour
- Room completed: 100%
