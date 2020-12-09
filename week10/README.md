# Networking simulation

Pre-requisite: install net-tools (to get netstat) using: ```sudo apt install net-tools```

## Network tools
In this simulation we will use [netcat](https://www.sans.org/security-resources/sec560/netcat_cheat_sheet_v1.pdf) and [netstat](https://linux.die.net/man/8/netstat) to simulate client server communication. Netcat
is a networking utility that reads and writes data across network connections, which means it can act both as a client and a server. It is very powerful and we will only be using it in interactive mode, by typing the data that we want to send on the command line. 
Netstat (short for network statistics) is another powerdful command line tool that records basic statistics on all network activities happening on the computer. While it has many features, it is mostly used to check which ports and addresses are currently active and what state they are in.

## Simulation description
In this simulation we will run netcat in two modes: Server (listening) and Client (connecting).

### Server (listening)
We will be using the following command: ```nc -l -p port``` with the command line arguments being:
*  -l: set the “listen” mode, waits for the incoming connections
*  -p port: choose the local port to listen on, e.g. **-p 9999**

### Client (connecting)
We will be using the following command: ```nc host port``` with the command line arguments being:
*  host: the computer we will connect to, in our case it will be **localhost** (your computer)
*  port: the local port the server is listening on, e.g. **9999**

### Netstat (monitoring)
We will be using the following command: ```netstat -all | grep port``` with the command line arguments being:
* -all: display sockets in all the states (not just connected)
* | grep port: print only the lines that have a specific port number in them, e.g. **| grep 9999** (the port we will be monitoring)


## Simulation commands

Open a terminal window, set its title to **Monitoring** (Menu Terminal > Set Title...) and run the following command: ```netstat -a | grep 9999```. This should not produce any output

Open another terminal window, set its title to **Server** and run the following command: ```nc -l -p 9999```. Again there should be no output

Go back to the monitoring terminal. Running the command again should produce the following:
```
lp2@llp2-vm:~/Desktop$ netstat -a | grep 9999
tcp        0      0 0.0.0.0:9999            0.0.0.0:*               LISTEN 
```
This means that a TCP server is listening for connections on port 9999 from any network card available. 



__Original Article__: 
* https://ubidots.com/blog/how-to-simulate-a-tcpudp-client-using-netcat/
