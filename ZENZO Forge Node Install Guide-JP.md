![ZENZOForgeLogo](https://imgur.com/IeqNCeF.png)
# ZENZO Forgeフルノードインストールガイド (Ubuntu 18.04)

###### このガイドでは、VPSとBitviseを使用してLinuxサーバー（Ubuntu 18.04）にZENZO Forgeノードをセットアップする方法を学びます。****
###### ZENZO Forgeの詳細については[こちら](https://zenzo-ecosystem.medium.com/a-new-nft-standard-emerges-zfi-1-e09e701b4729)をご覧ください。

***
## 必要になるもの
1) **VPS** + **SSHクライアント**
2) **[ZENZO (ZNZ) Linuxウォレット](https://github.com/Zenzo-Ecosystem/ZENZO-Core/releases)**
3) **[ZENZO Forge](https://github.com/ZENZO-Ecosystem/zenzo-forge)**
***

## 本ガイドの内容
* **Section A**: Bitvise経由でVPSに接続し、[ZENZO Core](https://github.com/ZENZO-Ecosystem/ZENZO-Core/releases/download/v2.1.0/zenzo-2.1.0-x86_64-linux-gnu.tar.gz) Walletをインストールする
* **Section B**: [ZENZO Forge](https://github.com/ZENZO-Ecosystem/zenzo-forge.git)のダウンロードとインストール
***


## Section A: Bitvise経由でVPSに接続し、ZENZO Core Walletをインストールする

***ステップ 1***
* Bitviseクライアントを起動する。

![Example-VULTR](https://imgur.com/SKcfkZe.png)
***

***ステップ 2***
* VPSに移動して、サーバーの情報を取得します。

![Example-VULTR](https://imgur.com/edPttTG.png)
***

***ステップ 3*** 
* [IP Address]をコピーし、Bitviseの[Host]フィールドに貼り付けます。
* [Username]をコピーし、Bitviseの[Username]フィールドに貼り付けます。
* [Password]をコピーし、Bitviseの[Password]フィールドに貼り付けます（最初に[Store encrypted password in profile]（暗号化されたパスワードをプロファイルに保存する）にチェックを入れます。

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
* 
![Example-New_Terminal](https://imgur.com/WFa91yD.png)
***

***ステップ 8*** 
* ZENZO Core Walletをインストールして実行します。以下のコマンドを順次実行していきます。
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

***ステップ 9*** 
* 次のコマンドを実行し、インストールと同期の進行状況を確認します:
  * `./zenzo-cli getinfo`
***

***ステップ 10*** 
* [blocks]をチェックし、 [ZENZO Explorer](https://chainz.cryptoid.info/znz/)とブロックの進行状況が一致することを確認します。
* 完全に同期され、公式のブロックエクスプローラーと一致したら、次のセクションでZENZO Forgeのインストールに進みます。

![Example-LinuxDownload](https://imgur.com/MHSgoDk.png)
***

***ステップ 11*** 
* 次のコマンドを実行して、ZNZアドレスを生成します:
  * `./zenzo-cli getnewaddress`

![Example-ZNZ-Address](https://imgur.com/1NZo1VP.png)
***

***ステップ 12*** 
* 次のコマンドを実行して、クライアントを停止し、ウォレットをシャットダウンします:
  * `./zenzo-cli stop`
***

***ステップ 13*** 
* 次のコマンドを実行し、`zenzo.conf`ファイルを開きます:
  * `nano /root/.zenzo/zenzo.conf`
***

***ステップ 14*** 
* `zenzo.conf`ファイルに新しいパラメーターを追加します。各パラメーターの内容は下記テキストの通りです:
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

***ステップ 15*** 
* `CTRL + O`を押してから`Enter`キーを押し、内容を追加した`zenzo.conf`を上書き保存します。
* 保存した後、`CTRL + X`を押して終了します。
* `./zenzod -daemon`と入力して、ZENZO Coreウォレットのバックアップを開始します。
***

## Section B: [ZENZO Forge](https://github.com/ZENZO-Ecosystem/zenzo-forge.git)のダウンロードとインストール

***ステップ 1***
* 次のコマンドを実行して、Node.jsをインストールします。（ZENZO Forgeを動かすために必要となります）
* 実行する前に、次のコマンドのインストールが完了していることを確認してください。
  * `sudo apt-get install -y curl`
  * `curl -fsSL https://deb.nodesource.com/setup_15.x | sudo -E bash -`
  * `sudo apt-get install -y nodejs`
  * `sudo apt-get install -y libgtk-3-0`
  * `sudo apt install -y git`
  * `npm i pm2 -g`
***

***ステップ 2***
* 次のコマンドを入力し、ZENZO Forgeをインストールして実行します。
* 実行する前に、次のコマンドのインストールが完了していることを確認してください。
  * `git clone https://github.com/ZENZO-Ecosystem/zenzo-forge.git forge`
  * `cd forge`
  * `npm i`
  * `cd lib`
  * `pm2 start index.js`
  * `pm2 stop 0`
***

***ステップ 3***
* `config.json`ファイルを作成し、`ZNZ Address`を追加します（セクションA、ステップ11で生成したZNZアドレス）
  * `nano /var/local/forge/data/config.json`

* 上記の内容をコピーし、編集内容（ユーザー、パス、ZNZアドレス）とともに貼り付けます。
* （ZENZO Coreの`rpcusername`と`rpcpassword`に一致するように、`user`と`pass`を編集してください）
```
{"fullnode":true,"wallet":{"datadir":"/root/.zenzo/","user":"user","pass":"forgepass","port":26211,"address":"ZrKZd3zuUk1StAUqPteBS1vVtEH7FjaPa9"},"forgeport":9002,"maxinvalidscore":25,"debug":"me,validations,net"}
```
* `CTRL + O`を押してから`Enter`キーを押し、更新した内容を保存します。
* `CTRL + X`を押して終了します。

![Example-JSON-File](https://imgur.com/C5hmG6m.png)
***

***ステップ 4*** 
* 次のコマンドを入力し、ZENZO Forgeクライアントを実行します:
  * `pm2 start 0`

![Example-Run-Forge](https://imgur.com/3iGKx9e.png)
***

### :confetti_ball:おめでとうございます！これでZENZO Forgeノードがアクティブになりました！


![ZENZOForgeGraphic](https://imgur.com/CUQqe6X.png)

# お問い合わせ & サポート
***

* 内容についての質問、ヘルプが必要な場合は、[**公式 ZENZO Discord**](https://discord.com/invite/kwBD3pk)に参加してください。
  * ZENZO Forgeについて質問がある場合は、Discord内チャンネル[#forge-help](https://discord.gg/A9vd4VXUxx)でお聞きください。