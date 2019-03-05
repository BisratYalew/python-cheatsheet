# Web Data Handling

- [Make a Request](#make-a-request)
- [Read](#read)
- [Get Code](#get-code)

<br><br>

```python
import urllib ## urllib module is used to send request and receive response from a server. It can used to get html / JSON / XML data from an api.

webData = urllib.request.urlopen("http://www.google.com") ## It opens a connectio to google.com and returns an object of class http.client.HTTPResponse
```