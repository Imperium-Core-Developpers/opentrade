# OpenTrade opensource cryptocurrency exchange fork to go beyond....

Live version: https://trade.multicoins.org/

Install :

sudo apt-get update
sudo apt-get install build-essential libssl-dev curl -y
curl -sL https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh -o install_nvm.sh
bash install_nvm.sh
sudo reboot  ( or just close and re-open terminal ??.... )

nvm install 8.0.0

git clone https://github.com/Imperium-Core-Developpers/opentrade.git

sudo npm install 
```

## Here is an example of the file ~/opentrade/server/modules/private_constants.js Edit with your configs.
```
'use strict';

exports.recaptcha_priv_key = 'YOUR_GOOGLE_RECAPTCHA_PRIVATE_KEY';
exports.password_private_suffix = 'LONG_RANDOM_STRING1';
exports.SSL_KEY = '../ssl_certificates/privkey.pem'; //change to your ssl certificates private key
exports.SSL_CERT = '../ssl_certificates/fullchain.pem'; //change to your ssl certificates fullchain

exports.walletspassphrase = {
    'MC' : 'LONG_RANDOM_STRING2',
    'BTC' : 'LONG_RANDOM_STRING3',
    'DOGE' : 'LONG_RANDOM_STRING4'
};
```

**After editing the configuration files , you can run the exchange**

```
cd  ~/opentrade/server
sudo node main.js
```

In your browser address bar, type https://127.0.0.1:40443 ( or simply https://localhost if you put port 443 )
You will see the OpenTrade platform.

The first registered user will be the exchange administrator. 

# How to add new trade pairs

For each coin, you should create a *.conf file
Here is a common example for "some_coin.conf"

```
rpcuser=long_random_string_one
rpcpassword=long_random_string_two
rpcport=12345
rpcclienttimeout=10
rpcallowip=127.0.0.1
server=1
daemon=1
upnp=0
rpcworkqueue=1000
enableaccounts=1
litemode=1
staking=0
addnode=1.2.3.4
addnode=5.6.7.8

```

Also, you must encrypt your cryptocurrency wallet with this command.

```
./bitcoind encryptwallet random_long_string_SAME_AS_IN_FILE_private_constants.js

```

*If the coin is not supported by encryption (like ZerroCash and it forks) then the coin can not be added to OpenTrade.*


Add your coin details to OpenTrade

1. Register on the exchange. The first registered user will be the exchange administrator.
2. Go to "Admin Area" -> "Coins" -> "Add coin"
3. Fill up all required fields and click on "Confirm"
4. Fill "Minimal confirmations count" and "Minimal balance" and uncheck then re-check the "Coin visible" button
5. Click on "Save"
6. Check the RPC command for the coin. If it is working then the coin has been added to the exchange!

All visible coins should appear in the Wallet. You should now create default coin pairs.

The file ~/opentrade/server/constants.js have some settings you can change

https://github.com/3s3s/opentrade/blob/master/server/constants.js

```
exports.TRADE_MAIN_COIN = "Marycoin"; //change Marycoin to your main coin pair
exports.TRADE_DEFAULT_PAIR = "Litecoin"; //change Litecoin to your default coin pair
exports.TRADE_COMISSION = 0.001; //change trade comission percent

exports.recaptcha_pub_key = "6LeX5SQUAAAAAKTieM68Sz4MECO6kJXsSR7_sGP1"; //change to your recaptcha public key

exports.NOREPLY_EMAIL = 'no-reply@multicoins.org'; //change no-reply email
exports.SUPPORT_EMAIL = 'ivanivanovkzv@gmail.com'; //change to your valid email for support requests
exports.my_portSSL = 40443; //change to your ssl port

```

File ~/opentrade/static_pages/chart.html

https://github.com/3s3s/opentrade/blob/master/static_pages/chart.html#L23

```
const PORT_SSL = 40443; //change to your ssl port
const MAIN_COIN = 'Marycoin'; //change Marycoin to your main coin pair same as in constants.js
const DEFAULT_PAIR = 'Litecoin'; //change Litecoin to your default coin pair same as in constants.js
      
const TRADE_COMISSION = 0.001;
```

After those modifications, your coins should now appear on the main page.



**Donate**
buy us some coffee !!   :-)

3s3s :

Bitcoin 36WA1WESULub6Q434bQcnmpnk62oLD7vuQ
Marycoin M9dKNcBYgrbbE2f4tz3ud32KLKj1i9FrmN
Dogecoin DCJRhs9Pjr2FBrrUbKvFeWcYC6ZaF2GTAx
Litecoin LTbDdTijroJEyXt27apQSnuMY4RoXyjdq2

IMPERIUM-main-dev :
Bitcoin 3HPUbratYNpP2Q2wWh65LmwjSmy441KSDU



