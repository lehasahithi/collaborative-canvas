###🎨 Collaborative Canvas

A Real-Time Multi-User Drawing Application

##📋 Project Overview

Collaborative Canvas is a real-time drawing application that allows multiple users to draw simultaneously on a shared canvas.
It synchronizes brush strokes, erasing actions, and undo/redo operations instantly across all connected clients using WebSockets (via Socket.io).

This project demonstrates real-time data synchronization, canvas rendering efficiency, and state management across multiple clients — built completely with Vanilla JavaScript, HTML5 Canvas, and Node.js.

##🚀 Features

✅ Real-time collaborative drawing using WebSockets
✅ Multiple users can draw simultaneously
✅ Brush, Eraser, Color Picker, and Size Adjustment
✅ Global Undo / Redo across all users
✅ Live user count and latency display
✅ Smooth and modern UI with a glassmorphism theme
✅ Cross-browser support (Chrome, Firefox, Safari)
✅ Works on both desktop and touch devices

##🧠 Tech Stack
Layer	Technology
Frontend	HTML5, CSS3, Vanilla JavaScript
Backend	Node.js, Express.js, Socket.io
Real-time Communication	WebSockets
Rendering	HTML5 Canvas API
##🗂️ Folder Structure
collaborative-canvas/
├── client/
│   ├── index.html          # UI and Canvas
│   ├── style.css           # Styling and layout
│   ├── canvas.js           # Drawing logic and rendering
│   ├── websocket.js        # WebSocket client handling
│   └── main.js             # UI bindings and tool actions
├── server/
│   └── server.js           # Node.js + Socket.io backend
├── package.json            # NPM dependencies and scripts
├── README.md               # Documentation (this file)
└── ARCHITECTURE.md         # Technical architecture explanation

##⚙️ Setup Instructions
1️⃣ Clone the Repository
git clone https://github.com/yourusername/collaborative-canvas.git
cd collaborative-canvas

2️⃣ Install Dependencies
npm install

3️⃣ Start the Application
npm start


By default, the app runs on http://localhost:3000

##🧩 How It Works
#🧵 WebSocket Events
Event	Direction	Description
draw:start	Client → Server	User begins drawing a stroke
draw:point	Client ↔ Server	Streams stroke coordinates during drawing
draw:end	Client → Server	Stroke finalized and broadcasted to all users
undo, redo, clear	Client ↔ Server	Synchronizes global actions
cursor	Client ↔ Server	Sends real-time cursor position
init	Server → Client	Sends initial state and drawing history
#🧮 State Synchronization Logic

The server maintains a global array history[] that stores all strokes.

Each client sends stroke data through WebSocket events.

When new users join, the server sends the current history so their canvas loads instantly.

Undo/Redo commands modify this history and sync the result to all clients.

volatile messages (for cursor and move events) reduce network load.

#🧱 Undo/Redo Strategy

Every stroke drawn is stored in a history stack.

On Undo → the last stroke is popped and moved to a redoStack.

On Redo → a stroke is moved back from redoStack to history.

Each update is broadcast globally to ensure all users have consistent canvas state.

#🪶 UI and Design Highlights

Floating glass-style toolbar with soft shadows

Animated gradient background (Figma-style)

Responsive layout for desktops and tablets

Smooth brush rendering using quadratic curves for natural strokes

Dynamic brush preview that matches selected color and size

#🧠 Architecture Summary

Client Layer (Browser)

Captures user drawing events (mousedown, mousemove, mouseup)

Renders strokes in real time using Canvas API

Sends drawing data to the server via WebSocket

Server Layer (Node + Socket.io)

Broadcasts drawing updates to all connected clients

Maintains the global state of the drawing (history[])

Handles Undo, Redo, Clear, and new user synchronization

Synchronization Model

Full-duplex communication over WebSocket

Stateless drawing operations + centralized state on server

#🧰 Scripts
Command	Description
npm start	Run the app (production mode)
npm run dev	Run with nodemon (development mode)
##📸 Screenshots

#🎨 Canvas in Action

##🧑‍💻 Author

#Lehasahithi Mamidi
AI/ML & Cloud Computing Enthusiast | Software Developer
📧 your.email@example.com

##🏁 Submission Checklist

✅ Working demo on http://localhost:3000
✅ Real-time drawing synchronization tested with 2+ browser tabs
✅ Proper folder structure
✅ README.md and ARCHITECTURE.md included
✅ GitHub repo publicly accessible

##🌟 Future Enhancements

Room-based collaboration (multiple canvases)

Canvas persistence (save and reload sessions)

Mobile drawing optimization

Export canvas as PNG or PDF

Add shapes and text tools

##📜 License

This project is licensed under the MIT License — free to use and modify.

##💬 Acknowledgment

Developed as part of the FLAM Internship Assignment.
Focus: Canvas rendering, real-time sync, and collaborative UI design.

##✅ Now just:

Save this file as README.md

Commit and push:

git add README.md
git commit -m "Added detailed README documentation"
git push
