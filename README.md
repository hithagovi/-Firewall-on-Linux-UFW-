# Setup and Use a Firewall on Linux (UFW)
## Objective
Configure and test basic firewall rules to allow or block traffic using UFW (Uncomplicated Firewall).

## Tool Used
- UFW on Linux

## Steps Performed
### 1. Enable UFW
```bash
sudo ufw enable

_Output:_  
`Firewall is active and enabled on system startup.`
```
### 2. list current rules
```bash
sudo ufw status
```

### 3. Block Port 23 (Telnet)
```bash
sudo ufw deny 23/tcp
```
### 4. Allow SSH (Port 22)
```bash
sudo ufw allow 22/tcp
```
### 5. Verify Rules
```bash
sudo ufw status
```
**Example Output:**
```
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
23/tcp                     DENY        Anywhere
22/tcp (v6)                ALLOW       Anywhere (v6)
23/tcp (v6)                DENY        Anywhere (v6)
```

### 6. Remove the Test Rule (Restore State)
```bash
sudo ufw delete deny 23/tcp
```
## Testing
- Ran `telnet localhost 23` after blocking port → **Connection refused** (block successful)
- SSH (port 22) remained accessible.


## Firewall Configuration File

To save current rules to a file:
```bash
sudo ufw status > firewall_rules.txt
```
## How UFW Filters Traffic
- **Inbound rules** control traffic entering the system.
- **Outbound rules** control traffic leaving the system.
- **Stateful filtering** tracks active connections and allows related traffic automatically.
- Blocking unused ports (like Telnet 23) reduces the attack surface.

---

## Conclusion
The firewall was configured to:
- **Block Telnet** (Port 23)
- **Allow SSH** (Port 22)

Testing confirmed the rules worked as intended, improving system security by restricting unnecessary services.
