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
cliend side:
```
import socket

s = socket.socket()

s.bind(('localhost', 8000))

s.listen(5)

c, addr = s.accept()

address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}

while True:
    ip = c.recv(1024).decode()

    try:
        c.send(address[ip].encode())

    except KeyError:
        c.send("Not Found".encode())
```
server side:
```
import socket

s = socket.socket()

s.connect(('localhost', 8000))

while True:
    ip = input("Enter logical Address : ")

    s.send(ip.encode())

    print("MAC Address:", s.recv(1024).decode())
```
## OUPUT - ARP
<img width="490" height="272" alt="image" src="https://github.com/user-attachments/assets/eb716b21-3cc0-42f6-8797-48238db0eebd" />
<img width="501" height="291" alt="image" src="https://github.com/user-attachments/assets/899d3de1-3cff-418f-8482-88e5260ad5fc" />

## PROGRAM - RARP
client side:
```
import socket

s = socket.socket()

s.bind(('localhost', 9000))

s.listen(5)

c, addr = s.accept()

address = {
    "6A:08:AA:C2": "192.168.1.100",
    "8A:BC:E3:FA": "192.168.1.99"
}

while True:
    ip = c.recv(1024).decode()

    try:
        c.send(address[ip].encode())

    except KeyError:
        c.send("Not Found".encode())
```
server side:

```
import socket

s = socket.socket()

s.connect(('localhost', 9000))

while True:
    mac = input("Enter MAC Address : ")

    s.send(mac.encode())

    print("Logical Address:", s.recv(1024).decode())
```
## OUPUT -RARP

<img width="490" height="190" alt="image" src="https://github.com/user-attachments/assets/520d2b87-626e-4229-aefe-26766c4e4c2d" />
<img width="997" height="280" alt="image" src="https://github.com/user-attachments/assets/d5f7ee9c-389d-45b1-afe2-48756923ab3b" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
