- --
Netcat is a great "little" program. For all network related things.

# nc -lnvp
-- -
This is a **_common_** combo for **Netcat**.

- **`-l`** – Listen mode (netcat waits for incoming connections)  
- **`-n`** – No DNS lookups (faster, no hostname resolution)  
- **`-v`** – Verbose output (shows connection details)  
- **`-p <port>`** – Specifies the local port to listen on  

**Together:**  
`nc -lnvp <port>` starts a netcat server that listens on a port, avoids DNS resolution, prints connection info, and waits for a client to connect.


# `-n` disables DNS resolution.
- --
### What it does:
- Prevents hostname lookups  
- Forces netcat to treat addresses as raw IPs  
- Speeds up commands  
- Useful for scripting, scanning, and avoiding delays


# -a — Version-Specific Behavior
- --

-a is not a universal netcat flag, and its meaning differs by implementation.

In OpenBSD netcat (most modern Linux systems):
-a is not a supported flag — it is ignored or may produce an error.

In some older / classic netcat versions:

### -a may mean one of the following:
* Listen on all local addresses
* Show all listening and connected sockets
* Alias for listen mode (rare)

Because of this inconsistency, -a is generally not recommended unless you know your netcat version supports it.