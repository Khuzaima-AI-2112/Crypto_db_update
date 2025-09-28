# Crypto Portfolio Data Pipeline Workflow

A comprehensive n8n automation workflow designed for crypto portfolio management platforms, featuring secure data handling, API integrations, and real-time analytics.

## Features

- **Secure Data Processing**: Handles sensitive crypto portfolio data with proper validation
- **API Integration**: Connects multiple data sources (CoinGecko, exchanges) to database
- **Real-time Analytics**: Live dashboard showing portfolio metrics and statistics
- **Duplicate Prevention**: Automatically detects and handles existing records
- **Error Handling**: Robust validation and error responses for financial data

## Workflow Structure

### 1. Data Ingestion (`/webhook` endpoint)
- Receives crypto price data from CoinGecko API
- Validates and processes market data (prices, volume, market cap)
- Stores portfolio data securely in database
- Returns confirmation or existing record if duplicate

### 2. Portfolio Sync (`/sync` endpoint)
- Syncs user portfolio data from exchange APIs
- Updates balances and transaction history
- Handles API authentication securely
- Provides real-time portfolio updates

### 3. Analytics Dashboard (`/dashboard` endpoint)
- Displays comprehensive portfolio analytics
- Shows total value, gains/losses, and asset distribution
- Clean, responsive interface for portfolio tracking
- Real-time data from secure database

## Setup Requirements

- **n8n**: Automation platform for workflow orchestration
- **Supabase/Database**: Secure database for storing portfolio data
- **CoinGecko API**: Real-time cryptocurrency price data
- **Exchange APIs**: Bybit and other exchange integrations
- **Webhook Endpoints**: Multiple endpoints for different functions

## Database Schema (Supabase)

| Field | Type | Description |
|-------|------|-------------|
| id | UUID | Unique portfolio record identifier |
| user_id | UUID | User reference with RLS security |
| asset_symbol | Text | Cryptocurrency symbol (BTC, ETH, etc.) |
| amount | Decimal | Asset quantity in portfolio |
| current_price | Decimal | Latest price from CoinGecko |
| total_value | Decimal | Calculated portfolio value |
| last_updated | Timestamp | Data refresh timestamp |
| exchange_source | Text | Source exchange (Bybit, etc.) |

## API Endpoints

- `POST /webhook` - Receive and process crypto price data
- `POST /sync?user_id=<id>` - Sync portfolio from exchange APIs
- `GET /dashboard?user_id=<id>` - View portfolio analytics dashboard

## Configuration

1. Update Supabase credentials and connection settings
2. Configure CoinGecko API key for price data
3. Set up exchange API credentials (Bybit, etc.)
4. Implement Row Level Security (RLS) policies
5. Configure webhook authentication tokens
6. Test all endpoints with sample portfolio data

## Security Features

- **Row Level Security**: Users only access their own portfolio data
- **API Key Protection**: Secure storage of exchange API credentials
- **Input Validation**: All crypto data validated before database storage
- **Rate Limiting**: Prevents API abuse and ensures compliance
- **Encrypted Storage**: Sensitive data encrypted at rest

## Technologies Used

- **n8n** (Workflow Automation & API Orchestration)
- **Supabase** (PostgreSQL Database with RLS)
- **CoinGecko API** (Cryptocurrency Price Data)
- **Bybit API** (Exchange Integration)
- **JavaScript** (Custom data processing logic)
- **Webhooks** (Real-time data synchronization)
- **PostgreSQL** (Secure data storage)
