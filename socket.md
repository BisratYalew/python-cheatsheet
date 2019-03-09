
# Socket
- [Get Hostname](#get-hostname)
- [File Transfer Protocol (ftp) client](#ftp-client)
- [File Transfer Protocol (ftp) server](#ftp-server)

<br><br>
### Get Hostname
```python
>>> import socket
>>> socket.gethostname()
'root@bisratyalew'

>>> hostname = socket.gethostname()

>>> socket.gethostbyname('localhost')
'127.0.0.1'

>>> socket.gethostbyname(hostname) ### Returns ip address
'192.168.1.3'

```

<br><br>
### FTP Client
```python
import socket                   # Import socket module

port = 60000                    # Reserve a port for your service.
s = socket.socket()             # Create a socket object
host = socket.gethostname()     # Get local machine name
s.bind((host, port))            # Bind to the port
s.listen(5)                     # Now wait for client connection.

print('Server listening....')

while True:
    conn, addr = s.accept()     # Establish connection with client.
    print('Got connection from', addr)
    data = conn.recv(1024)
    print('Server received', repr(data))

    filename = 'mytext.txt'
    with open(filename, 'rb') as f:
        in_data = f.read(1024)
        while in_data:
            conn.send(in_data)
            print('Sent ', repr(in_data))
            in_data = f.read(1024)

    print('Done sending')
    conn.send('Thank you for connecting')
    conn.close()


# client side server

import socket                   # Import socket module

s = socket.socket()             # Create a socket object
host = socket.gethostname()     # Get local machine name
port = 60000                    # Reserve a port for your service.

s.connect((host, port))
s.send("Hello server!")

with open('received_file', 'wb') as f:
    print('file opened')
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        # write data to a file
        f.write(data)

f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```

<br><br>

### FTP Server
```python
"""
	File transfer protocol used to send and receive files using FTP server.
	Use credentials to provide access to the FTP client	
"""

from ftplib import FTP
ftp = FTP('xxx.xxx.x.x')  # Enter the ip address or the domain name here
ftp.login(user='username', passwd='password')
ftp.cwd('/Enter the directory here/')

"""
	The file which will be received via the FTP server
	Enter the location of the file where the file is received
"""

def recieve_file():
	file_name = 'example.txt'   """ Enter the location of the file """
	with open(file_name, 'wb') as LocalFile:
		ftp.retrbinary('RETR ' + file_name, LocalFile.write, 1024)
	ftp.quit()

"""
	The file which will be sent via the FTP server
	The file send will be send to the current working directory
"""

def send_file():
	file_name = 'example.txt'   """ Enter the name of the file """
	with open(file_name, 'rb') as LocalFile:
		ftp.storbinary('STOR ' + file_name, LocalFile)
	ftp.quit()

```
<br><br>
### [Back To Top](#socket)