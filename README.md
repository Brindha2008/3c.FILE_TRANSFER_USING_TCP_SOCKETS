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
    conn.close()
```
## OUPUT

<img width="1170" height="431" alt="Screenshot 2026-05-19 144203" src="https://github.com/user-attachments/assets/46c83b32-0b4b-45b5-b4e3-5c49f6dc60c2" />


<img width="1862" height="628" alt="Screenshot 2026-05-19 144215" src="https://github.com/user-attachments/assets/3cd1ba9a-9b1a-4c51-afd5-1cd98b47800f" />


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
