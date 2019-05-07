# BEP-6: Time locking of tokens

- [BEP-6: Time locking of tokens](#bep-6-time-locking-of-tokens)
  - [1. Summary](#1-summary)
  - [2. Abstract](#2-abstract)
  - [3. Status](#3-status)
  - [4. Motivation](#4-motivation)
  - [5. Specification](#5-specification)
    - [5.1 Operations](#51-operations)
      - [5.1.1 TimeLock](#511-timelock)
      - [5.1.2 TimeUnlock](#512-timeunlock)
      - [5.1.3 TimeRelock](#513-timerelock)
      - [5.1.4 QueryTimeLockRecords](#514-querytimelockrecords)
      - [5.1.4 QueryTimeLockRecord](#514-querytimelockrecord)
  - [6. License](#6-license)


## 1.  Summary

This BEP describes a proposal for time-locking functionality of tokens on the Binance Chain.

## 2.  Abstract

BEP-6 Proposal describes functionality to time-lock tokens on the Binance Chain. Such as:

- TimeLock: TimeLock will transfer locked tokens to an escrow account and before the lock time specified user will not be able to claim them back.

- TimeUnlock: TimeUnlock will claim the locked tokens back when the lock time specified is passed.

- TimeRelock: TimeRelock will extend lock time, increase amount of locked tokens or modify description of a specific lock record.

- QueryTimeLockRecords: QueryTimeLockRecords will query all lock records of a specific address.

- QueryTimeLockRecord: QueryTimeLockRecord will query a given lock record of a specific address.

## 3.  Status

This BEP is WIP. 

## 4.  Motivation

Some projects require tokens to be time-locked against transfers for letting members adhere to vesting schedules.

## 5.  Specification

###  5.1 Operations

#### 5.1.1 TimeLock

TimeLock operation is to lock tokens from operator account to a given future time. 

**Parameters for TimeLock Operation**:

| **Field**    | **Type** | **Description**                                              |
| :------------ | :-------- | :------------------------------------------------------------ |
| Description   | string  | Description of lock operation |
| Amount        | []Coin   | A set of tokens to be locked |
| LockTime      | int64  | Time when these tokens can be unlocked |

TimeLock operation will transfer locked tokens to an escrow account and will return a `TimeLock` record id.

#### 5.1.2 TimeUnlock

TimeUnlock operation is to unlock tokens of a given `TimeLock` record. TimeUnlock operation will fail if operation time is before `LockTime` specified in TimeLock operation. 

If TimeUnlock operation succeeds, locked tokens will be transfered to owner's account, and the related `TimeLock` record will be deleted.

**Parameters for TimeUnlock Operation**:

| **Field**    | **Type** | **Description**                                              |
| :------------ | :-------- | :------------------------------------------------------------ |
| RecordId   | int64  | `TimeLock` record id |

#### 5.1.3 TimeRelock

TimeUnlock operation is to update amount of locked tokens or lock time of a given `TimeLock` record. But user can only increase the amount of locked tokens and increase lock time.

**Parameters for TimeRelock Operation**:

| **Field**    | **Type** | **Description**                                              |
| :------------ | :-------- | :------------------------------------------------------------ |
| RecordId    | int64  | `TimeLock` record id |
| Description   | string  | Description of lock operation. If `Description` is empty, this operation will not change description of `TimeLock` record. |
| Amount      | []Coin  | A set of tokens to be locked. If `Amount` is empty, this operation will not change amount of `TimeLock` record. If `Amount` is not empty, amount should be more than original amount. |
| LockTime      | int64  | Time when these tokens can be unlocked. If `LockTime` is zero, this operation will not change lock time of `TimeLock` record. If `LockTime` is not zeror, it should be after the original lock time|

#### 5.1.4 QueryTimeLockRecords

QueryTimeLockRecords will return all `TimeLock` records of specific address.

#### 5.1.4 QueryTimeLockRecord

QueryTimeLockRecord will return `TimeLock` record of a given `TimeLock` record id of specific address.

## 6. License

The content is licensed under [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
