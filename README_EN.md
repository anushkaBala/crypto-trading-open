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

## 🏗️ Core System Architecture

### System Components

```
Multi-Exchange Strategy Automation System
├── 📊 Grid Trading System
│   ├── Standard Grid                    # Fixed price range grid
│   ├── Martin Grid                      # Martingale progressive strategy
│   ├── Price Following Grid             # Dynamic price tracking
│   ├── Scalping Mode                    # Quick stop-loss strategy
│   ├── Smart Scalping                   # Multi-dip detection
│   ├── Capital Protection Mode          # Auto stop-loss protection
│   ├── Take-Profit Mode                 # Auto liquidation at target
│   └── Spot Reserve Management          # Spot currency reserve
├── 🔍 Grid Volatility Scanner
│   ├── Virtual Grid Simulation          # Simulation without actual orders
│   ├── Real-Time APR Calculation        # Accurate annualized return prediction
│   ├── Token Ranking                    # Sort by volatility and APR
│   ├── Smart Rating System              # S/A/B/C/D rating assessment
│   └── Terminal UI                      # Rich real-time monitoring
├── 💹 Volume Maker System
│   ├── Limit Order Mode                 # Limit order volume making (Backpack)
│   └── Market Order Mode                # Fast market order volume making (Lighter)
├── 🔄 Arbitrage Monitor & Execution
│   ├── Basic Mode Arbitrage             # Historical data decision + auto execution
│   ├── Segmented Arbitrage System       # Advanced segmented execution (grid mode)
│   ├── Price Monitoring                 # Real-time spread monitoring
│   ├── Funding Rate Monitoring          # Cross-exchange rate differences
│   ├── Arbitrage Opportunity Identification & Execution  # Auto execution
│   ├── Terminal UI                      # Rich real-time monitoring
│   └── Trading Pair Auto Discovery      # Multi-exchange pair matching
├── 🔔 Price Alert System
│   ├── Price Breakout Monitoring        # Alert on price target hit
│   ├── Multi-Exchange Support           # All connected exchanges
│   ├── Terminal UI                      # Real-time price display
│   └── Sound Alert                      # Sound notification on breakout
├── 🔗 Exchange Adapter Layer
│   ├── Hyperliquid Adapter              # Perpetual + Spot
│   ├── Backpack Adapter                 # Perpetual
│   ├── Lighter Adapter                  # Perpetual + Spot (WS batch, smart replenishment)
│   ├── Binance Adapter                  # Spot + Perpetual
│   ├── OKX Adapter                      # Spot + Perpetual
│   ├── EdgeX Adapter                    # Perpetual
│   ├── Paradex Adapter                  # Perpetual (Starknet)
│   ├── GRVT Adapter                     # Perpetual (Decentralized)
│   ├── Variational Adapter              # Perpetual (BBO only)
│   └── Unified Interface Standard       # Standardized API
└── 🏛️ Infrastructure Layer
    ├── Dependency Injection Container   # DI management
    ├── Event System                     # Event-driven architecture
    ├── Logging System                   # Structured logging
    ├── Configuration Management         # YAML configuration system
    └── Data Aggregator                  # Multi-exchange data aggregation
```

## 🚀 Quick Start

### System Requirements

- Python 3.8+ (Python 3.12 recommended)
- Supported OS: Linux, macOS, Windows
- Optional: tmux (for multi-process management)

### Install Dependencies

```bash
# Method 1: Main environment dependencies (arbitrage, perpetual grid, volume maker)
pip install -r requirements.txt

# Method 2: Python 3.12 environment dependencies
pip install -r requirements-py312.txt

# Method 3: Lighter Spot-specific environment (auto-install)
./setup_lighter_spot_env.sh
```

**Dependencies Note:**
- `requirements.txt` - Standard packages
- `requirements-py312.txt` - Python 3.12 compatible
- `requirements-lighter-spot.txt` - Lighter spot-specific (new SDK version)
- Detailed dependency conflict notes: [docs/dependency_conflicts.md](docs/dependency_conflicts.md)

### Configure API Keys

Configure API keys for corresponding exchanges in `config/exchanges/` directory:

```bash
config/exchanges/
├── hyperliquid_config.yaml      # Hyperliquid config
├── backpack_config.yaml         # Backpack config
├── lighter_config.yaml          # Lighter config
├── binance_config.yaml          # Binance config
├── okx_config.yaml              # OKX config
├── edgex_config.yaml            # EdgeX config
├── paradex_config.yaml          # Paradex config
└── grvt_config.yaml             # GRVT config
```

### Quick Start Each System

#### Grid Trading System (Perpetual)
```bash
# Activate main environment
source .venv-py312/bin/activate

# Start grid trading
python3 run_grid_trading.py config/grid/lighter-long-perp-btc.yaml
```

#### Grid Trading System (Lighter Spot)
```bash
# Activate Lighter spot-specific environment
source .venv-lighter-spot/bin/activate
# Or use quick script
source activate_lighter_spot.sh

# Start spot grid trading
python3 run_grid_trading.py config/grid/lighter-long-spot-eth.yaml
```

#### Volume Maker System (Backpack Limit Order Mode)
```bash
python3 run_volume_maker.py config/volume_maker/backpack_btc_volume_maker.yaml
```

#### Volume Maker System (Lighter Market Order Mode)
```bash
python3 run_lighter_volume_maker.py config/volume_maker/lighter_volume_maker.yaml
```

