## Module 6

### Commit 1 Reflection Notes

First, the code imports the required modules, for example, ```io::{prelude::*, BufReader}``` to provide the input and output functionality, and ```net:{TcpListener, TcpStream}``` to provide the networking functionality to create a TCP server.

In the main function, the ```TcpListener``` binds the server to the desired IP address on port 7878 so that it listens to incoming connections. Then using a for loop, it iterates over the incoming TCP connections and by ```stream.unwrap()```, it extracts the TcpStream from its results wrapper and calls the function ```handle_connection``` to process each incomming connections. 

In ```handle_connection``` function, the BufReader wraps the TcpStream in a buffered reader for efficient line-by-line reading. The reader will read all the lines until an empty line, and collects the request lines into a ```Vec<String>```.  Then the function prints the request to the console. 


