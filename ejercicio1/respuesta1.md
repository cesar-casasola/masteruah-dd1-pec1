## Instalación del cliente Ethereum: geth

**Ejercicio 1 (2 puntos)
Construya y configure su propia blockchain a partir de un archivo génesis que usted
mismo debe definir. Se recomienda el uso del cliente Geth.**

**- Cree una cuenta mediante el cliente Geth.**

- Instalación de geth
`sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install ethereum`

- Creamos una nueva cuenta
`julio@julio-VirtualBox:~$ geth --datadir ethdata account new
INFO [06-20|19:12:03.193] Maximum peer count                       ETH=25 LES=0 total=25
Your new account is locked with a password. Please give a password. Do not forget this password.
Passphrase: 
Repeat passphrase: 
Address: {0125ea3a4db84c10cad3ae02fa405a8fc1963352}
julio@julio-VirtualBox:~$`

- Creamos el fichero 'genesis.json'
`{
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
}`

- Creamos la red privada con el nodo genesis
`geth --datadir="ethdata" init genesis.json`

- Lanzamos un nodo en la nueva red con la cuenta anterior (0125ea3a4db84c10cad3ae02fa405a8fc1963352) como coinbase para recibir los ethers de minado
`geth --etherbase '0125ea3a4db84c10cad3ae02fa405a8fc1963352' --mine --datadir="ethdata" --networkid 15 --nodiscover console --unlock 0125ea3a4db84c10cad3ae02fa405a8fc1963352 --rpc --rpcport "8000" --rpcaddr "0.0.0.0" --rpccorsdomain "*" --rpcapi "eth,net,web3,miner,debug,personal,rpc"`

**- Consiga su propio Ether a partir de la minería.**

- Comprobamos las cuentas que tenemos actualmente
`eth.accounts
["0x0125ea3a4db84c10cad3ae02fa405a8fc1963352"]` 

- Recuperamos el balance de nuestra cuenta (solo tenemos una)
`web3.fromWei(eth.getBalance(eth.accounts[0]), "ether");`

- Activamos la minería durante unos momentos para recibir algunos ethers en nuestra dirección:
`miner.start()
miner.stop()`

- Comprobamos de nuevo el balance
`web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")
25` 

- Volvemos a activar la minería y enviamos una transacción sobre nuestra propia cuenta 
`miner.start()
eth.sendTransaction({from: eth.coinbase, to: eth.accounts[0], value: web3.toWei(10, "ether")})
web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")
miner.stop()`

- Comprobamos de nuevo el balance. A los ethers enviados se han añadido los ethers resultado de la minería
`web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")
220` 
