### Basic Network Info
```bash
ip a                # Show IP addresses and interfaces
ifconfig            # Display network interface details
ip addr show        # Detailed IP address info
hostname            # Show system hostname
```
****
### Connectivity and Diagnostics
```bash
ping google.com     # Test connectivity
ping -c 4 google.com # Send 4 ping requests
netstat -tulpn      # List listening ports and processes
nmap -sS host       # Stealth scan ports on a host
arp -a              # Display ARP cache
curl google.com     # Fetch content from a URL
dig google.com      # Query DNS information
traceroute google.com # Trace network path
```
****
### Network Management
```bash
iwconfig            # Show wireless interface details
route -n            # Display routing table
ss -tuln            # List socket statistics (alternative to netstat)
```
