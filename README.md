
# Made by Ano.mobb


# Rubygen generator

Bitcoin Brainwallet Brute Forcer<br/>

#

```
Donate to the author of this program: 1GmQaG9R5NPs3ZzR6XPMD9jZk17F9MuoWn
```

#

# Installation

<b> Python 3.4.0 Required </b> 

<b>A Constant Internet Connection Is Required</b>

Installation: 

```
$ git clone https://github.com/mobb111/rubygen-master

$ cd rubygen

$ pip install -r requirements.txt 
```

#

# Usage

$ cd rubygen

$ python rubygen.py

New function added:

Enter number of passphrase



Select your API:
1) Bitcoinlegacy Blockexplorer
2) Blockchain
3) Blockexplorer
4) Bitpay




```
<br>

# Proof of Concept

This program is meant to analyze possible ways Bitcoin could be stolen. Because it is impossible to convert a wallet address back into its private key, this program goes from bip39 phrase and generates a privatekey, then converts it into its respective Bitcoin address. It then queries the calculated address for a balance and <a href="#expected-outputs">prints the result</a> to the user.

This program does this in a brute-force style, repeatedly generating and converting private keys, and querying balances. The ultimate goal is to randomly find a wallet with a balance out of the 2<sup>160</sup> possible wallets in existence. In the event that a wallet with a balance is found, the wallet's private key, public key, wallet address, and balance is stored in a text file `rubygen.txt` for later use.

Although this project can be used maliciously, it is simply an exploration into the Bitcoin protocol and advanced encryption and hashing techniques using Python.

#

# How it Works

Private keys are generated from bip39 phrases to create 64 byte hexidecimal string using the cryptographically secure `sha512()` function.

The private keys are converted into their respective public keys. Then the public keys are converted into their Bitcoin wallet addresses using the `binascii`, `ecdsa`, and `hashlib` Python modules.

The wallet addresses are queried using <a href="https://bitcoinlegacy.blockexplorer.com/api-ref">Block Explorer API</a> to collect balance details.

If the wallet contains a balance, then the private key, public key, wallet address, and balance are saved to a text file `rudygen.txt` on the user's hard drive.

#

# Expected Outputs

If the wallet is empty, then the format `Wallet Address = 0` will be printed. An example is:

 ['barricades']    1JZJ6dJb5N7fZ4pxPUZKjC6Uf7rKxH4aTK   5HstYJ4xTyGrjvViPMRJPSGTrExfrD1ebGLD75kdLDAKAVqw3QF = 0

However, if a balance is found, then the output will include all necessary information about the wallet. A copy of the output will also be saved in a text file titled `rudygen.txt` with all balances in Satoshi. An example is:

>address: 1JGM6sREUwt5paFEfHNuzvRy7nXtQdaamn<br>
>private key: 6694e2d40e786839d48b1b699ab9c318514dc0a0f27f2ccaf7f9f32224ead3a8<br>
>WIF private key: 5JbTtbihnAnNbBtqZKmkWbrDUeei1bCamqKPrHJ49vQx1CT8oUQ<br>
>public key: 04475C43E9E58637630E10DB01F2FF38C64430E07E272E4C82C877653B8AF15720E4F98F66B49BB4E91B36D4C08FC4F2E13F0A5079DFCEB1821FA05A9F9F30F361<br>
>balance: 10000000

#

# Warnings

If you are receiving: 

>HTTP Error Code: (number)<br/>
>Retrying in 5 seconds

Or

>Unable to connect to API after several attempts<br>
>Retrying in 30 seconds

This program queries Block Explorer API for wallet balances making a HTTP request necessary for complete operation. If connection to the API is found to be unresponsive (failing to return a 200 HTTP status) the program will pause for 5 seconds and attempt to continue.

If you are receiving a lot of errors, visit <a href="https://bitcoinlegacy.blockexplorer.com/">Blockexplorer.com</a> to see if their API might be down.

This program also responds to 429 HTTP responses because of the high frequency of server requests. When a 429 is encountered, the program will print the error `HTTP Error Code: 429`, but will not pause. However, if several 429's are received consecutively, the user will get the result `Unable to connect to API after several attempts` and will be forced to wait 30 seconds until the program continues again.

#

# Efficiency

This program is able to handle, generate, and query a private key in 0.5 seconds. However, because this program uses the internet for balance requests, a slower internet connection may impact time efficiency.

#

```
Donate to the author of this program: 1GmQaG9R5NPs3ZzR6XPMD9jZk17F9MuoWn
```

#
