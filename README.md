# Secure Chat Application

A real-time chat application built with **Java socket programming** and **end-to-end encryption**, designed to demonstrate secure client-server communication over a network.

## Features

- 🔒 **End-to-End Encryption** — messages are encrypted on the sender's side and only decrypted by the intended recipient, keeping content unreadable in transit and on the server
- 💬 **Real-Time Messaging** — low-latency message delivery using Java socket programming (TCP)
- 🔑 **Key Exchange** — secure key exchange protocol to establish a shared encryption key between client and server without exposing it over the network
- 🧵 **Multi-threaded Server** — handles multiple simultaneous client connections without blocking
- 🛡️ **Message Integrity** — safeguards against tampering during transmission
- 👤 **Client Authentication** — verifies user identity before allowing message exchange

## Tech Stack

| Component        | Technology                          |
|-------------------|--------------------------------------|
| Language           | Java                                |
| Networking         | Java Sockets (TCP/IP)               |
| Encryption          | `javax.crypto` (AES / RSA)          |
| Concurrency         | Java Threads                        |

## Architecture

```
┌─────────────┐        Encrypted Socket        ┌─────────────┐
│   Client A   │ ───────────────────────────── │    Server    │
└─────────────┘                                └──────┬──────┘
                                                        │
┌─────────────┐        Encrypted Socket        ┌───────┴──────┐
│   Client B   │ ───────────────────────────── │  Client B    │
└─────────────┘                                └──────────────┘
```

1. Client connects to the server via a TCP socket.
2. Client and server perform a key exchange to establish a shared secret.
3. All subsequent messages are encrypted before being sent and decrypted upon receipt.
4. The server relays encrypted messages between connected clients without ever accessing plaintext content.

## Getting Started

### Prerequisites

- Java JDK 8 or higher
- A terminal / IDE (IntelliJ, Eclipse, or VS Code with Java extensions)

### Installation

```bash
git clone https://github.com/Kasthuri-001/secure-chat-application.git
cd secure-chat-application
```

### Compile

```bash
javac Server.java Client.java
```

### Run the Server

```bash
java Server
```

### Run the Client

In a separate terminal:

```bash
java Client
```

Repeat for additional clients to simulate multiple users chatting simultaneously.

## Usage

1. Start the server first — it will listen for incoming connections on the configured port.
2. Launch one or more client instances.
3. Each client establishes a secure session with the server via key exchange.
4. Type messages in the client console to send encrypted messages to other connected users.
5. Type `bye` (or your configured exit command) to close the connection gracefully.

## Security Notes

- Encryption keys are generated per session and never transmitted in plaintext.
- The server does not store or log decrypted message content.
- This project is intended for **educational purposes** to demonstrate secure communication principles — further hardening (certificate pinning, forward secrecy, replay-attack protection) would be needed for production use.

## Project Structure

```
secure-chat-application/
├── Server.java          # Handles client connections and message relay
├── Client.java          # Client-side connection and messaging logic
├── EncryptionUtils.java # Encryption/decryption and key exchange helpers
└── README.md
```

## Future Improvements

- [ ] Add a GUI (JavaFX or Swing)
- [ ] Support group chat rooms
- [ ] Add file transfer with encryption
- [ ] Implement perfect forward secrecy
- [ ] Add persistent, encrypted message history

## Author

**Kasthuri**

GitHub: [Kasthuri-001](https://github.com/Kasthuri-001)

## License

This project is open source and available under the [MIT License](LICENSE).
