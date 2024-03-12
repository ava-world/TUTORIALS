
## sending your first IBC PACKET on polymer testnet

1. install git

```
add-apt-repository ppa:git-core/ppa
apt update; apt install git

```

2. clone template to your local machine

```
git clone https://github.com/ava-world/first-xcounter
```

3. install node.js

```
sudo apt install curl
curl -s https://deb.nodesource.com/setup_18.x | sudo bash
sudo apt install nodejs -y
node -v
```
install NVM

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"

```

```
nvm
```

```
nvm install 20
```

```
nvm use 20
```

4.install foundry

```
curl -L https://foundry.paradigm.xyz | bash
```

```
source /root/.bashrc
```

```
foundryup
```

5. install just

```
wget -qO - 'https://proget.makedeb.org/debian-feeds/prebuilt-mpr.pub' | gpg --dearmor | sudo tee /usr/share/keyrings/prebuilt-mpr-archive-keyring.gpg 1> /dev/null
echo "deb [arch=all,$(dpkg --print-architecture) signed-by=/usr/share/keyrings/prebuilt-mpr-archive-keyring.gpg] https://proget.makedeb.org prebuilt-mpr $(lsb_release -cs)" | sudo tee /etc/apt/sources.list.d/prebuilt-mpr.list
sudo apt update
```

```
sudo apt install just
```

```
cd first-xcounter

just install
```

6. set up environment

```
cp .env.example .env
```



<l1>
EDIT .env file by imputing the right informations, an editor like vscode makes it easier to edit, its optional to use an editor though.
  <l1/>

### IMPORTANT!!!!!
You are only making changes to line 2, 6, 7, 8,9. DO NOT COPY MINE JUST USE THE LINKS I PROVIDED TO GET YOUR KEYS AND EDIT THEM IN THE .env file

```
nano .env
```


<l1>
  
a.   
PRIVATE_KEY_1='YOUR_METAMASK_PRIVATE_KEY'
 Add more if your project requires more private keys

 API keys for developer tooling and infra
OP_ALCHEMY_API_KEY='YOUR_ALCHEMY_OP_SEPOLIA_API_KEY' link: https://docs.alchemy.com/docs/alchemy-quickstart-guide
BASE_ALCHEMY_API_KEY='YOUR_ALCHEMY_BASE_SEPOLIA_API_KEY' link: https://docs.alchemy.com/docs/alchemy-quickstart-guide
OP_BLOCKSCOUT_API_KEY='YOUR_OP_BLOCKSCOUT_API_KEY' link: https://optimism-sepolia.blockscout.com/account/api-key
BASE_BLOCKSCOUT_API_KEY='YOUR_ALCHEMY_BASE_SEPOLIA_API_KEY'  link: https://base-sepolia.blockscout.com/account/api-key
TENDERLY_TOKEN=''

<l1/>


after you can save using ctrl + x, then type "y", then enter.


7. claim faucets with same wallet


   https://www.alchemy.com/faucets/optimism-sepolia
https://www.alchemy.com/faucets/base-sepolia


9. send transaction 

```
just send-packet base

```

```
just set-contracts optimism XCounterUC true
```

```
just switch-client
```

```
just deploy optimism base

```

```
just sanity-check

```

```
just send-packet optimism

```

10. copy your transaction hash and check in sepolia.polymer.zone/packets.

ONLY SEND PROOF TO DISCORD AFTER YOUR TRANSACTION IS DELIVERED 


  
