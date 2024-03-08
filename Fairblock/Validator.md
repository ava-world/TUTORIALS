## PREREQUISITES

1. Upgrade your system

```
sudo apt update && sudo apt upgrade -y
```

2. install dependencies

   

```
sudo apt install git curl tar wget libssl-dev jq build-essential gcc make

```

3. download and install go v1.21


```
sudo apt remove --autoremove golang-go; sudo apt install snapd; sudo snap install --classic --channel=1.21/stable go

```
```
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.profile
source $HOME/.profile
```

## INSTALLATION

4. clone repository & install

```
cd $HOME
rm -rf fairyring
git clone https://github.com/Fairblock/fairyring.git
cd fairyring

```

```
git checkout v0.4.0

```

```
make install

```

5. verify installation (should be 0.4.0)

```
fairyringd version

```

## RUN TESTNET

6. initialize the node (change "NODE_NAME" to your name)

```
fairyringd init NODE_NAME

```

7. copy genesis file just to be sure

```
cd
```

```

cp ~/fairyring/networks/testnets/fairytest-1/genesis.json ~/.fairyring/config/genesis.json

```

```
cd fairyring

```

8. set peers

```

SEEDS=$(cat $HOME/fairyring/networks/testnets/fairytest-1/peers-nodes.txt)
echo $SEEDS
sed -i.bak -e "s/^persistent_peers *=.*/persistent_peers = \"$SEEDS\"/" $HOME/.fairyring/config/config.toml

```

9. start node

```

fairyringd start

```





