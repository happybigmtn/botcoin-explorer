# 🤖 Botcoin Explorer

Real-time block explorer for Botcoin, powered by Convex.

## Features

- **Real-time updates** - Blocks appear instantly via Convex subscriptions
- **Block explorer** - View blocks, transactions, addresses
- **Mining stats** - Top miners, hashrate, difficulty
- **Search** - Find blocks, transactions, addresses

## Architecture

```
botcoind (RPC) → Indexer Service → Convex (ns-db-1)
                                      ↓
                              Next.js Frontend
                          (real-time subscriptions)
```

## Setup

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure Convex

```bash
npx convex dev
```

Set your deployment URL in `.env.local`:
```
NEXT_PUBLIC_CONVEX_URL=https://your-deployment.convex.cloud
CONVEX_URL=https://your-deployment.convex.cloud
```

### 3. Configure Botcoin RPC

Set the RPC connection in `.env.local`:
```
BOTCOIN_RPC_URL=http://95.111.227.14:8332
BOTCOIN_RPC_USER=botcoin
BOTCOIN_RPC_PASS=your-rpc-password
```

### 4. Run Indexer

```bash
npm run indexer
```

This syncs blocks from botcoind to Convex in real-time.

### 5. Run Frontend

```bash
npm run dev
```

Visit http://localhost:3000

## Deployment

### Indexer
Run on a server with access to botcoind RPC:
```bash
CONVEX_URL=... BOTCOIN_RPC_URL=... npm run indexer
```

### Frontend
Deploy to Vercel:
```bash
npx vercel
```

## API Endpoints (Convex)

- `getLatestBlocks({ limit })` - Latest N blocks
- `getBlockByHeight({ height })` - Block by height
- `getBlockByHash({ hash })` - Block by hash
- `getTransaction({ txid })` - Transaction details
- `getAddress({ address })` - Address info
- `getNetworkStats()` - Network statistics
- `getTopMiners({ limit })` - Top miners by blocks

## License

MIT
