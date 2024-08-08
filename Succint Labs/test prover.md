# RUN YOUR FIRST SP1 PROOF
This test was done using Ubuntu 22.04 system

### Install Prerequisites
- Install Git

  
```
sudo apt install git-all && git --version
```


- Install Rust

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

-select 1, and press Enter 


- Reconfigure path
  

  ``
. "$HOME/.cargo/env"
  ``

- Install docker


```
apt install docker.io

```


might experience error if docker is already installed

- verify docker is installed

```
docker --version
```

### Install Toolchain

```
curl -L https://sp1.succinct.xyz | bash
```

- Reconfigure path

```
source /root/.bashrc
```

- Install

```
sp1up
```

this will install the toolchain and create a configured test environment for you
you will see "done"



### Generating Proof


- Create new project

```
cargo prove new fibonacci && cd fibonacci
```


- Execute Proof

```
cd script
```


```
RUST_LOG=info cargo run --release -- --execute
```


This should take some minutes, but you should see a message like "program executed successfully"



- Generate a proof (automatically saves to your disk)

```
RUST_LOG=info cargo run --release -- --prove
```


you will see 2 messages "successfully generated proof" and "successfully verified proof"




- Congratulations, you can flex on twitter and share the link on discord 😁 