#### Arbitrage Monitor & Execution System
```bash
# Basic mode arbitrage (historical data decision + auto execution)
python3 run_arbitrage_monitor.py

# Arbitrage System V2 (enhanced monitoring + execution)
python3 run_arbitrage_monitor_v2.py

# Segmented arbitrage system (grid mode, recommended)
python3 main_unified.py \
  --config config/arbitrage/arbitrage_segmented.yaml \
  --monitor-config config/arbitrage/monitor_v2.yaml

# Monitoring only mode (no execution)
python3 main_unified.py \
  --monitor-config config/arbitrage/monitor_lighter_gold.yaml

# ========== Quick Reference Commands ==========

# Environment Activation
source .venv-py312/bin/activate           # Python 3.12 environment
source .venv-lighter-spot/bin/activate    # Lighter spot-specific

# Arbitrage System Startup Examples
# Lighter Gold Monitoring Config
python main_unified.py \
  --monitor-config config/arbitrage/monitor_lighter_gold.yaml

# Lighter Multi-Trading Pair BTC Monitoring
python main_unified.py \
  --config config/arbitrage/arbitrage_segmented.yaml \
  --monitor-config config/arbitrage/monitor_lighter_multi_btc.yaml

# ETH Spot Arbitrage
python main_unified.py \
  --config config/arbitrage/arbitrage_segmented.yaml \
  --monitor-config config/arbitrage/monitor_lighter_eth_spot.yaml

# Test Tools
python test/ws_rest_fill_probe.py --exchange backpack --mode limit
```

#### Price Alert System
```bash
python3 run_price_alert.py config/price_alert/binance_alert.yaml
```

#### Grid Volatility Scanner
```bash
python3 grid_volatility_scanner/run_scanner.py
```

## 📋 Core Features Details

### 1️⃣ Grid Trading System

#### Features

- **Multiple Grid Modes**: Standard grid, Martin grid, price following grid
- **Smart Strategies**: Scalping, smart scalping, capital protection, take-profit mode
- **Health Check**: Auto order validation and repair mechanism
- **Terminal UI**: Real-time monitoring interface showing positions, P&L, grid status
- **Spot Support**: Spot reserve management (auto currency balance maintenance), market type auto-adaptation
- **Multi-Exchange**: Supports Hyperliquid, Backpack, Lighter (both spot and perpetual)

#### Configuration Files Location

```
config/grid/
├── lighter-long-perp-btc.yaml              # Lighter BTC perpetual long
├── lighter-long-perp-eth.yaml              # Lighter ETH perpetual long
├── lighter-long-spot-eth.yaml              # Lighter ETH spot long (needs new env)
├── lighter-long-spot-template.yaml         # Lighter spot template
├── hyperliquid_btc_perp_long.yaml          # Hyperliquid BTC long
├── hyperliquid_btc_perp_short.yaml         # Hyperliquid BTC short
├── hyperliquid_btc_spot_long.yaml          # Hyperliquid spot long
├── backpack_capital_protection_long_btc.yaml   # Backpack BTC capital protection
├── backpack_capital_protection_long_eth.yaml   # Backpack ETH capital protection
├── backpack_capital_protection_long_sol.yaml   # Backpack SOL capital protection
├── backpack_capital_protection_long_bnb.yaml   # Backpack BNB capital protection
└── backpack_capital_protection_long_hype.yaml  # Backpack HYPE capital protection
```

#### Startup Methods

```bash
# Method 1: Perpetual grid (main environment)
source .venv-py312/bin/activate
python3 run_grid_trading.py config/grid/lighter-long-perp-btc.yaml
python3 run_grid_trading.py config/grid/lighter-long-perp-eth.yaml

# Method 2: Spot grid (Lighter-specific environment)
source activate_lighter_spot.sh
python3 run_grid_trading.py config/grid/lighter-long-spot-eth.yaml

# Method 3: DEBUG mode startup (detailed logging)
python3 run_grid_trading.py config/grid/lighter-long-perp-btc.yaml --debug

# Method 4: Batch startup using shell script (tmux)
./scripts/start_all_grids.sh
```

#### Core Files

| File Path | Description |
|-----------|-------------|
| `run_grid_trading.py` | Grid trading main startup script |
| `core/services/grid/coordinator/grid_coordinator.py` | Grid system coordinator (core logic) |
| `core/services/grid/implementations/grid_engine_impl.py` | Grid execution engine |
| `core/services/grid/implementations/grid_strategy_impl.py` | Grid strategy implementation |
| `core/services/grid/implementations/position_tracker_impl.py` | Position tracker |
| `core/services/grid/implementations/order_health_checker.py` | Order health checker |
| `core/services/grid/scalping/scalping_manager.py` | Scalping manager |
| `core/services/grid/scalping/smart_scalping_tracker.py` | Smart scalping tracker |
| `core/services/grid/capital_protection/capital_protection_manager.py` | Capital protection manager |
| `core/services/grid/terminal_ui.py` | Terminal UI interface |

### 2️⃣ Volume Maker System

#### Features

- **Dual Trading Modes**: Limit order mode (Backpack), market order mode (Lighter)
- **Signal Sources**: Backpack REST API, Hyperliquid WebSocket
- **Smart Detection**: Buy/sell order quantity comparison, price change monitoring
- **Real-Time Statistics**: Trading volume, trade amount, fee statistics
- **Terminal UI**: Real-time display of trading status and statistics

#### Configuration Files Location

```
config/volume_maker/
├── backpack_btc_volume_maker.yaml   # Backpack limit order mode
└── lighter_volume_maker.yaml        # Lighter market order mode (multiple signals)
```

#### Startup Methods

```bash
# Backpack limit order mode volume making
python3 run_volume_maker.py config/volume_maker/backpack_btc_volume_maker.yaml
# Or use quick startup script
./scripts/start_volume_maker.sh

# Lighter market order mode (supports Backpack/Hyperliquid signals)
python3 run_lighter_volume_maker.py config/volume_maker/lighter_volume_maker.yaml
# Or use quick startup script
./scripts/start_lighter_volume_maker.sh
```

#### Core Files

