# Machine Tool Managment Protocol (MTMP)
Machine Tool Managment Protocol is a HTTP based protocol used to interface with common functions for managing Machine Tools such as Load Program, Set Tool Offset, Set Variable, etc.

![Protocol_Diagram](MTMP-Diagram-01.png)

## Purpose
To provide a common HTTP based interface for Loading Programs, Setting Tool Offsets, etc. on a Machine Tool.

## Functions
- Load NC Program
  - POST (/Machine01/Program)
    - Request Body = NC Code File Contents
- Set Tool Offset
  - POST (/Machine01/ToolOffset/14)
    - Request Body = Tool Offset JSON (see below)
- Set Variable
  - PUT (/Machine01/Variable/5601?value=56.123)
  
## Authorization
API Tokens are generated on the MTMP Broker and configured for a specific Machine Connection. A client can then use this API Token to send requests and the Broker can verify that the Client is authorized to make the request.

## Broker
The broker is responsible for hosting the web server used to accept Function Requests. It is also used to host the Adapters that communicate with the machine tool's API.

## Adapter
The Adapters are used to communicate with the specific machine tool API. An example would be a Fanuc Adapter that communicates using the Fanuc FOCAS API.
