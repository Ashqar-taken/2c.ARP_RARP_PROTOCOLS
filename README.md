# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
```
Developed By: Ashqar Ahamed S.T
Register No: 21224240018
```

**Server:**
```
import socket
s=socket.socket()
s.bind(('localhost',8800))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
**Client:**
```
import socket
s = socket.socket()
s.connect(('localhost',8800))
while True:
    ip=input("Enter Logical Address: ")
    s.send(ip.encode())
    print("MAC address",s.recv(1024).decode())

```

## OUPUT - ARP
<img width="1363" height="1063" alt="image" src="https://github.com/user-attachments/assets/b2e93fc1-bbdc-4f2b-b1ef-83fce2083fa0" />

## PROGRAM - RARP
**Server:**
```
import socket
s = socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr = s.accept()
address = {"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}
while True:
    mac=c.recv(1024).decode()
    try:
        c.send(address[mac].encode())
    except:
        c.send("Not Found".encode())
```
**Client:**
```
import socket
s = socket.socket()
s.connect(('localhost',9000))
while True:
    mac=input("Enter MAC Address: ")
    s.send(mac.encode())
    print("Logical Address: ",s.recv(1024).decode())
```
## OUPUT -RARP
<img width="1456" height="812" alt="image" src="https://github.com/user-attachments/assets/313fcaed-11c7-43a5-ae9a-9a0b5318a010" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
