# Redis PubSub Manager with Singleton Pattern

## Project Overview
A TypeScript implementation of a Redis PubSub manager using Singleton pattern to efficiently handle real-time stock price subscriptions.

## Key Features
- Singleton pattern ensures single Redis connection
- Dynamic channel subscription management
- Automatic cleanup of inactive subscriptions
- Scalable architecture for multiple stocks/users

## Project Structure
```
WEEK21.2_SINGLETON_PUBSUB2/
├── src/
│   ├── PubSubManager.ts  # Core singleton implementation
│   ├── index.ts          # Demo subscription logic
├── dist/                 # Compiled JS files
├── node_modules/
├── package.json
├── tsconfig.json
└── README.md
```

## Core Components

### PubSubManager.ts
```typescript
class PubSubManager {
    private static instance: PubSubManager;
    private redisClient: RedisClientType;
    private subscriptions: Map<string, string[]>;
    
    // Singleton implementation
    public static getInstance(): PubSubManager {
        if (!PubSubManager.instance) {
            PubSubManager.instance = new PubSubManager();
        }
        return PubSubManager.instance;
    }
    
    // Subscription management
    public userSubscribe(userId: string, stock: string) {
        // Manages Redis subscriptions
    }
}
```

## How It Works
1. Users subscribe to stock channels
2. Manager maintains subscription list
3. Redis broadcasts messages to all subscribers
4. Automatic cleanup of inactive users

## Setup & Run
1. Install dependencies:
```bash
npm install
```
2. Start Redis server
3. Run the application:
```bash
tsc && node dist/index.js
```

## Testing
1. In separate terminal:
```bash
redis-cli
PUBLISH APPL "Test message"
```

## Implementation Notes
- Uses Redis for pub/sub functionality
- Singleton ensures single connection pool
- TypeScript provides type safety
- Efficient memory management with subscription cleanup
