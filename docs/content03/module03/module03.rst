管理ポートへのGUIアクセス
======================================


- 管理用PCから設定したBIG-IPの管理IPアドレスへ、HTTPSでアクセスします。デフォルトの証明書は正式に取得した証明書ではないため、以下のような画面が現れますが、「続行する」を選択してください。


.. figure:: images/mod3-3-1.png
   :scale: 50%
   :align: center


- ログイン画面が現れますので、以下のデフォルトのIDとPasswordでログインしてください。
| Username: **admin**
| Password: **admin**

.. figure:: images/mod3-3-2.png
   :scale: 50%
   :align: center

.. note::
   バージョン14.0より、デフォルトでBIG-IPのセキュアパスワードポリシーが有効となっています。パスワードポリシーを変更しない限り、v13.0以前のデフォルトパスワードは利用できません。

本ガイドでは以下のように設定し、「Save」ボタンを押します。

| Current Password: **admin**
| New Password: **ilovef5**
| Confirm: **ilovef5**

.. figure:: images/mod3-3-3.png
   :scale: 50%
   :align: center

- 設定したパスワードでログインし直します。

.. figure:: images/mod3-3-4.png
   :scale: 50%
   :align: center

- 「Next」ボタンを押します。

.. figure:: images/mod3-3-5.png
   :scale: 20%
   :align: center

- ライセンス画面が出ます。「Next」ボタンを押します。

.. figure:: images/mod3-3-6.png
   :scale: 20%
   :align: center

(中略)

.. figure:: images/mod3-3-7.png
   :scale: 20%
   :align: center

- プロビジョニング画面がでますので、「LTM」のチェックを外して「APM」にチェックを入れます。「Next」ボタンを押すと再起動の確認がでるのでOKを押します。

.. figure:: images/mod3-3-8.png
   :scale: 20%
   :align: center

- SSL証明書の確認がなされますが、デフォルトのまま、「Next」ボタンを押します。

.. figure:: images/mod3-3-9.png
   :scale: 20%
   :align: center

- ホスト名、タイムゾーン、Rootのパスワードを設定します。「Next」ボタンを押します。

.. figure:: images/mod3-3-10.png
   :scale: 30%
   :align: center

- この後、Standard Network Configurationの「Next」を押すことでウィザード形式にて冗長化も含めた設定が可能ですが、ここではスタンドアローン構成にするため、Advanced Network Configurationの「Finished」ボタンを押します。

.. figure:: images/mod3-3-11.png
   :scale: 20%
   :align: center