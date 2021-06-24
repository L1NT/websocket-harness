This python script can be placed between traditional web penetration testing tools and WebSocket connections, which does translation from HTTP to WebSocket and back. Think of it like a fuzzing harness that is used for native code.

Example: python websocket-harness.py -p 7080 -u wss://echo.websocket.org/

In the example above, the WebSocket harness will listen on local loopback, and forward any HTTP POST requests to the target WebSocket endpoint (wss://echo.websocket.org/).

Happy bug hunting!
