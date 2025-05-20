# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
TO IMPLEMENT SLIDING WINDOW PROTOCOL
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
client.py
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
server.py
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUPUT
client.py
![Screenshot 2025-05-20 131553](https://github.com/user-attachments/assets/694c75f3-8997-4141-8aca-3e37c9616c03)

server.py
![image](https://github.com/user-attachments/assets/f33efcc6-2bf3-41d5-a199-b623bf86647f)

## RESULT
Thus, python program to IMPLEMENT SLIDING WINDOW PROTOCOL was successfully executed
