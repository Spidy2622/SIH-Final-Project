# Design Document

## Overview

This design outlines the restructuring of the SIH-Project from its current nested structure to a clean, deployment-ready architecture with separate frontend and backend directories. The restructure will maintain all existing functionality while enabling independent deployment of each component.

## Architecture

### Current Structure
```
SIH-Project/
├── project-bolt-sb1-udhsdu17/
│   ├── project/ (React frontend)
│   └── server/ (Express backend)
└── README.md
```

### Target Structure
```
SIH-Project/
├── frontend/ (React + Vite + TypeScript)
├── backend/ (Express + TypeScript + MongoDB)
├── package.json (workspace configuration)
└── README.md (updated documentation)
```

## Components and Interfaces

### Frontend Component
- **Technology Stack**: React 18, TypeScript, Vite, Tailwind CSS
- **Port**: 3000 (development), static files (production)
- **API Communication**: HTTP requests to backend API endpoints
- **Build Output**: Static files in `dist/` directory
- **Key Features**:
  - Game interface with multiple pages
  - User authentication UI
  - Leaderboard and results display
  - Profile management

### Backend Component
- **Technology Stack**: Express.js, TypeScript, MongoDB with Mongoose
- **Port**: 5000 (configurable via environment)
- **Database**: MongoDB with collections for users, scores, and game data
- **API Endpoints**:
  - `/api/auth` - Authentication routes
  - `/api/scores` - Score management
  - `/api/users` - User management
  - `/api/health` - Health check

### Workspace Configuration
- **Root package.json**: Manages both frontend and backend as workspaces
- **Scripts**: Unified commands to run, build, and deploy both applications
- **Dependencies**: Shared development tools and configurations

## Data Models

### User Model (Backend)
```typescript
interface User {
  id: string;
  username: string;
  email: string;
  password: string; // hashed
  scores: Score[];
  createdAt: Date;
}
```

### Score Model (Backend)
```typescript
interface Score {
  userId: string;
  gameType: string;
  score: number;
  completedAt: Date;
}
```

### Frontend State Models
```typescript
interface GameState {
  currentScore: number;
  timeRemaining: number;
  gameStatus: 'playing' | 'completed' | 'paused';
}

interface User {
  id: string;
  username: string;
  email: string;
}
```

## Error Handling

### Frontend Error Handling
- API request failures with user-friendly error messages
- Form validation with real-time feedback
- Network connectivity issues handling
- Graceful fallbacks for missing data

### Backend Error Handling
- Express error middleware for centralized error handling
- MongoDB connection error handling
- Authentication and authorization errors
- Input validation errors with descriptive messages
- CORS configuration for cross-origin requests

## Testing Strategy

### Frontend Testing
- Component testing with React Testing Library
- Integration testing for user flows
- Build process validation
- Cross-browser compatibility testing

### Backend Testing
- API endpoint testing with Jest/Supertest
- Database integration testing
- Authentication flow testing
- Error handling validation

### End-to-End Testing
- Full application flow testing
- Frontend-backend integration validation
- Deployment process testing

## Deployment Configuration

### Frontend Deployment
- **Build Command**: `npm run build`
- **Output Directory**: `dist/`
- **Static Hosting**: Compatible with Netlify, Vercel, GitHub Pages
- **Environment Variables**: API endpoint configuration

### Backend Deployment
- **Build Command**: `npm run build`
- **Start Command**: `npm start`
- **Platform**: Compatible with Heroku, Railway, DigitalOcean
- **Environment Variables**: MongoDB URI, JWT secrets, CORS origins

### Development Environment
- **Frontend Dev Server**: Vite dev server with hot reload
- **Backend Dev Server**: ts-node-dev with auto-restart
- **Concurrent Development**: Both servers running simultaneously
- **API Proxy**: Frontend dev server proxying API requests to backend

## Migration Strategy

### Phase 1: Directory Structure Creation
1. Create `frontend/` and `backend/` directories
2. Set up workspace package.json configuration
3. Create environment configuration files

### Phase 2: Frontend Migration
1. Move React application from nested structure to `frontend/`
2. Update import paths and configurations
3. Configure Vite for proper API communication
4. Test frontend functionality

### Phase 3: Backend Migration
1. Move Express application to `backend/`
2. Update TypeScript configurations
3. Migrate environment variables and database configurations
4. Test API endpoints

### Phase 4: Integration and Testing
1. Configure CORS for frontend-backend communication
2. Test full application flow
3. Validate build processes
4. Update documentation

## Security Considerations

- Environment variables properly configured and documented
- CORS settings configured for production domains
- Authentication tokens handled securely
- Database connection strings protected
- Input validation on all API endpoints
- Password hashing maintained in user authentication