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
# CLIENT:
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
# SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUTPUT
# CLIENT:
![Screenshot 2024-04-10 105933](https://github.com/Dharanya2005/2b_SLIDING_WINDOW_PROTOCOL/assets/145742468/da03a3e2-09d0-495f-bd05-0776d44b097c)
# SERVER:
![Screenshot 2024-04-10 110247](https://github.com/Dharanya2005/2b_SLIDING_WINDOW_PROTOCOL/assets/145742468/10ebd1ba-6f20-43bd-91c6-4ba684518016)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
