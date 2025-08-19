# Real-Time Stock Ratio Analysis Dashboard

This project is a financial analysis tool that provides a real-time streaming dashboard to monitor the price ratio between two stocks. It is designed to help users identify trading opportunities by visualizing deviations in the stock price relationship.

## Overview

The application continuously fetches live market data for two stocks, calculates the ratio of their prices, and plots this ratio on an interactive chart. It also defines an upper and lower bound for the ratio; if the live ratio crosses these bounds, a visual alert is triggered on the graph.

This tool is built with a `Python` script for data processing and a `React`/`TypeScript` frontend for data visualization.

## Features

* **Real-Time Data Processing**: Fetches live bid and ask prices from a stock market feed.
* **Ratio Calculation**: Computes the real-time ratio of the two stocks' mid-prices (average of bid and ask).
* **Interactive Dashboard**: Uses the `Perspective` library to render a high-performance, interactive time-series chart.
* **Automated Alerts**: Automatically triggers and displays alerts on the graph when the price ratio deviates beyond a predefined threshold (e.g., ±5%).
* **Robust & Tested**: The Python data client includes a suite of unit tests to ensure data calculations are accurate and reliable.

## How It Works

The project consists of two main components:

### 1. Backend Data Client (Python)

The `client.py` script is responsible for:

* Connecting to the data feed to stream quotes for two stocks.
* Calculating the mid-price for each stock as `(top_bid_price + top_ask_price) / 2`.
* Computing the ratio of the two stocks' prices.
* Outputting the calculated data for the frontend to consume.

### 2. Frontend Dashboard (React & TypeScript)

The frontend is a web application that:

* Receives the processed data from the Python client.
* Uses `DataManipulator.ts` to structure the data for visualization, calculating the ratio and checking if it has breached the predefined upper or lower bounds.
* Renders the data in `Graph.tsx`, a React component that displays a time-series chart of the following:
    * The live price ratio.
    * The upper bound line.
    * The lower bound line.
    * A trigger alert marker if a bound is breached.

## Technologies Used

* **Backend**: `Python`
* **Frontend**: `React`, `TypeScript`
* **Data Visualization**: `Perspective`
* **Testing**: `unittest` (Python)

## Setup and Installation

To run this project, you will need to set up both the Python client and the React frontend.

**Prerequisites**:

* Python 3.x
* Node.js and npm

**Backend**:

1.  Navigate to the root directory.
2.  Install Python dependencies:
    ```sh
    pip install -r requirements.txt
    ```
3.  Run the client:
    ```sh
    python client.py
    ```

**Frontend**:

1.  Navigate to the `src` directory.
2.  Install npm packages:
    ```sh
    npm install
    ```
3.  Start the development server:
    ```sh
    npm start
    ```
4.  Open your browser to `http://localhost:3000` to view the dashboard.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.
