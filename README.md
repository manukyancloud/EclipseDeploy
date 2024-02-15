# Eclipse




## Contrat Deployment:

```console
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"

# sol cli
sh -c "$(curl -sSfL https://release.solana.com/stable/install)"
PATH="/root/.local/share/solana/install/active_release/bin:$PATH"
solana config set --url https://staging-rpc.dev.eclipsenetwork.xyz

# create key
solana-keygen new

# faucet
solana airdrop 10

# 8gb ram needed.
solana-test-validator
# komut çalışınca ctrl c ile durdurabilirsiniz.

# if 
# nodejs kurulumu - komutları tek tek kullanalım
sudo apt-get install -y ca-certificates curl gnupg
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg

NODE_MAJOR=20
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list
sudo apt-get update
sudo apt-get install nodejs -y

# deploy contract
git clone https://github.com/solana-labs/example-helloworld
cd example-helloworld
npm install

# wait a min
npm run build:program-rust

# Program id
solana program deploy dist/program/helloworld.so
npm run start
# success çıktısı verecek en sonda.

```

## Bridge

```console
sudo apt update -y && sudo apt upgrade -y
sudo apt install git

git clone https://github.com/Eclipse-Laboratories-Inc/testnet-deposit.git
cd testnet-deposit

yarn install
yarn add ethers

# 
node deposit.js <solanaAdresi> 0x7C9e161ebe55000a3220F972058Fb83273653a6e 500000 100 <MetamaskPrivateKeyi> https://rpc.sepolia.org
# 
```

> success output

> https://explorer.dev.eclipsenetwork.xyz/?cluster=testnet 

> Fill the form: https://docs.google.com/forms/d/e/1FAIpQLSfJQCFBKHpiy2HVw9lTjCj7k0BqNKnP6G1cd0YdKhaPLWD-AA/viewform