| File Path | Description |
|-----------|-------------|
| `run_volume_maker.py` | Limit order mode startup script (Backpack) |
| `run_lighter_volume_maker.py` | Market order mode startup script (Lighter) |
| `core/services/volume_maker/implementations/volume_maker_service_impl.py` | Limit order mode implementation |
| `core/services/volume_maker/implementations/lighter_market_volume_maker_service.py` | Market order mode implementation |
| `core/services/volume_maker/terminal_ui.py` | Volume maker system terminal UI |
| `core/services/volume_maker/hourly_statistics.py` | Hourly statistics module |

### 3️⃣ Arbitrage Monitor & Execution System

#### Features

- **Dual Mode Support**: Basic mode and segmented mode
- **Basic Mode**: Historical data-based decision engine + auto arbitrage execution
- **Segmented Mode**: Advanced segmented grid execution strategy, reducing slippage and market impact
  - Supports SEG-GRID (segmented grid), SEG-SCALP (segmented scalp), SEG-GRID+ (segmented split) modes
  - Unified decision engine: Volume-driven algorithm (target - actual = delta)
  - Supports multi-trading pair independent configuration, multi-leg arbitrage, multi-exchange arbitrage
- **Price Monitoring**: Real-time multi-exchange spread monitoring (EdgeX, Lighter, Paradex, GRVT)
- **Funding Rate Monitoring**: Cross-exchange funding rate difference tracking
- **Arbitrage Opportunity Identification**: Spread and funding rate arbitrage
- **Lighter Batch Execution Optimization**:
  - WebSocket batch market order placement (`place_market_orders_ws_batch`)
  - Single-leg fill detection & smart replenishment (3 retries: REST market → REST market → aggressive limit IOC)
  - Order push deduplication (based on deque+set sync cache)
  - Dynamic slippage protection (supports multiple slippage, up to 100x)
- **Risk Control System**:
  - Price stability detection, counterparty liquidity validation
  - Reduce-only status management & probe recovery
  - Error avoidance controller (auto pause/resume anomalies)
- **Terminal UI**: Modern real-time monitoring interface using Rich library
- **Trading Pair Auto Discovery**: Auto-match supported pairs across exchanges
- **Funding Rate Duration Tracking**: Track high funding rate duration
- **Dynamic Price Precision**: Auto-adjust display precision based on price size
- **Smart Sorting**: Sort by spread, timed refresh to avoid UI jitter

#### Configuration Files Location

```
config/arbitrage/
├── monitor.yaml                          # Basic monitoring config
├── monitor_v2.yaml                       # V2 monitoring config
├── monitor_lighter_gold.yaml             # Lighter gold monitoring
├── monitor_lighter_multi_btc.yaml        # Lighter multi-pair monitoring
├── arbitrage_segmented.yaml              # Segmented arbitrage config
└── (other monitoring configs)
```

#### Startup Methods

```bash
# Method 1: Basic arbitrage monitoring
python3 run_arbitrage_monitor.py

# Method 2: Arbitrage monitoring V2
python3 run_arbitrage_monitor_v2.py

# Method 3: Unified arbitrage system (segmented mode)
python3 main_unified.py \
  --config config/arbitrage/arbitrage_segmented.yaml \
  --monitor-config config/arbitrage/monitor_v2.yaml

# Method 4: Individual monitoring config
python3 main_unified.py \
  --monitor-config config/arbitrage/monitor_lighter_gold.yaml

# Method 5: Use quick startup script
./scripts/start_arbitrage_monitor.sh
```

#### Core Files

| File Path | Description |
|-----------|-------------|
| `run_arbitrage_monitor.py` | Basic arbitrage startup (monitor+execute) |
| `run_arbitrage_monitor_v2.py` | Arbitrage V2 startup (enhanced) |
| `main_unified.py` | Unified segmented arbitrage startup (grid mode) |
| `core/services/arbitrage_monitor_v2/core/unified_orchestrator.py` | Unified orchestrator (monitor+decide+execute) |
| `core/services/arbitrage_monitor_v2/execution/arbitrage_executor.py` | Arbitrage executor (core) |
| `core/services/arbitrage_monitor_v2/execution/lighter_batch_executor.py` | Lighter batch execution (WS batch+replenishment) |
| `core/services/arbitrage_monitor_v2/decision/unified_decision_engine.py` | Unified decision engine (volume-driven) |
| `core/services/arbitrage_monitor_v2/decision/arbitrage_decision.py` | Basic mode decision engine (historical analysis) |
| `core/services/arbitrage_monitor_v2/history/history_calculator.py` | Historical data calculator (natural spread/rate diff) |
| `core/services/arbitrage_monitor_v2/utils/risk_control_utils.py` | Risk control tools (liquidity, stability) |
| `core/services/arbitrage_monitor/implementations/arbitrage_monitor_impl.py` | Basic mode monitor & execution |
| `core/services/arbitrage_monitor/interfaces/arbitrage_monitor_service.py` | Arbitrage service interface |
| `core/services/arbitrage_monitor/models/arbitrage_models.py` | Arbitrage data models |
| `core/services/arbitrage_monitor/utils/symbol_converter.py` | Trading pair converter |

### 4️⃣ Price Alert System

#### Features

- **Price Breakout Monitoring**: Monitor prices hitting upper/lower limits
- **Multi-Exchange Support**: All connected exchanges
- **Terminal UI**: Real-time current and target price display
- **Sound Alert**: Sound notification on price breakout
- **Auto Exit**: Auto exit after triggering alert

#### Configuration Files Location

```
config/price_alert/
└── binance_alert.yaml         # Price alert config
```

#### Startup Methods

```bash
# Direct startup
python3 run_price_alert.py config/price_alert/binance_alert.yaml

# Use quick startup script
./scripts/start_price_alert.sh
```

#### Core Files

