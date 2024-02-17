# port-scanner
import socket

target = input("[+] Enter the target website in the format 'www.example.com': ")
targetIP = socket.gethostbyname(target)

def scan(targetIP, port):
    try:
      #create new socket
      sock = socket.socket.socket()
      #timeout to handle refused connections
      sock.settimeout(1)
      #connect to host and port
      sock.connect((targetIP, port))
      b = sock.recv(1024)   
      print(f"Port {port} is open on {targetIP} with banner: {b}")
    except:
      print("[-] Port " + str(port) + " is closed")
      pass
    finally:
      sock.close()

for port in range(1, 100):
  scan(targetIP, port)
print("Scan complete")
