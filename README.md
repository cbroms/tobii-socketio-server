# Tobii Socket.io Server

This project provides a way to stream eye tracking data from a Tobii consumer eye tracker to the browser. 

## Development

WARNING: It's quite involved to set up the project for development as a result of very poorly maintained and annoying to use dependencies. It's probably easiest to download the pre-build binary and use that. These dependencies are likely to break at any time, so continue only if you're willing to spend time troubleshooting. 

### Socket.io Cpp

For interfacing with the socketio server, this project uses [socket.io-client-cpp](https://github.com/socketio/socket.io-client-cpp), which is abandoned and out of date. To build it, you can follow [their instructions](https://github.com/socketio/socket.io-client-cpp/blob/master/INSTALL.md), making a few adjustments. 

1. Install Boost as [outlined here](https://github.com/socketio/socket.io-client-cpp/blob/master/INSTALL.md#boost-setup). 
2. Clone the client repositiory with:
```
git clone --recurse-submodules https://github.com/socketio/socket.io-client-cpp.git
```
Enter the `websocketpp` lib directory and pull the latest version:
```
cd lib/websocketpp
git pull origin master 
```
3. Return to the repository root and run `cmake` as [described here](https://github.com/socketio/socket.io-client-cpp/blob/master/INSTALL.md#with-cmake). 
4. Build the project by opening in VS 2017 and selecting the `Release` config, then building. 
5. Now you should have a new directory called `Release` containing two files, `sioclient.lib` and `sioclient_tls.lib`. Copy the `sioclient.lib` file to this repository's `/lib/sio` directory. 
6. Copy the header files from socket.io client's `src/` directory to this repository's `/include/sio` directory. 

### Tobii Stream Engine

Next we need to install Tobii's C++ SDK. 

1. Download it [from their website](https://developer.tobii.com/consumer-eye-trackers/stream-engine/getting-started/). 
2. Copy the header files from stream engine's `/include/tobii` directory to this repository's `/include/tobii` directory. 
3. Copy the stream engine lib file from `/lib/tobii/tobii_stream_engine.lib` to this repository's `/lib/tobii` directory. 
4. Copy the stream engine dll file from `/lib/tobii/tobii_stream_engine.dll` to this repository's `x64/Debug/` directory. 

### Run it

Now you should be read to run the C++ project. Open it up in Visual Studio and run it as `x64`. 