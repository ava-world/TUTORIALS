## To join POP mining with a linux server and secure the Hemi Network, follow the below intructions
check the <a href="https://docs.hemi.xyz/how-to-tutorials/pop-mining">official docs</a> for more customizations and more information about other server requirements

- Download file

```
wget https://github.com/hemilabs/heminetwork/releases/download/v0.3.7/heminetwork_v0.3.7_linux_amd64.tar.gz
```

- Extract file
 
```
tar -xvzf heminetwork_v0.3.7_linux_amd64.tar.gz
```

- Enter Folder
   
```
cd heminetwork_v0.3.7_linux_amd64
```

- Install xattry

```
apt install xattr -y
```

- Remove quarantine (recommended if ubuntu version is < 22.04)

```
xattr -d com.apple.quarantine ./popmd
```

- Confirm that file is executable

  ```
  ./popmd --help
  
  ```

- Generate Key

  ```
  ./keygen -secp256k1 -json -net="testnet" > ~/popm-address.json
  
  ```

- Open JSON file, save all details including private key and public hash

  ```
  cat ~/popm-address.json
  
  ```

- Create screen

  ```
  screen -S hemi
  ```

  ## Make sure to claim faucet in discord with your public hash which is your $tbtc address

- Replace "MYPRIVATEKEY" with the private key you saved earlier, Run Miner.

```
export POPM_BTC_PRIVKEY=MYPRIVATEKEY
export POPM_STATIC_FEE=50
export POPM_BFG_URL=wss://testnet.rpc.hemi.network/v1/ws/public
./popmd

```

## You can exit screen with ctrl + A + D, and can always resume back with ``screen -r hemi``


  

      
