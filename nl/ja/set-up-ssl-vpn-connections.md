---

copyright:
  years: 1994, 2017-2019
lastupdated: "2019-03-06"

keywords: Linux Fedora, SSL VPN connections Windows, backend IP address

subcollection: iaas-vpn

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}

# SSL VPN 接続のセットアップ
{:#setup-ssl-vpn-connections}

Windows、Linux Fedora、および Linux は、本書に示されている、個別化された接続手順を必要とします。 以下に、SSL VPN 接続の使用例をいくつか示します。

* Windows 2003 サーバーを管理するためのサーバーのバックエンド IP アドレス (10.4.X.X) へのリモート・デスクトップ。
* UNIX サーバーを管理するためのサーバーのバックエンド IP アドレス (10.4.X.X) への SSH。
* IPMI クライアントによる、バックエンド IPMI アドレス (10.4.X.X) を使用したサーバーの制御。 IPMI クライアント・ツールは、接続後に http://downloads.softlayer.local/ipmi/ からダウンロードできます (SoftLayer プライベート VPN に接続されている必要があります)。
  * **注:** IPMIView は Java のインストールを必要とします。  http://www.sun.com/java/
* パブリック IP での稼働前のバックエンド IP での Web サイトのテスト。
* サーバーと自宅/オフィス間でのセキュア・データのファイル転送。
* 自宅/オフィスへのサーバー上の構成ファイルのバックアップ。
* 弊社 [Web ポータル](http://control.softlayer.com/)へのセキュア接続。

## Windows (Internet Explorer)
{:#setup-ssl-vpn-connections-windows}

1. Internet Explorer を開き、`http://www.softlayer.com/vpn-access` にアクセスします。
* ユーザー名とパスワードを入力すると、ActiveX プラグインのインストールを求めるプロンプトが出されます。 バックエンド・ネットワークに接続するには、このプラグインをインストールする必要があります。 
* ActiveX プラグインをインストールするには、ワークステーションでの管理権限も必要です。 このプラグインをインストールする権限がない場合は、ローカル・システム管理者に代わりにインストールするよう依頼してください。 
* ActiveX プラグインがインストールされると、Array SSL VPN ネットワーク・コネクターが起動し、VPN デバイスへの接続を確立します。 正常に確立されると、タスクバーに赤い**「A」**が表示されます。 **「A」**をクリックすればいつでも、SSL VPN 接続の状況 (状況、割り当て済み IP アドレス、割り当て済み DNS サーバー、ネットワーク経路、接続時刻など) を確認できます。 
* いつでもブラウザー・セッションを最小化して、プライベート・ネットワーク上で他のアプリケーションをセキュアに使用できます。 
* 終了したら、右側にある切断ボタンを選択して切断するか、単にウィンドウを閉じます。

## Linux Fedora 
{:#setup-ssl-vpn-connections-linux}

Firefox では NPAPI プラグイン (java アプレット) がサポートされなくなりました。以下のステップを実行する場合は別のブラウザーを使用してください。
{:note}

コマンドはすべて root として実行することをお勧めします。 (`setuid root`)

1. Java を `http://java.com/en/download/manual.jsp` からダウンロードします。 これは Linux の自己解凍ファイルです。
* ブラウザーを閉じます。
* Java のインストール先 (通常は `/usr/local`) にファイルを移動します。
* コマンド `chmod +x jre-6u1-linux-i586.bin` を使用してファイルを実行可能にします。
* コマンド `./jre-6u1-linux-i586.bin` を使用してインストーラーを実行します。
* ご利用条件に同意し、インストールします。
* インストールが完了したら、シンボリック・リンクを作成する必要があります。

## Linux の例
{:#setup-ssl-vpn-connections-linux-example}

1. ブラウザーを開き、`http://www.softlayer.com/vpn-access` にアクセスします。
* カスタマー・ポータルのユーザー名とパスワードでログインします。
* 接続したら、**「ネットワーク」**タブを選択します。
* 「接続/インストール」ボタンが表示されます。 このボタンを選択すると、Java コンポーネントのインストールを確認するプロンプトが出されます。
* コンポーネントをデフォルト・パスにインストールします。このパスは手動での作成が必要になる場合があります。 (`/usr/local/array_vpn`)
* インストール後、接続を知らせるウィンドウが表示されます。
* VPN トンネルを利用するにはこのウィンドウを開いたままにしておく必要がありますが、最小化できます。
* 接続をテストするには、10.0.80.11 またはご使用のサーバーのプライベート・アドレスを ping します。 応答を受け取った場合は、正常に接続されています。
* 終了したら、「ネットワーク」タブの下にある切断ボタンを選択するか、単にブラウザー・ウィンドウをすべて閉じます。
