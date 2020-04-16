FLYBIT OPEN API
===================
Thank you for visiting Flybit's Development Page. Flybit is currently providing "REST API" to our users and public. Restful API has two types; 1. Public 2. Private

1. Public   : Anyone can access.      - functions: orderbook/transaction history/ticker/market/system satus. 
2. Private  : Only for Flybit's users. - functions: order call/cancel/order history/balance. 

Contact: If you have any question/concern/suggestion for our development page or <a href="https://flybit.com">trading site</a>, please leave a message in <a href="https://github.com/flybit-core/flybit-api/issues">Issue section</a>.

API List
-------------
<table style="width:90%">
  <thead><tr><th>URL</th><th>Type</th><th>Description</th></tr></thead>
  <tbody><tr><td><a href="#marketall">public/market/all</a></td><td>Public</td><td>Get Market Information</td></tr>
  <tr><td><a href="#ticker">public/ticker</a></td><td>Public</td><td>Get Ticker</td></tr>
  <tr><td><a href="#orderbook">public/orderbook</a></td><td>Public</td><td>Get OrderBook</td></tr>
  <tr><td><a href="#transhistory">public/transaction_history</a></td><td>Public</td><td>Get Transaction History</td></tr>
  <tr><td><a href="#sysstatus">public/systemStatus</a></td><td>Public</td><td>Get System Status</td></tr>
  <tr><td><a href="#waddress">private/walletInfo</a></td><td>Private</td><td>Get Account Balances</td></tr>
  <tr><td><a href="#orderhis">private/orderHis</a></td><td>Private</td><td>Get Order History</td></tr>
  <tr><td><a href="#order">private/order</a></td><td>Private</td><td>Create Order</td></tr>
  <tr><td><a href="#cancel">private/deleteOrder</a></td><td>Private</td><td>Cancel Orders</td></tr>
  </tbody>
</table>


-------------
####  <p id="marketall" name="marketall">1. Market Information</p>
> **Description:**
 Provide market information
