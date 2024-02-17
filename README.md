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
cd root
npx @_koii/create-task-cli@latest
```

**-then choose claim rewards for this example i will use the free token Task**

**Task id:** 6GbpHRK3duDbo3dCEFXuJ2KD5Hg6Yo4A9LyHozeE7rjN

**stakePotAccount:** FnQm11NXJxPSjza3fuhuQ6Cu4fKNqdaPkVSRyLSWf14d

**address that the funds will be transfered to:** your_wallet_address

**path to claimer wallet:** VPS-task/namespace/staking_wallet.json



