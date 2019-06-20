### Instalación del cliente Ethereum: geth

sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install ethereum

geth --datadir ethdata account new


julio@julio-VirtualBox:~$ geth --datadir ethdata account new
INFO [06-20|19:12:03.193] Maximum peer count                       ETH=25 LES=0 total=25
Your new account is locked with a password. Please give a password. Do not forget this password.
Passphrase: 
Repeat passphrase: 
Address: {0125ea3a4db84c10cad3ae02fa405a8fc1963352}
julio@julio-VirtualBox:~$ 



Fichero "genesis.json"
{

    "config":{
        "chainId":15,
        "homesteadBlock":0,
        "eip155Block":0,
        "eip158Block":0
    },
    "gasLimit":"2100000000",
    "alloc":{},
    "coinbase"   : "0x0000000000000000000000000000000000000000",
    "difficulty" : "0x20000",
    "extraData"  : "",
    "nonce"   : "0x0000000000000042",
    "mixhash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
    "parentHash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
    "timestamp"  : "0x00"

}

geth --datadir="ethdata" init genesis.json


geth --etherbase '0125ea3a4db84c10cad3ae02fa405a8fc1963352' --mine --datadir="ethdata" --networkid 15 --nodiscover console --unlock 0125ea3a4db84c10cad3ae02fa405a8fc1963352 --rpc --rpcport "8000" --rpcaddr "0.0.0.0" --rpccorsdomain "*" --rpcapi "eth,net,web3,miner,debug,personal,rpc"

web3.fromWei(eth.getBalance(eth.accounts[0]), "ether");

> eth.accounts
["0x0125ea3a4db84c10cad3ae02fa405a8fc1963352"]
> 

miner.start()
miner.stop()

> web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")
25
> 

miner.start()

eth.sendTransaction({from: eth.coinbase, to: eth.accounts[0], value: web3.toWei(10, "ether")})
web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")
miner.stop()

> web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")
220
> 


