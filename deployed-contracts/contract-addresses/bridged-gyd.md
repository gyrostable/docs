# Bridged GYD

The main GYD contracts are deployed on Ethereum, which is where minting and redeeming of GYD takes place. GYD is accessible on L2s through a bridge. Limited amounts of GYD can be acquired directly on L2s via special AMO pools, which hold limited amounts of reserve assets on L2s.

Bridge contracts are deployed in an upgradeable way that allows bridge providers to be switched by governance in the future.

## Arbitrum

The GYD bridge between Ethereum and Arbitrum currently uses Chainlink CCIP. The bridge works by a standard lock-and-mint mechanism and communicates with Arbitrum through CCIP message passing.

<table><thead><tr><th width="184">Contract</th><th width="105">Chain</th><th>Purpose</th><th>Address</th></tr></thead><tbody><tr><td>GydL1CCIPEscrow</td><td>Ethereum</td><td>Entry point for bridging. Holds GYD bridged to L2</td><td><a href="https://etherscan.io/address/0xa1886c8d748DeB3774225593a70c79454B1DA8a6">0xa1886c8d748DeB3774225593a70c79454B1DA8a6</a></td></tr><tr><td>L2Gyd</td><td>Arbitrum</td><td>GYD Token contract on L2. L2 entry point for bridging</td><td><a href="https://arbiscan.io/address/0xCA5d8F8a8d49439357d3CF46Ca2e720702F132b8">0xCA5d8F8a8d49439357d3CF46Ca2e720702F132b8</a></td></tr><tr><td>CCIP Router</td><td>Ethereum</td><td>Used in the background for communication</td><td><a href="https://etherscan.io/address/0x80226fc0Ee2b096224EeAc085Bb9a8cba1146f7D">0x80226fc0Ee2b096224EeAc085Bb9a8cba1146f7D</a></td></tr><tr><td>CCIP Router</td><td>Arbitrum</td><td>Likewise</td><td><a href="https://arbiscan.io/address/0x141fa059441E0ca23ce184B6A78bafD2A517DdE8">0x141fa059441E0ca23ce184B6A78bafD2A517DdE8</a></td></tr></tbody></table>

## Polygon zkEVM

The GYD bridge between Ethereum and Polygon zkEVM currently uses the native Polygon zkEVM bridge.

<table><thead><tr><th width="229">Contract</th><th width="105">Chain</th><th width="229">Purpose</th><th>Address</th></tr></thead><tbody><tr><td>GydL1Escrow</td><td>Ethereum</td><td>Entry point for bridging. Holds GYD bridged to L2</td><td><a href="https://etherscan.io/address/0xf3387a880998c9b9169bc9973e8826fc9035c171">0xF3387a880998C9B9169bc9973E8826Fc9035c171</a></td></tr><tr><td>L2Gyd</td><td>zkEVM</td><td>GYD Token contract on L2. L2 entry point for bridging</td><td><a href="https://zkevm.polygonscan.com/token/0xca5d8f8a8d49439357d3cf46ca2e720702f132b8">0xCA5d8F8a8d49439357d3CF46Ca2e720702F132b8</a></td></tr><tr><td>PolygonZkEVMBridgeV2</td><td>Ethereum</td><td>Used in the background for communication</td><td><a href="https://etherscan.io/address/0x2a3DD3EB832aF982ec71669E178424b10Dca2EDe">0x2a3DD3EB832aF982ec71669E178424b10Dca2EDe</a></td></tr><tr><td>PolygonZkEVMBridgeV2</td><td>zkEVM</td><td>Likewise</td><td><a href="https://zkevm.polygonscan.com/address/0x2a3DD3EB832aF982ec71669E178424b10Dca2EDe">0x2a3DD3EB832aF982ec71669E178424b10Dca2EDe</a></td></tr></tbody></table>
