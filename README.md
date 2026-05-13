# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
**SERVER SIDE:**

```import socket

# Create socket
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind host and port
server.bind(("localhost", 6789))

# Listen for connection
server.listen(1)

print("Server is online...")
print("Waiting for user connection...")

# Accept client
conn, addr = server.accept()

print("Connected with:", addr)

while True:
    # Receive message from client
    message = conn.recv(1024).decode()
    print("Client:", message)

    # Exit condition
    if message.lower() == "exit":
        break

    # Send reply
    reply = input("Server Reply: ")
    conn.send(reply.encode())

server.close()
```
**CLIENT SIDE:**
```
import socket

# Create client socket
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to server
client.connect(("localhost", 6789))

print("Connected to server")

while True:
    # Send message
    msg = input("Client Message: ")
    client.send(msg.encode())

    # Exit condition
    if msg.lower() == "exit":
        break

    # Receive reply
    reply = client.recv(1024).decode()
    print("Server:", reply)

client.close()
```
## CODE

<img width="1920" height="1080" alt="Screenshot 2026-05-13 154017" src="https://github.com/user-attachments/assets/3cd44eaf-7e2b-4ec7-9b06-f8d2719abbc5" />

<img width="1920" height="1080" alt="Screenshot 2026-05-13 154042" src="https://github.com/user-attachments/assets/c2cb435a-95a7-4857-8bed-cfd3753dcbf5" />

## OUTPUT

<img width="1920" height="1080" alt="Screenshot 2026-05-13 154042" src="https://github.com/user-attachments/assets/15043bec-129d-4fae-a7db-e42aa130f4c1" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
