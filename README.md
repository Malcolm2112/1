import socket 

target = input(Enter target IP: ")
ports = [21, 22, 23, 80, 443] 

def scan_port(ip, port): 
  try: 
      sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM) 
      sock.settimeout(1)
      result = sock.connect_ex((ip, port)) 

      if result == 0: 
          print(f"[+] Port {port} is OPEN")
      else: 
        print(f"[-] Port {port} is CLOSED")

      sock.close()
    except Exception as e: 
      print(f"Error: {e}") 

for port in ports: 
    scan_port(target, port)
