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

Client.py

```
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()

size = int(input("Enter number of frames to send : "))
l = list(range(size))
s = int(input("Enter Window Size : "))
st = 0
i = 0

while True:
    while (i < len(l)):
        st = st + s
        c.send(str(l[i:st]).encode())
        ack = c.recv(1024).decode()
        if ack:
            print(ack)
            i += s
```

server.py

```
import socket
s = socket.socket()
s.connect(('localhost', 8000))

while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```
## OUPUT

Client.py

<img width="685" height="299" alt="image" src="https://github.com/user-attachments/assets/c072ffba-d0a1-4577-83ca-fd2177d78393" />

Server.py

<img width="738" height="210" alt="image" src="https://github.com/user-attachments/assets/b515be92-de22-44cd-9515-3afdd20b82e1" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
