![ZENZOLogo](https://i.imgur.com/fI2tHA8.png)
# ZENZO Masternode Setup Guide (Windows + Ubuntu 16.04)

###### In this guide, you will learn how to set up a ZENZO(ZNZ) Masternode on a Linux server(Ubuntu 16.04) with hosting from VULTR. 
***
## Requirements
1) **ZENZO/ZNZ Windows Local [Wallet](https://github.com/Zenzo-Ecosystem/ZENZO-Core/releases)**
2) **15,000 ZNZ Coins**
3) **A [VULTR](https://www.vultr.com/?ref=7517156) VPS running Linux with Ubuntu 16.04 OS installed**
4) **An SSH Client ([Bitvise](https://www.bitvise.com/ssh-client-download)**)
***
## Contents
* **Section A**: Creating the VPS on [VULTR](https://www.vultr.com/?ref=7517156)
* **Section B**: Downloading and installing [Bitvise](https://www.bitvise.com/ssh-client-download)
* **Section C**: Connecting to the VPS and file installation
* **Section D**: Preparing the ZENZO/ZNZ Local Wallet
* **Section E**: Connecting & Starting the ZENZO/ZNZ Masternode
***

## Section A: Creating the VPS within [VULTR](https://www.vultr.com/?ref=7517156) 

***Step 1***
* Register at [VULTR](https://www.vultr.com/?ref=7517156).
***

***Step 2***
* After you have added funds to your account go [here](https://my.vultr.com/deploy/) to create your Server.
***

***Step 3*** 
* Choose a server location.
![Example-Location](https://i.imgur.com/lnKG2tq.png)
***

***Step 4***
* Choose a server type: Ubuntu 16.04.
![Example-OS](https://i.imgur.com/aSMqHUK.png)
***

***Step 5***
* Choose a server size: $3.50 per month package (IPv4).
![Example-OS](https://i.imgur.com/04cCtec.png)
***

***Step 6*** 
* Set a Server Hostname & Label (name it whatever you want).
![Example-hostname](https://i.imgur.com/i48i8vO.png)
***

***Step 7***
* Click "Deploy now".

![Example-Deploy](https://i.imgur.com/4qpYuH0.png)
***

## Section B: Downloading and installing [Bitvise](https://www.bitvise.com/ssh-client-download) 

***Step 1***
* Download Bitvise [here](https://www.bitvise.com/ssh-client-download).
***

***Step 2***
* Select the first download option "Download Bitvise SSH Client (Tunnelier)".
![Example-Download](https://i.imgur.com/hxKu49j.png)
***

## Section C: Connecting to the VPS via Bitvise and Installing ZENZO Files

***Step 1***
* Copy your VPS IP (Servers Tab -> Your Server Name -> Overview).
![Example-VULTR](https://i.imgur.com/ntzPUPH.png)
***

***Step 2***
* Open the [Bitvise](https://www.bitvise.com/ssh-client-download) application (.exe file) and click yes to all changes it asks).
***

***Step 3***
* Click the "I agree to accept all of the terms of this License Agreement" and then click "Install".

![Example-BitviseInstall](https://i.imgur.com/mQW0DsJ.png)
***

***Step 4*** 
* Once you have opened the application, fill in your IP Address in the Host field and "root" in the Username field.
* Then click Login.

![Example-Bitvise Login](https://i.imgur.com/5sfWAuU.png)
***

***Step 5*** 
* A box will pop up and ask you to "Accept and Save" or "Accept for This Session", click either one.
***

***Step 6*** 
* Go to your new VPS in VULTR and copy your password (same screen as Step 1: Section C).
![Example-CopyPassword](https://i.imgur.com/eOH3bm5.png)
***

***Step 7*** 
* Paste your password in the next box that pops up, then click OK.

![Example-PastePassword](https://i.imgur.com/uC02ngU.png)
***

***Step 8*** 
* Now you are logged in to your server. Bitvise will have 2 windows open (Terminal + GUI Terminal).
***

***Step 9*** 
* Download the ZENZO/ZNZ Linux [Wallet](https://github.com/Zenzo-Ecosystem/ZENZO-Core/releases) from GitHub.

![Example-LinuxDownload](https://i.imgur.com/7Xhvqzz.png)
***

***Step 10*** 
* Extract this file (on your Desktop to make things easier and faster).
* You will now see 4 files, but will only need the first 3.
  * zenzo-cli
  * zenzo-tx
  * zenzod
  * ~~zenzo-qt~~
***

***Step 11*** 
* In your Bitvise Terminal, create two new directories. Type in the following 2 commands(separately, one at a time).
  * `mkdir zenzo`
  * `mkdir .zenzo`

![Example-CreateZenzoDir](https://i.imgur.com/3bMVKbI.png)
***

***Step 12*** 
* Proceed to your Bitvise GUI Client and click the "Refresh" icon to see the new directories you made. 

![Example-Refresh](https://i.imgur.com/U1Z45HX.jpg)
***

***Step 13*** 
* Select all three files: `zenzo-cli`, `zenzo-tx`, and `zenzod` in the Bitvise GUI Client (left panel).
* Drag and drop these 3 files into the `zenzo` folder (you can also click the "Upload" arrow).
* Wait for files to fully upload (this could take 10 seconds to a few minutes, depending on your computer and internet connection).

![Example-MoveFiles](https://i.imgur.com/W8xRnoH.jpg)
***

***Step 14*** 
* Create a text document (in Notepad or any text editor program).
* Add the following text and then save the file as `zenzo.conf`.
```
rpcuser=(create-your-username)
rpcpassword=(create-your-password)
rpcallowip=127.0.0.1
listen=1
server=1
daemon=1
txindex=1
staking=1
enablezeromint=0
addnode=80.211.138.180:26210
addnode=45.76.42.236:26210
addnode=45.76.184.133:26210
addnode=95.179.200.83:26210
addnode=45.76.117.67:26210
addnode=80.240.31.194:26210
addnode=144.202.101.208:26210
addnode=23.227.163.202:26210
addnode=195.206.181.235:26210
addnode=217.69.15.189:26210
addnode=149.28.224.239:26210
addnode=103.102.46.249:26210
addnode=45.77.224.165:26210
addnode=159.69.177.150:26210
addnode=207.148.93.79:26210
addnode=150.66.40.253:26210
addnode=108.61.166.192:26210
addnode=45.77.4.175:26210
addnode=207.180.253.25:26210
addnode=109.230.215.134:26210
addnode=207.148.64.152:26210
```

* Confirm your text document looks like the image below.

![Example-ZenzoConfFile](https://i.imgur.com/wHa6zGK.png)

* Upon saving the text document, it will save as `zenzo.conf.txt.` Delete the `.txt`.
* Windows will ask are you sure you want to make this change. Click "Yes".

 ![Example-ConfirmChange](https://i.imgur.com/qchTjqL.png)
***

***Step 15*** 
* Select the newly created `zenzo.conf` file you just made in the Bitvise GUI Client (left panel).
* Drag and drop the `zenzo.conf` file into the `.zenzo` folder (you can also click the "Upload" arrow).

![Example-MoveFile](https://i.imgur.com/FRVDIvi.jpg)
***

***Step 16*** 
* Click back on your Bitvise Terminal to enter the command `chmod +x zenzo/zenzo*`.

![Example-ChModCommand](https://i.imgur.com/kG7TL1D.png)
***

***Step 17*** 
* Now start your daemon/server by entering the command `zenzo/zenzod -daemon`.
* Your terminal should look exactly the same as below and read "Zenzo server starting".

![Example-StartServer](https://i.imgur.com/923C76M.png)
***

## Section D: Preparing the ZENZO/ZNZ Local Wallet

***Step 1***
* Open up your ZENZO/ZNZ Local Wallet by clicking zenzo-qt.
***

***Step 2***
* Encrypt your wallet by creating a unique password, if you have not already.
* Backup your `wallet.dat` file and store it somewhere safe (preferably off of your computer and on a new USB flash drive).
* Your wallet will reboot after you successfully create a new password and encrypt it.

![Example-EncryptWallet](https://i.imgur.com/IfBu7dQ.png)
***

***Step 3***
* After your wallet reboots, click **Tools -> Open Wallet Configuration File**.

![Example-EditConfFile](https://i.imgur.com/FlKnEm9.png)
* Confirm your .conf file contains the information below (the same information as you VPS `zenzo.conf` file).

```
rpcuser=(create-your-username)
rpcpassword=(create-your-password)
rpcallowip=127.0.0.1
listen=1
server=1
daemon=1
txindex=1
staking=1
enablezeromint=0
addnode=80.211.138.180:26210
addnode=45.76.42.236:26210
addnode=45.76.184.133:26210
addnode=95.179.200.83:26210
addnode=45.76.117.67:26210
addnode=80.240.31.194:26210
addnode=144.202.101.208:26210
addnode=23.227.163.202:26210
addnode=195.206.181.235:26210
addnode=217.69.15.189:26210
addnode=149.28.224.239:26210
addnode=103.102.46.249:26210
addnode=45.77.224.165:26210
addnode=159.69.177.150:26210
addnode=207.148.93.79:26210
addnode=150.66.40.253:26210
addnode=108.61.166.192:26210
addnode=45.77.4.175:26210
addnode=207.180.253.25:26210
addnode=109.230.215.134:26210
addnode=207.148.64.152:26210
```
***

***Step 4***
* Create a new address under **File -> Receiving Addresses...**.

![Example-NewAddress](https://i.imgur.com/oIrROwd.png)

* Click the New button on the bottom left and then right click "edit" to name your new address MN01 (or whatever you like).

![Example-EditLabel](https://i.imgur.com/gz16IvY.png)
***

***Step 5***
* Send 15,000 ZNZ(Masternode Collateral) to the newly created and labeled address ("MN01" for this example).

![Example-Send15k](https://i.imgur.com/KYhLspv.png)
***

***Step 6***
* Get your masternode genkey.
  * Open your Debug Console ( **Tools -> Debug Console** ).
  * Type command `masternode genkey` and press enter.
  * Copy this key and paste in a text editor program, like Notepad, for easy access for the following steps.
  * Do not share this masternode genkey online or with anyone (it functions as a private key).

![Example-MNGenKey](https://i.imgur.com/XJPm1Uj.png)
***

***Step 7***
* Paste your masternode genkey in the `zenzo.conf` file that is inside your VPS (Bitvise GUI Client).
  * Open your `zenzo.conf` file in your VPS (Bitvise GUI Client - Remote Files).
  * Copy and paste the following:
```
masternode=1
masternodeprivkey=yourgenkeyhere
```
  * Paste your genkey after `masternodeprivkey=` and then save the file and close it.
  
![Example-PasteMNGenKey](https://i.imgur.com/scjDeGq.png)
***

***Step 8***
* Get your masternode outputs.
  * Open your Debug Console ( **Tools -> Debug Console** ).
  * Type command `masternode outputs` and press enter.
  * Copy the "txhash" and "outputidx" and paste in a text editor program, like Notepad, for easy access for the following steps.
  * Do not share this masternode outputs online or with anyone (it functions as a private key).

![Example-MasternodeOutputs](https://i.imgur.com/CgXBuxT.jpg)
***

## Section E: Connecting & Starting the ZENZO/ZNZ Masternode

***Step 1***
* Edit the `masternode.conf` file in your ZENZO/ZNZ Local Wallet.
  * **Tools -> Open Masternode Configuration File**
  * Paste the following information on one line with one space between each input/field:
```
Alias VPSIPAddress:26210 MasternodeGenKey MasternodeTxHash MasternodeOutputID
```
* A correct example (follow this format):
```
MN01 45.77.15.154:26210 8DBMdmareMGqcc61HN5Jsr33w3U1AX7ezAsnmJHoMXhwam85uHE 27f1d2c8b05f4a61857e5ac201a537a86d21703a2d30bd4a456055bf9f861462 0
```

![Example-MNConfFile](https://i.imgur.com/QBkSBSY.png)  

* Save the file and restart your ZENZO/ZNZ Local Wallet.
***

***Step 2***
* Click your Masternodes Tab (left menu) in your ZENZO/ZNZ Local Wallet.
  * Confirm that your Masternode now appears and the Status says `MISSING`.

![Example-MNTab](https://i.imgur.com/5meW4JB.jpg)
***

***Step 3***
* Activate and start up your masternode.
  * Open your Debug Console ( **Tools -> Debug Console** ).
  * Type command `startmasternode all 0` and press enter.

![Example-StartMN](https://i.imgur.com/HB7leEI.jpg)

* Your ZENZO/ZNZ Local Wallet should now look like this, with the status "ENABLED":

![Example-MNSuccess](https://i.imgur.com/lUBjhYu.jpg)
***

***Step 4***
* Check the status of your masternode inside your VPS by entering the following command in your Bitvise Terminal:

`zenzo/zenzo-cli masternode status`

* If it is setup and activated correctly, you will see 'status: 4'.

![Example-Status4](https://i.imgur.com/1TnwujQ.jpg)

***

## Congratulations! You have successfully setup your ZENZO/ZNZ Masternode!





# Contact & Support
***

* For any help of questions, please join the [**Official ZENZO Discord**](https://discord.gg/BbQwvjq).
  * Join #wallet-help or #masternode-help channels regarding any issues with the wallet or masternode(s).



*Special thanks to @Visco33 for their Carebit Masternode Guide Template.*
