# Asyncio


- [Definition](#definition)
- [asyncio.run](#asyncio.run)
- [Copy File](#copy-a-file)
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