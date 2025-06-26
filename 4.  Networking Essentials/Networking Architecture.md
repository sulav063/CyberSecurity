
Networking architecture defines how devices (nodes) in a network are organized and how they communicate with each other.

## 1. Client-Server Model

- In this architecture, a **central server** provides resources or services, and **client devices** request and consume those services.
- The server is responsible for managing resources, storing data, and handling client requests.
- Common in business and web environments.

### Characteristics:
- Centralized control and management
- Scalable and secure
- Better performance monitoring

### Examples:
- **Web browsing:** A browser (client) requests a webpage from a web server (e.g., Google, Wikipedia).
- **Email services:** An email client (e.g., Outlook) retrieves email from a mail server.
- **Company network:** Employees' PCs (clients) access a shared file server or database server.

### Pros:
- Easy to manage, monitor, and secure
- Centralized data storage and backup
- Efficient for large organizations

### Cons:
- Server failure can affect all clients
- Requires more resources (maintenance, hardware)

---

## 2. Peer-to-Peer (P2P) Model

- In a P2P network, **each device (peer)** can act as both a client and a server.
- Resources (files, printers, etc.) are shared **directly** between devices without a central authority.
- Suitable for small or temporary networks.

### Characteristics:
- Decentralized architecture
- All nodes are equal
- No dedicated server

### Examples:
- **File sharing applications:** BitTorrent allows users to download and upload parts of files simultaneously.
- **LAN gaming:** Multiplayer games on a local network where each computer communicates directly.
- **Bluetooth file transfer** between mobile devices.

### Pros:
- Easy and inexpensive to set up
- No need for dedicated hardware
- Good for small/home networks

### Cons:
- Less secure and harder to manage
- No centralized control or backup
- Poor scalability for large networks

---

## Comparison Table

| Feature           | Client-Server Model           | Peer-to-Peer Model                    |
| ----------------- | ----------------------------- | ------------------------------------- |
| Structure         | Centralized                   | Decentralized                         |
| Resource Location | On central servers            | Shared among peers                    |
| Security          | Easier to enforce             | Harder to control                     |
| Scalability       | High (with investment)        | Poor for large networks               |
| Cost              | Higher setup/maintenance      | Low setup cost                        |
| Example           | Web servers, email, databases | File sharing (BitTorrent), LAN gaming |

