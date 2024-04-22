# Roburna Chain Configuration

### Hardware Requirements

Minimum:

- CPU with 2+ cores
- 4GB RAM
- 1TB free storage space to sync the Mainnet
- 10 MBit/sec download Internet service

Recommended:

- Fast CPU with 8+ cores
- 32GB+ RAM
- High-performance SSD with at least 1TB of free space
- 50+ MBit/sec download Internet service

### Download Geth

- clone and install geth from https://github.com/Roburna-Blockchain-Network/roburna-go

```bash
apt-get update -y
wget https://go.dev/dl/go1.21.0.linux-amd64.tar.gz
tar -xvf go1.21.0.linux-amd64.tar.gz
mv go /usr/local
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
source ~/.profile
apt-get install software-properties-common build-essential -y
git clone https://github.com/Roburna-Blockchain-Network/roburna-go
cd roburna-go
make all
alias geth='/root/roburna-go/build/bin/geth'

```

### Download Config/Genesis

```bash
# Mainnet
$ curl -L $(curl -s https://api.github.com/repos/Roburna-Blockchain-Network/node-config/releases/latest |grep browser_ |grep mainnet |cut -d\" -f4) -o mainnet.tar.gz
$ tar -xf mainnet.tar.gz

# Testnet
$ curl -L $(curl -s https://api.github.com/repos/Roburna-Blockchain-Network/node-config/releases/latest |grep browser_ |grep testnet |cut -d\" -f4) -o testnet.tar.gz
$ tar -xf testnet.tar.gz
```

### Running a Fullnode

```bash
# Initial Genesis Block
$ ./geth --datadir ./data init ./genesis.json

# Run
$ ./geth --datadir ./data --config ./config.toml --syncmode full
```

### Running a Archivenode

```bash
# Initial Genesis Block
$ ./geth --datadir ./data init ./genesis.json

# Run
$ ./geth --datadir ./data --config ./config.toml  --syncmode full --gcmode archive
```
