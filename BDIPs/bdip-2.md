---
bdip: 2
title: DApp ID
author: Shun Usami <usatie@yenom.tech>,
        Taiki Uchida <yuiki@yenom.tech>,
        Akifumi Fujita <akifuji@yenom.tech>
type: Standard Track
status: Draft
Created: 2018-11-1
---

=================

Table of Contents
* [Simple Summary](#simple-summary)
* [Abstract](#abstract)
* [Motivation](#motivation)
* [Specification](#specification)
   * [Data in the OP_RETURN output](#data-in-the-op_return-output)
   * [Transaction Field Definitions](#transaction-field-definitions)
   * [Transaction Definitions](#transaction-definitions)
   * [Updating DApps](#updating-dapps)
* [Rationale](#rationale)
* [References](#references)
* [Copyright](#copyright)

## Simple Summary
 A unique identifier for a single DApp Protocol with the specification of the DApp.

## Abstract
Anyone can create DApp ID by simply broadcasting a transaction. The transaction must have OP_RETURN output, which contains the summary of the DApp's protocol spec. The txid of this transaction is regarded as the DApp ID.

## Motivation
Currently, private key providers (i.e. wallets) does not have a way to trustlessly get a DApps protocol spec such as,
- If the DApp requires to use an single address. (i.e. Wormhole token application)
- If the DApp requires to keep utxos. (i.e. SLP token application)

The protocol spec of DApps is the core part of DApps, but we don't have the standard way to share it.
The motivation of DApp ID is to accomplish it in a trustless manner.


## Specification
The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be interpreted as described in RFC 2119.

### Data in the OP_RETURN output
The script of the output consists of OP_RETURN and a sequence of OP_PUSHDATA with data.
If the data is NULL, use `OP_0` instead of OP_PUSHDATA with data.

Example.
```
OP_RETURN
OP_PUSHDATA [data 1]
OP_PUSHDATA [data 2]
...
OP_PUSHDATA [data n]
```

These fields are required for all transactions.
- Magic bytes
- Transaction type
- Transaction version


### Transaction Field Definitions
This section defines the fields that are used to construct transaction messages.


#### Field: Magic bytes
- Description: the magic bytes for DApp ID protocol.
- Size: `4 bytes`, binary data
- Valid value: `0x64617070`

#### Field: Transaction type
- Description: The available function fields provided by the protocol.
- Size: `1 byte`,  8-bit unsigned integer
- Current Valid values:
    - 0 : [Create DApp](#create-dapp)

#### Field: Transaction version
- Description: The version of the transaction - definition, monotonically increasing independently for each transaction type
- Size: `2 bytes`, 16-bit unsigned integer
- Inter-dependencies: [Transaction type](#field-transaction-type)
- Valid values: 0 to 65535

#### Field: Bitcoin File URI
- Description: The Bitcoinfile URI of the file describing the DApp spec. The way to upload files to the Bitcoin blockchain must follows [Bitcoin Files Protocol Specification](https://github.com/simpleledger/slp-specifications/blob/master/bitcoinfiles.md).
- Size: `32 bytes`, binary data


#### Field: Application type
- Description: Specifies if the coins sent to the DApp's addresses are spendable or not, and if the DApp is account model or not
- Size: `1 byte`, 8-bit unsigned integer
- Current Valid values: 0 to 3
    - 0 [00000000] : Unspendable
    - 1 [00000001] : Spendable
    - 2 [00000010] : Unspendable, Account model
    - 3 [00000011] : Spendable, Account model

```
76543210
||||||||
|||||||+- Spendable Flag
||||||+-- Account base Flag
||||||
```

#### Field: String

- Description: a variable length string
- Size: variable
- Valid values: Unicode encoded with UTF-8

### Transaction Definitions
Each transaction definition has its own version number to enable support for changes to each transaction definition. The fields specified in sections below must not be removed and the ordering of the fields must not be changed. Transactions which has insufficient fields or invalid ordering of the fields shall be invalid.

#### Create DApp
- Description : Creating DApp ID tranaction
- Transaction type : 0 (0x00)
- Transaction version : 0 (0x0000)

| Filed | Type | Example |
| --- | --- | --- |
| Magic bytes | [Magic bytes](#Field-Magic-bytes) | 0x64617070 |
| Transaction type | [Transaction type](#Field-Transaction-type) | 0 (0x00) |
| Transaction version | [Transaction version](#Field-Transaction-version) | 0 (0x0000) |
| Application type | [Application type](#Field-Application-type) | 0 (0x00) |
| Name | [String](#Field-String) | "BitcoinCashApp" (14 bytes) |
| Protocol Spec file URI | [Bitcoinfile URI](#Field-Bitcoin-file-URI) / NULL | 0eac357541b0ba572849113c5faa1d1990f6382741dc3e2f5507e3ca8346dc0e |
| URL | [String](#Field-String) / NULL | "web3bch.cash" (12 bytes) |
| Meta Data | [String](#Field-String) / NULL | "Hello Bitcoin Cash" (18 bytes) |


### Updating DApps
Updating DApps protocol is regarded as creating new DApps. So the transaction format is the same as [Create DApp](#Create-DApp).
If you want to prove the update is the cannonical one, it seems a good way to use the change utxo of the previous DApp creating tx.

However, it should be emphasized that DApps are protocols so if DApp ID changes, it's not the same protocol anymore.
It means that anyone can fork and update any DApps at anytime by simply creating the new DApp ID.

## Rationale
The DApp ID should not be depend on centralized system. So we believe storing information in the blockchain is the best way to do it.

## References
1. Wormhole protocol https://www.wormhole.cash
2. Simple Ledger Protocol  https://simpleledger.cash
3. Bitcoin Files Protocol https://bitcoinfiles.com
4. RFC 2119 Key words for use in RFCs to Indicate Requirement Levels. https://www.ietf.org/rfc/rfc2119.txt

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
