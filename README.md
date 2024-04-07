# Guide to run koii node on vps:
These are the commands that were used in : 
https://youtu.be/h9LkcSo29IA

for more detailed information please check:
https://docs.koii.network/run-a-node/task-nodes/Running-on-VPS



**-Update the apt**
```
sudo apt update
sudo apt upgrade
```
**-Install git**
```
sudo apt install git
```
**-Clone the project**
```
git clone https://github.com/koii-network/VPS-task
```
**-let's go to the cloned project directory**
```
cd VPS-task
```
**-Download koii cli**
```
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init.sh)"
```
**-check if it works**
```
koii --version
```
**-configure the testnet url**
```
koii config set --url https://testnet.koii.live
```
**-check if it works**
```
koii balance
```
**-create new wallet**
```
koii-keygen new -o /root/.config/koii/id.json
```
**-install docker**
```
sudo apt install docker
```
**-check if docker-compose was installed proberly**
```
docker-compose --version
```
**-run the docker ((you have to be in the VPS-Task directory))**
```
docker-compose up
```

**if you are facing an error when using docker-compose up**
**-check where docker-compose is installed**
```
which docker-compose 
```
**-update the docker-compose library**
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
**-give the system ther permission**
```
sudo chmod +x /usr/local/bin/docker-compose
```

**-If it docker-compose up is running properly then press ctrl + c then write**
```
docker-compose up -d
```

**-this will run docker in the background**

**-to check if docker is running proberly use**
```
docker logs -f --tail 10 task_node
```


**To Claim rewards**
**-install npm library**
```
sudo apt install npm
```

**-Run this command**
```
cd
npx @_koii/create-task-cli@latest
```

**-then choose claim rewards for this example i will use the free token Task**

**Task id:** GbumTdsj7hcPZKGbExTFLxQ4Cj8FeQFvH7NZWCahYows

**stakePotAccount:** stakepotaccount8BKM1uyj4QRi6TvbwhJA6JGMnBsL

**address that the funds will be transfered to:** your_wallet_address

**path to claimer wallet:** VPS-task/namespace/staking_wallet.json


##
--------------------------------------------------------------------------
##
**To update your VPS node to testnet 2**

If you have staked koii in the task first unstake all of your koii using :

```
npx @_koii/create-task-cli@latest
```

After you emptied the stake wallet, remove the VPS-task directory:

```
rm -r VPS-task/
```

Download the new VPS-task:

```
git clone https://github.com/koii-network/VPS-task
```

Now you need to change the address for the koii cli:

```
koii config set --url https://testnet.koii.network/
```

Now update your .env-local file:

```
cd VPS-task
nano .env-local
```

Change ENVIRONMENT from development to production 

```
ENVIRONMENT="production"
```

Set initial staking wallet balance to whatever you want (keep in mind this should bigger than all staked koii in all of the tasks combined):

```
INITIAL_STAKING_WALLET_BALANCE=4
```

Change K2_NODE_URL to the new testnet URL:

```
K2_NODE_URL="https://testnet.koii.network"
```

Change taskID to the new task id, for example the free token task:

```
TASKS="GbumTdsj7hcPZKGbExTFLxQ4Cj8FeQFvH7NZWCahYows"
```

Now run the task:

```
docker-compose up -d
```


