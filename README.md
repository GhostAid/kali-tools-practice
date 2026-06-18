# 🛠️ Kali Linux Tools Practice

My hands-on practice with professional penetration testing tools on Kali Linux 2026.1

---

## 📡 **Nmap - Network Scanner**

### What I learned:
- Port scanning with `nmap scanme.nmap.org`
- Service version detection (`-sV`)
- Operating system detection (`-O`)
- Aggressive scanning (`-A`)
- Using nmap from inside Metasploit

### Scan Results:

---

## 📡 **Wireshark - Packet Analysis**

### What I captured:
- **DHCP packets** — computers asking for IP addresses
- **ARP packets** — device discovery on the network
- **DNS packets** — website name lookups
- **HTTP packets** — web traffic
- **MDNS packets** — Chromecast/device discovery

### Filters I learned:
| Filter | Purpose |
|--------|---------|
| `http` | Show web traffic |
| `dns` | Show DNS lookups |
| `dhcp` | Show DHCP traffic |
| `arp` | Show ARP traffic |
| `ip.addr == X.X.X.X` | Filter by IP |

---

## 🔑 **Hydra - Password Cracking**

### What I learned:
- Brute-force attacks with wordlists
- Attacking SSH, FTP, and HTTP services
- Using custom wordlists
- Verbose mode (`-vV`) to see every attempt
- Using Kali's built-in wordlists

### Commands I used:
```bash
# Single username attack
hydra -l admin -P passwords.txt ssh://scanme.nmap.org

# Multiple usernames attack
hydra -L users.txt -P passwords.txt ssh://scanme.nmap.org

# Verbose mode (see every attempt)
hydra -l admin -P passwords.txt -vV ssh://scanme.nmap.org


## 💣** Metasploit Framework**

### What I learned:
- Navigating Metasploit with `help` and `search- Using auxiliary modules (scanners)
- Using auxiliary modules(scanners)
- SSH login scanner
- TCP port scanner
- Running nmap from inside Metasploit

### Commands I used:
```bash
# Start Metasploit
sudo msfconsole

# SSH scanner
use auxiliary/scanner/ssh/ssh_login
set RHOSTS scanme.nmap.org
set USERNAME admin
set PASS_FILE /home/ghostaid/my_passwords.txt
run

# Port scanner
use auxiliary/scanner/portscan/tcp
set RHOSTS scanme.nmap.org
set PORTS 1-1000
run

# Run nmap from Metasploit
nmap scanme.nmap.org
