# Streaming Electricity Marketplace

***
## 【Introduction of the Streaming Electricity Marketplace】
- This is a smart contract that allow a buyer to be able to buy electricity with subscription (streaming) plan.
- Libraries and smart contracts of below are used for implementing this smart contract.
  - Streamr (for subscription) 
  - Provable Things (for oracle of electricity price)

&nbsp;

***

## 【Workflow】
- ① A producer create the electricity as a product.   
  At that time,   
  - a product ID for the electricity is published.  
  - Subscription fees and subscription period are defined by a producer.  
- ② A buyer buy the electricity as a product which they prefer by paying for subscription fees.   
- ③ Once subscription period is expired, a buyer can extend subscription period by paying for subscription fees again.  


&nbsp;

***

## 【Remarks】
- Version for following the Streamer smart contract
  - Solidity (Solc): v0.5.16
  - Truffle: v5.1.60
  - web3.js: v1.2.9
  - openzeppelin-solidity: v2.5.0
  - ganache-cli: v6.9.1 (ganache-core: 2.10.2)


&nbsp;

***

## 【Setup】
### ① Install modules
- Install npm modules in the root directory
```
$ npm install
```

<br>

- Install npm modules in the `./ethereum-bridge` directory
```
$ cd ethereum-bridge
$ npm install
```

<br>

### ② Compile & migrate contracts (on local)
```
$ npm run migrate:local
```

<br>

### ③ Test (Mainnet-fork approach)
- 1: Start ganache-cli
```
$ ganache-cli
```

<br>

- 2: Start ethereum-bridge
```
$ node bridge -H localhost:8545 -a 1
```

<br>

- 3: Execute test of the smart-contracts (on the local)
  - Test for the ElectricityPriceOracle contract
    `$ npm run test:oracle`
    (truffle test ./test/test-local/ElectricityPriceOracle.test.js)

  - Test for the StreamingElectricityMarketplace contracts
    `$ npm run test:streaming`  
    ($ truffle test ./test/test-local/StreamingElectricityMarketplace.test.js)

<br>


***

## 【References】
- Streamr
  - Marketplace smart-contract（Solidity v0.5.16）：https://github.com/streamr-dev/marketplace-contracts 
  - Doc（Data Union）：https://streamr.network/docs/data-unions/intro-to-data-unions
  - Devpost（Hacker Guide）：https://oceandec.devpost.com/details/hackerguide
  - Slide：https://docs.google.com/presentation/d/1QjBD3s-2fS-CrETtPAHrSR4PuFFSRFvvimJOCQbmvGI/edit#slide=id.g875ff90d1f_0_0
  - Streamr Data Challenge 2021：https://www.streamrdatachallenge.com

<br>

- Provable Things
    - oraclizeAPI_0.5.sol:   
      https://github.com/provable-things/ethereum-api/blob/master/oraclizeAPI_0.5.sol  

    - ethereum-bridge:  
      https://github.com/provable-things/ethereum-bridge  

    - Testing Provable's Diesel Prices Example  
      - DieselPrice.sol  
        https://github.com/provable-things/ethereum-examples/blob/master/solidity/truffle-examples/diesel-price/contracts/DieselPrice.sol
      - Test（diesel-price-test.js）  
        https://github.com/provable-things/ethereum-examples/blob/master/solidity/truffle-examples/diesel-price/test/diesel-price-test.js  

<br>

- Energy Web Foundation (EWF)
  - Data for your contracts: Oracles with Oraclize
    https://energyweb.atlassian.net/wiki/spaces/EWF/pages/558432257/Data+for+your+contracts+Oracles+with+Oraclize

    - Method for getting the Electric Price：
      - FuelPrice.sol: https://github.com/ngyam/tutorial-oraclize/blob/master/contracts/FuelPrice.sol 
      - Test of FuelPrice.sol: https://github.com/ngyam/tutorial-oraclize/blob/master/test/response.js

    - Test query tool (provided by the Provable Things)：  
      https://app.provable.xyz/home/test_query  
