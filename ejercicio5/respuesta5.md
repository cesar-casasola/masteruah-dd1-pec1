

web3.sha3('abr(uint8 _a, address _address) internal').substr(0,10)

- function sumValues (uint _a, uint _b) public view returns (uint _c) {}
- function getGasDetails() public payable{}
- function __callback(bytes32 id, string memory result) public{}
- function abr(uint8 _a, address _address) internal{}


> web3.sha3('sumValues (uint256, uint256) view returns (uint _c)').substr(0,10)
"0x22606277"
> 

> web3.sha3('getGasDetails() public payable').substr(0,10)
"0xdedd409b"
> 

> web3.sha3('function __callback(bytes32 id, string memory result) public').substr(0,10)
"0xce450f12"

> web3.sha3('abr(uint8 _a, address _address) internal').substr(0,10)
"0x8beaf4df"