> - url : https://api.flybit.com/v2/public/market/all
  <p>Input Parameters: No</p>
  <p>Return Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>market</td><td>String</td><td>Market Information</td></tr>
    <tr><td>korean_name</td><td>String</td><td>Cryptocurrency Korean</td></tr>
    <tr><td>english_name</td><td>String</td><td>Cryptocurrency English</td></tr>
    <tr><td>market_Id</td><td>String</td><td>Market ID</td></tr>
  </table>
  <pre>
  [
  {
    "MARKET":"BTC-ETH",
    "KOREAN_NAME":"이더리움",
    "ENGLISH_NAME":"ETH"
  },
  {
    "MARKET":"ETH-BTC",
    "KOREAN_NAME":"비트코인",
    "ENGLISH_NAME":"BTC"
  }
  ] 
  </pre>
  
  ####  <p id="ticker" name="marketall">2. Ticker</p>
  > **Description:**
   The current price of the exchange cryptocurrency at the time of processing request is provided
  > - url : https://api.flybit.com/v2/public/ticker?market=KRW-BTC
  <p>Input Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>market</td><td>String</td><td>Market Group</td></tr>
  </table>
  <p>Return Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>closing_price</td><td>Number(String)</td><td>Closing price 00:00 basis</td></tr>
    <tr><td>prev_closing_price</td><td>Number(String)</td><td>Previous day’s closing price</td></tr>
    <tr><td>date</td><td>String</td><td>Date time</td></tr>
    <tr><td>fluctuate_24h</td><td>Number(String)</td><td>The change in the last 24hours</td></tr>
    <tr><td>acc_trade_value</td><td>Number(String)</td><td>Volume 00:00 basis</td></tr>
    <tr><td>min_price</td><td>Number(String)</td><td>Low price 00:00 basis</td></tr>
    <tr><td>opening_price</td><td>Number(String)</td><td>Current Price 00:00 basis</td></tr>
    <tr><td>units_traded</td><td>Number(String)</td><td>Volume 00:00 basis</td></tr>
    <tr><td>units_traded_24h</td><td>Number(String)</td><td>Last 24hour volume</td></tr>
    <tr><td>fluctuate_rate_24h</td><td>Number(String)</td><td>Last 24hour volume change</td></tr>
    <tr><td>acc_trade_value_24h</td><td>Number(String)</td><td>Last 24hour trading amount</td></tr>
    <tr><td>max_price</td><td>Number(String)</td><td>High 00:00 basis</td></tr>
  </table>
  <pre>
  {
    "CLOSING_PRICE": 9735000,
    "PREV_CLOSING_PRICE": 9040000,
    "DATE": 1578448510137,
    "FLUCTATE_24H": 700000,
    "ACC_TRADE_VALUE": 37247083.5,
    "MIN_PRICE": 8885000,
    "OPENING_PRICE": 9735000,
    "UNITS_TRADED": 3.8261,
    "UNITS_TRADED_24H": 10.45288198,
    "FLUCTATE_RATE_24H": 0,
    "ACC_TRADE_VALUE_24H": 101654277.2555,
    "MAX_PRICE": 9735000
  }
  </pre>
  
  ####  <p id="orderbook" name="orderbook">3. OrderBook</p>
  > **Description:**
  Provides order information of exchange cryptocurrency at the time of processing request
  > - url : https://api.flybit.com/v2/public/orderbook?market=KRW-BTC
  <p>Input Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>market</td><td>String</td><td>Market Group</td></tr>
  </table>
  <p>Return Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>bid</td><td>Array[Object]</td><td>Purchase request history</td></tr>
    <tr><td>quantity</td><td>Number(String)</td><td>Purchase Currency quantity</td></tr>
    <tr><td>price</td><td>Number(String)</td><td>Purchase Currency price</td></tr>
    <tr><td>ask</td><td>Array[Object]</td><td>Sell request history</td></tr>
    <tr><td>quantity</td><td>Number(String)</td><td>Sell Currency quantity</td></tr>
    <tr><td>price</td><td>Number(String)</td><td>Sell Currency price</td></tr>
  </table>
  <pre>
  {
    "result": {
        "ask": [
            {
                " PRICE": 9710000,
                " QUANTITY": 0.016
            },
            {
                " PRICE": 9700000,
                " QUANTITY ": 0.002
            },
            …….
        ],
        "bid": [
            {
                " PRICE": 4217000,
                " QUANTITY ": 2.186
            },
            {
                " PRICE": 4217000,
                " QUANTITY ": 1.96
            }
            ……..
        ]
    }
  }

  </pre>  
  
  ####  <p id="transhistory" name="transhistory">4. Transaction History</p>
  > **Description:**
  Provides details of transaction completion
  > - url : https://api.flybit.com/v2/public/transaction_history?market=KRW-BTC
  <p>Input Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>market</td><td>String</td><td>Market Group</td></tr>
  </table>
  <p>Return Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>total</td><td>Number(String)</td><td>Total transaction amount</td></tr>
    <tr><td>transaction_date</td><td>String</td><td>Execution time</td></tr>
    <tr><td>price</td><td>Number(String)</td><td>Execution Price</td></tr>
    <tr><td>units_traded</td><td>Number(String)</td><td>Volume</td></tr>
    <tr><td>type</td><td>String</td><td>Transaction type(bid:purshase, ask:sell)</td></tr>
  </table>
  <pre>
  [
    {
        "TOTAL": 31878,
        "TRANSACTION_DATE": "2020-01-08 11:21:23",
        "PRICE": 9660000,
        "UNITS_TRADED": 0.0033,
        "TYPE": "BID"
    },
    {
        "TOTAL": 0.00001815,
        "TRANSACTION_DATE": "2020-01-08 11:21:23",
        "PRICE": 0.0033,
        "UNITS_TRADED": 0.0055,
        "TYPE": "ASK"
    },
    {
        "TOTAL": 11592,
        "TRANSACTION_DATE": "2020-01-08 11:21:15",
        "PRICE": 9660000,
        "UNITS_TRADED": 0.0012,
        "TYPE": "BID"
    },
    {
        "TOTAL": 0.0000066,
        "TRANSACTION_DATE": "2020-01-08 11:21:15",
        "PRICE": 0.0012,
        "UNITS_TRADED": 0.0055,
        "TYPE": "ASK"
    }
  ]

  </pre>  
  
  ####  <p id="sysstatus" name="sysstatus">5. System Status</p>
  > **Description:**
  Provides processing system information
  > - url : https://api.flybit.com/v2/public/systemStatus
  <p>Input Parameters: No</p>
  <p>Return Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>coin</td><td>String</td><td>Crytocurrency name</td></tr>
    <tr><td>assetType</td><td>String</td><td>Activation</td></tr>
    <tr><td>deposit</td><td>String</td><td>Market Status</td></tr>
    <tr><td>withdrawals</td><td>String</td><td>Withdrawals Status</td></tr>
    <tr><td>trading</td><td>String</td><td>Whether to trade</td></tr>
  <tr><td>url</td><td>String</td><td>Tracking address</td></tr>
  </table>
  <pre>
  [
    {
        "DEPOSITS": "Active",
        "ASSETTYPE": "Coin",
        "WITHDRAWALS": "Active",
        "TRADING": "Active",
        "COIN": "BTC",
        "URL": ""
    },
    {
        "DEPOSITS": "Active",
        "ASSETTYPE": "Coin",
        "WITHDRAWALS": "Active",
        "TRADING": "Active",
        "COIN": "ETH",
        "URL": ""
    },
    {
        "DEPOSITS": "Active",
        "ASSETTYPE": "Coin",
        "WITHDRAWALS": "Active",
        "TRADING": "Active",
        "COIN": "BCH",
        "URL": ""
    }
  ]
  </pre>  
  
  
  ####  <p id="waddress" name="waddress">6. Wallet Account Balance</p>
  > **Description:**
  Provides the transaction wallet member's coin wallet address, quantity and usage
  > - url : https://api.flybit.com/v2/private/walletInfo
  <p>Input Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>authorization</td><td>String</td><td>Header(accessKey,nonce)</td></tr>
  </table>
  <p>Return Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>Address</td><td>String</td><td>Wallet address</td></tr>
    <tr><td>Balance</td><td>String</td><td>Total amount</td></tr>
    <tr><td>Locked</td><td>String</td><td>The amount enclosed during the order</td></tr>
    <tr><td>Currency</td><td>String</td><td>an abbreviation for money on English</td></tr>
  </table>
  <pre>
  {
    "result": [
        {
            "CURRENCY": "KRW",
            "LOCKED": 51400,
            "ADDRESS": "35260101125712",
            "BALANCE": 229702.18600209
        },
        {
            "CURRENCY": "BTC",
            "LOCKED": 0,
            "ADDRESS": "3BXXXXXXXXXXX",
            "BALANCE": 0.54346056
        },
        {
            "CURRENCY": "ETH",
            "LOCKED": 0,
            "ADDRESS": "0x3aXXXXXXXXXX",
            "BALANCE": 10000941.43676287
        },
        {
            "CURRENCY": "HDAC",
            "LOCKED": 14,
            "ADDRESS": "4aXXXXXXXXXXXXX",
            "BALANCE": 100989.01
        }

    ]
  }

  </pre>

  ####  <p id="orderhis" name="orderhis">7. Order History</p>
  > **Description:**
  Processing history provides members buy / sell-registered or history information of the transaction
  > - url : https://api.flybit.com/v2/private/orderHis
  <p>Input Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>authorization</td><td>String</td><td>Header(accessKey,nonce)</td></tr>
    <tr><td>orderId</td><td>String</td><td>Order number(if none)</td></tr>
    <tr><td>marketId</td><td>Number</td><td>unique key (1)</td></tr>
    <tr><td>state</td><td>String</td><td>Order Status ( GO: Order , CC: Cancel, CM: Closed)</td></tr>
    <tr><td>count</td><td>Number</td><td>Number of inquary (Default 100)</td></tr>
  </table>
  <p>Return Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>ORDER_ID</td><td>String</td><td>Unique ID of the order</td></tr>
    <tr><td>SIDE</td><td>String</td><td>Order type ( B: Buy , S: Sell)</td></tr>
    <tr><td>ORD_TYPE</td><td>String</td><td>Order method (N:limits price)</td></tr>
    <tr><td>PRICE</td><td>String</td><td>The currency price at the time of order</td></tr>
    <tr><td>STATE</td><td>String</td><td>Order Status ( GO: Order , CC: Cancel, CM: Closed)</td></tr>
    <tr><td>MARKET</td><td>String</td><td>Market unique code</td></tr>
    <tr><td>CURRENCY</td><td>String</td><td>an abbreviation for money on English</td></tr>
    <tr><td>CREATED_AT</td><td>String</td><td>Order creation time</td></tr>
    <tr><td>VOLUME</td><td>String</td><td>Order quantity entered by the user</td></tr>
    <tr><td>REMAINING_VOLUME</td><td>String</td><td>Remaining order after order execution</td></tr>
    <tr><td>EXECUTED_VOLUME</td><td>String</td><td>Executed volume</td></tr>
  </table>
  <pre>
  {
    "result": [
        {
            "CURRENCY": "BTC",
            "SIDE": "B",
            "EXECUTED_VOLUME": 0,
            "MARKET": "KRW",
            "ORDER_ID": 40860911,
            "PRICE": 11210000,
            "CREATED_AT": "2019-07-31 09:33:36",
            "VOLUME": 0.0001,
            "STATE": "CC",
            "REMAINING_VOLUME": 0.0001,
            "ORD_TYPE": "N"
        },
        {
            "CURRENCY": "BTC",
            "SIDE": "B",
            "EXECUTED_VOLUME": 0.0001,
            "MARKET": "KRW",
            "ORDER_ID": 40860910,
            "PRICE": 12000000,
            "CREATED_AT": "2019-07-31 09:32:05",
            "VOLUME": 0.0001,
            "STATE": "CM",
            "REMAINING_VOLUME": 0,
            "ORD_TYPE": "N"
        },
        {
            "CURRENCY": "BTC",
            "SIDE": "B",
            "EXECUTED_VOLUME": 0.0001,
            "MARKET": "KRW",
            "ORDER_ID": 40858873,
            "PRICE": 22000000,
            "CREATED_AT": "2019-07-17 14:44:59",
            "VOLUME": 0.0001,
            "STATE": "CM",
            "REMAINING_VOLUME": 0,
            "ORD_TYPE": "N"
        }
    ]
  }
  </pre>

  ####  <p id="order" name="order">8. Order</p>
  > **Description:**
  Processing history Buy / Sell register function
  > - url : https://api.flybit.com/v2/private/order
  <p>Input Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>authorization</td><td>String</td><td>Header(accessKey,nonce)</td></tr>
    <tr><td>marketId</td><td>Number</td><td>unique key (1)</td></tr>
    <tr><td>amount</td><td>Number</td><td>Order quantity</td></tr>
    <tr><td>orderType</td><td>String</td><td>Order Type ( B: Buy , S: Sell)</td></tr>
    <tr><td>callType</td><td>String</td><td>call type(N)</td></tr>
    <tr><td>price</td><td>Number</td><td>Order price</td></tr>
  </table>
  <p>Return Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>ORDER_ID</td><td>String</td><td>Unique ID of the order</td></tr>
    <tr><td>SIDE</td><td>String</td><td>Order type ( B: Buy , S: Sell)</td></tr>
    <tr><td>ORD_TYPE</td><td>String</td><td>Order method (N:limits price)</td></tr>
    <tr><td>PRICE</td><td>String</td><td>The currency price at the time of order</td></tr>
    <tr><td>STATE</td><td>String</td><td>Order Status ( GO: Order , CC: Cancel, CM: Closed)</td></tr>
    <tr><td>MARKET</td><td>String</td><td>Market unique code</td></tr>
    <tr><td>CURRENCY</td><td>String</td><td>an abbreviation for money on English</td></tr>
  </table>
  <pre>
  {
    "result": [
        {
            "orderId": 40860911,
            "status": "true"
        }
    ]
  }
  </pre>
  
  ####  <p id="cancel" name="cancel">9. Cancel</p>
  > **Description:**
  Processing history offers registered buy / sell order cancellation feature
  > - url : https://api.flybit.com/v2/private/deleteOrder

  <p>Input Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>authorization</td><td>String</td><td>Header(accessKey,nonce)</td></tr>
    <tr><td>orderId</td><td>int</td><td>Order no</td></tr>
  </table>
  <p>Return Parameters</p>
  <table>
    <tr><th>Parameters</th><th>Date Type</th><th>Description</th></tr>
    <tr><td>status</td><td>String</td><td>true/false</td></tr>
  </table>
  <pre>
  {
    "result": [
        {
            "STATUS": "TRUE"
        }
    ]
  }
  </pre>
  
  ERROR CODE
