デバイストラスト設定 ※Active機 (big50.f5jp.local)側から実施
==========================================================

デバイストラスト設定にて、冗長化する機器間で信頼関係を結びます。

.. note::
   以降は、Active機 (big50.f5jp.local)からのみ、設定します。


- 「Device Management」→「Device Trust」→「Device Trust Members」を選択し、「Add」ボタンを押します。

.. figure:: images/mod7-5-1.png
   :scale: 20%
   :align: center

- ”Peer“を選択し、Standby機 (big40.f5jp.local)のIPアドレスと管理者ID(Admin)とパスワードを指定します。「Retrieve Device Information」ボタンを押します。

.. figure:: images/mod7-5-2.png
   :scale: 20%
   :align: center

- Standby機 (big40.f5jp.local)の証明書情報が表示されます。「Device Certificate Matches」ボタンを押します。

.. figure:: images/mod7-5-3.png
   :scale: 20%
   :align: center

- Standby機のHostnameを確認し、「Add Device」を押します。

.. figure:: images/mod7-5-4.png
   :scale: 20%
   :align: center

- 承認されたデバイスとして登録された状態です。

.. figure:: images/mod7-5-5.png
   :scale: 20%
   :align: center

- 「Device Management」→「Devices」で見ると、bigip50.f5jp.local (self)に加え、Standby機 (big40.f5jp.local)も表示されます。 (ここは確認のみです。)

.. figure:: images/mod7-5-6.png
   :scale: 20%
   :align: center
