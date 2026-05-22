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
## client.py
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

print(s.recv(1024).decode())
s.send("Acknowledgement Received".encode())

s.close()
```
## server.py
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Server is waiting for connection...")
c, addr = s.accept()
print("Connected with:", addr)

while True:
    i = input("Enter data: ")

    c.send(i.encode())

    ack = c.recv(1024).decode()

    # check if client disconnected
    if not ack:
        print("Client disconnected")
        break

    print("Client:", ack)

    # optional exit condition
    if i.lower() == "exit":
        print("Closing connection...")
        break

c.close()
s.close()
```
## OUTPUT


<img width="1920" height="1080" alt="Screenshot 2026-05-22 112808" src="https://github.com/user-attachments/assets/e56ad2e2-9ebf-453d-839d-8cbbb82efcc3" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
