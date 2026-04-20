# Service Portal 📋

A modern web application for employees with a regulatory document database, user authentication, and online status tracking.

## Features ✨

- ✅ **User Authentication** - Simple login system with JWT tokens
- ✅ **Online Status Tracking** - Real-time tracking of who's online and last seen time
- ✅ **Regulatory Database** - Organized document management system
- ✅ **Testing System** - Knowledge assessment tests for employees
- ✅ **WebSocket Support** - Real-time updates using Socket.io
- ✅ **Responsive UI** - Modern React interface

## Tech Stack 🛠️

### Backend
- Node.js + Express
- PostgreSQL
- Socket.io (Real-time communication)
- JWT (Authentication)
- TypeScript

### Frontend
- React 18 + TypeScript
- Vite (Build tool)
- Socket.io Client
- Axios (HTTP client)

## Project Structure 📁

```
service-portal/
├── backend/
│   ├── src/
│   │   ├── server.ts           # Main server file
│   │   ├── models/             # Database models
│   │   ├── routes/             # API routes
│   │   ├── middleware/         # Express middleware
│   │   └── sockets/            # WebSocket handlers
│   ├── package.json
│   └── tsconfig.json
├── frontend/
│   ├── src/
│   │   ├── App.tsx             # Main React component
│   │   ├── App.css             # Styling
│   │   ├── main.tsx            # Entry point
│   │   └── index.css           # Global styles
│   ├── package.json
│   ├── vite.config.ts
│   └── index.html
├── docker-compose.yml          # Docker Compose setup
├── .env.example                # Environment variables template
└── README.md
```

## Quick Start 🚀

### Prerequisites
- Node.js (v18+)
- npm or yarn
- PostgreSQL (or Docker)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/skorpy01/service-portal.git
   cd service-portal
   ```

2. **Setup environment variables**
   ```bash
   cp .env.example .env
   ```

3. **Install dependencies**

   Backend:
   ```bash
   cd backend
   npm install
   ```

   Frontend:
   ```bash
   cd frontend
   npm install
   ```

### Development

**Option 1: Local development (requires PostgreSQL running)**

Terminal 1 - Backend:
```bash
cd backend
npm run dev
```

Terminal 2 - Frontend:
```bash
cd frontend
npm run dev
```

**Option 2: Docker Compose (recommended)**
```bash
docker-compose up
```

This will start:
- PostgreSQL on `http://localhost:5432`
- Backend on `http://localhost:3001`
- Frontend on `http://localhost:5173`

### Accessing the Application

Open your browser and navigate to `http://localhost:5173`

## API Endpoints 🔌

### Health Check
```
GET /api/health
```

### Online Users
```
GET /api/users/online
```

## WebSocket Events 🔗

### Client → Server
- `user_login` - Send when user logs in with userId

### Server → Client
- `users_online` - Broadcast list of active users

## Database Schema 🗄️

### Users Table
```sql
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  username VARCHAR(255) UNIQUE NOT NULL,
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  last_login TIMESTAMP,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Sessions Table
```sql
CREATE TABLE sessions (
  id SERIAL PRIMARY KEY,
  user_id INTEGER REFERENCES users(id),
  socket_id VARCHAR(255),
  last_seen TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Future Features 🔮

- [ ] Document upload and management
- [ ] User roles and permissions
- [ ] Quiz/Test system
- [ ] Email notifications
- [ ] Advanced search
- [ ] User profiles
- [ ] Activity logging
- [ ] Analytics dashboard

## Testing 🧪

### Backend Tests
```bash
cd backend
npm test
```

### Frontend Tests
```bash
cd frontend
npm test
```

## Contributing 🤝

1. Create a feature branch: `git checkout -b feature/your-feature`
2. Commit changes: `git commit -am 'Add your feature'`
3. Push to branch: `git push origin feature/your-feature`
4. Submit a Pull Request

## License 📄

This project is licensed under the MIT License - see the LICENSE file for details.

## Support 💬

For questions or issues, please create an issue on GitHub.

---

**Made with ❤️ for service portal needs**