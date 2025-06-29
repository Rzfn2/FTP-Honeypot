##  FTP Honeypot - Abdullah FTP Trap

A realistic FTP honeypot built using Python and `pyftpdlib`, designed to simulate a legitimate FTP service while logging all attacker actions. This trap supports anonymous access, realistic bait files, and detailed session logging.

---

## 🔐 Features

* Full FTP server simulation using `pyftpdlib`
* Anonymous access enabled (with restricted permissions)
* Realistic bait files (e.g., `secrets.txt`, `emergency_update_required.txt`)
* Custom login banner for legal warning and realism
* Detailed logging of:

  * FTP logins
  * File downloads/uploads
  * Commands issued
  * Connections and disconnections

---

## 🛠️ Setup Instructions

### 1. 🔧 Install Dependency

```bash
pip install pyftpdlib
```

### 2. 🚀 Run the Honeypot

```bash
sudo python3 ftp_honeypot.py
```

> The script runs on port `21` and listens for incoming FTP connections.

---

## 🧪 Test Access

### From Linux:

```bash
ftp <your-ip>
# Username: anonymous
# Password: (press Enter)
```

Or using `curl`:

```bash
curl ftp://<your-ip> --user anonymous:
```

---

## 🧾 Example Output (Client View)

```text
220 Welcome to Abdullah FTP
This server is for authorized use only. All activity is monitored.

ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rw-r--r--    1 0        0             142 Apr 25 20:19 secrets.txt
-rw-r--r--    1 0        0             345 Apr 25 20:20 emergency_update_required.txt
226 Directory send OK.
```

---

## 🧠 Disclaimer

This project is for **educational and research purposes only**. Deploying a honeypot online may attract real attacks. Ensure you run it in a **safe, isolated environment** and monitor activity responsibly.

---

## 👨‍💻 Author

**Abdullah Banwair**

Contributions and suggestions are welcome!
