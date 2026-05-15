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

### SERVER:

```py
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

### CLIENT:
```py
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
ip=input("Enter logical Address : ")
s.send(ip.encode())
print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP

### SERVER:

<img width="885" height="310" alt="image" src="https://github.com/user-attachments/assets/27a5df57-7440-4339-ae0f-5e9c73cb7d8f" />

### CLIENT:

<img width="902" height="228" alt="image" src="https://github.com/user-attachments/assets/44458b16-d229-47fd-8b71-a4a093f97a8d" />

## PROGRAM - RARP

### SERVER:

```py
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

### CLIENT:

```py
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP

### SERVER:

<img width="977" height="317" alt="image" src="https://github.com/user-attachments/assets/9452ca44-5f0d-4b8e-9d10-f080108e643e" />

### CLIENT:

<img width="838" height="186" alt="image" src="https://github.com/user-attachments/assets/6edab967-a151-4ddc-9d6c-ee50442e8bc7" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