-------------
<table style="width:90%">
  <thead><tr><th>CODE</th><th>Description(ENG)</th><th>Description(ENG)</th></tr></thead>
  <tbody><tr><td>9001</td><td>Description</td></tr>
  <tr><td>9002</td><td>Description</td></tr>
  <tr><td>9003</td><td>Description</td></tr>
  <tr><td>4001</td><td>Description</td></tr>
  <tr><td>4002</td><td>Description</td></tr>
  <tr><td>4003</td><td>Description</td></tr>
  <tr><td>4004</td><td>Description</td></tr>
  <tr><td>4005</td><td>Description</td></tr>
  <tr><td>4010</td><td>Description</td></tr>
  <tr><td>4070</td><td>Description</td></tr>
  <tr><td>4080</td><td>Description</td></tr>
  <tr><td>4090</td><td>Description</td></tr>
  <tr><td>20011</td><td>Description</td></tr>
  <tr><td>20012</td><td>Description</td></tr>
  <tr><td>20021</td><td>Description</td></tr>
  <tr><td>20022</td><td>Description</td></tr>
  <tr><td>20031</td><td>Description</td></tr>
  <tr><td>20032</td><td>Description</td></tr>
  <tr><td>20033</td><td>Description</td></tr>
  <tr><td>5000</td><td>Description</td></tr>
  <tr><td>5001</td><td>Description</td></tr>
  </tbody>
</table>
