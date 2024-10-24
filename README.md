# Task Automation Agent

An intelligent agent framework for automating complex web-based tasks using LLMs and modern automation tools.

## Overview

This project implements a modular, extensible automation framework that combines Large Language Models (LLMs) with web automation tools to create intelligent agents capable of handling complex tasks autonomously.

## Architecture

### Core System Architecture

```mermaid
graph TB
    subgraph "Core System"
        AC[Agent Controller]
        LLM[LLM Engine]
        AE[Automation Engine]
        MS[Memory System]
        TI[Tool Integration]
    end

    User -->|Input| AC
    AC -->|Tasks| LLM
    LLM -->|Commands| AE
    AE -->|Results| MS
    MS -->|Context| LLM
    TI -->|External Data| AE
    AE -->|Actions| External[External Systems]
    MS -->|History| AC
```

## Tech Stack

- **Base LLM**: Mistral-7b or Llama2
- **Framework**: LangChain or AutoGPT
- **Browser Automation**: Playwright/Selenium
- **Vector DB**: ChromaDB

## Core Components

### 1. Agent Controller

- Central orchestrator managing workflow
- Handles task parsing and goal setting
- Manages component coordination
- Implements error handling and recovery
- Maintains state management
- Monitors execution

### 2. LLM Engine

Decision making and reasoning core with components:

- **Task Planning Module**
  - Breaks down high-level tasks
  - Generates execution plans
- **Decision Engine**
  - Evaluates scenarios
  - Handles uncertainty
- **Response Parser**
  - Structures outputs
  - Validates responses

### 3. Automation Engine

Handles system interactions through:

- **Browser Controller**
  - Web session management
  - Dynamic content handling
  - Retry mechanisms
- **Element Interaction Manager**
  - Selector management
  - UI change handling
- **Data Extractor**
  - Information scraping
  - Data validation

### 4. Memory System

Maintains context through:

```mermaid
graph TB
    subgraph "Memory Management"
        STM[Short Term Memory]
        LTM[Long Term Memory]
        VS[Vector Store]
    end

    Input[New Data] --> STM
    STM -->|Important Info| LTM
    STM -->|Embeddings| VS
    VS -->|Similar Cases| LLM
    LTM -->|Historical Patterns| LLM
```

## Execution Flow

### Component Interaction

```mermaid
sequenceDiagram
    participant User
    participant Controller
    participant LLM
    participant Automation
    participant Memory

    User->>Controller: Submit Task
    Controller->>Memory: Load Context
    Controller->>LLM: Generate Plan
    LLM->>Controller: Return Action Steps
    loop Execution
        Controller->>Automation: Execute Action
        Automation->>Memory: Store Result
        Memory->>LLM: Update Context
        LLM->>Controller: Next Action
    end
    Controller->>User: Return Result
```

### State Management

```mermaid
stateDiagram-v2
    [*] --> Initialize
    Initialize --> Planning
    Planning --> Execution
    Execution --> Monitoring
    Monitoring --> Success
    Monitoring --> Failure
    Success --> [*]
    Failure --> ErrorHandling
    ErrorHandling --> Planning
    ErrorHandling --> Execution
```

## Example Use Case: Flight Booking

```mermaid
graph TB
    Start[Start] --> LoadPrefs[Load Preferences]
    LoadPrefs --> SearchStrat[Generate Search Strategy]
    SearchStrat --> Navigate[Navigate to Site]
    Navigate --> Search[Execute Search]
    Search --> Extract[Extract Results]
    Extract --> Analyze[Analyze Prices]
    Analyze --> Decision{Decision Making}
    Decision -->|Good Price| Book[Start Booking]
    Decision -->|High Price| Wait[Wait/Monitor]
    Book --> Payment[Process Payment]
    Payment --> Confirm[Confirm Booking]
    Wait --> Search
    Confirm --> End[End]
```

### Task Flow:

1. **Initialization**

   - Parse requirements
   - Load past experiences
   - Generate search strategy

2. **Planning**

   - Site navigation
   - Search execution
   - Result analysis
   - Price comparison
   - Booking process

3. **Execution**
   - Navigate site
   - Input criteria
   - Analyze results
   - Make decisions
   - Handle payment

## Getting Started

[Coming Soon]

## Contributing

[Coming Soon]

## License

[Coming Soon]
