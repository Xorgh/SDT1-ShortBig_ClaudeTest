# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Stock trading game — a JavaFX desktop application where users buy/sell simulated stocks to grow their portfolio balance. DevSchool (SDT1) learning project.

**Tech stack**: Java, JavaFX (UI), file-based persistence.

## Build & Run

No build system (Gradle/Maven) is configured yet. Java source files are in `src/` without a standard build tool structure. When a build system is added, update this section.

## Architecture

Clean architecture with layer-based package organization:

```
src/
├── entities/       # Domain models (Portfolio, Stock, Transaction, OwnedStock, StockPriceHistory, enums)
├── business/       # Business logic services (not yet implemented)
├── dtos/           # Data Transfer Objects (not yet implemented)
├── persistence/    # File-based data access (not yet implemented)
├── presentation/   # JavaFX UI controllers (not yet implemented)
└── shared/         # Common utilities (not yet implemented)
```

**Data flow**: presentation → dtos → business → entities/persistence

## Domain Model

- **Portfolio**: user's account with a balance. Identified by UUID.
- **Stock**: tradeable asset with symbol (PK), name, current price, and state (up/down/stable).
- **OwnedStock**: links a portfolio to a stock with share count. FK to portfolio (UUID) and stock (symbol).
- **Transaction**: records a buy/sell action. FK to portfolio and stock. Includes quantity, price, fee, timestamp.
- **StockPriceHistory**: tracks price over time per stock symbol.
- **TransactionType** enum: `BUY`, `SELL`
- **StockState** enum: values not yet defined (TODO).

All entities use `UUID` for primary keys (except Stock which uses its symbol). Entity classes use `final` fields for immutability where appropriate.

## Functional Requirements

Mandatory: real-time stock chart (F1), buy (F2), sell (F3), view portfolio (F4), win condition at target balance (F5).
Optional: transaction history (F6), portfolio balance history (F7), multiple portfolios (F8).

## Current State

Entity layer is scaffolded but incomplete — most classes lack getters/setters and have TODO comments. All other layers are empty placeholder directories.
