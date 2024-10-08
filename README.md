# Ethereum-to-ICP
How Deposit ETH from Ethereum to ICP with ckEth
Here is a tutorial on how to deposit ETH from Ethereum to ICP using ckEth:


*Text Description:*

*Step 1: Install Required Tools*

- Install Node.js (>=14) and npm
- Install Truffle Suite (truffle, ganache-cli)
- Install Web3.js library

*Step 2: Set Up Ethereum Wallet*

- Create an Ethereum wallet (e.g., MetaMask)
- Fund the wallet with ETH

*Step 3: Set Up ICP Wallet*

- Create an ICP wallet (e.g., Plug Wallet)
- Fund the wallet with ICP

*Step 4: Install ckEth*

- Clone the ckEth repository: `git clone (link unavailable)
- Install dependencies: `npm install`

*Step 5: Configure ckEth*

- Set up ckEth configuration file (`config.js`):
    - Ethereum provider (e.g., `(link unavailable))
    - ICP provider (e.g., `(link unavailable)`)
    - Ethereum wallet address
    - ICP wallet address

*Step 6: Deposit ETH to ckEth*

- Run `truffle migrate` to deploy ckEth contracts
- Use `ckEth` CLI to deposit ETH:
    - `ckEth deposit --amount 1 --network ethereum`

*Step 7: Withdraw ETH from ckEth*

- Use `ckEth` CLI to withdraw ETH:
    - `ckEth withdraw --amount 1 --network icp`


*Frontend Code:*

Create a basic frontend using HTML, CSS, and JavaScript:


*index.html*
```
<!DOCTYPE html>
<html>
<head>
  <title>ckEth Deposit/Withdraw</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <h1>ckEth Deposit/Withdraw</h1>
  <form id="deposit-form">
    <label>Deposit Amount:</label>
    <input type="number" id="amount" />
    <button id="deposit-btn">Deposit</button>
  </form>
  <form id="withdraw-form">
    <label>Withdraw Amount:</label>
    <input type="number" id="amount" />
    <button id="withdraw-btn">Withdraw</button>
  </form>
  <script src="script.js"></script>
</body>
</html>
```


*styles.css*
```
body {
  font-family: Arial, sans-serif;
}

form {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 10px;
}

input[type="number"] {
  width: 100%;
  height: 40px;
  font-size: 24px;
  padding: 10px;
}

button {
  width: 100%;
  height: 40px;
  font-size: 24px;
  background-color: #4CAF50;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #3e8e41;
}
```


*script.js*
```
const depositForm = document.getElementById('deposit-form');
const withdrawForm = document.getElementById('withdraw-form');
const amountInput = document.getElementById('amount');

depositForm.addEventListener('submit', async (e) => {
  e.preventDefault();
  const amount = amountInput.value;
  // Call ckEth deposit function
  const response = await fetch('/deposit', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ amount }),
  });
  const result = await response.json();
  console.log(result);
});

withdrawForm.addEventListener('submit', async (e) => {
  e.preventDefault();
  const amount = amountInput.value;
  // Call ckEth withdraw function
  const response = await fetch('/withdraw', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ amount }),
  });
  const result = await response.json();
  console.log(result);
});
```


*Backend Code (Node.js):*

Create a Node.js server to handle deposit and withdraw requests:


*server.js*
```
const express = require('express');
const app = express();
const Web3 = require('web3');
const ckEth = require('ckEth');

const web3 = new Web3(new Web3.providers.HttpProvider('(link unavailable)'));
const ckEthInstance = new ckEth(web3);

app.use(express.json());

app.post('/deposit', async (req, res) => {
  const amount = req.body.amount;
  try {
    const result = await ckEthInstance.deposit(amount);
    res.json(result);
  } catch (error) {
    console.error(error);
```
