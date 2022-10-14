<p style="text-align: center;">
  <img src="assets/logo/web3js.jpg" width="200" alt="web3.js">
</p>

# web3.js - Ethereum JavaScript API

[![NPM Package Downloads][npm-image-downloads]][npm-url] [![cdnhits][cdnhits-image]][cdnhits-url] [![Discord][discord-image]][discord-url] [![StackExchange][stackexchange-image]][stackexchange-url] [![NPM Package Version][npm-image-version]][npm-url] [![Build Status][actions-image]][actions-url]  [![Coverage Status][coveralls-image]][coveralls-url] [![Lerna][lerna-image]][lerna-url] [![Netlify Status][netlify-image]][netlify-url] [![GitPOAP Badge][gitpoap-image]][gitpoap-url] [![Twitter][twitter-image]][twitter-url]

This is a modified version of the web3.js library, which only includes the `web3-eth-abi` package.

## Usage

For use in browser envirnoment, see [example.html](./example.html)
```js
const Web3 = require('web3');
const web3 = new Web3();

const decoded = web3.eth.abi.decodeLog([
        {
            type: 'bytes32',
            name: 'node',
            indexed: true
        },
        {
            type: 'string',
            name: 'indexedKey',
            indexed: true
        },
        {
            type: 'string',
            name: 'key',
        },
    ],
    '0x000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000000066176617461720000000000000000000000000000000000000000000000000000',
    [
        "0xd8c9334b1a9c2f9da342a0a2b32629c1a229b6445dad78947f674b44444a7550",
        "0xf6ed4a4a8c7d4df88c25a6ec2f3868a66e3bc9c6f2a7481dfd0c3ea7d32d2129",
        "0xd1f86c93d831119ad98fe983e643a7431e4ac992e3ead6e3007f4dd1adf66343"
    ]
);

console.log(decoded)
```