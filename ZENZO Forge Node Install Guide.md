![ZENZOForgeLogo](https://imgur.com/IeqNCeF.png)
# ZENZO Forge Full Node Install Guide (Ubuntu 18.04)

###### In this guide, you will learn how to set up a ZENZO Forge Node on a Linux server (Ubuntu 18.04) with hosting from VULTR. 
###### Learn more about the [ZENZO Forge](https://zenzo-ecosystem.medium.com/a-new-nft-standard-emerges-zfi-1-e09e701b4729).

***
## Requirements
1) **[ZENZO (ZNZ) Linux Wallet](https://github.com/Zenzo-Ecosystem/ZENZO-Core/releases)**
2) **$10 USD per month** (VPS Hosting Fee)
3) **[VULTR VPS](https://www.vultr.com/?ref=7517156)** (Running Linux with Ubuntu 18.04 OS installed)
4) **SSH Client ([Bitvise](https://www.bitvise.com/ssh-client-download)**)
***
## Contents
* **Section A**: Creating the VPS on [VULTR](https://www.vultr.com/?ref=7517156)
* **Section B**: Downloading & Installing [Bitvise](https://www.bitvise.com/ssh-client-download)
* **Section C**: Connecting to the VPS via Bitvise and Installing [ZENZO Core](https://github.com/ZENZO-Ecosystem/ZENZO-Core/releases/download/v2.1.0/zenzo-2.1.0-x86_64-linux-gnu.tar.gz)
* **Section D**: Downloading & Installing [ZENZO Forge](https://github.com/ZENZO-Ecosystem/zenzo-forge.git)
***

## Section A: Creating the VPS within [VULTR](https://www.vultr.com/?ref=7517156) 

***Step 1***
* Register at [VULTR](https://www.vultr.com/?ref=7517156).
***

***Step 2***
* After you have added funds to your account go [here](https://my.vultr.com/deploy/) to create your Server.
***

***Step 3*** 
* Choose a server type (Cloud Compute).
 
![Example-Type](https://imgur.com/R4F3OPC.png)
***

***Step 4*** 
* Choose a server location.
 
![Example-Location](https://imgur.com/MUEkQej.png)
***

***Step 5***
* Choose a server type: Ubuntu 18.04 (or the latest stable build).
 
![Example-OS](https://imgur.com/gw5uqAp.png)
***

***Step 6***
* Choose a server size: $10 per month package (55 GB SSD).
  * 1 CPU
  * 2048MB Memory
  * 2000GB Bandwidth
 
![Example-OS](https://imgur.com/9kX0n3H.png)
***

***Step 7*** 
* Set a Server Hostname & Label (name it whatever you want).
 
![Example-hostname](https://imgur.com/fWcz4Pp.png)
***

***Step 8***
* Click "Deploy now".

![Example-Deploy](https://i.imgur.com/4qpYuH0.png)
***

## Section B: Downloading and Installing [Bitvise](https://www.bitvise.com/ssh-client-download) 

***Step 1***
* Download Bitvise [here](https://dl.bitvise.com/BvSshClient-Inst.exe).
***
***Step 2***
* Open the [Bitvise](https://dl.bitvise.com/BvSshClient-Inst.exe) application (.exe file) and click yes to all changes it requires).
***

***Step 3***
* Click the "I agree to accept all of the terms of this License Agreement" and then click "Install".

![Example-BitviseInstall](https://imgur.com/fRfKFM9.png)
***

## Section C: Connecting to the VPS via Bitvise and Installing ZENZO Core

***Step 1***
* Open up the Bitvise Client.

![Example-VULTR](https://imgur.com/SKcfkZe.png)
***

***Step 2***
* Navigate to your newly deployed VPS on VULTR (Left Dashboard: Products -> Your Server Name -> Overview).

![Example-VULTR](https://imgur.com/edPttTG.png)
***

***Step 3*** 
* Copy the "IP Address" and paste it into the "Host" field in Bitvise.
* Copy the "Username" and paste it into the "Username" field in Bitvise.
* Copy the "Password" and paste it into the "Password" field in Bitvise (click "Store encrypted password in profile" first)

![Example-VULTR_VPS_Details](https://imgur.com/r3IsZ58.png)
***

***Step 4*** 
* Once you have filled in the correct information, then click Login.

![Example-Bitvise Login](https://imgur.com/oIWBjkl.png)
***

***Step 5*** 
* A box will pop up and ask you to "Accept and Save" or "Accept for This Session", click either one.
***

***Step 6*** 
* Now you are logged in to your server. Click the "New terminal console" icon.

![Example-New_Terminal](https://imgur.com/iDrb69z.png)
***

***Step 7*** 
* With your terminal open, you can begin installing ZENZO Core with the following commands in the next step.

![Example-New_Terminal](https://imgur.com/WFa91yD.png)
***

***Step 8*** 
* Install ZENZO Core and run the client. Run the following commands, one after another. 
* Make sure the commands have finished installing before running the next command.
  * `sudo apt-get update -y && sudo apt-get upgrade -y`
  * `wget https://github.com/ZENZO-Ecosystem/ZENZO-Core/releases/download/v2.1.0/zenzo-2.1.0-x86_64-linux-gnu.tar.gz`
  * `tar -xvf zenzo-2.1.0-x86_64-linux-gnu.tar.gz`
  * `cd zenzo-2.1.0/bin/`
  * `mv zenzo-cli  zenzod  zenzo-qt  zenzo-tx /root`
  * `cd`
  * `rm -r zenzo-2.1.0 zenzo-2.1.0-x86_64-linux-gnu.tar.gz`
  * `chmod +x zenzo*`
  * `./zenzod -daemon`
***

***Step 9*** 
* Check the progress of your installion and synchronization by typing this command:
  * `./zenzo-cli getinfo`
***

***Step 10*** 
* Check the "blocks" to make sure that it matches with the [ZENZO Explorer](https://chainz.cryptoid.info/znz/). 
* Once it is fully synchronized and matches the official block explorer, you may proceed to install the ZENZO Forge in the next section.

![Example-LinuxDownload](https://imgur.com/MHSgoDk.png)
***

***Step 11*** 
* Generate a ZNZ Address by typing in the following command:
  * `./zenzo-cli getnewaddress`

![Example-ZNZ-Address](https://imgur.com/1NZo1VP.png)
***

***Step 12*** 
* Stop the client and shutdown the wallet by typing in this command:
  * `./zenzo-cli stop`
***

***Step 13*** 
* Open the `zenzo.conf` file by typing in the following command:
  * `nano /root/.zenzo/zenzo.conf`
***

***Step 14*** 
* Add new parameters to the `zenzo.conf` file to match the following text:
```
rpcuser=user
rpcpassword=forgepass
rpcport=26211
rpcallowip=127.0.0.1
usehd=0
daemon=1
txindex=1
maxconnections=250
listen=1
```

![Example-ZENZO-Conf](https://imgur.com/41QTLuW.png)
***

***Step 15*** 
* Save the update `zenzo.conf` additions by typing `CTRL + O` and then `Enter`.
* After saving, exit by typing `CTRL + X`.
* Start back up your ZENZO Core Wallet by typing `./zenzod -daemon`.
***

## Section D: Downloading and Installing the [ZENZO Forge](https://github.com/ZENZO-Ecosystem/zenzo-forge.git)

***Step 1***
* Run the following commands to install Node.js (required for the ZENZO Forge).
* Make sure the commands have finished installing before running the next command.
  * `sudo apt-get install -y curl`
  * `curl -fsSL https://deb.nodesource.com/setup_15.x | sudo -E bash -`
  * `sudo apt-get install -y nodejs`
  * `sudo apt-get install -y libgtk-3-0`
  * `sudo apt install -y git`
  * `npm i pm2 -g`
***

***Step 2***
* Install and run the ZENZO Forge by typing the following commands.
* Make sure the commands have finished installing before running the next command.
  * `git clone https://github.com/ZENZO-Ecosystem/zenzo-forge.git forge`
  * `cd forge`
  * `npm i`
  * `cd lib`
  * `pm2 start index.js`
  * `pm2 stop 0`
***

***Step 3***
* Create `config.json` file and add your `ZNZ Address` (Section C, Step 11).
  * `nano /var/local/forge/data/config.json`

* Copy and paste this information, with your edits (user, pass, ZNZ Address).
* (Remember to change your `user` and `pass` to match your `rpcusername` and `rpcpassword` in ZENZO Core)
```
{"fullnode":true,"wallet":{"datadir":"/root/.zenzo/","user":"user","pass":"forgepass","port":26211,"address":"ZrKZd3zuUk1StAUqPteBS1vVtEH7FjaPa9"},"forgeport":9002,"maxinvalidscore":25,"debug":"me,validations,net"}
```
* Save the updates by typing `CTRL + O` and then `Enter`. 
* Exit by tying `CTRL + X`.

![Example-JSON-File](https://imgur.com/C5hmG6m.png)
***

***Step 4*** 
* Run your ZENZO Forge client by typing the following command:
  * `pm2 start 0`

![Example-Run-Forge](https://imgur.com/3iGKx9e.png)
***

### :confetti_ball:Congratulations, your ZENZO Forge Node is now active!


![ZENZOForgeGraphic](https://imgur.com/CUQqe6X.png)

# Contact & Support
***

* For any help or questions, please join the [**Official ZENZO Discord**](https://discord.com/invite/kwBD3pk).
  * Join [#forge-help](https://discord.gg/A9vd4VXUxx) if you have any questions regarding the ZENZO Forge.
