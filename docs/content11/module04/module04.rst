Standby機 (big40.f5jp.local)の設定
======================================

VLAN設定
--------------------------------------

- Standby機 (big40.f5jp.local)に設定されたVLANは以下のようになります。(Active機と同様です。)

.. figure:: images/mod11-4-1.png
   :scale: 50%
   :align: center

Self-IP設定
--------------------------------------

- Standby機 (big40.f5jp.local)に設定されたSelf IPアドレスは以下のようになります。

.. figure:: images/mod11-4-2.png
   :scale: 20%
   :align: center

Device設定
--------------------------------------

「Device Management」→「Devices」で、自分自身: big40.f5jp.local (self)を選択し、Active機同様に、Device Connectivityの設定を行います。

- ConfigSync設定

.. figure:: images/mod11-4-3-1.png
   :scale: 20%
   :align: center

- Failover Network設定

.. figure:: images/mod11-4-3-2.png
   :scale: 20%
   :align: center

- Mirroring設定

.. figure:: images/mod11-4-3-3.png
   :scale: 20%
   :align: center

NTP設定
--------------------------------------

NTPの設定もActive機同様に行います。

.. figure:: images/mod11-4-4.png
   :scale: 20%
   :align: center
