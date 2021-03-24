# WebSockets

- Websocket technology is a bidirectional full duplex protocol for communication between client and server over the web.
- It has been standardized in 2011 and is fully compatible with HTTP
- WebSockets enables real time applications such as:
    - Chatting Apps
    - Notifications
    - Live feed
    - Multiplayer gaming
    - Progress bar/logging/uploading


#### Why websockets existed?

- HTTP1.0 build on TCP protocol
- HTTP uses request response system so that client always makes a request and the server and server responds to the request. It is not the other way around(okay the server doesn't just randomly send the information to client)

- TCP is expensive it requires memory and all descriptors to be set in the server

- So when client send a request to server an tcp connection is opened and connects closed once the server is responded
- Every HTTP request made in this way establishes tcp connnection and closes once the request is fullfilled by the server. This literally killed the performance

- When HTTP1.1 is introducted, it supported websocketsm, i.e when tcp connection is opened the client and server can communicate continuously and can close connnectino when the communication finishes

- So websockets use persistent TCP connection  as a vehicle to send data from client to server and server to client and they both aware of each other which means they no longer stateless its a stateful connection. 


#### How WebSockets Work?
- WebSockets handshake 
- Initial request is always HTTP which we all know creates a tcp connection, that request then http upgrade tells the server to use it as bidirectional.  
- Once done switches to binary protocol. 
- Ws:// wss:// protocol 


#### WebSockets Pros and Cons

- Pros
    1. Full-duplex no need for constant polling  
    2. compatible with HTTP, so proxies know to deal with it
    3. Firewalls won’t block it doesn’t use a special port

- Cons
    1. Proxying is tricky, lots of proxies and transparent proxies don’t support it yet
    2. Layer 7 load balancing is tricky, timeouts on the load balancer. 
    3. More complicated to implement (simple telnet use HTTP)
    4. Not ideal for all use cases - (microservices)



#### Do you have to use Web Sockets ? ( alternatives  ) 
It is important to note that WebSockets is not the only HTTP realtime based solution, there are other ways to achieve real time such as eventsource, and long polling. 

- Load Balancing with WebSockets (bonus) 
- layer 4 
- Layer 7 (tunnel) 

Longpolling
Eventsource
WebSockets 