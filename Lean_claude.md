# Claude Project Context: Lean Algorithmic Trading Engine

This file provides comprehensive codebase context regarding this customized fork of the QuantConnect Lean trading platform for Claude AI.

## Project Overview
* **Name**: LEAN Algorithmic Trading Engine (by QuantConnect)
* **Languages**: C# (94.2% - Core Engine & Type Definitions), Python (5.6% - Algorithm API bindings)
* **Type**: Professional-caliber, event-driven quantitative simulation and live execution platform.
* **Supported Asset Classes**: Equities, Forex, Options, Futures, Crypto, and Alternative Data wrappers.

## Core Modular Architecture
LEAN operates via an elegant, decoupled structure with clear plug-in points:
1. **Algorithm Interface**: The code defined by the user (written using `Algorithm.Python` or `Algorithm.CSharp`).
2. **Data Feed**: Direct ingestion of streaming ticks, trade bars, or quote data from historical files or live sockets.
3. **Brokerage Models**: Pluggable modules defining exact order execution limits, fill behaviors, and fee models (e.g., Interactive Brokers, Binance).
4. **Transaction Handler**: Orchestrates execution pipelines, active position book keeping, and portfolio valuations.

## Repository Structure & Key Directories
* `/Algorithm.Python/` - Target ecosystem for Python-based trading strategies and documentation.
* `/Algorithm.CSharp/` - Target ecosystem for C#-based trading strategies and performance suites.
* `/Common/` - Shared types, order types, tick specifications, and operational data structures.
* `/Engine/` - Core processing execution engine, transaction queues, and historical data handlers.
* `/Indicators/` - Out-of-the-box system analytical indicator code (e.g., EMA, RSI, Bollinger Bands).
* `/ToolBox/` - Data downloaders and processing micro-tools for parsing raw exchange text formats.

## System Dependencies & Compilation
* **Target Runtime Framework**: `.NET 9 SDK`
* **Linux (Debian/Ubuntu) Setup**: 
  * Build solution: `dotnet build QuantConnect.Lean.sln`
  * Launch engine runner: `cd Launcher/bin/Debug && dotnet QuantConnect.Lean.Launcher.dll`
* **Windows Pipeline**: Load `QuantConnect.Lean.sln` in Visual Studio and tap `F5`.

## Lean Command Line Interface (CLI) Integration
When guiding workflow executions or Docker deployments, leverage the prebuilt `lean` CLI:
* **Installation via Pip**: `pip install lean`
* **Project Generation**: `lean project-create` -> Seeds starter code templates.
* **Local Backtesting (Dockerized)**: `lean backtest`
* **Parameter Optimization**: `lean optimize`
* **Local Notebook Analytics**: `lean research` -> Boots up a managed Jupyter environment.
* **Direct Live Deployments**: `lean live`

## AI Assistant Guidelines for this Project
1. **Event-Driven API Syntax**: When implementing strategies, explicitly override LEAN standard lifecycles such as `Initialize()` for environment configurations and `OnData(Slice data)` for incoming market telemetry.
2. **Co-existence Constraints**: Remember that even if a strategy is scripted in Python, underlying operations leverage C# object definitions via Python.NET wrapper interfaces (e.g., utilize exact API definitions like `self.SetCash(100000)`).
3. **Cross-Asset Accounting**: When suggesting position risk re-balancing metrics, cross-check structural parameters for differences in lot size limits, leverage capabilities, and specific exchange clearing rules.
