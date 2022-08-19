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


You will see the following:

![img](./images/rust.png)

Press 1 and press enter.

##### Source the environment
```
source $HOME/.cargo/env
```

#### Clone `nearcore` project from GitHub
First, clone the [`nearcore` repository](https://github.com/near/nearcore).

```
git clone https://github.com/near/nearcore
cd nearcore
git fetch
```

Checkout to the commit needed. Please refer to the commit defined in [this file](https://github.com/near/stakewars-iii/blob/main/commit.md). 
```
git checkout <commit>
```

#### Compile `nearcore` binary
In the `nearcore` folder run the following commands:

```
cargo build -p neard --release --features shardnet
```
The binary path is `target/release/neard`. If you are seeing issues, it is possible that cargo command is not found. Compiling `nearcore` binary may take a little while.

#### Initialize working directory

In order to work properly, the NEAR node requires a working directory and a couple of configuration files. Generate the initial required working directory by running:

```
./target/release/neard --home ~/.near init --chain-id shardnet --download-genesis
```

![img](./images/initialize.png)

This command will create the directory structure and will generate `config.json`, `node_key.json`, and `genesis.json` on the network you have passed. 

- `config.json` - Configuration parameters which are responsive for how the node will work. The config.json contains needed information for a node to run on the network, how to communicate with peers, and how to reach consensus. Although some options are configurable. In general validators have opted to use the default config.json provided.

- `genesis.json` - A file with all the data the network started with at genesis. This contains initial accounts, contracts, access keys, and other records which represents the initial state of the blockchain. The genesis.json file is a snapshot of the network state at a point in time. In contacts accounts, balances, active validators, and other information about the network. 

- `node_key.json` -  A file which contains a public and private key for the node. Also includes an optional `account_id` parameter which is required to run a validator node (not covered in this doc).

- `data/` -  A folder in which a NEAR node will write it's state.

#### Replace the `config.json`

From the generated `config.json`, there two parameters to modify:
- `boot_nodes`: If you had not specify the boot nodes to use during init in Step 3, the generated `config.json` shows an empty array, so we will need to replace it with a full one specifying the boot nodes.
- `tracked_shards`: In the generated `config.json`, this field is an empty. You will have to replace it to `"tracked_shards": [0]`

```
rm ~/.near/config.json
wget -O ~/.near/config.json https://s3-us-west-1.amazonaws.com/build.nearprotocol.com/nearcore-deploy/shardnet/config.json
```

#### Run the node
To start your node simply run the following command:

```
cd ~/nearcore
./target/release/neard --home ~/.near run
```

![img](./images/download.png)
The node is now running you can see log outputs in your console. Your node should be find peers, download headers to 100%, and then download blocks.

----




