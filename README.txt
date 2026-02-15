# 🔐 Secure Encrypted Block Storage Service

![Java](https://img.shields.io/badge/Java-17-blue)
![TLS](https://img.shields.io/badge/TLS-1.2%2F1.3-green)
![AES](https://img.shields.io/badge/AES-256--GCM-red)
![Security](https://img.shields.io/badge/Security-Applied%20Cryptography-black)

### Computer Systems Security — NOVA FCT

Secure client–server application that allows storing, retrieving and searching **encrypted files** over a TLS connection.  
All encryption is performed on the client side — the server never sees plaintext data.

---

## 🚀 Features

- Encrypted file storage using **AES-256-GCM**
- Secure communication via **TLS sockets**
- Integrity & authenticity verification (HMAC + AEAD)
- **Searchable encryption** using keyword tokens
- Encrypted metadata stored on the server
- Block **deduplication** with SHA-256
- Persistent local client index
- Multi-client support

---

## 🏗️ Architecture

Client encrypts files → sends encrypted blocks → server stores encrypted data.

The server **cannot read file contents or keywords**.

---

## ⚙️ Technologies

- Java  
- TCP / TLS sockets  
- AES-GCM encryption  
- HMAC-SHA256  
- PBKDF2 key derivation  

---

## 🎓 Academic Project

Developed for the course **Computer Systems Security**  
MSc Computer Engineering — NOVA FCT

---

## 👨‍💻 Author

Tomás Alexandre
