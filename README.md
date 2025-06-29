##  FTP Honeypot - Abdullah FTP Trap

A deceptive yet harmless FTP server built using Python and `pyftpdlib` to simulate a production environment. It logs all intruder activities, supports anonymous login, and presents realistic bait files to encourage engagement.

---

## 🔐 Features

* ✅ Anonymous login support (realistic attack scenario)
* ✅ Simulated file system with planted sensitive files
* ✅ Logs every session, command, file access, and disconnection
* ✅ Displays a legal banner message
* ✅ Easy to set up and run in isolated environments


---

## 🛠️ Setup Instructions

### 1. Install Dependencies

```bash
pip install pyftpdlib
```

### 2. Run the FTP Honeypot

```bash
sudo python3 ftp_honeypot.py
```

> ⚠️ Run with `sudo` to bind to port 21 (privileged port).

---

## 🧪 How to Access (Test)

### Via Linux FTP Client:

```bash
ftp <your-ip>
Name: anonymous
Password: (just press Enter)
```

### Via `curl`:

```bash
curl ftp://<your-ip> --user anonymous:
```

---

## 🧾 Client View Output Example

```text
220 Welcome to Abdullah FTP
This server is for authorized use only. All activity is monitored.

ftp> ls
-rw-r--r--    1 0        0             142 secrets.txt
-rw-r--r--    1 0        0             345 emergency_update_required.txt
```

---

## 📜 License

MIT License — free for educational and ethical use.

---

## ⚠️ Disclaimer

This project is for **educational and research purposes only**. Deploy only in secure environments. Misuse of this software is strictly prohibited.

---

## 👨‍💻 Author

**Abdullah Banwair**

Suggestions, contributions, and pull requests are welcome!