| File Path | Description |
|-----------|-------------|
| `run_price_alert.py` | Price alert startup script |
| `core/services/price_alert/implementations/price_alert_service_impl.py` | Alert service implementation |
| `core/services/price_alert/interfaces/price_alert_service.py` | Alert service interface |
| `core/services/price_alert/models/alert_config.py` | Alert config model |
| `core/services/price_alert/models/alert_statistics.py` | Alert statistics model |

### 5️⃣ Grid Volatility Scanner

#### Features

- **Virtual Grid Simulation**: Simulate grid trading without actual orders
- **Real-Time APR Calculation**: Accurate annualized return prediction
- **Token Ranking**: Sort by volatility and APR, display top tokens
- **Smart Rating System**: S/A/B/C/D rating (S≥500% APR)
- **Terminal UI**: Modern real-time monitoring using Rich library
- **Flexible Configuration**: Support custom grid width, spacing, scan duration
- **Multi-Exchange Support**: Supports Lighter, Hyperliquid, etc.

#### Configuration Files Location

```
grid_volatility_scanner/config/
└── market_config.yaml         # Market config (grid parameters)
```

#### Startup Methods

```bash
# Basic startup (1 hour scan)
python3 grid_volatility_scanner/run_scanner.py

# Custom scan duration (30 minutes)
python3 grid_volatility_scanner/run_scanner.py --duration 1800

# Specify exchange (Hyperliquid)
python3 grid_volatility_scanner/run_scanner.py --exchange hyperliquid

# Use custom config file
python3 grid_volatility_scanner/run_scanner.py --config my_config.yaml
```

#### Core Files

| File Path | Description |
|-----------|-------------|
| `grid_volatility_scanner/run_scanner.py` | Scanner startup script |
| `grid_volatility_scanner/scanner.py` | Main scanner logic |
| `grid_volatility_scanner/models/virtual_grid.py` | Virtual grid model |
| `grid_volatility_scanner/models/simulation_result.py` | Simulation result model |
| `grid_volatility_scanner/core/price_monitor.py` | Price monitor |
| `grid_volatility_scanner/core/cycle_detector.py` | Cycle detector |
| `grid_volatility_scanner/core/apr_calculator.py` | APR calculator |
| `grid_volatility_scanner/ui/scanner_ui.py` | Rich terminal UI |

#### APR Calculation Formula

```
APR = (grid spacing% - fee%) × grid spacing% / grid width% × cycles per hour × 8760
```

#### Rating System

| Rating | APR Range | Description |
|--------|-----------|-------------|
| 🔥 S | ≥ 500% | Highly Recommended |
| ⭐ A | ≥ 300% | Strongly Recommended |
| ✅ B | ≥ 150% | Recommended |
| 🟡 C | ≥ 50%  | Consider |
| ❌ D | < 50%  | Not Recommended |

## 🔗 Supported Exchanges

### Fully Adapted Exchanges

| Exchange | Spot | Perpetual | REST API | WebSocket | Status |
|----------|------|-----------|----------|-----------|--------|
| **Hyperliquid** | ✅ | ✅ | ✅ | ✅ | ✅ Fully Adapted |
| **Backpack** | ❌ | ✅ | ✅ | ✅ | ✅ Fully Adapted |
| **Lighter** | ✅ | ✅ | ✅ | ✅ | ✅ Fully Adapted (spot needs new SDK) |
| **Binance** | ✅ | ✅ | ✅ | ✅ | ✅ Fully Adapted |
| **OKX** | ✅ | ✅ | ✅ | ✅ | ✅ Fully Adapted |
| **EdgeX** | ❌ | ✅ | ✅ | ✅ | ✅ Fully Adapted |
| **Paradex** | ❌ | ✅ | ✅ | ✅ | ✅ Fully Adapted (Starknet) |
| **GRVT** | ❌ | ✅ | ✅ | ✅ | ✅ Fully Adapted (Decentralized) |
| **Variational** | ❌ | ⚠️ | ✅ | ❌ | 🟡 BBO only |

**Note:** 
- Lighter spot trading requires independent virtual environment and new SDK, see [Lighter Spot Setup Guide](LIGHTER_SPOT_SETUP.md)
- Variational currently only supports BBO (best bid-ask) data, limited trading functionality

### Exchange Adapter Files

```
core/adapters/exchanges/adapters/
├── hyperliquid.py           # Hyperliquid unified interface
├── hyperliquid_base.py      # Base class
├── hyperliquid_rest.py      # REST API
├── hyperliquid_websocket.py # WebSocket
├── backpack.py              # Backpack unified interface
├── backpack_base.py         # Base class
├── backpack_rest.py         # REST API
├── backpack_websocket.py    # WebSocket
├── lighter.py               # Lighter unified interface
├── lighter_base.py          # Base class
├── lighter_rest.py          # REST API (WS batch, slippage protection)
├── lighter_websocket.py     # WebSocket (dedup, unified logging)
├── binance.py               # Binance unified interface
├── okx.py                   # OKX unified interface
├── edgex.py                 # EdgeX unified interface
├── paradex.py               # Paradex interface (Starknet)
├── grvt.py                  # GRVT interface (Decentralized)
└── variational.py           # Variational interface (BBO only)
```

## 📁 Complete Project Structure

