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
server.py
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
       ip=c.recv(1024).decode()
       try:
          c.send(address[ip].encode())
       except KeyError:
          c.send("Not Found".encode())
```
client.py
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
<img width="1247" height="195" alt="image" src="https://github.com/user-attachments/assets/f6aa6639-2dc4-480e-ab7f-3c9025f2e107" />
<img width="1110" height="301" alt="image" src="https://github.com/user-attachments/assets/5982e938-8a47-4e65-9040-905d98992a85" />


## PROGRAM - RARP
Server.py
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
      c.send(address[ip].encode())
    except KeyError:
      c.send("Not Found".encode())
```
Client.py
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
   ip=input("Enter MAC Address : ")
   s.send(ip.encode())
   print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP

<img width="1267" height="271" alt="Screenshot 2026-05-18 185111" src="https://github.com/user-attachments/assets/d8f4fb4b-c850-4a43-9d67-dd19323d9e69" />


<img width="1250" height="275" alt="image" src="https://github.com/user-attachments/assets/1a29b976-eac8-4ebf-abef-4db4531e1021" />




## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
