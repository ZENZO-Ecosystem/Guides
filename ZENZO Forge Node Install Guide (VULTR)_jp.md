![ZENZOForgeLogo](https://imgur.com/IeqNCeF.png)
# ZENZO Forgeフルノードインストールガイド（Ubuntu 18.04）

###### このガイドでは、VULTRからのホスティングを使用してLinuxサーバー（Ubuntu 18.04）にZENZO Forgeノードをセットアップする方法を学びます。
###### ZENZO Forgeの詳細については[こちら](https://zenzo-ecosystem.medium.com/a-new-nft-standard-emerges-zfi-1-e09e701b4729)をご覧ください。

***
## 必要になるもの
1) **[ZENZO (ZNZ) Linuxウォレット](https://github.com/Zenzo-Ecosystem/ZENZO-Core/releases)**
2) **月額10USD** (VPSホスティング料金)
3) **[VULTR VPS](https://www.vultr.com/?ref=7517156)** (Ubuntu 18.04 OSがインストールされたLinuxマシンでの実行)
4) **SSHクライアント ([Bitvise](https://www.bitvise.com/ssh-client-download)**)
***
## 本ガイドの内容
* **Section A**: [VULTR](https://www.vultr.com/?ref=7517156)でVPSを作成する
* **Section B**: [Bitvise](https://www.bitvise.com/ssh-client-download)のダウンロードとインストール
* **Section C**: Bitviseを使ったVPSへの接続と[ZENZO Core](https://github.com/ZENZO-Ecosystem/ZENZO-Core/releases/download/v2.1.0/zenzo-2.1.0-x86_64-linux-gnu.tar.gz) Walletのインストール
* **Section D**: [ZENZO Forge](https://github.com/ZENZO-Ecosystem/zenzo-forge.git)のダウンロードとインストール
***

## Section A: [VULTR](https://www.vultr.com/?ref=7517156)でVPSを作成する

***ステップ 1***
* [VULTR](https://www.vultr.com/?ref=7517156)に登録してアカウントを作成します。
***

***ステップ 2***
* アカウントに代金を追加します。その後、[こちら](https://my.vultr.com/deploy/)へ移動してサーバーを作成します。
***

***ステップ 3*** 
* サーバータイプ（Cloud Compute）を選択します。
 
![Example-Type](https://imgur.com/R4F3OPC.png)
***

***ステップ　4*** 
* サーバーのロケーションを選択します。
 
![Example-Location](https://imgur.com/MUEkQej.png)
***

***ステップ 5***
* サーバータイプを選択します：Ubuntu 18.04（または最新の安定バージョンを選択します）
 
![Example-OS](https://imgur.com/gw5uqAp.png)
***

***Step 6***
* サーバーサイズを選択します：ここでは例として55GB SSD、月額$10のパッケージを選択します。
  * 1 CPU
  * 2048MB メモリ
  * 2000GB 帯域幅
 
![Example-OS](https://imgur.com/9kX0n3H.png)
***

***ステップ 7*** 
* サーバーのホストネームとラベルを設定します。（任意の名前をつけます）
 
![Example-hostname](https://imgur.com/fWcz4Pp.png)
***

***ステップ 8***
* [Deploy Now]をクリックします。

![Example-Deploy](https://i.imgur.com/4qpYuH0.png)
***

## Section B: [Bitvise](https://www.bitvise.com/ssh-client-download)のダウンロードとインストール

***ステップ 1***
* [こちら](https://dl.bitvise.com/BvSshClient-Inst.exe)からBitviseをダウンロードしてください。
***
***ステップ 2***
* [Bitvise](https://dl.bitvise.com/BvSshClient-Inst.exe)アプリケーション（.exeファイル）を開き、必要なすべての変更に対して[Yes]をクリックします）。
***

***ステップ 3***
* [I agree to accept all of the terms of this License Agreement]（この使用許諾契約のすべての条項に同意します）にチェックを入れ、[Install]をクリックしてインストールを開始します。

![Example-BitviseInstall](https://imgur.com/fRfKFM9.png)
***

## Section C: Bitviseを使ったVPSへの接続とZENZO Core Walletのインストール

***ステップ 1***
* Bitviseクライアントを起動します。

![Example-VULTR](https://imgur.com/SKcfkZe.png)
***

***ステップ 2***
* VULTRに新しくデプロイしたVPSに移動します。（左側のダッシュボードから：[Products]-> [サーバー名]-> [Overview]）

![Example-VULTR](https://imgur.com/edPttTG.png)
***

***ステップ 3*** 

    
    
* [IPアドレス]をコピーして、Bitviseの[ホスト]フィールドに貼り付けます。
* [ユーザー名]をコピーして、Bitviseの[ユーザー名]フィールドに貼り付けます。
* [Password]をコピーして、Bitviseの[Password]フィールドに貼り付けます（最初に[Store encrypted password in profile]（暗号化されたパスワードをプロファイルに保存する）をクリックします。

![Example-VULTR_VPS_Details](https://imgur.com/r3IsZ58.png)
***

***ステップ 4*** 
* 正確に情報を入力し、[Login]をクリックします。

![Example-Bitvise Login](https://imgur.com/oIWBjkl.png)
***

***ステップ 5*** 
* [Accept and Save]（承諾して保存する）、または[Accept for This Session]（このセッションを承諾する）というメッセージがポップアップで表示されるので、いずれかをクリックします。
***

***ステップ 6*** 
* これでサーバーにログインしました。[New terminal console]アイコンをクリックします。

![Example-New_Terminal](https://imgur.com/iDrb69z.png)
***

***ステップ 7*** 
* ターミナルを開き、ZENZO Coreのインストールを開始します。手順や使用するコマンドは次ステップ以降で解説します。

![Example-New_Terminal](https://imgur.com/WFa91yD.png)
***

***ステップ 8*** 
* ZENZO Core Walletをインストールして実行します。以下のコマンドを実行していきます。
* 実行する前に、コマンドのインストールが完了していることをまず確認してください。
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

***ここからStep 9*** 
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
