# 🔐 Python VPN — Built from Scratch

A VPN (Virtual Private Network) implementation built from scratch using Python.
Demonstrates AES-256-CBC encryption, HMAC integrity verification, and secure
tunneling — all explained in beginner-friendly code comments.

> Built for learning and portfolio purposes. Not for production use.

---

## 🤔 What is a VPN?

```
WITHOUT VPN:
Your Computer ──────────────────────────→ Internet
              (anyone can see your data!)

WITH VPN:
Your Computer → [AES-256 ENCRYPTED TUNNEL] → VPN Server → Internet
              (data looks like random noise to anyone watching)
```

---

## 🔐 How Encryption Works (Simply)

```
Your Data: "GET /index.html HTTP/1.1 Host: google.com"
     ↓
[AES-256 Encryption with 256-bit key]
     ↓
Encrypted: "a3f9b2c8d4e1f6a7b3c9d5e2f8a4b1c7d6e3f9a2b5c8d4..."
     ↓
[Send through network — looks like random noise!]
     ↓
[VPN Server decrypts with same key]
     ↓
Original: "GET /index.html HTTP/1.1 Host: google.com"
```

---

## 🛡️ Security Features

| Feature | Implementation | Purpose |
|---|---|---|
| Encryption | AES-256-CBC | Makes data unreadable |
| Key Exchange | Encrypted with shared secret | Secure session key transfer |
| Integrity | HMAC-SHA256 | Detects tampering |
| Forward Secrecy | Random session key per connection | Past sessions stay safe |

---

## 📁 Project Structure

```
python-vpn/
├── crypto.py         # AES-256 encryption + HMAC (fully explained)
├── server.py         # VPN server — receives and decrypts packets
├── client.py         # VPN client — encrypts and sends packets
├── demo.py           # Visual demo of encryption working
├── requirements.txt  # Python dependencies
└── README.md
```

---

## ⚙️ Setup

```bash
# Install dependencies
pip3 install -r requirements.txt --break-system-packages
```

---

## ▶️ Usage

### Step 1 — Run the Demo (see encryption in action)
```bash
python3 demo.py
```

### Step 2 — Start the VPN Server
```bash
# Terminal 1
python3 server.py
```

### Step 3 — Connect the VPN Client
```bash
# Terminal 2 — Interactive mode (type your own messages)
python3 client.py

# Terminal 2 — Auto demo mode
python3 client.py demo
```

### Step 4 — Test the Encryption Module
```bash
python3 crypto.py
```

---

## 🖥️ Example Output

**Server:**
```
============================================================
   🔐 Python VPN Server
============================================================
   Listening on : 127.0.0.1:5555
   Encryption   : AES-256-CBC + HMAC-SHA256

  [+] Client connected: 127.0.0.1:54321
  [✓] Session key received: a3f9b2c8d4e1f6a7...
  [✓] Secure tunnel established!

  [10:30:15] Packet #1
  Encrypted size : 96 bytes
  Decrypted size : 42 bytes
  Content        : Hello VPN Server! This is encrypted.
```

**Client:**
```
  [*] Connecting to VPN server 127.0.0.1:5555...
  [✓] TCP connection established
  [✓] VPN Tunnel established!
  [✓] All traffic is now AES-256 encrypted

  VPN> Hello, internet!
  Original  : Hello, internet!
  Encrypted : a3f9b2c8d4e1f6a7b3c9d5e2f8a4b1c7...
  Size      : 16 → 64 bytes (encrypted)
```

---

## 🧠 Key Concepts Explained in Code

### AES-256-CBC Encryption (`crypto.py`)
- How AES block cipher works
- What CBC (Cipher Block Chaining) mode does
- Why we need an IV (Initialization Vector)
- How PKCS7 padding works

### HMAC Integrity (`crypto.py`)
- What HMAC-SHA256 is
- How it detects packet tampering
- Why we verify before decrypting

### Session Keys (`client.py`)
- What Perfect Forward Secrecy means
- Why we use two keys (shared secret + session key)
- How the handshake works

---

## 💼 Resume Bullet Points

- Built a VPN from scratch using Python sockets with AES-256-CBC encryption
- Implemented HMAC-SHA256 for packet integrity verification
- Designed secure key exchange using encrypted session keys
- Demonstrated Perfect Forward Secrecy with per-connection random session keys
- Added multi-client support using Python threading

---

## 🛠️ Tech Stack

`Python 3` · `cryptography` · `socket` · `threading` · `AES-256-CBC` · `HMAC-SHA256`

---

## ⚠️ Disclaimer

This VPN is built for **educational purposes** to understand how VPNs work internally.
It is **not production-ready** — use WireGuard or OpenVPN for real privacy needs.

---

## 👩‍💻 Author

**Rishita Sharma**
- GitHub: [@RISHITASHARMA01](https://github.com/RISHITASHARMA01)
- Email: sharmarishita0111@gmail.com
