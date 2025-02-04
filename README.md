
---
# CO_O2_Analyser
## Overview

**CO_O2_Analyser** is a software tool designed to communicate with the **Teledyne N300M** carbon monoxide analyzer via HTTP protocol, retrieve air quality data, and store it in a database. The software provides a graphical interface for real-time monitoring of **CO (Carbon Monoxide) and O₂ (Oxygen)** concentrations over time. Additionally, it generates reports for **governmental exhaust gas quality certification** by recalculating and processing analyzer data.

## Features

- **Real-time Data Monitoring**: Displays CO and O₂ levels over time.
- **Graphical User Interface (GUI)**: Includes connection status and issue indicators.
- **Automated Data Harvesting**: Retrieves data from the Teledyne N300M using a RESTful API (JSON format).
- **Database Integration**: Stores historical measurement data for further analysis.
- **Report Generation**: Produces air quality certification reports.
- **HTTP-Based Communication**: Utilizes REST API over port **8180** for interfacing with the Teledyne N300M.

## System Requirements

- **Operating System**: Linux (Ubuntu 22.04 recommended) / Windows
- **Programming Language**: Python 3.x
- **Dependencies**:
  - `requests` (for API communication)
  - `matplotlib` (for graph visualization)
  - `pandas` (for data processing)
  - `sqlite3` or another database for data storage
  - `flask` (if a web interface is needed)
- **Hardware**: Teledyne N300M Analyzer connected via network

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/your-repo/CO_O2_Analyser.git
   cd CO_O2_Analyser
   ```

2. Install required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Configure database settings (if required).

4. Run the application:
   ```bash
   python main.py
   ```

## API Documentation

The software communicates with the **Teledyne N300M** instrument using the **TAPI Tag REST Interface**. The API supports the following key operations:

- **Retrieve Instrument Tags**:
  ```http
  GET http://<device-ip>:8180/api/taglist
  ```

- **Get Tag Value**:
  ```http
  GET http://<device-ip>:8180/api/tag/{tag.Name}/value
  ```

- **Set Tag Value**:
  ```http
  PUT http://<device-ip>:8180/api/tag/{tag.Name}/value
  Content-Type: application/json
  {
    "value": "new_value"
  }
  ```

- **Retrieve Logged Data**:
  ```http
  GET http://<device-ip>:8180/api/dataloglist
  ```

Refer to the [API.md](API.md) file for the full API documentation.

## User Interface

- **Connection Status Indicator**: Displays connection issues or errors.
- **Graph Display**: Plots real-time **CO** and **O₂** levels with time on the X-axis.
- **Report Export**: Users can generate and download certification reports.

## Data Storage

- Collected data is stored in a **relational database** (`SQLite`, `PostgreSQL`, etc.).
- The software periodically fetches data and updates the database.
- Logged data can be accessed via the UI or exported to CSV/PDF.

## Error Handling

Common API errors include:

- **400 Bad Request**: Invalid request format.
- **401 Unauthorized**: Access denied due to authentication issues.
- **404 Not Found**: Requested resource does not exist.
- **500 Internal Server Error**: Instrument-side error.
- **503 Service Unavailable**: Overloaded or unreachable instrument.

## Contribution

1. Fork the repository.
2. Create a feature branch (`feature-xyz`).
3. Commit your changes and push to your fork.
4. Create a Pull Request.

## License

This project is licensed under the MIT License.

## Contact

For inquiries, please contact:
- **Developer**: Wojciech Gajewski
- **Email**: software@farfalelab.com
- **Company**:  Farfalle Lab Software Solution

---
