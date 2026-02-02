# 💬 Real-Time Chat Application

A modern, real-time chat application built with **Go** (backend) and **React** (frontend), featuring WebSocket communication for instant messaging.

![Chat App Demo](https://img.shields.io/badge/Status-Active-success?style=flat-square)
![Go Version](https://img.shields.io/badge/Go-1.21+-00ADD8?style=flat-square&logo=go)
![React Version](https://img.shields.io/badge/React-18.0+-61DAFB?style=flat-square&logo=react)

---

## 🌟 Features

- ✅ **Real-time messaging** using WebSockets
- ✅ **Multi-user support** - Multiple users can chat simultaneously
- ✅ **Instant notifications** - See when users join/leave
- ✅ **Modern UI** - Clean, professional design with smooth animations
- ✅ **Responsive design** - Works on desktop and mobile
- ✅ **Lightweight** - Minimal dependencies

---

## 🛠️ Tech Stack

### Backend
- **Go** - High-performance backend server
- **Gorilla WebSocket** - WebSocket implementation for Go
- **Goroutines & Channels** - Concurrent message handling

### Frontend
- **React** - Component-based UI framework
- **SCSS** - Styled components with modern CSS
- **WebSocket API** - Real-time browser communication

---

## 📸 Screenshots

### Chat Interface
<img width="3419" height="1915" alt="34F7BBB7-63E8-426E-9E36-9567759F6D5F" src="https://github.com/user-attachments/assets/613b24ed-b6fe-415d-90dc-f52698c3b1eb" />



### Multiple Users
<img width="3419" height="1898" alt="58AB3501-B11A-4C0C-8878-8644148C7F98" src="https://github.com/user-attachments/assets/fbd76fa9-474b-47ba-b6e4-e53bcfca898c" />

## 📸 GIF

![Untitled](https://github.com/user-attachments/assets/265af659-0ec6-4400-bf05-1b433fcb1c9e)




---

## 🚀 Getting Started

### Prerequisites

- **Go** 1.21 or higher ([Download](https://golang.org/dl/))
- **Node.js** 16.0 or higher ([Download](https://nodejs.org/))
- **npm** or **yarn**

### Installation

1. **Clone the repository**
```bash
   git clone https://github.com/YOUR_USERNAME/realtime-chat-go-react.git
   cd realtime-chat-go-react
```

2. **Set up the Backend**
```bash
   # Install Go dependencies
   go mod download
   
   # Run the Go server
   go run main.go
```
   
   Server will start on `http://localhost:9000`

3. **Set up the Frontend**
```bash
   # Navigate to frontend directory
   cd frontend
   
   # Install dependencies
   npm install
   
   # Start the React app
   npm start
```
   
   App will open at `http://localhost:3000`

---

## 📁 Project Structure
```
realtime-chat-go-react/
├── main.go                 # Entry point for Go server
├── go.mod                  # Go module dependencies
├── pkg/
│   └── websocket/
│       ├── client.go       # WebSocket client logic
│       ├── pool.go         # Connection pool management
│       └── websocket.go    # WebSocket upgrade handler
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── ChatHistory/   # Chat message display
│   │   │   ├── ChatInput/      # Message input field
│   │   │   ├── Header/         # App header
│   │   │   └── Message/        # Individual message component
│   │   ├── api/
│   │   │   └── index.js        # WebSocket connection
│   │   ├── App.js              # Main React component
│   │   └── index.js            # React entry point
│   └── package.json
└── README.md
```

---

## 🔧 How It Works

### Architecture Overview
```
┌─────────────┐         WebSocket          ┌─────────────┐
│   Browser   │ ←────────────────────────→ │  Go Server  │
│  (React)    │     ws://localhost:9000    │             │
└─────────────┘                            └─────────────┘
      │                                           │
      │                                           │
      ├── User sends message                      │
      │                                           ├── Receives message
      │                                           ├── Broadcasts to all clients
      │                                           └── Manages connections
      └── Displays messages in real-time
```

### Backend Flow

1. **Server starts** and listens on port `9000`
2. **Pool goroutine** starts, managing client connections
3. **Client connects** via WebSocket upgrade
4. **New goroutine** spawned for each client to read messages
5. **Messages broadcasted** to all connected clients via channels

### Frontend Flow

1. **React app loads** and connects to WebSocket
2. **User types message** and hits Enter
3. **Message sent** to Go server via WebSocket
4. **Server broadcasts** to all clients
5. **All clients receive** and display the message

---

## 🧪 Testing

### Test with Multiple Users

1. **Start the backend**: `go run main.go`
2. **Start the frontend**: `npm start`
3. **Open multiple browser tabs**: `http://localhost:3000`
4. **Type messages** in any tab - they appear in all tabs instantly!

### Expected Behavior

- ✅ When a user connects, all users see "New User Joined..."
- ✅ When a user sends a message, all users receive it
- ✅ When a user disconnects, all users see "User Disconnected..."

---

## 🐛 Troubleshooting

### Backend Issues

**Problem**: `cannot find package github.com/gorilla/websocket`
```bash
# Solution: Install dependencies
go mod download
```

**Problem**: `address already in use`
```bash
# Solution: Kill process on port 9000
# On Mac/Linux:
lsof -ti:9000 | xargs kill -9

# On Windows:
netstat -ano | findstr :9000
taskkill /PID <PID> /F
```

### Frontend Issues

**Problem**: `Cannot find module 'sass'`
```bash
# Solution: Install sass
npm install sass
```

**Problem**: WebSocket connection fails
- ✅ Ensure backend is running on port 9000
- ✅ Check `frontend/src/api/index.js` has correct URL: `ws://localhost:9000/ws`

---

## 🎨 Customization

### Change Port

**Backend** (main.go):
```go
log.Fatal(http.ListenAndServe(":8080", nil))  // Change to 8080
```

**Frontend** (src/api/index.js):
```javascript
var socket = new WebSocket('ws://localhost:8080/ws');  // Update port
```

### Modify Colors

Edit `frontend/src/components/Header/Header.scss`:
```scss
.header {
  background: linear-gradient(135deg, #your-color-1 0%, #your-color-2 100%);
}
```

---

## 📚 Learning Resources

- [Gorilla WebSocket Documentation](https://pkg.go.dev/github.com/gorilla/websocket)
- [React Documentation](https://react.dev)
- [WebSocket API (MDN)](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)
- [Go Concurrency Patterns](https://go.dev/blog/pipelines)

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

---


## 👨‍💻 Author

**Govind YagyaSaini**

- GitHub: [@govindyagyasaini](https://github.com/govindyagyasaini)
- LinkedIn: www.linkedin.com/in/govindyagyasaini

---

## 🙏 Acknowledgments

- [Gorilla WebSocket](https://github.com/gorilla/websocket) for the excellent WebSocket library
- [Create React App](https://create-react-app.dev/) for the React boilerplate
- Tutorial inspiration from [[YouTube Channel Name]](https://www.youtube.com/@AkhilSharmaTech)

---

## 📈 Future Enhancements

- [ ] User authentication
- [ ] Private messaging (DMs)
- [ ] Message persistence (database)
- [ ] File/image sharing
- [ ] Typing indicators
- [ ] User avatars
- [ ] Message reactions (emojis)
- [ ] Dark mode toggle

---

## ⭐ Show Your Support

If you found this project helpful, please give it a ⭐ on GitHub!

---

<div align="center">
  Made with ❤️ and Go
</div>
