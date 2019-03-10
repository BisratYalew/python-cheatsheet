# Asyncio


- [Definition](#definition)
- [Write a File](#write-a-file)
- [Copy File](#copy-a-file)
- [Move File](#move-a-file)
- [Readline](#readline)


### Definition

asyncio is a library included in Python 3.5 that supports a programming model where sometimes, operations that would normally block the thread until some other event happened (like getting a response from a network connection) instead allow other code to run on that thread while waiting.

asyncio takes a very, very explicit approach to asynchronous programming: only code written in methods flagged as async can call any code in an asynchronous way.