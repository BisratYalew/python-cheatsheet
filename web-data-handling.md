# Web Data Handling

- [Make a Request](#make-a-request)
- [Read](#read)
- [Get Code](#get-code)
- [HTML Parsing](#html-parsing)
- [JSON Parsing](#json-parsing)
- [XML Parsing](#xml-parsing)

<br><br>

# Make a Request
```python
import urllib.request ## urllib module is used to send request and receive response from a server. It can used to get html / JSON / XML data from an api.

webData = request.urlopen("http://www.google.com") ## It opens a connection to google.com and returns an object of class http.client.HTTPResponse
```

### Read
```.read()``` return the HTML data of the webpage.

### Get Code
```.getcode()```  returns the status code of the connection establishment. 


### HTML Parsing

```python
from html.parser import HTMLParser

class MyHTMLParser(HTMLParser):
    def error(self, message):
        pass
        
parser = MyHTMLParser()
f = open("check.html")
if f.mode == 'r':  # file successfully opened
    contents = f.read()
    parser.feed(contents)
```

### JSON Parsing
```python
import json
json_data = json.loads(response)
```

### XML Parsing
```python
import xml.dom.minidom
doc = minidom.parse("check.xml")
```


### [Back To Top](#web-data-handling)