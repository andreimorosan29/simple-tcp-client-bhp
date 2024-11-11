# Simple TCP Client Script in Python BHP Version

## Overview

This repository contains a Python script that demonstrates a basic TCP client implementation using the `socket` module. The script connects to a remote server, sends an HTTP GET request, receives the response, and prints it to the console. This educational example is perfect for anyone wanting to understand low-level networking concepts in Python, showcasing how TCP connections and basic HTTP requests work.

## Features

- Establishes a TCP connection to a specified server and port.
- Sends an HTTP GET request to the server.
- Receives and decodes the response.
- Prints the server's response to the console.

## Code Walkthrough

### 1. Importing Required Module
```python
import socket
```
- The `socket` module provides low-level network communication capabilities, enabling the creation of client-server applications.

### 2. Setting Target Details
```python
target_host = "www.google.com"
target_port = 80
```
- `target_host`: The domain or IP address of the server to connect to.
- `target_port`: The port number used for communication (80 is typically used for HTTP).

### 3. Creating the Socket Object
```python
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
```
- `AF_INET`: Specifies the use of IPv4 addresses.
- `SOCK_STREAM`: Indicates the use of TCP, a reliable, connection-oriented protocol.

### 4. Establishing the Connection
```python
client.connect((target_host, target_port))
```
- Establishes a TCP connection to the server at `target_host` on `target_port`.

### 5. Sending an HTTP GET Request
```python
client.send(b"GET / HTTP/1.1\r\nHost: google.com\r\n\r\n")
```
- Sends an HTTP/1.1 GET request to fetch the root document ('/') from the server.
- Includes the `Host` header to specify the domain.

### 6. Receiving the Response
```python
response = client.recv(4096)
```
- Receives up to 4096 bytes of data from the server.
- The buffer size can be adjusted for larger or smaller data chunks.

### 7. Printing and Closing
```python
print(response.decode())
client.close()
```
- Decodes the byte response to a human-readable string and prints it.
- Closes the socket to free up resources.

## How to Run the Script

1. Ensure Python is installed (Python 3.x recommended).
2. Copy the script into a `.py` file, e.g., `tcp_client.py`.
3. Run the script using:
   ```bash
   python tcp_client.py
   ```

## Explanation of Key Concepts

- **Socket Programming**: Essential for building network-based applications, sockets facilitate client-server communication over a network.
- **HTTP Protocol**: The script demonstrates sending a minimal HTTP GET request using raw sockets without any additional libraries, showcasing the underlying network operation.

## Potential Enhancements

- Add error handling to manage failed connections or timeouts.
- Extend the script to handle responses larger than 4096 bytes.
- Incorporate command-line arguments for flexibility in specifying the target host and port.

## Educational Takeaways

- Understanding TCP socket basics.
- Comprehending HTTP requests and response parsing.
- Building foundational knowledge for more advanced network programming projects.

## License

This project is open-source and available under the [MIT License](LICENSE).

---

Feel free to explore, modify, and expand this simple TCP client to suit more complex networking needs.
