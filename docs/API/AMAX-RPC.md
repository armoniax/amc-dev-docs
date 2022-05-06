RPC
----
Describe how to use HTTP RPC.

Content
---
- [Disposition](#Disposition)
- [Interface](#Interface)
    - [get_info](#get_info)
    - [get_block](#get_block)
    - [get_account](#get_account)
    - [get_code](#get_code)
    - [get_table_rows](#get_table_rows)
    - [abi_json_to_bin](#get_json_to_bin)
    - [abi_bin_to_json](#get_bin_to_json)
    - [push_transaction](#push_transaction)
    - [push_transactions](#push_transactions)
    - [get_required_keys](#get_required_keys)
 
- [wallet RPC](#wallet RPC)
    - [wallet_create](#wallet_create)
    - [wallet_open](#wallet_open)
    - [wallet_lock](#wallet_lock)
    - [wallet_lock_all](#wallet_lock_all)
    - [wallet_import_key](#wallet_import_key)
    - [wallet_wallet_list](#wallet_list)
    - [wallet_list_keys](#wallet_list_keys)
    - [wallet_get_public_keys](#wallet_get_public_keys)
    - [wallet_set_timeout](#wallet_set_timeout)
    - [wallet_sign_trx](#wallet_sign_trx)


# Disposition

Amax uses REST RPC interface, and plug-ins can register their own endpoints on the API server. This page will explain how to use APIs to get information about blockchain and transaction.

Before querying Amax, you must enable the required API plug-in. Add the following line to your Amax's config.ini, depending on the API you want to use:

```C++
plugin = eosio::chain_api_plugin // 生效链API
plugin = eosio::wallet_api_plugin // 生效钱包API
```
In addition, for wallet API, you can separate the wallet function from Amax by running wallet separately.


# Interface
## get_info

Get the latest information related to the node.

### get_info usage example

```bash
curl http://127.0.0.1:8888/v1/chain/get_info
```

### get_info result example

```json
{
  "server_version": "b2eb1667",
  "head_block_num": 259590,
  "last_irreversible_block_num": 259573,
  "head_block_id": "0003f60677f3707f0704f16177bf5f007ebd45eb6efbb749fb1c468747f72046",
  "head_block_time": "2017-12-10T17:05:36",
  "head_block_producer": "initp",
  "recent_slots": "1111111111111111111111111111111111111111111111111111111111111111",
  "participation_rate": "1.00000000000000000"
}
```

## get_block

Get block information.

### get_block usage example

```bash
$ curl  http://127.0.0.1:8888/v1/chain/get_block -X POST -d '{"block_num_or_id":5}'
$ curl  http://127.0.0.1:8888/v1/chain/get_block -X POST -d '{"block_num_or_id":0000000445a9f27898383fd7de32835d5d6a978cc14ce40d9f327b5329de796b}'
```

### get_block result example

```json
{
  "previous": "0000000445a9f27898383fd7de32835d5d6a978cc14ce40d9f327b5329de796b",
  "timestamp": "2017-07-18T20:16:36",
  "transaction_merkle_root": "0000000000000000000000000000000000000000000000000000000000000000",
  "producer": "initf",
  "producer_changes": [ ],
  "producer_signature": "204cb94b3186c3b4a7f88be4e9db9f8af2ffdb7ef0f27a065c8177a5fcfacf876f684e59c39fb009903c0c59220b147bb07f1144df1c65d26c57b534a76dd29073",
  "cycles": [ ],
  "id":"000000050c0175cbf218a70131ddc3c3fab8b6e954edef77e0bfe7c36b599b1d",
  "block_num":5,
  "ref_block_prefix":27728114
}
```

## get_account

Get account information.

### get_account usage example

```bash
$ curl  http://127.0.0.1:8888/v1/chain/get_account -X POST -d '{"account_name":"inita"}'
```

### get_account result example

```json
{
  "name": "inita",
  "eos_balance": "999998.9574 EOS",
  "staked_balance": "0.0000 EOS",
  "unstaking_balance": "0.0000 EOS",
  "last_unstaking_time": "2106-02-07T06:28:15",
  "permissions": [
    {
      "name": "active",
      "parent": "owner",
      "required_auth": {
        "threshold": 1,
        "keys": [
          {
            "key": "EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV",
            "weight": 1
          }
        ],
        "accounts": []
      }
    },
    {
      "name": "owner",
      "parent": "owner",
      "required_auth": {
        "threshold": 1,
        "keys": [
          {
            "key": "EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV",
            "weight": 1
          }
        ],
        "accounts": []
      }
    }
  ]
}
```

## get_code

Get smart contract code

### get_code usage example

```bash
$ curl  http://127.0.0.1:8888/v1/chain/get_code -X POST -d '{"account_name":"currency"}'
```

### get_code result example

```json
{
  "name":"currency",
  "code_hash":"a1c8c84b4700c09c8edb83522237439e33cf011a4d7ace51075998bd002e04c9",
  "wast":"(module\n  (type $0 (func (param i64 i64 i32) (result i32)))\n ...truncated",
  "abi": {
  "types": [{
      "new_type_name": "account_name",
      "type": "name"
    }
  ],
  "structs": [{
      "name": "transfer",
      "base": "",
      "fields": [
        {"name":"from", "type":"account_name"},
        {"name":"to", "type":"account_name"},
        {"name":"quantity", "type":"uint64"}
      ]
    },{
      "name": "account",
      "base": "",
      "fields": [
        {"name":"key", "type":"name"},
        {"name":"balance", "type":"uint64"}
      ]
    }
  ],
  "actions": [{
      "name": "transfer",
      "type": "transfer"
    }
  ],
  "tables": [{
      "name": "account",
      "type": "account",
      "index_type": "i64",
      "key_names" : ["key"],
      "key_types" : ["name"]
    }
  ]
  }
}
```

## get_table_rows

Get smart contract data.

### get_table_rows usage example

```bash
$ curl  http://127.0.0.1:8888/v1/chain/get_table_rows -X POST -d '{"scope":"inita", "code":"currency", "table":"account", "json": true}'
$ curl  http://127.0.0.1:8888/v1/chain/get_table_rows -X POST -d '{"scope":"inita", "code":"currency", "table":"account", "json": true, "lower_bound":0, "upper_bound":-1, "limit":10}'
```

### get_table_rows result example

```json
{
  "rows": [
    {
      "account": "account",
      "balance": 1000
    }
  ],
  "more": false
}
```

## abi_json_to_bin

Serialize json to binary hexadecimal. The resulting binary hexadecimal is usually used for data fields of push_transaction.

### abi_json_to_bin usage example

```bash
$ curl  http://127.0.0.1:8888/v1/chain/abi_json_to_bin -X POST -d '{"code":"currency", "action":"transfer", "args":{"from":"initb", "to":"initc", "quantity":1000}}'
```

### abi_json_to_bin result example

```json
{
  "binargs": "000000008093dd74000000000094dd74e803000000000000",
  "required_scope": [],
  "required_auth": []
}
```

## abi_bin_to_json

Serialize binary hex to json.

### abi_bin_to_json usage example

```bash
$ curl  http://127.0.0.1:8888/v1/chain/abi_bin_to_json -X POST -d '{"code":"currency", "action":"transfer", "binargs":"000000008093dd74000000000094dd74e803000000000000"}'
```

### abi_bin_to_json result example

```json
{
  "args": {
    "from": "initb",
    "to": "initc",
    "quantity": 1000
  },
  "required_scope": [],
  "required_auth": []
}
```

## push_transaction

This method expects transactions in JSON format and will try to apply it to blockchain.

### Successful return

When successful, it will return HTTP 200 and transaction ID.

```json
{
  "transaction_id": "..."
}
```

Just because the transaction is conducted locally does not mean that the transaction has been merged into one block.

### Error return

If an error occurs, it will return HTTP 400 (invalid parameter) or 500 (internal server error)

```
HTTP/1.1 500 Internal Server Error
Content-Length: 1466
...error message...
```

## push_transactions

Push multiple transactions at a time.

### push_transactions usage example

```bash
curl  http://localhost:8888/v1/chain/push_transaction -X POST -d '[{"ref_block_num":"101","ref_block_prefix":"4159312339","expiration":"2017-09-25T06:28:49","scope":["initb","initc"],"actions":[{"code":"currency","type":"transfer","recipients":["initb","initc"],"authorization":[{"account":"initb","permission":"active"}],"data":"000000000041934b000000008041934be803000000000000"}],"signatures":[],"authorizations":[]}, {"ref_block_num":"101","ref_block_prefix":"4159312339","expiration":"2017-09-25T06:28:49","scope":["inita","initc"],"actions":[{"code":"currency","type":"transfer","recipients":["inita","initc"],"authorization":[{"account":"inita","permission":"active"}],"data":"000000008040934b000000008041934be803000000000000"}],"signatures":[],"authorizations":[]}]'
```

## get_required_keys

Get required private keys and sign the transaction from the key list.

### get_required_keys usage example

```bash
curl  http://localhost:8888/v1/chain/get_required_keys -X POST -d '{"transaction": {"ref_block_num":"100","ref_block_prefix":"137469861","expiration":"2017-09-25T06:28:49","scope":["initb","initc"],"actions":[{"code":"currency","type":"transfer","recipients":["initb","initc"],"authorization":[{"account":"initb","permission":"active"}],"data":"000000000041934b000000008041934be803000000000000"}],"signatures":[],"authorizations":[]}, "available_keys":["EOS4toFS3YXEQCkuuw1aqDLrtHim86Gz9u3hBdcBw5KNPZcursVHq","EOS7d9A3uLe6As66jzN8j44TXJUqJSK3bFjjEEqR4oTvNAB3iM9SA","EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV"]}'```
```

### get_required_keys result example

```json
{
  "required_keys": [
    "EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV"
  ]
}
```

## get_required_keys

Get required keys and sign the transaction from the key list.

### get_required_keys usage example

```bash
curl  http://localhost:8888/v1/chain/get_required_keys -X POST -d '{"transaction": {"ref_block_num":"100","ref_block_prefix":"137469861","expiration":"2017-09-25T06:28:49","scope":["initb","initc"],"actions":[{"code":"currency","type":"transfer","recipients":["initb","initc"],"authorization":[{"account":"initb","permission":"active"}],"data":"000000000041934b000000008041934be803000000000000"}],"signatures":[],"authorizations":[]}, "available_keys":["EOS4toFS3YXEQCkuuw1aqDLrtHim86Gz9u3hBdcBw5KNPZcursVHq","EOS7d9A3uLe6As66jzN8j44TXJUqJSK3bFjjEEqR4oTvNAB3iM9SA","EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV"]}'```
```

### get_required_keys result example

```json
{
  "required_keys": [
    "EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV"
  ]
}
```

# Wallet RPC


## wallet_create

Create a wallet with given name.

### wallet_create usage example

```bash
$ curl http://localhost:8889/v1/wallet/create -X POST -d '"default"'
```

### wallet_create result example

This command will return the password that can be used to unlock the wallet in the future.

```
PW5KFWYKqvt63d4iNvedfDEPVZL227D3RQ1zpVFzuUwhMAJmRAYyX
```

## wallet_open

Open an existing wallet with the given name.

### wallet_open usage example

```bash
$ curl http://localhost:8889/v1/wallet/open -X POST -d '"default"'
```

### wallet_open result example

```json
{}
```

## wallet_lock_all

Lock all wallets.

### wallet_lock_all usage example

```bash
$ curl http://localhost:8889/v1/wallet/lock_all 
```

### wallet_lock_all result example

```json
{}
```

## wallet_unlock

Unlock the wallet with the given name and password.

### wallet_unlock usage example

```bash
$ curl http://localhost:8889/v1/wallet/unlock -X POST -d '["default", "PW5KFWYKqvt63d4iNvedfDEPVZL227D3RQ1zpVFzuUwhMAJmRAYyX"]'
```

### wallet_unlock result example

```json
{}
```

## wallet_list

List all wallets.

### wallet_list usage example

```bash
$ curl http://localhost:8889/v1/wallet/list_wallets
```

### wallet_list result example

```json
["default *"]

```

## wallet_list_keys

List all private keys in all wallets.

### wallet_list_keys usage example

```bash
$ curl http://localhost:8889/v1/wallet/list_keys
```

### wallet_list_keys result example

```json
[["EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV","5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3"]]

```

## wallet_get_public_keys

List all public keys in all wallets.

### wallet_get_public_keys usage example

```bash
$ curl http://localhost:8889/v1/wallet/get_public_keys 
```

### wallet_get_public_keys result example

```json
["EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV"]
```

## wallet_set_timeout

Set the wallet auto lock timeout (in seconds).

### wallet_set_timeout usage example

```bash
$ curl http://localhost:8889/v1/wallet/set_timeout -X POST -d '10'
```

### wallet_set_timeout result example

```json
{}
```

## wallet_sign_trx

Given the signature transaction of a transaction array, the public key and Chain ID are required

### wallet_sign_trx usage example

```bash
$ curl http://localhost:8889/v1/wallet/sign_transaction -X POST -d '[{"ref_block_num":21453,"ref_block_prefix":3165644999,"expiration":"2017-12-08T10:28:49","scope":["initb","initc"],"read_scope":[],"messages":[{"code":"currency","type":"transfer","authorization":[{"account":"initb","permission":"active"}],"data":"000000008093dd74000000000094dd74e803000000000000"}],"signatures":[]}, ["EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV"], ""]'```
```

### wallet_sign_trx result example

```json
{
  "ref_block_num": 21453,
  "ref_block_prefix": 3165644999,
  "expiration": "2017-12-08T10:28:49",
  "scope": [
    "initb",
    "initc"
  ],
  "read_scope": [],
  "messages": [
    {
      "code": "currency",
      "type": "transfer",
      "authorization": [
        {
          "account": "initb",
          "permission": "active"
        }
      ],
      "data": "000000008093dd74000000000094dd74e803000000000000"
    }
  ],
  "signatures": [
    "1f393cc5ce6a6951fb53b11812345bcf14ffd978b07be386fd639eaf440bca7dca16b14833ec661ca0703d15e55a2a599a36d55ce78c4539433f6ce8bcee0158c3"
  ]
}
```
