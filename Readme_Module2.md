# SMART CNTRACT CONECTION WITH METAMASK USING FRONTEND TO DISPLY IN WEB

This is a simple frontend web page used to connect the smart contract and metamask by linkng the ganache RPC server . This web page is diplayed while deplying the server on the web and can connect through metamask and smart contract and can change the data written over there

## Description

This frontend application uses the HTML, JAVASCRRIPT SOLIDITY for creating the page and so the require task so first of all i write the html designing code and created 4 buttons on the the web page which is used to connect the metamask , smart contract and retrieve data and can change the data using metamask etherum.

## Getting Started

### Installing

* Install MetaMask browser extension 
* A ganache install and  created an Etherum wallet and connect to MetaMask.
* The address and ABI (Application Binary Interface) of the smart contract you want to interact with.

### Executing program

1.Clone this repository to your local machine or download the HTML file.

2.3.Open the HTML file (index.html) in a web browser.

Make sure you have the Web3.js library included in your HTML file. In the provided code, the library is included using the following script tag:

4.If you prefer to use a different version or host the library locally, update the script tag accordingly.

5.Click the "CONNECTING  TO METAMASK" button. This will prompt you to connect your MetaMask wallet to the browser.

6.After connecting to MetaMask, your Ethereum account address will be displayed.

7.Click the "CONNECTING TO CONTRACT" button. This will connect to the specific smart contract using the provided contract address and ABI.

8.Once connected to the smart contract, the message "connected to smart contract" will be displayed.

9.You can now use the "GET MESSAGE FROM THE CONTRACT" button to retrieve the message stored in the smart contract. The message will be displayed below the button.

Similarly, you can use the "GET PRESENT MESSAGE FROM THE SMART CONTRACT" button to retrieve the number stored in the smart contract. The number will be displayed below the button.

<!DOCTYPE html>
<html>
<head>
    <title>SMART CONTRACT TEST</title>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/web3/1.2.7-rc.0/web3.min.js"></script>
    <style>
        body {
            background-color: #d1f485;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
        }
        .container {
            background-color: #ffffff;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            padding: 20px;
            margin: 10px;
            width: 300px;
        }
        h1 {
            font-size: 20px;
            color: #333;
            text-align: center;
        }
        button {
            background-color: #d566ed;
            color: white;
            font-size: 16px;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            margin-top: 10px;
            transition: background-color 0.3s ease;
        }
        button:hover {
            background-color: #42e8eb;
        }
        input {
            width: calc(100% - 20px);
            padding: 10px;
            font-size: 16px;
            margin-top: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        p {
            font-size: 14px;
            color: #555;
            background-color: #f9f9f9;
            padding: 10px;
            border-radius: 5px;
            margin-top: 10px;
            text-align: center;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Metamask Connection</h1>
        <button onclick="connectMetamask()">CONNECT TO METAMASK</button>
        <p id="accountArea">Connection Status: NOT CONNECTED to Metamask</p>
    </div>

    <div class="container">
        <h1>Smart Contract</h1>
        <button onclick="connectContract()">CONNECT TO CONTRACT</button>
        <p id="contractArea">Connection Status: NOT CONNECTED to Smart Contract</p>
    </div>

    <div class="container">
        <h1>Contract Data</h1>
        <button onclick="readWord()">GET MESSAGE FROM THE CONTRACT</button>
        <p id="dataArea">Data Status: NO Data from Smart Contract</p>
        <input type="text" id="inputArea" placeholder="Enter new data">
        <button onclick="changeWord()">CHANGE PRESENT MESSGAE ON THE SMART CONTRACT</button>
    </div>

    <script>
        let account;
        const connectMetamask = async () => {
            if (window.ethereum !== "undefined") {
                const accounts = await ethereum.request({ method: "eth_requestAccounts" });
                account = accounts[0];
                document.getElementById("accountArea").innerHTML = `Account is: ${account}`;
            }
        }

        const connectContract = async () => {
            const ABI = 
            [
	{
		"inputs": [
			{
				"internalType": "uint256",
				"name": "_number",
				"type": "uint256"
			}
		],
		"name": "changeNumber",
		"outputs": [],
		"stateMutability": "nonpayable",
		"type": "function"
	},
	{
		"inputs": [],
		"name": "getNumber",
		"outputs": [
			{
				"internalType": "uint256",
				"name": "",
				"type": "uint256"
			}
		],
		"stateMutability": "view",
		"type": "function"
	}
]
            const Address = "0xbBe36e9f8775D6F3a3f3CA120D8f2eF135bF67e7";
            window.web3 = await new Web3(window.ethereum);
            window.contract = await new window.web3.eth.Contract(ABI, Address);
            document.getElementById("contractArea").innerHTML = "Connection Status: Success";
        }

        const readWord = async () => {
            const data = await window.contract.methods.getNumber().call();
            document.getElementById("dataArea").innerHTML = `Number is: ${data}`;
        }

        const changeWord = async () => {
            const myEntry = document.getElementById("inputArea").value;
            await window.contract.methods.changeNumber(myEntry).send({ from: account });
        }
    </script>
</body>
</html>


## Help

1. Make sure MetaMask is properly set up and connected to the correct Ethereum network (e.g., Mainnet, Rinkeby,localganache etc.).
2. In the remix Choose the environment as Custon external HTTP Provider
3. While changing the number the metamask may get coneect to your old account 1 go and change the account and if error occur repeatedly then change the etherum address to some new address and it will work properly after that.

## Authors

Amrita Kumari

(https://www.linkedin.com/in/amrita-kumari-753319232/)



## License

//SPDX-License-Identifier: GPL-3.0
