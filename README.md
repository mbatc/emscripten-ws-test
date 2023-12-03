# Websocket Emscripten Test

Here I have put together a simple test that opens a connection to a WebSocket server using emscriptens websocket API.

The code here is not original and only has some very minor modifications. I have taken this code for the following,

* [ws/echo.py](https://github.com/buehren/websocket-echo-server-python/blob/main/wsecho.py)
* [src/main.cpp](https://gist.github.com/nus/564e9e57e4c107faa1a45b8332c265b9)

The work motivating this is to cross-compile the [Swift Robotics simulator](https://github.com/jhavl/swift) to WebAssembly. The simulator uses WebSockets to pass messages from the client to the server and (at this stage) is the only component that is not cross-compiled to WebAssembly (see [emscripten-forge/recipes](https://github.com/emscripten-forge/recipes))

# Guide

All you should need to do is run `build.sh`. Then run both `start-http-server.sh` and `start-ws-server.sh` in separate terminals. You should now be able to open `http://127.0.0.1:8000` in your browser and see that "Hello World" has been sent to the WebSocket server, which echoed it back to the browser.

# Details
* `build.sh` builds the WASM binary, JS, and html to the `dist` directory.
* `start-ws-server.sh` simply runs the WebSocket server script `ws/echo.py` hosted on port 8080
* `start-http-server.sh` starts a HTTP server hosted on port 8000, which serves the files in the `dist` directory.
