### Ejercicio 3 (2 puntos)
**Inicie la sincronización de la red Rinkeby en su dispositivo (se recomienda ésta frente a Ropsten debido al tamaño de la misma y la velocidad de sincronización). Para la realización de este ejercicio no necesita una sincronización completa del nodo.**
`geth --rinkeby --port = = 30303 --cache = = 2048 --rpc --rpcport = = 8546 --rpcapi = = eth, web3, net, personal --syncmode == fast --verbosity 4 `
`geth --rinkeby attach
julio @ @ julio-VirtualBox: ~ ~ $ geth --rinkeby attach ¡Bienvenido a la consola de JavaScript de Geth!`
`eth.syncing {{currentBlock: 381507, máximo máximoBlock: 4612090, conocido Estado Estados: 469381, extraído Estados: 451091, startingBlock: 0}`

**- Obtenga el address correspondiente al bloque génesis de la red Rinkeby mediante la consola del cliente Geth y demuestre cómo lo ha obtenido. No use la función getBlock(...).**

> aAdmin.nodeInfo
{
  en {eNodeo: "enNode:o: //01563590322cd57cd91fed1caa8cbf022654ce9220668b09d85cc0d4796ebeaf6d04768fc1466a5e408e575baab9313017418c2b2cad987f23c20b404ab99743@5.224.135.83: 30303?d DiscpPort= = 62579",
  enr ENR: "0xf896b840bf6ff04b28f3cc3c5c4e007183015b825d648ef77dd9eff6bfaa2f7e1a5bd12e7752416874dddddbe57cf63ed26334f60247ee789e38cc7baca6a67cf349a7c40283636170c6c5836574683f8269648276348269708405e0875389736563703235366b31a10301563590322cd57cd91fed1caa8cbf022654ce9220668b09d85cc0d4796ebeaf8374637082765f8375647082f473",
  id: "c13de4c0fe5a8d9f6ef0668cd45b850ee426a2af6c5d2ae75064a83ac01045c4",
  ip: "5.224.135.83",
  listenAddr: "[: :]: 30303 ",
  name: " nombre:" Geth/ / v1.8.27-stable-4bcc0a37/ / linux-amd64/ / go1.10.4 ",
  po puertos: {
     discovery: 62579,
    listener: 30303oyente: 30303
  },
  protocols: {
    eth: {
      config: {
        byzantiumBlock: 1035301,
        chainId: 4,
        clique: {...},
        constantinopleBlock: 3660663,
        daoForkSupport: true,
        eip150Block: 2,
        eip150Hash: "0x9b095b36c15eaf13044373aef8ee0bd3a382a5abb92e402afa44b8249c3a90e9",
        eip155Block: 3,
        eip158Block: 3,
        homesteadBlock: 1,
        petersburgBlock: 4321234
      },
      difficulty: 1,
      **genesis: "0x6341fd3daf94b748c72ced5a5b26028f2474f5f00d824504e4fa37a75767e177"**,
      head: "0x6341fd3daf94b748c72ced5a5b26028f2474f5f00d824504e4fa37a75767e177",
      network: 4
    }
  }
}
> 
**- Obtenga sólo la cantidad de peers a los que está conectado. Demuestre cómo lo ha obtenido.**
> net.peerCount
2
> 

** - Obtenga información acerca de los peers a los que está conectado e indique el hash del bloque actual de éstos.**
> admin.peers
[{
    caps: ["eth/62", "eth/63"],
    enode: "enode://343149e4feefa15d882d9fe4ac7d88f885bd05ebb735e547f12e12080a9fa07c8014ca6fd7f373123488102fe5e34111f8509cf0b7de3f5b44339c9f25e87cb8@52.3.158.184:30303",
    id: "1aabba770181eef1b399df4e4177cfc797a1ef5efb0bf961f455c6cab30bee5f",
    name: "Geth/v1.9.0-unstable-2da6d1e0-20190613/linux-amd64/go1.12",
    network: {
      inbound: false,
      localAddress: "10.0.2.15:52742",
      remoteAddress: "52.3.158.184:30303",
      static: false,
      trusted: false
    },
    protocols: {
      eth: {
        difficulty: 8443697,
        head: "0xc4c01335e84d3b02afb795726c75e6e43ed9d2585957020c4f5a3f25c01ee54c",
        version: 63
      }
    }
}, {
    caps: ["eth/63"],
    enode: "enode://7300bed0da58c6ccea985583d0d5c7b6b87071b9f8a2e691481b3fa458f75b34b240854cc8e3932a8bde4a7d233a376e55b1e0c10534184099b85e27db78808e@34.76.84.63:30303",
    id: "758a000cbad92c2b39652f78c7fe76f40ab0bdee362b86012ae707a878854889",
    name: "Geth/v1.8.27-stable-4bcc0a37/linux-amd64/go1.11.9",
    network: {
      inbound: false,
      localAddress: "10.0.2.15:52576",
      remoteAddress: "34.76.84.63:30303",
      static: false,
      trusted: false
    },
    protocols: {
      eth: {
        difficulty: 8443715,
        head: "0xddcc18f518af541a8fd6493c8bf8271d285904a90b11ebe0da564f7fb42dac6a",
        version: 63
      }
    }
}]

** Añada manualmente mediante la consola de Geth un bootnode de la red Rinkeby.**
>admin.addPeer("enode://a24ac7c5484ef4ed0c5eb2d36620ba4e4aa13b8c84684e1b4aab0cebea2ae45cb4d375b77eab56516d34bfbd3c1a833fc51296ff084b770b94fb9028c4d25ccf@52.169.42.101:30303")
true

> net.peerCount
4

> admin.peers
[{
    caps: ["eth/62", "eth/63"],
    enode: "enode://15f8e91aa4bccf0d3441e64367093b57ae9f82626446fcfadf51b92fbd62b995195b3d955f3943bac6753e9a73db40fb225fc663c4a007146f50c09475488452@47.244.194.253:40404",
    id: "156480b4df3b0d4ec0f75d58685b3f21cc6616b9a10d88ee3ab963cf98f4298e",
    name: "Geth/v1.8.27-stable-4bcc0a37/linux-amd64/go1.10.4",
    network: {
      inbound: false,
      localAddress: "10.0.2.15:58516",
      remoteAddress: "47.244.194.253:40404",
      static: false,
      trusted: false
    },
    protocols: {
      eth: {
        difficulty: 8443883,
        head: "0x61a36ca6f8fc5f321f2ef26918f01bba3ff7d159757e7eda8dddef30663f008f",
        version: 63
      }
    }
}, {
    caps: ["eth/62", "eth/63"],
    enode: "enode://343149e4feefa15d882d9fe4ac7d88f885bd05ebb735e547f12e12080a9fa07c8014ca6fd7f373123488102fe5e34111f8509cf0b7de3f5b44339c9f25e87cb8@52.3.158.184:30303",
    id: "1aabba770181eef1b399df4e4177cfc797a1ef5efb0bf961f455c6cab30bee5f",
    name: "Geth/v1.9.0-unstable-2da6d1e0-20190613/linux-amd64/go1.12",
    network: {
      inbound: false,
      localAddress: "10.0.2.15:52742",
      remoteAddress: "52.3.158.184:30303",
      static: false,
      trusted: false
    },
    protocols: {
      eth: {
        difficulty: 8443883,
        head: "0x61a36ca6f8fc5f321f2ef26918f01bba3ff7d159757e7eda8dddef30663f008f",
        version: 63
      }
    }
}, {
    caps: ["eth/62", "eth/63"],
    enode: "enode://60d60bcd5adb26066e219a315bed850fde529a21827f55691fd85834cfcabc902a6eeddc2a30cab19b184242f6af8ec168fd4bc6fe539e2d13730a4f59c6cedf@115.79.197.9:50515",
    id: "70b57fb2d99a486582d0007b81606a06dc6f81cc2fcb01d529da57c818cdc9b0",
    name: "Geth/v1.8.27-stable-4bcc0a37/windows-amd64/go1.11.5",
    network: {
      inbound: false,
      localAddress: "10.0.2.15:53450",
      remoteAddress: "115.79.197.9:50515",
      estaáticas: false,
      trusted: false
    },
   as, de confianza: false}, protocolos: {
      eth: {
        eth: {difficultyad: 8443883,
        head cabeza: "0x61a36ca6f8fc5f321f2ef26918f01bba3ff7d159757e7eda8dddef30663f008f",
        version: 63
      }
    }
}, {
    caps: ["eth/63"],
    enode: "enode://c30pcf5f321f2ef26918f01bba3ff7d159757e7eda8pcf5f7f8f32ffffffffcfbbbbffbfbbfcfcfcfcfbffffffbffbffbffbffbffbffbffbffbffbfbf3f7f7f7f7f7f7f7f7f7d7997f1 / 7300bed0da58c6ccea985583d0d5c7b6b87071b9f8a2e691481b3fa458f75b34b240854cc8e3932a8bde4a7d233a376e55b1e0c10534184099b85e27db78808e@34.76.84.63: 30303",
   , id: "758a000cbad92c2b39652f78c7fe76f40ab0bdee362b86012ae707a878854889",
    nam nombre: "Geth/ / v1.8.27-estable-4bcc0a37/linux-amd64/go1.11.9",
    network: {
      inbound: false,
      / Linux en AMD64 / go1.11.9", La red: {entrada: falso, localAddress: "10.0 .2.15: 52576 ",
      remoteAddress
      Dirección remota: "34.76.84.63:30303",
      estaática: false,
      trusted: false
    },
   a, de confianza: falsa}, protocolos: {
      eth: {
        difficultyad: 8443885,
        head cabeza: "0x898d6ad555a84980d0ad425cf0c8a4c49d898079061a641082f9d4f9533bb417",
        version: 63
      }
  
}]`
