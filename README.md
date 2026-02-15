<div align="center">

# Secure Encrypted Block Storage Service

![Java](https://img.shields.io/badge/Java-17-blue?style=for-the-badge&logo=openjdk)
![TLS](https://img.shields.io/badge/TLS-1.2%2F1.3-green?style=for-the-badge&logo=letsencrypt)
![AES](https://img.shields.io/badge/AES-256--GCM-red?style=for-the-badge&logo=keepassxc)
![Security](https://img.shields.io/badge/Security-Applied%20Cryptography-black?style=for-the-badge&logo=hackaday)

### Course - Computer Systems Security 

*Secure client–server application that allows storing, retrieving and searching **encrypted files** over a TLS connection.*

</div>

## Main Goal

The objective of this project is to design and implement a secure client–server system that provides an encrypted block storage service.

- Confidential storage of files on an untrusted server  
- Integrity and authenticity verification of stored data  
- Secure communication over TLS  
- The ability to search encrypted files using privacy-preserving techniques
- All encryption is performed on the client side, the server never sees plaintext data.

This project demonstrates how modern cryptography can be applied to build a secure remote storage service where the server never has access to plaintext data.

## Features

- **End-to-End Encryption** — File encryption using **AES-256-GCM**
- **Searchable Encryption** — Search files using secure keyword tokens
- **Block Deduplication** — Efficient storage with **SHA-256** hashing
- **Persistent Index** — Local client index for fast file management
- **Encrypted Metadata** — Server stores encrypted data only
- **Multi-Client Support** — Multiple concurrent clients

#### **Client-Side Encryption**
- All files are encrypted on the client before transmission
- Keys are derived from user passwords using **PBKDF2**
- Server has zero knowledge of plaintext data

#### **Secure Communication**
- Encrypted transmission via **TLS 1.2/1.3**
- Certificate-based authentication
- Protection against MITM attacks

#### Data Integrity & Authenticity
- **HMAC-SHA256** for message authentication
- **AEAD (AES-GCM)** for authenticated encryption
- Tamper detection for all stored blocks

#### Privacy-Preserving Search
- Keywords are transformed into secure tokens
- Server can match tokens without knowing the actual keywords
- Search over encrypted data without decryption

## Technologies

| Technology | Purpose |
|------------|---------|
| **Java 17** | Core application language |
| **TCP/TLS Sockets** | Secure network communication |
| **AES-256-GCM** | Authenticated encryption |
| **HMAC-SHA256** | Message authentication |
| **PBKDF2** | Key derivation from passwords |
| **SHA-256** | Block deduplication & integrity |

## Setup Instructions

```bash
## 1 - Gerar Certificados TLS

keytool -genkeypair -alias server -keyalg RSA -keysize 2048 -keystore serverkeystore.jks -storepass changeit -keypass changeit -dname "CN=localhost, OU=Dev, O=Dev, L=City, S=State, C=PT" -validity 3650

keytool -exportcert -alias server -keystore serverkeystore.jks -storepass changeit -rfc -file server.cer

keytool -importcert -alias server -file server.cer -keystore clienttruststore.jks -storepass changeit -noprompt

## 2 - Compilar

javac *.java

## 3 - Executar o Servidor

java BlockStorageServer

## 4 - Executar o Cliente 

java BlockStorageClient

## 5 - Usar o Cliente Teste

java ClTest
java ClTest PUT <ficheiro> <kw1,kw2,...>
java ClTest GET <ficheiro|keyword> [destino]
java ClTest SEARCH <keyword>
java ClTest LIST
java ClTest CHECKINTEGRITY <ficheiro>
```

## Academic Context

This project was developed as part of the **Computer Systems Security** course in the **MSc in Computer Engineering** program at **NOVA School of Science and Technology**.

With the Authors:
- **Tomás Alexandre**  
- **Nicolae Iachimovschi**
