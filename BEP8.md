# BEP 8: Trading assets by other users on Binance Chain


- [BEP 8: Trading assets by other users on Binance Chain](#bep-8--trading_asset_by_other_users_on_binance_chain)
  * [1.  Summary](#1--summary)
  * [2.  Abstract](#2--abstract)
  * [3.  Status](#3--status)
  * [4.  Motivation](#4--motivation)
  * [5.  Specification](#5--specification)
    - [5.1 Approve](#51-approve)
    - [5.2 Disapprove](#52-disapprove)
    - [5.3 OrderFrom](#53-orderfrom)
    - [5.4 CancelFrom](#54-cancelfrom)
  * [6. License](#6-license)


## 1.  Summary

This BEP describes a proposal for trading assets from other wallets on the Binance Chain.

## 2.  Abstract

BEP-8 Proposal describes a common set of rules for trading order on the Binance Chain.
It like API Key and Secret to allow 3rd party to send order on behalf of user.
Application like robot trading and social trading platform can perform trade for user programmatically without granting transfer asset from user's wallet.


## 3.  Status

This BEP is drafting. 

## 4.  Motivation

Robot trading and social trading platform is allow user to trade asset with ease. However allow 3rd party to full access the fund can be dangerous.
Malicious party can steal all the asset by transferring all of the asset from wallets. It would be safer to just allow 3rd party to only trade asset for user.

## 5.  Specification

### 5.1 Approve

- Grant right to trade assets from another user.

### 5.2 Disapprove

- Remove right to trade assets from another user.

###  5.3 OrderFrom

- Place order for another user.

###  5.3 CancelFrom

- Cancel order for another user.


## 6. License

The content is licensed under [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
