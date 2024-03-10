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
#client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send: "))
l=list(range(size))
s=int(input("Enter Window Size: "))
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

# server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recieved from the server".encode())
```
## OUPUT
# client
```
![Screenshot 2024-03-10 230737 - Copy](https://github.com/BaskarUmapathi/2b_SLIDING_WINDOW_PROTOCOL/assets/151434098/6cb64ef1-dfa4-40de-a040-830f4ce4df39)

```
# server
```
![Screenshot 2024-03-10 230737 - Copy](https://github.com/BaskarUmapathi/2b_SLIDING_WINDOW_PROTOCOL/assets/151434098/4f0adad4-e3a0-490f-9c3b-f5ee30f13aee)

```

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
