###  cree una nueva cuenta en su blockchain

> personal.newAccount("master")
"0x8076915dd3824133ea730d7ee3762d93e09e2427"
> 


> eth.accounts
["0x0125ea3a4db84c10cad3ae02fa405a8fc1963352", "0x8076915dd3824133ea730d7ee3762d93e09e2427"]
> 


> web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")
220
> 

> web3.fromWei(eth.getBalance(eth.accounts[1]), "ether")
0
> 

> eth.sendTransaction({from: eth.accounts[0], to: eth.accounts[1], value: web3.toWei(30, "ether")})
INFO [06-20|20:10:02.650] Submitted transaction                    fullhash=0x629357b667d30f63eb37baab3e9a51c6b7c3a5919bb51b1587ca7b782b95b0b9 recipient=0x8076915Dd3824133eA730d7ee3762D93E09E2427
"0x629357b667d30f63eb37baab3e9a51c6b7c3a5919bb51b1587ca7b782b95b0b9"
> 

> web3.fromWei(eth.getBalance(eth.accounts[1]), "ether")
0
miner.start()
miner.stop()

> web3.fromWei(eth.getBalance(eth.accounts[1]), "ether")
30
> 


