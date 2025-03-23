
"There are two ways to write error-free programs; only the third one works."

- The interaction between Web client(s) and server(s)
- What is the architecture of WEB
- How to develop applications on the back-end

WWW = "World Wide Web" 
	An information space containing resources denoted by global identifiers - URI/IRI

---
## HTTP = "HyperText Transfer Protocol" 
- A reliable request/response protocol
- Standard access port: **80**
- Based on **TCP/IP** stack
- Situated on the [application layer](obsidian://open?vault=Obsidian%20Vault&file=Pasted%20image%2020250323171347.png) 
	
- HTTP/2.0 - [Focused on performance](obsidian://open?vault=Obsidian%20Vault&file=Pasted%20image%2020250323172049.png)
	- Binary messages
	- TCP connection reuse (a single connection per host)
	- Multiplexing (many parallel streams)
	- Sending messages to the client (server push)
- HTTP/3.0 - HTTP over ***QUIC*** *(Quick UDP Internet Connections)*
	- UDP
	- Data stream multiplexing 
	- Data encryption
	- Quick connection establishment

- Web Server
	- daemon ("Protective Spirit") - doesn't require user input

- Web Client
	- browser
	- robot (web crawler)
	- multimedia player
	- native application (desktop/mobile)
	- conversational assistant

---
### HTTP Concepts

- Message
	- request
	- response
- Proxy
	- Managing requests: Who did the request? Is that machine authorized?
	- Intercepts requests
	- Can act as a cache
	- Located in the proximity of the server/client.
	- forward proxy :
		- Near client
		- Intermediary for a group of nearby clients acts of behalf of clients
	- reverse proxy:
		- Near server
		- Intermediary for a group of nearby servers
- Gateways
	- Intermediary that hides the servers (also the reverse proxy does that)
	- Ensure load balancing
	- Short-term data storage: caching
	- Message or request translation (e.g. HTTPS > HTTP)
- Tunnel
	- To encrypt messages - HTTPS protocol - ensures "secure" communication
	- HTTP via TLS (Transport Layer Security)
	- Authentication used on digital certificates + bidirectional data encryption
- Cache
	- Static content
	- Local storage area - in memory, on disc - for the messages (data)
	- Can be both server and/or client side
	- Future requests for that data can be served faster
	- Ensuring Web applications' performance
- Messages
	- HTTP message = header + body
	- Header
		- includes a set of fields
			- field-name ":" [field-value] CRLF     
				CR = Carriage Return \r - code 13
				LR = Line Feed \n - code 10
	- Request
		- ==Method== *Request-URI* **ProtocolVersion** CRLF
		[Message-header]  [CRLF MIME-data]
		- Example: 
			- ==GET== */sabin.buraga/teach/courses/web/* **HTTP/1.1** CRLF
			Host: profs.info.uaic.ro
	- Response
		- HTTP-version Digit Digit Digit Reason
			- Digit Digit Digit is a 3 digit code
			- Reason is an explanation of the 3-digit code

## HTTP Methods

- Methods
	- GET
		- Request - performed by a client - to access a resource's representation
	- HEAD 
		- Similar to get
		- Offers only meta-data (only the header part) (information about the data)
	- PUT
		- Updates a resource representation or, eventually, creates a resource on the Web server
	- POST
		- Creates a resource
		- Example: Data entered into a Web form's field
	- DELETE
		- Erases a resource - it's representation - from the server

> [!NOTE]
>  Traditionally, the Web browser only permits the use of GET and POST methods. (HTML forms)

A method is considered ==**safe**== if it does not modify the server state
	- GET and HEAD are ***SAFE***
	- POST, PUT and DELETE are ***NOT SAFE***

A method is ==***idempotent***== if it can be called many times without different outcomes, returning the same response (representation)
	- GET, HEAD, PUT and DELETE are ***idempotent***
	- POST is not ***idempotent***
Test

