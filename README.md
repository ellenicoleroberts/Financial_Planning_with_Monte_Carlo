<img src= "images/mc.png" width="930" height="200">

# Financial Planning
This notebook creates two financial analysis tools: 

_Tool #1_: A financial planner for emergencies whereby users are able to visualize their current savings and plan accordingly.

_Tool #2_: A financial planner for retirement that forecasts the performance of a retirement portfolio for a specified amount of time. It uses Monte Carlo simulations based off of historical data acquired with an Alpaca API call via the Alpaca SDK. 

---
## Technologies

This application leverages python 3.7 with the following packages:

* pandas: an open-source library that offers easy-to-use data analysis tools for Python.
* pathlib: for creation of file paths allowing the application to interact with a computer's filesystem.
* %matplotlib: for creating static, animated, and interactive visualizations in Python.
* requests: a library that helps access data via APIs.
* json: a library for putting API responses into a human-readable format.
* python-dotenv: a library for reading key-value pairs from an environment file (.env) and adding them as  
  environment variables.
* alpaca-trade-api: the Alpaca SDK used to interact with the Alpaca API (Alpaca is an API for stock 
  trading.)

---
## Installation Guide

Begin by cloning the GitHub repo (the same repo that this README.md file is contained within) into your terminal. 

Then activate the correct environment by inputting the following command into your terminal:

`conda activate dev`

Within this environment, next install the above listed dependencies. To do so, in your terminal while in this same repo, enter `pip install -r requirements.txt`.

Finally, while in your IDE, open the "financial_planning_tools.ipynb" notebook file and run the code.

Note: Requests and JSON libraries should already be installed with Anaconda. To confirm their installation, in your terminal activate the Conda development environment, and then enter `conda list requests` and `conda list json`. If they are not installed, in your terminal install each respectively with the following: `conda install -c anaconda requests` and `conda install -c jmcmurray json`.

Note: This code requires use of Alpaca API keys. If you do not already have Alpaca API keys, to get set up please consult [this guide](https://algotrading101.com/learn/alpaca-trading-api-guide/).

Note: The MCForecastTools library file is included in this repo. Specifically, this code uses and imports the MCSimulation module from the MCForecastTools library.

---
## Usage

### _Tool #1: A Financial Planner for Emergencies_

The first part of this code evaluates the value of a cryptocurrency wallet containing Bitcoin and Ethereum. The current prices for Bitcoin and Ethereum are determined by using the Python Requests library, assuming (for this prototype) that the member holds 1.2 Bitcoins (BTC) and 5.3 Ethereum coins (ETH). 

The second part of this code evaluates a member's stock and bond holdings by using the Alpaca SDK. First, the code makes an API call to Alpaca via the Alpaca SDK to get the current closing prices of the SPDR S&P 500 ETF Trust (ticker: SPY) and of the iShares Core US Aggregate Bond ETF (ticker: AGG). Assuming that the member holds 110 shares of SPY (representing the stock portion of their portfolio) and 200 shares of AGG (representing the bond portion of their portfolio), the code then calculates the value of each of the stock and bond portions of the portfolio and finally the total value of the stock and bond holdings together.

The third part of this code determines if the member has enough savings to build an emergency fund into their financial plan given the valuations for their cryptocurrency wallet and for the stock and bond portions of their portfolio. A pie chart that visualizes the composition of the member’s portfolio is then plotted, as shown here:

![Portfolio pie chart.](images/portfolio.png)

### _Tool #2: A Financial Planner for Retirement_

This section uses the MCForecastTools library to create a Monte Carlo simulation for the member’s savings portfolio. 

An API call is made via the Alpaca SDK to get three years of historical closing prices for a 60/40 portfolio split: 60% stocks (SPY) and 40% bonds (AGG).

Next, a Monte Carlo simulation is run for 500 samples and 30 years for the 60/40 portfolio, and then the results are plotted as shown here: 

![Monte Carlo simulation.](images/examplemc.png)

The probability distribution of the Monte Carlo simulation is plotted with a histogram and summary statistics are generated. Using these statistics, specifically the upper and lower bounds of a 95% confidence interval, the expected value of the portfolio in 30 years is determined.

Finally, each step in this section (_Tool #2: A Financial Planner for Retirement_) is then repeated to forecast the portfolio's value in 10 years from now using an 80/20 portfolio split: 80% stocks (SPY) and 20% bonds (AGG).

The two investment approaches (the 60/40 split invested for 30 years versus the 80/20 split invested for 10 years) are compared.

---
## Contributors

Nicole Roberts,
elle.nicole.roberts@gmail.com

---

## License

[BSD 3](https://choosealicense.com/licenses/bsd-3-clause-clear/): BSD 3-clause is a permissive licence, allowing nearly unlimited freedom with the software as long as BSD copyright and license notice is included.
