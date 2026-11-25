# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
### SERVER:
```
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server.bind(('localhost', 8000))
server.listen(1)

print("Server is waiting for client...")

conn, addr = server.accept()
print("Client connected:", addr)

while True:
    msg = conn.recv(1024).decode()

    if msg.lower() == 'exit':
        print("Client disconnected")
        break

    print("Client:", msg)

    reply = input("Server: ")
    conn.send(reply.encode())

    if reply.lower() == 'exit':
        break

conn.close()
server.close()
```
### CLIENT:
```
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(('localhost', 8000))

print("Connected to server")

while True:
    msg = input("Client: ")
    client.send(msg.encode())

    if msg.lower() == 'exit':
        break

    reply = client.recv(1024).decode()
    print("Server:", reply)

    if reply.lower() == 'exit':
        break

client.close()
```
## OUPUT
### SERVER & CLIENT:

<img width="1327" height="382" alt="image" src="https://github.com/user-attachments/assets/fd067637-3978-4181-9c1a-a491aed53189" />


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
