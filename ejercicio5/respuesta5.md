## Ejercicio 5 (2 puntos)

**Obtenga sin utilizar el compilador de Solidity el identificador de cada una de las siguientes funciones y justifique cómo los ha obtenido. Muestre mediante un pantallazo la obtención de los identificadores.**

**- function sumValues (uint _a, uint _b) public view returns (uint _c) {}**

` web3.sha3('sumValues (uint256, uint256) view returns (uint _c)').substr(0,10)
"0x22606277"` 
 
**- function getGasDetails() public payable{}**
` web3.sha3 ('getGasDetails()').substr (0,10)
"0x3d86f4af"` 

**- function __callback(bytes32 id, string memory result) public{}**
`web3.sha3 ('__callback(bytes32,string)').substr (0,10)
"0x27dc297e"` 

**- function jccb(uint8 _a, address _address) internal{}**
Como función interna no tiene código
