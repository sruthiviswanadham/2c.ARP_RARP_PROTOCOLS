## EXP NO 2C.SIMULATING ARP /RARP PROTOCOLS

## NAME: VISWANADHAM VENKATA SAI SRUTHI
## REG NO: 212223100061

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

## PROGRAM - ARP
## Client:

```
mport socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; while True:
ip=c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```
## Server:

```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
ip = input("Enter logical address: ")
s.send(ip.encode())
print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
## Client:

![image](https://github.com/sruthiviswanadham/2c.ARP_RARP_PROTOCOLS/assets/151760421/6ebe10c8-3e56-4521-9cd1-cfb600480133)

## Server:

![image](https://github.com/sruthiviswanadham/2c.ARP_RARP_PROTOCOLS/assets/151760421/596a2542-e7c5-40b6-b561-effd76956a6d)

## PROGRAM - RARP
## Client:

```
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr = s.accept()
address = {"6A:08:AA:C2":"165.165.80.1","8A:BC:E3:FA":"165.165.79.1"}
while True:
ip = c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
## Server:
```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
ip = input("Enter MAC address: ")
s.send(ip.encode())
print("Logical Address",s.recv(1024).decode())
```

## OUTPUT -RARP
## Client:

![image](https://github.com/sruthiviswanadham/2c.ARP_RARP_PROTOCOLS/assets/151760421/2d08dc6b-29c6-46ae-8048-e54a2eea8bce)

## Server:

![image](https://github.com/sruthiviswanadham/2c.ARP_RARP_PROTOCOLS/assets/151760421/113ded18-6fab-4b0d-b2e1-8da56e6810b9)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
