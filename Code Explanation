## 🧠 Code Explanation — FTP Honeypot

This document provides a segmented, explanation of the core logic in the FTP honeypot.

---

### 📂 Directory and Logging Setup

```python
import os
import logging

os.makedirs("ftp_root", exist_ok=True)
os.makedirs("logs", exist_ok=True)

logging.basicConfig(
    filename="logs/ftp_audit.log",
    level=logging.INFO,
    format="%(asctime)s [%(levelname)s] %(message)s",
    datefmt="%Y-%m-%d %H:%M:%S"
)
```

**Explanation:**

* `os.makedirs()` ensures necessary folders exist without throwing an error if they already do.
* Logging is initialized to record events like connection, command execution, and downloads.

---

### 🪤 Bait File Creation

```python
with open("ftp_root/secrets.txt", "w") as f:
    f.write("user: admin\npassword: 123456")

with open("ftp_root/emergency_update_required.txt", "w") as f:
    f.write("EMERGENCY: Unpatched vulnerability exploited. Fix ASAP!")
```

**Explanation:**

* These files simulate high-value content and provoke attacker interaction.
* File contents are chosen to appear sensitive or urgent.

---

### 🔐 Authorization Configuration

```python
from pyftpdlib.authorizers import DummyAuthorizer

authorizer = DummyAuthorizer()
authorizer.add_anonymous("ftp_root", perm="elr")
```

**Explanation:**

* `DummyAuthorizer` is used to emulate a misconfigured FTP server.
* `add_anonymous` allows anonymous login with permissions:

  * `e`: change directory
  * `l`: list directory
  * `r`: retrieve (download) files

---

### ⚙️ Custom FTP Handler

```python
from pyftpdlib.handlers import FTPHandler

class HoneypotFTPHandler(FTPHandler):
    def on_connect(self):
        logging.info(f"[+] Connected: {self.remote_ip}:{self.remote_port}")

    def on_login(self, username):
        logging.info(f"[+] Login successful: {username}")

    def on_disconnect(self):
        logging.info(f"[-] Disconnected: {self.remote_ip}:{self.remote_port}")

    def on_file_sent(self, file):
        logging.info(f"[+] File downloaded: {file}")

    def on_command(self, cmd, arg):
        logging.info(f"[+] Command: {cmd} {arg if arg else ''}")
```

**Explanation:**

* Subclassing `FTPHandler` enables custom logging of every session.
* `on_connect`, `on_login`, and `on_disconnect` handle session lifecycle.
* `on_file_sent` captures bait file interactions.
* `on_command` logs all FTP instructions and arguments for forensic analysis.

---

### 🖼️ Banner and Handler Configuration

```python
handler = HoneypotFTPHandler
handler.authorizer = authorizer
handler.banner = "220 Welcome to Abdullah FTP\nThis server is for authorized use only. All activity is monitored."
```

**Explanation:**

* Assigns the custom handler and the anonymous-only authorizer.
* The `banner` is a realistic warning shown to connecting users.

---

### 🚀 FTP Server Initialization

```python
from pyftpdlib.servers import FTPServer

address = ("0.0.0.0", 21)
server = FTPServer(address, handler)
server.serve_forever()
```

**Explanation:**

* Binds the FTP server to all network interfaces on port 21.
* `serve_forever()` keeps the server alive for continuous monitoring.

---

## ✅ Conclusion

This honeypot mimics a common misconfiguration (anonymous FTP access) to attract unauthorized users. Every command and file interaction is logged for research or detection purposes.

Let me know if you'd like this broken into smaller docs for modular learning or converted to Markdown for GitHub.