```
crypto-trading/
├── 🚀 Startup Scripts
│   ├── run_grid_trading.py                # Grid trading startup
│   ├── run_volume_maker.py                # Limit order volume maker (Backpack)
│   ├── run_lighter_volume_maker.py        # Market order volume maker (Lighter)
│   ├── run_arbitrage_monitor.py           # Basic arbitrage (monitor+execute)
│   ├── run_arbitrage_monitor_v2.py        # Arbitrage V2 (enhanced)
│   ├── run_arbitrage_monitor_simple.py    # Simplified arbitrage startup
│   ├── run_arbitrage_execution_v3.py      # Arbitrage V3 (deprecated)
│   ├── main_unified.py                    # Unified segmented arbitrage (grid mode)
│   ├── run_price_alert.py                 # Price alert startup
│   └── grid_volatility_scanner/
│       └── run_scanner.py                 # Grid volatility scanner startup
├── 🏛️ core/ - Core Business Layer
│   ├── data_aggregator.py                 # Data aggregator
│   ├── __init__.py
│   ├── adapters/ - Exchange Adapter Layer
│   │   └── exchanges/
│   │       ├── adapter.py                 # Base adapter
│   │       ├── factory.py                 # Adapter factory
│   │       ├── interface.py               # Unified interface
│   │       ├── manager.py                 # Adapter manager
│   │       ├── models.py                  # Data models
│   │       ├── subscription_manager.py    # Subscription manager
│   │       ├── websocket_manager.py       # WebSocket manager
│   │       ├── adapters/                  # Exchange adapter implementations
│   │       │   ├── hyperliquid*.py        # Hyperliquid adapter
│   │       │   ├── backpack*.py           # Backpack adapter
│   │       │   ├── lighter*.py            # Lighter adapter (WS batch, replenishment)
│   │       │   ├── binance*.py            # Binance adapter
│   │       │   ├── okx*.py                # OKX adapter
│   │       │   ├── edgex*.py              # EdgeX adapter
│   │       │   ├── paradex*.py            # Paradex adapter (Starknet)
│   │       │   ├── grvt*.py               # GRVT adapter (Decentralized)
│   │       │   └── variational*.py        # Variational adapter (BBO only)
│   │       └── utils/                     # Utilities
│   │           ├── log_formatter.py       # Log formatting
│   │           └── setup_logging.py       # Log setup
│   ├── services/ - Business Service Layer
│   │   ├── grid/ - Grid Trading Service
│   │   │   ├── coordinator/               # Coordinator module
│   │   │   │   ├── grid_coordinator.py    # Grid coordinator (core)
│   │   │   │   ├── balance_monitor.py     # Balance monitor
│   │   │   │   ├── position_monitor.py    # Position monitor
│   │   │   │   ├── order_operations.py    # Order operations
│   │   │   │   ├── scalping_operations.py # Scalping operations
│   │   │   │   ├── grid_reset_manager.py  # Grid reset manager
│   │   │   │   └── verification_utils.py  # Verification tools
│   │   │   ├── implementations/           # Implementation module
│   │   │   │   ├── grid_engine_impl.py    # Execution engine
│   │   │   │   ├── grid_strategy_impl.py  # Strategy implementation
│   │   │   │   ├── position_tracker_impl.py   # Position tracking
│   │   │   │   ├── order_health_checker.py    # Health check
│   │   │   │   └── order_monitor.py       # Order monitor
│   │   │   ├── interfaces/                # Interface definitions
│   │   │   │   ├── grid_engine.py
│   │   │   │   ├── grid_strategy.py
│   │   │   │   └── position_tracker.py
│   │   │   ├── models/                    # Data models
│   │   │   │   ├── grid_config.py         # Grid config
│   │   │   │   ├── grid_state.py          # Grid state
│   │   │   │   ├── grid_order.py          # Grid order
│   │   │   │   └── grid_metrics.py        # Grid metrics
│   │   │   ├── scalping/                  # Scalping module
│   │   │   │   ├── scalping_manager.py    # Scalping manager
│   │   │   │   └── smart_scalping_tracker.py  # Smart scalping tracking
│   │   │   ├── capital_protection/        # Capital protection module
│   │   │   │   └── capital_protection_manager.py
│   │   │   ├── take_profit/               # Take-profit module
│   │   │   │   └── take_profit_manager.py
│   │   │   ├── price_lock/                # Price lock module
│   │   │   │   └── price_lock_manager.py
│   │   │   ├── reserve/                   # Spot reserve module
│   │   │   │   ├── spot_reserve_manager.py
│   │   │   │   ├── reserve_monitor.py
│   │   │   │   └── reserve_checker.py
│   │   │   └── terminal_ui.py             # Grid system terminal UI
│   │   ├── volume_maker/ - Volume Maker Service
│   │   │   ├── implementations/
│   │   │   │   ├── volume_maker_service_impl.py   # Limit order implementation
│   │   │   │   └── lighter_market_volume_maker_service.py  # Market order implementation
│   │   │   ├── interfaces/
│   │   │   │   └── volume_maker_service.py
│   │   │   ├── models/
│   │   │   │   ├── volume_maker_config.py
│   │   │   │   └── volume_maker_statistics.py
│   │   │   ├── hourly_statistics.py       # Hourly statistics
│   │   │   └── terminal_ui.py             # Volume maker terminal UI
│   │   ├── arbitrage_monitor/ - Arbitrage Monitor & Execution (Basic)
│   │   │   ├── implementations/
│   │   │   │   └── arbitrage_monitor_impl.py   # Monitor & execution
│   │   │   ├── interfaces/
│   │   │   │   └── arbitrage_monitor_service.py  # Service interface
│   │   │   ├── models/
│   │   │   │   └── arbitrage_models.py    # Data models
│   │   │   └── utils/
│   │   │       └── symbol_converter.py    # Trading pair converter
│   │   ├── arbitrage_monitor_v2/ - Arbitrage Monitor & Execution V2 (Segmented)
│   │   │   ├── models.py                  # V2 data models
│   │   │   ├── analysis/                  # Analysis module
│   │   │   │   ├── exchange_locker.py     # Exchange locker
│   │   │   │   ├── opportunity_finder.py  # Opportunity finder
│   │   │   │   └── spread_calculator.py   # Spread calculator
│   │   │   ├── config/                    # Config module
│   │   │   │   ├── arbitrage_config.py    # Arbitrage config
│   │   │   │   ├── monitor_config.py      # Monitoring config
│   │   │   │   ├── unified_config_manager.py  # Unified config manager
│   │   │   │   ├── symbol_config.py       # Trading pair config
│   │   │   │   ├── debug_config.py        # Debug config
│   │   │   │   ├── multi_exchange_config.py   # Multi-exchange config
│   │   │   │   └── multi_leg_pairs_config.py  # Multi-leg config
│   │   │   ├── core/                      # Core module
│   │   │   │   ├── unified_orchestrator.py       # Unified orchestrator (monitor+decide+execute)
│   │   │   │   ├── arbitrage_orchestrator_v3.py  # V3 orchestrator (multi-pair)
│   │   │   │   ├── orchestrator.py               # Base orchestrator
│   │   │   │   ├── orchestrator_simple.py        # Simple orchestrator (lightweight)
│   │   │   │   ├── orchestrator_bootstrap.py     # Bootstrap orchestrator
│   │   │   │   ├── orchestrator_ui_controller.py # UI controller
│   │   │   │   ├── spread_pipeline.py            # Spread data pipeline
│   │   │   │   ├── reduce_only_probe_service.py  # Reduce-only probe service
│   │   │   │   ├── health_monitor.py             # System health monitor
│   │   │   │   └── debug_state_printer.py        # Debug state printer
│   │   │   ├── data/                      # Data module
│   │   │   │   ├── data_processor.py      # Data processor
│   │   │   │   └── data_receiver.py       # Data receiver
│   │   │   ├── decision/                  # Decision module
│   │   │   │   ├── arbitrage_decision.py  # Basic mode decision engine (historical)
│   │   │   │   └── unified_decision_engine.py  # Unified decision engine (volume-driven)
│   │   │   ├── display/                   # Display module
│   │   │   │   ├── ui_manager.py          # UI manager
│   │   │   │   ├── realtime_scroller.py   # Real-time scroller
│   │   │   │   ├── simple_printer.py      # Simple printer
│   │   │   │   └── ui_components.py       # UI components
│   │   │   ├── execution/                 # Execution module
│   │   │   │   ├── arbitrage_executor.py  # Arbitrage executor (core)
│   │   │   │   ├── lighter_batch_executor.py   # Lighter batch execution (WS batch+replenishment)
│   │   │   │   ├── order_strategy_executor.py  # Order strategy execution
│   │   │   │   ├── order_monitor.py       # Order monitor
│   │   │   │   └── reduce_only_handler.py # Reduce-only handler
│   │   │   ├── guards/                    # Guard module
│   │   │   │   └── reduce_only_guard.py   # Reduce only guard
│   │   │   ├── history/                   # Historical data module
│   │   │   │   ├── history_calculator.py  # Calculator (natural spread/rate diff)
│   │   │   │   ├── spread_history_recorder.py  # Recorder (continuous sampling)
│   │   │   │   ├── spread_history_reader.py    # Reader (query interface)
│   │   │   │   └── chart_generator.py     # Chart generator
│   │   │   ├── risk_control/              # Risk control module
│   │   │   │   ├── global_risk_controller.py   # Global risk control
│   │   │   │   ├── error_backoff_controller.py # Error avoidance
│   │   │   │   └── network_state.py            # Network state
│   │   │   ├── state/                     # State module
│   │   │   │   └── symbol_state_manager.py     # Trading pair state
│   │   │   └── utils/                     # Utilities
│   │   │       ├── orchestrator_utils.py  # Orchestrator tools
│   │   │       └── risk_control_utils.py  # Risk control (liquidity, stability)
│   │   ├── price_alert/ - Price Alert Service
│   │   │   ├── implementations/
│   │   │   │   └── price_alert_service_impl.py  # Alert implementation
│   │   │   ├── interfaces/
│   │   │   │   └── price_alert_service.py # Service interface
│   │   │   └── models/
│   │   │       ├── alert_config.py        # Config model
│   │   │       └── alert_statistics.py    # Statistics model
│   │   ├── symbol_manager/ - Symbol Manager Service
│   │   │   ├── implementations/
│   │   │   │   ├── symbol_conversion_service.py
│   │   │   │   └── symbol_cache_service.py
│   │   │   ├── interfaces/
│   │   │   │   ├── symbol_conversion_service.py
│   │   │   │   └── symbol_cache.py
│   │   │   └── models/
│   │   │       ├── symbol_normalization.py
│   │   │       └── symbol_cache_models.py
│   │   ├── events/ - Event System
│   │   │   ├── event.py
│   │   │   ├── event_handler.py
│   │   │   └── __init__.py
│   │   ├── implementations/ - Generic Service Implementations
│   │   │   └── config_service.py
│   │   └── interfaces/ - Generic Service Interfaces
│   │       ├── base.py
│   │       └── config_service.py
│   ├── domain/ - Domain Model Layer
│   │   ├── __init__.py
│   │   └── (domain entities and value objects)
│   ├── infrastructure/ - Infrastructure Layer
│   │   ├── __init__.py
│   │   └── (cache, database, message queue, etc.)
│   ├── di/ - Dependency Injection Container
│   │   ├── container.py                   # DI container
│   │   ├── modules.py                     # Module registration
│   │   └── (other DI files)
│   └── logging/ - Logging System
│       ├── __init__.py
│       └── (logging config and tools)
├── 🌐 api/ - API Layer
│   ├── gateway.py                         # FastAPI gateway
│   ├── middleware/                        # Middleware
│   │   ├── logging.py
│   │   └── __init__.py
│   ├── websocket/                         # WebSocket service
│   │   └── __init__.py
│   └── graphql/                           # GraphQL service
│       └── __init__.py
├── 🔧 config/ - Configuration Files
│   ├── exchanges/                         # Exchange configs
│   │   ├── hyperliquid_config.yaml
│   │   ├── backpack_config.yaml
│   │   ├── lighter_config.yaml
│   │   ├── binance_config.yaml
│   │   ├── okx_config.yaml
│   │   ├── edgex_config.yaml
│   │   ├── paradex_config.yaml
│   │   └── grvt_config.yaml
│   ├── grid/                              # Grid configs
│   │   ├── lighter_btc_perp_long.yaml
│   │   ├── lighter_btc_perp_short.yaml
│   │   ├── hyperliquid_btc_perp_long.yaml
│   │   ├── hyperliquid_btc_perp_short.yaml
│   │   ├── hyperliquid_btc_spot_long.yaml
│   │   └── backpack_capital_protection_*.yaml  (multiple)
│   ├── volume_maker/                      # Volume maker configs
│   │   ├── backpack_btc_volume_maker.yaml
│   │   └── lighter_volume_maker.yaml
│   ├── arbitrage/                         # Arbitrage configs
│   │   ├── monitor.yaml                   # Basic mode
│   │   ├── monitor_v2.yaml                # V2 mode
│   │   ├── monitor_lighter_gold.yaml      # Lighter gold monitoring
│   │   ├── monitor_lighter_multi_btc.yaml # Lighter multi-pair
│   │   ├── arbitrage_segmented.yaml       # Segmented arbitrage execution
│   │   └── (other arbitrage configs)
│   ├── price_alert/                       # Price alert configs
│   │   └── binance_alert.yaml
│   ├── symbol_conversion.yaml             # Trading pair conversion
│   └── logging.yaml                       # Logging config
├── 🛠️ tools/ - Tool Scripts
│   ├── martin_grid_calculator.py          # Martin grid calculator
│   ├── convert_account_index.py           # Account index conversion
│   ├── query_account_simple.py            # Simple account query
│   ├── query_account_with_apikey.py       # API key account query
│   ├── test_apikey_direct.py              # API key direct test
│   └── README.md                          # Tools documentation
├── 📜 scripts/ - Operations Scripts
│   ├── start_all_grids.sh                 # Batch startup grids (tmux)
│   ├── stop_all_grids.sh                  # Batch stop grids
│   ├── start_volume_maker.sh              # Startup limit order volume maker
│   ├── start_lighter_volume_maker.sh      # Startup market order volume maker
│   ├── start_arbitrage_monitor.sh         # Startup arbitrage monitoring
│   ├── start_price_alert.sh               # Startup price alert
│   ├── check_arbitrage_executor_legs.sh   # Check arbitrage logs
│   ├── check_lighter_ws_batch.sh          # Monitor Lighter WS batch
│   ├── check_ports.sh                     # Port check
│   ├── apply_log_optimization.sh          # Log optimization
│   ├── release.sh                         # Release script
│   ├── deployment/                        # Deployment scripts
│   │   ├── start_system.sh
│   │   └── stop_system.sh
│   ├── migration/                         # Migration scripts
│   │   └── (data migration scripts)
│   └── README.md                          # Scripts documentation
├── 🧪 tests/ - Test Code
│   ├── adapters/                          # Adapter tests
│   │   ├── hyperliquid/                   # Hyperliquid tests
│   │   ├── backpack/                      # Backpack tests
│   │   ├── lighter/                       # Lighter tests
│   │   ├── binance/                       # Binance tests
│   │   └── okx/                           # OKX tests
│   ├── strategies/                        # Strategy tests
│   │   ├── grid/                          # Grid strategy tests
│   │   └── volume_maker/                  # Volume maker tests
│   ├── arbitrage/                         # Arbitrage tests
│   │   └── reports/                       # Test reports
│   ├── integration/                       # Integration tests
│   ├── unit/                              # Unit tests
│   ├── performance/                       # Performance tests
│   ├── debug/                             # Debug tests
│   └── README.md                          # Test documentation
├── 🧪 test/ - Quick Test Scripts
│   ├── test_lighter_*.py                  # Lighter quick tests
│   ├── test_hyperliquid_*.py              # Hyperliquid quick tests
│   ├── verify_liquidation_price.py        # Liquidation price verify
│   ├── compare_liquidation_methods.py     # Liquidation method comparison
│   ├── test_log_optimization.py           # Log optimization test
│   └── (other quick tests)
├── 📝 examples/ - Example Code
│   ├── basic_demo.py                      # Basic demo
│   ├── exchange_adapter_demo.py           # Adapter demo
│   ├── edgex_adapter_demo.py              # EdgeX demo
│   ├── subscription_mode_demo.py          # Subscription mode demo
│   └── (other example scripts)
├── 🔍 grid_volatility_scanner/ - Grid Volatility Scanner
│   ├── __init__.py                        # Module init
│   ├── scanner.py                         # Main scanner logic
│   ├── run_scanner.py                     # Startup script
│   ├── README.md                          # Scanner documentation
│   ├── config/
│   │   └── market_config.yaml             # Market config
│   ├── models/
│   │   ├── virtual_grid.py                # Virtual grid model
│   │   └── simulation_result.py           # Simulation result model
│   ├── core/
│   │   ├── price_monitor.py               # Price monitor
│   │   ├── cycle_detector.py              # Cycle detector
│   │   └── apr_calculator.py              # APR calculator
│   └── ui/
│       └── scanner_ui.py                  # Rich terminal UI
├── 📚 docs/ - Documentation
│   ├── README.md                          # Documentation index
│   ├── INDEX.md                           # Documentation index
│   ├── lighter_sdk_upgrade_guide.md       # Lighter SDK upgrade guide
│   ├── dependency_conflicts.md            # Dependency conflicts explanation
│   ├── grid-trading/                      # Grid trading docs
│   │   └── (70+ detailed docs)
│   ├── grid_volatility_scanner/           # Grid volatility scanner docs
│   │   └── (7 detailed docs)
│   ├── volume-maker/                      # Volume maker docs
│   │   └── (42 detailed docs)
│   ├── arbitrage_monitor/                 # Arbitrage monitor docs
│   │   └── (10 detailed docs)
│   ├── price-alert/                       # Price alert docs
│   │   └── (1 doc)
│   ├── lighter/                           # Lighter exchange docs
│   │   └── (47 detailed docs)
│   ├── hyperliquid/                       # Hyperliquid exchange docs
│   │   └── (23 detailed docs)
│   ├── architecture/                      # Architecture docs
│   │   └── (36 architecture docs)
│   ├── adapters/                          # Adapter docs
│   │   └── (10 adapter docs)
│   ├── features/                          # Feature docs
│   │   └── (7 feature docs)
│   ├── fixes/                             # Fix records
│   │   └── (107 fix records)
│   ├── troubleshooting/                   # Troubleshooting guides
│   │   └── (22 troubleshooting guides)
│   ├── tools/                             # Tool docs
│   │   └── (1 doc)
│   ├── websocket/                         # WebSocket docs
│   │   └── (2 WebSocket docs)
│   ├── legacy/                            # Legacy docs
│   │   └── (3 docs)
│   ├── Terminal UI Stable Display Design Guide.md  # Terminal UI guide
│   ├── Python Terminal UI Library Comparison.md    # UI library comparison
│   └── (other topic docs)
├── 🗂️ deprecated/ - Deprecated Code
│   └── old_monitoring_system/            # Old monitoring system
├── 📦 web-console/ - Web Frontend (Optional)
│   ├── src/                               # Source code
│   │   ├── components/                    # Common components
│   │   ├── pages/                         # Page components
│   │   ├── services/                      # Frontend services
│   │   └── types/                         # Type definitions
│   ├── package.json                       # Frontend dependencies
│   └── vite.config.ts                     # Build config
├── 📋 logs/ - Log Directory
│   ├── system.log                         # System log
│   ├── ExchangeAdapter.log                # Adapter log
│   ├── core.services.grid.*.log           # Grid system logs
│   └── (other log files)
├── 🐳 docker/ - Docker Config
│   └── README.md
├── 📄 requirements.txt                    # Python dependencies (main)
├── 📄 requirements-py312.txt              # Python 3.12 dependencies
├── 📄 requirements-lighter-spot.txt       # Lighter spot-specific
├── 📜 setup_lighter_spot_env.sh           # Lighter spot auto-setup
├── 📜 activate_lighter_spot.sh            # Lighter spot quick activation
├── 📖 README.md                           # Project documentation
├── 📖 LIGHTER_SPOT_SETUP.md               # Lighter spot quick setup
├── 📋 PROJECT_STRUCTURE.md                # Project structure
├── 📋 REST_API_USAGE.md                   # REST API usage
├── 📋 CHANGELOG.md                        # Change log
└── 📋 VERSION                             # Version number
```

