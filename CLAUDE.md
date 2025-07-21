# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

TradePilot is a copy trading platform that enables traders to broadcast their trades and allows copiers to automatically replicate these trades on connected exchange accounts. The platform supports Bitget and Bybit exchanges.

## Technology Stack

### Frontend
- **Framework**: Next.js 14 (App Directory)
- **Language**: TypeScript 5.x
- **Styling**: Tailwind CSS 3.x + shadcn/ui
- **State Management**: Zustand
- **Data Fetching**: TanStack Query
- **Real-time**: Socket.io Client

### Backend
- **Framework**: FastAPI 0.104+
- **Language**: Python 3.11+
- **Database**: Supabase (PostgreSQL 15)
- **Cache**: Redis 7.x
- **Task Queue**: Celery with Redis
- **WebSockets**: python-socketio

## Common Development Commands

### Frontend (Next.js)
```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Build for production
npm run build

# Run production build
npm start

# Run linting
npm run lint

# Run type checking
npm run type-check

# Run tests
npm test

# Run single test file
npm test -- path/to/test.spec.ts
```

### Backend (FastAPI)
```bash
# Install dependencies
pip install -r requirements.txt

# Run development server
uvicorn app.main:app --reload

# Run tests
pytest

# Run single test file
pytest tests/test_file.py

# Run linting
ruff check .

# Format code
ruff format .

# Run type checking
mypy app/
```

### Docker Commands
```bash
# Build and run all services
docker-compose up --build

# Run specific service
docker-compose up frontend
docker-compose up backend

# Run tests in container
docker-compose run backend pytest
```

## Architecture Overview

The platform follows a microservices architecture with the following key services:

1. **Trading Service**: Handles trade execution, broadcasting, and replication
2. **User Management Service**: Authentication, authorization, and user profiles
3. **Position Monitoring Service**: Real-time position tracking and risk management
4. **Analytics Service**: Performance metrics and reporting
5. **Notification Service**: Telegram/Discord alerts
6. **Admin Service**: Platform management and monitoring

### Key Architectural Patterns

- **Event-Driven Architecture**: WebSocket for real-time trade broadcasting
- **Repository Pattern**: For database operations
- **Service Layer**: Business logic separated from API routes
- **DTO Pattern**: Data transfer objects for API contracts
- **Dependency Injection**: Using FastAPI's dependency system

### Database Schema

The main entities include:
- `users`: Platform users with role-based access
- `traders`: Trading profiles with performance metrics
- `copiers`: Copy trading configurations
- `strategies`: Trading strategies and configurations
- `trades`: Trade history and execution logs
- `positions`: Active trading positions
- `notifications`: Alert preferences and history

### Real-time Trade Flow

1. Trader executes trade on exchange
2. WebSocket connection broadcasts trade to Trading Service
3. Trading Service validates and stores trade
4. Position Monitoring Service updates positions
5. Trade is replicated to all active copiers
6. Notifications sent to configured channels

## Design System

- **Dark Mode First**: Web3 native aesthetics
- **Color Palette**: 
  - Success/Profits: Green (#10B981)
  - Danger/Losses: Red (#EF4444)
  - Primary/CTAs: Blue (#3B82F6)
  - Premium: Purple (#8B5CF6)
- **Typography**: Inter (primary), JetBrains Mono (numbers/data)
- **Component Library**: shadcn/ui with custom theming

## Security Considerations

- All API keys are encrypted with AES-256 before storage
- JWT authentication with refresh token rotation
- Rate limiting on all API endpoints
- WebSocket connections require authentication
- Never log or expose sensitive user data

## Performance Requirements

- Trade execution latency: <1 second
- WebSocket message delivery: <100ms
- API response time: <200ms (p95)
- Support 10,000+ concurrent WebSocket connections
- Database query optimization for high-frequency operations

## Testing Strategy

- Unit tests for all business logic
- Integration tests for API endpoints
- WebSocket connection tests
- Load testing for performance requirements
- End-to-end tests for critical user flows

## Development Workflow

1. Work on feature branches off `dev`
2. Follow conventional commit messages
3. Ensure all tests pass before pushing
4. Create PR to `dev` for review
5. After testing on staging, merge `dev` to `main`

## Key Implementation Notes

- Use Redis for caching trader performance metrics
- Implement circuit breakers for exchange API calls
- Use Celery for async tasks (notifications, analytics)
- Store trade history in time-series optimized tables
- Implement proper error handling for exchange API failures
- Use database transactions for critical operations
- Monitor WebSocket connection health
- Implement reconnection logic for dropped connections