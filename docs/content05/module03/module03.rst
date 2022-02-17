SSLサーバ証明書の設定
======================================

BIG-IPが持つデフォルトのサーバ証明書は正式な認証局で取得したものではないため、クライアントPCのWebブラウザでVirtual Serverへアクセスすると以下のような警告が出ます。

.. figure:: images/mod5-3.png
   :scale: 50%
   :align: center

以降で、正式な認証局 (例: Verisign, CyberTrust等)で署名されたサーバ証明書をインポートして利用するまでの手順を示します。

F5 UDF Labで利用するサーバ証明書
--------------------------------------

一般的には、以下の手順でサーバ証明書の発行を行います。

| 1. BIG-IPのGUIでCSRと秘密鍵を生成し、CSRを認証局 (例: Verisign等)に送付する。
| 2. CSRに対して認証局が署名を行うことで、サーバ証明書が完成する。
| 3. サーバ証明書を返送してもらい、BIG-IPへインポートする。

本ガイドでは簡易的に、秘密鍵ファイルとサーバ証明書の両方がすでに存在しているものとしてインポートします。リモートデスクトップ接続したクライアントPC (Windows 10 Client)のデスクトップ上にある、以下のフォルダを開いてください。

.. figure:: images/mod5-3-1-1.png
   :scale: 100%
   :align: center

このフォルダ内の以下2つのファイルを使用します。


1. 秘密鍵ファイル: **abcCompany-key.pem**
2. サーバ証明書ファイル: **abcCompany-cert.pem**


秘密鍵とサーバ証明書のインポート
--------------------------------------

- まず、サーバの秘密鍵をインポートします。

- 「System」 → 「Certificate Management」 → 「Traffic Certificate Management」 → 「SSL Certificate List」で表示された画面右上の「Import」ボタンを押します。

.. figure:: images/mod5-3-2-1.png
   :scale: 50%
   :align: center

- Keyを選択します。

.. figure:: images/mod5-3-2-2.png
   :scale: 70%
   :align: center

- 以下のように設定します。

.. figure:: images/mod5-3-2-3.png
   :scale: 20%
   :align: center

- 以下の状態になります。

.. figure:: images/mod5-3-2-4.png
   :scale: 50%
   :align: center

- 次に、サーバ証明書をインポートします。インポートした秘密鍵をクリックすると、以下の画面が現れます。「Import」ボタンを押します。

.. figure:: images/mod5-3-2-5.png
   :scale: 20%
   :align: center

- 以下のように設定して、インポートします。

.. figure:: images/mod5-3-2-6.png
   :scale: 20%
   :align: center

- サーバ証明書がインポートされた状態です。

.. figure:: images/mod5-3-2-7.png
   :scale: 20%
   :align: center

Client SSL Profileの生成とVSへの割当て
--------------------------------------

- Client SSL Profileを作ります。「Local Traffic」 → 「Profiles」 → 「SSL」 → 「Client」で表示された画面右上の「Create」ボタンを押すと、以下の画面が表示されますので、以下のように設定します。

.. figure:: images/mod5-3-3-1.png
   :scale: 20%
   :align: center

- 「Add」ボタンを押すと以下のような設定画面が表示されるので、「abcCompany」を設定します。

.. figure:: images/mod5-3-3-2.png
   :scale: 60%
   :align: center

- 以下のように表示されます。

.. figure:: images/mod5-3-3-3.png
   :scale: 20%
   :align: center

(省略)

.. figure:: images/mod5-3-3-4.png
   :scale: 20%
   :align: center

- 作成した設定が登録されていることを確認します。

.. figure:: images/mod5-3-3-5.png
   :scale: 20%
   :align: center

- Virtual ServerへのClient SSL Profileを割り当てます。「Local Traffic」 → 「Virtual Servers」 を選択し、SSL-VPN接続用に設定したVirtual Server (本ガイドの例では"NetAccess-001_vs")をクリックすると、以下の画面が表示されます。

.. figure:: images/mod5-3-3-6.png
   :scale: 70%
   :align: center

(省略)

.. figure:: images/mod5-3-3-7.png
   :scale: 20%
   :align: center

(省略)

.. figure:: images/mod5-3-3-8.png
   :scale: 20%
   :align: center
