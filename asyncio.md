# Asyncio


- [Definition](#definition)
- [asyncio.run](#asyncio.run)
- [Socket with Asyncio](#socket-with-asyncio)
- [Move File](#move-a-file)
- [Readline](#readline)


### Definition

asyncio is a library included in Python 3.5 that supports a programming model where sometimes, operations that would normally block the thread until some other event happened (like getting a response from a network connection) instead allow other code to run on that thread while waiting.

asyncio takes a very, very explicit approach to asynchronous programming: only code written in methods flagged as async can call any code in an asynchronous way.
<br>
<br>

### asyncio.run
This is new in Python 3.7

```python
>>> import asyncio
>>> from concurrent.futures import ThreadPoolExecutor

>>> e = ThreadPoolExecutor()
>>> async def read_file(file_):
...     loop = asyncio.get_event_loop()
...     with open(file_) as f:
...         return (await loop.run_in_executor(e, f.read))
...
>>> ret = asyncio.run(read_file('/etc/passwd'))
```

<br><br>

### Socket with Asyncio
```python
import asyncio
import socket

host = 'localhost'
port = 9527
loop = asyncio.get_event_loop()
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM, 0)
s.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
s.setblocking(False)
s.bind((host, port))
s.listen(10)

async def handler(conn):
    while True:
        msg = await loop.sock_recv(conn, 1024)
        if not msg:
            break
        await loop.sock_sendall(conn, msg)
    conn.close()

async def server():
    while True:
        conn, addr = await loop.sock_accept(s)
        loop.create_task(handler(conn))

loop.create_task(server())
loop.run_forever()
loop.close()
```
```shell
output: (bash 1)

$ nc localhost 9527
Hello
Hello
```
```shell
output: (bash 2)

$ nc localhost 9527
World
World
```