## Module 6

### Commit 1 Reflection Notes

First, the code imports the required modules, for example, ```io::{prelude::*, BufReader}``` to provide the input and output functionality, and ```net:{TcpListener, TcpStream}``` to provide the networking functionality to create a TCP server.

In the main function, the ```TcpListener``` binds the server to the desired IP address on port 7878 so that it listens to incoming connections. Then using a for loop, it iterates over the incoming TCP connections and by ```stream.unwrap()```, it extracts the TcpStream from its results wrapper and calls the function ```handle_connection``` to process each incomming connections. 

In ```handle_connection``` function, the BufReader wraps the TcpStream in a buffered reader for efficient line-by-line reading. The reader will read all the lines until an empty line, and collects the request lines into a ```Vec<String>```.  Then the function prints the request to the console. 

### Commit 2 Reflection Notes

![commits 2 screen](/assets/images/commit2-1.png)

The ```handle_connection``` function now can send an HTTP response back to the client instead of being able to just printing the request. 

Now, after reading the incoming request using a buffered reader, it defines a HTTP status 200, to indicate the client that request is successful. The function then reads the content of the file ```hello.html``` into a string and gets the length of the file content. Then it formats the HTTP Response to construct a valid HTTP response. Then by ```stream.write_all()```, it converts the response to bytes and writes it to the TCP stream, sending it back to the client. 

### Commit 3 Reflection Notes

![commits 3 screen](/assets/images/commit3-1.png)

Now, the ```handle_connection``` function can handle 404 response. Instead of reading all the lines, the function now reads the first line of the HTTP request (e.g., ```GET / HTTP/1.1```). If request matches the request ```GET / HTTP/1.1```, it will serve the page ```hello.html``` with a 200 OK status. Otherwise, it will serve the page ```404_bad.html``` with a 404 Not Found status.  