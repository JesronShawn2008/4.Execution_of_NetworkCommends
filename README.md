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

Server
```
import socket
import subprocess
import platform

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
print("Server listening on port 8000...")
c, addr = s.accept()
print("Connected:", addr)

while True:
    command = c.recv(1024).decode().strip()
    if not command or command.lower() == 'exit':
        print("Client disconnected.")
        break

    try:
        # Run ANY command the client sends
        completed = subprocess.run(
            command, 
            capture_output=True, 
            text=True, 
            shell=True
        )
        output = completed.stdout + (completed.stderr or "")
    except Exception as e:
        output = f"Command failed: {e}"

    c.sendall(output.encode('utf-8'))

c.close()
s.close()
```
CLient
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

print("Connected. Type any network command (ipconfig, ping, etc.) or 'exit'.")

while True:
    cmd = input("Enter command: ").strip()
    if not cmd:
        continue

    s.send(cmd.encode('utf-8'))
    
    if cmd.lower() == "exit":
        print("Exiting...")
        break

    output = s.recv(65536).decode()
    print("\n----- RESULT -----")
    print(output)
    print("------------------\n")

s.close()
```
## Output
<img width="1236" height="785" alt="image" src="https://github.com/user-attachments/assets/c20350cc-01d4-41e4-81b9-4b83b986e9c3" />

<img width="1236" height="785" alt="image" src="https://github.com/user-attachments/assets/1c6edfc8-e501-4d6b-9ffa-d10261e4ceb4" />

<img width="1194" height="864" alt="image" src="https://github.com/user-attachments/assets/79540d00-05f9-4724-b2dc-72d23a4963fb" />

<img width="1272" height="155" alt="image" src="https://github.com/user-attachments/assets/c6610003-ad54-4f27-8788-3b23c219aad7" />

<img width="1290" height="863" alt="image" src="https://github.com/user-attachments/assets/74c8d791-6226-4399-a8d3-bf1653bfcee4" />

<img width="1289" height="869" alt="image" src="https://github.com/user-attachments/assets/b0321e41-5b16-4dcd-bf3c-9a666ec54be9" />

<img width="1269" height="824" alt="image" src="https://github.com/user-attachments/assets/6030ca45-8f3b-4100-8b99-fb2f81c33e28" />

<img width="1286" height="389" alt="image" src="https://github.com/user-attachments/assets/fa615d9a-9ab9-4c47-b472-19b432ecebf7" />

<img width="1291" height="364" alt="image" src="https://github.com/user-attachments/assets/6fa1b872-3d47-420d-8165-3a515fa79031" />

<img width="1290" height="409" alt="image" src="https://github.com/user-attachments/assets/d7377837-9b39-48b1-9831-f77e6160eb12" />

<img width="1271" height="830" alt="image" src="https://github.com/user-attachments/assets/bb6cd742-d5cf-4bd7-bfb0-435c7b6adbc5" />

<img width="642" height="432" alt="image" src="https://github.com/user-attachments/assets/7cddb5ec-4391-4bda-95b6-d65828b7fbe6" />

## Result
Thus Execution of Network commands Performed 
