クライアント証明書認証の設定
======================================

クライアント証明書による認証を行う設定方法を記載します。

クライアント証明書の発行
--------------------------------------

クライアント証明書認証の設定を行うためには、以下2つの証明書が必要です。

①	認証局の証明書
BIG-IP側で利用します。

②	クライアント証明書
クライアントPC側で利用します。

クライアント証明書の発行には、大きくは以下2つの方法があります。

a)	商用の認証局（Verisign、CyberTrust等）から発行してもらう
b)	独自の認証局（例：OpenSSLの利用）を建てて、発行する

本ガイドでは、b)の方法：OpenSSLを使って独自の認証局を建てて、クライアント証明書を発行したものを利用します。リモートデスクトップ接続したPCのデスクトップ上にある、以下のフォルダを開いてください。

.. figure:: images/mod6-1-1.png
   :scale: 100%
   :align: center

このフォルダ内の以下のファイルを使用します。

クライアント証明書ファイル: **abc-client001.p12**

クライアントPCへのクライアント証明書インポート
--------------------------------------

クライアント証明書 (PKCS#12)をクライアントPCへインストールする手順について、参考までに記載します。
本ガイドのクライアントPCはWindows10＋Chromeを利用しています。

- Chromeの設定画面で、証明書の管理を選択します。

.. figure:: images/mod6-1-2-1.png
   :scale: 20%
   :align: center

- 個人タブを選択して「インポート」ボタンを押します。

.. figure:: images/mod6-1-2-2.png
   :scale: 20%
   :align: center

- 「次へ」ボタンを押します。

.. figure:: images/mod6-1-2-3.png
   :scale: 20%
   :align: center

- 「参照」ボタンを押し、クライアント証明書を選択して、「次へ」ボタンを押します。

.. figure:: images/mod6-1-2-4.png
   :scale: 20%
   :align: center

- 秘密キーがパスワードで保護されているので、パスワードを入力して、「次へ」ボタンを押します。 (OpenSSLで発行する際に指定したパスワードは「f5demo」です。)

.. figure:: images/mod6-1-2-5.png
   :scale: 20%
   :align: center

- 「次へ」ボタンを押します。

.. figure:: images/mod6-1-2-6.png
   :scale: 20%
   :align: center

- 「完了」ボタンを押します。

.. figure:: images/mod6-1-2-7.png
   :scale: 20%
   :align: center

- 以下のようにクライアント証明書が登録されます。クライアント証明書をダブルクリックすると、証明書の詳細が確認できます。

.. figure:: images/mod6-1-2-8.png
   :scale: 20%
   :align: center

User-Agentをログ上で確認
--------------------------------------

- 以下のコマンドを実行します。


上図1-6のIPアドレスが必要になりますので、あらかじめご用意ください。

.. code-block:: bash

   [root@bigXXX:Active:Standalone] config # tail –f /var/log/ltm


- クライアントPCで、iRuleを設定したVirutal Serverへ、ChromeおよびFirefoxから以下2つのブラウザからアクセスします。

- /var/log/ltmに、以下のようなログ (例)が出力されます。
**Chromeの場合**

.. code-block:: bash

   Jun 27 17:44:11 big50 info tmm1[9735]: Rule /Common/User-Agent_check <HTTP_REQUEST>: USER-AGENT is mozilla/5.0 (windows nt 10.0; win64; x64) applewebkit/537.36 (khtml, like gecko) chrome/75.0.3770.142 safari/537.36


**Firefoxの場合**

.. code-block:: bash
   
   Jun 27 17:43:53 big50 info tmm1[9735]: Rule /Common/User-Agent_check <HTTP_REQUEST>: USER-AGENT is mozilla/5.0 (windows nt 10.0; wow64; rv:65.0) gecko/20100101 firefox/68.0


