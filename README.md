Original project presented at [Derbycon 2019](https://www.irongeek.com/i.php?page=videos/derbycon9/stable-35-old-tools-new-tricks-hacking-websockets-michael-fowl-nick-defoe).

This python script can be placed between traditional web penetration testing tools and WebSocket connections, which does translation from HTTP to WebSocket and back. Think of it like a fuzzing harness that is used for native code.

Setup: this script requires Python 3 and the `websocket-client` module, which can either be installed in your environment or in a virtualenv like so:
```
# to create a new virtualenv in the "./venv/" directory
python -m venv venv
# install the required module(s)
pip install -r requirements.txt

# source the virtualenv in each shell before usage
. venv/bin/activate
```

Example: `.\websocket-harness.py -p 7080 -u wss://echo.websocket.org/`

In the example above, the WebSocket harness will listen on local loopback and specified port (`127.0.0.1:7080`), and forward any HTTP POST request bodies to the target WebSocket endpoint (wss://echo.websocket.org/).

For example, one can create a generic POST request in either Burp's Repeater or Intruder targeting the listening port, such as the following (the same thing can be accomplished by putting `127.0.0.1:7080` into the proxied browser and using the generated request, changing the method to POST and adding the payload):
```
POST / HTTP/1.1
Host: 127.0.0.1:7080
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.102 Safari/537.36
Accept-Encoding: gzip, deflate
Connection: close
Content-Length: 41

{"username":  "foo", "password": "bar"}

```

Happy bug hunting!
