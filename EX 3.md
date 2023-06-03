# EX-3 IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

# DATE : 20/03/2023

# AIM :
To write a python program to perform sliding window protocol

# ALGORITHM :
```
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client otherwise it
will send NACKsignal to client.
6. Stop the program
```
# PROGRAM :
# CLIENT PROGRAM :
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
 while(i<len(l)):
 st+=s
 c.send(str(l[i:st]).encode())
 ack=c.recv(1024).decode()
 if ack:
 print(ack)
 i+=s

```
# SERVER PROGRAM :
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())

```
# OUTPUT :
# CLIENT OUTPUT :
![client3](https://github.com/JeyaKrishnaSJ/EX-3/assets/118707091/d3067054-6023-4751-9602-5443084c6217)


# SERVER OUTPUT :

![server3](https://github.com/JeyaKrishnaSJ/EX-3/assets/118707091/9653e9c0-d83f-4b4b-ba4b-9e2d3a6b782d)


# RESULT:
Thus, python program to perform sliding window protocol was successfully executed.
