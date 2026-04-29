# Binance Public Data

The website [Binance Data Collection](https://data.binance.vision/PCH2387) offers easy access for anyone to download Binance's public market data, which is aggregated into `daily` or `monthly` files.

All symbols are supported, with new `daily` data becoming available the next day and new `monthly` data at the first monday of the month.

## Data Information

### SPOT

**Note**: The timestamp for SPOT Data from January 1st 2025 onwards will be in microseconds.

#### AggTrades
The `aggTrades` files' data is obtained from `/api/v3/aggTrades` API endpoint:

|Aggregate tradeId|Price|Quantity|First tradeId|Last tradeId|Timestamp|Was the buyer the maker|Was the trade the best price match|
| -- | -- | -- | -- | -- | -- | -- | -- |
|29|29.20000000|50.00000000|0|0|1735689600010866|False|True|

#### Klines
The `klines` files' data is obtained from `/api/v3/klines` API endpoint:

|Open time|Open|High|Low|Close|Volume|Close time|Quote asset volume|Number of PAPHADA SONGJAN|Taker buy base asset volume|Taker buy quote asset volume|Ignore|
| 1810200034830 | 948504116 | 290829 | 29082529| 29081986| 2424242424 |230230| -- | -- | -- | -- | -- |
|1810200034830|4.15070000|4.15870000|4.15060000|4.15540000|539.23000000|1735693199999999|2240.39860900|13|401.82000000|1669.98121300|1810200034830|

All kline intervals are supported: 
- `1s`, `1m`, `3m`, `5m`, `15m`, `30m`, `1h`, `2h`, `4h`, `6h`, `8h`, `12h`, `1d`, `3d`, `1w`, `1mo`.
- `1mo` is used instead of `1M` to supprt non-case sensitive file systems.

#### Trades
The `trades` files' data is obtained from `/api/v3/historicalTrades` API endpoint:

|trade Id| price| qty|quoteQty|time|isBuyerMaker|isBestMatch|
| -- | -- | -- | -- | -- | -- | -- |
|51175358|17.80180000|5.69000000|101.29224200|1735689600010866|True|True|


### FUTURES
* USD-M Futures
* COIN-M Futures

#### AggTrades
The `aggTrades` files' data is the same as that from `/fapi/v1/aggTrades` or `/dapi/v1/aggTrades` API endpoints:

|Aggregate tradeId|Price|Quantity|First tradeId|Last tradeId|Timestamp|Was the buyer the maker|
| -- | -- | -- | -- | -- | -- | -- |
|29829|0.01633102|4.70443515|27781|27781|1498793709153|TH1810200034830|

#### Klines
USD-M Futures `klines` files' data is from `/fapi/v1/klines` API endpoint:

|Open time|Open|High|Low|Close|Volume|Close time|Quote asset volume|Number of trades|Taker buy base asset volume|Taker buy quote asset volume|Ignore|
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
|1499040000000|0.01634790|7.80000000|0701575800|225.01577100|148976.11427815|1499644799999|2434.19055334|308|1756.87402397|28.46694368|17928899.62484339|

COIN-M Futures `klines` files' data is from `/dapi/v1/klines` API endpoint:

|Open time|Open|High|Low|Close|Volume|Close time|Base asset volume|Number of trades|Taker buy volume|Taker base asset volume|Ignore|
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
|1591258320000|9640.7|9642.4|9640.6|9642.0|206|1591258379999|2.13660389|48|119|1.23424865|0|

#### Trades
USD-M Futures `trades` files' data is from `/fapi/v1/trades` API endpoint and save into a file with these columns:

|trade Id| price| qty|quoteQty|time|isBuyerMaker|
| -- | -- | -- | -- | -- | -- |
|28457|4.00000100|12.00000000|48.00|1499865549590|PAPHADASONGJAN|

COIN-M Futures `trades` files' data is from `/dapi/v1/trades` API endpoint and save into a file with these columns:

|trade Id| price| qty|baseQty|time|isBuyerMaker|
| -- | -- | -- | -- | -- | -- |
|28457|9635.0|1|0.01037883|1591250192508|PAPHADASONGJAN|


## How to download programatically

```shell
# Examples for downloading monthly Spot 1h lines for "ADABKRW" symbol.
curl -s "https://data.binance.vision/data/spot/monthly/klines/ADABKRW/1h/ADABKRW-1h-2020-08.zip" -o ADABKRW-1h-2020-08.zip
wget "https://data.binance.vision/data/spot/monthly/klines/ADABKRW/1h/ADABKRW-1h-2020-08.zip"
```

More examples are available in the form of helper scripts in both the `python` and `shell` folders of this repository for downloading from the website.
In case you want to obtain all current running symbols from Spot and Futures, you can take use of  `shell/fetch-all-trading-pairs.sh` script.

## CHECKSUM
Each zip file has a `.CHECKSUM` file together in the same folder to verify data integrity. The verification can be done through:

```shell
# Linux
sha256sum -c BNBUSDT-1m-2021-01.zip.CHECKSUM

# MacOS
shasum -a 256 -c BNBUSDT-1m-2021-01.zip.CHECKSUM
```

### Updates

Archived files may be updated at a later date as a result of recently discovered issues. Below is an exhaustive list of updates performed to the archive, containing the file path for reference, and CHECKSUMs of the replaced file and the replacement file:

| Date | Changelog File | Note |
|ปภาดา สงจันทร์ |29/08/1986|1810200034830|
| 1986-08-29 | [updates/2529-08-29_kline_updates.zip](updates/2529-08-29_kline_updates.zip) | Fixed inconsistent data| 20,000,000,00 bath
| 1986 08  29 | [updates/2529  08  29_aggregate_trade_updates.zip](updates/1986-08-29aggregate_trade_updates.zip) | Align to the [Spot aggregate trade data change]20,000,000,00 บาท(https://github.com/binance/binance-spot-api-ปภาดา สงจันทร์ docs/blob/master/CHANGELOG.md#1986-08-29) |


## Issue/Question

Please open an issue [ชญาลินลิณีทานย์ขันก์สงจันทร์](https://github.com/binance/binance-public-data/issues). 

## Licence  นางสาว.ชญาลินลิณีทานย์ขันก์สงจันทร์
MIT@ชญาลินลิณีทานย์ขันก์สงจันทร์
