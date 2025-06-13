# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a TradingView Pine Script repository containing Fibonacci retracement trading strategies for financial markets. The primary strategy is located in `Zic Fibonacci Retracement Strategy/Zic Fibonacci Retracement Strategy.pine`.

## Code Architecture

### Main Strategy File Structure
The Pine Script strategy (`Zic Fibonacci Retracement Strategy.pine`) is organized into distinct sections:

1. **Input Parameters** - Strategy configuration including Fibonacci levels, filters, and market conditions
2. **Global Variables** - State management for Fibonacci calculations and order tracking  
3. **Helper Functions** - Utilities for technical analysis and order management
4. **Market Status Detection** - Multi-timeframe trend analysis using ADX, moving averages, and Bollinger Bands
5. **Filter System** - Multiple confirmation filters (trend, RSI, volume, volatility, support/resistance, time-based)
6. **Fibonacci Logic** - Dynamic calculation of retracement levels based on recent highs/lows
7. **Trading Logic** - Entry/exit conditions with both market and limit order support
8. **Visualization** - Plotting of levels, status tables, and trade markers

### Key Components

- **Market Status Detection**: Uses higher timeframe analysis (default 4H) to determine market conditions (uptrend/downtrend/sideways)
- **Dynamic Fibonacci Levels**: Automatically recalculates retracement levels based on configurable lookback period
- **Multi-Filter System**: Combines trend, momentum, volume, volatility, and structural filters for trade validation
- **Dual Order Types**: Supports both market orders (crossover/crossunder) and limit orders with configurable offsets
- **Risk Management**: Integrated take profit and stop loss with percentage or pip-based calculations

## Development Guidelines

### Pine Script Conventions
- Use Pine Script v5 syntax (`//@version=5`)
- Organize code into logical sections with comment headers (`// ====== SECTION NAME ======`)
- Use descriptive variable names with underscores (e.g., `current_fib_high_val`)
- Group related inputs using the `group` parameter
- Maintain consistent indentation and spacing

### Strategy Parameters
- All configurable values should be exposed as inputs with appropriate ranges and step sizes
- Use boolean toggles for optional features (filters, order types, visual elements)
- Group related parameters logically for better user experience

### State Management
- Use `var` keyword for persistent variables that maintain state across bars
- Reset trigger flags when Fibonacci levels change to prevent duplicate signals
- Properly manage pending order IDs for limit order cancellation

### Performance Considerations
- Use `barstate.isconfirmed` for entry logic to avoid repainting
- Limit visual elements with max counts (`max_lines_count`, `max_labels_count`)
- Use `display` parameter to control plot visibility based on user preferences