# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

## Output
Client.py:
```import socket
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect(("localhost", 5000))
website = input("Enter website to ping: ")
client.send(website.encode())
result = client.recv(4096).decode()
print("Ping Result:\n")
print(result)
client.close()
```
OUTPUT:

<img width="1152" height="355" alt="Screenshot 2026-03-12 085351" src="https://github.com/user-attachments/assets/a73192b8-f15a-49c1-a9c6-a121ecf42948" />

Server.py:
```
import socket
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind(("localhost", 5000))
server.listen(1)
print("Server is waiting for connection...")
conn, addr = server.accept()
print("Connected by", addr)
website = conn.recv(1024).decode()
print("Client requested to ping:", website)
import os
result = os.popen("ping " + website).read()
conn.send(result.encode())
conn.close()
server.close()
```
OUTPUT:
<img width="906" height="318" alt="Screenshot 2026-03-12 085814" src="https://github.com/user-attachments/assets/bb89a3b5-b55c-4a25-bcfe-5e32b1ae0cda" />

Tracert.py
```
import subprocess
host = "www.google.com"  # Change this to the website or IP you want
result = subprocess.run(["tracert", host], capture_output=True, text=True)
print(result.stdout)
```
OUTPUT:
<img width="847" height="303" alt="Screenshot 2026-03-11 161605" src="https://github.com/user-attachments/assets/c989a715-26e5-4dbc-9188-abd9000eab4f" />

Ping.py
```
import subprocess
host = "www.google.com"  # Replace with any IP or domain
result = subprocess.run(["ping", host], capture_output=True, text=True)
print(result.stdout)
```
OUTPUT:
<img width="758" height="337" alt="Screenshot 2026-03-11 161748" src="https://github.com/user-attachments/assets/0167471f-f9ff-406b-8c94-5edfc8b15f3e" />

Serverping.py:
```
import socket
HOST = '0.0.0.0'  # Listen on all interfaces
PORT = 5001       # Port for ping messages
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind((HOST, PORT))
server_socket.listen(5)
print(f"Ping Server listening on {HOST}:{PORT}...")
while True:
    conn, addr = server_socket.accept()
    print(f"Connection from {addr}")
    try:
        while True:
            data = conn.recv(1024)
            if not data:
                break
            # Reply to client (simulating a ping response)
            conn.sendall(b"Pong")
    except Exception as e:
        print(f"Error: {e}")
    finally:
        conn.close()
        print(f"Connection closed for {addr}")
```
OUTPUT:
<img width="959" height="349" alt="image" src="https://github.com/user-attachments/assets/09b94278-7191-4890-b00b-0643beaee511" />

NETSTAT:
```Netstat stands for network statistics. It’s a command-line tool available on Windows, Linux, and macOS that displays information about network connections, routing tables, and interface statistics. It helps monitor network activity and troubleshoot networking issues.```
<img width="1260" height="707" alt="Screenshot 2026-02-19 101915" src="https://github.com/user-attachments/assets/323ad3bf-c393-4002-9159-7a528ec9a9fa" />

IPCONFIG:
```ipconfig stands for Internet Protocol Configuration. It’s a command-line tool in Windows used to display and manage the IP configuration of network interfaces. It helps you see your network settings, troubleshoot connectivity issues, and release/renew IP addresses.```
<img width="1227" height="836" alt="Screenshot 2026-02-19 101954" src="https://github.com/user-attachments/assets/12cbf44d-0aec-462b-b3a2-f492963ade40" />

PING:
```ping is a network diagnostic command used to test connectivity between your computer and another device on a network or the internet. It works by sending ICMP (Internet Control Message Protocol) Echo Request packets to the target and waiting for a reply (Echo Reply).```
<img width="914" height="294" alt="Screenshot 2026-02-19 102243" src="https://github.com/user-attachments/assets/099d76cd-22b3-4cdd-ba78-4b35e9991813" />

TRACERT:
```tracert stands for Trace Route. It’s a network diagnostic command used to show the path that packets take from your computer to a target host on a network or the internet.```
<img width="973" height="376" alt="image" src="https://github.com/user-attachments/assets/5f67a7ed-7ec9-4224-b5f1-37588c0fb23c" />

Nslookup:
```nslookup stands for Name Server Lookup. It’s a command-line tool used to query DNS (Domain Name System) servers to find information about domain names, IP addresses, and DNS records.```
<img width="507" height="106" alt="Screenshot 2026-02-19 102316" src="https://github.com/user-attachments/assets/b28384be-9a4f-474d-b913-c1f6cabf9161" />

getmac:
```getmac is a Windows command-line tool used to display the MAC (Media Access Control) addresses of the network interfaces on your computer.```
<img width="978" height="202" alt="Screenshot 2026-02-19 102432" src="https://github.com/user-attachments/assets/50d84ca5-08a4-4d60-873d-855774f6bd57" />

Hostname:
```The hostname command is used to display or set the name of a computer on a network. A hostname is a human-readable label that identifies a device in a network, instead of using its IP address.It works on Windows, Linux, and macOS, though the syntax may slightly differ for setting a hostname.```
<img width="309" height="77" alt="Screenshot 2026-02-19 102448" src="https://github.com/user-attachments/assets/f6d5f69c-6b33-4d18-8ac6-2cfb515bd29b" />

ARP:
```arp stands for Address Resolution Protocol. It’s a command-line tool used to view and manage the mapping between IP addresses and MAC addresses on a local network.```
<img width="1031" height="666" alt="Screenshot 2026-02-19 102527" src="https://github.com/user-attachments/assets/1dcd4664-43a7-45c4-a566-ebc66a7d48b3" />

SYSTEM INFO:
```systeminfo is a Windows command-line tool that displays detailed information about your computer and its operating system.It provides a comprehensive overview of hardware, software, and network settings, which is useful for troubleshooting, inventory, or system auditing.```
<img width="1175" height="964" alt="Screenshot 2026-02-19 102607" src="https://github.com/user-attachments/assets/f1274f21-0cc1-485a-b0fa-7d88fc29a6a7" />

##RESULT:
Thus Execution of Network commands Performed



