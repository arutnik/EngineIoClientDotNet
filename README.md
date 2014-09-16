# EngineIoClientDotNet
====================

Engine.IO Client Library for .Net

This is the Engine.IO Client Library for C#, which is ported from the [JavaScript client](https://github.com/LearnBoost/engine.io-client).


## Installation
Nuget install:
```
Install-Package EngineIoClientDotNet
```

## Usage
EngineIoClientDotNet has a similar api to those of the [JavaScript client](https://github.com/LearnBoost/engine.io-client).

You can use `Socket` to connect:

```cs
var socket = new Socket("ws://localhost");
socket.On(Socket.EVENT_OPEN, () =>
{
	socket.Send("hi", () =>
	{
		socket.Send("hi");
		socket.Close();
	});
});
socket.Open();
```

Receiving data
```cs
var socket = new Socket("ws://localhost");
socket.On(Socket.EVENT_OPEN, () =>
{
	socket.On(Socket.EVENT_MESSAGE, (data) =>
	{
		socket.On(Socket.EVENT_MESSAGE, (data) => Console.WriteLine((string)data));
	});
});
socket.Open();            
```

## Features
This library supports all of the features the JS client does, including events, options and upgrading transport.

## Tests
Run tests on windows or linux:
```
git clone https://github.com/Quobject/EngineIoClientDotNet.git
cd EngineIoClientDotNet/grunt
npm install
```
Update `config.json` and add line to hosts file: `127.0.0.1 testme.quobject.com`. 
```
grunt
```
This will start test server and xunit tests for windows. 

In linux this will stop after starting test server. Start xunit tests within a new linux terminal:
```
grunt testClient
```

## License

MIT
