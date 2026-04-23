# Multi-Exchange Strategy Automation System

**Enterprise-Grade Cryptocurrency Automated Trading System**

## 🎯 Project Overview

This is an enterprise-grade multi-exchange cryptocurrency automated trading system with **advanced arbitrage system at its core**, providing high-performance, highly reliable segmented arbitrage, grid trading, volume maker trading, and market monitoring capabilities.

### 🔥 Core Highlights: Advanced Arbitrage System

The **arbitrage engine** of this system is its most core and advanced functional module with the following unique advantages:

#### 🚀 Dual-Mode Architecture
- **Grid Arbitrage Mode (Segmented System)**: Uses segmented grid strategy to open positions gradually when spreads widen and close gradually when they converge, reducing market impact and slippage losses. Supports scalping variants with trigger grids.
- **Historical Data-Based Decision Mode**: Continuously records price spreads and funding rate data from various exchange pairs through a historical data recorder. Calculates "natural spreads" (historical median) via historical data calculator, enabling precise decision-making based on historical norms.

#### 💡 Unified Decision Engine
- **Volume-Driven Algorithm**: `target - actual = delta`, precisely controls positions
- **Multi-Trading Pair Independent Configuration**: Each trading pair has independent risk control and decision-making
- **Multi-Leg Arbitrage Support**: Supports complex multi-leg hedging strategies
- **Multi-Exchange Arbitrage**: Cross-exchange spread capture, maximizing returns

#### ⚡ Lighter Deep Optimization
- **WebSocket Batch Order Placement**: `place_market_orders_ws_batch`, ultra-fast execution
- **Smart Order Replenishment Strategy**: Single-leg fill detection + 3 retries (REST market → REST market → Aggressive limit IOC)
- **Order Push Deduplication**: Precision state tracking based on deque+set sync cache
- **Dynamic Slippage Protection**: Supports 1x~100x dynamic slippage, adapting to extreme market conditions

#### 🛡️ Multi-Layer Risk Control System
- **Price Stability Detection**: Filters false breakouts, avoids chasing rallies or selling dips
- **Counterparty Liquidity Validation**: Ensures orders can be fully filled
- **Reduce-Only Smart Management**: Auto-detection recovery, prevents liquidation failures
- **Error Avoidance Controller**: Auto pause/resume on exchange anomalies

### Core Features

- **🏆 Advanced Arbitrage System**: Segmented arbitrage, multi-leg arbitrage, cross-exchange arbitrage, unified decision engine, smart order replenishment
- **📊 Grid Trading System**: Standard/Martin/Moving grids, scalping, capital protection, take-profit and stop-loss
- **💹 Volume Maker System**: Limit order mode (Backpack), market order mode (Lighter)
- **🔔 Price Alert System**: Multi-exchange price breakout monitoring, sound alerts
- **🔗 Multi-Exchange Compatibility**: Complete adaptation for 9 major exchanges (Hyperliquid, Backpack, Lighter, Paradex, Binance, OKX, EdgeX, GRVT, Variational)
- **🛡️ Smart Risk Control**: Multi-layer risk control system, liquidity validation, error avoidance, reduce-only management
- **🎨 Real-Time Monitoring UI**: Modern terminal interface implemented with Rich library
- **🏗️ Enterprise Architecture**: Layered design, dependency injection, interface separation, high scalability
