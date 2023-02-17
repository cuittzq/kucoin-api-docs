---
title: title

language_tabs: # must be one of https://git.io/vQNgJ


toc_footers:
  - <a href='https://www.kucoin.com'>Sign Up for KuCoin</a>

includes:

search: true
---

# General

## Introduction

Welcome to KuCoin’s trader and developer documentation. These documents outline the exchange functionality, market details, and APIs.

The whole documentation is divided into two parts: REST API and Websocket feed.

The REST API contains four sections: User(private) , Trade(private), Market Data(public), Margin Trade and Others(public).

The WebSocket contains two sections: Public Channels and Private Channels

## Upcoming Changes

To get the latest updates in API, you can click ‘Watch’ on our [KuCoin Docs Github](https://github.com/Kucoin/kucoin-api-docs).

**To reinforce the security of the API, KuCoin upgraded the API key to version 2.0, the validation logic has also been changed. It is recommended to [create](https://www.kucoin.com/account/api) and update your API key to version 2.0. The API key of version 1.0 is invalid. [Check new signing method](#signing-a-message)**


**17/02/23**:
- add Query Margin Trading Pairs `GET /api/v2/margin/symbols`interface
- add Query Lending Configuration `GET /api/v2/margin/lend/config`interface
- add Lending Order Query (Paginated) `GET /api/v2/margin/lend/orders`interface
- add Query Single Lending Order `GET /api/v2/margin/lend`interface
- add Query Lending Records `GET /api/v2/margin/lend/trade/orders`interface
- add Get Isolated Margin Account Info `GET /api/v2/isolated/accounts`
- add Get Cross Margin Account Info  `GET /api/v2/margin/accounts`
- add Query the Max Transferrable Amount  `Get /api/v2/margin/transferable`
- add Get the Leverage Limit `Get /api/v2/margin/riskLimits`
- add Apply for a Loan `POST /api/v2/margin/borrow`
- add Quick Repayment `POST /api/v2/margin/repay/all`
- add Single Repayment `POST /api/v2/margin/repay/single`
- add Query Repayment Records `GET /api/v2/margin/repay`
- add Margin Order Placement `POST /api/v2/margin/order`
- Deprecate  `GET /api/v1/margin/account`, please use  `GET   /api/v2/margin/accounts`
- Deprecate  `GET /api/v1/risk/limit/strategy`, please use  `Get   /api/v2/margin/riskLimits`
- Deprecate  `POST /api/v1/margin/borrow`, please use `POST  /api/v2/margin/borrow`
- Deprecate  `GET /api/v1/margin/borrow/outstanding`, please use `GET /api/v2/margin/repay`
- Deprecate  `GET /api/v1/margin/borrow/repaid`, please use `GET /api/v2/margin/repay`
- Deprecate  `POST /api/v1/margin/repay/all`, please use `POST  /api/v2/margin/repay/all`
- Deprecate  `POST /api/v1/margin/repay/single`, please use `POST /api/v2/margin/repay/single`
- Deprecate  `GET /api/v1/margin/lend/active`, please use `GET /api/v2/margin/lend/orders`
- Deprecate  `GET /api/v1/margin/lend/done`, please use `GET /api/v2/margin/lend/orders`
- Deprecate  `GET /api/v1/margin/lend/trade/unsettled`, please use `GET /api/v2/margin/lend/trade/orders`
- Deprecate  `GET /api/v1/margin/lend/trade/settled`, please use `GET /api/v2/margin/lend/trade/orders`
- Deprecate  `GET /api/v1/margin/market`, please use `GET /api/v2/margin/lend/market`
- Deprecate  `GET /api/v1/isolated/symbols`, please use  `GET  /api/v2/margin/symbols`
- Deprecate  `GET /api/v1/isolated/accounts`, please use `GET  /api/v2/isolated/accounts`
- Deprecate  `GET /api/v1/isolated/account/{symbol}`, please use `GET  /api/v2/isolated/accounts`
- Deprecate  `POST /api/v1/isolated/borrow`, please use `POST  /api/v2/margin/borrow`
- Deprecate  `GET /api/v1/isolated/borrow/outstanding`, please use `GET /api/v2/margin/repay`
- Deprecate  `GET /api/v1/isolated/borrow/repaid`, please use `GET /api/v2/margin/repay`
- Deprecate  `POST /api/v1/isolated/repay/all`, please use `POST  /api/v2/margin/repay/all`
- Deprecate  `POST /api/v1/isolated/repay/single`, please use `POST /api/v2/margin/repay/single`

**11/08/22**:

- Deprecate `POST /api/v1/accounts` interface

**11/01/22**:

- Add `chain` response field to `GET /api/v1/withdrawals` interface  and `GET /api/v1/deposits` interface
- Add `generalSubQuantity`, `marginSubQuantity`, `futuresSubQuantity`, `maxDefaultSubQuantity`, `maxGeneralSubQuantity`, `maxMarginSubQuantity` and `maxFuturesSubQuantity` fields to `POST /api/v1/sub/user` interface response
- Add `GET /api/v2/sub/user` and `GET /api/v2/sub-accounts` pagination interface

**10/20/22**:

- Deprecate `GET /api/v1/symbols` interface, please use `GET /api/v2/symbols` new interface instead

**09/22/22**:

- Add the `DELETE /api/v1/sub/api-key` interface related to sub-account
- Add the `time` field (milliseconds) to the Topic of `/market/level2`.

**08/24/22**:

- Add the following interfaces related to sub-account: `GET /api/v1/user-info`、`POST /api/v1/sub/user`、`GET /api/v1/sub/api-key`、`POST /api/v1/sub/api-key`、`POST /api/v1/sub/api-key/update`

**08/03/22**:

- Add `currencyType` request parameter to `GET /api/v1/base-fee` interface
- Add `feeDeductType` request parameter to `POST /api/v1/withdrawals` interface
- Add `chain` response parameter to `GET /api/v2/currencies/{currency}` interface

**07/05/22**:

- Added the following interfaces related to isolated margin: `GET /api/v1/isolated/symbols`、`GET /api/v1/isolated/accounts`、`GET /api/v1/isolated/account/{symbol}`、`POST /api/v1/isolated/borrow`、`GET /api/v1/isolated/borrow/outstanding`、`GET /api/v1/isolated/borrow/repaid`、`POST /api/v1/isolated/repay/all`、`POST /api/v1/isolated/repay/single`
- Modify the following interface to support isolated margin: `POST /api/v2/accounts/inner-transfer`、`GET /api/v1/accounts/transferable`、`POST /api/v1/margin/order`
- Check and revise the document description to improve the readability of the document

**01/25/22**:

- Add [Query the cross/isolated margin risk limit](#query-the-cross-isolated-margin-risk-limit) endpoint
- Deprecate [GET /api/v1/hist-orders](#get-v1-historical-orders-list-deprecated) endpoint

**12/23/21**:

- Deprecate the **pool** type for [List Accounts](#list-accounts).
- Deprecate the **pool** type for [Inner Transfer](#inner-transfer).
- Deprecate the **POOL** type for [Get the Transferable](#get-the-transferable).

**11/26/21**:

- Add [Get Currency Detail(Recommend)](#get-currency-detail-recommend) endpoint.
- Modify [List of currently supported symbol](#list-of-currently-supported-symbol) by Index Price and Mark Price for Margin.

**09/23/21**:

- Modify API KEY PERMISSIONS of the [Get Repay Record](#get-repay-record) and [Get Repayment Record](#get-repayment-record) endpoint, these endpoints requires the "General" permission

**08/18/21**:

- Check and revise the document description to improve the readability of the document

**08/09/21**:

- Modify the request parameter time range of  [Get Account Ledgers](#get-account-ledgers).

**07/15/21**:

- modify the strategy of [Request Rate Limit](#request-rate-limit).

**06/04/21**:

- Modify the query of the lifetime for the order by clientOid [Get Single Order by clientOid](#get-single-active-order-by-clientoid)
- Modify the timestamp to millisecond [Get an order](#get-an-order)

**04/26/21**:

- Add [Get Full Order Book(aggregated)](#get-full-order-book-aggregated),[Get Full Order Book(atomic)](#get-full-order-book-atomic) endpoints(V3 version), these endpoints requires the "General" permission
- Deprecate [Get Full Order Book(aggregated)](#get-full-order-book-aggregated-deprecated),[Get Full Order Book(atomic)](#get-full-order-book-atomic-deprecated) endpoints(V2 version)
- Add [Get Deposit Addresses(V2)](#get-deposit-addresses-v2)

**02/24/21**  

- Add [Place a margin order](#place-a-margin-order) 

**11/05/20**:

- Add [Trade Fee](#trade-fee) module，[Basic user fee](#basic-user-fee),[Actual fee rate of the trading pair](#actual-fee-rate-of-the-trading-pair)
- Add [Get Account Ledgers](#get-account-ledgers)，and deprecate [Get Account Ledgers(deprecated)](#get-account-ledgers-deprecated)

**10/28/20**:

- Add the Basic Taker Fee,Basic Maker Fee,Taker Fee Coefficient,Maker Fee Coefficient for [Get 24hr Stats](#get-24hr-stats),[Get All Tickers](#get-all-tickers).
- Add [Transfer between Master user and Sub-user](#transfer-between-master-user-and-sub-user) Added types of account that support transfer.
- Add [Inner Transfer](#inner-transfer) Added types of account that support transfer.
- Deprecate '/api/v1/accounts/sub-transfer' endpoint for [Transfer between Master user and Sub-user](#transfer-between-master-user-and-sub-user).
- Add REST API [Stop Order](#stop-order)
- Add websocket [Stop Order Event](#stop-order-event)，and deprecate [Stop Order Received Event](#stop-order-received-event), [Stop Order Activate Event](#stop-order-activate-event)


**08/12/20**:

- Add [Cancel Single Order by clientOid](#cancel-single-order-by-clientoid)；
- Add [Get Single Active Order by clientOid](#get-single-active-order-by-clientoid)；


**07/13/20**:

- Add [Private Order Change Events](#private-order-change-events)，[Full MatchEngine Data (revision) (Level 3)](#full-matchengine-data-revision-level-nbsp-3)，[Level2 - 5 best ask/bid orders](#level2-5-best-askbid-orders)，[Level2 - 50 best ask/bid orders](#level2-50-best-askbid-orders)；
- Add [Get Full Order Book(atomic)(revision)](#get-full-order-book-atomic-revision)；

**06/12/20**:

- Add channelType field: public(public channel, default), private(private channel), session(session channel) for Websocket.
- Deprecate ({topic}:privateChannel:{userId}) and userId in private messages after three months.

**05/28/20**:

- Add unique key for [Get Account Ledgers](#get-account-ledgers)

**04/22/20**:

- Deprecate [Get Holds](#get-holds) on 10th May 2020.
- Add the **relationContext** field for [Account Balance Notice](#account-balance-notice).
- Modify the default chain of USDT into ERC20.

**04/09/20**:

- Add the **pool** type for [List Accounts](#list-accounts).
- Add the **pool** type for [Inner Transfer](#inner-transfer).
- Add the **POOL** type for [Get the Transferable](#get-the-transferable).
- Deprecate the **balance** field for [Get Account Ledgers](#get-account-ledgers) and set **balance** 0 by default.

**03/27/20**:

- Add the request parameters: **bizType** and **direction** for [Get Account Ledgers](#get-account-ledgers)

**03/11/20**:

- Add [Service Status](#service-status).

**02/03/20**:

- Add [Place bulk orders](#place-bulk-orders).

**01/03/20**:

- Add the description of **postOnly** for [Place a new order](#place-a-new-order).


**27/02/20**:

- Add the **price protection mechanism** for [Place a new order](#place-a-new-order).


**02/01/20**:

- Add the **time** field to [Get Full Order Book(atomic)](#get-full-order-book(atomic)).
- Add **reason** field in the subscription for [Stop Order Activate Event](#stop-order-activate-event).

**10/20/19**:

- Deprecate '/api/v1/accounts/inner-transfer' endpoint for [Inner Transfer](#inner-transfer).
- Add the **margin** type for [List Accounts](#list-accounts).
- Support the margin account for [Get an Account](#get-an-account).
- Add the **margin** type for [Create an Account](#create-an-account).
- Add the extra bizType for margin via [Get Account Ledgers](#get-account-ledgers).
- Add the extra bizType for margin via [Get Holds](#get-holds)
- Add the margin account via [Get Account Balance of a Sub-Account](#get-account-balance-of-a-sub-account)
- Support the margin account for [Get the Aggregated Balance of all Sub-Accounts](#get-the-aggregated-balance-of-all-sub-accounts)
- Add the **MARGIN** type for [Transfer between Master user and Sub-user](#transfer-between-master-user-and-sub-user)
- Add the **margin** type for [Inner Transfer](#inner-transfer)
- Add [Get the Transferable](#get-the-transferable).
- Add [Place a new order](#place-a-new-order) **tradeType** field.
- Add [Cancel all orders](#cancel-all-orders) **tradeType** field.
- Add **tradeType** field for [List Orders](#list-orders), [Recent Orders](#recent-orders), [Get an order](#get-an-order).
- Add **tradeType** field for [List Fills](#list-fills), [Recent Fills](#recent-fills).
- Add [Get Symbols List](#get-symbols-list)**isMarginEnabled** field.
- Add [Get Currencies](#get-currencies) and [Get Currency Detail](#get-currency-detail) **isMarginEnabled**, **isDebitEnabled** field.
- Add [Margin Trade](#margin-trade) module.

**10/17/19**:

- Add the **remark** field to [Get Deposit List](#get-deposit-list) and [Get Withdrawals List](#get-withdrawals-list)

**10/12/19**:

- Merge [Get Market List](get-market-list) ETH、NEO、TRX three markets into ALTS.

**9/27/19**

- Add **symbolName** response to [Get All Tickers](#get-all-tickers).

**6/19/19**:

- Modify [Transfer between Master user and Sub-user](#transfer-between-master-user-and-sub-user)

**6/13/19**:

- Add [FAQ](#faq) for Open API.
- Add the advantage descriptions for [Level-3](#matchengine-data).

**5/28/19**:

- Modify [Get Market List](#Get-Market-List) SC changed to USDS.
- Add one new endpoint for [Inner Transfer](#inner-transfer), the original interface will expire after three months (8/28/19).
- Add the usage description to the favorite withdrawal address [Apply Withdraw](#apply-withdraw).
- Add **averagePrice** field to [Get 24hr Stats](#get-24hr-stats).


**5/8/19** :

- Add **chain** field to [Create Deposit Address](#create-deposit-address), [Get Deposit Address](#get-deposit-address), [Get Currency Detail](#get-currency-detail), [Get Withdrawal Quotas](#get-withdrawal-quotas) and [Apply Withdraw](#apply-withdraw).
-  Add the description of how to transfer assets in the [Inner Transfer](#inner-transfer) interface.
- Add **L3 SDK** to [Full MatchEngine Data(Level 3)](#full-matchengine-data(level-3)).
- modify the strategy of [Rate Limit](#request-rate-limit).

**4/24/19**:

- Delete the "size" and "funds" fields of the “received” message in the subscription for [Full MatchEngine Data(Level 3)](#full-matchengine-data(level-3)) via the public channels, therefore protecting the hidden orders. These fields in the private channels remain unchangeds.
- Delete the “remainSize” field of the “open” messages in the subscription for [Full MatchEngine Data(Level 3)](#full-matchengine-data(level-3)) via the public channels, therefore protecting the hidden orders. These fileds in the private channels remain unchanged.
- Add [Get User Info of all Sub-Accounts](#get-user-info-of-all-sub-accounts).
- Add [Get Account Balance of a Sub-Account](#get-account-balance-of-a-sub-account).
- Add [Get the Aggregated Balance of all Sub-Accounts of the Current User](#get-the-aggregated-balance-of-all-sub-accounts-of-the-current-user).
- Add [Transfer between Master account and Sub-Account](#transfer-between-master-account-and-sub-account).

**3/27/19** :

- Add **feeCurrency** field to [Get Symbols List](#get-symbols-list).

**3/25/19** :

- Add **volValue** field to [Get All Tickers](#get-all-tickers).
- Add **clientOid** field to [Full MatchEngine Data(Level 3)](#full-matchengine-data(level-3))which allows you to filter your order info by clientOid when you subscribe to the "received " messages through private channels.
- Add **accountId** field in the subscription for [Account balance notice](#account-balance-notice).

**3/13/19** :

- Modify the maximum matching orders for a single trading pair in one account is 200 (stop orders included).

**3/6/19** :

- Add **nanoseconds** as the time unit of the order system and matching engine.

**2/28/19** :

- Modify [Get Symbols List](#get-symbols-list) response description
- Add [Get V1 Historical Deposits List](#get-v1-historical-deposits-list)
- Add [Get V1 Historical Withdrawals List](#get-v1-historical-withdrawals-list)
- Add [Get V1 Historical Orders List](#get-v1-historical-orders-list)
- Add explanation to part of the API JSON field
- Delete "sn" field in [Match Execution Data](#match-execution-data)
- Modify [Get Fiat Price](#get-fiat-price) parameter description

**2/22/19** :

- Add **volValue** field to [Get 24hr Stats](#get-24hr-stats)

**2/21/19** :

- Add [Get Full Order Book(aggregated) v2](#get-full-order-book-aggregated)
- Add **time** field to Level-1,2,3 Data
- Add [Get Fiat Price](#get-fiat-price)

**2/20/19** :

- Add **time** field to [Get All Tickers](#get-all-tickers) and [Get Ticker](#get-ticker)

**2/19/19** :

- Add [Get All Tickers](#get-all-tickers)

**2/18/19** :

- Add [Recent Orders](#recent-orders)
- Add [Recent Fills](#recent-fills)

**2/16/19** :

- Add [All Symbols Ticker](#all-symbols-ticker)
- Modify [Permissions](#permissions)

**1/30/19** :

- Add SDK official provider [CCXT](#client-libraries)

**1/25/19** :

- Add [Get Market List](#get-market-list)
- Add [Symbol Snapshot Feed](#symbol-snapshot)
- Add [Market Snapshot Feed](#market-snapshot)
- Add official [Java & Go SDK](#client-libraries)

## Reading Guide

1. Read [Sandbox](#sandbox) to learn how to debug API in a test environment.
2. Read [REST API](#rest-api) to learn how to build a request.
3. Read [Time](#server-time) if you want to make a test request (and receive a sample response) without having to authorize.
4. Read [Service Status](#service-status) to maintain your trading strategy based on service status
5. Read [Authentication](#authentication) to learn how to make an authorized request.
6. Read [Inner Transfer](#inner-transfer) to see how to transfer assets.
7. Read [List Accounts](#list-accounts) to learn how to get the data of your account balance.
8. Read [Place a new order](/#place-a-new-order) to see how to place an order.
9. Read [Order Book](#get-part-order-book-aggregated) to get a snapshot of the order book.
10. Read [Websocket Feed](#websocket-feed) to learn how to establish a websocket connection.
11. Read [Level-2 Market Data](#level-2-market-data) to see how to build a local real-time order book with websocket.
12. Read [Account balance notice](#account-balance-notice) to see how to get a private websocket feed and get real time notice of balance changes.

## Sub-account

You can create a sub-account and its API key on the web end.

A sub-account can be used to separate the funds for crypto tradings and the funds can be transferred between the master account and the sub-account. Please note that the funds in sub-account is limited for sub-account crypto trading only and the funds cannot be withdrawn directly from the sub-account.

The API of a sub-account is available to access all the public endpoints. Besides this, traders can access the following private endpoints via the API key of a sub-account:


Endpoints | Description
---------- | -------
[List Accounts](#place-a-new-order) | Get the status of an account.
[Get an Account](#get-an-account) | Get the info of an account.
[Create an Account](#create-an-account) | Create an Account.
[Get Account Ledgers](#get-account-ledgers) | Get the funds details of an account.
[Get Holds](#get-holds) | Get the hold details of an account.
[Inner Transfer](#inner-transfer) | Transferring assets between the accounts of main and trade.
[Place a new order](#place-a-new-order) | Place an order.
[Cancel an order](#cancel-an-order) | Request to cancel an order.
[Cancel all orders](#cancel-all-orders) | Request to cancel all orders.
[List Orders](#list-orders) | Get orders details.
[Recent Orders](#recent-orders) | Get order details of the last 24 hours(up to 1000).
[Get an order](#get-an-order) | Get the details of a single order.
[List Fills](#list-fills) | Get the order execution details.
[Recent Fills](#recent-fills) | Get order execution details of the last 24 hours(up to 1000).
[Cancel Single Order by clientOid](#cancel-single-order-by-clientoid) | Cancel Single Order by clientOid.
[Get Single Active Order by clientOid](#get-single-active-order-by-clientoid) | Get Single Active Order by clientOid.

 A sub-account shares the same fee level as its master-account. (The fee level will be calculated based on the total transaction amount of the sub-account and the master account or the holding amount of KCS.)

The sub-account needs to transfer funds from the main account to the trade account before trading.

<aside class="notice">The withdrawal and deposit is not supported for sub-account.</aside>


## Matching Engine

### Order Lifecycle

Valid orders sent to the matching engine are confirmed immediately and are in the **received** state. If an order executes against another order immediately, the order is considered **done**. An order can execute in part or whole. Any part of the order not filled immediately, will be considered **open**. Orders will stay in the open state until canceled or subsequently filled by new orders. Orders that are no longer eligible for matching (filled or canceled) are in the **done** state.

### Self-Trade Prevention

**Self-Trade Prevention** is an option in advanced settings.It is not selected by default. If you specify STP when placing orders, your order won't be matched by another one which is also yours. On the contrary, if STP is not specified in advanced, your order can be matched by another one of your own orders. It should be noted that only the taker's protection strategy is effective.


#### DECREMENT AND CANCEL(DC)

**Market orders are currently not supported for DC**. When two orders from the same user cross, the smaller order will be canceled and the larger order will be decremented by the size of the smaller order. If the two orders are the same size, both will be canceled.

#### CANCEL OLDEST(CO)

Cancel the older (resting) order in full. The new order continues to execute.

#### CANCEL NEWEST(CN)

Cancel the newer (taking) order in full. The old resting order remains on the order book.

#### CANCEL BOTH(CB)

Immediately cancel both orders.



## Client Libraries

Client libraries can help you integrate with our API quickly.

**Official SDK of KuCoin**

- [Java SDK](https://github.com/Kucoin/KuCoin-Java-SDK)
- [PHP SDK](https://github.com/Kucoin/KuCoin-PHP-SDK)
- [Go SDK](https://github.com/Kucoin/KuCoin-Go-SDK)
- [Python SDK](https://github.com/Kucoin/kucoin-python-sdk)
- [Nodejs SDK](https://github.com/Kucoin/kucoin-node-sdk)


CCXT is our authorized SDK provider and you may access the KuCoin API through CCXT. For more information, please visit: [https://ccxt.trade](https://ccxt.trade).


**Examples**

- PHP File Example (GET & POST & DELETE)  [Github Link](https://github.com/Kucoin/kucoin-api-docs/tree/master/examples/php)

- - -

## Sandbox


**Sandbox is the test environment**, used for testing an API connection or web trading. It provides all the functionalities of the live exchange. All funds and transactions there are simulated for testing purposes.

The login session and the API key in the sandbox environment are completely separated from the production environment. You may use the web interface in the sandbox environment to create an API key.

Notice: After registering in the sandbox environment, you will receive a nummber amount of fake funds (BTC, ETH or KCS) automatically released by the system in your account. If you want to **trade**, please transfer assets from the  **main**  account to the  **trade** account. The funds are only for test purposes and cannot be withdrawn.


Sandbox URLs for API test:

Website:
**[https://sandbox.kucoin.com](https://sandbox.kucoin.com)**

REST API:
**https://openapi-sandbox.kucoin.com**


## Request Rate Limit

When a rate limit is exceeded, a status of **429** will be returned.
<aside class="notice">Once the rate limit is exceeded, the system will restrict your use of your IP or account for 10s.</aside>

###REST API

The limit strategy of private endpoints will restrict account by userid. The limit strategy of public endpoints will restrict IP.
<aside class="notice">Note that when an API has a specific rate limit, please refer to the specific limit.</aside>

###WEBSOCKET


### Number of Connections
Number of connections per user ID:   ≤ 50

### Connection Times
Connection Limit: 30 per minute


### Number of Uplink Messages
Message limit sent to the server: 100 per 10 seconds


### Topic Subscription Limit
Maximum number of batch subscriptions at a time: 100 topics

Subscription limit for each connection: 300 topics



### Apply for Higher Request Rate Limit
If you are a professional trader or market maker and need a higher limit, please send your KuCoin account, reason and approximate trading volume to [api@kucoin.com](mailto:api@kucoin.com).


## Market Making Incentive Scheme

KuCoin offers a Market Making Incentive Scheme for professional liquidity providers. Key benefits of this program include:

- Market Maker rebate.
- Monthly rewards up to 30,000 KCS for the market maker with the best performance.
- Direct Market Access and Co-location service.

Users with good maker strategies and huge trading volume are welcome to participate in this long-term program. If your account has a trading volume of more than 5000 BTC in the last 30 days on any exchange, please send the following information via email to **mm@kucoin.com**, with subject "Spot Market Maker Application":

- One KuCoin account ID (a non-referred account is required).
- Proof of volume traded on any exchange within the past 30 days. Proof of a VIP level is also acceptable.
- A brief explanation of your market making method (NO detail is needed), as well as estimation of maker orders’ percentage.

## VIP Fast Track

KuCoin now provides a VIP fast track to users with a large trading volume in crypto. If your accounts on different platforms have a total trading volume of more than 1000 BTC in the last 30 days, please send the following information via email to **vip@kucoin.com**, with subject "VIP Fast Track Application":

KuCoin account ID.
Proof of trading volume on other platforms within the past 30 days. Proof of a VIP level is also acceptable.

We will offer you a jumpstart (e.g. a VIP level which matches your volume on other exchanges even though you are not trading as much on KuCoin) for 30 days. After 30 days, your VIP level will be calculated based on your actual trading volume on KuCoin.


## FAQ

### Invalid Signature


* Check if your API-KEY, API-SECRET and API-PASSPHRASE are correct
* Check if the string sequence is correct: timestamp + method + requestEndpoint + body
* Check whether the timestamp in header is the same with the content above
* Check whether you are using the correct encoding in your signature, e.g. base64
* Check whether the **GET** request is submitted as a form
* Check whether the content-type of your POST request is in application/json form and is encoded by charset=utf-8

### Apply Withdraw
* memo


For currencies without memo, the memo field is not required. Please do not pass the parameter when you are applying to withdraw via API, or the system will return: **kucoin incorrect withdrawal address**.<br/>

* amount


The precision of the **amount** field shall satisfy the withdrawal precision requirements of the currency. The precision requirements for the currencies can be obtained by [Withdrawals Quotas](#get-withdrawal-quotas).
The withdrawal amount must be an integer multiple of the withdrawal accuracy. If the withdrawal accuracy is 0, the withdrawal amount it can only be an integer.


### .net SDK
* Invalid Signature on POST Request

{"code":"400005", "msg":"Invalid KC-API-SIGN"}<br/>
There is a bug in the code:<br/>
 var response = body == null ? await _restRepo.PostApi<ApiResponse<T>, SortedDictionary<string, object>>(url, body, headers) : await _restRepo.PostApi<ApiResponse<T>>(url, headers);<br/>
After fixing:<br/>
 var response = body != null ? await _restRepo.PostApi<ApiResponse<T>, SortedDictionary<string, object>>(url, body, headers) : await _restRepo.PostApi<ApiResponse<T>>(url, headers);

### WebSocket
* Subscription limit for each connection: 300 topics;
* Validity period for token: 24 hours;
* Number of connections per user: ≤ 50
* Number of Messages of the client side: 100 per 10 seconds;
* Subscribing one symbol means subscribing a topic; (e.g.Topic: /market/level2:{symbol},{symbol}...)

### 403  Error

If an error occurs as follows:
403 "The request could not be satisfied. Bad Request" from Amazon CloudFront<br/>

* Check whether the request is HTTPS
* Remove the RequestBody from the GET request





# REST API

## Base URL

The REST API has endpoints for account and order management as well as public market data.

The base url is **https://api.kucoin.com**.  

The request URL needs to be determined by BASE and specific endpoint combination.

## Endpoint of the Interface


Each interface has its own endpoint, described by field **HTTP REQUEST** in the docs.

For the **GET METHOD** API, the endpoint needs to contain the query parameters string.

E.G. For "List Accounts", the default endpoint of this API is **/api/v1/accounts**. If you pass the "currency" parameter(BTC), the endpoint will become **/api/v1/accounts?currency=BTC** and the final request URL will be **https://api.kucoin.com/api/v1/accounts?currency=BTC**.


## Request
All requests and responses are **application/json** content type.  

Unless otherwise stated, all timestamp parameters should in milliseconds. e.g. **1544657947759**

### PARAMETERS

For the **GET, DELETE** request, all query parameters need to be included in the request url. (**e.g. /api/v1/accounts?currency=BTC**)

For the **POST, PUT** request, all query parameters need to be included in the request body with JSON. (**e.g. {"currency":"BTC"}**). **Do not include extra spaces in JSON strings.**

### Errors

When errors occur, the HTTP error code or system error code will be returned. The body will also contain a message parameter indicating the cause.

#### HTTP error status codes

```
{
  "code": "400100",
  "msg": "Invalid Parameter."
}

```

Code | Meaning
---------- | -------
400 | Bad Request -- Invalid request format.
401 | Unauthorized -- Invalid API Key.
403 | Forbidden or Too Many Requests -- The request is forbidden or Access limit breached.
404 | Not Found -- The specified resource could not be found.
405 | Method Not Allowed -- You tried to access the resource with an invalid method.
415 | Unsupported Media Type. You need to use: application/json.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.


#### System error codes

| Code | Meaning |
| ---------- | ------- |
| 200001 | Order creation for this pair suspended       |
| 200002 | Order cancel for this pair suspended     |
| 200003 | Number of orders breached the limit      |
| 200009 | Please complete the KYC verification before you trade XX |
| 200004 | Balance insufficient                           |
| 400001 | Any of KC-API-KEY, KC-API-SIGN, KC-API-TIMESTAMP, KC-API-PASSPHRASE is missing in your request header |
| 400002 | KC-API-TIMESTAMP Invalid      |
| 400003 | KC-API-KEY not exists                      |
| 400004 | KC-API-PASSPHRASE error             |
| 400005 | Signature error     |
| 400006 | The requested ip address is not in the api whitelist |
| 400007 | Access Denied        |
| 404000 | Url Not Found                              |
| 400100 | Parameter Error                            |
| 400200 | Forbidden to place an order              |
| 400500 | Your located country/region is currently not supported for the trading of this token |
| 400700 | Transaction restricted, there's a risk problem in your account |
| 400800 | Leverage order failed                          |
| 411100 | User are frozen |
| 500000 | Internal Server Error              |
| 900001 | symbol not exists                              |

If the returned HTTP status code is 200, whereas the operation failed, an error will occur. You can check the above error code for details.

### Success

A successful response is indicated by an HTTP status code 200 and system code 200000. The success response is as follows:


```json
{
  "code": "200000",
  "data": "1544657947759"
}
```



### Pagination

Pagination allows for fetching results with the current page and is well suited for real time data. Endpoints like /api/v1/deposits, /api/v1/orders, /api/v1/fills, will return the latest items by default (50 pages in total). To retrieve more results, users should specify the currentPage number in the subsequent requests to turn the page based on the data previously returned.

#### PARAMETERS

Parameter | Default | Description
---------- | ------- | ------
currentPage | 1 | Current request page.
pageSize | 50 | Number of results per request. Minimum is 10, maximum is 500. 


#### Example
`GET /api/v1/orders?currentPage=1&pageSize=50`


## Types

### Timestamps

Unless otherwise specified, all timestamps from API are returned in **milliseconds**(e.g. **1546658861000**). Most modern languages and libraries will handle this without issues.

But please note that the timestamps between the **matching engine** and the **order** system are in nanoseconds.

### Numbers
Decimal numbers are returned as strings in order to preserve the full precision across platforms. When making a request, it is recommended that you also convert your numbers to strings to avoid truncation and precision errors.

## Authentication

### Generating an API Key

Before being able to sign any requests, you must create an API key via the KuCoin website. Upon creating a key you need to write down 3 pieces of information:


* Key
* Secret
* Passphrase

The Key and Secret are generated and provided by KuCoin and the Passphrase refers to the one you used to create the KuCoin API. Please note that these three pieces of information can not be recovered once lost. If you lost this information, please create a new API KEY.

### API KEY PERMISSIONS

You can manage the API permission on KuCoin’s official website. The permissions are:


* **General** - General - Allows a key general permissions. This includes most of the GET endpoints.
* **Trade** -  Allows a key to create orders.
* **Transfer** -  Allows a key to transfer funds (including deposit and withdrawal). Please note a sub-account is not authorized this permission. Enable with caution - API key transfers WILL BYPASS two-factor authentication.


Please refer to the documentation below to see what API key permissions are required for a specific route.

### Creating a Request

All private REST requests must contain the following headers:

* **KC-API-KEY** The API key as a string.
* **KC-API-SIGN** The base64-encoded signature (see Signing a Message).
* **KC-API-TIMESTAMP** A timestamp for your request.
* **KC-API-PASSPHRASE** The passphrase you specified when creating the API key.
* **KC-API-KEY-VERSION** You can check the version of API key on the page of [API Management](https://www.kucoin.com/account/api)

### Signing a Message

```php
    <?php
    class API {
        public function __construct($key, $secret, $passphrase) {
          $this->key = $key;
          $this->secret = $secret;
          $this->passphrase = $passphrase;
        }

        public function signature($request_path = '', $body = '', $timestamp = false, $method = 'GET') {

          $body = is_array($body) ? json_encode($body) : $body; // Body must be in json format

          $timestamp = $timestamp ? $timestamp : time() * 1000;

          $what = $timestamp . $method . $request_path . $body;

          return base64_encode(hash_hmac("sha256", $what, $this->secret, true));
        }
    }
    ?>
```

```python
    #Example for get balance of accounts in python

    api_key = "api_key"
    api_secret = "api_secret"
    api_passphrase = "api_passphrase"
    url = 'https://openapi-sandbox.kucoin.com/api/v1/accounts'
    now = int(time.time() * 1000)
    str_to_sign = str(now) + 'GET' + '/api/v1/accounts'
    signature = base64.b64encode(
        hmac.new(api_secret.encode('utf-8'), str_to_sign.encode('utf-8'), hashlib.sha256).digest())
    passphrase = base64.b64encode(hmac.new(api_secret.encode('utf-8'), api_passphrase.encode('utf-8'), hashlib.sha256).digest())
    headers = {
        "KC-API-SIGN": signature,
        "KC-API-TIMESTAMP": str(now),
        "KC-API-KEY": api_key,
        "KC-API-PASSPHRASE": passphrase,
        "KC-API-KEY-VERSION": "2"
    }
    response = requests.request('get', url, headers=headers)
    print(response.status_code)
    print(response.json())

    #Example for create deposit addresses in python
    url = 'https://openapi-sandbox.kucoin.com/api/v1/deposit-addresses'
    now = int(time.time() * 1000)
    data = {"currency": "BTC"}
    data_json = json.dumps(data)
    str_to_sign = str(now) + 'POST' + '/api/v1/deposit-addresses' + data_json
    signature = base64.b64encode(
        hmac.new(api_secret.encode('utf-8'), str_to_sign.encode('utf-8'), hashlib.sha256).digest())
    passphrase = base64.b64encode(
        hmac.new(api_secret.encode('utf-8'), api_passphrase.encode('utf-8'), hashlib.sha256).digest())
    headers = {
        "KC-API-SIGN": signature,
        "KC-API-TIMESTAMP": str(now),
        "KC-API-KEY": api_key,
        "KC-API-PASSPHRASE": passphrase,
        "KC-API-KEY-VERSION": 2
        "Content-Type": "application/json" # specifying content type or using json=data in request
    }
    response = requests.request('post', url, headers=headers, data=data_json)
    print(response.status_code)
    print(response.json())
```

For the header of **KC-API-SIGN**:

* Use API-Secret to encrypt the prehash string {timestamp+method+endpoint+body} with sha256 HMAC. The request body is a JSON string and need to be the same with the parameters passed by the API.
* After that, use base64-encode to encrypt the result in step 1 again.

For the **KC-API-PASSPHRASE** of the header:

* For API key-V1.0, please pass requests in plaintext.
* For API key-V2.0, please Specify **KC-API-KEY-VERSION** as **2** --> Encrypt passphrase with HMAC-sha256 via API-Secret --> Encode contents by base64 before you pass the request."

Notice:

* The encrypted timestamp shall be consistent with the KC-API-TIMESTAMP field in the request header.
* The body to be encrypted shall be consistent with the content of the Request Body.  
* The Method should be UPPER CASE.
* For GET, DELETE request, the endpoint needs to contain the query string. e.g. /api/v1/deposit-addresses?currency=XBT. The body is "" if there is no request body (typically for GET requests).



```python
#Example for Create Deposit Address

curl -H "Content-Type:application/json" -H "KC-API-KEY:5c2db93503aa674c74a31734" -H "KC-API-TIMESTAMP:1547015186532" -H "KC-API-PASSPHRASE:QWIxMjM0NTY3OCkoKiZeJSQjQA==" -H "KC-API-SIGN:7QP/oM0ykidMdrfNEUmng8eZjg/ZvPafjIqmxiVfYu4=" -H "KC-API-KEY-VERSION:2"
-X POST -d '{"currency":"BTC"}' http://openapi-v2.kucoin.com/api/v1/deposit-addresses

KC-API-KEY = 5c2db93503aa674c74a31734
KC-API-SECRET = f03a5284-5c39-4aaa-9b20-dea10bdcf8e3
KC-API-PASSPHRASE = QWIxMjM0NTY3OCkoKiZeJSQjQA==
KC-API-KEY-VERSION = 2
TIMESTAMP = 1547015186532
METHOD = POST
ENDPOINT = /api/v1/deposit-addresses
STRING-TO-SIGN = 1547015186532POST/api/v1/deposit-addresses{"currency":"BTC"}
KC-API-SIGN = 7QP/oM0ykidMdrfNEUmng8eZjg/ZvPafjIqmxiVfYu4=
```

<aside class="spacer16"></aside>
<aside class="spacer8"></aside>

### Selecting a Timestamp

The **KC-API-TIMESTAMP** header MUST be number of **milliseconds** since Unix Epoch in UTC. e.g. 1547015186532

Decimal values are allowed, e.g. 1547015186532. But you need to be aware that timestamp between match and order is **nanosecond**.

The difference between your timestamp and the API service time must be less than **5 seconds** , or your request will be considered expired and rejected. We recommend using the time endpoint to query for the API [server time](#server-time) if you believe there may be time skew between your server and the API server.




# User
Signature is required for this part.


# User Info

## Get User Info of all Sub-Accounts
```json
[{
		"userId": "5cbd31ab9c93e9280cd36a0a",  //subUserId
		"subName": "kucoin1",
		"type": 0,  //type:0-nomal
		"remarks": "kucoin1"
	},
	{
		"userId": "5cbd31b89c93e9280cd36a0d",
		"subName": "kucoin2",
		"type": 1,  //type:1-rebot
		"remarks": "kucoin2"
	}
]
```
You can get the user info of all sub-users via this interface.
<aside class="notice">It is recommended to use the <code>GET /api/v2/sub/user</code> interface for paging query</aside>


### HTTP REQUEST
`GET /api/v1/sub/user`
### Example
`GET /api/v1/sub/user`
### API KEY PERMISSIONS
This endpoint requires the `General` permission.
### PARAMETERS
`N/A`
### RESPONSES
Field | Description
--------- | -------
userId | The user ID of your sub-account
subName | The username of your sub-account
type | The type of your sub-account
remarks | Remark

## Get Paginated List of Sub-Accounts
```json
{
    "code":"200000",
    "data":{
        "currentPage":1,
        "pageSize":100,
        "totalNum":1,
        "totalPage":1,
        "items":[
            {
                "userId":"635002438793b80001dcc8b3",
                "uid":62356,
                "subName":"margin01",
                "status":2,
                "type":4,
                "access":"Margin",
                "createdAt":1666187844000,
                "remarks":null
            }
        ]
    }
}
```
This endpoint can be used to get a paginated list of sub-accounts. Pagination is required.
### HTTP REQUEST
`GET /api/v2/sub/user`
### Example
`GET /api/v2/sub/user`
### API KEY PERMISSIONS
This endpoint requires the `General` permission.
### PARAMETERS
Param | Type | Mandatory | Description
--------- | ------- | ------- | -------
currentPage | Int | No | Current request page. Default is `1`
pageSize  | Int  | No | Number of results per request. Minimum is `1`, maximum is `100`, default is `10`.
### RESPONSES
Field | Description
--------- | -------
createdAt |  Time of the event
remarks  | Remarks
status | Account status
subName | Sub-account name
type  | The type of your sub-account
uid  | Sub-account UID
userId | The user ID of your sub-account
access | Permission


# Account

## List Accounts
```json
[
  {
    "id": "5bd6e9286d99522a52e458de",  //accountId
    "currency": "BTC",  //Currency
    "type": "main",     //Account type, including main and trade
    "balance": "237582.04299",  //Total assets of a currency
    "available": "237582.032",  //Available assets of a currency
    "holds": "0.01099" //Hold assets of a currency
  },
  {
    "id": "5bd6e9216d99522a52e458d6",
    "currency": "BTC",
    "type": "trade",
    "balance": "1234356",
    "available": "1234356",
    "holds": "0"
}]

```
Get a list of accounts.

Please deposit funds to the main account firstly, then transfer the funds to the trade account via [Inner Transfer](#inner-transfer) before transaction.

### HTTP REQUEST
`GET /api/v1/accounts`

### Example
`GET /api/v1/accounts`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### PARAMETERS
Param | Type | Description
--------- | ------- | -------
currency | String | *[Optional]* [Currency](#get-currencies)
type | String | *[Optional]* Account type: **main**, **trade**, **margin**

### RESPONSES
Field | Description
--------- | -------
id | The ID of the account
currency | Currency
type | Account type: **main**, **trade**, **margin**
balance | Total funds in the account
available | Funds available to withdraw or trade
holds | Funds on hold (not available for use)

### ACCOUNT TYPE
There are three types of accounts: 1) **main** account 2) **trade** account 3) **margin** account.

No fees will be charged for the funds transfer between these account.

The main account is used for the storage, withdrawal, and deposit of the funds. The assets in the main account cannot be directly used for trading. To trade cryptos, you need to transfer funds from the main account to the trade account.

The trading account is used for transaction. When you place an order, the system will use the balance of the  trade account. You can’t withdraw funds directly from a trade account. To withdraw the funds, you need to transfer the funds from the trade account to the main account firstly.

The margin account is used to borrow assets and leverage transactions.

### FUNDS ON HOLD
When placing an order, the funds for the order will be freezed. The freezed funds cannot be used for other order placement or withdrawal and will remain on hold until the order is filled or cancelled.



## Get an Account
```json
{
    "currency": "KCS",  //Currency
    "balance": "1000000060.6299",  //Total assets of a currency
    "available": "1000000060.6299",  //Available assets of a currency
    "holds": "0" //Hold assets of a currency
}
```
Information for a single account. Use this endpoint when you know the accountId.

### HTTP REQUEST
`GET /api/v1/accounts/{accountId}`

### Example
`GET /api/v1/accounts/5bd6e9286d99522a52e458de`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.


### PARAMETERS
Param | Type | Description
--------- | ------- | ---------
accountId | String | **Path parameter.** ID of the account

### RESPONSES
Field | Description
--------- | -------
currency | The currency of the account
balance | Total funds in the account
holds | Funds on hold (not available for use)
available | Funds available to withdraw or trade

## Get Account Ledgers

This interface is for the history of deposit/withdrawal of all accounts, supporting inquiry of various currencies. 

Items are paginated and sorted to show the latest first. See the [Pagination](#pagination) section for retrieving additional entries after the first page.

```json
{
  "currentPage": 1,
  "pageSize": 50,
  "totalNum": 2,
  "totalPage": 1,
  "items": [
    {
      "id": "611a1e7c6a053300067a88d9",//unique key
      "currency": "USDT", //Currency
      "amount": "10.00059547", //Change amount of the funds
      "fee": "0", //Deposit or withdrawal fee
      "balance": "0", //Total assets of a currency
      "accountType": "MAIN", //Account Type
      "bizType": "Loans Repaid", //business type
      "direction": "in", //side, in or out
      "createdAt": 1629101692950, //Creation time
      "context": "{\"borrowerUserId\":\"601ad03e50dc810006d242ea\",\"loanRepayDetailNo\":\"611a1e7cc913d000066cf7ec\"}" //Business core parameters
    },
    {
      "id": "611a18bc6a0533000671e1bf",
      "currency": "USDT",
      "amount": "10.00059547",
      "fee": "0",
      "balance": "0",
      "accountType": "MAIN",
      "bizType": "Loans Repaid",
      "direction": "in",
      "createdAt": 1629100220843,
      "context": "{\"borrowerUserId\":\"5e3f4623dbf52d000800292f\",\"loanRepayDetailNo\":\"611a18bc7255c200063ea545\"}"
    }
  ]
}
```

### HTTP REQUEST
`GET /api/v1/accounts/ledgers`

### Example
`GET /api/v1/accounts/ledgers?currency=BTC&startAt=1601395200000`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is **18 times/3s**.

<aside class="notice">This request is paginated.</aside>


### PARAMETERS
Param | Type | Description
--------- | ------- | -------
currency | String | *[Optional]* Currency ( you can choose more than one currency). You can specify 10 currencies at most for one time. If not specified, all currencies will be inquired by default.
direction | String | *[Optional]*  Side: **in** - Receive, **out** - Send
bizType   | String | *[Optional]*  Business type: **DEPOSIT**, **WITHDRAW**, **TRANSFER**, **SUB_TRANSFER**,**TRADE_EXCHANGE**, **MARGIN_EXCHANGE**, **KUCOIN_BONUS**.
startAt| long | *[Optional]*  Start time (milisecond)
endAt| long | *[Optional]* End time (milisecond)

<aside class="notice">the start and end time range cannot exceed 24 hours. An error will occur if the specified time window exceeds the range. If you specify the end time only, the system will automatically calculate the start time as end time minus 24 hours, and vice versa.</aside>
<aside class="notice">Support to obtain 1 year historical data, if need to obtain longer historical data, please submit a ticket: https://kucoin.zendesk.com/hc/en-us/requests/new</aside>

### RESPONSES
Field | Description
--------- | -------
id | unique key
currency | The currency of an account
amount | The total amount of assets (fees included) involved in assets changes such as transaction, withdrawal and bonus distribution.
fee | Fees generated in transaction, withdrawal, etc.
balance | Remaining funds after the transaction.
accountType | The account type of the master user: MAIN, TRADE, MARGIN or CONTRACT.
bizType | Business type leading to the changes in funds, such as exchange, withdrawal, deposit,  KUCOIN_BONUS, REFERRAL_BONUS, Lendings etc.
direction | Side, **out** or **in**
createdAt | Time of the event
context | Business related information such as order ID, serial No., etc.

### context
If the returned value under bizType is **“trade exchange”**, the additional info. (such as order ID and trade ID, trading pair, etc.) of the trade will be returned in field **context**.

### BizType Description
Field | Description
--------- | -------
Assets Transferred in After Upgrading | Assets Transferred in After V1 to V2 Upgrading
Deposit  | Deposit 
Withdrawal  | Withdrawal
Transfer | Transfer
Trade_Exchange | Trade
Vote for Coin | Vote for Coin
KuCoin Bonus | KuCoin Bonus
Referral Bonus | Referral Bonus
Rewards | Activities Rewards
Distribution  | Distribution, such as get GAS by holding NEO
Airdrop/Fork  | Airdrop/Fork
Other rewards | Other rewards, except Vote, Airdrop, Fork
Fee Rebate | Fee Rebate
Buy Crypto | Use credit card to buy crypto
Sell Crypto | Use credit card to sell crypto
Public Offering Purchase | Public Offering Purchase for Spotlight
Send red envelope | Send red envelope
Open red envelope  | Open red envelope
Staking  | Staking 
LockDrop Vesting | LockDrop Vesting
Staking Profits | Staking Profits
Redemption | Redemption
Refunded Fees | Refunded Fees
KCS Pay Fees | KCS Pay Fees
Margin Trade | Margin Trade
Loans   | Loans
Borrowings  | Borrowings
Debt Repayment   | Debt Repayment
Loans Repaid  | Loans Repaid
Lendings  | Lendings
Pool transactions  | Pool-X transactions
Instant Exchange  | Instant Exchange
Sub-account transfer  | Sub-account transfer
Liquidation Fees   | Liquidation Fees 
Soft Staking Profits  | Soft Staking Profits
Voting Earnings  | Voting Earnings on Pool-X
Redemption of Voting  | Redemption of Voting on Pool-X
Convert to KCS   | Convert to KCS 

## Get Account Summary Information
```json
{
    "code": "200000",
    "data": {
        "level": 0,
        "subQuantity": 11,
        "subQuantityByType": {
            "generalSubQuantity": 9,
            "marginSubQuantity": 1,
            "futuresSubQuantity": 1
        },
        "maxSubQuantity": 35,
        "maxSubQuantityByType": {
            "maxDefaultSubQuantity": 5,
            "maxGeneralSubQuantity": 10,
            "maxMarginSubQuantity": 10,
            "maxFuturesSubQuantity": 10
        }
    }
}
```
This endpoint can be used to obtain account summary information.

### HTTP REQUEST
`GET /api/v1/user-info`

### Example
`GET /api/v1/user-info`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### PARAMETERS
`N/A`

### RESPONSES
Field | Description
--------- | -------
level | User level
subQuantity | Number of sub-accounts
generalSubQuantity | General sub-account opened quantity
marginSubQuantity | Margin sub-account opened quantity
futuresSubQuantity |  Futures sub-account opened quantity
maxSubQuantity| Max number of sub-accounts
maxDefaultSubQuantity | Max number of default open sub-accounts
maxGeneralSubQuantity | Max number of General sub-accounts
maxMarginSubQuantity | Max number of Margin sub-account
maxFuturesSubQuantity | Max number of Futures sub-account

## Create Sub-Account
```json
{
    "code": "200000",
    "data": {
        "uid": 9969082973,
        "subName": "AAAAAAAAAA0007",
        "remarks": "remark",
        "access": "All"
    }
}
```
This endpoint can be used to create sub-accounts.

### HTTP REQUEST
`POST /api/v1/sub/user`

### Example
`POST /api/v1/sub/user`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### PARAMETERS
Param | Type | Mandatory | Description
--------- | ------- | ------- | -------
password | String | Yes | Password(7-24 characters, must contain letters and numbers, cannot only contain numbers or include special characters)
remarks | String | No | Remarks(1~24 characters)
subName | String | Yes | Sub-account name(must contain 7-32 characters, at least one number and one letter. Cannot contain any spaces.)
access | String | No | Permission (This can only be set to `All`, `Futures`, or `Margin`, default is `All`. `All`: unrestricted; `Futures`: cannot use margin features; `Margin`: cannot use futures features.)

### RESPONSES
Field | Description
--------- | -------
remarks | Remarks
subName | Sub-account name
uid | Sub-account UID
access | Permission

## Get Sub-Account Spot API List
```json
{
    "code": "200000",
    "data": [
        {
            "subName": "AAAAAAAAAAAAA0022",
            "remark": "hytest01-01",
            "apiKey": "63032453e75087000182982b",
            "permission": "General",
            "ipWhitelist": "",
            "createdAt": 1661150291000
        }
    ]
}
```
This endpoint can be used to obtain a list of Spot APIs pertaining to a sub-account.

### HTTP REQUEST
`GET /api/v1/sub/api-key`

### Example
`GET /api/v1/sub/api-key`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### PARAMETERS
Param | Type | Mandatory | Description
--------- | ------- | ------- | -------
apiKey | String | No | API-Key.
subName | String | Yes | Sub-account name.

### RESPONSES
Field | Description
--------- | -------
apiKey | API-Key
createdAt | Time of the event
ipWhitelist | IP whitelist
permission | Permissions
remark | Remarks
subName | Sub-account name


## Create Spot APIs for Sub-Account
```json
{
    "code": "200000",
    "data": {
        "subName": "AAAAAAAAAA0007",
        "remark": "remark",
        "apiKey": "630325e0e750870001829864",
        "apiSecret": "110f31fc-61c5-4baf-a29f-3f19a62bbf5d",
        "passphrase": "passphrase",
        "permission": "General",
        "ipWhitelist": "",
        "createdAt": 1661150688000
    }
}
```
This endpoint can be used to create Spot APIs for sub-accounts.

### HTTP REQUEST
`POST /api/v1/sub/api-key`

### Example
`POST /api/v1/sub/api-key`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### PARAMETERS
Param | Type | Mandatory | Description
--------- | ------- | ------- | -------
subName | String | Yes | Sub-account name, create sub account name of API Key.
passphrase | String | Yes | Password(Must contain 7-32 characters. Cannot contain any spaces.)
remark | String | Yes | Remarks(1~24 characters)
permission | String | No | Permissions(Only "General" and "Trade" permissions can be set, such as "General, Trade". The default is "General")
ipWhitelist | String | No | IP whitelist(You may add up to 20 IPs. Use a halfwidth comma to each IP)
expire | String | No | API expiration time; Never expire(default)`-1`，30Day`30`，90Day`90`，180Day`180`，360Day`360`

### RESPONSES
Field | Description
--------- | -------
apiKey | API-Key
createdAt | Time of the event
ipWhitelist | IP whitelist
permission | Permissions
remark | Remarks
subName  | Sub-account name
apiSecret | API secret
passphrase | Password

## Modify Sub-Account Spot APIs
```json
{
    "code": "200000",
    "data": {
        "subName": "AAAAAAAAAA0007",
        "apiKey": "630329b4e7508700018298c5",
        "permission": "General",
        "ipWhitelist": "127.0.0.1",
    }
}
```
This endpoint can be used to modify sub-account Spot APIs.

### HTTP REQUEST
`POST /api/v1/sub/api-key/update`

### Example
`POST /api/v1/sub/api-key/update`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### PARAMETERS
Param | Type | Mandatory | Description
--------- | ------- | ------- | -------
subName | String | Yes | Sub-account name
apiKey | String | Yes | API-Key(Sub-account APIKey)
passphrase | String | Yes | Password of API key
permission | String | No | Permission list.If modified, permissions will be reset.
ipWhitelist | String | No | IP whitelist(you may add up to 20 IPs. Use a halfwidth comma to each IP.If modified, the IP will be reset.)
expire | String | No | API expiration time; Never expire(default)`-1`，30Day`30`，90Day`90`，180Day`180`，360Day`360`

### RESPONSES
Field | Description
--------- | -------
apiKey | API-Key
ipWhitelist | IP whitelist
permission | Permissions
subName | Sub-account name

## Delete Sub-Account Spot APIs
```json
{
 "code": "200000",
 "data": {
   "subName": "AAAAAAAAAA0007",
   "apiKey": "630325e0e750870001829864"
 }
}
```
This endpoint can be used to delete sub-account Spot APIs.

### HTTP REQUEST
`DELETE /api/v1/sub/api-key`

### Example
`DELETE /api/v1/sub/api-key`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### PARAMETERS
Param | Type | Mandatory | Description
--------- | ------- | ------- | -------
apiKey | String | Yes | API-Key(API key to be deleted)
passphrase | String | Yes | Password(Password of the API key)
subName | String | Yes | Sub-account name(The sub-account name corresponding to the API key)

### RESPONSES
Field | Description
--------- | -------
apiKey | API-Key
subName | Sub-account name

## Get Account Balance of a Sub-Account
```json
{
    "subUserId":"5caefba7d9575a0688f83c45",
    "subName":"sdfgsdfgsfd",
    "mainAccounts":[
        {
            "currency":"BTC",
            "balance":"8",
            "available":"8",
            "holds":"0",
            "baseCurrency":"BTC",
            "baseCurrencyPrice":"1",
            "baseAmount":"1.1"
        }
    ],
    "tradeAccounts":[
        {
            "currency":"BTC",
            "balance":"1000",
            "available":"1000",
            "holds":"0",
            "baseCurrency":"BTC",
            "baseCurrencyPrice":"1",
            "baseAmount":"1.1"
        }
    ],
    "marginAccounts":[
        {
            "currency":"BTC",
            "balance":"1.1",
            "available":"1.1",
            "holds":"0",
            "baseCurrency":"BTC",
            "baseCurrencyPrice":"1",
            "baseAmount":"1.1"
        }
    ]
}
```

This endpoint returns the account info of a sub-user specified by the subUserId.

### HTTP REQUEST
`GET /api/v1/sub-accounts/{subUserId}`

### Example
`GET /api/v1/sub-accounts/5caefba7d9575a0688f83c45?includeBaseAmount=false`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### PARAMETERS
Param | Type | Description
--------- | ------- | -------
subUserId | String | the [user ID](#get-user-info-of-all-sub-accounts) of a sub-account.
includeBaseAmount | boolean | false: do not display the currency which asset is 0, true: display all currency


### RESPONSES
Field | Description
--------- | -------
subUserId | The user ID of a sub-user.
subName | The username of a sub-user.
currency | Currency
balance | Total funds in an account.
available | Funds available to withdraw or trade.
holds | Funds on hold (not available for use).
baseCurrency | Calculated on this currency.
baseCurrencyPrice | The base currency price.
baseAmount | The base currency amount.


## Get the Aggregated Balance of all Sub-Accounts
```json
[
    {
        "subUserId":"5caefba7d9575a0688f83c45",
        "subName":"kucoin1",
        "mainAccounts":[
            {
                "currency":"BTC",
                "balance":"6",
                "available":"6",
                "holds":"0",
                "baseCurrency":"BTC",
                "baseCurrencyPrice":"1",
                "baseAmount":"1.1"
            }
        ],
        "tradeAccounts":[
            {
                "currency":"BTC",
                "balance":"1000",
                "available":"1000",
                "holds":"0",
                "baseCurrency":"BTC",
                "baseCurrencyPrice":"1",
                "baseAmount":"1.1"
            }
        ],
        "marginAccounts":[
            {
                "currency":"BTC",
                "balance":"1.1",
                "available":"1.1",
                "holds":"0",
                "baseCurrency":"BTC",
                "baseCurrencyPrice":"1",
                "baseAmount":"1.1"
            }
        ]
    }
]
```
This endpoint returns the account info of all sub-users.
<aside class="notice">It is recommended to use the <code>GET /api/v2/sub-accounts</code> interface for paging query</aside>

### HTTP REQUEST
`GET /api/v1/sub-accounts`
### Example
`GET /api/v1/sub-accounts`
### API KEY PERMISSIONS
This endpoint requires the `General` permission.
### PARAMETERS
`N/A`
### RESPONSES
Field | Description
--------- | -------
subUserId | The user ID of the sub-user.
subName | The username of the sub-user.
currency | The currency of the account.
balance | Total funds in the account.
available | Funds available to withdraw or trade.
holds | Funds on hold (not available for use).
baseCurrency | Calculated on this currency.
baseCurrencyPrice | The base currency price.
baseAmount | The base currency amount.

## Get Paginated Sub-Account Information.
```json
{
    "code": "200000",
    "data": {
        "currentPage": 1,
        "pageSize": 10,
        "totalNum": 14,
        "totalPage": 2,
        "items": [
            {
                "subUserId": "635002438793b80001dcc8b3",
                "subName": "margin03",
                "mainAccounts": [
                    {
                        "currency": "00",
                        "balance": "0",
                        "available": "0",
                        "holds": "0",
                        "baseCurrency": "BTC",
                        "baseCurrencyPrice": "125.63",
                        "baseAmount": "0"
                    }
                ]
            }
        ]
    }
}
```
This endpoint can be used to get paginated sub-account information. Pagination is required.
### HTTP REQUEST
`GET /api/v2/sub-accounts`
### Example
`GET /api/v2/sub-accounts`
### API KEY PERMISSIONS
This endpoint requires the `General` permission.
### PARAMETERS
Param | Type | Mandatory | Description
--------- | ------- | ------- | -------
currentPage | Int | No | Current request page. Default is `1`
pageSize  | Int  | No | Number of results per request. Minimum is `1`, maximum is `100`, default is `10`.
### RESPONSES
Field | Description
--------- | -------
subUserId      | The user ID of the sub-user.
subName    | The username of the sub-user.
currency    | The currency of the account.
balance    | Total funds in the account.
available    | Funds available to withdraw or trade.
holds    | Funds on hold (not available for use).
baseCurrency    | Calculated on this currency.
baseCurrencyPrice    | The base currency price.
baseAmount     | The base currency amount.

## Get the Transferable

```json
 {
    "currency": "KCS",
    "balance": "0",
    "available": "0",
    "holds": "0",
    "transferable": "0"
}
```
This endpoint returns the transferable balance of a specified account.


### HTTP REQUEST
`GET /api/v1/accounts/transferable`

### Example
`GET /api/v1/accounts/transferable?currency=BTC&type=MAIN`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### PARAMETERS
Param | Type | Mandatory | Description
--------- | ------- | ------- | -------
currency | String | Yes |[currency](#get-currencies)
type | String | Yes |The account type: `MAIN`, `TRADE`, `MARGIN` or `ISOLATED`
tag | String | No | Trading pair, required when the account type is `ISOLATED`; other types are not passed, e.g.: `BTC-USDT`

### RESPONSES
Field | Description
--------- | -------
currency | Currency 
balance | Total funds in an account.
available | Funds available to withdraw or trade.
holds | Funds on hold (not available for use).
transferable | Funds available to transfer.


## Transfer between Master user and Sub-user
```json
{
	"orderId": "5cbd870fd9575a18e4438b9a"
}
```
Funds in the main account, trading account and margin account of a Master Account can be transferred to the main account, trading account, futures account and margin account of its Sub-Account. The futures account of both the Master Account and Sub-Account can only accept funds transferred in from the main account, trading account and margin account and cannot transfer out to these accounts.

### HTTP REQUEST
`POST /api/v2/accounts/sub-transfer`

<aside class="notice">Recommended for use</aside>

### Example
`POST /api/v2/accounts/sub-transfer`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is **3 times/3s**.

### PARAMETERS
Param | Type | Description
--------- | ------- | -------
clientOid | String | Unique order id created by users to identify their orders, e.g. UUID.
currency | String | [currency](#Get-Currencies)
amount | String | Transfer amount, the amount is a positive integer multiple of the [currency precision](#get-currencies).
direction | String | OUT — the master user to sub user<br/>IN — the sub user to the master user.
accountType | String | *[Optional]* The account type of the master user: **MAIN**, **TRADE**, **MARGIN** or **CONTRACT**
subAccountType | String | *[Optional]* The account type of the sub user: **MAIN**, **TRADE**, **MARGIN** or **CONTRACT**, default is **MAIN**.
subUserId | String | the [user ID](#get-user-info-of-all-sub-accounts) of a sub-account.


### RESPONSES
Field | Description
--------- | -------
orderId | The order ID of a master-sub assets transfer.


## Inner Transfer
```json
{
    "orderId": "5bd6e9286d99522a52e458de"
}
```

This API endpoint can be used to transfer funds between accounts internally. Users can transfer funds between their main account, trading account, cross margin account, and isolated margin account free of charge. Transfer of funds from the main account, cross margin account, and trading account to the futures account is supported, but transfer of funds from futures accounts to other accounts is not supported.

### HTTP REQUEST
`POST /api/v2/accounts/inner-transfer`

### API KEY PERMISSIONS
This endpoint requires the `Trade` permission.

### PARAMETERS
Param | Type | Mandatory | Description |  
--------- | ------- | -----------| -----------|
clientOid | String | Yes | clientOid, the unique identifier created by the client, use of UUID 
currency | String | Yes | [currency](#Get-Currencies) 
from | String | Yes | Payment Account Type: `main`, `trade`, `margin`, or `isolated` 
to | String | Yes | Receiving Account Type: `main`, `trade`, `margin`, `isolated`, or `contract` 
amount | String | Yes | Transfer amount, the precision being a positive integer multiple of the [Currency Precision](#get-currencies) 
fromTag | String | No | Trading pair, required when the payment account type is `isolated`, e.g.: `BTC-USDT` 
toTag | String | No | Trading pair, required when the receiving account type is `isolated`, e.g.: `BTC-USDT`


### RESPONSES
Field | Description
--------- | -------
orderId | The order ID of a funds transfer


# Deposit

## Create Deposit Address

```json
{
	"address": "0x78d3ad1c0aa1bf068e19c94a2d7b16c9c0fcd8b1",
	"memo": "5c247c8a03aa677cea2a251d",   //tag
	"chain": "OMNI"
}
```
Request via this endpoint to create a deposit address for a currency you intend to deposit.

### HTTP REQUEST
`POST /api/v1/deposit-addresses`

### Example
`POST /api/v1/deposit-addresses`

### API KEY PERMISSIONS
This endpoint requires the **"Transfer"** permission.

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
currency | String | Currency
chain | String | *[Optional]* The chain name of currency, e.g. The available value for USDT are OMNI, ERC20, TRC20, default is ERC20. The available value for BTC are Native, Segwit, TRC20, the parameters are bech32, btc, trx, default is Native. This only apply for multi-chain currency, and there is no need for single chain currency. 

### RESPONSES
Field | Description
--------- | ------- 
address | Deposit address
memo | Address remark. If there’s no remark, it is empty. When you [withdraw](#apply-withdraw) from other platforms to the KuCoin, you need to fill in memo(tag). If you do not fill memo (tag), your deposit may not be available, please be cautious.
chain | The chain name of currency, e.g. The available value for USDT are OMNI, ERC20, TRC20, default is ERC20. The available value for BTC are Native, Segwit, TRC20, the parameters are bech32, btc, trx, default is Native. 

## Get Deposit Addresses(V2)
```json
[
  {
    "address": "bc1qaj6kkv85w5d6lr8p8h7tckyce5hnwmyq8dd84d",
    "memo": "",
    "chain": "BTC-Segwit",
    "contractAddress": ""
  },
  {
    "address": "3HwsFot9TW6jL4K4EUHxDSyL8myttxV7Av",
    "memo": "",
    "chain": "BTC",
    "contractAddress": ""
  },
  {
    "address": "TUDybru26JmozStbg2cJGDbR9EPSbQaAie",
    "memo": "",
    "chain": "TRC20",
    "contractAddress": ""
  }
]
```

Get all deposit addresses for the currency you intend to deposit. If the returned data is empty, you may need to create a deposit address first.

### HTTP REQUEST
`GET /api/v2/deposit-addresses`

### Example
`GET /api/v2/deposit-addresses?currency=BTC`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### PARAMETERS
Param | Type | Description
--------- | -------  | -------
currency | String | The currency

### RESPONSES
Field | Description
--------- | ------- 
address | Deposit address
memo | Address remark. If there’s no remark, it is empty. When you [withdraw](#apply-withdraw) from other platforms to the KuCoin, you need to fill in memo(tag). If you do not fill memo (tag), your deposit may not be available, please be cautious.
chain | The chain name of currency.
contractAddress | The token contract address.

## Get Deposit Address
```json
{
	"address": "0x78d3ad1c0aa1bf068e19c94a2d7b16c9c0fcd8b1",
	"memo": "5c247c8a03aa677cea2a251d",        //tag
	"chain": "OMNI"
}
```

Get a deposit address for the currency you intend to deposit. If the returned data is null, you may need to create a deposit address first.

### HTTP REQUEST
`GET /api/v1/deposit-addresses`

### Example
`GET /api/v1/deposit-addresses`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
currency | String | Currency
chain | String | *[Optional]* The chain name of currency, e.g. The available value for USDT are OMNI, ERC20, TRC20, default is ERC20. The available value for BTC are Native, Segwit, TRC20, the parameters are bech32, btc, trx, default is Native. This only apply for multi-chain currency, and there is no need for single chain currency. 

### RESPONSES
Field | Description
--------- | ------- 
address | Deposit address
memo | Address remark. If there’s no remark, it is empty. When you [withdraw](#apply-withdraw) from other platforms to the KuCoin, you need to fill in memo(tag). If you do not fill memo (tag), your deposit may not be available, please be cautious.
chain | The chain name of currency, e.g. The available value for USDT are OMNI, ERC20, TRC20, default is ERC20. The available value for BTC are Native, Segwit, TRC20, the parameters are bech32, btc, trx, default is Native. 


## Get Deposit List
```json
{
    "code": "200000",
    "data": {
        "currentPage": 1,
        "pageSize": 50,
        "totalNum": 1,
        "totalPage": 1,
        "items": [
            {
                "currency": "XRP",
                "chain": "xrp",
                "status": "SUCCESS",
                "address": "rNFugeoj3ZN8Wv6xhuLegUBBPXKCyWLRkB",
                "memo": "1919537769",
                "isInner": false,
                "amount": "20.50000000",
                "fee": "0.00000000",
                "walletTxId": "2C24A6D5B3E7D5B6AA6534025B9B107AC910309A98825BF5581E25BEC94AD83B@e8902757998fc352e6c9d8890d18a71c",
                "createdAt": 1666600519000,
                "updatedAt": 1666600549000,
                "remark": "Deposit"
            }
        ]
    }
}
```

Request via this endpoint to get deposit list
Items are paginated and sorted to show the latest first. See the [Pagination](#pagination) section for retrieving additional entries after the first page.


### HTTP REQUEST
`GET /api/v1/deposits`

### Example
`GET /api/v1/deposits`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is **6 times/3s**.

<aside class="notice">This request is paginated.</aside>

### PARAMETERS
Param | Type | Mandatory | Description |  
--------- | ------- | -----------| -----------|
currency | String | No | Currency
startAt| long | No | Start time (milisecond)
endAt| long | No | End time (milisecond)
status | String | No | Status. Available value: `PROCESSING`, `SUCCESS`, and `FAILURE`

### RESPONSES
Field | Description
--------- | ------- | -----------
address | Deposit address
memo |Address remark. If there’s no remark, it is empty. When you [withdraw](#apply-withdraw) from other platforms to the KuCoin, you need to fill in memo(tag). If you do not fill memo (tag), your deposit may not be available, please be cautious.
amount | Deposit amount
fee | Fees charged for deposit
currency | Currency
chain | The chain of currency
isInner | Internal deposit or not
walletTxId | Wallet Txid
status | Status
remark | remark
createdAt | Creation time of the database record
updatedAt | Update time of the database record



## Get V1 Historical Deposits List

```json
{
    "currentPage":1,
    "pageSize":1,
    "totalNum":9,
    "totalPage":9,
    "items":[
        {
            "currency":"BTC",
            "createAt":1528536998,
            "amount":"0.03266638",
            "walletTxId":"55c643bc2c68d6f17266383ac1be9e454038864b929ae7cee0bc408cc5c869e8@12ffGWmMMD1zA1WbFm7Ho3JZ1w6NYXjpFk@234",
            "isInner":false,
            "status":"SUCCESS"
        }
    ]
}
```

Request via this endpoint to get the V1 historical deposits list on KuCoin.
<aside class="notice">The data of the latest one month will be queried by default.</aside>

### HTTP REQUEST
`GET /api/v1/hist-deposits`

### Example
`GET /api/v1/hist-deposits`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is **6 times/3s**.

<aside class="notice">This request is paginated.</aside>

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
currency | String | *[Optional]*  [Currency](#get-currencies).
startAt| long | *[Optional]*  Start time (milisecond)
endAt| long | *[Optional]* End time (milisecond)
status | String | *[Optional]*  Status. Available value: PROCESSING, SUCCESS, and FAILURE

### RESPONSES
Field | Description
--------- | ------- | -----------
amount | Deposit amount
currency | Currency
isInner | Internal deposit or not
walletTxId | Wallet Txid
createAt | Creation time of the database record
status | Status

# Withdrawals

## Get Withdrawals List
```json
{
    "code": "200000",
    "data": {
        "currentPage": 1,
        "pageSize": 50,
        "totalNum": 1,
        "totalPage": 1,
        "items": [
            {
                "id": "63564dbbd17bef00019371fb",
                "currency": "XRP",
                "chain": "xrp",
                "status": "SUCCESS",
                "address": "rNFugeoj3ZN8Wv6xhuLegUBBPXKCyWLRkB",
                "memo": "1919537769",
                "isInner": false,
                "amount": "20.50000000",
                "fee": "0.50000000",
                "walletTxId": "2C24A6D5B3E7D5B6AA6534025B9B107AC910309A98825BF5581E25BEC94AD83B",
                "createdAt": 1666600379000,
                "updatedAt": 1666600511000,
                "remark": "test"
            }
        ]
    }
}
```

### HTTP REQUEST
`GET /api/v1/withdrawals`

### Example
`GET /api/v1/withdrawals`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is **6 times/3s**.

<aside class="notice">This request is paginated.</aside>

### PARAMETERS
Param | Type | Mandatory | Description |  
--------- | ------- | -----------| -----------|
currency | String | No | [Currency](#get-currencies)
status | String | No | Status. Available value: `PROCESSING`, `WALLET_PROCESSING`, `SUCCESS`, and `FAILURE`
startAt| long | No | Start time (milisecond)
endAt| long | No | End time (milisecond)

### RESPONSES
Field | Description
--------- | -------
id | Unique identity
address | Withdrawal address
memo |  Address remark. If there’s no remark, it is empty. When you [withdraw](#apply-withdraw) from other platforms to the KuCoin, you need to fill in memo(tag). If you do not fill memo (tag), your deposit may not be available, please be cautious.
currency | Currency
chain | The chain of currency
amount | Withdrawal amount
fee | Withdrawal fee
walletTxId | Wallet Txid
isInner | Internal withdrawal or not
status | status
remark | remark
createdAt | Creation time
updatedAt | Update time

## Get V1 Historical Withdrawals List
```json
{
    "currentPage":1,
    "pageSize":1,
    "totalNum":2,
    "totalPage":2,
    "items":[
        {
            "currency":"BTC",
            "createAt":1526723468,
            "amount":"0.534",
            "address":"33xW37ZSW4tQvg443Pc7NLCAs167Yc2XUV",
            "walletTxId":"aeacea864c020acf58e51606169240e96774838dcd4f7ce48acf38e3651323f4",
            "isInner":false,
            "status":"SUCCESS"
        }
    ]
}
```
List of KuCoin V1 historical withdrawals.

<aside class="notice">Default query for one month of data.</aside>

### HTTP REQUEST
`GET /api/v1/hist-withdrawals`

### Example
`GET /api/v1/hist-withdrawals`


### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is **6 times/3s**.

<aside class="notice">This request is paginated.</aside>

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
currentPage | int | *[Optional]*  The current page.
pageSize | int | *[Optional]*  Number of entries per page.  
currency | String | *[Optional]*  [Currency](#get-currencies).
startAt| long | *[Optional]*  Start time (milisecond)
endAt| long | *[Optional]* End time (milisecond)
status | String | *[Optional]*  Status. Available value: PROCESSING, SUCCESS, and FAILURE

### RESPONSES
Field | Description
--------- | ------- | -----------
amount | Withdrawal amount
currency | Currency
isInner | Internal deposit or not
walletTxId | Wallet Txid
createAt | Creation time of the database record
status | Status

##  Get Withdrawal Quotas
```json
{
	"currency": "KCS",
	"limitBTCAmount": "2.0",
	"usedBTCAmount": "0",
	"remainAmount": "75.67567568",
	"availableAmount": "9697.41991348",
	"withdrawMinFee": "0.93000000",
	"innerWithdrawMinFee": "0.00000000",
	"withdrawMinSize": "1.4",
	"isWithdrawEnabled": true,
	"precision": 8,   //withdrawal precision
	"chain": "OMNI"
}
```

### HTTP REQUEST
`GET /api/v1/withdrawals/quotas`

### Example
`GET /api/v1/withdrawals/quotas?currency=BTC`


### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
currency | String | currency. e.g. BTC
chain | String | *[Optional]* The chain of currency. This only apply for multi-chain currency, and there is no need for single chain currency; you can query the `chain` through the response of the `GET /api/v2/currencies/{currency}` interface.

### RESPONSES
Field | Description
--------- | ------- | -----------
currency | Currency
availableAmount | Current available withdrawal amount
remainAmount | Remaining amount available to withdraw the current day
withdrawMinSize | Minimum withdrawal amount
limitBTCAmount | Total BTC amount available to withdraw the current day
innerWithdrawMinFee | Fees for internal withdrawal
usedBTCAmount | The estimated BTC amount (based on the daily fiat limit) that can be withdrawn within the current day
isWithdrawEnabled | Is the withdraw function enabled or not
withdrawMinFee | Minimum withdrawal fee
precision | Floating point precision.
chain | The chain name of currency, e.g. The available value for USDT are OMNI, ERC20, TRC20, default is ERC20.

## Apply Withdraw
```json
{
  "withdrawalId": "5bffb63303aa675e8bbe18f9"
}
```

### HTTP REQUEST
`POST /api/v1/withdrawals`

<aside class="notice">On the WEB end, you can open the switch of specified favorite addresses for withdrawal, and when it is turned on, it will verify whether your withdrawal address(including chain) is a favorite address(it is case sensitive); if it fails validation, it will respond with the error message <code>{"msg":"Already set withdraw whitelist, this address is not favorite address","code":"260325"}</code>.</aside>

### Example
`POST /api/v1/withdrawals`

### API KEY PERMISSIONS
This endpoint requires the `Transfer` permission.

### PARAMETERS
Param | Type | Mandatory | Description |  
--------- | ------- | -----------| -----------|
currency   | String | Yes |Currency|
address   | String | Yes | Withdrawal address
amount | number | Yes | Withdrawal amount, a positive number which is a multiple of the amount precision (fees excluded)
memo   | String | No | [Optional] Address remark. If there’s no remark, it is empty. When you withdraw from other platforms to the KuCoin, you need to fill in memo(tag). If you do not fill memo (tag), your deposit may not be available, please be cautious.
isInner | boolean | No | [Optional]  Internal withdrawal or not. Default setup: false
remark | String | No | [Optional]  Remark
chain | String | No | *[Optional]* The chain of currency. For a currency with multiple chains, it is recommended to specify chain parameter instead of using the default chain; you can query the `chain` through the response of the `GET /api/v2/currencies/{currency}` interface.
feeDeductType | String | No | Withdrawal fee deduction type: `INTERNAL` or `EXTERNAL` or not specified<br/><br/>1. `INTERNAL`- deduct the transaction fees from your withdrawal amount</br>2. `EXTERNAL`- deduct the transaction fees from your main account</br>3. If you don't specify the `feeDeductType` parameter, when the balance in your main account is sufficient to support the withdrawal, the system will initially deduct the transaction fees from your main account. But if the balance in your main account is not sufficient to support the withdrawal, the system will deduct the fees from your withdrawal amount. For example:  Suppose you are going to withdraw 1 BTC from the KuCoin platform (transaction fee: 0.0001BTC), if the balance in your main account is insufficient, the system will deduct the transaction fees from your withdrawal amount. In this case, you will be receiving 0.9999BTC.

### RESPONSES
Field | Description
--------- | -------
withdrawalId | Withdrawal id

## Cancel Withdrawal
Only withdrawals requests of **PROCESSING** status could be canceled.

### HTTP REQUEST
`DELETE /api/v1/withdrawals/{withdrawalId}`

### Example
`DELETE /api/v1/withdrawals/5bffb63303aa675e8bbe18f9`

### API KEY PERMISSIONS
This endpoint requires the **"Transfer"** permission.

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
withdrawalId | String | Path parameter, a unique ID for a withdrawal order


# Trade Fee

## Basic user fee

This interface is for the basic fee rate of users

```json
{
    "code": "200000",
    "data": {
        "takerFeeRate": "0.001",
        "makerFeeRate": "0.001"
    }
}
```

### HTTP REQUEST
`GET /api/v1/base-fee`

### Example
`GET /api/v1/base-fee`
<br/>
`GET /api/v1/base-fee?currencyType=1`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### PARAMETERS
Param | Type | Mandatory | Description
--------- | ------- | -------| -------
currencyType| String | No | Currency type: `0`-crypto currency, `1`-fiat currency. default is `0`-crypto currency

### RESPONSES
Field | Description
--------- | -------
takerFeeRate | Base taker fee rate
makerFeeRate | Base maker fee rate

## Actual fee rate of the trading pair

This interface is for the actual fee rate of the trading pair. You can inquire about fee rates of 10 trading pairs each time at most. The fee rate of your sub-account is the same as that of the master account.  

```json
{
    "code": "200000",
    "data": [
        {
            "symbol": "BTC-USDT",
            "takerFeeRate": "0.001",
            "makerFeeRate": "0.001"
        },
        {
            "symbol": "KCS-USDT",
            "takerFeeRate": "0.002",
            "makerFeeRate": "0.0005"
        }
    ]
}
```

### HTTP REQUEST
`GET /api/v1/trade-fees`

### Example
`GET /api/v1/trade-fees?symbols=BTC-USDT,KCS-USDT`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### PARAMETERS
Param | Type | Mandatory | Description
--------- | ------- | -------| -------
symbols|String|Yes|Trading pair (optional, you can inquire fee rates of `10` trading pairs each time at most)

### RESPONSES
Field | Description
--------- | -------
symbol | The unique identity of the trading pair and will not change even if the trading pair is renamed
takerFeeRate | Actual taker fee rate of the trading pair
makerFeeRate | Actual maker fee rate of the trading pair

# Trade

Signature is required for this part.

# Orders

## Place a new order

```json
{
  "orderId": "5bd6e9286d99522a52e458de"
}
```

You can place two types of orders: **limit** and **market**. Orders can only be placed if your account has sufficient funds. Once an order is placed, your account funds will be put on hold for the duration of the order. How much and which funds are put on hold depends on the order type and parameters specified. See the Holds details below.

<aside class="notice">Placing an order will enable price protection. When the price of the limit order is outside the threshold range, the price protection mechanism will be triggered, causing the order to fail.</aside>


Please note that the system will frozen the fees from the orders that entered the order book in advance. Read [List Fills](#list-fills) to learn more.

Before placing an order, please read [Get Symbol List](#get-symbols-list) to understand the requirements for the quantity parameters for each trading pair.

**Do not include extra spaces in JSON strings**.

###Place Order Limit

The maximum active orders for a single trading pair in one account is **200** (stop orders included).


### HTTP Request
`POST /api/v1/orders`

### Example
`POST /api/v1/orders`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is **45 times/3s**.

### PARAMETERS
| Param     | type   | Description  |
| --------- | ------ |-------------------------------- |
| clientOid | String | Unique order id created by users to identify their orders, e.g. UUID. |
| side      | String | **buy** or **sell**      |
| symbol    | String | a valid trading symbol code. e.g. ETH-BTC     |
| type      | String | *[Optional]* **limit** or **market** (default is **limit**)          |
| remark    | String | *[Optional]*  remark for the order, length cannot exceed 100 utf8 characters|
| stp       | String | *[Optional]*  self trade prevention , **CN**, **CO**, **CB** or **DC**|
| tradeType | String | *[Optional]* The type of trading : **TRADE**（Spot Trade）, **MARGIN_TRADE** (Margin Trade). Default is **TRADE**. **Note: To improve the system performance and to accelerate order placing and processing, KuCoin has added a new interface for order placing of margin. For traders still using the current interface, please move to the new one as soon as possible. The current one will no longer accept margin orders by May 1st, 2021 (UTC). At the time, KuCoin will notify users via the announcement, please pay attention to it.** |

#### LIMIT ORDER PARAMETERS
| Param       | type    | Description                                                  |
| ----------- | ------- | ------------------- |
| price       | String  | price per base currency          |
| size        | String  | amount of base currency to buy or sell         |
| timeInForce | String  | *[Optional]* **GTC**, **GTT**, **IOC**, or **FOK** (default is **GTC**), read [Time In Force](#time-in-force).   |
| cancelAfter | long    | *[Optional]*  cancel after **n** seconds, requires **timeInForce** to be **GTT**                   |
| postOnly    | boolean | *[Optional]*  Post only flag, invalid when **timeInForce** is **IOC** or **FOK**                               |
| hidden      | boolean | *[Optional]*  Order will not be displayed in the order book |
| iceberg    | boolean | *[Optional]*  Only aportion of the order is displayed in the order book |
| visibleSize | String  | *[Optional]*  The maximum visible size of an iceberg order   |


#### MARKET ORDER PARAMETERS
Param | type | Description
--------- | ------- | -----------
size | String | *[Optional]*  Desired amount in base currency
funds | String | *[Optional]*  The desired amount of quote currency to use

* It is required that you use one of the two parameters, **size** or **funds**.

###Advanced Description

###SYMBOL

The symbol must match a valid trading [symbol](#get-symbols-list).

###CLIENT ORDER ID

Generated by yourself, the optional clientOid field must be a unique id (e.g UUID). Only numbers, characters, underline(_) and separator(-) are allowed. The value will be returned in order detail. You can use this field to identify your orders via the public feed. The client_oid is different from the server-assigned order id. Please do not send a repeated client_oid. The length of the client_oid cannot exceed 40 characters. You should record the server-assigned order_id as it will be used for future query order status.


###TYPE

The order type you specify may decide whether other optional parameters are required, as well as how your order will be executed by the matching engine. If order type is not specified, the order will be a **limit** order by default.

**Price** and **size** are required to be specified for a **limit order**.  The order will be filled at the price specified or better, depending on the market condition.   If a limit order cannot be filled immediately, it will be outstanding in the open order book until matched by another order, or canceled by the user.


A **market order** differs from a limit order in that the execution price is not guaranteed. Market order, however, provides a way to buy or sell specific size of order without having to specify the price. Market orders will be executed immediately, and no orders will enter the open order book afterwards. Market orders are always considered takers and incur taker fees.

###TradeType
The platform currently supports spot (**TRADE**) and margin (**MARGIN_TRADE**) . The system will freeze the funds of the specified account according to your parameter type. If this parameter is not specified, the funds in your trade account will be frozen by default. **Note: To improve the system performance and to accelerate order placing and processing, KuCoin has added a new interface for order placing of margin. For traders still using the current interface, please move to the new one as soon as possible. The current one will no longer accept margin orders by May 1st, 2021 (UTC). At the time, KuCoin will notify users via the announcement, please pay attention to it.** 

###PRICE
The price must be specified in priceIncrement symbol units. The priceIncrement is the smallest unit of price. For the BTC-USDT symbol, the priceIncrement is 0.00001000. Prices less than 0.00001000 will not be accepted, The price for the placed order should be multiple numbers of priceIncrement, or the system would report an error when you place the order. Not required for market orders.

###SIZE
The size must be greater than the baseMinSize for the symbol and no larger than the baseMaxSize. The size must be specified in baseIncrement symbol units. Size indicates the amount of BTC (or base currency) to buy or sell.

###FUNDS
The funds field indicates the how much of the quote currency you wish to buy or sell. The size of the funds must be specified in quoteIncrement symbol units and the size of funds in order shall be a positive integer multiple of quoteIncrement, ensuring the funds is greater than the quoteMinSize for the symbol but no larger than the quoteMaxSize.


###TIME IN FORCE
Time in force policies provide guarantees about the lifetime of an order. There are four policies: Good Till Canceled **GTC**, Good Till Time **GTT**, Immediate Or Cancel **IOC**, and Fill Or Kill **FOK**.

**GTC** Good Till Canceled orders remain open on the book until canceled. This is the default behavior if no policy is specified.

**GTT** Good Till Time orders remain open on the book until canceled or the allotted cancelAfter is depleted on the matching engine. GTT orders are guaranteed to cancel before any other order is processed after the cancelAfter seconds placed in order book.

**IOC** Immediate Or Cancel orders instantly cancel the remaining size of the limit order instead of opening it on the book.

**FOK** Fill Or Kill orders are rejected if the entire size cannot be matched.

* Note that self trades belong to match as well. For market orders, using the “TimeInForce” parameter has no effect.

### POST ONLY
The post-only flag ensures that the trader always pays the maker fee and provides liquidity to the order book. If any part of the order is going to pay taker fee, the order will be fully rejected.

If a post only order will get executed immediately against the existing orders (except iceberg and hidden orders) in the market, the order will be cancelled.

* For post only orders, it will get executed immediately against the iceberg orders and hidden orders in the market. Users placing the post only order will be charged the maker fees and the iceberg and hidden orders will be charged the taker fees.


### HIDDEN AND ICEBERG


The **Hidden** and **iceberg Orders** are two **options** in advanced settings (note: the iceberg order is a special form of the hidden order). You may select “Hidden” or “Iceberg” when placing a limit or stop limit order.

A hidden order will enter but not display on the orderbook.

Different from the hidden order, an **iceberg order** is divided into visible portion and invisible portion. When placing an iceberg order, you need to set the **visible size**. The minimum visible size is 1/20 of the order size. The minimum visible size shall be greater than the minimum order size, or an error will occur.

In a matching event, the visible portion of an iceberg order will be executed first, and another visible portion will pop up until the order is fully filled.

**Note**:
- The system will charge **taker fees** for **Hidden** and **iceberg Orders**.

- If both "Iceberg" and "Hidden" are selected, your order will be filled as an **iceberg Order** by default.


###HOLDS
For limit buy orders, we will hold the needed portion from your funds (price x size of the order). Likewise, on sell orders, we will also hold the amount of assets that you wish to sell. Actual fees are assessed at the time of a trade. If you cancel a partially filled or unfilled order, any remaining funds will be released from being held.

For market buy or sell orders where the funds are specified, the funds amount will be put on hold. If only size is specified, all of your account balance (in the quote account) will be put on hold for the duration of the market order (usually a trivially short time).

### SELF-TRADE PREVENTION

**Self-Trade Prevention** is an option in advanced settings.It is not selected by default. If you specify **STP** when placing orders, your order won't be matched by another one which is also yours. On the contrary, if **STP** is not specified in advanced, your order can be matched by another one of your own orders.

**Market order is currently not supported for DC**. When the **timeInForce** is set to **FOK**, the **stp** flag will be forcely specified as **CN**.


**Market order is currently not supported for DC**. When *timeInForce* is **FOK**, the stp flag will be forced to be specified as **CN**.

| Flag | Name                          |
| ---- | ----------------------------- |
| DC   | Decrease and Cancel           |
| CO   | Cancel oldest                 |
| CN   | Cancel newest                 |
| CB   | Cancel both                   |

### ORDER LIFECYCLE
The HTTP Request will respond when an order is either rejected (insufficient funds, invalid parameters, etc) or received (accepted by the matching engine). A **200** response indicates that the order was received and is active. **Active** orders may execute immediately (depending on price and market conditions) either partially or fully. A partial execution will put the remaining size of the order in the open state. An order that is filled completely, will go into the **done** state.

Users listening to streaming market data are encouraged to use the order ID field to identify their received messages in the feed.

### PRICE PROTECTION MECHANISM

1. If there are contra orders against the market/limit orders placed by users in the order book, the system will detect whether the difference between the corresponding market price and the ask/bid price will exceed the threshold (you can request via the API symbol interface).
2. For limit orders, if the difference exceeds the threshold, the order placement would fail.
3. For market orders, the order will be partially executed against the existing orders in the market within the threshold and the remaining unfilled part of the order will be canceled immediately.
For example: If the threshold is 10%, when a user places a market order to buy 10,000 USDT in the KCS/USDT market (at this time, the current ask price is 1.20000), the system would determine that the final execution price would be 1.40000. As for (1.40000-1.20000)/1.20000=16.7%>10%, the threshold price would be 1.32000. Therefore, this market order will execute with the existing orders offering prices up to 1.32000 and the remaining part of the order will be canceled immediately.
Notice: There might be some deviations of the detection. If your order is not fully filled, it may probably be led by the unfilled part of the order exceeding the threshold.


###RESPONSES
Field | Description
--------- | -------
orderId | The ID of the order

A successful order will be assigned an order ID. A successful order is defined as one that has been accepted by the matching engine.

<aside class="notice">Open orders do not expire and will remain open until they are either filled or canceled.</aside>


## Place a margin order
```json
{
  "orderId": "5bd6e9286d99522a52e458de",
  "borrowSize":10.2,
  "loanApplyId":"600656d9a33ac90009de4f6f"
}
```

You can place two types of orders: `limit` and `market`. Orders can only be placed if your account has sufficient funds. Once an order is placed, your account funds will be put on hold for the duration of the order. How much and which funds are put on hold depends on the order type and parameters specified. See the Holds details below.

<aside class="notice">Placing an order will enable price protection. When the price of the limit order is outside the threshold range, the price protection mechanism will be triggered, causing the order to fail.</aside>


Please note that the system will frozen the fees from the orders that entered the order book in advance. Read [List Fills](#list-fills) to learn more.

Before placing an order, please read [Get Symbol List](#get-symbols-list) to understand the requirements for the quantity parameters for each trading pair.

**Do not include extra spaces in JSON strings**.

### Place Order Limit
The maximum active orders for a single trading pair in one account is `200` (stop orders included).

### HTTP Request
`POST /api/v1/margin/order`

### API KEY PERMISSIONS
This endpoint requires the `Trade` permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is `45 times/3s`.

### PARAMETERS
| Param     | type   | Description  |
| --------- | ------ |-------------------------------- |
| clientOid | String | Unique order id created by users to identify their orders, e.g. UUID. |
| side      | String | `buy` or `sell`      |
| symbol    | String | a valid trading symbol code. e.g. ETH-BTC     |
| type      | String | *[Optional]* `limit` or `market` (default is `limit`)          |
| remark    | String | *[Optional]*  remark for the order, length cannot exceed 100 utf8 characters|
| stp       | String | *[Optional]*  self trade prevention , `CN`, `CO`, `CB` or `DC`|
| marginModel | String | *[Optional]*  The type of trading, including `cross` (cross mode) and `isolated` (isolated mode). It is set at `cross` by default.|
| autoBorrow | boolean | *[Optional]*  Auto-borrow to place order. The system will first borrow you funds at the optimal interest rate and then place an order for you. Currently `autoBorrow` parameter only supports `cross` mode, not `isolated` mode|

#### LIMIT ORDER PARAMETERS

| Param       | type    | Description                                                  |
| ----------- | ------- | ------------------- |
| price       | String  | price per base currency          |
| size        | String  | amount of base currency to buy or sell         |
| timeInForce | String  | *[Optional]* `GTC`, `GTT`, `IOC`, or `FOK` (default is `GTC`), read [Time In Force](#time-in-force).   |
| cancelAfter | long    | *[Optional]*  cancel after `n` seconds, requires `timeInForce` to be `GTT`                  |
| postOnly    | boolean | *[Optional]*  Post only flag, invalid when `timeInForce` is `IOC` or `FOK`                               |
| hidden      | boolean | *[Optional]*  Order will not be displayed in the order book |
| iceberg    | boolean | *[Optional]*  Only aportion of the order is displayed in the order book |
| visibleSize | String  | *[Optional]*  The maximum visible size of an iceberg order   |


#### MARKET ORDER PARAMETERS

Param | type | Description
--------- | ------- | -----------
size | String | *[Optional]*  Desired amount in base currency
funds | String | *[Optional]*  The desired amount of quote currency to use

* It is required that you use one of the two parameters, `size` or `funds`.

###Advanced Description


###MarginMode
There are two modes for API margin trading: `cross` and `isolated`, it is set at `cross` by default.

###AutoBorrow
This is the symbol of Auto-Borrow, if it is set to `true`, the system will automatically borrow the funds required for an order according to the order amount. By default, the symbol is set to `false`. When your order amount is too large, exceeding the max. borrowing amount via the max. leverage or the risk limit of margin, then you will fail in borrowing and order placing.  Currently `autoBorrow` parameter only supports `cross` mode, not `isolated` mode


###RESPONSES
Field | Description
--------- | -------
orderId | The ID of the order
borrowSize | Borrowed amount. The field is returned only after placing the order under the mode of Auto-Borrow. 
loanApplyId | ID of the borrowing response. The field is returned only after placing the order under the mode of Auto-Borrow.

A successful order will be assigned an `orderId`. A successful order is defined as one that has been accepted by the matching engine.

<aside class="notice">Open orders do not expire and will remain open until they are either filled or canceled.</aside>


## Place Bulk Orders

```json
//response
{
  "data": [
    {
      "symbol": "KCS-USDT",
      "type": "limit",
      "side": "buy",
      "price": "0.01",
      "size": "0.01",
      "funds": null,
      "stp": "",
      "stop": "",
      "stopPrice": null,
      "timeInForce": "GTC",
      "cancelAfter": 0,
      "postOnly": false,
      "hidden": false,
      "iceberge": false,
      "iceberg": false,
      "visibleSize": null,
      "channel": "API",
      "id": "611a6a309281bc000674d3c0",
      "status": "success",
      "failMsg": null,
      "clientOid": "552a8a0b7cb04354be8266f0e202e7e9"
    },
    {
      "symbol": "KCS-USDT",
      "type": "limit",
      "side": "buy",
      "price": "0.01",
      "size": "0.01",
      "funds": null,
      "stp": "",
      "stop": "",
      "stopPrice": null,
      "timeInForce": "GTC",
      "cancelAfter": 0,
      "postOnly": false,
      "hidden": false,
      "iceberge": false,
      "iceberg": false,
      "visibleSize": null,
      "channel": "API",
      "id": "611a6a309281bc000674d3c1",
      "status": "success",
      "failMsg": null,
      "clientOid": "bd1e95e705724f33b508ed270888a4a9"
    }
  ]
}
```

Request via this endpoint to place 5 orders at the same time. The order type must be a limit order of the same symbol.
**The interface currently only supports spot trading**


### HTTP Request
`POST /api/v1/orders/multi`


### Example
```json
//request
{
  "symbol": "KCS-USDT",
  "orderList": [
    {
      "clientOid": "3d07008668054da6b3cb12e432c2b13a",
      "side": "buy",
      "type": "limit",
      "price": "0.01",
      "size": "0.01"
    },
    {
      "clientOid": "37245dbe6e134b5c97732bfb36cd4a9d",
      "side": "buy",
      "type": "limit",
      "price": "0.01",
      "size": "0.01"
    }
  ]
}
```
`POST /api/v1/orders/multi`

### API KEY PERMISSIONS
This endpoint requires the `Trade` permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is `3 times/3s`.

### PARAMETERS
| Param     | type   | Description  |
| --------- | ------ |-------------------------------- |
| clientOid | String | Unique order id created by users to identify their orders, e.g. UUID. |
| side      | String | **buy** or **sell**      |
| symbol    | String | a valid trading symbol code. e.g. ETH-BTC     |
| type      | String | *[Optional]* only **limit** (default is **limit**)          |
| remark    | String | *[Optional]*  remark for the order, length cannot exceed 100 utf8 characters|
| stop      | String | *[Optional]* Either **loss** or **entry**. Requires **stopPrice** to be defined |
| stopPrice | String | *[Optional]* Need to be defined if stop is specified. |
| stp       | String | *[Optional]*  self trade prevention , **CN**, **CO**, **CB** or **DC**|
| tradeType | String | *[Optional]*  Default is **TRADE** |
| price       | String  | price per base currency          |
| size        | String  | amount of base currency to buy or sell         |
| timeInForce | String  | *[Optional]* **GTC**, **GTT**, **IOC**, or **FOK** (default is **GTC**), read [Time In Force](#time-in-force).   |
| cancelAfter | long    | *[Optional]*  cancel after **n** seconds, requires **timeInForce** to be **GTT**                   |
| postOnly    | boolean | *[Optional]*  Post only flag, invalid when **timeInForce** is **IOC** or **FOK**                               |
| hidden      | boolean | *[Optional]*  Order will not be displayed in the order book |
| iceberg     | boolean | *[Optional]*  Only aportion of the order is displayed in the order book |
| visibleSize | String  | *[Optional]*  The maximum visible size of an iceberg order   |

### RESPONSES
Field | Description
--------- | -------
|status  |  status (success, fail) |
|failMsg |  the cause of failure   |


## Cancel an order

```json
{
     "cancelledOrderIds": [
      "5bd6e9286d99522a52e458de"   //orderId
    ]
}
```

Request via this endpoint to cancel a single order previously placed.

<aside class="notice">This interface is only for cancellation requests. The cancellation result needs to be obtained by querying the order status or subscribing to websocket. It is recommended that you DO NOT cancel the order until receiving the Open message, otherwise the order cannot be cancelled successfully.
</aside>


### HTTP REQUEST
`DELETE /api/v1/orders/{orderId}`

### Example
`DELETE /api/v1/orders/5bd6e9286d99522a52e458de`


### API KEY PERMISSIONS
This endpoint requires the `Trade` permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is `60 times/3s`.

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
orderId | String | [Order ID](#list-orders), unique ID of the order.

### RESPONSES
Field | Description
--------- | -------
orderId | Unique ID of the cancelled order



<aside class="notice">The <b>order ID</b> is the server-assigned order id and not the passed clientOid.</aside>

### CANCEL REJECT
If the order could not be canceled (already filled or previously canceled, etc), then an error response will indicate the reason in the **message** field.

## Cancel Single Order by clientOid

```json
{
  "cancelledOrderId": "5f311183c9b6d539dc614db3",
  "clientOid": "6d539dc614db3"
}
```

Request via this interface to cancel an order via the clientOid.

### HTTP REQUEST
`DELETE /api/v1/order/client-order/{clientOid}`

### Example
`DELETE /api/v1/order/client-order/6d539dc614db3`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
| Param | Type | Description                            |
| ------- | ------ | ----------------------------- |
| clientOid | String | Unique order id created by users to identify their orders |

### RESPONSES
| Field | Description     |
| ----------------- | ------- |
| cancelledOrderId | Order ID of cancelled order |
| clientOid | Unique order id created by users to identify their orders |

## Cancel all orders
```json
{
    "cancelledOrderIds": [

        "5c52e11203aa677f33e493fb",  //orderId
        "5c52e12103aa677f33e493fe",
        "5c52e12a03aa677f33e49401",
        "5c52e1be03aa677f33e49404",
        "5c52e21003aa677f33e49407",
        "5c6243cb03aa67580f20bf2f",
        "5c62443703aa67580f20bf32",
        "5c6265c503aa676fee84129c",
        "5c6269e503aa676fee84129f",
        "5c626b0803aa676fee8412a2"
    ]
}
```
Request via this endpoint to cancel all open orders. The response is a list of ids of the canceled orders.

### HTTP REQUEST
`DELETE /api/v1/orders`

### Example
`DELETE /api/v1/orders?symbol=ETH-BTC&tradeType=TRADE`<br/>
`DELETE /api/v1/orders?symbol=ETH-BTC&tradeType=MARGIN_ISOLATED_TRADE`

### API KEY PERMISSIONS
This endpoint requires the `Trade` permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is `3 times/3s`.

### PARAMETERS
|Param | Type | Description|
|--------- | ------- | -----------|
|symbol | String | *[Optional]* symbol, cancel the orders for the specified trade pair. |
|tradeType| String | *[Optional]*  the type of trading :`TRADE`(Spot Trading), `MARGIN_TRADE`(Cross Margin Trading), `MARGIN_ISOLATED_TRADE`(Isolated Margin Trading), and the default is `TRADE` to cancel the spot trading orders.|

### RESPONSES
Field | Description
--------- | -------
orderId | Order ID, unique identifier of an order.



## List Orders

```json
{
    "currentPage": 1,
    "pageSize": 1,
    "totalNum": 153408,
    "totalPage": 153408,
    "items": [
        {
            "id": "5c35c02703aa673ceec2a168",   //orderid
            "symbol": "BTC-USDT",   //symbol
            "opType": "DEAL",      // operation type: DEAL
            "type": "limit",       // order type,e.g. limit,market,stop_limit.
            "side": "buy",         // transaction direction,include buy and sell
            "price": "10",         // order price
            "size": "2",           // order quantity
            "funds": "0",          // order funds
            "dealFunds": "0.166",  // deal funds
            "dealSize": "2",       // deal quantity
            "fee": "0",            // fee
            "feeCurrency": "USDT", // charge fee currency
            "stp": "",             // self trade prevention,include CN,CO,DC,CB
            "stop": "",            // stop type
            "stopTriggered": false,  // stop order is triggered
            "stopPrice": "0",      // stop price
            "timeInForce": "GTC",  // time InForce,include GTC,GTT,IOC,FOK
            "postOnly": false,     // postOnly
            "hidden": false,       // hidden order
            "iceberg": false,      // iceberg order
            "visibleSize": "0",    // display quantity for iceberg order
            "cancelAfter": 0,      // cancel orders time，requires timeInForce to be GTT
            "channel": "IOS",      // order source
            "clientOid": "",       // user-entered order unique mark
            "remark": "",          // remark
            "tags": "",            // tag order source        
            "isActive": false,     // status before unfilled or uncancelled
            "cancelExist": false,   // order cancellation transaction record
            "createdAt": 1547026471000,  // create time
            "tradeType": "TRADE"
        }
     ]
 }
```

Request via this endpoint to get your current order list. Items are paginated and sorted to show the latest first. See the [Pagination](#pagination) section for retrieving additional entries after the first page.

### HTTP REQUEST
`GET /api/v1/orders`

### Example
`GET /api/v1/orders?status=active`<br/>
`GET /api/v1/orders?status=active?tradeType=MARGIN_ISOLATED_TRADE`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is `30 times/3s`.

<aside class="notice">This request is paginated.</aside>


### PARAMETERS
You can pinpoint the results with the following query paramaters.

Param | Type | Description
--------- | ------- | -----------
status | String |*[Optional]* `active` or `done`(`done` as default), Only list orders with a specific status .
symbol |String|*[Optional]* Only list orders for a specific symbol.
side | String | *[Optional]* `buy` or `sell`
type | String | *[Optional]* `limit`, `market`, `limit_stop` or `market_stop`
tradeType | String |The type of trading:`TRADE`-Spot Trading, `MARGIN_TRADE`-Cross Margin Trading, `MARGIN_ISOLATED_TRADE`-Isolated Margin Trading.
startAt| long | *[Optional]*  Start time (milisecond)
endAt| long | *[Optional]* End time (milisecond)

### RESPONSES
Field | Description
--------- | -------
id |  Order ID, the ID of an order.
symbol | symbol
opType |  Operation type: DEAL
type | order type
side | transaction direction,include buy and sell
price |  order price
size |  order quantity
funds | order funds
dealFunds |  executed size of funds
dealSize | executed quantity
fee | fee
feeCurrency | charge fee currency
stp |  self trade prevention,include `CN`,`CO`,`DC`,`CB`
stop |  stop type, include entry and loss
stopTriggered |  stop order is triggered or not
stopPrice |  stop price
timeInForce | time InForce,include `GTC`,`GTT`,`IOC`,`FOK`
postOnly | postOnly
hidden | hidden order
iceberg | iceberg order
visibleSize | displayed quantity for iceberg order
cancelAfter | cancel orders time，requires timeInForce to be `GTT`
channel | order source
clientOid | user-entered order unique mark
remark | remark
tags | tag order source
isActive |  order status, true and false. If true, the order is active, if false, the order is fillled or cancelled
cancelExist | order cancellation transaction record
createdAt | create time
tradeType | The type of trading

### ORDER STATUS AND SETTLEMENT
Any order on the exchange order book is in active status. Orders removed from the order book will be marked with done status. After an order becomes done, there may be a few milliseconds latency before it’s fully settled.

You can check the orders in any status. If the status parameter is not specified, orders of done status will be returned by default.

When you query orders in active status, there is no time limit. However, when you query orders in done status, the start and end time range cannot exceed 7* 24 hours. An error will occur if the specified time window exceeds the range. If you specify the end time only, the system will automatically calculate the start time as end time minus 7*24 hours, and vice versa.


The history for cancelled orders is only kept for **one month**. You will not be able to query for cancelled orders that have happened more than a month ago.

<aside class="notice">The total number of items retrieved cannot exceed 50,000. If it is exceeded, please shorten the query time range.</aside>

### POLLING
For high-volume trading, it is highly recommended that you maintain your own list of open orders and use one of the streaming market data feeds to keep it updated. You should poll the open orders endpoint to obtain the current state of any open order.

## Recent Orders

```json
{
    "currentPage": 1,
    "pageSize": 1,
    "totalNum": 153408,
    "totalPage": 153408,
    "items": [
        {
            "id": "5c35c02703aa673ceec2a168",
            "symbol": "BTC-USDT",
            "opType": "DEAL",
            "type": "limit",
            "side": "buy",
            "price": "10",
            "size": "2",
            "funds": "0",
            "dealFunds": "0.166",
            "dealSize": "2",
            "fee": "0",
            "feeCurrency": "USDT",
            "stp": "",
            "stop": "",
            "stopTriggered": false,
            "stopPrice": "0",
            "timeInForce": "GTC",
            "postOnly": false,
            "hidden": false,
            "iceberg": false,
            "visibleSize": "0",
            "cancelAfter": 0,
            "channel": "IOS",
            "clientOid": "",
            "remark": "",
            "tags": "",
            "isActive": false,
            "cancelExist": false,
            "createdAt": 1547026471000,
            "tradeType": "TRADE"
        }
    ]
}
```

Request via this endpoint to get 1000 orders in the last 24 hours.
Items are paginated and sorted to show the latest first. See the [Pagination](#pagination) section for retrieving additional entries after the first page.

### HTTP REQUEST
`GET /api/v1/limit/orders`

### Example
`GET /api/v1/limit/orders`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.


### RESPONSES
Field | Description
--------- | -------
orderId | Order ID, unique identifier of an order.
symbol | symbol
opType |  Operation type: DEAL
type | order type, e.g. limit, market, stop_limit
side | transaction direction,include buy and sell
price |  order price
size |  order quantity
funds | order funds
dealFunds |  deal funds
dealSize | deal quantity
fee | fee
feeCurrency | charge fee currency
stp |  self trade prevention,include CN,CO,DC,CB
stop |  stop type, include entry and loss
stopTriggered |  stop order is triggered
stopPrice |  stop price
timeInForce | time InForce,include GTC,GTT,IOC,FOK
postOnly | postOnly
hidden | hidden order
iceberg | iceberg order
visibleSize | display quantity for iceberg order
cancelAfter | cancel orders time，requires timeInForce to be GTT
channel | order source
clientOid | user-entered order unique mark
remark | remark
tags | tag order source
isActive | order status, true and false. If true, the order is active, if false, the order is fillled or cancelled
cancelExist | order cancellation transaction record
createdAt | create time
tradeType | The type of trading : **TRADE**（Spot Trading）, **MARGIN_TRADE** (Margin Trading).




<aside class="spacer4"></aside>
<aside class="spacer2"></aside>

## Get an order

```json
{
    "id": "5c35c02703aa673ceec2a168",
    "symbol": "BTC-USDT",
    "opType": "DEAL",
    "type": "limit",
    "side": "buy",
    "price": "10",
    "size": "2",
    "funds": "0",
    "dealFunds": "0.166",
    "dealSize": "2",
    "fee": "0",
    "feeCurrency": "USDT",
    "stp": "",
    "stop": "",
    "stopTriggered": false,
    "stopPrice": "0",
    "timeInForce": "GTC",
    "postOnly": false,
    "hidden": false,
    "iceberg": false,
    "visibleSize": "0",
    "cancelAfter": 0,
    "channel": "IOS",
    "clientOid": "",
    "remark": "",
    "tags": "",
    "isActive": false,
    "cancelExist": false,
    "createdAt": 1547026471000,
    "tradeType": "TRADE"
 }
```
Request via this endpoint to get a single order info by order ID.

### HTTP REQUEST
`GET /api/v1/orders/{order-id}`

### Example
`GET /api/v1/orders/5c35c02703aa673ceec2a168`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
orderId | String | Order ID, unique identifier of an order, obtained via the [List orders](#list-orders).

### RESPONSES
Field | Description
--------- | -------
orderId | Order ID, the ID of an order
symbol | symbol
opType |  operation type,deal is pending order,cancel is cancel order
type | order type,e.g. limit,market,stop_limit.
side | transaction direction,include buy and sell
price |  order price
size |  order quantity
funds | order funds
dealFunds |  deal funds
dealSize | deal quantity
fee | fee
feeCurrency | charge fee currency
stp |  self trade prevention,include CN,CO,DC,CB
stop |  stop type, include entry and loss
stopTriggered |  stop order is triggered
stopPrice |  stop price
timeInForce | time InForce,include GTC,GTT,IOC,FOK
postOnly | postOnly
hidden | hidden order
iceberg | iceberg order
visibleSize | display quantity for iceberg order
cancelAfter | cancel orders time，requires timeInForce to be GTT
channel | order source
clientOid | user-entered order unique mark
remark | remark
tags | tag order source
isActive | order status, true and false. If true, the order is active, if false, the order is fillled or cancelled
cancelExist | order cancellation transaction record
createdAt | create time
tradeType | The type of trading : **TRADE**（Spot Trading）, **MARGIN_TRADE** (Margin Trading).



<aside class="spacer4"></aside>
<aside class="spacer2"></aside>


## Get Single Active Order by clientOid 

```json
{
  "id": "5f3113a1c9b6d539dc614dc6",
  "symbol": "KCS-BTC",
  "opType": "DEAL",
  "type": "limit",
  "side": "buy",
  "price": "0.00001",
  "size": "1",
  "funds": "0",
  "dealFunds": "0",
  "dealSize": "0",
  "fee": "0",
  "feeCurrency": "BTC",
  "stp": "",
  "stop": "",
  "stopTriggered": false,
  "stopPrice": "0",
  "timeInForce": "GTC",
  "postOnly": false,
  "hidden": false,
  "iceberg": false,
  "visibleSize": "0",
  "cancelAfter": 0,
  "channel": "API",
  "clientOid": "6d539dc614db312",
  "remark": "",
  "tags": "",
  "isActive": true,
  "cancelExist": false,
  "createdAt": 1597051810000,
  "tradeType": "TRADE"
}
```

Request via this interface to check the information of a single active order via clientOid. The system will prompt that the order does not exists if the order does not exist or has been settled.


### HTTP REQUEST
`GET /api/v1/order/client-order/{clientOid}`

### Example
`GET /api/v1/order/client-order/6d539dc614db312`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### PARAMETERS
| Param | Type | Description                           |
| ------- | ------ | ----------------------------- |
| clientOid | String | Unique order id created by users to identify their orders |

### RESPONSES
Field | Description
--------- | -------
id | Order ID, the ID of an order
symbol | symbol
opType |  operation type,deal is pending order,cancel is cancel order
type | order type,e.g. limit,market,stop_limit.
side | transaction direction,include buy and sell
price |  order price
size |  order quantity
funds | order funds
dealFunds |  deal funds
dealSize | deal quantity
fee | fee
feeCurrency | charge fee currency
stp |  self trade prevention,include CN,CO,DC,CB
stop |  stop type, include entry and loss
stopTriggered |  stop order is triggered
stopPrice |  stop price
timeInForce | time InForce,include GTC,GTT,IOC,FOK
postOnly | postOnly
hidden | hidden order
iceberg | iceberg order
visibleSize | display quantity for iceberg order
cancelAfter | cancel orders time，requires timeInForce to be GTT
channel | order source
clientOid | user-entered order unique mark
remark | remark
tags | tag order source
isActive | order status, true and false. If true, the order is active, if false, the order is fillled or cancelled
cancelExist | order cancellation transaction record
createdAt | create time
tradeType | The type of trading : **TRADE**（Spot Trading）, **MARGIN_TRADE** (Margin Trading).



# Fills

## List Fills

```json
{
    "currentPage":1,
    "pageSize":1,
    "totalNum":251915,
    "totalPage":251915,
    "items":[
        {
            "symbol":"BTC-USDT",    //symbol
            "tradeId":"5c35c02709e4f67d5266954e",   //trade id
            "orderId":"5c35c02703aa673ceec2a168",   //order id
            "counterOrderId":"5c1ab46003aa676e487fa8e3",  //counter order id
            "side":"buy",   //transaction direction,include buy and sell
            "liquidity":"taker",  //include taker and maker
            "forceTaker":true,  //forced to become taker
            "price":"0.083",   //order price
            "size":"0.8424304",  //order quantity
            "funds":"0.0699217232",  //order funds
            "fee":"0",  //fee
            "feeRate":"0",  //fee rate
            "feeCurrency":"USDT",  // charge fee currency
            "stop":"",        // stop type
            "type":"limit",  // order type,e.g. limit,market,stop_limit.
            "createdAt":1547026472000,  //time
            "tradeType": "TRADE"
        }
    ]
}
```

Request via this endpoint to get the recent fills.

Items are paginated and sorted to show the latest first. See the [Pagination](#pagination) section for retrieving additional entries after the first page.


### HTTP REQUEST
`GET /api/v1/fills`

### Example
`GET /api/v1/fills`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is **9 times/3s**.

<aside class="notice">This request is paginated.</aside>


### PARAMETERS
You can request fills for specific orders using query parameters.

Param | Type | Description
--------- | ------- | -----------
orderId | String |*[Optional]* Limit the list of fills to this orderId（If you specify orderId, ignore other conditions）
symbol | String |*[Optional]* Limit the list of fills to this symbol
side | String |*[Optional]* **buy** or **sell**
type | String |*[Optional]* **limit**, **market**, **limit_stop** or **market_stop**
startAt| long | *[Optional]*  Start time (milisecond)
endAt| long | *[Optional]* End time (milisecond)
tradeType | String |The type of trading : **TRADE**（Spot Trading）, **MARGIN_TRADE** (Margin Trading).


### RESPONSES
Field | Description
--------- | -------
symbol | symbol.
tradeId | trade id, it is generated by Matching engine.
orderId | Order ID, unique identifier of an order.
counterOrderId | counter order id.
side | transaction direction,include buy and sell.
price |  order price
size |  order quantity
funds | order funds
type | order type,e.g. limit,market,stop_limit.
fee | fee
feeCurrency | charge fee currency
stop |  stop type, include entry and loss
liquidity |  include taker and maker
forceTaker |  forced to become taker, include true and false
createdAt | create time
tradeType | The type of trading : **TRADE**（Spot Trading）, **MARGIN_TRADE** (Margin Trading).


**Data time range**

The system allows you to retrieve data up to one week (start from the last day by default). If the time period of the queried data exceeds one week (time range from the start time to end time exceeded 7*24 hours), the system will prompt to remind you that you have exceeded the time limit. If you only specified the start time, the system will automatically calculate the end time (end time = start time + 7 * 24 hours). On the contrary, if you only specified the end time, the system will calculate the start time (start time= end time - 7 * 24 hours) the same way.

<aside class="notice">The total number of items retrieved cannot exceed 50,000. If it is exceeded, please shorten the query time range.</aside>

**Settlement**

The settlement contains two parts:
- **Transactional settlement**
- **Fee settlement**


After an order is matched, the transactional and fee settlement data will be updated in the data store. Once the data is updated, the system would enable the settlement process and will deduct the fees from your pre-frozen assets. After that, the currency will be transferred to the account of the user.  

**Fees**

Orders on KuCoin platform are classified into two types， taker and maker. A taker order matches other resting orders on the exchange order book, and gets executed immediately after order entry. A maker order, on the contrary, stays on the exchange order book and awaits to be matched. Taker orders will be charged taker fees, while maker orders will receive maker rebates. Please note that market orders, iceberg orders and hidden orders are always charged taker fees.

The system will pre-freeze a predicted taker fee when you place an order.The liquidity field indicates if the fill was charged taker or maker fees.

With the leading matching engine system in the market, users placing orders on KuCoin platform are classified into two types: **taker** and **maker**. **Taker**s, as the taker in the market, would be charged with taker fees; while **maker**s as the maker in the market, would be charged with less fees than the taker, or even get maker fees from KuCoin （The exchange platform would compensate the transaction fees for you）.

After placing orders on the KuCoin platform, to ensure the execution of these orders, the system would pre-freeze your assets based on the taker fee charges (because the system could not predict the order types you may choose). Please be noted that the system would deduct the fees from the orders entered the orderbook in advance.

If your order is market order, the system would charge taker fees from you.

If your order is limit order and is immediately matched and executed, the system would charge **taker fees** from you. On the contrary, if the order or part or your order is not executed immediately and enters into the order book, the system would charge **maker** **fees** from you if it is executed before being cancelled

After the order is executed and when the left order funds is **0**, the transaction is completed. If the remaining funds is not sufficient to support the minimum product (min.: 0.00000001), then the left part in the order would be cancelled.

If your order is a maker order, the system would return the left pre-frozen **taker** fees to you.

Notice:

- For a **hidden**/**iceberg** order, if it is not executed immediately and becomes a maker order, the system would still charge **taker fees** from you.
- Post Only order will charge you maker fees. If a post only order would get executed immediately against the existing orders (except iceberg and hidden orders) in the market, the order will be cancelled. If the post only order will execute against an iceberg/hidden order immediately, you will get the maker fees.




For example:

Take **BTC/USDT** as the trading pair, if you plan to buy **1 BTC** in market price, suppose the fee charge is **0.1%** and the data on the order book is as follows:

| Price（USDT） | Size（BTC） | Side |
| ------------- | ----------- | ---- |
| 4200.00       | 0.18412309  | sell |
| 4015.60       | 0.56849308  | sell |
| 4011.32       | 0.24738383  | sell |
| 3995.64       | 0.84738383  | buy  |
| 3988.60       | 0.20484000  | buy  |
| 3983.85       | 1.37584908  | buy  |

 When you placed a buy order in market price, the order would be executed immediately. The transaction detail is as follows:

| Price（USDT） | Size（BTC） | Fee（BTC） |
| ------------- | ----------- | ---------- |
| 4011.32       | 0.24738383  | 0.00024738 |
| 4015.60       | 0.56849308  | 0.00056849 |
| 4200.00       | 0.18312409  | 0.00018312 |




## Recent Fills

```json
{
    "code":"200000",
    "data":[
        {
            "counterOrderId":"5db7ee769797cf0008e3beea",
            "createdAt":1572335233000,
            "fee":"0.946357371456",
            "feeCurrency":"USDT",
            "feeRate":"0.001",
            "forceTaker":true,
            "funds":"946.357371456",
            "liquidity":"taker",
            "orderId":"5db7ee805d53620008dce1ba",
            "price":"9466.8",
            "side":"buy",
            "size":"0.09996592",
            "stop":"",
            "symbol":"BTC-USDT",
            "tradeId":"5db7ee8054c05c0008069e21",
            "tradeType":"MARGIN_TRADE",
            "type":"market"
        },
        {
            "counterOrderId":"5db7ee4b5d53620008dcde8e",
            "createdAt":1572335207000,
            "fee":"0.94625",
            "feeCurrency":"USDT",
            "feeRate":"0.001",
            "forceTaker":true,
            "funds":"946.25",
            "liquidity":"taker",
            "orderId":"5db7ee675d53620008dce01e",
            "price":"9462.5",
            "side":"sell",
            "size":"0.1",
            "stop":"",
            "symbol":"BTC-USDT",
            "tradeId":"5db7ee6754c05c0008069e03",
            "tradeType":"MARGIN_TRADE",
            "type":"market"
        },
        {
            "counterOrderId":"5db69aa4688933000aab8114",
            "createdAt":1572248229000,
            "fee":"1.882148318525",
            "feeCurrency":"USDT",
            "feeRate":"0.001",
            "forceTaker":false,
            "funds":"1882.148318525",
            "liquidity":"maker",
            "orderId":"5db69a9c4e6d020008f03275",
            "price":"9354.5",
            "side":"sell",
            "size":"0.20120245",
            "stop":"",
            "symbol":"BTC-USDT",
            "tradeId":"5db69aa477d8de0008c1efac",
            "tradeType":"MARGIN_TRADE",
            "type":"limit"
        }
    ]
}

```


Request via this endpoint to get a list of 1000 fills in the last 24 hours.


### HTTP REQUEST
`GET /api/v1/limit/fills`

### Example
`GET /api/v1/limit/fills`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### RESPONSES
Field | Description
--------- | -------
symbol | symbol
tradeId | trade id, it is generated by Matching engine.
orderId | Order ID, unique identifier of an order.
counterOrderId | counter order id.
side | transaction direction,include buy and sell.
price |  order price
size |  order quantity
funds | order funds
type | order type,e.g. limit,market,stop_limit.
fee | fee
feeCurrency | charge fee currency
stop |  stop type, include entry and loss
liquidity |  include taker and maker
forceTaker |  forced to become taker, include true and false
createdAt | create time
tradeType | The type of trading : **TRADE**（Spot Trading）, **MARGIN_TRADE** (Margin Trading).



<aside class="spacer4"></aside>
<aside class="spacer2"></aside>

# Stop Order

A stop order is an order to buy or sell the specified amount of cryptos at the last traded price or pre-specified limit price once the order has traded at or through a pre-specified stopPrice. The order will be executed by the highest price first. For orders of the same price, the order will be executed in time priority.

**stop: 'loss'**: Triggers when the last trade price changes to a value at or below the stopPrice.

**stop: 'entry'**: Triggers when the last trade price changes to a value at or above the stopPrice.

The last trade can be found in the latest match message. Note that not all match messages may be received due to dropped messages.

The last trade price is the last price at which an order was filled. This price can be found in the latest match message. Note that not all match messages may be received due to dropped messages.

Note that when triggered, stop orders execute as either market or limit orders, depending on the type.

When placing a stop loss order, the system will not pre-freeze the assets in your account for the order. **When you are going to place a stop market order, we recommend you to specify the funds for the order when trading**.

## Place a new order

```json
{
  "orderId": "vs8hoo8kpkmklv4m0038lql0"
}
```

**Do not include extra spaces in JSON strings in request body.**

### Limitation

The maximum untriggered stop orders for a single trading pair in one account is **20**.

### HTTP Request
`POST /api/v1/stop-order`

### Example
`POST /api/v1/stop-order`

### API KEY PERMISSIONS

This endpoint requires the **"Trade"** permission.

### Request Body Parameters

| Param     | Type   | Description                                                  |
| --------- | ------ | ------------------------------------------------------------ |
| clientOid | String | Unique order id created by users to identify their orders, e.g. UUID. |
| side      | String | **buy** or **sell**                                          |
| symbol    | String | a valid trading symbol code. e.g. ETH-BTC                    |
| type      | String | *[Optional]* **limit** or **market**, the default is **limit** |
| remark    | String | *[Optional]* remark for the order, length cannot exceed 100 utf8 characters |
| stop      | String | *[Optional]* Either **loss** or **entry**, the default is **loss**. Requires stopPrice to be defined. |
| stopPrice | String | Need to be defined if stop is specified.                     |
| stp       | String | *[Optional]* self trade prevention , **CN**, **CO**, **CB** , **DC** (limit order does not support DC) |
| tradeType | String | *[Optional]* The type of trading : **TRADE**（Spot Trade）, **MARGIN_TRADE** (Margin Trade). Default is **TRADE** |

#### LIMIT ORDER PARAMETERS

| Param       | type    | Description                                                  |
| ----------- | ------- | ------------------------------------------------------------ |
| price       | String  | price per base currency                                      |
| size        | String  | amount of base currency to buy or sell                       |
| timeInForce | String  | *[Optional]* **GTC**, **GTT**, **IOC**, or **FOK** (default is **GTC**), read [Time In Force](#time-in-force). |
| cancelAfter | long    | *[Optional]*  cancel after **n** seconds, requires **timeInForce** to be **GTT** |
| postOnly    | boolean | *[Optional]*  Post only flag, invalid when **timeInForce** is **IOC** or **FOK** |
| hidden      | boolean | *[Optional]*  Order will not be displayed in the order book  |
| iceberg     | boolean | *[Optional]*  Only aportion of the order is displayed in the order book |
| visibleSize | String  | *[Optional]*  The maximum visible size of an iceberg order   |


#### MARKET ORDER PARAMETERS

| Param | type   | Description                                               |
| ----- | ------ | --------------------------------------------------------- |
| size  | String | *[Optional]*  Desired amount in base currency             |
| funds | String | *[Optional]*  The desired amount of quote currency to use |

* It is required that you use one of the two parameters, **size** or **funds**.

###RESPONSES

| Field   | Description         |
| ------- | ------------------- |
| orderId | The ID of the order |

A successful order will be assigned an order ID. A successful order is defined as one that has been accepted by the matching engine.

## Cancel an Order

```json
{
  "cancelledOrderIds": [
    "611477889281bc0006d68aea"
  ]
}
```

Request via this endpoint to cancel a single stop order previously placed.

You will receive cancelledOrderIds field once the system has received the cancellation request. The cancellation request will be processed by the matching engine in sequence. To know if the request is processed (successfully or not), you may check the order status or the update message from the pushes.

### HTTP Request
`DELETE /api/v1/stop-order/{orderId}`

### Example
`DELETE /api/v1/stop-order/5bd6e9286d99522a52e458de`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
| Param   | Type   | Description                                       |
| ------- | ------ | ------------------------------------------------- |
| orderId | String | [Order ID](#list-orders), unique ID of the order. |

### RESPONSES
| Field   | Description                      |
| ------- | -------------------------------- |
| cancelledOrderIds | cancelled order ids    |



<aside class="notice">The <b>order ID</b> is the server-assigned order id and not the passed clientOid.</aside>

### CANCEL REJECT

If the order could not be canceled (already filled or previously canceled, etc), then an error response will indicate the reason in the **message** field.

## Cancel Orders

```json
{
  "cancelledOrderIds": [
    "vs8hoo8m4751f5np0032t7gk",
    "vs8hoo8m4758qjjp0037mslk",
    "vs8hoo8prp98qjjp0037q9gb",
    "vs8hoo8prp91f5np00330k6p"
  ]
}
```

Request via this interface to cancel a batch of stop orders.

### HTTP Request
`DELETE /api/v1/stop-order/cancel`

### Example
`DELETE /api/v1/stop-order/cancel?symbol=ETH-BTC&tradeType=TRADE&orderIds=5bd6e9286d99522a52e458de,5bd6e9286d99522a52e458df`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### PARAMETERS
| Parm      | Type   | Decription                                                   |
| --------- | ------ | ------------------------------------------------------------ |
| symbol    | String | [Optional] symbol                                            |
| tradeType | String | [Optional] The type of trading : **TRADE**（Spot Trading）, **MARGIN_TRADE** (Margin Trading). |
| orderIds  | String | [Optional] Comma seperated order IDs.                        |

### RESPONSES
| Field             | Decription          |
| ----------------- | ------------------- |
| cancelledOrderIds | cancelled order ids |

## Get Single Order Info

```json
{
  "id": "vs8hoo8q2ceshiue003b67c0",
  "symbol": "KCS-USDT",
  "userId": "60fe4956c43cbc0006562c2c",
  "status": "NEW",
  "type": "limit",
  "side": "buy",
  "price": "0.01000000000000000000",
  "size": "0.01000000000000000000",
  "funds": null,
  "stp": null,
  "timeInForce": "GTC",
  "cancelAfter": -1,
  "postOnly": false,
  "hidden": false,
  "iceberg": false,
  "visibleSize": null,
  "channel": "API",
  "clientOid": "40e0eb9efe6311eb8e58acde48001122",
  "remark": null,
  "tags": null,
  "orderTime": 1629098781127530345,
  "domainId": "kucoin",
  "tradeSource": "USER",
  "tradeType": "TRADE",
  "feeCurrency": "USDT",
  "takerFeeRate": "0.00200000000000000000",
  "makerFeeRate": "0.00200000000000000000",
  "createdAt": 1629098781128,
  "stop": "loss",
  "stopTriggerTime": null,
  "stopPrice": "10.00000000000000000000"
}
```

Request via this interface to get a stop order information via the order ID.

### HTTP Request
`GET /api/v1/stop-order/{orderId}`

### Example
`GET /api/v1/stop-order/5c35c02703aa673ceec2a168`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### PARAMETERS
| Parm    | Type   | Decription |
| ------- | ------ | ---------- |
| orderId | String | Order ID   |

### RESPONSES
| Field       | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| id          | Order ID, the ID of an order.                                |
| symbol      | Symbol                                                       |
| userId      | User ID                                                      |
| status      | Order status, include **NEW**, **TRIGGERED**                 |
| type        | Order type                                                   |
| side        | transaction direction,include buy and sell                   |
| price       | order price                                                  |
| size        | order quantity                                               |
| funds       | order funds                                                  |
| stp         | self trade prevention                                        |
| timeInForce | time InForce,include GTC,GTT,IOC,FOK                         |
| cancelAfter | cancel orders after n seconds，requires timeInForce to be GTT |
| postOnly    | postOnly                                                     |
| hidden      | hidden order                                                 |
| iceberg     | Iceberg order                                                |
| visibleSize | displayed quantity for iceberg order                         |
| channel     | order source                                                 |
| clientOid   | user-entered order unique mark                               |
| remark      | Remarks                                                      |
| tags        | tag order source                                             |
| orderTime   | Time of place a stop order, accurate to nanoseconds          |
| domainId    | domainId, e.g: kucoin                                        |
| tradeSource | trade source: **USER**（Order by user）, **MARGIN_SYSTEM**（Order by margin system） |
| tradeType   | The type of trading : **TRADE**（Spot Trading）, **MARGIN_TRADE** (Margin Trading). |
| feeCurrency | The currency of the fee                                      |
| takerFeeRate | Fee Rate of taker                                           |
| makerFeeRate | Fee Rate of maker                                           |
| createdAt   | order creation time                                          |
| stop        | Stop order type, include loss and entry                      |
| stopTriggerTime | The trigger time of the stop order                       |
| stopPrice   | stop price                                                   |


## List Stop Orders

```json
{
  "currentPage": 1,
  "pageSize": 50,
  "totalNum": 1,
  "totalPage": 1,
  "items": [
    {
      "id": "vs8hoo8kqjnklv4m0038lrfq",
      "symbol": "KCS-USDT",
      "userId": "60fe4956c43cbc0006562c2c",
      "status": "NEW",
      "type": "limit",
      "side": "buy",
      "price": "0.01000000000000000000",
      "size": "0.01000000000000000000",
      "funds": null,
      "stp": null,
      "timeInForce": "GTC",
      "cancelAfter": -1,
      "postOnly": false,
      "hidden": false,
      "iceberg": false,
      "visibleSize": null,
      "channel": "API",
      "clientOid": "404814a0fb4311eb9098acde48001122",
      "remark": null,
      "tags": null,
      "orderTime": 1628755183702150167,
      "domainId": "kucoin",
      "tradeSource": "USER",
      "tradeType": "TRADE",
      "feeCurrency": "USDT",
      "takerFeeRate": "0.00200000000000000000",
      "makerFeeRate": "0.00200000000000000000",
      "createdAt": 1628755183704,
      "stop": "loss",
      "stopTriggerTime": null,
      "stopPrice": "10.00000000000000000000"
    }
  ]
}
```

Request via this endpoint to get your current untriggered stop order list. Items are paginated and sorted to show the latest first. See the [Pagination](#pagination) section for retrieving additional entries after the first page.

### HTTP REQUEST
`GET /api/v1/stop-order`

### Example
`GET /api/v1/stop-order`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

<aside class="notice">This request is paginated.</aside>


### PARAMETERS

You can pinpoint the results with the following query paramaters.

| Param       | Type   | Description                                                  |
| ----------- | ------ | ------------------------------------------------------------ |
| symbol      | String | *[Optional]* Only list orders for a specific symbol.         |
| side        | String | *[Optional]* **buy** or **sell**                             |
| type        | String | *[Optional]* **limit**, **market**, **limit_stop** or **market_stop** |
| tradeType   | String | The type of trading : **TRADE**（Spot Trading）, **MARGIN_TRADE** (Margin Trading). |
| startAt     | long   | *[Optional]*  Start time (milisecond)                        |
| endAt       | long   | *[Optional]* End time (milisecond)                           |
| currentPage | Int    | *[Optional]* current page                                    |
| orderIds    | String | *[Optional]* comma seperated order ID list                   |
| pageSize    | Int    | *[Optional]* page size                                       |

### RESPONSES

| Field       | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| id          | Order ID, the ID of an order.                                |
| symbol      | Symbol                                                       |
| userId      | User ID                                                      |
| status      | Order status, include **NEW**, **TRIGGERED**                 |
| type        | Order type                                                   |
| side        | transaction direction,include buy and sell                   |
| price       | order price                                                  |
| size        | order quantity                                               |
| funds       | order funds                                                  |
| stp         | self trade prevention                                        |
| timeInForce | time InForce,include GTC,GTT,IOC,FOK                         |
| cancelAfter | cancel orders after n seconds，requires timeInForce to be GTT |
| postOnly    | postOnly                                                     |
| hidden      | hidden order                                                 |
| iceberg     | Iceberg order                                                |
| visibleSize | displayed quantity for iceberg order                         |
| channel     | order source                                                 |
| clientOid   | user-entered order unique mark                               |
| remark      | Remarks                                                      |
| tags        | tag order source                                             |
| orderTime   | Time of place a stop order, accurate to nanoseconds          |
| domainId    | domainId, e.g: kucoin                                             |
| tradeSource | trade source: **USER**（Order by user）, **MARGIN_SYSTEM**（Order by margin system）  |
| tradeType   | The type of trading : **TRADE**（Spot Trading）, **MARGIN_TRADE** (Margin Trading). |
| feeCurrency | The currency of the fee                                      |
| takerFeeRate | Fee Rate of taker                                       |
| makerFeeRate | Fee Rate of maker                                       |
| createdAt   | order creation time                                          |
| stop        | Stop order type, include loss and entry                      |
| stopTriggerTime | The trigger time of the stop order                      |
| stopPrice   | stop price                                                   |


## Get Single Order by clientOid

```json
[
  {
    "id": "vs8hoo8os561f5np0032vngj",
    "symbol": "KCS-USDT",
    "userId": "60fe4956c43cbc0006562c2c",
    "status": "NEW",
    "type": "limit",
    "side": "buy",
    "price": "0.01000000000000000000",
    "size": "0.01000000000000000000",
    "funds": null,
    "stp": null,
    "timeInForce": "GTC",
    "cancelAfter": -1,
    "postOnly": false,
    "hidden": false,
    "iceberg": false,
    "visibleSize": null,
    "channel": "API",
    "clientOid": "2b700942b5db41cebe578cff48960e09",
    "remark": null,
    "tags": null,
    "orderTime": 1629020492834532568,
    "domainId": "kucoin",
    "tradeSource": "USER",
    "tradeType": "TRADE",
    "feeCurrency": "USDT",
    "takerFeeRate": "0.00200000000000000000",
    "makerFeeRate": "0.00200000000000000000",
    "createdAt": 1629020492837,
    "stop": "loss",
    "stopTriggerTime": null,
    "stopPrice": "1.00000000000000000000"
  }
]
```

Request via this interface to get a stop order information via the clientOid.

### HTTP Request
`GET /api/v1/stop-order/queryOrderByClientOid`

### Example
`GET /api/v1/stop-order/queryOrderByClientOid?symbol=BTC-USDT&clientOid=9823jnfda923a`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
| Param     | Type   | Description                                                  |
| --------- | ------ | ------------------------------------------------------------ |
| clientOid | String | Unique order id created by users to identify their orders    |
| symbol    | String | [Optional] Only list orders for a specific symbol.           |

### RESPONSES
| Field       | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| id          | Order ID, the ID of an order.                                |
| symbol      | Symbol                                                       |
| userId      | User ID                                                      |
| status      | Order status, include **NEW**, **TRIGGERED**                 |
| type        | Order type                                                   |
| side        | transaction direction,include buy and sell                   |
| price       | order price                                                  |
| size        | order quantity                                               |
| funds       | order funds                                                  |
| stp         | self trade prevention                                        |
| timeInForce | time InForce,include GTC,GTT,IOC,FOK                         |
| cancelAfter | cancel orders after n seconds，requires timeInForce to be GTT |
| postOnly    | postOnly                                                     |
| hidden      | hidden order                                                 |
| iceberg     | Iceberg order                                                |
| visibleSize | displayed quantity for iceberg order                         |
| channel     | order source                                                 |
| clientOid   | user-entered order unique mark                               |
| remark      | Remarks                                                      |
| tags        | tag order source                                             |
| orderTime   | Time of place a stop order, accurate to nanoseconds          |
| domainId    | domainId, e.g: kucoin                                        |
| tradeSource | trade source: **USER**（Order by user）, **MARGIN_SYSTEM**（Order by margin system） |
| tradeType   | The type of trading : **TRADE**（Spot Trading）, **MARGIN_TRADE** (Margin Trading). |
| feeCurrency | The currency of the fee                                      |
| takerFeeRate | Fee Rate of taker                                           |
| makerFeeRate | Fee Rate of maker                                           |
| createdAt   | order creation time                                          |
| stop        | Stop order type, include loss and entry                      |
| stopTriggerTime | The trigger time of the stop order                       |
| stopPrice   | stop price                                                   |


## Cancel Single Order by clientOid

```json
{
  "cancelledOrderId": "vs8hoo8ksc8mario0035a74n",
  "clientOid": "689ff597f4414061aa819cc414836abd"
}
```

Request via this interface to cancel a stop order via the clientOid.

### HTTP REQUEST
`DELETE /api/v1/stop-order/cancelOrderByClientOid`

### Example
`DELETE /api/v1/stop-order/cancelOrderByClientOid?symbol=BTC-USDT&clientOid=9823jnfda923a`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
| Param     | Type   | Description                                                  |
| --------- | ------ | ------------------------------------------------------------ |
| clientOid | String | Unique order id created by users to identify their orders    |
| symbol    | String | [Optional] Unique order id created by users to identify their orders |

### RESPONSES
| Field            | Description                                               |
| ---------------- | --------------------------------------------------------- |
| cancelledOrderId | Order ID of cancelled order                               |
| clientOid        | Unique order id created by users to identify their orders |


# Market Data

Signature is not required for this part

# Symbols & Ticker

## Get Symbols List(deprecated)
```json
{
    "code": "200000",
    "data": [
        {
            "symbol": "GALAX-USDT",
            "name": "GALA-USDT",
            "baseCurrency": "GALA",// It's not accurate, It should be GALAX instead of GALA
            "quoteCurrency": "USDT",
            "feeCurrency": "USDT",
            "market": "USDS",
            "baseMinSize": "10",
            "quoteMinSize": "0.001",
            "baseMaxSize": "10000000000",
            "quoteMaxSize": "99999999",
            "baseIncrement": "0.0001",
            "quoteIncrement": "0.00001",
            "priceIncrement": "0.00001",
            "priceLimitRate": "0.1",
            "minFunds": "0.1",
            "isMarginEnabled": true,
            "enableTrading": true
        },
        {
            "symbol": "XLM-USDT",
            "name": "XLM-USDT",
            "baseCurrency": "XLM",
            "quoteCurrency": "USDT",
            "feeCurrency": "USDT",
            "market": "USDS",
            "baseMinSize": "0.1",
            "quoteMinSize": "0.01",
            "baseMaxSize": "10000000000",
            "quoteMaxSize": "99999999",
            "baseIncrement": "0.0001",
            "quoteIncrement": "0.000001",
            "priceIncrement": "0.000001",
            "priceLimitRate": "0.1",
            "minFunds": "0.1",
            "isMarginEnabled": true,
            "enableTrading": true
        }
    ]
}
```

Request via this endpoint to get a list of available currency pairs for trading.
If you want to get the market information of the trading symbol, please use [Get All Tickers](#get-all-tickers).

### HTTP REQUEST
`GET /api/v1/symbols`

<aside class="notice">The <code>GET /api/v1/symbols</code> endpoint is deprecated because when the <code>name</code> of trading pairs changes, the <code>baseCurrency</code> in the response also changes, which is not accurate. So it is recommended to use <code>GET /api/v2/symbols</code> endpoint instead</aside>

### Example
`GET /api/v1/symbols`

### PARAMETERS
Param | Type | Mandatory  | Description | 
--------- | ------- | -----------| -----------| 
market | String | No | The [trading market](#get-market-list). | 

### RESPONSES
Field |  Description
--------- | -----------
symbol | unique code of a symbol, it would not change after renaming
name | Name of trading pairs, it would change after renaming
baseCurrency |  Base currency,e.g. BTC.
quoteCurrency |  Quote currency,e.g. USDT.
market |  The [trading market](#get-market-list).
baseMinSize |  The minimum order quantity requried to place an order.
quoteMinSize | The minimum order funds required to place a market order.
baseMaxSize |  The maximum order size required to place an order.
quoteMaxSize | The maximum order funds  required to place a market order.
baseIncrement |The increment of the order size. The value shall be a positive multiple of the baseIncrement.
quoteIncrement | The increment of the funds required to place a market order. The value shall be a positive multiple of the quoteIncrement.
priceIncrement |  The increment of the price required to place a limit order. The value shall be a positive multiple of the priceIncrement.
feeCurrency | The currency of charged fees.
enableTrading |  Available for transaction or not.
isMarginEnabled |  Available for margin or not.
priceLimitRate | Threshold for price portection
minFunds | the minimum spot and margin trading amounts

The `baseMinSize` and `baseMaxSize` fields define the min and max order size. The `priceIncrement` field specifies the min order price as well as the price increment.This also applies to `quote` currency.

The order `price` must be a positive integer multiple of this `priceIncrement` (i.e. if the increment is 0.01, the  0.001 and 0.021 order prices would be rejected).

`priceIncrement` and `quoteIncrement` may be adjusted in the future. We will notify you by email and site notifications before adjustment.

Order Type | Follow the rules of minFunds
--------- | ------- | -----------
Limit Buy |	[Order Amount * Order Price] >= `minFunds`
Limit Sell |	[Order Amount * Order Price] >= `minFunds`
Market Buy |	Order Value >= `minFunds`
Market Sell | [Order Amount * Last Price of Base Currency] >= `minFunds`

Note:

* API market buy orders (by amount) valued at [Order Amount * Last Price of Base Currency] <`minFunds` will be rejected.
* API market sell orders (by value) valued at <`minFunds` will be rejected.
* Take profit and stop loss orders at market or limit prices will be rejected when triggered.

## Get Symbols List

```json
{
    "code": "200000",
    "data": [
        {
            "symbol": "GALAX-USDT",
            "name": "GALA-USDT",
            "baseCurrency": "GALAX",
            "quoteCurrency": "USDT",
            "feeCurrency": "USDT",
            "market": "USDS",
            "baseMinSize": "10",
            "quoteMinSize": "0.001",
            "baseMaxSize": "10000000000",
            "quoteMaxSize": "99999999",
            "baseIncrement": "0.0001",
            "quoteIncrement": "0.00001",
            "priceIncrement": "0.00001",
            "priceLimitRate": "0.1",
            "minFunds": "0.1",
            "isMarginEnabled": true,
            "enableTrading": true
        },
        {
            "symbol": "XLM-USDT",
            "name": "XLM-USDT",
            "baseCurrency": "XLM",
            "quoteCurrency": "USDT",
            "feeCurrency": "USDT",
            "market": "USDS",
            "baseMinSize": "0.1",
            "quoteMinSize": "0.01",
            "baseMaxSize": "10000000000",
            "quoteMaxSize": "99999999",
            "baseIncrement": "0.0001",
            "quoteIncrement": "0.000001",
            "priceIncrement": "0.000001",
            "priceLimitRate": "0.1",
            "minFunds": "0.1",
            "isMarginEnabled": true,
            "enableTrading": true
        }
    ]
}
```

Request via this endpoint to get a list of available currency pairs for trading.
If you want to get the market information of the trading symbol, please use [Get All Tickers](#get-all-tickers).

### HTTP REQUEST
`GET /api/v2/symbols`

### Example
`GET /api/v2/symbols`

### PARAMETERS
Param | Type | Mandatory  | Description | 
--------- | ------- | -----------| -----------| 
market | String | No | The [trading market](#get-market-list). | 

### RESPONSES
Field |  Description
--------- | -----------
symbol | unique code of a symbol, it would not change after renaming
name | Name of trading pairs, it would change after renaming
baseCurrency |  Base currency,e.g. BTC.
quoteCurrency |  Quote currency,e.g. USDT.
market |  The [trading market](#get-market-list).
baseMinSize |  The minimum order quantity requried to place an order.
quoteMinSize | The minimum order funds required to place a market order.
baseMaxSize |  The maximum order size required to place an order.
quoteMaxSize | The maximum order funds  required to place a market order.
baseIncrement |The increment of the order size. The value shall be a positive multiple of the baseIncrement.
quoteIncrement | The increment of the funds required to place a market order. The value shall be a positive multiple of the quoteIncrement.
priceIncrement |  The increment of the price required to place a limit order. The value shall be a positive multiple of the priceIncrement.
feeCurrency | The currency of charged fees.
enableTrading |  Available for transaction or not.
isMarginEnabled |  Available for margin or not.
priceLimitRate | Threshold for price portection
minFunds | the minimum spot and margin trading amounts

The `baseMinSize` and `baseMaxSize` fields define the min and max order size. The `priceIncrement` field specifies the min order price as well as the price increment.This also applies to `quote` currency.

The order `price` must be a positive integer multiple of this `priceIncrement` (i.e. if the increment is 0.01, the  0.001 and 0.021 order prices would be rejected).

`priceIncrement` and `quoteIncrement` may be adjusted in the future. We will notify you by email and site notifications before adjustment.

Order Type | Follow the rules of minFunds
--------- | ------- | -----------
Limit Buy |	[Order Amount * Order Price] >= `minFunds`
Limit Sell |	[Order Amount * Order Price] >= `minFunds`
Market Buy |	Order Value >= `minFunds`
Market Sell | [Order Amount * Last Price of Base Currency] >= `minFunds`

Note:

* API market buy orders (by amount) valued at [Order Amount * Last Price of Base Currency] <`minFunds` will be rejected.
* API market sell orders (by value) valued at <`minFunds` will be rejected.
* Take profit and stop loss orders at market or limit prices will be rejected when triggered.

## Get Ticker

```json
//Get Ticker
{
    "sequence": "1550467636704",
    "bestAsk": "0.03715004",
    "size": "0.17",
    "price": "0.03715005",
    "bestBidSize": "3.803",
    "bestBid": "0.03710768",
    "bestAskSize": "1.788",
    "time": 1550653727731
}
```

Request via this endpoint to get Level 1 Market Data. The returned value includes the best bid price and size, the best ask price and size as well as the last traded price and the last traded size.

### HTTP REQUEST
`GET /api/v1/market/orderbook/level1`


### Example
`GET /api/v1/market/orderbook/level1?symbol=BTC-USDT`

### PARAMETERS

Param | Type | Description
--------- | ------- | -----------
symbol | String |[symbol](#get-symbols-list)


### RESPONSES
Field |  Description
--------- | -----------
sequence | Sequence
bestAsk |  Best ask price
size | Last traded size
price |  Last traded price
bestBidSize | Best bid size
bestBid | Best bid price
bestAskSize |  Best ask size
time |  timestamp



<aside class="spacer2"></aside>


## Get All Tickers

```json
{
    "time":1602832092060,
    "ticker":[
        {
            "symbol": "BTC-USDT",	// symbol
            "symbolName":"BTC-USDT", // Name of trading pairs, it would change after renaming
            "buy": "11328.9",	// bestAsk
            "sell": "11329",	// bestBid
            "changeRate": "-0.0055",	// 24h change rate
            "changePrice": "-63.6",	// 24h change price
            "high": "11610",	// 24h highest price
            "low": "11200",	// 24h lowest price
            "vol": "2282.70993217",	// 24h volume，the aggregated trading volume in BTC
            "volValue": "25984946.157790431",	// 24h total, the trading volume in quote currency of last 24 hours
            "last": "11328.9",	// last price
            "averagePrice": "11360.66065903",	// 24h average transaction price yesterday
            "takerFeeRate": "0.001",	// Basic Taker Fee
            "makerFeeRate": "0.001",	// Basic Maker Fee
            "takerCoefficient": "1",	// Taker Fee Coefficient
            "makerCoefficient": "1"	// Maker Fee Coefficient
        }
    ]
}
```

Request market tickers for all the trading pairs in the market (including 24h volume).

On the rare occasion that we will change the currency name, if you still want the changed symbol name, you can use the symbolName field instead of the symbol field via “Get all tickers” endpoint.

### HTTP REQUEST
`GET /api/v1/market/allTickers`

### PARAMETERS
`N/A`

### RESPONSES
Field |  Description
--------- | -----------
time |  timestamp
symbol | Symbol
symbolName | Name of trading pairs, it would change after renaming
buy |  Best bid price
sell | Best ask price
changeRate |  24h change rate
changePrice | 24h change price
high | Highest price in 24h
low |  Lowest price in 24h
vol | 24h volume, executed based on base currency
volValue | 24h traded amount
last | Last traded price
averagePrice | Average trading price in the last 24 hours
takerFeeRate | Basic Taker Fee
makerFeeRate | Basic Maker Fee
takerCoefficient | Taker Fee Coefficient
makerCoefficient | Maker Fee Coefficient
<aside class="spacer2"></aside>

## Get 24hr Stats

```json
//Get 24hr Stats
{
    "time": 1602832092060,	// time
    "symbol": "BTC-USDT",	// symbol
    "buy": "11328.9",	// bestAsk
    "sell": "11329",	// bestBid
    "changeRate": "-0.0055",	// 24h change rate
    "changePrice": "-63.6",	// 24h change price
    "high": "11610",	// 24h highest price
    "low": "11200",	// 24h lowest price
    "vol": "2282.70993217",	// 24h volume，the aggregated trading volume in BTC
    "volValue": "25984946.157790431",	// 24h total, the trading volume in quote currency of last 24 hours
    "last": "11328.9",	// last price
    "averagePrice": "11360.66065903",	// 24h average transaction price yesterday
    "takerFeeRate": "0.001",	// Basic Taker Fee
    "makerFeeRate": "0.001",	// Basic Maker Fee
    "takerCoefficient": "1",	// Taker Fee Coefficient
    "makerCoefficient": "1"	// Maker Fee Coefficient
}
```

Request via this endpoint to get the statistics of the specified ticker in the last 24 hours.

### HTTP REQUEST
`GET /api/v1/market/stats`

### Example
`GET /api/v1/market/stats?symbol=BTC-USDT`

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
symbol | String | [symbol](#get-symbols-list)


### RESPONSES
Field |  Description
--------- | -----------
time |  timestamp
symbol | Symbol
buy |  Best bid price
sell | Best ask price
changeRate |  24h change rate
changePrice | 24h change price
high | Highest price in 24h
low |  Lowest price in 24h
vol | 24h volume, executed based on base currency
volValue | 24h traded amount
last | Last traded price
averagePrice | Average trading price in the last 24 hours
takerFeeRate | Basic Taker Fee
makerFeeRate | Basic Maker Fee
takerCoefficient | Taker Fee Coefficient
makerCoefficient | Maker Fee Coefficient
<aside class="spacer2"></aside>

## Get Market List

```json
//Get Market List
{
  "data" : [
    "USDS", //SC has been changed to USDS
    "BTC",
    "KCS",
    "ALTS", //ALTS market includes ETH, NEO, TRX
    "NFT-ETF",
    "FIAT",
    "DeFi",
    "NFT",
    "Metaverse",
    "Polkadot",
    "ETF"
  ],
  "code" : "200000"
}
```

Request via this endpoint to get the transaction currency for the entire trading market.

<aside class="notice">SC has been changed to USDS, but you can still use SC as a query parameter</aside>
<aside class="notice">The three markets of ETH, NEO and TRX are merged into the ALTS market. You can query the trading pairs of the ETH, NEO and TRX markets through the ALTS trading area.</aside>

### HTTP REQUEST
`GET /api/v1/markets`

### Example
`GET /api/v1/markets`

### PARAMETERS
`N/A`


<aside class="spacer2"></aside>

# Order Book

## Get Part Order Book(aggregated)

```json
{
    "sequence": "3262786978",
    "time": 1550653727731,
    "bids": [["6500.12", "0.45054140"],
             ["6500.11", "0.45054140"]],  //[price，size]
    "asks": [["6500.16", "0.57753524"],
             ["6500.15", "0.57753524"]]   
}
```

Request via this endpoint to get a list of open orders for a symbol.

Level-2 order book includes all bids and asks (aggregated by price), this level returns only one size for each active price (as if there was only a single order for that price).

Query via this endpoint and the system will return only part of the order book to you. If you request level2_20, the system will return you 20 pieces of data (ask and bid data) on the order book. If you request level_100, the system will return 100 pieces of data (ask and bid data) on the order book to you. You are recommended to request via this endpoint as the system reponse would be faster and cosume less traffic.


To maintain up-to-date Order Book, please use [Websocket](#level-2-market-data) incremental feed after retrieving the Level 2 snapshot.



### HTTP REQUEST
`GET /api/v1/market/orderbook/level2_20`<br/>
`GET /api/v1/market/orderbook/level2_100`

### Example
`GET /api/v1/market/orderbook/level2_20?symbol=BTC-USDT`<br/>
`GET /api/v1/market/orderbook/level2_100?symbol=BTC-USDT`

### PARAMETERS

Param | Type | Description
--------- | ------- | -----------
symbol | String | [symbol](#get-symbols-list)

### RESPONSES

Field |  Description
--------- | -----------
sequence | Sequence number
time | Timestamp
bids | bids
asks | asks

### Data Sort

**Asks**: Sort price from low to high

**Bids**: Sort price from high to low

## Get Full Order Book(aggregated)

```json
{
    "sequence": "3262786978",
    "time": 1550653727731,
    "bids": [["6500.12", "0.45054140"],
             ["6500.11", "0.45054140"]],  //[price，size]
    "asks": [["6500.16", "0.57753524"],
             ["6500.15", "0.57753524"]]  
}
```

Request via this endpoint to get the order book of the specified symbol.

Level 2 order book includes all bids and asks (aggregated by price). This level returns only one aggregated size for each price (as if there was only one single order for that price).

This API will return data with **full** depth.

It is generally used by professional traders because it uses more server resources and traffic, and we have strict access frequency control.

To maintain up-to-date Order Book, please use [Websocket](#level-2-market-data) incremental feed after retrieving the Level 2 snapshot.


### HTTP REQUEST
`GET /api/v3/market/orderbook/level2`(Recommend)

### Example
`GET /api/v3/market/orderbook/level2?symbol=BTC-USDT`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### REQUEST RATE LIMIT
This API is restricted for each account, the request rate limit is **30 times/3s**.

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
symbol | String | [symbol](#get-symbols-list)

### RESPONSES
Field |  Description
--------- | -----------
sequence | Sequence number
time | Timestamp
bids | bids
asks | asks

### Data Sor

**Asks**: Sort price from low to high

**Bids**: Sort price from high to low

<aside class="spacer4"></aside>

# Histories

## Get Trade Histories

```json
[
    {
        "sequence": "1545896668571",
        "price": "0.07",                      //Filled price
        "size": "0.004",                      //Filled amount
        "side": "buy",                        //Filled side. The filled side is set to the taker by default.
        "time": 1545904567062140823           //Transaction time
    },
    {
        "sequence": "1545896668578",
        "price": "0.054",
        "size": "0.066",
        "side": "buy",
        "time": 1545904581619888405
    }
]
```
Request via this endpoint to get the trade history of the specified symbol.


### HTTP REQUEST
`GET /api/v1/market/histories`

### Example
`GET /api/v1/market/histories?symbol=BTC-USDT`

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
symbol | String | [symbol](#get-symbols-list)

### RESPONSES
Field |  Description
--------- | -----------
sequence | Sequence number
time | Transaction time
price | Filled price
size |  Filled amount
side | Filled side. The filled side is set to the taker by default


###SIDE
The trade side indicates the taker order side. A taker order is the order that was matched with orders opened on the order book.

<aside class="spacer2"></aside>

## Get Klines

```json
[
    [
        "1545904980",             //Start time of the candle cycle
        "0.058",                  //opening price
        "0.049",                  //closing price
        "0.058",                  //highest price
        "0.049",                  //lowest price
        "0.018",                  //Transaction volume
        "0.000945"                //Transaction amount
    ],
    [
        "1545904920",
        "0.058",
        "0.072",
        "0.072",
        "0.058",
        "0.103",
        "0.006986"
    ]
]
```
Request via this endpoint to get the kline of the specified symbol. Data are returned in grouped buckets based on requested type.


<aside class="notice"> Klines data may be incomplete. No data is published for intervals where there are no ticks.</aside>

<aside class="warning"> Klines should not be polled frequently. If you need real-time information, use the trade and book endpoints along with the websocket feed.</aside>

### HTTP REQUEST
`GET /api/v1/market/candles`

### Example
`GET /api/v1/market/candles?type=1min&symbol=BTC-USDT&startAt=1566703297&endAt=1566789757`

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
symbol | String | [symbol](#get-symbols-list)
startAt| long | *[Optional]*  Start time (second), default is 0
endAt| long | *[Optional]* End time (second), default is 0
type | String |Type of candlestick patterns: **1min, 3min, 5min, 15min, 30min, 1hour, 2hour, 4hour, 6hour, 8hour, 12hour, 1day, 1week**

<aside class="notice">For each query, the system would return at most **1500** pieces of data. To obtain more data, please page the data by time.</aside>

### RESPONSES
Field |  Description
--------- | -----------
time | Start time of the candle cycle
open |  Opening price
close | Closing price
high | Highest price
low | Lowest price
volume |Transaction volume
turnover | Transaction amount



# Currencies


## Get Currencies

```json
[
  {
    "currency": "CSP",
    "name": "CSP",
    "fullName": "Caspian",
    "precision": 8,
    "confirms": 12,
    "contractAddress": "0xa6446d655a0c34bc4f05042ee88170d056cbaf45",
    "withdrawalMinSize": "2000",
    "withdrawalMinFee": "1000",
    "isWithdrawEnabled": true,
    "isDepositEnabled": true,
    "isMarginEnabled": false,
    "isDebitEnabled": false
  },
  {
    "currency": "LOKI",
    "name": "OXEN",
    "fullName": "Oxen",
    "precision": 8,
    "confirms": 10,
    "contractAddress": "",
    "withdrawalMinSize": "2",
    "withdrawalMinFee": "2",
    "isWithdrawEnabled": true,
    "isDepositEnabled": true,
    "isMarginEnabled": false,
    "isDebitEnabled": true
  }
]
```

Request via this endpoint to get the currency list.

<aside class="notice">Not all currencies currently can be used for trading.</aside>


### HTTP REQUEST
`GET /api/v1/currencies`

### Example
`GET /api/v1/currencies`

### RESPONSES
|Field | Description|
|-----|-------------|
|currency| A unique currency code that will never change|
|name| Currency name, will change after renaming|
|fullName| Full name of a currency, will change after renaming |
|precision| Currency precision |
|confirms| Number of block confirmations |
|contractAddress| Contract address |
|withdrawalMinSize| Minimum withdrawal amount |
|withdrawalMinFee|  Minimum fees charged for withdrawal |
|isWithdrawEnabled| Support withdrawal or not |
|isDepositEnabled| Support deposit or not |
|isMarginEnabled| Support margin or not |
|isDebitEnabled| Support debit or not |


**CURRENCY CODES**

Currency codes will conform to the ISO 4217 standard where possible. Currencies which have or had no representation in ISO 4217 may use a custom code.

Code | Description
--------- | -------  
BTC | Bitcoin
ETH | Ethereum
KCS | Kucoin Shares

For a coin, the "**currency**" is a fixed value and works as the only recognized identity of the coin. As the "**name**", "**fullnane**" and "**precision**" of a coin are modifiable values, when the "**name**" of a coin is changed, you should use "**currency**" to get the coin.

For example:

The "**currency**" of XRB is "XRB", if the "**name**" of XRB is changed into "**Nano**", you should use "XRB" (the currency of XRB) to search the coin.

## Get Currency Detail
```json
{
  "currency": "BTC",
  "name": "BTC",
  "fullName": "Bitcoin",
  "precision": 8,
  "confirms": 2,
  "contractAddress": "",
  "withdrawalMinSize": "0.001",
  "withdrawalMinFee": "0.0006",
  "isWithdrawEnabled": true,
  "isDepositEnabled": true,
  "isMarginEnabled": true,
  "isDebitEnabled": true
}
```
Request via this endpoint to get the currency details of a specified currency

### HTTP REQUEST
`GET /api/v1/currencies/{currency}`

### Example
`GET /api/v1/currencies/BTC`

<aside class="notice">Details of the currency.</aside>

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
currency | String | **Path parameter**. [Currency](#get-currencies)
chain | String | *[Optional]* Support for querying the chain of currency, e.g. The available value for USDT are OMNI, ERC20, TRC20. This only apply for multi-chain currency, and there is no need for single chain currency.

### RESPONSES
|Field | Description|
|-----|-------------|
|currency| A unique currency code that will never change|
|name| Currency name, will change after renaming |
|fullName| Full name of a currency, will change after renaming |
|precision| Currency precision |
|confirms| Number of block confirmations|
|contractAddress| Contract address|
|withdrawalMinSize| Minimum withdrawal amount |
|withdrawalMinFee| Minimum fees charged for withdrawal |
|isWithdrawEnabled| Support withdrawal or not |
|isDepositEnabled| Support deposit or not |
|isMarginEnabled| Support margin or not |
|isDebitEnabled| Support debit or not |

## Get Currency Detail(Recommend)
```json
{
    "code": "200000",
    "data": {
        "currency": "BTC",
        "name": "BTC",
        "fullName": "Bitcoin",
        "precision": 8,
        "confirms": null,
        "contractAddress": null,
        "isMarginEnabled": true,
        "isDebitEnabled": true,
        "chains": [
            {
                "chainName": "BTC",
                "chain": "btc",
                "withdrawalMinSize": "0.001",
                "withdrawalMinFee": "0.0005",
                "isWithdrawEnabled": true,
                "isDepositEnabled": true,
                "confirms": 2,
                "contractAddress": ""
            },
            {
                "chainName": "KCC",
                "chain": "kcc",
                "withdrawalMinSize": "0.0008",
                "withdrawalMinFee": "0.00002",
                "isWithdrawEnabled": true,
                "isDepositEnabled": true,
                "confirms": 20,
                "contractAddress": ""
            },
            ...
        ]
    }
}
```
Request via this endpoint to get the currency details of a specified currency

### HTTP REQUEST
`GET /api/v2/currencies/{currency}`

### Example
`GET /api/v2/currencies/BTC`

<aside class="notice">Recommended for use</aside>

### PARAMETERS
Param | Type | Description
--------- | ------- | -----------
currency | String | **Path parameter**. [Currency](#get-currencies)
chain | String | *[Optional]* Support for querying the chain of currency, return the currency details of all chains by default.

### RESPONSES
|Field | Description|
|-----|-------------|
|currency| A unique currency code that will never change|
|name| Currency name, will change after renaming |
|fullName| Full name of a currency, will change after renaming |
|precision| Currency precision |
|confirms| Number of block confirmations|
|contractAddress| Contract address|
|withdrawalMinSize| Minimum withdrawal amount |
|chainName| chain name of currency |
|chain| chain of currency |
|withdrawalMinFee| Minimum fees charged for withdrawal |
|isWithdrawEnabled| Support withdrawal or not |
|isDepositEnabled| Support deposit or not |
|isMarginEnabled| Support margin or not |
|isDebitEnabled| Support debit or not |

## Get Fiat Price
```json
{
    "code": "200000",
    "data": {
        "BTC": "3911.28000000",
        "ETH": "144.55492453",
        "LTC": "48.45888179",
        "KCS": "0.45546856"
    }
}
```
Request via this endpoint to get the fiat price of the currencies for the available trading pairs.  

### HTTP REQUEST
`GET /api/v1/prices`

### Example
`GET /api/v1/prices`

### PARAMETERS
|Param | Type | Description|
|--------- | ------- | -----------|
| base | String |*[Optional]* Ticker symbol of a base currency,eg.USD,EUR. Default is USD |
| currencies | String |*[Optional]* Comma-separated cryptocurrencies to be converted into fiat, e.g.: BTC,ETH, etc. Default to return the fiat price of all currencies.|


# Margin

# Margin Info

## Get Mark Price
```json
{
    "code": "200000",
    "data": {
        "symbol": "USDT-BTC",
        "timePoint": 1659930234000,
        "value": 0.0000429
    }
}
```

Request via this endpoint to get the index price of the specified symbol.

### HTTP REQUEST
`GET /api/v1/mark-price/{symbol}/current`

### Example
`GET /api/v1/mark-price/USDT-BTC/current`

### PARAMETERS
|Param | Type | Description|
|--------- | ------- | -----------|
| symbol | String | **Path parameter.** [symbol](#get-symbols-list) |

#### List of currently supported symbol
<aside class="notice">USDT-BTC, ETH-BTC, LTC-BTC, EOS-BTC, XRP-BTC, KCS-BTC, DIA-BTC, VET-BTC, DASH-BTC, DOT-BTC, XTZ-BTC, ZEC-BTC, BSV-BTC, ADA-BTC, ATOM-BTC, LINK-BTC, LUNA-BTC, NEO-BTC, UNI-BTC, ETC-BTC, BNB-BTC, TRX-BTC, XLM-BTC, BCH-BTC, USDC-BTC, GRT-BTC, 1INCH-BTC, AAVE-BTC,SNX-BTC, API3-BTC, CRV-BTC, MIR-BTC, SUSHI-BTC, COMP-BTC, ZIL-BTC, YFI-BTC, OMG-BTC,XMR-BTC, WAVES-BTC, MKR-BTC, COTI-BTC, SXP-BTC, THETA-BTC, ZRX-BTC, DOGE-BTC, LRC-BTC, FIL-BTC, DAO-BTC, BTT-BTC, KSM-BTC, BAT-BTC, ROSE-BTC, CAKE-BTC, CRO-BTC, XEM-BTC, MASK-BTC, FTM-BTC, IOST-BTC, ALGO-BTC, DEGO-BTC, CHR-BTC, CHZ-BTC, MANA-BTC, ENJ-BTC, IOST-BTC, ANKR-BTC, ORN-BTC, SAND-BTC, VELO-BTC, AVAX-BTC, DODO-BTC, WIN-BTC, ONE-BTC, SHIB-BTC, ICP-BTC, MATIC-BTC, CKB-BTC, SOL-BTC, VRA-BTC, DYDX-BTC, ENS-BTC, NEAR-BTC, SLP-BTC, AXS-BTC, TLM-BTC, ALICE-BTC,IOTX-BTC, QNT-BTC, SUPER-BTC, HABR-BTC, RUNE-BTC, EGLD-BTC, AR-BTC, RNDR-BTC, LTO-BTC, YGG-BTC</aside>

### RESPONSES
|Field        | Description                    |
|------------ |--------------------------------|
| symbol      | symbol                         |
| timePoint   | Time (millisecond)             |
| value       | Mark price    |

## Get Margin Configuration Info
```json
{
    "code": "200000",
    "data": {
        "currencyList": [
            "XEM",
            "MATIC",
            "VRA",
            ...
        ],
        "maxLeverage": 5,
        "warningDebtRatio": "0.95",
        "liqDebtRatio": "0.97"
    }
}
```
Request via this endpoint to get the configure info of the margin.

### HTTP REQUEST
`GET /api/v1/margin/config`

### Example
`GET /api/v1/margin/config`

### PARAMETERS
`N/A`

### RESPONSES
|Field | Description|
|----- |-------------|
| currencyList | Available currencies for margin trade |
| warningDebtRatio | The warning debt ratio of the forced liquidation |
| liqDebtRatio | The debt ratio of the forced liquidation |
| maxLeverage | Max leverage available |

## Get Margin Account（Deprecate）
```json
{
    "code": "200000",
    "data": {
        "debtRatio": "0",
        "accounts": [
            {
                "currency": "KCS",
                "totalBalance": "0.01",
                "availableBalance": "0.01",
                "holdBalance": "0",
                "liability": "0",
                "maxBorrowSize": "0"
            },
            {
                "currency": "USDT",
                "totalBalance": "0",
                "availableBalance": "0",
                "holdBalance": "0",
                "liability": "0",
                "maxBorrowSize": "0"
            },
            ...
        ]
    }
}
```
Request via this endpoint to get the info of the margin account.

### HTTP REQUEST
`GET /api/v1/margin/account`

### Example
`GET /api/v1/margin/account`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### RESPONSES
|Field | Description|
|----- |-------------|
| accounts | Margin account list |
| debtRatio | Debt ratio |
| currency | Currency |
| totalBalance | Total funds in the account |
| availableBalance | Available funds in the account |
| holdBalance | Funds on hold in the account |
| liability | Total liabilities |
| maxBorrowSize | Available size to borrow |

## Query the cross/isolated margin risk limit（Deprecate）
```json
// CROSS MARGIN RESPONSES
{
    "code": "200000",
    "data": [
        {
            "currency": "BTC",
            "borrowMaxAmount": "140",
            "buyMaxAmount": "60",
            "holdMaxAmount": "522.8",
            "precision": 8
        },
        {
            "currency": "USDT",
            "borrowMaxAmount": "2000000",
            "buyMaxAmount": "10000000",
            "holdMaxAmount": "15000000",
            "precision": 8
        },
        {
            "currency": "ETH",
            "borrowMaxAmount": "1000",
            "buyMaxAmount": "600",
            "holdMaxAmount": "3737.1",
            "precision": 8
        },
        ...
    ]
}
```
```json
// ISOLATED MARGIN RESPONSES
{
    "code": "200000",
    "data": [
        {
            "symbol": "ETH-USDT",
            "baseMaxBorrowAmount": "200",
            "quoteMaxBorrowAmount": "3000000",
            "baseMaxBuyAmount": "210",
            "quoteMaxBuyAmount": "3300000",
            "baseMaxHoldAmount": "3737.1",
            "quoteMaxHoldAmount": "5000000",
            "basePrecision": 8,
            "quotePrecision": 8
        },
        {
            "symbol": "BTC-USDT",
            "baseMaxBorrowAmount": "20",
            "quoteMaxBorrowAmount": "3000000",
            "baseMaxBuyAmount": "25",
            "quoteMaxBuyAmount": "3300000",
            "baseMaxHoldAmount": "522.8",
            "quoteMaxHoldAmount": "5000000",
            "basePrecision": 8,
            "quotePrecision": 8
        },
        ...
    ]
}
```
This endpoint can query the cross/isolated margin risk limit. 

### HTTP REQUEST
`GET /api/v1/risk/limit/strategy`

### Example
`GET /api/v1/risk/limit/strategy?marginModel=cross`

### API KEY PERMISSIONS
This endpoint requires the `General` permission.

### REQUEST RATE LIMIT

This API is restricted for each account, the request rate limit is `1 times/3s`.

### PARAMETERS
|Param | Type | Description|
|--------- | ------- | -----------|
| marginModel | String | The type of marginModel : `cross`（cross margin）, `isolated` (isolated margin). Default is `cross`.  |

### CROSS MARGIN RESPONSES
|Field | Description|
|----- |-------------|
| currency | Currency |
| borrowMaxAmount | Maximum borrow amount  |
| buyMaxAmount | Maximum buy amount  |
| holdMaxAmount | Maximum hold amount  |
| precision | Precision  |

### ISOLATED MARGIN RESPONSES
|Field | Description|
|----- |-------------|
| symbol | The valid trading symbol code. e.g: EOS-USDC. |
| baseMaxBorrowAmount | Maximum borrowing amount of base currency|
| quoteMaxBorrowAmount |Maximum borrowing amount of quote currency|
| baseMaxBuyAmount | Maximum buy amount of base currency|
| quoteMaxBuyAmount | Maximum buy amount of quote currency|
| baseMaxHoldAmount | Maximum holding amount of base currency |
| quoteMaxHoldAmount | Maximum holding amount of quote currency |
| basePrecision | Base currency precision |
| quotePrecision | Quote currency precision|

## Query Margin Trading Pairs
```json 
{
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": {
        "timestamp": 1669709339758,
        "items": [
            {
                "symbol": "BTC-USDT",
                "name": "BTC-USDT",
                "enableTrading": true,
                "market": "USDS",
                "baseCurrency": "BTC",
                "quoteCurrency": "USDT",
                "baseIncrement": "0.00000001",
                "baseMinSize": "0.00000001",
                "quoteIncrement": "0.000001",
                "quoteMinSize": "0.000001",
                "baseMaxSize": "10000000000",
                "quoteMaxSize": "99999999",
                "priceIncrement": "0.00000001",
                "feeCurrency": "USDT",
                "priceLimitRate": "1",
                "minFunds": "0.000001"
            }
        ]
    }
}
```
### HTTP REQUEST
 `GET /api/v2/margin/symbols`

### Example
`GET /api/v2/margin/symbols?isIsolated=True&symbol=KCS-USDT`

### API KEY PERMISSIONS
This API endpoint requires the `General` permission..

### PARAMETERS
| Param      | Type    | Description                                              |
| ---------- | ------- | -------------------------------------------------------- |
| isIsolated | Boolean | true-Isolated margin, false-Cross margin; default: false |
| symbol     | STRING  | Trading pair                                             |

### RESPONSES
| Field          | Description                                                                                                           |
| -------------- | --------------------------------------------------------------------------------------------------------------------- |
| symbol         | Trading pair unique identifier                                                                                        |
| name           | Trading pair name. Changes when renamed.                                                                              |
| baseCurrency   | Refers to the asset traded (the asset written first in the trading pair)                                              |
| quoteCurrency  | The coin used to determine the value of the traded asset (the asset written second in the trading pair)               |
| market         | The marketplace                                                                                                       |
| baseMinSize    | The minimum size when placing an order.                                                                               |
| quoteMinSize   | The minimum value when placing a market order.                                                                        |
| baseMaxSize    | The maximum size when placing an order.                                                                               |
| quoteMaxSize   | The maximum value when placing an order.                                                                              |
| baseIncrement  | The amount the size can be increased by. The size of the order must be a multiple of the baseIncrement.               |
| quoteIncrement | Market Orders: the amount the quote can be increased by. The quote of the order must be a multiple of quoteIncrement. |
| priceIncrement | Limit Orders: the amount the price can be increased by. The price of the order must be a multiple of priceIncrement.  |
| feeCurrency    | The currency trading fees are calculated in.                                                                          |
| enableTrading  | Whether or not trading is enabled                                                                                     |
| priceLimitRate | The price protection threshold.                                                                                       |
| minFunds       | Minimum transaction amount                                                                                            |

# Borrow & Lend

## Post Borrow Order （Deprecate）
```json
{
    "orderId": "a2111213",
    "currency": "USDT"
}
```

### HTTP REQUEST
`POST /api/v1/margin/borrow`

### Example
`POST /api/v1/margin/borrow`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description|
|--------- | ------- | -----------|
| currency | String | Currency to Borrow |
| type | String | Type: FOK, IOC |
| size | BigDecimal | Total size |
| maxRate | BigDecimal | *[Optional]* The max interest rate. All interest rates are acceptable if this field is left empty.|
| term | String | *[Optional]* Term (Unit: Day). All terms are acceptable if this field is left empty. Please note to separate the terms via comma. For example, 7,14,28.|


<aside class="notice">Available terms currently supported: 7, 14, 28</aside>

### RESPONSES
|Field | Description|
|----- |-------------|
| orderId | Borrow order ID |
| currency | Currency to borrow  |

## Get Borrow Order
```json
{
    "orderId": "a2111213",
    "currency": "USDT",
    "size": "1.009",
    "filled": 1.009,
    "matchList": [
      {
        "currency": "USDT",
        "dailyIntRate": "0.001",
        "size": "12.9",
        "term": 7,
        "timestamp": "1544657947759",
        "tradeId": "1212331"
      }
    ],
    "status": "DONE"
  }

```

Request via this endpoint to get the info of the borrow order through the **orderId** retrieved from [Post Borrow Order](#post-borrow-order) .


### HTTP REQUEST
`GET /api/v1/margin/borrow`

### Example
`GET /api/v1/margin/borrow?orderId=123456789`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description|
|--------- | ------- | -----------|
| orderId | String | Borrow order ID |

### RESPONSES
|Field | Description|
|----- |-------------|
| orderId      | Borrow order ID |
| currency | Currency |
| size | Total size  |
| filled | Size executed |
| status | Status. DONE (Canceled or Filled),PROCESSING |
| matchList | Execution details |
| tradeId | Trade ID| |
| dailyIntRate | Daily interest rate |
| term | Term |
| timestamp | Borrow time|

## Get Repay Record（Deprecate）
```json
{
    "currentPage": 0,
    "pageSize": 0,
    "totalNum": 0,
    "totalPage": 0,
    "items": [
        {
            "tradeId": "1231141",
            "currency": "USDT",
            "accruedInterest": "0.22121",
            "dailyIntRate": "0.0021",
            "liability": "1.32121",
            "maturityTime": "1544657947759",
            "principal": "1.22121",
            "repaidSize": "0",
            "term": 7,
            "createdAt": "1544657947759"
        }
    ]
  }
```


### HTTP REQUEST
`GET /api/v1/margin/borrow/outstanding`

### Example
`GET /api/v1/margin/borrow/outstanding`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

<aside class="notice">This request is paginated.</aside>

### PARAMETERS

|Param | Type | Description|
|--------- | ------- | -----------|
| currency | String |  *[Optional]* Currency. All currencies will be quried if this field is not required. |

### RESPONSES
|Field | Description|
|----- |-------------|
| tradeId | Trade ID |
| currency  | Currency |
| liability | Total liabilities |
| principal | Outstanding principal to repay    |
| accruedInterest | Accrued interest |
| createdAt   | Execution time |
| maturityTime  | Maturity time |
| term       | Term  |
| repaidSize | Repaid size  |
| dailyIntRate | Daily interest rate   |

## Get Repayment Record（Deprecate）
```json
{
    "pageSize": 0,
    "totalNum": 0,
    "totalPage": 0,
    "currentPage": 0,
    "items": [
        {
            "tradeId": "1231141",
            "currency": "USDT",
            "dailyIntRate": "0.0021",
            "interest": "0.22121",
            "principal": "1.22121",
            "repaidSize": "0",
            "repayTime": "1544657947759",
            "term": 7
        }
    ]
  }
```

### HTTP REQUEST
`GET /api/v1/margin/borrow/repaid`

### Example
`GET /api/v1/margin/borrow/repaid`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

<aside class="notice">This request is paginated.</aside>

### PARAMETERS
|Param | Type | Description|
|--------- | ------- | -----------|
| currency | String | *[Optional]* Currency. All currencies will be quried if this field is not required. |

### RESPONSES
|Field | Description|
|----- |-------------|
| tradeId | Trade ID |
| currency       | Currency |
| interest   | Interest |
| principal  | Principal |
| repayTime | Repayment time|
| term   | Term  |
| repaidSize | Repaid size |
| dailyIntRate | Daily interest rate |

## One-Click Repayment（Deprecate）
```json
{
  "code": "200000",
  "data": null
}
```

### HTTP REQUEST
`POST /api/v1/margin/repay/all`

### Example
`POST /api/v1/margin/repay/all`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| currency | String | Currency |
| sequence | String | Repayment strategy. RECENTLY_EXPIRE_FIRST: Time priority, namely to repay the loans of the nearest maturity time first, HIGHEST_RATE_FIRST: Rate Priority: Repay the loans of the highest interest rate first. |
| size | BigDecimal | Repayment size |

### RESPONSES
A successful repayment response is indicated by an HTTP status code 200 and system code 200000. If the system returns other code, it means the repayment fails.

## Repay a Single Order（Deprecate）
```json
{
  "code": "200000",
  "data": null
}
```

Request via this endpoint to repay a single order.


### HTTP REQUEST
`POST /api/v1/margin/repay/single`

### Example
`POST /api/v1/margin/repay/single`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| currency | String | Currncy |
| tradeId | String | Trade ID |
| size | BigDecimal | Repayment size |

### RESPONSES
A successful repayment response is indicated by an HTTP status code 200 and system code 200000. If the system returns other code, it means the repayment fails.

## Post Lend Order
```json
{
	"orderId": "5da5a4f0f943c040c2f8501e"
}
```

Request via this endpoint to post lend order.


Please ensure that you have sufficient funds in your Main Account before you post the order. Once the post succeed, the funds posted will be frozen until the order is succssfuly lent out or cancelled.

### HTTP REQUEST
`POST /api/v1/margin/lend`

### Example
`POST /api/v1/margin/lend`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| currency     | String | Currency to lend   |
| size         | String | Total size     |
| dailyIntRate | String | Daily interest rate. e.g. 0.002 is 0.2% |
| term         | int    | Term (Unit: Day)    |

### RESPONSES
|Field | Description|
|----- |-------------|
| orderId | Lend order ID |

## Cancel Lend Order
```json
{
  "code": "200000",
  "data": null
}
```

Request via this endpoint to cancel lend order.

### HTTP REQUEST
`DELETE /api/v1/margin/lend/{orderId}`

### Example
`DELETE /api/v1/margin/lend/5d9f133ef943c0882ca37bc8`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| orderId  | String | Lend order ID |

## Set Auto-lend
```json
{
  "code": "200000",
  "data": null
}
```

Request via this endpoint to set up the automatic lending for a specified currency.

### HTTP REQUEST
`POST /api/v1/margin/toggle-auto-lend`

### Example
`POST /api/v1/margin/toggle-auto-lend`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| currency     | String  | Currency                                        |
| isEnable     | boolean | Auto-lend enabled or not                                |
| retainSize   | String  | Reserved size in main account. Mandatory when **isEnable** is true.   |
| dailyIntRate | String  | acceptable min. day rate, 0.002 is 0.2%. Mandatory when **isEnable** is true.     |
| term         | int     | Term (Unit: Day). Mandatory when **isEnable** is true.            |

###Advanced Description

###dailyIntRate

When the priority interest rate is higher than the acceptable min. day rate, the system will place lending orders at the rate of the former one. The priority interest rate is the optimal market rate for all pending orders of the selected lending period, orders with this interest rate will be prioritized for auto-lending.

When the priority interest rate is lower than the acceptable min. day rate, the system will place lending orders at the rate of the latter one.

## Get Active Order（Deprecate）
```json
{
	  "currentPage": 1,
	  "pageSize": 1,
	  "totalNum": 1,
	  "totalPage": 1,
	  "items": [
        {
            "orderId": "5da59f5ef943c033b2b643e4",
            "currency": "BTC",
            "size": "0.51",
            "filledSize": "0",
            "dailyIntRate": "0.0001",
            "term": 7,
            "createdAt": 1571135326913
        }
    ]
}
```

Request via this endpoint to get active lend orders. Items are paginated and sorted to show the latest first. See the Pagination section for retrieving additional entries after the first page. The max pageSize is 100.

Active lend orders include orders unfilled, partially filled and uncanceled.

### HTTP REQUEST
`GET /api/v1/margin/lend/active`

### Example
`GET /api/v1/margin/lend/active?currency=BTC&currentPage=1&pageSize=50`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| currency | String | *[Optional]*  Currency |

### RESPONSES
|Field | Description|
|----- |----------------------------------|
| orderId      | Lend order ID           |
| currency     | Currency                |
| size         | Total size            |
| filledSize   | Size executed               |
| dailyIntRate | Daily interest rate. e.g. 0.002 is 0.2% |
| term         | Term (Unit: Day)           |
| createdAt    | Time of the event (millisecond)       |

## Get Lent History（Deprecate）
```json
{
    "currentPage": 1,
    "pageSize": 1,
    "totalNum": 1,
    "totalPage": 1,
    "items": [
        {
            "orderId": "5da59f5bf943c033b2b643da",
            "currency": "BTC",
            "size": "0.51",
            "filledSize": "0.51",
            "dailyIntRate": "0.0001",
            "term": 7,
            "status": "FILLED",
            "createdAt": 1571135323984
        }
    ]
}
```

Request via this endpoint to get lent orders . Items are paginated and sorted to show the latest first. See the Pagination section for retrieving additional entries after the first page. The max pageSize is 100.

Lent order history involves orders canceled or fully filled.

### HTTP REQUEST
`GET /api/v1/margin/lend/done`

### Example
`GET /api/v1/margin/lend/done?currency=BTC&currentPage=1&pageSize=50`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| currency | String | *[Optional]* Currency |

### RESPONSES
|Field | Description|
|----- |----------------------------------|
| orderId      | Lend order ID                     |
| currency     | Currency                          |
| size         | Total size                      |
| filledSize   | Size executed                         |
| dailyIntRate | Daily interest rate. e.g. 0.002 is 0.2%    |
| term         | Term (Unit: Day)                     |
| createdAt    | Time of the event (millisecond)      |
| status       | Order status: FILLED -- Fully filled, CANCELED -- Canceled |

## Get Active Lend Order List（Deprecate）
```json
{
    "currentPage": 1,
    "pageSize": 1,
    "totalNum": 1,
    "totalPage": 1,
    "items": [
        {
            "tradeId": "5da6dba0f943c0c81f5d5db5",
            "currency": "BTC",
            "size": "0.51",
            "accruedInterest": "0",
            "repaid": "0.10999968",
            "dailyIntRate": "0.0001",
            "term": 14,
            "maturityTime": 1572425888958
        }
    ]
}
```

Request via this endpoint to get the outstanding lend order list. Items are paginated and sorted to show the latest first. See the Pagination section for retrieving additional entries after the first page. The max pageSize is 100.

When a lending order is executed, the system will generate the lending history. The outstanding lend orders includes orders unrepaid and partially repaid.

### HTTP REQUEST
`GET /api/v1/margin/lend/trade/unsettled`

### Example
`GET /api/v1/margin/lend/trade/unsettled?currency=BTC&currentPage=1&pageSize=50`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| currency | String | *[Optional]* Currency |

### RESPONSES
|Field | Description|
|----- |----------------------------------|
| tradeId         | Trade ID                                             |
| currency        | Currency                                             |
| size            | Size executed                                            |
| accruedInterest | Accrued interest. This value will decrease when borrower repays the interest. |
| repaid          | Repaid size                                          |
| dailyIntRate    | Daily interest rate. e.g. 0.002 is 0.2%              |
| term            | Term (Unit: Day)                                     |
| maturityTime    |  Maturity time  (millisecond)                        |

## Get Settled Lend Order History（Deprecate）
```json
{
    "currentPage": 1,
    "pageSize": 1,
    "totalNum": 1,
    "totalPage": 1,
    "items": [
        {
            "tradeId": "5da59fe6f943c033b2b6440b",
            "currency": "BTC",
            "size": "0.51",
            "interest": "0.00004899",
            "repaid": "0.510041641",
            "dailyIntRate": "0.0001",
            "term": 7,
            "settledAt": 1571216254767,
            "note": "The account of the borrowers reached a negative balance, and the system has supplemented the loss via the insurance fund. Deposit funds: 0.51."
        }
    ]
}
```

Request via this endpoint to get the settled lend orders . Items are paginated and sorted to show the latest first. See the Pagination section for retrieving additional entries after the first page. The max pageSize is 100.

The settled lend orders include orders repaid fully or partially before or at the maturity time.


### HTTP REQUEST
`GET /api/v1/margin/lend/trade/settled`

### Example
`GET /api/v1/margin/lend/trade/settled?currency=BTC&currentPage=1&pageSize=50`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| currency | String | *[Optional]* Currency |

### RESPONSES
|Field | Description|
|----- |----------------------------------|
| tradeId      | Trade ID                                     |
| currency     | Currency                                     |
| size         | Size executed                                    |
| interest     | Total interest                               |
| repaid       | Repaid size                                  |
| dailyIntRate | Daily interest rate. e.g. 0.002 is 0.2%      |
| term         | Term (Unit: Day)                             |
| settledAt    | Settlement time (millisecond)                |
| note         | Note. To note the account of the borrower reached a negative balance, and whether the insurance fund is repaid. |

## Get Account Lend Record
```json
[
    {
        "currency": "BTC",
        "outstanding": "1.02",
        "filledSize": "0.91000213",
        "accruedInterest": "0.00000213",
        "realizedProfit": "0.000045261",
        "isAutoLend": false
    }
]
```
Request via this endpoint to get the lending history of the main account.

### HTTP REQUEST
`GET /api/v1/margin/lend/assets`

### Example
`GET /api/v1/margin/lend/assets?currency=BTC`

### API KEY PERMISSIONS
This endpoint requires the **"Trade"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| currency | String | *[Optional]* Currency |

### RESPONSES
|Field | Description                      |
|----- |----------------------------------|
| currency        | Currency              |
| outstanding     | Outstanding size       |
| filledSize      | Size executed             |
| accruedInterest | Accrued Interest      |
| realizedProfit  | Realized profit       |
| isAutoLend      | Auto-lend enabled or not |

## Lending Market Data（Deprecate）
```json
[
    {
        "dailyIntRate": "0.0001",
        "term": 7,
        "size": "1.02"
    }
]
```

Request via this endpoint to get the lending market data.
The returned value is sorted based on the descending sequence of the daily interest rate and terms.

### HTTP REQUEST
`GET /api/v1/margin/market`

### Example
`GET /api/v1/margin/market?currency=BTC&term=7`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| currency | String |   Currency    |
| term     | int    | *[Optional]* Term (Unit: Day)   |

### RESPONSES
|Field | Description                      |
|----- |----------------------------------|
| dailyIntRate | Daily interest rate. e.g. 0.002 is 0.2% |
| term         | Term (Unit: Day)                        |
| size         | Total size                              |

## Margin Trade Data
```json
[
    {
        "tradeId": "5da6dba0f943c0c81f5d5db5",
        "currency": "BTC",
        "size": "0.51",
        "dailyIntRate": "0.0001",
        "term": 14,
        "timestamp": 1571216288958989641
    }
]
```

Request via this endpoint to get the last 300 fills in the lending and borrowing market.
The returned value is sorted based on the descending sequence of the order execution time.

### HTTP REQUEST
`GET /api/v1/margin/trade/last`

### Example
`GET /api/v1/margin/trade/last?currency=BTC`

### API KEY PERMISSIONS
This endpoint requires the **"General"** permission.

### PARAMETERS
|Param | Type | Description |
|--------- | ------- | -----------|
| currency | String |   Currency    |

### RESPONSES
|Field | Description                      |
|----- |----------------------------------|
| tradeId      | Trade ID                                 |
| currency     | Currency                                 |
| size         | Executed size                            |
| dailyIntRate | Daily interest rate. e.g. 0.002 is 0.2%  |
| term         | Term (Unit: Day)                         |
| timestamp    | Time of execution in nanosecond          |

## Query Lending Configuration
```json
 {
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": {
        "timestamp": 1669709409384,
        "items": [
            {
                "currency": "BTC",
                "lendMinSize": "0.001",
                "lendMaxSize": "300",
                "increment": "0.0001",
                "minDailyIntRate": "0",
                "maxDailyIntRate": "0.002",
                "precisionDailyIntRate": "0.00001",
                "terms": "7,14,28"
            }
        ]
    }
}
 ```

### HTTP REQUEST
`GET /api/v2/margin/lend/config`

### Example
`GET /api/v2/margin/lend/config?currency=USDT`

### API KEY PERMISSIONS
This API endpoint requires the `General` permission..

### PARAMETERS
| Param    | Type   | Description                                                          |
| -------- | ------ | -------------------------------------------------------------------- |
| currency | STRING | Path parameter, coin code. If empty, all coin types will be queried. |

### RESPONSES
| Field                 | Description                                                                                                      |
| --------------------- | ---------------------------------------------------------------------------------------------------------------- |
| currency              | Coin type                                                                                                        |
| lendMinSize           | Minimum size of a loan                                                                                           |
| lendMaxSize           | Maximum size of a loan                                                                                           |
| increment             | The amount the size of a loan can be increased by. The size of a loan must be a multiple of the increment value. |
| minDailyIntRate       | Minimum daily interest rate                                                                                      |
| maxDailyIntRate       | Maximum daily interest rate                                                                                      |
| precisionDailyIntRate | Daily interest rate precision                                                                                    |
| terms                 | Term of the loan. Units in days. Comma-separated. Example: 7,14,28                                               |

## Query Lending Market List
```json
 {
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": {
        "timestamp": 1669709478401,
        "items": [
            {
                "currency": "BTC",
                "size": "300",
                "dailyIntRate": "0.002",
                "term": 7
            }
        ]
    }
}
 ```
### HTTP REQUEST
`GET /api/v2/margin/lend/market`

### Example
`GET /api/v2/margin/lend/market?currency=USDT&term=7`

### API KEY PERMISSIONS
This API endpoint requires the `General` permission..
### PARAMETERS
| Param    | Type   | Description                  |
| -------- | ------ | ---------------------------- |
| currency | STRING | Coin Code                    |
| term     | INT    | Term of loan. Units in days. |

### RESPONSES
| Field        | Description                  |
| ------------ | ---------------------------- |
| currency     | Coin Code                    |
| size         | Loan amount                  |
| dailyIntRate | Daily interest rate          |
| term         | Term of loan. Units in days. |

## Lending Order Query (Paginated)
```json 
{
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": {
        "timestamp": 1669708513820,
        "currentPage": 1,
        "pageSize": 100,
        "totalNum": 1,
        "totalPage": 1,
        "items": [
            {
                "orderId": "637c85a15403ae00016bd6df",
                "currency": "USDT",
                "size": "3000000",
                "filledSize": "144",
                "dailyIntRate": "0.002",
                "term": 7,
                "createdAt": 1669105056560,
                "status": "ACTIVE"
            }
        ]
    }
}
```
### HTTP REQUEST
`GET /api/v2/margin/lend/orders`

### Example
`GET /api/v2/margin/lend/orders?currency=USDT&status=FINISH&currentPage=1&pageSize=10`

### API KEY PERMISSIONS
This API endpoint requires the `Trade` permission.

### PARAMETERS
| Param       | Type   | Description                                         |
| ----------- | ------ | --------------------------------------------------- |
| currency    | STRING | Coin code                                           |
| status      | STRING | Order Status: FINISH-completed, ACTIVE-in progress. |
| currentPage | INT    | Current page, defaults to 1.                        |
| pageSize    | INT    | The page size, 1<=pageSize<=100, defaults to 50.    |

### RESPONSES
| Field        | Description                                             |
| ------------ | ------------------------------------------------------- |
| orderId      | Order ID                                                |
| currency     | Coin code                                               |
| size         | Total size of order                                     |
| filledSize   | The amount of the order filled                          |
| dailyIntRate | Daily interest in decimal format. 0.002 refers to 0.2%. |
| term         | Term of loan (units in days)                            |
| createdAt    | Time order was placed (units: milliseconds)             |
| status       | Order status: FINISH-completed, ACTIVE-in progress.     |

## Query Single Lending Order
```json
{
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": {
        "orderId": "6385c0b3e0debdb6feb06e97",
        "currency": "USDT",
        "size": "11",
        "filledSize": "0",
        "dailyIntRate": "0.002",
        "term": 7,
        "createdAt": 1669710002360,
        "status": "ACTIVE"
    }
}
```

### HTTP REQUEST
`GET /api/v2/margin/lend`

### Example
`GET /api/v2/margin/lend?orderId=6385c0b3e0debdb6feb06e97`

### API KEY PERMISSIONS
This API endpoint requires the `Trade` permission.

### PARAMETERS
| Param   | Type   | Description   |
| ------- | ------ | ------------- |
| orderId | STRING | The order ID. |

### RESPONSES
| Field        | Description                                             |
| ------------ | ------------------------------------------------------- |
| orderId      | Order ID                                                |
| currency     | Coin code                                               |
| size         | The total size of the order                             |
| filledSize   | Amount of the order filled                              |
| dailyIntRate | Daily interest in decimal format. 0.002 refers to 0.2%. |
| term         | Term of loan (units in days)                            |
| createdAt    | Time order was placed (units: milliseconds)             |
| status       | Order status: FINISH-completed, ACTIVE-in progress.     |

## Query Lending Records
```json
 {
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": {
        "timestamp": 1669711220219,
        "currentPage": 1,
        "pageSize": 10,
        "totalNum": 39,
        "totalPage": 4,
        "items": [
            {
                "tradeId": "637c85a754f4d9000122f510",
                "currency": "USDT",
                "size": "11",
                "repaidSize": "11",
                "interest": "0.15400056",
                "accruedInterest": "0",
                "term": 7,
                "maturityTime": 1669709863747,
                "status": "CLEAR",
                "note": ""
            },
            {
                "tradeId": "6335ab03503ab80001485cb3",
                "currency": "USDT",
                "size": "1117",
                "repaidSize": "1117",
                "interest": "15.63799944",
                "accruedInterest": "0",
                "term": 7,
                "maturityTime": 1665066311258,
                "status": "CLEAR",
                "note": ""
            }
        ]
    }
}
 ```

### HTTP REQUEST
`GET /api/v2/margin/lend/trade/orders`

### Example
`GET /api/v2/margin/lend/trade/orders?currency=USDT&status=LEND&currentPage=1&pageSize=10`

### API KEY PERMISSIONS
This API endpoint requires the `Trade` permission.

### PARAMETERS
| Param       | Type   | Description                                                      |
| ----------- | ------ | ---------------------------------------------------------------- |
| currency    | STRING | Coin code                                                        |
| status      | STRING | Lending Order Status: LEND-Not fully repaid, CLEAR-Fully repaid. |
| currentPage | INT    | Current page (default: 1)                                        |
| pageSize    | INT    | The page size, 1<=pageSize<=100, defaults to 50.                 |

### RESPONSES
| Field           | Description                                                                                                                                                                 |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| tradeId         | Order ID of the loan                                                                                                                                                        |
| currency        | Coin code                                                                                                                                                                   |
| size            | Size of the loan                                                                                                                                                            |
| repaidSize      | The amount repaid.                                                                                                                                                          |
| interest        | Total interest                                                                                                                                                              |
| accruedInterest | Interest due                                                                                                                                                                |
| term            | Term of loan. Units in days.                                                                                                                                                |
| maturityTime    | Time of loan maturity (in milliseconds)                                                                                                                                     |
| status          | Loan Order Status: LEND-Not fully repaid, CLEAR-Fully repaid.                                                                                                               |
| note            | Notes are added when there is a negative balance, stating that the borrower has a negative balance and indicating whether repayment has been made using the Insurance Fund. |

# Isolated Margin
## Query Isolated Margin Trading Pair Configuration（Deprecate）
```json
{
    "code":"200000",
    "data": [
        {
            "symbol": "EOS-USDC",
            "symbolName": "EOS-USDC",
            "baseCurrency": "EOS",
            "quoteCurrency": "USDC",
            "maxLeverage": 10,
            "flDebtRatio": "0.97",
            "tradeEnable": true,
            "autoRenewMaxDebtRatio": "0.96",
            "baseBorrowEnable": true,
            "quoteBorrowEnable": true,
            "baseTransferInEnable": true,
            "quoteTransferInEnable": true
        },
        {
            "symbol": "MANA-USDT",
            "symbolName": "MANA-USDT",
            "baseCurrency": "MANA",
            "quoteCurrency": "USDT",
            "maxLeverage": 10,
            "flDebtRatio": "0.9",
            "tradeEnable": true,
            "autoRenewMaxDebtRatio": "0.96",
            "baseBorrowEnable": true,
            "quoteBorrowEnable": true,
            "baseTransferInEnable": true,
            "quoteTransferInEnable": true
        }
    ]
}
```
This API endpoint returns the current isolated margin trading pair configuration.

### HTTP Request
`GET /api/v1/isolated/symbols`

### API KEY PERMISSIONS
This endpoint requires the `General` permissions

### PARAMETERS
`N/A`

### RESPONSES
| Field | Description                     
| ------------ | ----------------- 
symbol | The trading pair code 
baseCurrency | Base currency type 
quoteCurrency | Quote coin 
symbolName | Trading pair name 
maxLeverage | Maximum leverage 
flDebtRatio | Liquidation debt ratio 
tradeEnable | Trade switch 
autoRenewMaxDebtRatio | During automatic renewal of the max debt ratio, the loan will only be renewed if it is lower than the debt ratio, with partial liquidation triggered for repayment if the debt ratio is in excess 
baseBorrowEnable | base coin type borrow switch 
quoteBorrowEnable | quote coin type borrow switch 
baseTransferInEnable | base coin type transfer switch 
quoteTransferInEnable | quote coin type transfer switch

## Query Isolated Margin Account Info（Deprecate）
```json
{
    "code":"200000",
    "data": {
        "totalConversionBalance": "3.4939947",
        "liabilityConversionBalance": "0.00239066",
        "assets": [
            {
                "symbol": "MANA-USDT",
                "status": "CLEAR",
                "debtRatio": "0",
                "baseAsset": {
                    "currency": "MANA",
                    "totalBalance": "0",
                    "holdBalance": "0",
                    "availableBalance": "0",
                    "liability": "0",
                    "interest": "0",
                    "borrowableAmount": "0"
                },
                "quoteAsset": {
                    "currency": "USDT",
                    "totalBalance": "0",
                    "holdBalance": "0",
                    "availableBalance": "0",
                    "liability": "0",
                    "interest": "0",
                    "borrowableAmount": "0"
                }
            },
            {
                "symbol": "EOS-USDC",
                "status": "CLEAR",
                "debtRatio": "0",
                "baseAsset": {
                    "currency": "EOS",
                    "totalBalance": "0",
                    "holdBalance": "0",
                    "availableBalance": "0",
                    "liability": "0",
                    "interest": "0",
                    "borrowableAmount": "0"
                },
                "quoteAsset": {
                    "currency": "USDC",
                    "totalBalance": "0",
                    "holdBalance": "0",
                    "availableBalance": "0",
                    "liability": "0",
                    "interest": "0",
                    "borrowableAmount": "0"
                }
            }
        ]
    }
}
```
This API endpoint returns all isolated margin accounts of the current user.

### HTTP Request
`GET /api/v1/isolated/accounts`

### API KEY PERMISSIONS
This endpoint requires the `General` permissions

### PARAMETERS
| Param | Type | Mandatory | Description 
| ------ | ------ | ------ | ------ 
balanceCurrency | String | No | The pricing coin, currently only supports `USDT`, `KCS`, and `BTC`. Defaults to `BTC` if no value is passed.

### RESPONSES
| Field | Description                     
| ------------ | ----------------- 
totalConversionBalance | The total balance of the isolated margin account (in the specified coin) 
liabilityConversionBalance | Total liabilities of the isolated margin account (in the specified coin) 
assets | Account list 
assets.symbol | Trading pairs, with each trading pair indicating a position 
assets.status | The position status: Existing liabilities-`DEBT`, No liabilities-`CLEAR`, Bankrupcy (after position enters a negative balance)-`BANKRUPTCY`, Existing borrowings-`IN_BORROW`, Existing repayments-`IN_REPAY`, Under liquidation-`IN_LIQUIDATION`, Under auto-renewal assets`-IN_AUTO_RENEW` .
debtRatio | Debt ratio 
assets.baseAsset | base coin type asset info 
assets.quoteAsset | quote coin type asset info 
currency | Coin type Code 
totalBalance | Current coin type asset amount 
holdBalance | Current coin type frozen 
availableBalance | The available balance (available assets - frozen assets)

## Query Single Isolated Margin Account Info（Deprecate）
```json
{
    "code": "200000",
    "data": {
        "symbol": "MANA-USDT",
        "status": "CLEAR",
        "debtRatio": "0",
        "baseAsset": {
            "currency": "MANA",
            "totalBalance": "0",
            "holdBalance": "0",
            "availableBalance": "0",
            "liability": "0",
            "interest": "0",
            "borrowableAmount": "0"
        },
        "quoteAsset": {
            "currency": "USDT",
            "totalBalance": "0",
            "holdBalance": "0",
            "availableBalance": "0",
            "liability": "0",
            "interest": "0",
            "borrowableAmount": "0"
        }
    }
}
```
This API endpoint returns the info on a single isolated margin account of the current user.

### HTTP Request
`GET /api/v1/isolated/account/{symbol}`

### API KEY PERMISSIONS
This endpoint requires the `General` permissions

### PARAMETERS
| Param | Type | Mandatory | Description | 
------ | ------ | ------ | ------ 
symbol | String | Yes | Trading pair, e.g.: `BTC-USDT`

### RESPONSES
| Field | Description                     
| ------------ | ----------------- 
symbol | Trading pair 
status |The position status: Existing liabilities-`DEBT`, No liabilities-`CLEAR`, Bankrupcy (after position enters a negative balance)-`BANKRUPTCY`, Existing borrowings-`IN_BORROW`, Existing repayments-`IN_REPAY`, Under liquidation-`IN_LIQUIDATION`, Under auto-renewal-`IN_AUTO_RENEW` (permissions per state) | Debt ratio baseAsset | base coin type asset info 
quoteAsset | quote coin type asset info 
currency | Coin type Code 
totalBalance | Current coin type asset amount 
availableBalance | Amount of current coin available 
holdBalance | Amount of current coin frozen 
liability | The principal of the of current coin liability (the outstanding principal) 
interest | The interest of the liability of the current coin (the outstanding interest) 
borrowableAmount | The borrowable amount

## Isolated Margin Borrowing（Deprecate）
```json
{
    "code": "200000",
    "data": {
        "orderId": "62baad0aaafc8000014042b3",
        "currency": "USDT",
        "actualSize": "10"
    }
}
```
This API endpoint initiates isolated margin borrowing.

### HTTP Request
`POST /api/v1/isolated/borrow`

### API KEY PERMISSIONS
This endpoint requires the `Trade` permissions

### PARAMETERS
| Param | Type | Mandatory | Description 
| ------ | ------ | ------ | ------ 
symbol | String | Yes | Trading pair, e.g.: `BTC-USDT` 
currency | String | Yes | Borrowed coin type 
size | BigDecimal | Yes | Borrowed amount 
borrowStrategy | String | Yes | Borrowing strategy: `FOK`, `IOC` 
maxRate | BigDecimal | No | Max interest rate, defaults to all interest rates if left blank 
period | String | No |The term in days. Defaults to all terms if left blank. `7`,`14`,`28`

### RESPONSES
| Field | Description                     
| ------------ | ----------------- 
orderId | Borrow order ID 
currency | Borrowed coin type 
actualBorrowSize | Actual borrowed amount

## Query Outstanding Repayment Records（Deprecate）
```json
{
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": {
        "currentPage": 1,
        "pageSize": 10,
        "totalNum": 6,
        "totalPage": 1,
        "items": [
            {
                "loanId": "62aec83bb51e6f000169a3f0",
                "symbol": "BTC-USDT",
                "currency": "USDT",
                "liabilityBalance": "10.02000016",
                "principalTotal": "10",
                "interestBalance": "0.02000016",
                "createdAt": 1655621691869,
                "maturityTime": 1656226491869,
                "period": 7,
                "repaidSize": "0",
                "dailyInterestRate": "0.001"
            },
            {
                "loanId": "62aa94e52a3fbb0001277fd1",
                "symbol": "BTC-USDT",
                "currency": "USDT",
                "liabilityBalance": "10.05166708",
                "principalTotal": "10",
                "interestBalance": "0.05166708",
                "createdAt": 1655346405447,
                "maturityTime": 1655951205447,
                "period": 7,
                "repaidSize": "0",
                "dailyInterestRate": "0.001"
            }
        ]
    }
}
```
This API endpoint is used to query the outstanding repayment records of isolated margin positions.

### HTTP Request
`GET /api/v1/isolated/borrow/outstanding`

### Example
`GET /api/v1/isolated/borrow/outstanding?symbol=BTC-USDT&currency=USDT`

### API KEY PERMISSIONS
This endpoint requires the `General` permissions

### PARAMETERS
| Param | Type | Mandatory | Description 
| ------ | ------ | ------ | ------ 
symbol | String | No | Trading pair, e.g.: `BTC-USDT` 
currency | String | No | Coin type 
pageSize | int | No | Page size [`10`-`50`] 
currentPage | int | No | Current page number [`1`-`100`]

### RESPONSES
| Field | Description                     
| ------------ | ----------------- 
loanId | Trade id 
symbol | Trading pair 
currency | Coin type 
liabilityBalance | Remaining liabilities 
principalTotal | Principal 
interestBalance | Accrued interest 
createdAt | Trade time, timestamp 
maturityTime | Maturity date, timestamp 
period | Term 
repaidSize | Amount repaid 
dailyInterestRate | Daily interest

## Query Repayment Records（Deprecate）
```json
{
    "code": "200000",
    "data": {
        "currentPage": 1,
        "pageSize": 10,
        "totalNum": 30,
        "totalPage": 3,
        "items": [
            {
                "loanId": "628df5787818320001c79c8b",
                "symbol": "BTC-USDT",
                "currency": "USDT",
                "principalTotal": "10",
                "interestBalance": "0.07000056",
                "repaidSize": "10.07000056",
                "createdAt": 1653470584859,
                "period": 7,
                "dailyInterestRate": "0.001",
                "repayFinishAt": 1654075506416
            },
            {
                "loanId": "628c570f7818320001d52b69",
                "symbol": "BTC-USDT",
                "currency": "USDT",
                "principalTotal": "11",
                "interestBalance": "0.07699944",
                "repaidSize": "11.07699944",
                "createdAt": 1653364495783,
                "period": 7,
                "dailyInterestRate": "0.001",
                "repayFinishAt": 1653969432251
            }
        ]
    }
}
```
This API endpoint is used to query the repayment records of isolated margin positions.

### HTTP Request
`GET /api/v1/isolated/borrow/repaid`

### Example
`GET /api/v1/isolated/borrow/repaid?symbol=BTC-USDT&currency=USDT`

### API KEY PERMISSIONS
This endpoint requires the `General` permissions

### PARAMETERS
| Param | Type | Mandatory | Description 
| ------ | ------ | ------ | ------ 
symbol | String | No | Trading pair, e.g.: `BTC-USDT` 
currency | String | No | Coin type 
pageSize | int | No | Page size \[`10`-`50`] 
currentPage | int | No | Current page number \[`1`-`100`]

### RESPONSES
| Field | Description                     
| ------------ | ----------------- 
loanId | Trade id 
symbol | Trading pair 
currency | Coin type 
principalTotal | Principal 
interestBalance | Accrued interest 
repaidSize | Amount repaid 
createdAt | Trade time, timestamp 
period | Term 
dailyInterestRate | Daily interest 
repayFinishAt | Repayment time

## Quick Repayment（Deprecate）
```json
//request
{
    "currency": "BTC",
    "seqStrategy": "HIGHEST_RATE_FIRST",
    "size": 1.9,
    "symbol": "BTC-USDT"
}
```
```json
//response
{
    "code": "200000",
    "data": null
}
```
This API endpoint is used to initiate quick repayment for isolated margin accounts

### HTTP Request
`POST /api/v1/isolated/repay/all`

### API KEY PERMISSIONS
This endpoint requires the `Trade` permissions

### PARAMETERS
| Param | Type | Mandatory | Description 
| ------ | ------ | ------ | ------ 
symbol | String | Yes | Trading pair, e.g.: `BTC-USDT` 
currency | String | Yes | Repayment coin type 
size | BigDecimal | Yes | Repayment amount 
seqStrategy | String | Yes | Repayment sequence strategy, `RECENTLY_EXPIRE_FIRST`: Maturity date priority (the loan with the closest maturity is repaid first), `HIGHEST_RATE_FIRST`: Interest rate priority (the loan with the highest interest rate is repaid first)

### RESPONSES
When the system returns HTTP status code `200` and system code `200000`, it indicates that the response is successful.

## Single Repayment（Deprecate）
```json
//request
{
    "currency": "BTC",
    "loanId": 8765321,
    "size": 1.9,
    "symbol": "BTC-USDT"
}
```
```json
//response
{
    "code": "200000",
    "data": null
}
```
This API endpoint is used to initiate quick repayment for single margin accounts

### HTTP Request
`POST /api/v1/isolated/repay/single`

### API KEY PERMISSIONS
This endpoint requires the `Trade` permissions

### PARAMETERS
| Param | Type | Mandatory | Description 
| ------ | ------ | ------ | ------ 
symbol | String | Yes | Trading pair, e.g.: `BTC-USDT` 
currency | String | Yes | Repayment coin type 
size | BigDecimal | Yes | Repayment amount 
loanId | String | Yes | Trade order number; when this field is configured, the sequence strategy is invalidated

### RESPONSES
When the system returns HTTP status code `200` and system code `200000`, it indicates that the response is successful.

# Margin Trade
## Get Isolated Margin Account Info
```json 
{
    "code": "200000",
    "data": [
        {
            "totalAssetOfQuoteCurrency": "3.4939947",
            "totalLiabilityOfQuoteCurrency": "0.00239066",
            "timestamp": 1668062174000,
            "assets": [
                {
                    "symbol": "MANA-USDT",
                    "debtRatio": "0",
                    "status": "BORROW",
                    "baseAsset": {
                        "currency": "MANA",
                        "borrowEnabled": true,
                        "transferInEnabled": true,
                        "liability": "0",
                        "total": "0",
                        "available": "0",
                        "hold": "0",
                        "maxBorrowSize": "1000"
                    },
                    "quoteAsset": {
                        "currency": "USDT",
                        "borrowEnabled": true,
                        "transferInEnabled": true,
                        "liability": "0",
                        "total": "0",
                        "available": "0",
                        "hold": "0",
                        "maxBorrowSize": "50000"
                    }
                }
            ]
        }
    ]
}
``` 
This API is used to query isolated margin account info.
### HTTP REQUEST
`GET /api/v2/isolated/accounts`

### Example
`GET /api/v2/isolated/accounts`

### API Permission
This API endpoint requires the `Trade`  permission.

### PARAMETERS
| Field         | Type   | Definition                                                                                                            |
| ------------- | ------ | --------------------------------------------------------------------------------------------------------------------- |
| symbol        | String | [Optional] For isolated trading pairs. Queries all when no argument is passed.                                        |
| quoteCurrency | String | [Optional] The quote currency. Currently only supports USDT, KCS, and BTC. Defaults to USDT if no argument is passed. |


### RESPONSES
| Field                         | Definition                                |
| ----------------------------- | ----------------------------------------- |
| totalAssetOfQuoteCurrency     | Total assets in the quoted currency.      |
| totalLiabilityOfQuoteCurrency | Total liabilities in the quoted currency. |
| timestamp                     | The timestamp.                            |
| assets                        | A list of the assets.                     |

| Field      | Definition                                                                                                                                                                                                                              |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| symbol     | The trading pair.                                                                                                                                                                                                                       |
| debtRatio  | The debt ratio.                                                                                                                                                                                                                         |
| baseAsset  | The base asset.                                                                                                                                                                                                                         |
| quoteAsset | The quoted asset.                                                                                                                                                                                                                       |
| status     | The position status: EFFECTIVE - The position is effective. BANKRUPTCY - The position has a negative balance. LIQUIDATION - The position is being liquidated. REPAY - The position is being repaid. BORROW - The position is borrowing. |

| Field             | Definition                                                          |
| ----------------- | ------------------------------------------------------------------- |
| currency          | The currency type.                                                  |
| borrowEnabled     | Is borrowing enabled?                                               |
| transferInEnabled | Is transfer-in enabled?                                             |
| liability         | The amount of liabilities.                                          |
| total             | The total assets.                                                   |
| available         | The available assets in the account (total assets - frozen assets). |
| hold              | The frozen assets in the account.                                   |
| maxBorrowSize     | The max remaining borrowable amount.                                |

## Get Cross Margin Account Info
```json 
{
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": {
        "totalLiabilityOfQuoteCurrency": "0.976",
        "totalAssetOfQuoteCurrency": "1.00",
        "debtRatio": "0.976",
        "status": "LIQUIDATION",
        "timestamp": 1669708513820,
        "assets": [
            {
                "currency": "BTC",
                "borrowEnabled": true,
                "transferInEnabled": false,
                "liability": "0.976",
                "total": "1.00",
                "available": "0.024",
                "hold": "0",
                "maxBorrowSize": "0"
            }
        ]
    }
}
``` 
This API is used to query cross margin account info.

### HTTP REQUEST
`GET /api/v2/margin/accounts`

### Example
`GET /api/v2/margin/accounts?quoteCurrency=BTC`

### API Permission
This API endpoint requires the `Trade` permission.

### PARAMETERS
| Field         | Type   | Definition                                                                                                            |
| ------------- | ------ | --------------------------------------------------------------------------------------------------------------------- |
| quoteCurrency | String | [Optional] The quote currency. Currently only supports USDT, KCS, and BTC. Defaults to USDT if no argument is passed. |


### RESPONSES
| Field                         | Definition                                                                                                                                                                                                                              |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| totalAssetOfQuoteCurrency     | Total assets in the quoted currency.                                                                                                                                                                                                    |
| totalLiabilityOfQuoteCurrency | Total liabilities in the quoted currency.                                                                                                                                                                                               |
| debtRatio                     | The debt ratio.                                                                                                                                                                                                                         |
| status                        | The position status: EFFECTIVE - The position is effective. BANKRUPTCY - The position has a negative balance. LIQUIDATION - The position is being liquidated. REPAY - The position is being repaid. BORROW - The position is borrowing. |
| assets                        | A list of the assets.                                                                                                                                                                                                                   |

| Field             | Definition                                                          |
| ----------------- | ------------------------------------------------------------------- |
| currency          | The currency type.                                                  |
| borrowEnabled     | Is borrowing enabled?                                               |
| transferInEnabled | Is transfer-in enabled?                                             |
| liability         | The amount of liabilities.                                          |
| total             | The total assets.                                                   |
| available         | The available assets in the account (total assets - frozen assets). |
| hold              | The frozen assets in the account.                                   |
| maxBorrowSize     | The max remaining borrowable amount.                                |

## Query the Max Transferrable Amount
```json
{
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": {
        "balance": "100",
        "available": "80",
        "holds": "20",
        "transferable": "20",
        "timestamp": 1668062174000
    }
}
 ``` 
This API is used to obtain the maximum transferrable amount of cross margin/isolated margin.

### HTTP REQUEST
`Get /api/v2/margin/transferable`

### API Permission
This API endpoint requires the `Trade` permission.

### PARAMETERS
| Field      | Type    | Definition                                                     |
| ---------- | ------- | -------------------------------------------------------------- |
| isIsolated | Boolean | true - isolated margin, false - cross margin; default = false. |
| symbol     | String  | [Optional] The isolated margin pair.                           |
| currency   | String  | The currency type.                                             |

### RESPONSES
| Field        | Definition                          |
| ------------ | ----------------------------------- |
| total        | The total assets.                   |
| available    | The available assets in the account |
| hold         | The frozen assets in the account.   |
| transferable | The maximum transferable quantity.  |
| timestamp    | The timestamp.                      |

## Get the Leverage Limit
```json 
// MARGIN RESPONSES
{
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": [
        {
            "timestamp": 1672733936758,
            "currency": "USDT",
            "borrowMaxAmount": "70000",
            "buyMaxAmount": "71000",
            "holdMaxAmount": "71001",
            "precision": 8
        },
        {
            "timestamp": 1672733936758,
            "currency": "BTC",
            "borrowMaxAmount": "46000",
            "buyMaxAmount": "46500",
            "holdMaxAmount": "46501",
            "precision": 8
        }
    ]
}
```
```json 
// Isolated RESPONSES
{
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": [
        {
            "timestamp": 1672734099363,
            "symbol": "ACT-ETH",
            "baseMaxBorrowAmount": "100",
            "quoteMaxBorrowAmount": "800",
            "baseMaxBuyAmount": "100",
            "quoteMaxBuyAmount": "800",
            "baseMaxHoldAmount": "100",
            "quoteMaxHoldAmount": "800",
            "basePrecision": 8,
            "quotePrecision": 8
        },
        {
            "timestamp": 1672734099363,
            "symbol": "MANA-USDT",
            "baseMaxBorrowAmount": "2700",
            "quoteMaxBorrowAmount": "10000",
            "baseMaxBuyAmount": "2800",
            "quoteMaxBuyAmount": "20000",
            "baseMaxHoldAmount": "2801",
            "quoteMaxHoldAmount": "20001",
            "basePrecision": 8,
            "quotePrecision": 8
        }
    ]
}
``` 
This API is used to obtain the cross margin/isolated margin leverage limit.

### HTTP REQUEST
`Get /api/v2/margin/riskLimits`

### API Permission
This API endpoint requires the `General` permission.

### PARAMETERS
| Field      | Type    | Definition                                                     |
| ---------- | ------- | -------------------------------------------------------------- |
| isIsolated | Boolean | true - isolated margin, false - cross margin; default = false. |
| symbol     | String  | [Optional] The trading pair, isolated position filter.         |
| currency   | String  | [Optional] The currency type, cross position filter condition. |

**Response: Cross Margin**

| Field           | Definition                                |
| --------------- | ----------------------------------------- |
| currency        | The currency type.                        |
| holdMaxAmount   | The max position (configurable).          |
| borrowMaxAmount | The max borrowable amount (configurable). |
| precision       | The precision of the loan.                |
| buyMaxAmount    | The max buy amount (configurable).        |

**Response: Isolated Margin**

| Field                | Definition                                      |
| -------------------- | ----------------------------------------------- |
| symbol               | The trading pair.                               |
| baseMaxBorrowAmount  | The base maximum borrow amount (configurable).  |
| quoteMaxBorrowAmount | The quote maximum borrow amount (configurable). |
| baseMaxBuyAmount     | The base maximum buy amount (configurable).     |
| quoteMaxBuyAmount    | The quote maximum buy amount (configurable).    |
| baseMaxHoldAmount    | The base maximum position (configurable).       |
| quoteMaxHoldAmount   | The quote maximum position (configurable).      |
| basePrecision        | The base precision of the loan.                 |
| quotePrecision       | The quote precision of the loan.                |

## Apply for a Loan
```json 
{
    "code": "200000",
    "timestamp": 1668062174000,
    "data": {
        "orderId": "5da6dba0f943c0c81f5d5db5",
        "size": "20.9"
    }
}
``` 
This API is used to apply for loans.

### HTTP REQUEST
`POST /api/v2/margin/borrow`

### API Permission
This API endpoint requires the `Trade` permission.

### PARAMETERS
| Field       | Type    | Definition                                                          |
| ----------- | ------- | ------------------------------------------------------------------- |
| isIsolated  | Boolean | true - isolated margin, false - cross margin; default = false.      |
| symbol      | String  | [Optional] The trading pair, required for isolated margin accounts. |
| currency    | String  | The borrowed currency.                                              |
| timeInForce | String  | The time in force (IOC, FOK).                                       |
| size        | String  | The borrowed amount.                                                |
| maxRate     | String  | [Optional] The maximum interest rate.                               |
| term        | Int     | [Optional] The term of the loan.                                    |

### RESPONSES
| Field   | Definition                     |
| ------- | ------------------------------ |
| orderId | The order ID of the borrowing. |
| size    | The transaction amount.        |

## Quick Repayment
```json 
{
    "code": "200000",
    "data": {
        "tradeId": "5da6dba0f4234345c81f5d50f",
        "timestamp": 1668062174000
    }
}
``` 
This API is used to perform batch repayment. When the HTTP status code 200 and 200000 are returned, this means that repayment was successful. Any other code means that repayment failed.

### HTTP REQUEST
`POST /api/v2/margin/repay/all`

### API Permission
This API endpoint requires the **Trade **permission.

### PARAMETERS
| Field      | Type    | Definition                                                                                                                                                                                                                                                                                                |
| ---------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| isIsolated | Boolean | true - isolated margin, false - cross margin; default = false.                                                                                                                                                                                                                                            |
| symbol     | String  | [Optional] Leave empty for cross margin, provide a value for isolated margin.                                                                                                                                                                                                                             |
| currency   | String  | The currency type.                                                                                                                                                                                                                                                                                        |
| size       | String  | The amount to be repaid.                                                                                                                                                                                                                                                                                  |
| sequence   | String  | The repayment sequence policy. RECENTLY\_EXPIRE\_FIRST - Prioritizes the maturity date, meaning that priority is given to repaying loans that are due the soonest. HIGHEST\_RATE\_FIRST - Prioritizes the interest rate, meaning that priority is given to repaying loans with the highest interest rate. |

### RESPONSES
| Field     | Definition     |
| --------- | -------------- |
| tradeId   | The trade ID.  |
| timestamp | The timestamp. |

## Single Repayment
```json 
{
    "code": "200000",
    "data": {
        "tradeId": "5da6dba0f4234345c81f5d50f",
        "timestamp": 1668062174000
    }
}
``` 
This API is used to perform single repayment. When the HTTP status code 200 and 200000 are returned, this means that repayment was successful. Any other code means that repayment failed.

### HTTP REQUEST
`POST /api/v2/margin/repay/single`

### API Permission
This API endpoint requires the `Trade` permission.

### PARAMETERS
| Field      | Type    | Definition                                                                    |
| ---------- | ------- | ----------------------------------------------------------------------------- |
| isIsolated | Boolean | true - isolated margin, false - cross margin; default = false.                |
| symbol     | String  | [Optional] Leave empty for cross margin, provide a value for isolated margin. |
| currency   | String  | The currency type.                                                            |
| size       | String  | The amount to be repaid.                                                      |
| tradeId    | String  | The ID of the loan order.                                                     |

### RESPONSES
| Field     | Definition     |
| --------- | -------------- |
| tradeId   | The trade ID.  |
| timestamp | The timestamp. |

## Query Repayment Records
```json
 {
    "success": true,
    "code": "200",
    "msg": "success",
    "retry": false,
    "data": {
        "timestamp": 1669708513820,
        "currentPage": 1,
        "pageSize": 100,
        "totalNum": 1,
        "totalPage": 1,
        "items": [
            {
                "tradeId": "5da6dba0f943c0c81f5d5db5",
                "currency": "USDT",
                "principal": "50000",
                "interest": "50",
                "repaidSize": "4000",
                "maturityTime": 1668062174000,
                "dailyIntRate": "0.0004",
                "term": 28,
                "status": "ACTIVE"
            }
        ]
    }
}
```
This API is used to query repayment records.

### HTTP REQUEST
`GET /api/v2/margin/repay`

### API Permission
This API endpoint requires the **Trade **permission.

### PARAMETERS
| Field       | Type    | Definition                                                     |
| ----------- | ------- | -------------------------------------------------------------- |
| currentPage | Int     | [Optional] The current page, defaults to 1.                    |
| pageSize    | Int     | [Optional] The page size. 1<=pageSize<=100, defaults to 50.    |
| isIsolated  | Boolean | true - isolated margin, false - cross margin; default = false. |
| symbol      | String  | [Optional] The isolated margin pair.                           |
| status      | String  | FINISH-completed, ACTIVE-in progress.                          |
| currency    | String  | [Optional] The currency type.                                  |
| startTime   | Long    | [Optional] The start time.                                     |
| endTime     | Long    | [Optional] The end time.                                       |

### RESPONSES
| Field        | Definition                                          |
| ------------ | --------------------------------------------------- |
| tradeId      | The trade ID.                                       |
| currency     | The currency type.                                  |
| principal    | The borrowed amount.                                |
| interest     | The total interest.                                 |
| repaidSize   | The repaid amount (including principal + interest). |
| maturityTime | The maturity date.                                  |
| dailyIntRate | The daily interest.                                 |
| term         | The term of the loan.                               |
| status       | FINISH-completed, ACTIVE-in progress.               |

## Margin Order Placement
```json 
{
    "code": "200000",
    "data": [
        {
            "orderId": "5bd6e9286d99522a52e458de",
            "borrowSize": 10.2,
            "loanApplyId": "600656d9a33ac90009de4f6f"
        }
    ]
}
``` 
This API is used to place cross margin and isolated margin orders.

### HTTP REQUEST
`POST /api/v2/margin/order`

### API Permission
This API endpoint requires the `Trade` permission.

### PARAMETERS
**Order Public Parameters:**

| Field      | Type    | Definition                                                                                                                                                                                          |
| ---------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| isIsolated | Boolean | true - isolated margin, false - cross margin; default = false.                                                                                                                                      |
| clientOid  | String  | The unique identifier created by the client (UUID is recommended).                                                                                                                                  |
| side       | String  | Buy or sell.                                                                                                                                                                                        |
| symbol     | String  | The trading pair, such as ETH-BTC.                                                                                                                                                                  |
| type       | String  | [Optional] The order type (limit or market). Defaults to limit.                                                                                                                                     |
| remark     | String  | [Optional] The order remarks. The length should not exceed 100 characters (UTF-8).                                                                                                                  |
| stp        | String  | [Optional] Self-trade prevention (this API requires **trading permissions**). Divided into four policies: CN, CO, CB, and DC.                                                                       |
| autoBorrow | Boolean | [Optional] Automatically borrow assets to place an order (the platform will auto borrow assets at the best market interest rate, then places an order). At present, only cross margin is supported. |

**Addition PARAMETERS required for limit orders:**

| Field       | Type    | Definition                                                                     |
| ----------- | ------- | ------------------------------------------------------------------------------ |
| price       | String  | The price in the specified currency.                                           |
| size        | String  | The amount of the specified currency.                                          |
| timeInForce | String  | [Optional] The time in force (GTC, GTT, IOC, FOK). Defaults to GTC.            |
| cancelAfter | Long    | [Optional] Cancel after n seconds. The time in force is GTT.                   |
| postOnly    | Boolean | [Optional] The passive order ID. Invalid when the time in force is IOC or FOK. |
| hidden      | Boolean | [Optional] Is the order hidden (not displayed in the order book)?              |
| iceberg     | Boolean | [Optional] Display the visible part of the order in the iceberg list?          |
| visibleSize | String  | [Optional] The max display quantity of the iceberg order.                      |

**Addition PARAMETERS required for market orders**

| Field | Type   | Definition                                |
| ----- | ------ | ----------------------------------------- |
| size  | String | [Optional] Choose one from size or funds. |
| funds | String | [Optional] Choose one from size or funds. |

### RESPONSES
| Field       | Definition                                                                       |
| ----------- | -------------------------------------------------------------------------------- |
| orderId     | The order ID.                                                                    |
| borrowSize  | The loan amount. Returned only after the automatic loan order is placed.         |
| loanApplyId | The loan application ID. Returned only after the automatic loan order is placed. |


# Others


## Server Time
```json
{  
    "code":"200000",
    "msg":"success",
    "data":1546837113087
}
```

Get the server time.

### HTTP REQUEST
`GET /api/v1/timestamp`

### Example
`GET /api/v1/timestamp`

### PARAMETERS
`N/A`

<aside class="spacer2"></aside>

## Service Status
```json
{    
  "code": "200000",     
  "data": {

      "status": "open",                //open:normal transaction, close:Stop Trading/Maintenance, cancelonly:can only cancel the order but not place order
      "msg":  "upgrade match engine"   //remark for operation
    }
}
```
Get the service status

### HTTP REQUEST
`GET /api/v1/status`

### Example
`GET /api/v1/status`

### PARAMETERS
`N/A`

### RESPONSES
|Field    | Description                                             |
|-------- |-------------------------------------------------------  |
| status  | Status of service: **open**：normal transaction, **close**：Stop Trading/Maintenance, **cancelonly**：can only cancel the order but not place order|
| msg     | Remark for operation                                    |





# Websocket Feed

While there is a strict access frequency control for REST API, we highly recommend that API users utilize Websocket to get the real-time data.


<aside class="notice">The recommended way is to just create a websocket connection and subscribe to multiple channels.
</aside>

## Apply connect token

```json
{
	"code": "200000",
	"data": {
		"token": "2neAiuYvAU61ZDXANAGAsiL4-iAExhsBXZxftpOeh_55i3Ysy2q2LEsEWU64mdzUOPusi34M_wGoSf7iNyEWJ4aBZXpWhrmY9jKtqkdWoFa75w3istPvPtiYB9J6i9GjsxUuhPw3BlrzazF6ghq4L_u0MhKxG3x8TeN4aVbNiYo=.mvnekBb8DJegZIgYLs2FBQ==",
		"instanceServers": [{
			"endpoint": "wss://ws-api-spot.kucoin.com/",	//It is recommended to use a dynamic URL, which may change
			"encrypt": true,
			"protocol": "websocket",
			"pingInterval": 18000,
			"pingTimeout": 10000
		}]
	}
}

```

You need to apply for one of the two tokens below to create a websocket connection.

### Public token (No authentication required):

If you only use public channels (e.g. all public market data), please make request as follows to obtain the server list and temporary public token:

#### HTTP REQUEST
`POST /api/v1/bullet-public`

### Private channels (Authentication request required):

For private channels and messages (e.g. account balance notice), please make request as follows after authorization to obtain the server list and authorized token.

#### HTTP REQUEST
`POST /api/v1/bullet-private`


### Response
|Field | Description|
-----|-----
|endpoint| Websocket server address for establishing connection|
|protocol| Protocol supported|
|encrypt| Indicate whether SSL encryption is used |
|pingInterval| Recommended to send ping interval in millisecond|
|pingTimeout| After such a long time(millisecond), if you do not receive pong, it will be considered as disconnected. |
|token| token|

## Create connection

```javascript
var socket = new WebSocket("wss://ws-api-spot.kucoin.com/?token==xxx&[connectId=xxxxx]");
```


When the connection is successfully established, the system will send a welcome message.

<aside class="notice">Only when the welcome message is received will the connection be available</aside>

**connectId**: the connection id, a unique value taken from the client side. Both the id of the welcome message and the id of the error message are connectId.

If you only want to receive private messages of the specified topic, please set privateChannel to true when subscribing.

```json
{
    "id":"hQvf8jkno",
    "type":"welcome"
}
```



<aside class="spacer2"></aside>

## Ping
```json
{
    "id":"1545910590801",
    "type":"ping"
}
```


To prevent the TCP link being disconnected by the server, the client side needs to send ping messages every pingInterval time to the server to keep alive the link.

After the ping message is sent to the server, the system would return a pong message to the client side.

If the server has not received any message from the client for a long time, the connection will be disconnected.


```json
{
    "id":"1545910590801",
    "type":"pong"
}
```
<aside class="spacer3"></aside>

## Subscribe

```json
{
    "id": 1545910660739,                          //The id should be an unique value
    "type": "subscribe",
    "topic": "/market/ticker:BTC-USDT,ETH-USDT",  //Topic needs to be subscribed. Some topics support to divisional subscribe the informations of multiple trading pairs through ",".
    "privateChannel": false,                      //Adopted the private channel or not. Set as false by default.
    "response": true                              //Whether the server needs to return the receipt information of this subscription or not. Set as false by default.
}
```

To subscribe channel messages from a certain server, the client side should send subscription message to the server.

If the subscription succeeds, the system will send ack messages to you, when the response is set as true.


```json
{
    "id":"1545910660739",
    "type":"ack"
}
```
While there are topic messages generated, the system will send the corresponding messages to the client side. For details about the message format, please check the definitions of topics.

### Parameters
#### ID
ID is unique string to mark the request which is same as id property of ack.

#### Topic
The topic you want to subscribe to.

#### PrivateChannel
For some specific topics (e.g. /market/level2), **privateChannel** is available. The default value of **privateChannel** is **False**. If the **privateChannel** is set to **true**, the user will only receive messages related himself on the topic.

#### Response
If the response is set as true, the system will return the ack messages after the subscription succeed.

## UnSubscribe
Unsubscribe from topics you have subscribed to.

```json
{
    "id": "1545910840805",                            //The id should be an unique value
    "type": "unsubscribe",
    "topic": "/market/ticker:BTC-USDT,ETH-USDT",      //Topic needs to be unsubscribed. Some topics support to divisional unsubscribe the informations of multiple trading pairs through ",".
    "privateChannel": false,
    "response": true                                  //Whether the server needs to return the receipt information of this subscription or not. Set as false by default.
}
```

```json
{
    "id": "1545910840805",
    "type": "ack"
}
```

### Parameters

#### ID
Unique string to mark the request.

#### Topic
The topic you want to subscribe.

#### PrivateChannel
If the **privateChannel** is set to **true**, the private topic will be unsubscribed.

#### Response
If the response is set as true, the system would return the ack messages after the unsubscription succeed.

## Multiplex

In one physical connection, you could open different multiplex tunnels to subscribe different **topics** for different data.


For example, enter the command below to open **bt1** multiple tunnel :

 {"id": "1Jpg30DEdU", "type": "openTunnel", "newTunnelId": "bt1", "response": true}

Add “**tunnelId**” in the command:

{"id": "1JpoPamgFM", "type": "subscribe", "topic": "/market/ticker:KCS-BTC"，"tunnelId": "bt1", "response": true}

You would then, receive messages corresponding to the id **tunnelIId**:  

{"id": "1JpoPamgFM", "type": "message", "topic": "/market/ticker:KCS-BTC", "subject": "trade.ticker", "tunnelId": "bt1", "data": {...}}

To close the **tunnel**, you can enter the command below:

{"id": "1JpsAHsxKS", "type": "closeTunnel", "tunnelId": "bt1", "response": true}

##### Limitations

1. The multiplex **tunnel** is provided for API users only.
2. The maximum multiplex tunnels available: **5**.


## Sequence Numbers
The sequence field exists in order book, trade history and snapshot messages by default and the Level 3 and Level 2 data works to ensure the full connection of the sequence. If the sequence is non-sequential, please enable the calibration logic.


## General Logic for Message Judgement in Client Side
1.Judge message type. There are three types of messages at present: message (the commonly used messages for push), notice (the notices generally used), and command (consecutive command).

2.Judge messages by topic. You could judge the message type through the topic.

3.Judge messages by subject. For the same type of messages with the same topic, you could judge the type of messages through their subjects.

# Public Channels

## Symbol Ticker

```json

{
    "id": 1545910660739,
    "type": "subscribe",
    "topic": "/market/ticker:BTC-USDT",
    "response": true
}
```


```json
{
    "type":"message",
    "topic":"/market/ticker:BTC-USDT",
    "subject":"trade.ticker",
    "data":{
        "sequence":"1545896668986", // Sequence number
        "price":"0.08",             // Last traded price
        "size":"0.011",             //  Last traded amount
        "bestAsk":"0.08",          // Best ask price
        "bestAskSize":"0.18",      // Best ask size
        "bestBid":"0.049",         // Best bid price
        "bestBidSize":"0.036"     // Best bid size
    }
}
```

Topic: `/market/ticker:{symbol},{symbol}...`

* Push frequency: once every `100ms`

Subscribe to this topic to get the push of BBO changes.

Please note that more information may be added to messages from this channel in the near future.


<aside class="spacer2"></aside>
<aside class="spacer4"></aside>


## All Symbols Ticker

```json

{
    "id": 1545910660739,                          
    "type": "subscribe",
    "topic": "/market/ticker:all",
    "response": true                              
}
```
```json
{
    "type":"message",
    "topic":"/market/ticker:all",
    "subject":"BTC-USDT",
    "data":{
        "sequence":"1545896668986",
        "bestAsk":"0.08",
        "size":"0.011",
        "bestBidSize":"0.036",
        "price":"0.08",
        "bestAskSize":"0.18",
        "bestBid":"0.049"
    }
}
```
Topic: `/market/ticker:all`

* Push frequency: once every `100ms`

Subscribe to this topic to get the push of all market symbols BBO change.

<aside class="spacer8"></aside>


## Symbol Snapshot

```json
{
    "type": "message",
    "topic": "/market/snapshot:KCS-BTC",
    "subject": "trade.snapshot",
    "data": {
        "sequence": "1545896669291",
        "data": {
            "trading": true,
            "symbol": "KCS-BTC",
            "buy": 0.00011,
            "sell": 0.00012,
            "sort": 100,
            "volValue": 3.13851792584,   //total
            "baseCurrency": "KCS",
            "market": "BTC",
            "quoteCurrency": "BTC",
            "symbolCode": "KCS-BTC",
            "datetime": 1548388122031,
            "high": 0.00013,
            "vol": 27514.34842,
            "low": 0.0001,
            "changePrice": -1.0e-5,
            "changeRate": -0.0769,
            "lastTradedPrice": 0.00012,
            "board": 0,
            "mark": 0
        }
    }
}
```
Topic: `/market/snapshot:{symbol}`

* Push frequency: once every `2s`

Subscribe to get snapshot data for a single symbol.

<aside class="spacer4"></aside>
<aside class="spacer4"></aside>
<aside class="spacer"></aside>

## Market Snapshot

```json
{
    "type": "message",
    "topic": "/market/snapshot:BTC",
    "subject": "trade.snapshot",
    "data": {
        "sequence": "1545896669291",
        "data": [
            {
                "trading": true,
                "symbol": "KCS-BTC",
                "buy": 0.00011,
                "sell": 0.00012,
                "sort": 100,
                "volValue": 3.13851792584,
                "baseCurrency": "KCS",
                "market": "BTC",
                "quoteCurrency": "BTC",
                "symbolCode": "KCS-BTC",
                "datetime": 1548388122031,
                "high": 0.00013,
                "vol": 27514.34842,
                "low": 0.0001,
                "changePrice": -1.0e-5,
                "changeRate": -0.0769,
                "lastTradedPrice": 0.00012,
                "board": 0,
                "mark": 0
          }
       ]
    }
}
```

Topic: `/market/snapshot:{market}`

* Push frequency: once every `2s`

Subscribe this topic to get the snapshot data of for the entire [market](#get-market-list).


<aside class="spacer4"></aside>
<aside class="spacer4"></aside>
<aside class="spacer"></aside>

## Level-2 Market Data

```json
{
    "id": 1545910660740,                          
    "type": "subscribe",
    "topic": "/market/level2:BTC-USDT",
    "response": true                              
}
```

Topic: `/market/level2:{symbol},{symbol}...`

* Push frequency:`real-time`

Subscribe to this topic to get Level2 order book data.

When the websocket subscription is successful,  the system would send the increment change data pushed by the websocket to you.

```json
{
    "type": "message",
    "topic": "/market/level2:BTC-USDT",
    "subject": "trade.l2update",
    "data": {
        "changes": {
            "asks": [
                [
                    "18906",//price
                    "0.00331",//size
                    "14103845"//sequence
                ],
                [
                    "18907.3",
                    "0.58751503",
                    "14103844"
                ]
            ],
            "bids": [
                [
                    "18891.9",
                    "0.15688",
                    "14103847"
                ]
            ]
        },
        "sequenceEnd": 14103847,
        "sequenceStart": 14103844,
        "symbol": "BTC-USDT",
        "time": 1663747970273//milliseconds
    }
}
```

Calibration procedure：

1. After receiving the websocket Level 2 data flow, cache the data.
2. Initiate a [REST](#get-full-order-book-aggregated) request to get the snapshot data of Level 2 order book.
3. Playback the cached Level 2 data flow.
4. Apply the new Level 2 data flow to the local snapshot to ensure that `sequenceStart(new)<=sequenceEnd+1(old)` and `sequenceEnd(new) > sequenceEnd(old)`. The sequence on each record in changes only represents the last modification of the corresponding sequence of the price, and does not serve as a basis for judging message continuity.
5. Update the level2 full data based on sequence according to the price and size. If the price is 0, ignore the messages and update the sequence. If the size=0, update the sequence and remove the price of which the size is 0 out of level 2. For other cases, please update the price.


**Example**

Take BTC/USDT as an example, suppose the current order book data in level 2 is as follows:

After subscribing to the channel, you would receive changes as follows:


<code>
...<br/>
"asks":[<br/>
&nbsp;&nbsp;["3988.59","3", 16], // ignore it because sequence = 16<br/>
&nbsp;&nbsp;["3988.61","0", 19], // Remove 3988.61<br/>
&nbsp;&nbsp;["3988.62","8", 15], // ignore it because sequence < 16 <br/>
]<br/>
"bids":[<br/>
&nbsp;&nbsp;["3988.50", "44", "18"] // Update size of 3988.50 to 44<br/>
]<br/>
"sequenceEnd": 15,<br/>
"sequenceStart": 19,<br/>
...<br/>
</code>

<aside class="notice">The sequence on each record in changes only represents the last modification of the corresponding sequence of the price, not as a basis for judging the continuity of the message; for example, when there are multiple updates at the same price ["3988.50", "20", "17" "], ["3988.50", "44", "18"], at this time only the latest ["3988.50", "44", "18"] will be pushed</aside>

Get a snapshot of the order book through a **REST** request ([Get Order Book](#get-part-order-book-aggregated)) to build a local order book. Suppose that data we got is as follows:

<code>
...<br/>
"sequence": "16",<br/>
"asks":[<br/>
&nbsp;&nbsp;["3988.62","8"],//[Price, Size]<br/>
&nbsp;&nbsp;["3988.61","32"],<br/>
&nbsp;&nbsp;["3988.60","47"],<br/>
&nbsp;&nbsp;["3988.59","3"],<br/>
]<br/>
"bids":[<br/>
&nbsp;&nbsp;["3988.51","56"],<br/>
&nbsp;&nbsp;["3988.50","15"],<br/>
&nbsp;&nbsp;["3988.49","100"],<br/>
&nbsp;&nbsp;["3988.48","10"]<br/>
]<br/>
...<br/>
</code>

The current data on the local order book is as follows:

<code>
| Price | Size | Side |<br/>
|---------|-----|------|<br/>
| 3988.62 | 8&nbsp;&nbsp;    | Sell |<br/>
| 3988.61 | 32&nbsp;   | Sell |<br/>
| 3988.60 | 47&nbsp;   | Sell |<br/>
| 3988.59 | 3&nbsp;&nbsp;    | Sell |<br/>
| 3988.51 | 56&nbsp;   | Buy&nbsp;  |<br/>
| 3988.50 | 15&nbsp;   | Buy&nbsp;  |<br/>
| 3988.49 | 100  | Buy&nbsp;  |<br/>
| 3988.48 | 10&nbsp;  | Buy&nbsp;  |<br/>
</code>

In the beginning, the sequence of the order book is `16`. Discard the feed data of sequence that is below or equals to `16`, and apply playback the sequence `[18,19]` to update the snapshot of the order book. Now the sequence of your order book is `19` and your local order book is up-to-date.

**Diff:**

- Update size of 3988.50 to 44 (Sequence 18)
- Remove 3988.61 (Sequence 19)

Now your current order book is up-to-date and final data is as follows:

<code>
| Price | Size | Side |<br/>
|---------|-----|------|<br/>
| 3988.62 | 8&nbsp;&nbsp;    | Sell |<br/>
| 3988.60 | 47&nbsp;    | Sell |<br/>
| 3988.59 | 3&nbsp;&nbsp; | Sell |<br/>
| 3988.51 | 56&nbsp;    | Buy&nbsp;   |<br/>
| 3988.50 | 44&nbsp;    | Buy&nbsp;   |<br/>
| 3988.49 | 100  | Buy&nbsp;   |<br/>
| 3988.48 | 10&nbsp;   | Buy&nbsp;   |<br/>
</code>

## Level2 - 5 best ask/bid orders
```json
{
    "type": "message",
    "topic": "/spotMarket/level2Depth5:BTC-USDT",
    "subject": "level2",
    "data": {
	      "asks":[
            ["9989","8"],    //price, size
            ["9990","32"],
            ["9991","47"],
            ["9992","3"],
            ["9993","3"]
        ],
        "bids":[
            ["9988","56"],
            ["9987","15"],
            ["9986","100"],
            ["9985","10"],
            ["9984","10"]
        ],
        "timestamp": 1586948108193
    }
}

```

Topic: `/spotMarket/level2Depth5:{symbol},{symbol}...`

* Push frequency: once every `100ms`

The system will return the 5 best ask/bid orders data, which is the snapshot data of every 100 milliseconds (in other words, the 5 best ask/bid orders data returned every 100 milliseconds in real-time).

<aside class="spacer4"></aside>
<aside class="spacer4"></aside>
<aside class="spacer"></aside>

## Level2 - 50 best ask/bid orders
```json
{
    "type": "message",
    "topic": "/spotMarket/level2Depth50:BTC-USDT",
    "subject": "level2",
    "data": {
	      "asks":[
            ["9993","3"],     //price,size
            ["9992","3"],
            ["9991","47"],
            ["9990","32"],
            ["9989","8"]
        ],
        "bids":[
            ["9988","56"],
            ["9987","15"],
            ["9986","100"],
            ["9985","10"],
            ["9984","10"]
        ]
        "timestamp": 1586948108193
    }
}
```

Topic: `/spotMarket/level2Depth50:{symbol},{symbol}...`

* Push frequency: once every `100ms`

The system will return the 50 best ask/bid orders data, which is the snapshot data of every 100 milliseconds (in other words, the 50 best ask/bid orders data returned every 100 milliseconds in real-time).

<aside class="spacer4"></aside>
<aside class="spacer4"></aside>
<aside class="spacer"></aside>

## Klines

```json
{
    "type":"message",
    "topic":"/market/candles:BTC-USDT_1hour",
    "subject":"trade.candles.update",
    "data":{
        "symbol":"BTC-USDT",    // symbol
        "candles":[
            "1589968800",   // Start time of the candle cycle
            "9786.9",       // open price
            "9740.8",       // close price
            "9806.1",       // high price
            "9732",         // low price
            "27.45649579",  // Transaction volume
            "268280.09830877"   // Transaction amount
        ],
        "time":1589970010253893337  // now（us）
    }
}
```
Topic: `/market/candles:{symbol}_{type}`

* Push frequency: `real-time`

Param |  Description
--------- | -------
symbol | [symbol](#get-symbols-list)
type |  `1min`, `3min`, `15min`, `30min`, `1hour`, `2hour`, `4hour`, `6hour`, `8hour`, `12hour`, `1day`, `1week`


Subscribe to this topic to get K-Line data.


## Match Execution Data

```json
{
    "id": 1545910660741,                          
    "type": "subscribe",
    "topic": "/market/match:BTC-USDT",
    "privateChannel": false,                      
    "response": true                              
}
```
Topic: `/market/match:{symbol},{symbol}...`

* Push frequency: `real-time`

Subscribe to this topic to get the matching event data flow of Level 3.

For each order traded, the system would send you the match messages in the following format.

```json
{
    "type":"message",
    "topic":"/market/match:BTC-USDT",
    "subject":"trade.l3match",
    "data":{
        "sequence":"1545896669145",
        "type":"match",
        "symbol":"BTC-USDT",
        "side":"buy",
        "price":"0.08200000000000000000",
        "size":"0.01022222000000000000",
        "tradeId":"5c24c5da03aa673885cd67aa",
        "takerOrderId":"5c24c5d903aa6772d55b371e",
        "makerOrderId":"5c2187d003aa677bd09d5c93",
        "time":"1545913818099033203"
    }
}
```
<aside class="spacer8"></aside>
<aside class="spacer"></aside>

## Index Price

```json
{
  "id": 1545910660740,                              
  "type": "subscribe",
  "topic": "/indicator/index:USDT-BTC",
  "response": true
}
```

Topic: `/indicator/index:{symbol0},{symbol1}...`

Subscribe to this topic to get the index price for the margin trading.

```json
{
    "id":"5c24c5da03aa673885cd67a0",
    "type":"message",
    "topic":"/indicator/index:USDT-BTC",
    "subject":"tick",
    "data":{
        "symbol": "USDT-BTC",
        "granularity": 5000,
        "timestamp": 1551770400000,
        "value": 0.0001092
    }
}
```

The following ticker symbols are supported: [List of currently supported symbol](#list-of-currently-supported-symbol)

<aside class="spacer8"></aside>
<aside class="spacer4"></aside>

## Mark Price

```json
{
  "id": 1545910660741,                              
  "type": "subscribe",
  "topic": "/indicator/markPrice:USDT-BTC",
  "response": true
}
```
```json
{
    "id":"5c24c5da03aa673885cd67aa",
    "type":"message",
    "topic":"/indicator/markPrice:USDT-BTC",
    "subject":"tick",
    "data":{
        "symbol": "USDT-BTC",
        "granularity": 5000,
        "timestamp": 1551770400000,
        "value": 0.0001093
    }
}
```
Topic: `/indicator/markPrice:{symbol0},{symbol1}...`

Subscribe to this topic to get the mark price for margin trading.

The following ticker symbols are supported: [List of currently supported symbol](#list-of-currently-supported-symbol)

<aside class="spacer8"></aside>
<aside class="spacer4"></aside>

## Order Book Change

```json
{
  "id": 1545910660742,
  "type": "subscribe",
  "topic": "/margin/fundingBook:BTC",
  "response": true
}
```
```json
{
    "id": "5c24c5da03aa673885cd67ab",
	  "type": "message",
	  "topic": "/margin/fundingBook:BTC",
	  "subject": "funding.update",
	  "data": {

		    "sequence": 1000000,       //Sequence number
		    "currency": "BTC",         //Currency
		    "dailyIntRate": "0.00007",   //Daily interest rate. e.g. 0.002 is 0.2%
		    "annualIntRate": "0.12",     //Annual interest rate. e.g. 0.12 is 12%
		    "term": 7,                 //Term (Unit: Day)    
		    "size": "1017.5",            //Current total size. When this value is 0, remove this record from the order book.
		    "side": "lend",            //Lend or borrow. Currently, only "Lend" is available
		    "ts": 1553846081210004941  //Timestamp (nanosecond)
    }
}
```
Topic: `/margin/fundingBook:{currency0},{currency1}...`

Subscribe to this topic to get the order book changes on margin trade.

<aside class="spacer8"></aside>
<aside class="spacer2"></aside>



# Private Channels

Subscribe to private channels require `privateChannel=“true”`.


## Private Order Change Events

Topic: `/spotMarket/tradeOrders`

* Push frequency: `real-time`

This topic will push all change events of your orders.


**Order Status**

“match”: when taker order executes with orders in the order book, the taker order status is “match”;

“open”: the order is in the order book;

“done”: the order is fully executed successfully;


### Message Type

#### open
```json
{
    "type":"message",
    "topic":"/spotMarket/tradeOrders",
    "subject":"orderChange",
    "channelType":"private",
    "data":{
        "symbol":"KCS-USDT",
        "orderType":"limit",
        "side":"buy",
        "orderId":"5efab07953bdea00089965d2",
        "type":"open",
        "orderTime":1670329987026,
        "size":"0.1",
        "filledSize":"0",
        "price":"0.937",
        "clientOid":"1593487481000906",
        "remainSize":"0.1",
        "status":"open",
        "ts":1670329987311000000
    }
}
```
when the order enters into the order book;

<aside class="spacer4"></aside>
<aside class="spacer4"></aside>
<aside class="spacer2"></aside>

#### match
```json
{
    "type":"message",
    "topic":"/spotMarket/tradeOrders",
    "subject":"orderChange",
    "channelType":"private",
    "data":{
        "symbol":"KCS-USDT",
        "orderType":"limit",
        "side":"sell",
        "orderId":"5efab07953bdea00089965fa",
        "liquidity":"taker",
        "type":"match",
        "orderTime":1670329987026,
        "size":"0.1",
        "filledSize":"0.1",
        "price":"0.938",
        "matchPrice":"0.96738",
        "matchSize":"0.1",
        "tradeId":"5efab07a4ee4c7000a82d6d9",
        "clientOid":"1593487481000313",
        "remainSize":"0",
        "status":"match",
        "ts":1670329987311000000
    }
}
```
when the order has been executed;

<aside class="spacer4"></aside>
<aside class="spacer4"></aside>
<aside class="spacer2"></aside>

#### filled
```json
{
    "type":"message",
    "topic":"/spotMarket/tradeOrders",
    "subject":"orderChange",
    "channelType":"private",
    "data":{
        "symbol":"KCS-USDT",
        "orderType":"limit",
        "side":"sell",
        "orderId":"5efab07953bdea00089965fa",
        "type":"filled",
        "orderTime":1670329987026,
        "size":"0.1",
        "filledSize":"0.1",
        "price":"0.938",
        "clientOid":"1593487481000313",
        "remainSize":"0",
        "status":"done",
        "ts":1670329987311000000
    }
}
```
when the order has been executed and its status was changed into DONE;

<aside class="spacer4"></aside>
<aside class="spacer4"></aside>
<aside class="spacer2"></aside>

#### canceled
```json
{
    "type":"message",
    "topic":"/spotMarket/tradeOrders",
    "subject":"orderChange",
    "channelType":"private",
    "data":{
        "symbol":"KCS-USDT",
        "orderType":"limit",
        "side":"buy",
        "orderId":"5efab07953bdea00089965d2",
        "type":"canceled",
        "orderTime":1670329987026,
        "size":"0.1",
        "filledSize":"0",
        "price":"0.937",
        "clientOid":"1593487481000906",
        "remainSize":"0",
        "status":"done",
        "ts":1670329987311000000
    }
}
```
when the order has been cancelled and its status was changed into DONE;

<aside class="spacer4"></aside>
<aside class="spacer4"></aside>
<aside class="spacer2"></aside>

#### update
```json
{
    "type":"message",
    "topic":"/spotMarket/tradeOrders",
    "subject":"orderChange",
    "channelType":"private",
    "data":{
        "symbol":"KCS-USDT",
        "orderType":"limit",
        "side":"buy",
        "orderId":"5efab13f53bdea00089971df",
        "type":"update",
        "oldSize":"0.1",
        "orderTime":1670329987026,
        "size":"0.06",
        "filledSize":"0",
        "price":"0.937",
        "clientOid":"1593487679000249",
        "remainSize":"0.06",
        "status":"open",
        "ts":1670329987311000000
    }
}
```
when the order has been updated;

<aside class="spacer4"></aside>
<aside class="spacer4"></aside>

## Account Balance Notice
```json
{
    "type": "message",
	  "topic": "/account/balance",
	  "subject": "account.balance",
    "channelType":"private",
	  "data": {
		    "total": "88", // total balance
		    "available": "88", // available balance
		    "availableChange": "88", // the change of available balance
		    "currency": "KCS", // currency
		    "hold": "0", // hold amount
		    "holdChange": "0", // the change of hold balance
		    "relationEvent": "trade.setted", //relation event
		    "relationEventId": "5c21e80303aa677bd09d7dff", // relation event id
		    "relationContext": {
            "symbol":"BTC-USDT",
            "tradeId":"5e6a5dca9e16882a7d83b7a4", // the trade Id when order is executed
            "orderId":"5ea10479415e2f0009949d54"
        },  // the context of trade event
		"time": "1545743136994" // timestamp
  }
}

```
Topic: `/account/balance`

* Push frequency: `real-time`

You will receive this message when an account balance changes. The message contains the details of the change.


### Relation Event

| Type    | Description |
|---------| ----------- |
main.deposit | Deposit
main.withdraw_hold | Hold withdrawal amount
main.withdraw_done | Withdrawal done
main.transfer | Transfer (Main account)
main.other | Other operations (Main account)
trade.hold | Hold (Trade account)
trade.setted | Settlement (Trade account)
trade.transfer | Transfer (Trade account)
trade.other | Other operations (Trade account)
margin.hold | Hold (Margin account)
margin.setted | Settlement (Margin account)
margin.transfer |Transfer (Margin account)
margin.other | Other operations (Margin account)
other | Others

<aside class="spacer4"></aside>
<aside class="spacer2"></aside>


## Debt Ratio Change

```json
{
    "type":"message",
    "topic":"/margin/position",
    "subject":"debt.ratio",
    "channelType":"private",
    "data": {
        "debtRatio": 0.7505,                                         //Debt ratio
        "totalDebt": "21.7505",                                      //Total debt in BTC (interest included)
        "debtList": {"BTC": "1.21","USDT": "2121.2121","EOS": "0"},  //Debt list (interest included)
        "timestamp": 15538460812100                                  //Timestamp (millisecond)
  }
}

```

Topic: `/margin/position`

The system will push the current debt message periodically when there is a liability.

<aside class="spacer4"></aside>
<aside class="spacer2"></aside>


## Position Status Change Event

```json
{
    "type":"message",
    "topic":"/margin/position",
    "subject":"position.status",
    "channelType":"private",
    "data": {
        "type": "FROZEN_FL",         //Event type
        "timestamp": 15538460812100  //Timestamp (millisecond)
    }
}
```

Topic: `/margin/position`

The system will push the change event when the position status changes.

Event type:

FROZEN_FL: When the debt ratio exceeds the liquidation threshold and the position is frozen, the system will push this event.

UNFROZEN_FL: When the liquidation is finished and the position returns to “EFFECTIVE” status, the system will push this event.

FROZEN_RENEW: When the auto-borrow renewing is complete and the position returns to “EFFECTIVE” status, the system will push this event.

UNFROZEN_RENEW: When the account reaches a negative balance, the system will push this event.

LIABILITY: When the account reaches a negative balance, the system will push this event.

UNLIABILITY: When all the liabilities is repaid and the position returns to “EFFECTIVE” status, the system will push this event.




<aside class="spacer4"></aside>
<aside class="spacer2"></aside>

## Margin Trade Order Enters Event

```json
{
    "type": "message",
    "topic": "/margin/loan:BTC",
    "subject": "order.open",
    "channelType":"private",
    "data": {
        "currency": "BTC",                            //Currency
        "orderId": "ac928c66ca53498f9c13a127a60e8",   //Trade ID
        "dailyIntRate": 0.0001,                       //Daily interest rate.
        "term": 7,                                    //Term (Unit: Day)  
        "size": 1,                                    //Size
        "side": "lend",                               //Lend or borrow. Currently, only "Lend" is available
        "ts": 1553846081210004941                     //Timestamp (nanosecond)
    }
}
```

Topic: `/margin/loan:{currency}`

The system will push this message to the lenders when the order enters the order book.


<aside class="spacer4"></aside>
<aside class="spacer2"></aside>

## Margin Order Update Event


```json
{
    "type": "message",
    "topic": "/margin/loan:BTC",
    "subject": "order.update",
    "channelType":"private",
    "data": {
        "currency": "BTC",                            //Currency
        "orderId": "ac928c66ca53498f9c13a127a60e8",   //Order ID
        "dailyIntRate": 0.0001,                       //Daily Interest Rate
        "term": 7,                                    //Term (Unit: Day)
        "size": 1,                                    //Size
        "lentSize": 0.5,                              //Size executed
        "side": "lend",                               //Lend or borrow. Currently, only "Lend" is available
        "ts": 1553846081210004941                     //Timestamp (nanosecond)
    }
}

```

Topic: `/margin/loan:{currency}`

The system will push this message to the lenders when the order is executed.


<aside class="spacer4"></aside>
<aside class="spacer2"></aside>

## Margin Order Done Event

```json
{
	"type": "message",
	"topic": "/margin/loan:BTC",
	"subject": "order.done",
    "channelType":"private",
	"data": {
		"currency": "BTC",                            //Currency
		"orderId": "ac928c66ca53498f9c13a127a60e8",   //Order ID
		"reason": "filled",                           //Done reason (filled or canceled)
		"side": "lend",                               //Lend or borrow. Currently, only "Lend" is available
		"ts": 1553846081210004941                     //Timestamp (nanosecond)
  }
}
```

Topic: `/margin/loan:{currency}`

The system will push this message to the lenders when the order is completed.



<aside class="spacer8"></aside>
<aside class="spacer"></aside>



```json
{
    "type":"message",
    "topic":"/spotMarket/advancedOrders",
    "subject":"stopOrder",
    "channelType":"private",
    "data":{
        "createdAt":1589789942337,
        "orderId":"5ec244f6a8a75e0009958237",
        "orderPrice":"0.00062",
        "orderType":"stop",
        "side":"sell",
        "size":"1",
        "stop":"entry",
        "stopPrice":"0.00062",
        "symbol":"KCS-BTC",
        "tradeType":"TRADE",
        "triggerSuccess":true,
        "ts":1589790121382281286,
        "type":"triggered"
    }
}
```

## Stop Order Event

Topic: `/spotMarket/advancedOrders`

* Push frequency: `real-time`

Subject: stopOrder

When a stop order is received by the system, you will receive a message with "open" type. It means that this order entered the system and waited to be triggered.

When a stop order is triggered by current trading price, you will receive a message with "triggered" type.

When you cancel a stop order, you will receive a message with "cancel" type.