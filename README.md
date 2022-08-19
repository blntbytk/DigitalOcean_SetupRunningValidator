# DigitalOcean_SetupRunningValidator
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""Stake Wars: Episode III. Challenge 005:Setup a running validator node for shardnet on any one of the most popular cloud providers and document the process to create an article about it.

	Amazon Web Services
	Google Cloud Platform
	Microsoft Azure
	IBM Cloud
	DigitalOcean
	Hetzner
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

As an information here is the list some of the specs and the prices. I recommended specs for shardnet  8CPU/16GB/500GB SSD.

![ch5_4](https://user-images.githubusercontent.com/105415280/185484855-52d1ff67-0d46-4403-ab43-b8c9447423ed.PNG)




For going  on with the DigitalOcean right click the banner below and open it in a new tab , you will be directed to the DigitalOcean web page.


<a href="https://www.digitalocean.com/?refcode=8faac9ad0613&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge"><img src="https://web-platforms.sfo2.cdn.digitaloceanspaces.com/WWW/Badge%201.svg" alt="DigitalOcean Referral Badge" /></a>


From list chose your signup option

![ch5_8](https://user-images.githubusercontent.com/105415280/185483416-de39c6a8-20ff-4870-8738-9c9765585f9e.PNG)


Form the list chose your payment method. I wanted credit card option and chose add card
![ch5_9](https://user-images.githubusercontent.com/105415280/185483615-bd88b6b2-a51d-4c75-8ca7-244676521c3d.PNG)

Fill theform with reel informations otherwise you can be banned

![ch5_10](https://user-images.githubusercontent.com/105415280/185483701-f8157902-efe8-4417-bd14-c510abc8d08e.PNG)

After the related confirmations now you are ready for chosing the VPS and create it.


![ch5_1](https://user-images.githubusercontent.com/105415280/185480374-b5671265-eb7b-4652-bd62-7dcb17a65341.PNG)








![ch5_5](https://user-images.githubusercontent.com/105415280/185486182-af140824-5931-4fd0-8c87-36a0e7f79bae.PNG)



![ch5_6](https://user-images.githubusercontent.com/105415280/185484909-3c4abf47-b804-43b1-bda3-982b1585d91c.PNG)


![ch5_7](https://user-images.githubusercontent.com/105415280/185484930-302ccabf-4414-4e3f-81cc-09e4765c0e4b.PNG)




After the droplet was created now you are ready for installing node .But also you need another server with min specs for the NEAR-CLI ,is a command-line interface that communicates with the NEAR blockchain via remote procedure calls (RPC). It is important that this server also   will have to work 7/24 becuase of ping works that we will see below pages.

Firstly we will create wallet from https://wallet.shardnet.near.org/  please dont forget to copy the keys.

Connect your NEAR-CLI server with SSH through web or a third party like putty ,use root previlligies.

![ch5_11](https://user-images.githubusercontent.com/105415280/185486997-f0c00dce-f3be-4968-bf33-a90345cb7949.PNG)



Update our server

```
sudo apt update && sudo apt upgrade -y
```

![01_1](https://user-images.githubusercontent.com/105415280/185493231-b0e769e1-366b-4dba-893c-6390e276f4a6.PNG)


installing `Node.js` and `npm`:
```
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -  
sudo apt install build-essential nodejs
PATH="$PATH"
```

![01_2](https://user-images.githubusercontent.com/105415280/185493272-51e98734-e7fb-4499-bc01-0e75b4e5870a.PNG)


![01_3](https://user-images.githubusercontent.com/105415280/185493292-6160b146-41f3-4677-a54f-f282345e65a0.PNG)


![01_4](https://user-images.githubusercontent.com/105415280/185493313-717ecf51-6253-4842-854a-9790a2933993.PNG)


![01_5](https://user-images.githubusercontent.com/105415280/185493369-539d9963-0145-4448-ae27-6807f18d6ffa.PNG)


![01_6](https://user-images.githubusercontent.com/105415280/185493391-b1438e97-ac06-48d7-9c68-d2ea42640912.PNG)



Check the versions of Node.js and npm :
```
node -v
```
> v18.x.x

```
npm -v
```
> 8.x.x

![01_7](https://user-images.githubusercontent.com/105415280/185493482-57f8933a-eb59-4dae-a9e8-f04229ddb5c5.PNG)



Install NEAR-CLI

sudo npm install -g near-cli

![01_11](https://user-images.githubusercontent.com/105415280/185494008-76ee8631-642e-4bbe-8451-f342da494e07.PNG)


![01_12](https://user-images.githubusercontent.com/105415280/185494025-ddef2c97-fe60-4a97-9bb2-bccb0205a945.PNG)


```
echo 'export NEAR_ENV=shardnet' >> ~/.bashrc
echo 'export NEAR_ENV=shardnet' >> ~/.bash_profile
source $HOME/.bash_profile
```

![01_13](https://user-images.githubusercontent.com/105415280/185494736-4527caaf-6aef-45b6-972a-488e0aee1162.PNG)



```
near proposals
```


![01_14](https://user-images.githubusercontent.com/105415280/185494758-b4bb2434-f8a5-4dc4-b0d1-f49ed152536f.PNG)


```
near validators current
```


![01_15](https://user-images.githubusercontent.com/105415280/185494968-7f8aa1b3-4b0f-4b44-80af-a70e2c64323d.PNG)



```
near validators next
```

![01_16](https://user-images.githubusercontent.com/105415280/185495309-a5b3b3b5-702c-4a6b-8f70-1da3eed532cb.PNG)


Now we are ready to install our node. Connect your NODE server with SSH through web or a third party like putty ,use root previlligies.


Check if your server supporting or not within below command

```
lscpu | grep -P '(?=.*avx )(?=.*sse4.2 )(?=.*cx16 )(?=.*popcnt )' > /dev/null \
  && echo "Supported" \
  || echo "Not supported"
```

![image](https://user-images.githubusercontent.com/105415280/185586456-54e19fbd-a5cf-45de-8fa1-0fd9f03ab179.png)

Install developer tools below
```
apt install -y git binutils-dev libcurl4-openssl-dev zlib1g-dev libdw-dev libiberty-dev cmake gcc g++ python3 docker.io protobuf-compiler libssl-dev pkg-config clang llvm cargo
```

![image](https://user-images.githubusercontent.com/105415280/185586737-afcbb9a7-eafd-49b8-974b-eebcda975340.png)



Install python
```
apt install python3-pip
```

For configuration set :

```
USER_BASE_BIN=$(python3 -m site --user-base)/bin
export PATH="$USER_BASE_BIN:$PATH"
```
![image](https://user-images.githubusercontent.com/105415280/185587811-d8f92e55-07a3-4e43-b6e0-eb73b759f3f5.png)


Building env install
```
apt install clang build-essential make
```

![image](https://user-images.githubusercontent.com/105415280/185587986-ac850cdf-ff7f-4e22-bb96-9ce7d277c45b.png)


Install Rust and Cargo
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Chose yes
![image](https://user-images.githubusercontent.com/105415280/185588160-4c1c24ca-a704-4135-b233-66af4aeab584.png)

Chose 1 and enter

![image](https://user-images.githubusercontent.com/105415280/185588276-93e9acbc-265d-4d89-a93b-3a436d713e77.png)


than use below command and install Rust
```
source $HOME/.cargo/env
```


Clone nearcore from github

```
git clone https://github.com/near/nearcore
cd nearcore
git fetch origin --tags
git checkout tags/shardnet
```
![image](https://user-images.githubusercontent.com/105415280/185590203-c857495a-106e-41bb-b127-99cf2ddc057d.png)

while at nearcore folder use below command for bianry, it will take some time , please wait finishing.

```
cargo build -p neard --release --features shardnet
```

![image](https://user-images.githubusercontent.com/105415280/185590653-dd6a91da-0521-40b3-ba2c-d79cd52ce2ff.png)

Download genesis, 

```
./target/release/neard --home ~/.near init --chain-id shardnet --download-genesis
```

![image](https://user-images.githubusercontent.com/105415280/185593352-764d1e37-1f00-410c-8c99-90f8f4dc1bd6.png)

At the end of command you wll find config.json`, `node_key.json`, and `genesis.json` under .near directory. These are important files at the end of all configuration backup them.

![image](https://user-images.githubusercontent.com/105415280/185593510-2a463b31-6ffd-4219-83cf-4fc0f0c77ed1.png)



Replace config.json by below command

```
rm ~/.near/config.json
wget -O ~/.near/config.json https://s3-us-west-1.amazonaws.com/build.nearprotocol.com/nearcore-deploy/shardnet/config.json
```

![image](https://user-images.githubusercontent.com/105415280/185593720-4804696c-ebdc-44f0-a5f6-37acecf35012.png)



thats all we installed the node ,now start it with below command and wait synching and downloading headers to 100%

```
cd ~/nearcore
./target/release/neard --home ~/.near run
```

![image](https://user-images.githubusercontent.com/105415280/185594128-6abd448b-a577-4494-add4-5c83f7e55ca8.png)



Now go to your NEAR-CLI server .Run below commnad

```
near login
```

![image](https://user-images.githubusercontent.com/105415280/185598496-f433b78d-75f2-4916-9f01-433711bb1667.png)

You will see a link , copy it to your browser and give full permisson from your wallet. Come back to your console and enter the same your wallet adress. Now we give the NEAR-CLI server to authenticate our wallet.




#####  Check the validator_key.json
* Run the following command:
```
cat ~/.near/validator_key.json
```


> Note: If a validator_key.json is not present, follow these steps to create one

Create a `validator_key.json` 

*   Generate the Key file:

```
near generate-key <pool_id>
```
<pool_id> ---> xx.factory.shardnet.near WHERE xx is you pool name

> Pool will be created at the next task, now you can give the same name as your wallet name  
For example :  
wallet name : john.shardnet.near (in future we will call it <accountId>)
pool name : john.factory.shardnet.near  
Please use the same pool name for next task "Mount your Staking Pool"

* Copy the file generated to shardnet folder:
Make sure to replace <pool_id> by your pool name
```
cp ~/.near-credentials/shardnet/YOUR_WALLET.json ~/.near/validator_key.json
```
* Edit “account_id” => xx.factory.shardnet.near, where xx is your PoolName
* Change `private_key` to `secret_key`

> Note: The account_id must match the staking pool contract name or you will not be able to sign blocks.\

File content must be in the following pattern:
```
{
  "account_id": "xx.factory.shardnet.near",
  "public_key": "ed25519:HeaBJ3xLgvZacQWmEctTeUqyfSU4SDEnEwckWxd92W2G",
  "secret_key": "ed25519:****"
}
```

#####  Start the validator node

```
target/release/neard run
```
* Setup Systemd
Command:

```
sudo vi /etc/systemd/system/neard.service
```
Paste:

```
[Unit]
Description=NEARd Daemon Service

[Service]
Type=simple
User=<USER>
#Group=near
WorkingDirectory=/home/<USER>/.near
ExecStart=/home/<USER>/nearcore/target/release/neard run
Restart=on-failure
RestartSec=30
KillSignal=SIGINT
TimeoutStopSec=45
KillMode=mixed

[Install]
WantedBy=multi-user.target
```

> Note: Change USER to your paths

Command:

```
sudo systemctl enable neard
```
Command:

```
sudo systemctl start neard
```
If you need to make a change to service because of an error in the file. It has to be reloaded:

```
sudo systemctl reload neard
```
###### Watch logs
Command:

```
journalctl -n 100 -f -u neard
```
Make log output in pretty print

Command:

```
sudo apt install ccze
```
View Logs with color

Command:

```
journalctl -n 100 -f -u neard | ccze -A
```
#### Becoming a Validator
In order to become a validator and enter the validator set, a minimum set of success criteria must be met.

* The node must be fully synced
* The `validator_key.json` must be in place
* The contract must be initialized with the public_key in `validator_key.json`
* The account_id must be set to the staking pool contract id
* There must be enough delegations to meet the minimum seat price. See the seat price [here](https://explorer.shardnet.near.org/nodes/validators).
* A proposal must be submitted by pinging the contract
* Once a proposal is accepted a validator must wait 2-3 epoch to enter the validator set
* Once in the validator set the validator must produce great than 90% of assigned blocks

Check running status of validator node. If “Validator” is showing up, your pool is selected in the current validators list.


## Let's go to challenge 3 🚀

[Mount your Staking Pool](./003.md).

## Update log

Updated 2022-07-13: Creation

Updated 2022-07-13: Creation

Updated 2022-07-18: Snapshot is not required after hardfork

Updated 2022-07-20: Clarified the rewards for solving the challenge



