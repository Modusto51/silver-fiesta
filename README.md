Main logo
Search for transactions, addresses, blocks and embedded text data...


API
API documentation
API documentation
Introduction
General stats endpoints
Retrieve overall information about blockchains and tokens
Stats on multiple blockchains at once
Bitcoin-like blockchain stats
Ethereum-like blockchain stats
Ripple-like blockchain stats
Stellar-like blockchain stats
Monero-like blockchain stats
Cardano-like blockchain stats
Mixin-like DAG stats
Omni Layer stats
ERC-20 stats
Dashboard endpoints
Retrieve information about various entities in a neat format from our databases
Raw data endpoints
Retrieve raw information about various entities directly from our full nodes
Infinitable endpoints
SQL-like queries: filter, sort, and aggregate blockchain data
Misc endpoints
Privacy-o-meter
News aggregator
Support
Show all
Blockchair API
Blockchair API
Blockchair API provides developers, researchers, and businesses with access to data contained in 14 blockchains
Explore pricing plans
General stats endpoints
Stats on multiple blockchains at once
Allows to retrieve the most important stats on all blockchains we support via just one API request.

Endpoint:

https://api.blockchair.com/stats
If you require data on just one blockchain, please use https://api.blockchair.com/{:chain}/stats instead.

Output:

data contains an array with stats on 15 blockchains we support at once:

Bitcoin
Bitcoin Cash
Ethereum
Litecoin
Bitcoin SV
Dogecoin
Dash
Ripple
Groestlcoin
Stellar
Monero
Cardano
Zcash
Mixin
eCash
and on 3 cross-chain tokens:

Tether (USDT)
USD Coin (USDC)
Binance USD (BUSD)
Note that Bitcoin Testnet stats are not included in this output.

Description of the fields is available in the next three sections of documentation.

Example output:

https://api.blockchair.com/stats:

{
  "data": {
    "bitcoin": {
      "data": {
        "blocks": 599952,
        ...
      }
    },
    "bitcoin-cash": {
      "data": {
        "blocks": 605134,
        ...
      }
    },
    "bitcoin-sv": {
      "data": {
        "blocks": 604886,
        ...
      }
    },
    "ethereum": {
      "data": {
        "blocks": 8766052,
        ...
      }
    },
    "litecoin": {
      "data": {
        "blocks": 1721519,
        ...
      }
    },
    "dogecoin": {
      "data": {
        "blocks": 2941267,
        ...
      }
    },
    "dash": {
      "data": {
        "blocks": 1156197,
        ...
      }
    },
    "ripple": {
      "data": {
        "ledgers": 50795982,
        ...
      }
    },
    "groestlcoin": {
      "data": {
        "blocks": 2801282,
        ...
      }
    },
    "stellar": {
      "data": {
        "ledgers": 26968006,
        ...
      }
    },
    "monero": {
      "data": {
        "blocks": 2014108,
        ...
      }
    },
    "cardano": {
      "data": {
        "blocks": 3673733,
        ...
      }
    },
    "zcash": {
      "data": {
        "blocks": 756512,
        ...
      }
    },
    "mixin": {
      "data": {
        "snapshots": 18632532,
        ...
      }
    },
    "cross-chain": {
      "tether": {
        "data": ...
      },
      "usd-coin": {
        "data": ...
      },
      "binance-usd": {
        "data": ...
      }
    }
  },
  "context": {
    "code": 200,
    ...
    }
  }
}
Request cost formula:

Always 1.

Explore visualizations on our front-end:

https://blockchair.com/
https://blockchair.com/compare
Bitcoin-like blockchain stats
Endpoints:

https://api.blockchair.com/bitcoin/stats
https://api.blockchair.com/bitcoin-cash/stats
https://api.blockchair.com/litecoin/stats
https://api.blockchair.com/bitcoin-sv/stats
https://api.blockchair.com/dogecoin/stats
https://api.blockchair.com/dash/stats
https://api.blockchair.com/groestlcoin/stats
https://api.blockchair.com/zcash/stats
https://api.blockchair.com/ecash/stats
https://api.blockchair.com/bitcoin/testnet/stats
Output:

