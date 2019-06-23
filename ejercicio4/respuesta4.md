ulio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ sudo apt-get install solc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libcvc4-4
The following NEW packages will be installed:
  libcvc4-4 solc
0 upgraded, 2 newly installed, 0 to remove and 312 not upgraded.
Need to get 5.468 kB of archives.
After this operation, 19,9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://es.archive.ubuntu.com/ubuntu bionic/universe amd64 libcvc4-4 amd64 1.5-1 [3.376 kB]
Get:2 http://ppa.launchpad.net/ethereum/ethereum/ubuntu bionic/main amd64 solc amd64 1:0.5.9-0ubuntu1~bionic [2.093 kB]
Fetched 5.468 kB in 3s (2.070 kB/s)                                 
Selecting previously unselected package libcvc4-4.
(Reading database ... 168702 files and directories currently installed.)
Preparing to unpack .../libcvc4-4_1.5-1_amd64.deb ...
Unpacking libcvc4-4 (1.5-1) ...
Selecting previously unselected package solc:amd64.
Preparing to unpack .../solc_1%3a0.5.9-0ubuntu1~bionic_amd64.deb ...
Unpacking solc:amd64 (1:0.5.9-0ubuntu1~bionic) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up libcvc4-4 (1.5-1) ...
Setting up solc:amd64 (1:0.5.9-0ubuntu1~bionic) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
julio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ 


julio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ solc example_pec1.sol --optimize --bin

======= example_pec1.sol:SimpleStorage =======
Binary: 
6080604052348015600f57600080fd5b5060a28061001e6000396000f3fe6080604052348015600f57600080fd5b506004361060325760003560e01c806360fe47b11460375780636d4ce63c146053575b600080fd5b605160048036036020811015604b57600080fd5b5035606b565b005b60596070565b60408051918252519081900360200190f35b600055565b6000549056fea165627a7a72305820a814f1677a75042bf2e1aca9a265a60ca3370a022a69d767e8947665c52b48d60029
julio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ 


---- CODIGOS DE OPERACION ----

julio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ solc example_pec1.sol --optimize --bin --opcodes

======= example_pec1.sol:SimpleStorage =======
Opcodes: 
PUSH1 0x80 PUSH1 0x40 MSTORE CALLVALUE DUP1 ISZERO PUSH1 0xF JUMPI PUSH1 0x0 DUP1 REVERT JUMPDEST POP PUSH1 0xA2 DUP1 PUSH2 0x1E PUSH1 0x0 CODECOPY PUSH1 0x0 RETURN INVALID PUSH1 0x80 PUSH1 0x40 MSTORE CALLVALUE DUP1 ISZERO PUSH1 0xF JUMPI PUSH1 0x0 DUP1 REVERT JUMPDEST POP PUSH1 0x4 CALLDATASIZE LT PUSH1 0x32 JUMPI PUSH1 0x0 CALLDATALOAD PUSH1 0xE0 SHR DUP1 PUSH4 0x60FE47B1 EQ PUSH1 0x37 JUMPI DUP1 PUSH4 0x6D4CE63C EQ PUSH1 0x53 JUMPI JUMPDEST PUSH1 0x0 DUP1 REVERT JUMPDEST PUSH1 0x51 PUSH1 0x4 DUP1 CALLDATASIZE SUB PUSH1 0x20 DUP2 LT ISZERO PUSH1 0x4B JUMPI PUSH1 0x0 DUP1 REVERT JUMPDEST POP CALLDATALOAD PUSH1 0x6B JUMP JUMPDEST STOP JUMPDEST PUSH1 0x59 PUSH1 0x70 JUMP JUMPDEST PUSH1 0x40 DUP1 MLOAD SWAP2 DUP3 MSTORE MLOAD SWAP1 DUP2 SWAP1 SUB PUSH1 0x20 ADD SWAP1 RETURN JUMPDEST PUSH1 0x0 SSTORE JUMP JUMPDEST PUSH1 0x0 SLOAD SWAP1 JUMP INVALID LOG1 PUSH6 0x627A7A723058 KECCAK256 0xa8 EQ CALL PUSH8 0x7A75042BF2E1ACA9 LOG2 PUSH6 0xA60CA3370A02 0x2a PUSH10 0xD767E8947665C52B48D6 STOP 0x29 
Binary: 
6080604052348015600f57600080fd5b5060a28061001e6000396000f3fe6080604052348015600f57600080fd5b506004361060325760003560e01c806360fe47b11460375780636d4ce63c146053575b600080fd5b605160048036036020811015604b57600080fd5b5035606b565b005b60596070565b60408051918252519081900360200190f35b600055565b6000549056fea165627a7a72305820a814f1677a75042bf2e1aca9a265a60ca3370a022a69d767e8947665c52b48d60029
julio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ 






---- IDENTIFICADOR DE LAS FUNCIONES ---

julio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ solc example_pec1.sol --optimize --bin --abi

======= example_pec1.sol:SimpleStorage =======
Binary: 
6080604052348015600f57600080fd5b5060a28061001e6000396000f3fe6080604052348015600f57600080fd5b506004361060325760003560e01c806360fe47b11460375780636d4ce63c146053575b600080fd5b605160048036036020811015604b57600080fd5b5035606b565b005b60596070565b60408051918252519081900360200190f35b600055565b6000549056fea165627a7a72305820a814f1677a75042bf2e1aca9a265a60ca3370a022a69d767e8947665c52b48d60029
Contract JSON ABI 
[{"constant":false,"inputs":[{"name":"x","type":"uint256"}],"name":"set","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"get","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"}]
julio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ 



julio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ solc example_pec1.sol --optimize --bin --hashes

======= example_pec1.sol:SimpleStorage =======
Binary: 
6080604052348015600f57600080fd5b5060a28061001e6000396000f3fe6080604052348015600f57600080fd5b506004361060325760003560e01c806360fe47b11460375780636d4ce63c146053575b600080fd5b605160048036036020811015604b57600080fd5b5035606b565b005b60596070565b60408051918252519081900360200190f35b600055565b6000549056fea165627a7a72305820a814f1677a75042bf2e1aca9a265a60ca3370a022a69d767e8947665c52b48d60029
Function signatures: 
6d4ce63c: get()
60fe47b1: set(uint256)
julio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ 


> web3.sha3('set(uint256)').substr(0,10)
"0x60fe47b1"

> web3.sha3('get()').substr(0,10)
"0x6d4ce63c"
> 


julio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ solc --gas example_pec1.sol

======= example_pec1.sol:SimpleStorage =======
Gas estimation:
construction:
   87 + 37800 = 37887
external:
   get():	413
   set(uint256):	20220
julio@julio-VirtualBox:~/masteruah-dd1-pec1/ejercicio4$ 

