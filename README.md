# EX- 2b: IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
# Developed by: KANIMOZHI P
# Reg no:212222230060
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## client
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
## server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
   print(s.recv(1024).decode())
   s.send("acknowledgement recieved from the server".encode())
```
## OUTPUT
![image](https://github.com/user-attachments/assets/4b9690be-3f8e-4846-8d61-b490779c2854)
![image](https://github.com/user-attachments/assets/fb0a9a64-8fe7-442e-86aa-75a949931033)
![image](https://github.com/user-attachments/assets/92c41308-e43e-4c60-b5d1-77d8b807b8ca)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
