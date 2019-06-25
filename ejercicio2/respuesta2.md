## Ejercicio 2 (2 puntos)
**1. A partir del ejercicio anterior, cree una nueva cuenta en su blockchain. Realice mediante el propio cliente Geth una transferencia de 1 Ether entre dos cuentas de esta blockchain.**

- Creación de una nueva cuenta
`personal.newAccount("master")
"0x8076915dd3824133ea730d7ee3762d93e09e2427"` 

- Mostramos las cuentas que tenemos actualmente
`eth.accounts
["0x0125ea3a4db84c10cad3ae02fa405a8fc1963352", "0x8076915dd3824133ea730d7ee3762d93e09e2427"]` 

- Comprobamos el saldo de cada cuenta
`web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")
220
web3.fromWei(eth.getBalance(eth.accounts[1]), "ether")
0`

- Llevamos a cabo una transacción desde la primera cuenta hasta la segunda
`eth.sendTransaction({from: eth.accounts[0], to: eth.accounts[1], value: web3.toWei(30, "ether")})
INFO [06-20|20:10:02.650] Submitted transaction                    fullhash=0x629357b667d30f63eb37baab3e9a51c6b7c3a5919bb51b1587ca7b782b95b0b9 recipient=0x8076915Dd3824133eA730d7ee3762D93E09E2427
"0x629357b667d30f63eb37baab3e9a51c6b7c3a5919bb51b1587ca7b782b95b0b9"` 

- Activamos la funcionalidad de minería el tiempo suficiente para confirmar la transacción
`miner.start()
miner.stop()`

- Comprobamos de nuevo el balance de la transacción
`web3.fromWei(eth.getBalance(eth.accounts[1]), "ether")
30`

**2. Realice mediante la consola de Truffle y conectado a una blockchain desplegada con Ganache una transferencia de 1 Ether entre dos cuentas de esta blockchain. Puede aprovechar el entorno creado en la actividad primera del bloque 1 (Truffle Pet Shop). **

- Comprobamos las cuentas del nodo de ganache desde el terminal de truffle:
`truffle(development)> web3.eth.getAccounts()
[ '0xfCDC6cc74375D72C77BAe4f4415FaE1fFE1a1427',
  '0x0290CD8311973AFCc102C747EEC54670ddE4F15E',
  '0xfEa3C5Fb247CC4DdBd6bE1ce2903a795D1Cfcc89',
  '0xd1e4561808508aF17Df1318Fd181B56B8610a505',
  '0xC51582ebEF117D0F850292Fa1A52EA938904533F',
  '0xc4D1dA4Db28FB36bD3A35B64A932F5072F05F001',
  '0x47e0d4169B3685627d753B15065fA6b69b6772Dc',
  '0x9bD165e3A4459601b020dED4627865edbb2b87a0',
  '0xD92B5ba7A2D8C5cB64f6CDB99f29f7E234e97B11',
  '0x7572431eB2978795A67760d6B1d747090579450a' ]
truffle(development)>`


- Llevamos a cabo una transacción desde el entorno de truffle:
`truffle(development)> web3.eth.sendTransaction({ from: '0xfEa3C5Fb247CC4DdBd6bE1ce2903a795D1Cfcc89', to: '0xC51582ebEF117D0F850292Fa1A52EA938904533F', value: 10 })
{ transactionHash: '0x7a3156d905becac1aa738659b3e2e7692654c9fc55d36854606d5490b5ee66c6',
  transactionIndex: 0,
  blockHash: '0xe399eb46ac0653747f5cc640cd7fa9162097b296e30ef023ed792c917ff7515f',
  blockNumber: 30,
  from: '0xfea3c5fb247cc4ddbd6be1ce2903a795d1cfcc89',
  to: '0xc51582ebef117d0f850292fa1a52ea938904533f',
  gasUsed: 21000,
  cumulativeGasUsed: 21000,
  contractAddress: null,
  logs: [],
  status: true,
  logsBloom: '0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000',
  v: '0x1c',
  r: '0x32f5b0a0a9571e7714f5c094aa943a3a203bedfc5e92103a945ada3a347f34c6',
  s: '0x206c09f18b1eb59bb34d33e1c8159c3d1f0117994cfe117d8c789b63e0fe13cc' }
truffle(development)>` 

- Comprobamos que el saldo se ha incrementado en 10 Ethers:
`truffle(development)> await web3.eth.getBalance('0xc51582ebef117d0f850292fa1a52ea938904533f')
'100000000000000000010'

- Si lanzamos una transacción para elviar 1 Ether comprobaremos que se incrementa el balance de la cuenta destino en 1 Ether
`truffle(development)> truffle(development)> web3.eth.sendTransaction({ from: '0xfEa3C5Fb247CC4DdBd6bE1ce2903a795D1Cfcc89', to: '0xC51582ebEF117D0F850292Fa1A52EA938904533F', value: 1 })
{ transactionHash: '0xc63fda7c9cba61543c70df26acd61cfb348dd7120e48b82e54bd186152033580',
  transactionIndex: 0,
  blockHash: '0x9c4d7c97dbf375c00b763bd90f9a2eac77307905f2c6f8c3cc5ac7737f41f428',
  blockNumber: 31,
  from: '0xfea3c5fb247cc4ddbd6be1ce2903a795d1cfcc89',
  to: '0xc51582ebef117d0f850292fa1a52ea938904533f',
  gasUsed: 21000,
  cumulativeGasUsed: 21000,
  contractAddress: null,
  logs: [],
  status: true,
  logsBloom: '0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000',
  v: '0x1b',
  r: '0x5b1b7ccf05779b68d218b6bcf2283b187c9c35a512536325afbcb38bd2633240',
  s: '0x704c6e7728b914d602d10ac04990ee1f8909188f8ea87cd2ae3d25afa60d5930' }
truffle(development)> await web3.eth.getBalance('0xc51582ebef117d0f850292fa1a52ea938904533f')
'100000000000000000011'
truffle(development)> `
