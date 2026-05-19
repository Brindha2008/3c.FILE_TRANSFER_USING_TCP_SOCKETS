# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## NAME:BRINDHA A R
## DATE:20/05/2026
## REG:212225040050
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## CLIENT SIDE
```
import socket

s = socket.socket()

host = socket.gethostname()
port = 60000

s.connect((host, port))
s.send("Hello server!".encode())

with open('received_file', 'wb') as f:
    print('receiving data...')
    while True:
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)

print('Successfully received the file')
s.close()
print('connection closed')
```
## SERVER SIDE
```
import socket

port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)

print("Server listening on port", port)

while True:
    conn, addr = s.accept()
    print("Connected to", addr)
    
    data = conn.recv(1024)
    print('Server received', repr(data))

    filename = "untitiled.txt"
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print('Sent', repr(l))
            l = f.read(1024)
    
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.send('I am Brindha'.encode())
    conn.close()
```
## OUPUT


<img width="1911" height="592" alt="Screenshot 2026-05-19 162301" src="https://github.com/user-attachments/assets/fe8c548e-a26a-4b37-9273-3a7da58448c7" />

<img width="1141" height="436" alt="Screenshot 2026-05-19 162332" src="https://github.com/user-attachments/assets/fc2ce715-a5fa-46af-b5ad-e45702f1ba44" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
