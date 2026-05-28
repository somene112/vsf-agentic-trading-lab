# Project Targets

## Main Direction

I want to focus on autonomous trading agents from a design-first and CLI-first perspective.

At this stage, I will prioritize domain knowledge, architecture, data pipeline design, and evaluation methodology before building a complex backend or UI.

## Target 1: Domain Knowledge

Build a solid understanding of:

- Market data and time-series data
- Trading signals
- Labeling methods
- Feature engineering
- Cross-validation for financial data
- Backtesting limitations
- Risk management
- Market simulation
- Agent-based trading systems

## Target 2: Architecture Design

Design a practical autonomous trading agent pipeline, including:

1. Data ingestion
2. Data storage and retrieval
3. Feature engineering
4. Signal generation
5. Strategy decision layer
6. Risk control
7. Backtesting and evaluation
8. Logging and reporting

The first implementation should be CLI-first rather than UI-first.

## Target 3: Data Infrastructure

Research suitable database/storage options for trading agents:

- In-memory vs on-disk storage
- SQL databases
- Time-series databases
- Columnar storage
- Vector databases for news, reports, and memory retrieval
- Tradeoffs between latency, cost, and complexity

## Target 4: Cost vs Efficiency

Evaluate when LLMs are actually useful.

LLMs may be useful for:

- News summarization
- Report interpretation
- Reasoning over qualitative information
- Agent explanation
- Research assistant workflows

LLMs may not be necessary for:

- Low-latency numerical signal generation
- Simple tabular feature pipelines
- Deterministic risk checks
- Standard backtesting logic

## Target 5: Documentation

Keep the repository easy to review by maintaining:

- Clear README
- Research notes
- Architecture documents
- CLI scripts
- Docusaurus-ready documentation structure

## Not in Scope for Early Stage

- No LLM fine-tuning
- No complex frontend
- No production-grade backend yet
- No private/company-sensitive data in the public repository
