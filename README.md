# MCP Beginner Project

This repository contains a collection of projects built using the MCP (Model Control Protocol) framework. The main project is a Weather Service that provides weather alerts and forecasts using the National Weather Service API.

## Project Structure

```
mcp-beginner/
├── .git/               # Git repository data
├── .gitignore         # Git ignore rules
├── tester.json        # Test configuration file
└── weather/           # Weather service project
    ├── .python-version # Python version specification
    ├── .venv/         # Virtual environment directory
    ├── README.md      # Weather project specific documentation
    ├── hello.py       # Simple hello world example
    ├── pyproject.toml # Project dependencies and metadata
    ├── uv.lock        # Dependency lock file
    └── weather.py     # Main weather service implementation
```

## Weather Service

The main application is a weather service that provides two main functionalities:

1. **Weather Alerts**: Get active weather alerts for any US state
2. **Weather Forecast**: Get detailed weather forecasts for any location using latitude and longitude

### Features

- Fetches data from the National Weather Service API
- Provides formatted, readable weather alerts and forecasts
- Handles errors gracefully
- Implements proper API request handling with timeouts and headers

### Technical Details

- **Python Version**: 3.11+
- **Key Dependencies**:
  - `httpx`: For making async HTTP requests
  - `mcp`: Model Control Protocol framework for tool integration

### API Endpoints

1. `get_alerts(state: str)`:
   - Takes a two-letter US state code (e.g., "CA", "NY")
   - Returns active weather alerts for the specified state

2. `get_forecast(latitude: float, longitude: float)`:
   - Takes latitude and longitude coordinates
   - Returns a 5-period weather forecast for the specified location

## Setup and Installation

1. Ensure you have Python 3.11 or higher installed
2. Navigate to the weather directory:
   ```bash
   cd weather
   ```
3. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```
4. Install dependencies:
   ```bash
   pip install -e .
   ```

## Usage

The weather service can be run as an MCP server:

```python
from weather import get_alerts, get_forecast

# Get weather alerts for California
alerts = await get_alerts("CA")

# Get weather forecast for San Francisco
forecast = await get_forecast(37.7749, -122.4194)
```