data contains an array with blockchain statistics:

blocks — total number of blocks (note that it's 1 more than the latest block number as there is block #0)
transactions — total number of transactions
outputs — total number of outputs (including spent)
circulation — number of coins in circulation (in satoshi)
blockchain_size — total size of all blocks in bytes (note: it's not the size of a full node, it's just bare blocks; nodes are bigger in size as they use database indexing, etc)
nodes— number of full network nodes (it's an approximate number and actually not a blockchain metric)
difficulty — current mining difficulty
hashrate_24h — approximated hashrate over the last 24 hours (returned as a string as it doesn't fit into an integer)
next_retarget_time_estimate — approximate timestamp of the next difficulty retarget (this field is available for Bitcoin and Litecoin only)
next_difficulty_estimate — approximate next difficulty value (this field is available for Bitcoin and Litecoin only)
best_block_height — the latest block height
best_block_hash — the latest block hash
best_block_time — the latest block time
mempool_transactions — number of transactions in the mempool
mempool_outputs — number of outputs in the mempool
mempool_size — mempool size in bytes
mempool_tps — number of transactions per second added to the mempool
mempool_total_fee_usd — sum of transaction fees in the mempool, in USD
blocks_24h — number of blocks mined over the last 24 hours
transactions_24h — number of transactions confirmed over the last 24 hours
volume_24h — total monetary volume of transactions over the last 24 hours
average_transaction_fee_24h — average transaction fee over the last 24 hours
average_transaction_fee_usd_24h — the same in USD
median_transaction_fee_24h— median transaction fee over the last 24 hours
median_transaction_fee_usd_24h — the same in USD
inflation_24h— number of new coins mined over the last 24 hours (in satoshi), this can be considered as the daily inflation
inflation_usd_24h — the same in USD
cdd_24h— total coindays destroyed over the last 24 hours
largest_transaction_24h — array of hash and value_usd — biggest payment over the last 24 hours
market_price_usd — average market price of 1 coin in USD (market data source: CoinGecko)
market_price_btc — average market price of 1 coin in BTC (for Bitcoin it always returns 1)
market_price_usd_change_24h_percentage — market price change in percent for 24 hours
market_cap_usd — market capitalization (coins in circulation * price per coin in USD)
market_dominance_percentage — dominance index (how much % of the total cryptocurrency market is the market capitalization of the coin)
countdowns (optional) — an optional array of events ([event, time_left] format), where time_left is the number of seconds till the event
suggested_transaction_fee_per_byte_sat — suggests a proper transaction fee in satoshi per byte based on the latest block
hodling_addresses — the total number of addresses with positive balance
Example output:

https://api.blockchair.com/bitcoin/stats:

{
  "data": {
    "blocks": 690165,
    "transactions": 654248075,
    "outputs": 1776138129,
    "circulation": 1875100229497096,
    "blocks_24h": 130,
    "transactions_24h": 229726,
    "difficulty": 14363025673660,
    "volume_24h": 187713267560047,
    "mempool_transactions": 6591,
    "mempool_outputs": 16532,
    "mempool_size": 5076549,
    "mempool_tps": 5.416666666666667,
    "mempool_total_fee_usd": 14219.1005,
    "best_block_height": 690164,
    "best_block_hash": "000000000000000000023fcb3703bf89ddbfc1ef5109f21c2387a9d630b78c6e",
    "best_block_time": "2021-07-08 14:37:00",
    "blockchain_size": 353767186147,
    "average_transaction_fee_24h": 14421,
    "inflation_24h": 81250000000,
    "median_transaction_fee_24h": 5269,
    "cdd_24h": 3696149.5996842394,
    "mempool_outputs": 44316,
    "largest_transaction_24h": {
      "hash": "7a83c11f42dadad1c6916cceb079835aa09ed70127dba7cdf15aa904277c907d",
      "value_usd": 773548352
    },
    "nodes": 8502,
    "hashrate_24h": "92904707138521187685",
    "inflation_usd_24h": 26587437.5,
    "average_transaction_fee_usd_24h": 4.719001232335435,
    "median_transaction_fee_usd_24h": 1.724338485,
    "market_price_usd": 32723,
    "market_price_btc": 1,
    "market_price_usd_change_24h_percentage": -5.7534,
    "market_cap_usd": 613578128025,
    "market_dominance_percentage": 43.03,
    "next_retarget_time_estimate": "2021-07-18 19:23:20",
    "next_difficulty_estimate": 17958208674260,
    "countdowns": [],
    "suggested_transaction_fee_per_byte_sat": 17,
    "hodling_addresses": 38343147
  },
  "context": {
    "code": 200,
    ...
  }
}
Request cost formula:

Always 1.

Explore visualizations on our front-end:

https://blockchair.com/bitcoin
https://blockchair.com/bitcoin-cash
https://blockchair.com/litecoin
https://blockchair.com/bitcoin-sv
https://blockchair.com/dogecoin
https://blockchair.com/dash
https://blockchair.com/groestlcoin
https://blockchair.com/zcash
https://blockchair.com/ecash
https://blockchair.com/bitcoin/testnet
Ethereum-like blockchain stats
Endpoints:

https://api.blockchair.com/ethereum/stats
https://api.blockchair.com/ethereum/testnet/stats
Output:

data contains an array with blockchain statistics:

blocks — total number of blocks (note that it's 1 more than the latest block number as there is block #0)
uncles — total number of uncles
transactions — total number of transactions
calls — total number of internal calls
circulation_approximate — number of coins in circulation (in wei)
blockchain_size — total size of all blocks in bytes (note: it's not the size of a full node, it's just bare blocks; nodes are bigger in size as they use database indexing, etc)
difficulty — current mining difficulty
hashrate_24h — approximated hashrate over the last 24 hours (returned as a string as it doesn't fit into an integer)
best_block_height — the latest block height
best_block_hash — the latest block hash
best_block_time — the latest block time
mempool_transactions — number of transactions in the mempool
mempool_median_gas_price — median gas price of transactions in the mempool
mempool_tps — number of transactions per second added to the mempool
mempool_total_value_approximate — sum of transaction amounts in the mempool, in wei
blocks_24h — number of blocks mined over the last 24 hours
uncles_24h — number of uncles over the last 24 hours
transactions_24h — number of transactions confirmed over the last 24 hours
volume_24h_approximate — total monetary volume of transactions over the last 24 hours
average_transaction_fee_24h — average transaction fee over the last 24 hours
average_transaction_fee_usd_24h — the same in USD
median_transaction_fee_24h— median transaction fee over the last 24 hours
median_transaction_fee_usd_24h — the same in USD
average_simple_transaction_fee_24h — average simple transfer (i.e. just sending ethers for 21.000 gas) fee over the last 24 hours
average_simple_transaction_fee_usd_24h — the same in USD
median_simple_transaction_fee_24h— median simple transfer fee over the last 24 hours
median_simple_transaction_fee_usd_24h — the same in USD
inflation_24h— number of new coins mined over the last 24 hours (in satoshi), this can be considered as the daily inflation
inflation_usd_24h — the same in USD
largest_transaction_24h: array of hash and value_usd — biggest payment over the last 24 hours
market_price_usd — average market price of 1 coin in USD (market data source: CoinGecko)
market_price_btc — average market price of 1 coin in BTC
market_price_usd_change_24h_percentage — market price change in percent for 24 hours
market_cap_usd — market capitalization (coins in circulation * price per coin in USD)
market_dominance_percentage — dominance index (how much % of the total cryptocurrency market is the market capitalization of the coin)
countdowns (optional) — an optional array of events ([event, time_left] format), where time_left is the number of seconds till the event
layer_2.erc_20 — an array of stats on the ERC-20 token layer consisting of the following elements:
tokens — total number of created ERC-20 tokens (which have at least 1 transaction)
transactions — total number of ERC-20 transfers
tokens_24h — number of tokens created over the last 24 hours
transactions_24h — total number of ERC-20 transfers over the last 24 hours
suggested_transaction_fee_gwei_options — recommended transaction fees in gwei. It has 5 options: sloth for occasions when take the risk and wait; slow, normal, and fast if you want to get the transaction confirmed within 2-10 minutes; cheetah for an almost guaranteed next-block confirmation
Example output:

https://api.blockchair.com/ethereum/stats:

{
  "data": {
    "blocks": 12023239,
    "transactions": 1043567165,
    "blocks_24h": 6433,
    "circulation_approximate": "115018182780730000000000000",
    "transactions_24h": 1302619,
    "difficulty": 5447494005324207,
    "volume_24h_approximate": "6300512633065118000000000",
    "mempool_transactions": 94866,
    "mempool_median_gas_price": 40000000000,
    "mempool_tps": 7.983333333333333,
    "mempool_total_value_approximate": "77011108570302550000000",
    "best_block_height": 12023240,
    "best_block_hash": "4338ee00f57c8d0bfcb5e9bbbdc47ab40d9685e2b41801541acda53da71132f3",
    "best_block_time": "2021-03-12 10:43:40",
    "uncles": 1121915,
    "uncles_24h": 307,
    "blockchain_size": 213678005011,
    "calls": 3032610029,
    "average_transaction_fee_24h": "9339692912924509",
    "median_transaction_fee_24h": "4887620538746249",
    "inflation_24h": 13411.4375,
    "average_simple_transaction_fee_24h": "2947056048574188",
    "median_simple_transaction_fee_24h": "3129000000000000",
    "largest_transaction_24h": {
      "hash": "0xbc4fc78885355694f0a5ffe27af7e2157f323855a4e40beaf37905e3f3617640",
      "value_usd": 872236755.0026
    },
    "hashrate_24h": "453957833777017",
    "inflation_usd_24h": 23792024.239375,
    "average_transaction_fee_usd_24h": 16.56870862445721,
    "median_transaction_fee_usd_24h": 8.670687711941234,
    "average_simple_transaction_fee_usd_24h": 5.228106900731096,
    "median_simple_transaction_fee_usd_24h": 5.55087729,
    "market_price_usd": 1774.01,
    "market_price_btc": 0.031517784173684,
    "market_price_usd_change_24h_percentage": 0.95673,
    "market_cap_usd": 203352392960,
    "market_dominance_percentage": 11.66,
    "layer_2": {
      "erc_20": {
        "tokens": 246816,
        "transactions": 604957673,
        "tokens_24h": 100,
        "transactions_24h": 859287
      }
    },
    "countdowns": [
      {
        "event": "eth2 launch",
        "eth_staked": 3487170.000069,
        "eth_needed": 524288
      }
    ],
    "suggested_transaction_fee_gwei_options": {
      "sloth": 102,
      "slow": 115,
      "normal": 122,
      "fast": 134,
      "cheetah": 173
    }
  },
  "context": {
    "code": 200,
    "state": 12023239,
    "state_layer_2": 12023239,
    "request_cost": 1,
    ...
  }
}
Request cost formula:

Always 1.

Explore visualization on our front-end:

https://blockchair.com/ethereum
https://blockchair.com/ethereum/testnet
Ripple-like blockchain stats
Endpoint:

https://api.blockchair.com/ripple/stats
Output:

data contains an array with blockchain statistics:

ledgers — total number of ledgers
circulation — number of coins in circulation (in XRP)
best_ledger_height — the latest ledger number
best_ledger_hash — the latest ledger hash
best_ledger_time — the latest ledger time
mempool_transactions — number of unconfirmed transactions
mempool_tps — number of transactions per second added to the mempool
mempool_total_fee_usd — sum of transaction fees in the mempool, in USD
ledgers_24h — number of ledgers closed over the last 24 hours
transactions_24h — number of transactions confirmed over the last 24 hours
volume_24h — total monetary volume of transactions over the last 24 hours
average_transaction_fee_24h — average transaction fee over the last 24 hours
average_transaction_fee_usd_24h — the same in USD
median_transaction_fee_24h— median transaction fee over the last 24 hours
median_transaction_fee_usd_24h — the same in USD
inflation_24h— number of new coins issued over the last 24 hours (can be negative in case more coins are destroyed than issued)
inflation_usd_24h — the same in USD
largest_transaction_24h: array of hash and value_usd — biggest payment over the last 24 hours
market_price_usd — average market price of 1 coin in USD (market data source: CoinGecko)
market_price_btc — average market price of 1 coin in BTC
market_price_usd_change_24h_percentage — market price change in percent for 24 hours
market_cap_usd — market capitalization (coins in circulation * price per coin in USD)
market_dominance_percentage — dominance index (how much % of the total cryptocurrency market is the market capitalization of the coin)
countdowns (optional) — an optional array of events ([event, time_left] format), where time_left is the number of seconds till the event
Example output:

https://api.blockchair.com/ripple/stats:

{
  "data": {
    "market_price_usd": 0.290587,
    "market_price_btc": 0.0000365637358586,
    "market_price_usd_change_24h_percentage": -3.31938,
    "market_cap_usd": 12543700763,
    "market_dominance_percentage": 5.78,
    "ledgers": 50795576,
    "best_ledger_height": 50795575,
    "best_ledger_hash": "07AFA06C63D6C24C31CBD83938A711C098D6C251EEAFC7AE65733CEA3D5EE32A",
    "best_ledger_time": "2019-10-18 16:28:41",
    "mempool_transactions": 43,
    "mempool_total_fee_usd": 0.00024496484099999997,
    "circulation": 99991318056632960,
    "average_transaction_fee_24h": 874.9259920487995,
    "median_transaction_fee_24h": 12,
    "average_transaction_fee_usd_24h": 0.00025366991765268457,
    "median_transaction_fee_usd_24h": 0.000003479196,
    "ledgers_24h": 22359,
    "transactions_24h": 864272,
    "mempool_tps": 10.003148148148147,
    "inflation_24h": -756174037,
    "inflation_usd_24h": -219.239807069521,
    "volume_24h": 712237245463407,
    "largest_transaction_24h": {
      "hash": "A773E7C3D07D76834280766AF7F90FE7E773E8D5AD77327A603BD6A5B1083611",
      "value_usd": 14496650
    }
  },
  "context": {
    "code": 200,
    ...
  }
}
Request cost formula:

Always 1.

Explore visualization on our front-end:

https://blockchair.com/ripple
Stellar-like blockchain stats
Endpoint:

https://api.blockchair.com/stellar/stats
Output:

data contains an array with blockchain statistics:

ledgers — total number of ledgers
circulation — number of coins in circulation (in stroops)
best_ledger_height — the latest ledger number
best_ledger_hash — the latest ledger hash
best_ledger_time — the latest ledger time
ledgers_24h — number of ledgers closed over the last 24 hours
transactions_24h — number of transactions confirmed over the last 24 hours
successful_transactions_24h— number of successful transactions over the last 24 hours
failed_transactions_24h— number of failed transactions over the last 24 hours
operations_24h — number of operations over the last 24 hours
average_transaction_fee_24h — average transaction fee over the last 24 hours
average_transaction_fee_usd_24h — the same in USD
market_price_usd — average market price of 1 coin in USD (market data source: CoinGecko)
market_price_btc — average market price of 1 coin in BTC
market_price_usd_change_24h_percentage — market price change in percent for 24 hours
market_cap_usd — market capitalization (coins in circulation * price per coin in USD)
market_dominance_percentage — dominance index (how much % of the total cryptocurrency market is the market capitalization of the coin)
countdowns (optional) — an optional array of events ([event, time_left] format), where time_left is the number of seconds till the event
Example output:

https://api.blockchair.com/stellar/stats:

{
  "data": {
    "ledgers": 26602978,
    "best_ledger_height": 26602978,
    "best_ledger_hash": "3151f16e9a6ce9ee43f57a068c83a04c7e864ccc7d1027519d42aab79e13b40f",
    "best_ledger_time": "2019-11-02 16:42:01",
    "circulation": 1054439020873472900,
    "ledgers_24h": 15643,
    "transactions_24h": 461072,
    "successful_transactions_24h": 285958,
    "failed_transactions_24h": 175114,
    "operations_24h": 1085466,
    "average_transaction_fee_24h": 283.5731513695005,
    "average_transaction_fee_usd_24h": 0.000001991250668916633,
    "market_price_usd": 0.07022,
    "market_price_btc": 0.0000075229454120425,
    "market_price_usd_change_24h_percentage": 3.41847,
    "market_cap_usd": 1406714595,
    "market_dominance_percentage": 0.56
  },
  "context": {
    "code": 200,
    ...
  }
}
Request cost formula:

Always 1.

Explore visualization on our front-end:

https://blockchair.com/stellar
Monero-like blockchain stats
Endpoint:

https://api.blockchair.com/monero/stats
Output:

data contains an array with blockchain statistics:

blocks — total number of blocks (note that it's 1 more than the latest block number as there is block #0)
transactions — total number of transactions
circulation — number of coins in circulation (in satoshi)
blockchain_size — total size of all blocks in bytes (note: it's not the size of a full node, it's just bare blocks; nodes are bigger in size as they use database indexing, etc)
difficulty — current mining difficulty
best_block_height — the latest block height
best_block_hash — the latest block hash
best_block_time — the latest block time
mempool_transactions — number of transactions in the mempool
mempool_size — mempool size in bytes
market_price_usd — average market price of 1 coin in USD (market data source: CoinGecko)
market_price_btc — average market price of 1 coin in BTC
market_price_usd_change_24h_percentage — market price change in percent for 24 hours
market_cap_usd — market capitalization (coins in circulation * price per coin in USD)
market_dominance_percentage — dominance index (how much % of the total cryptocurrency market is the market capitalization of the coin)
countdowns (optional) — an optional array of events ([event, time_left] format), where time_left is the number of seconds till the event
suggested_transaction_fee_per_byte_sat — suggests a proper transaction fee in piconero per byte
Example output:

https://api.blockchair.com/stellar/stats:

{
  "data": {
    "blocks": 2012711,
    "transactions": 6147319,
    "circulation": 17402679371662576000,
    "difficulty": 127374112357,
    "hashrate_24h": 1061450936,
    "mempool_transactions": 140,
    "mempool_size": 681994000,
    "best_block_height": 2012710,
    "best_block_hash": "3cfcac0ccd9e058f56158686fd4d7258351071e113feac9c1b10da65ce62cce5",
    "best_block_time": "2020-01-16 20:42:47",
    "suggested_transaction_fee_per_byte_sat": 13,
    "market_price_usd": 79.36,
    "market_price_btc": 0.0079091090293004,
    "market_price_usd_change_24h_percentage": -0.96449,
    "market_cap_usd": 1362957367,
    "market_dominance_percentage": 0.52
  },
  "context": {
    "code": 200,
    ...
  }
}
Request cost formula:

Always 1.

Explore visualizations on our front-end:

https://blockchair.com/monero
Cardano-like blockchain stats
Endpoint:

https://api.blockchair.com/cardano/stats
Output:

data contains an array with blockchain statistics:

blocks — total number of blocks
transactions — total number of transactions
circulation — number of coins in circulation (in satoshi)
blockchain_size — total size of all blocks in bytes (note: it's not the size of a full node, it's just bare blocks; nodes are bigger in size as they use database indexing, etc)
best_block_epoch — the latest epoch number
best_block_slot — the latest slot number
best_block_height — the latest block height
best_block_hash — the latest block hash
best_block_time — the latest block time
blocks_24h — number of blocks over the last 24 hours
transactions_24h — number of transactions over the last 24 hours
market_price_usd — average market price of 1 coin in USD (market data source: CoinGecko)
market_price_btc — average market price of 1 coin in BTC
market_price_usd_change_24h_percentage — market price change in percent for 24 hours
market_cap_usd — market capitalization (coins in circulation * price per coin in USD)
market_dominance_percentage — dominance index (how much % of the total cryptocurrency market is the market capitalization of the coin)
countdowns (optional) — an optional array of events ([event, time_left] format), where time_left is the number of seconds till the event
Example output:

https://api.blockchair.com/cardano/stats:

{
  "data": {
    "blocks": 3673733,
    "transactions": 1725714,
    "best_block_epoch": 170,
    "best_block_slot": 3790,
    "best_block_height": 3673733,
    "best_block_hash": "d70406d8707105b333f2107d6d786316f8232fd8c7beb9565b02f134fe1c03f2",
    "best_block_time": "2020-01-22 18:48:11",
    "blocks_24h": 4320,
    "transactions_24h": 1987,
    "circulation": 31112169560261348,
    "blockchain_size": 3474703715,
    "market_price_usd": 0.04703496,
    "market_price_btc": 0.000004687558301774,
    "market_price_usd_change_24h_percentage": -3.43458,
    "market_cap_usd": 1465483381,
    "market_dominance_percentage": 0.55
  },
  "context": {
    "code": 200,
    ...
  }
}
Request cost formula:

Always 1.

Explore visualizations on our front-end:

https://blockchair.com/cardano
Mixin-like DAG stats
Endpoint:

https://api.blockchair.com/mixin/stats
Output:

data contains an array with DAG statistics:

snapshots — total number of snapshots
snapshots_24h — number of snapshots over the last 24 hours
transactions_24h — number of transactions over the last 24 hours
mempool_transactions — number of unvonfirmed transactions
tps_24h — transactions per second over 24 hours period
best_snapshot_height — the latest snapshot number
best_snapshot_hash — the latest snapshots hash
best_snapshot_time — the latest snapshot time (UTC)
circulation — number of coins in circulation (smallest denomination)
circulation_xin — number of coins in circulation (in XINs)
market_price_usd — average market price of 1 coin in USD (market data source: CoinGecko)
market_price_btc — average market price of 1 coin in BTC
market_price_usd_change_24h_percentage — market price change in percent for 24 hours
market_cap_usd — market capitalization (coins in circulation * price per coin in USD)
market_dominance_percentage — dominance index (how much % of the total cryptocurrency market is the market capitalization of the coin)
countdowns (optional) — an optional array of events ([event, time_left] format), where time_left is the number of seconds till the event
accepted_nodes — number of accepted network nodes
mintings — number of coin mintings
Example output:

https://api.blockchair.com/mixin/stats:

{
  "data": {
    "snapshots": 18626733,
    "snapshots_24h": 135000,
    "transactions_24h": 135000,
    "mempool_transactions": 0,
    "tps_24h": 1.5625,
    "best_snapshot_height": 18626732,
    "best_snapshot_hash": "6cc46ccbd753dbaf09c1a72d94225af0aaabc5c0c1f705939c7ea77515d6d18c",
    "best_snapshot_time": "2020-04-22 16:33:08",
    "circulation_xin": 550991.78082032,
    "circulation": 55099178082032,
    "market_price_usd": 168.06,
    "market_price_btc": 0.02323,
    "market_price_usd_change_24h_percentage": 2.901,
    "market_cap_usd": 84247126,
    "market_dominance_percentage": 0.01,
    "accepted_nodes": 22,
    "mintings": 419
  },
  "context": {
    "code": 200,
    "state": 18626733,
    ...
  }
}
Request cost formula:

Always 1.

Explore visualizations on our front-end:

https://blockchair.com/mixin
Omni Layer stats
Allows to retrieve the some basic stats on Omni Layer (Bitcoin). Note that this endpoint is in the Alpha stage, and Wormhole (Bitcoin Cash Omni-like token system) was phased out on January 1st, 2020.

Endpoint:

https://api.blockchair.com/bitcoin/omni/stats
Output:

data contains an array with second layer statistics:

properties — total number of created properties
properties_mainnet — total number of "mainnet" properties
properties_testnet — total number of "testnet" properties
transactions_approximate — approximate number of transactions
latest_transactions — array of 10 latest transactions
Note that the "mainnet" and "testnet" terms don't imply using Bitcoin Testnet, the idea behind that is "testnet" properties still live on the Bitcoin Mainnet, but they have should have no monetary value, and their purpose is for testing only.

Example request:

https://api.blockchair.com/bitcoin/omni/stats
Example output:

https://api.blockchair.com/bitcoin/omni/stats:

{
  "data": {
    "properties": 1187,
    "properties_mainnet": 751,
    "properties_testnet": 436,
    "transactions_approximate": 14406305,
    "latest_transactions": [
      {
        "property_id": 31,
        "property_name": "TetherUS",
        "type_id": 0,
        "type": "Simple Send",
        "sender": "1B4dCsH6MC9XoZ6ob2nngvJesYEfNNtMQS",
        "recipient": "1FoWyxwPXuj4C6abqwhjDWdz6D4PZgYRjA",
        "valid": false,
        "amount": 960000,
        "transaction_hash": "ee1f0401cae15e5ad35cc760c99aacc8c25f21814f234bd80038b99d0ec83d9c",
        "time": "2019-10-18 19:34:28"
      },
      ...
    ]
  },
  "context": {
    "code": 200,
    "state": 599972,
    ...
  }
}
Request cost formula:

Always 1.

Explore visualization on our front-end:

https://blockchair.com/bitcoin/omni
ERC-20 stats
There's no separate endpoint to get ERC-20 stats, use https://api.blockchair.com/ethereum/stats instead which includes ERC-20 info. Description is available here

Explorers
Aptos
Arbitrum One
Avalanche
Base
Beacon Chain
Bitcoin
Bitcoin Cash
BNB
BOB
Botanix
Cardano
Dash
DigiByte
Dogecoin
eCash
Ethereum
Ethereum Classic
Fantom
Gnosis Chain
Groestlcoin
Tether USD
USD Coin
Binance USD
Handshake
Kusama
Linea
Liquid Network
Litecoin
Monero
Moonbeam
opBNB
Optimism
Peercoin
Polkadot
Polygon
Polygon zkEVM
Rootstock
Sei EVM
Solana
Stellar
The Open Network
TRON
XRP Ledger
Zcash
Data
API
Datasets
Charts
ENS Lookup New
Services
Blockchair News
Blockchair Donut
Blockchair Awesome
Products
Transaction receipts
Wallet statements
Portfolio tracker
Broadcast transaction
Privacy-o-meter
Node explorers
Release monitor
Halving countdown
Compare blockchains
Get Blockchair extension
Useful links
About Blockchair
FAQ
Changelog
Careers
Terms of service
Privacy policy
Blockchair Onion v3 URL 
For partners
Partnerships
Advertise with us
Brand kit
For developers
Submit a bug or request
Bug bounty program
API documentation
Status
Social
Twitter
Telegram
GitHub
LinkedIn
Languages
English
Español
Français
Italiano
Nederlands
Português
Русский
中文
فارسی
Вahasa Indonesia
Türkçe
日本語
한국어
Deutsch
© 2025 Blockchair
Footer Blockchair logoNo 3d party trackers
Works without javascript
2.0.2-549-g245b7183c [72] Wed 19 Mar 2025 18:58:13 UTC –
