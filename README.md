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
1. server.py
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
```
2. client.py
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```
## OUTPUT
<img width="1456" height="241" alt="Screenshot 2026-11-03 134115" src="https://github.com/user-attachments/assets/ebf64f84-9bd9-420f-86e5-df86c2ac0da9" />

<img width="1478" height="315" alt="Screenshot 2026-11-03 134015" src="https://github.com/user-attachments/assets/d2340bda-7284-4027-8b20-c0c97da1ddc6" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
