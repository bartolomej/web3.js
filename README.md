<p style="text-align: center;">
  <img src="assets/logo/web3js.jpg" width="200" alt="web3.js">
</p>

# web3.js - Ethereum JavaScript API

This is a modified version of the web3.js library, which only includes the `web3-eth-abi` package.

## Usage

This was adapted so that it can be used in BigQuery SQL. To use it yourself, upload `./dist/web3.min.js` file to Google Cloud bucket storage and use it like so:

```sql
CREATE TEMP FUNCTION myFunc()
RETURNS STRING
LANGUAGE js
OPTIONS (
library=['gs://lib-source/web3.min.js'])
AS r"""
const web3 = new window.Web3();

const decoded = web3.decodeLog([
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
            // Value emit was added just recently
            // https://github.com/ensdomains/ens-contracts/commit/d5174e4572d4143342d237ec8017d6e0da90bc7d
            // {
                //   type: 'string',
                //   name: 'value',
                // }
                ],
                '0x000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000000066176617461720000000000000000000000000000000000000000000000000000',
                [
                "0xd8c9334b1a9c2f9da342a0a2b32629c1a229b6445dad78947f674b44444a7550",
                "0xf6ed4a4a8c7d4df88c25a6ec2f3868a66e3bc9c6f2a7481dfd0c3ea7d32d2129",
                "0xd1f86c93d831119ad98fe983e643a7431e4ac992e3ead6e3007f4dd1adf66343"
                ]
                );

console.log(decoded)

return decoded.key;
""";

SELECT myFunc();
```