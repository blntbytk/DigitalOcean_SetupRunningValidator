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







