Traffic-group-1のActive/Standbyの切替え
==========================================================

Traffic-group-1のActive/Standbyの切替え
----------------------------------------

デフォルトでは、管理IPアドレス設定の大きい値を持つものがTraffic-group-1のActive機になりますが、マニュアルで強制的にActiveとStandbyを切替えます。

- アクティブ機の「Device Management」→「Traffic Groups」からTraffic-group-1を選択し、「Force to Standby」ボタンを押します。

.. figure:: images/mod7-9-1-1.png
   :scale: 20%
   :align: center

- 確認のポップアップがでるので、「Force to Standby」ボタンを押します。

.. figure:: images/mod7-9-1-2.png
   :scale: 100%
   :align: center

- その結果、ActiveからStandbyに変わります。

.. figure:: images/mod7-9-1-3.png
   :scale: 20%
   :align: center

- StandbyだったBIG-IPはActiveになります (※big40.f5jp.localで確認)。

.. figure:: images/mod7-9-1-4.png
   :scale: 20%
   :align: center

クライアントからの接続確認
--------------------------------------

:doc:`../../content05/module02/module02` 参照。 

再度traffic-group-1の切替え、クライアントからの通信が復旧するかを確認してください。
