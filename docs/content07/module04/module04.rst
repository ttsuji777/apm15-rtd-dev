Standby機 (big40.f5jp.local)の設定
======================================

:doc:`../../content03/content03` および :doc:`../../content04/content04` を参照して、Standby機もActive機と同様の初期設定、ネットワーク設定を行います。

VLAN設定
--------------------------------------

- Standby機 (big40.f5jp.local)に設定されたVLANは以下のようになります。(Active機と同様です。)

.. figure:: images/mod7-4-1.png
   :scale: 40%
   :align: center

Self-IP設定
--------------------------------------

- Standby機 (big40.f5jp.local)に設定されたSelf IPアドレスは以下のようになります。Port Lockdownの設定はActive機と同様に、external-ipは"Allow None"、internal-ipおよびHA-ipは"Allow Default"とします。

.. figure:: images/mod7-4-2.png
   :scale: 20%
   :align: center

Device設定
--------------------------------------

「Device Management」→「Devices」で、自分自身: big40.f5jp.local (self)を選択し、Active機同様に、Device Connectivityの設定を行います。

- ConfigSync設定

.. figure:: images/mod7-4-3-1.png
   :scale: 20%
   :align: center

- Failover Network設定

.. figure:: images/mod7-4-3-2.png
   :scale: 20%
   :align: center

- Mirroring設定

.. figure:: images/mod7-4-3-3.png
   :scale: 20%
   :align: center

NTP設定
--------------------------------------

NTPの設定もActive機同様に行います。

.. figure:: images/mod7-4-4.png
   :scale: 20%
   :align: center
