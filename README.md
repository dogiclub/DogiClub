# Dogiclub Art
Dogiclub Art are first of its kind Doggies like TRC20 [check here](https://github.com/TRC20org/TRC20) on the TRON blockchain using the hex data inscriptions format.

## Number of Dogiclub Members
1111

## Method
 - mint: `data:image/png;base64,XGpUY8Lw7RYMUZmPSYrjzmA485j58+kwc+vKZePtNXl0mZjGvONFZVzRmhL+XvPcdY+H5TKxeY2H5TJKa7LrMHN5mu8zXeZrM+sYz9TP3MczQ95o+80feGn3ho94aIaPeGiGmHVAysBKQ0Qg0SuCpUqVKlQOFy5c3RhGcuFfTqVwEMGcwGZm8x8uczcIxDA5zAYGUwuWTM3AymJBzgjLYMHgUuLxCHAk04OjMFde8kBI5e11jkiAlisuj922MKPyyq`
 - transfer: TBA

## Mint Dogiclub with nodejs
1. Install Node.js
2. Create a directory, such as `DogiclubTRX`
3. Open `DogiclubTRX`, execute command:`npm init`
4. Execute command:`npm install tronweb`
5. Create an index.js file, copy the code below
6. Pick a `base64_data` from `dogiclub_data.json`
7. Run index.js: `node index.js` 

```
const TronWeb = require('tronweb');
const HttpProvider = TronWeb.providers.HttpProvider;
const fullNode = new HttpProvider("https://api.trongrid.io");
const solidityNode = new HttpProvider("https://api.trongrid.io");
const eventServer = new HttpProvider("https://api.trongrid.io");
const privateKey = "your privateKey"; //
const tronWeb = new TronWeb(fullNode, solidityNode, eventServer, privateKey);

const blackHole = "TMFHAfhyAs981DqcE74g76MmbS3jLTMTdX";  //black hole address

const memo = 'data:image/png;base64,XGpUY8Lw7RYMUZmPSYrjzmA485j58+kwc+vKZePtNXl0mZjGvONFZVzRmhL+XvPcdY+H5TKxeY2H5TJKa7LrMHN5mu8zXeZrM+sYz9TP3MczQ95o+80feGn3ho94aIaPeGiGmHVAysBKQ0Qg0SuCpUqVKlQOFy5c3RhGcuFfTqVwEMGcwGZm8x8uczcIxDA5zAYGUwuWTM3AymJBzgjLYMHgUuLxCHAk04OjMFde8kBI5e11jkiAlisuj922MKPyyq';  

async function main() {

    const unSignedTxn = await tronWeb.transactionBuilder.sendTrx(blackHole, 69); 
    const unSignedTxnWithNote = await tronWeb.transactionBuilder.addUpdateData(unSignedTxn, memo, 'utf8');
    const signedTxn = await tronWeb.trx.sign(unSignedTxnWithNote);
    console.log("signed =>", signedTxn);
    const ret = await tronWeb.trx.sendRawTransaction(signedTxn);
    console.log("broadcast =>", ret);
}

main().then(() => {

    })
    .catch((err) => {
        console.log("error:", err);
    });
```

## Mint TRXI with TokenPocket Wallet
 - Receiver address:TMFHAfhyAs981DqcE74g76MmbS3jLTMTdX.
 - Transfer amount 69 TRX
 - Click on Advanced Settings and fill in `data:image/png;base64,XGpUY8Lw7RYMUZmPSYrjzmA485j58+kwc+vKZePtNXl0mZjGvONFZVzRmhL+XvPcdY+H5TKxeY2H5TJKa7LrMHN5mu8zXeZrM+sYz9TP3MczQ95o+80feGn3ho94aIaPeGiGmHVAysBKQ0Qg0SuCpUqVKlQOFy5c3RhGcuFfTqVwEMGcwGZm8x8uczcIxDA5zAYGUwuWTM3AymJBzgjLYMHgUuLxCHAk04OjMFde8kBI5e11jkiAlisuj922MKPyyq`



## Idea for developing indexer
1. Get all transactions of black hole address and see which unique mints are first.
2. Use the FULL NODE HTTP API to get the `from`,`to`,`data` field of each txid, match all mint inscriptions. For more details, please refer to the following link: https://developers.tron.network/reference/wallet-gettransactionbyid.
3. The obtained addresses need to undergo encoding conversion to Tron wallet addresses. For more details, please refer to the following link: https://www.btcschools.net/tron/tron_tool_base58check_hex.php.

## Indexer(TBA)





