<div align="center">

# 🔐 Secure Encrypted Block Storage Service

![Java](https://img.shields.io/badge/Java-17-blue?style=for-the-badge&logo=openjdk)
![TLS](https://img.shields.io/badge/TLS-1.2%2F1.3-green?style=for-the-badge&logo=letsencrypt)
![AES](https://img.shields.io/badge/AES-256--GCM-red?style=for-the-badge&logo=keepassxc)
![Security](https://img.shields.io/badge/Security-Applied%20Cryptography-black?style=for-the-badge&logo=hackaday)

### Computer Systems Security — NOVA FCT

*Secure client–server application that allows storing, retrieving and searching **encrypted files** over a TLS connection.*

**All encryption is performed on the client side — the server never sees plaintext data.**

---

</div>

## Features

- **End-to-End Encryption** — File encryption using **AES-256-GCM**
- **Secure Communication** — Encrypted transmission via **TLS sockets**
- **Integrity & Authenticity** — Verification using **HMAC + AEAD**
- **Searchable Encryption** — Search files using secure keyword tokens
- **Block Deduplication** — Efficient storage with **SHA-256** hashing
- **Persistent Index** — Local client index for fast file management
- **Encrypted Metadata** — Server stores encrypted data only
- **Multi-Client Support** — Multiple concurrent clients

---

## Architecture

```
┌──────────┐           ┌──────────────┐           ┌──────────┐ 
│  Client  │  ──────>  │   Encrypt    │  ──────>  │   TLS    │ ──────> ┌──────────┐
│          │           │  (AES-GCM)   │           │  Socket  │
└──────────┘           └──────────────┘           └──────────┘
                                               
```

**The server cannot read file contents or keywords** — All sensitive operations happen client-side.

---

## Technologies

| Technology | Purpose |
|------------|---------|
| **Java 17** | Core application language |
| **TCP/TLS Sockets** | Secure network communication |
| **AES-256-GCM** | Authenticated encryption |
| **HMAC-SHA256** | Message authentication |
| **PBKDF2** | Key derivation from passwords |
| **SHA-256** | Block deduplication & integrity |

---

## Security Features

### Client-Side Encryption
- All files are encrypted on the client before transmission
- Keys are derived from user passwords using **PBKDF2**
- Server has zero knowledge of plaintext data

### Secure Communication
- **TLS 1.2/1.3** for encrypted channels
- Certificate-based authentication
- Protection against MITM attacks

### Data Integrity
- **HMAC-SHA256** for message authentication
- **AEAD** (Authenticated Encryption with Associated Data) via AES-GCM
- Tamper detection for all stored blocks

### Searchable Encryption
- Keywords are transformed into secure tokens
- Server can match tokens without knowing the actual keywords
- Privacy-preserving search functionality

---

## 🚀 How to Run

**Grupo:** Tomás Alexandre (73213) & Nicolae Iachimovschi (73381)

**Password:** `123` (quando pedido)

---

### 1. Gerar Certificados TLS

```bash
keytool -genkeypair -alias server -keyalg RSA -keysize 2048 -keystore serverkeystore.jks -storepass changeit -keypass changeit -dname "CN=localhost, OU=Dev, O=Dev, L=City, S=State, C=PT" -validity 3650

keytool -exportcert -alias server -keystore serverkeystore.jks -storepass changeit -rfc -file server.cer

keytool -importcert -alias server -file server.cer -keystore clienttruststore.jks -storepass changeit -noprompt
```

---

### 2. Compilar

```bash
javac *.java
```

---

### 3. Executar o Servidor

```bash
java BlockStorageServer
```

**⚠️ Deixar este terminal aberto!**

---

### 4. Executar o Cliente (Novo Terminal)

**Cliente Interativo:**
```bash
java BlockStorageClient
```

Menu com opções 1-7:
- 1: Upload file
- 2: Download file  
- 3: Search keyword
- 4: List files
- 5: Check integrity
- 6: Delete file
- 7: Exit

**OU Cliente de Teste:**
```bash
java ClTest
java ClTest PUT <ficheiro> <kw1,kw2,...>
java ClTest GET <ficheiro|keyword> [destino]
java ClTest SEARCH <keyword>
java ClTest LIST
java ClTest CHECKINTEGRITY <ficheiro>
```

---

### 5. Testar com pizza.txt

```bash
java ClTest PUT client/clientfiles/pizza.txt receita
java ClTest LIST
java ClTest SEARCH receita
java ClTest GET pizza.txt
java ClTest GET receita
java ClTest CHECKINTEGRITY pizza.txt
```

Para testar falha de integridade: modificar o conteúdo do block no blockstorage

---

### 6. Encerrar

- **ClTest:** `Ctrl + C`
- **BlockStorageClient:** Opção `7`
- **Servidor:** `Ctrl + C`

---

## Academic Context

This project was developed as part of the **Computer Systems Security** course in the **MSc in Computer Engineering** program at **NOVA School of Science and Technology**.

### Learning Objectives
- Applied cryptography in real-world scenarios
- Secure network protocol design
- Client-server architecture with security focus
- Key management and secure storage

---

## Author

**Tomás Alexandre**  
**Nicolae Iachimovschi**

*MSc Computer Engineering*  
*NOVA School of Science and Technology*

---

## 📄 License

This project is part of an academic assignment at NOVA FCT.

---

<div align="center">

**Built with Security in Mind**

*Faculdade de Ciências e Tecnologia — Universidade NOVA de Lisboa*

</div>
