# lab-smart-derivative-contract

## Setup of Quorum by Quorum-Maker

This README describes the setup of a Quorum network out of docker images. It is possible to create a test/development network, but in addition to establish
a Quorum network on a physically distributed set of nodes and to manage them and, in addition, to observe them in browser Web UI. 
This README focuses on the case of a testnetwork on a single box.

## Getting Started


### Installation

- download VMbox and install

- download Vagrant and install  (add folder C:\HashiCorp\Vagrant\bin to windows PATH if not performed automatically)

- git clone https://github.com/synechron-finlabs/quorum-maker

- cd into ...git\quorum-maker

- vagrant init

- vagrant up

- vagrant ssh  --> This opens up a Linux (Ubuntu) shell.

Now proceed in there:

- Install docker: curl -sSL https://get.docker.com/ | sh

- Install docker-compose: sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

- sudo chmod a+x /usr/local/bin/docker-compose

- From home directory which you had entered originally, start quorum installation:    ./setup.sh

- You will see a menu of actions: Choose option 4 (Setup Development/Test network) and accept name "TestNetwork".

- Choose number of nodes, the test network should contain: perhaps 3 or 4.

- cd TestNetwork

- docker-compose up -d: This boots up everything.

- Take a first look at running nodes with docker ps. You should see them in a list together with their network configuration, in particular their nodes.

- You can now connect to the Quorum Maker UI for each node from a web browser by pointing to http://192.168.33.11:20104, or ...20204 or  ...20304 corresponding to your nodes.  




### Interaction with the network from outside


For command interaction with the network from either the host machine or from within the VM (Linux):

#### Windows:  

- Install go-ethereum (contains geth):  look at https://github.com/ethereum/go-ethereum and follow the installation instructions there to install a stable windows binary.

#### Linux/Ubuntu:  

First check if a c-compiler is installed.

Next install the go language package:

- sudo apt-get update
- sudo apt-get -y upgrade
- wget https://dl.google.com/go/go1.11.2.linux-amd64.tar.gz
- cd /usr/local
- sudo tar xvzf ~/go1.11.2.linux-amd64.tar.gz

Next install go-ethereum:

- git clone https://github.com/ethereum/go-ethereum

- cd go-ethereum

- make geth 

- sudo cp build/bin/geth /usr/local

- sudo chmod +x /usr/local/geth


#### Command execution from within geth console

From outside (e.g. Windows):

- Attach to node1:  geth attach http://192.168.33.11:20100 

From within the VM (Ubuntu) and there folder TestNetwork:

- Attach to node1: sudo geth attach ipc:node1/node/qdata/geth.ipc



### Documentation about Quorum-Maker

See https://github.com/synechron-finlabs/quorum-maker