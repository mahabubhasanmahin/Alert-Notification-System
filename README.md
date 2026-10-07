# 🔔 Alert & Notification System

A multi-threaded client-server messaging and alert management application built with **Java SE**, **Swing GUI**, and **TCP Socket Programming**[cite: 5, 7]. Designed for real-time notification broadcasting, status tracking, and direct administrative replies across multiple connected clients[cite: 4, 5, 6].

---

## 📸 Application Workflow & Screenshots

### 1. System Startup & Connection
| Server Running (Figure 3.2) | Client Connected (Figure 3.3) |
| :---: | :---: |
| ![Server Running](screenshots/01-server-start.png) | ![Client Connected](screenshots/02-client-connected.png) |
| *Server listening on port 5050 with thread pool initialized[cite: 15, 21].* | *Client auto-assigns ID and successfully connects to `localhost:5050`[cite: 10, 21].* |

---

### 2. Alert Transmission & Management
| Incoming Alert Popup (Figure 3.4) | Inspect Message & Read Status (Figure 3.5) |
| :---: | :---: |
| ![Server Alert Received](screenshots/03-server-alert-received.png) | ![Server Message Details](screenshots/04-server-message-details.png) |
| *Server receives incoming alert with visual popup and auditory beep[cite: 16, 22].* | *Selecting an alert displays sender details, timestamp, and marks it as read[cite: 15, 17, 23].* |

---

### 3. Direct Replies & Multi-Client Concurrency
| Server Reply on Client (Figure 3.8) | Multi-Client Handling (Figure 3.9) |
| :---: | :---: |
| ![Client Reply Received](screenshots/05-client-reply-received.png) | ![Multi Client Handling](screenshots/06-multi-client-handling.png) |
| *Client receives administrative reply with an auto-closing popup[cite: 12, 24].* | *Simultaneous handling of multiple clients (`Client_0`, `Client_15`) via multi-threading[cite: 24].* |

---

## 🚀 Key Features

### 🖥️ Server Side (`ServerApp`)
- **Port Configuration**: Start and stop listening on any configurable network port (default: `5050`)[cite: 6, 13, 15].
- **Thread Pool Architecture**: Uses Java's `ExecutorService` (Cached Thread Pool) to concurrently serve multiple clients without blocking the user interface[cite: 5, 15].
- **Alert Dashboard**:
  - Unread alerts are styled in **bold**, while read alerts appear in plain font[cite: 19].
  - Inspect message metadata: sender identifier, network address key (`IP:Port`), timestamp, and read status[cite: 15, 17].
  - Mark individual items or all alerts as read with live counter updates[cite: 6, 16, 17].
- **Auditory & Visual Notifications**: Toggle system beep alerts (`Toolkit.beep()`) and modal popup notifications on arrival of new messages[cite: 6, 16].
- **Targeted Reply**: Send direct responses back to specific clients via dedicated output streams[cite: 6, 17].

### 💻 Client Side (`ClientApp`)
- **Persistent Client ID**: Automatically generates and increments unique client names (e.g., `Client_0`, `Client_1`, `Client_15`) using a local sequence counter (`client_counter.txt`)[cite: 5, 9, 10, 24].
- **Connection Control**: Intuitive interface to connect and disconnect safely from the central server[cite: 5, 7, 9].
- **Message Transmission**: Formats and streams tab-delimited messages (`ClientName \t Message`) through socket streams[cite: 11, 18].
- **Temporary Popups**: Incoming replies trigger an auto-closing popup dialog that dismisses automatically after 3 seconds[cite: 12].

---

## 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| **Programming Language** | Java SE (JDK 8+)[cite: 5] |
| **Graphical User Interface (GUI)** | Java Swing & AWT (`JFrame`, `JSplitPane`, `JList`, `BorderLayout`)[cite: 5, 9, 13, 14] |
| **Networking** | Java Socket API (`Socket`, `ServerSocket`)[cite: 5] |
| **Concurrency & Multithreading** | Java Concurrency API (`ExecutorService`, Thread Pools)[cite: 5, 15] |
| **Storage / Persistence** | File-based I/O (`client_counter.txt`)[cite: 5, 9] |

---

## 📂 Project Structure

```text
Alert-Notification-System/
├── screenshots/
│   ├── 01-server-start.png
│   ├── 02-client-connected.png
│   ├── 03-server-alert-received.png
│   ├── 04-server-message-details.png
│   ├── 05-client-reply-received.png
│   └── 06-multi-client-handling.png
├── src/
│   └── com/
│       └── mycompany/
│           └── notification/
│               ├── ClientApp.java       # Client GUI & Socket listener thread
│               └── ServerApp.java       # Server GUI, ClientHandler & Alert model
├── client_counter.txt                   # Stores client sequence count
└── README.md
```
[cite: 9, 13]

---

## ⚙️ How to Run

### 1. Compile the Source Code
Compile all Java source files into a target directory (`bin`):
```bash
javac -d bin src/com/mycompany/notification/*.java
```

### 2. Launch the Server
Start the server instance before launching any clients:
```bash
java -cp bin com.mycompany.notification.ServerApp
```
- Keep the default port (`5050`) or enter a custom port, then click **Start**[cite: 13, 15].

### 3. Launch Client(s)
Open a separate terminal window for each client you want to connect[cite: 4, 24]:
```bash
java -cp bin com.mycompany.notification.ClientApp
```
- Verify the server address (`localhost:5050`) and click **Connect**[cite: 9, 10].
- Type your message in the input box and click **Send**[cite: 10, 11].

---

## 🔮 Limitations & Future Enhancements

- **Database Integration**: Integrate relational databases (e.g., MySQL or SQLite) to persist message history across server restarts[cite: 25].
- **Security & Encryption**: Implement SSL/TLS socket encryption to safeguard communication against eavesdropping[cite: 25].
- **User Authentication**: Incorporate login credentials and role-based permissions[cite: 25].
- **Modern Interface**: Upgrade legacy Swing components to JavaFX or a modern web-based UI[cite: 25].
- **External Notifications**: Integrate SMS/Email notification gateways for critical alerts[cite: 25].

---

## 👥 Contributors

- **MD MAHABUB HASAN MAHIN** — ID: 231902056[cite: 2]
- **MAJAHARUL ISLAM** — ID: 231902050[cite: 2]

*Department of Computer Science and Engineering (CSE)*[cite: 2]  
*Green University of Bangladesh*[cite: 2]  
*Course: CSE 312 - Computer Networking Lab*[cite: 2]
