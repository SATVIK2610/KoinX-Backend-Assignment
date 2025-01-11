# CryptoStat API

A Node.js backend service that tracks cryptocurrency prices and provides statistical analysis through RESTful APIs. The service automatically fetches price data for Bitcoin, Ethereum, and Polygon (MATIC) every 2 hours.

---

## Features

- Real-time cryptocurrency price tracking
- Price statistics and market cap data
- Standard deviation calculations for price volatility
- Automated data collection with configurable intervals
- Health check endpoint for monitoring
- Error handling and rate limiting
- MongoDB integration for data persistence

---

## Tech Stack

- **Node.js** & **Express**
- **MongoDB** & **Mongoose**
- **Node-cron** for scheduled tasks
- **Axios** for API requests
- **dotenv** for environment variables

---

## API Endpoints

### 1. Get Current Stats
```http
GET /api/stats?coin=<coinname>
```
Returns the latest price data for the specified coin:

```json
{
  "price": 52000.45,
  "marketCap": 1000000000,
  "change24h": 2.5,
  "timestamp": "2024-03-10T12:00:00Z"
}
```

### 2. Get Price Deviation
```http
GET /api/deviation?coin=<coinname>
```
Returns the standard deviation of prices:

```json
{
  "deviation": "1234.56"
}
```

### 3. Health Check
```http
GET /api/health
```
Returns the server status:

```json
{
  "status": "ok",
  "timestamp": "2024-03-10T12:00:00Z",
  "dbStatus": "connected"
}
```

---

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file in the root directory:
   ```env
   MONGODB_URI=your_mongodb_connection_string
   ```

4. Start the server:
   ```bash
   npm run dev
   ```

---

## Data Collection

The service collects data for:
- **Bitcoin (BTC)**
- **Ethereum (ETH)**
- **Polygon (MATIC)**

**Collection schedule:**
- Initial fetch on server startup
- Every 2 hours thereafter

---

## Error Handling

- **400**: Bad Request - Missing parameters
- **404**: Not Found - No data available
- **429**: Too Many Requests - API rate limit hit
- **500**: Server Error

---

## Rate Limiting

The service includes automatic retry logic for CoinGecko API rate limits:
- 60-second cooldown period
- Automatic retry after cooldown
- Error logging

---

## Development

The project structure follows a modular pattern:

- **/src/controllers** - Request handlers
- **/src/routes** - API route definitions
- **/src/services** - External API integration
- **/src/models** - Database schemas
- **/src/utils** - Helper functions
- **/src/jobs** - Scheduled tasks
- **/src/config** - Configuration files

---

## Contributing

1. Fork the repository
2. Create a feature branch:
   ```bash
   git checkout -b feature/name
   ```
3. Commit changes:
   ```bash
   git commit -am 'Add feature'
   ```
4. Push to branch:
   ```bash
   git push origin feature/name
   ```
5. Create a Pull Request

---

## License

MIT License - feel free to use this project for your own purposes.
