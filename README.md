# Firewall Configuration Using iptables

## Description
This project demonstrates a basic firewall configuration using `iptables` on a Linux system. It is designed to control inbound and outbound traffic, block unauthorized IP addresses, and filter specific ports.

## Installation
1. Open your terminal.
2. Copy the provided `iptables` rules.
3. Use the command `iptables-restore < /path/to/your/rules-file` to apply the rules.

## Configuration Overview
- The rules drop traffic on specific ports known to be vulnerable.
- Certain IP addresses have been blocked for security reasons.
- Traffic on ports 80 and 443 (HTTP/HTTPS) is allowed with limits to prevent abuse.

## Usage
- To view the current `iptables` rules, use: `iptables -L -v`
- To save your current rules: `iptables-save > /path/to/save/rules-file`

## Rules Explained
- `-A INPUT -p tcp -m tcp --dport 80 -m limit --limit 10/min --limit-burst 100 -j ACCEPT`: Limits HTTP traffic to prevent abuse.
- `-A INPUT -s 104.234.220.43/32 -j DROP`: Blocks traffic from a specific malicious IP address.
