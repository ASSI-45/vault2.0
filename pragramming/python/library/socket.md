- --
This is a library for internet connections using TCP/Ip and UDP. 

Here is a diagram showing how the **TCP** connections are established.
![[2025-12-12_09-23-26_5xDec.png]]

Now you may have an idea what where getting are self into.

**_Note!:_** There is a another library for handling **_[[socketserver]]_**.

-- -

Starting in the top left-hand column, note the API calls that the server makes to set up a “listening” socket:

    socket()
    .bind()
    .listen()
    .accept()

A listening socket does just what its name suggests. It listens for connections from clients. When a client connects, the server calls .accept() to accept, or complete, the connection.

The client calls .connect() to establish a connection to the server and initiate the three-way handshake. The handshake step is important because it ensures that each side of the connection is reachable in the network, in other words that the client can reach the server and vice-versa. It may be that only one host, client, or server can reach the other.

In the middle is the round-trip section, where data is exchanged between the client and server using calls to .send() and .recv().

At the bottom, the client and server close their respective sockets
[source](https://realpython.com/python-sockets/)

# basic server
-- -
Its nothing glamorous but it well accept a connection from a client. At this point is won't serve no static html. Just accept connections.

```python
def start_server():
    # Create a TCP socket using IPv4 (AF_INET) and TCP (SOCK_STREAM)
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        
        # Bind the socket to a specific host (IP) and port
        s.bind((HOST, PORT))
        
        # Start listening for incoming connections
        s.listen()

        # Accept a client connection; this returns a new socket (conn) and the client's address (addr)
        conn, addr = s.accept()

        # Handle the client connection inside this context
        with conn:
            print(f"Connected by {addr}")
            
            # Keep receiving data from the client until they disconnect
            while True:
                data = conn.recv(1024)  # Receive up to 1024 bytes
                if not data:            # If no data is received, the client closed the connection
                    break
                conn.sendall(data)      # Send the received data back to the client (echo)

```


