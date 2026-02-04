# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
Server.py

```
import socket
s = socket.socket()
s.connect(('localhost', 8002))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement received from the server".encode())
```
Client.py

```
import socket
s = socket.socket()
s.bind(('localhost',8002))
s.listen(5)
c, addr = s.accept()
ListSize = int(input("Enter the number of frames to send : "))
List = list(range(ListSize))
WindowSize = int(input("Enter Window Size : "))
st, i = 0, 0
while True:
    while(i < ListSize):
        st += WindowSize
        c.send(str(List[i:st]).encode())
        Acknowledgment = c.recv(1024).decode()
        if Acknowledgment:
            print(Acknowledgment)
            i+=st
```
## OUPUT
Server.py

<img width="1106" height="828" alt="image" src="https://github.com/user-attachments/assets/def3d0c0-5455-4e80-83a9-c6652e223a16" />

Client.py

<img width="1106" height="828" alt="Screenshot 2026-02-04 131227" src="https://github.com/user-attachments/assets/8144d1e5-60da-4f57-b0af-adb50ba48a9d" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