## 📊 Startup Scripts Summary

### Grid Trading System

| Script | Command | Description |
|--------|---------|-------------|
| Single grid startup | `python3 run_grid_trading.py <config>` | Start single grid trading |
| DEBUG mode | `python3 run_grid_trading.py <config> --debug` | Detailed logging |
| Batch startup | `./scripts/start_all_grids.sh` | Batch startup with tmux |
| Batch stop | `./scripts/stop_all_grids.sh` | Stop all grids |

### Volume Maker System

| Script | Command | Description |
|--------|---------|-------------|
| Limit order mode | `python3 run_volume_maker.py <config>` | Backpack limit order |
| Quick startup | `./scripts/start_volume_maker.sh` | Quick startup |
| Market order mode | `python3 run_lighter_volume_maker.py <config>` | Lighter market order |
| Quick startup | `./scripts/start_lighter_volume_maker.sh` | Quick startup |

### Arbitrage & Monitoring System

| Script | Command | Description |
|--------|---------|-------------|
| Basic arbitrage | `python3 run_arbitrage_monitor.py` | Basic mode (historical+execute) |
| Arbitrage V2 | `python3 run_arbitrage_monitor_v2.py` | V2 (enhanced) |
| Segmented arbitrage | `python3 main_unified.py --config <config> --monitor-config <monitor>` | Grid mode |
| Quick startup | `./scripts/start_arbitrage_monitor.sh` | Quick startup |
| Price alert | `python3 run_price_alert.py <config>` | Start price alert |
| Quick startup | `./scripts/start_price_alert.sh` | Quick startup |

### Analysis Tools

| Script | Command | Description |
|--------|---------|-------------|
| Grid volatility scanner | `python3 grid_volatility_scanner/run_scanner.py` | Scan & recommend |
| Custom duration | `python3 grid_volatility_scanner/run_scanner.py --duration <seconds>` | Custom duration |
| Specify exchange | `python3 grid_volatility_scanner/run_scanner.py --exchange <exchange>` | Specify exchange |

## 🛠️ Tool Scripts

### Martin Grid Calculator

```bash
# Calculate required capital and risk distribution for Martin grid
python3 tools/martin_grid_calculator.py
```

### Account Query Tools

```bash
# Simple account query
python3 tools/query_account_simple.py

# Account query with API Key
python3 tools/query_account_with_apikey.py
```

### Account Index Conversion Tool

```bash
python3 tools/convert_account_index.py
```

## 🤝 Contributing

Contributions are welcome! Please open an issue or submit a pull request.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Thanks to all contributors and community members
- Inspiration from advanced trading systems
- Special thanks to the exchange APIs for data access

---

**Made with ❤️ by the Crypto Trading Team**
