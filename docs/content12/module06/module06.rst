冗長化設定
======================================

Active機 (big50)での設定
--------------------------------------

- HA用VLANとSelf-IPの設定

.. code-block:: bash

   (tmos)# create net vlan HA interfaces replace-all-with { 1.3 }
   (tmos)# create net self HA-ip address 10.1.30.50/24 vlan HA allow-service default


- Centralized management (cm) ≒ Device Management設定の変更

BIG-IP間の冗長化では、各デバイスが持つ証明書によって信頼関係を結びます。
その証明書を、初期値のホスト名から、新しく設定したホスト名に変更します。
(GUIでは自動的に実施してくれますが、CLIでは必要なステップです。)

.. code-block:: bash

   (tmos)# mv cm device bigip1 big50.f5jp.local


- Device Mangementで、各DeviceのConfigsync、Mirrorアドレス、Failoverアドレスを設定した部分に該当します。

.. code-block:: bash

   (tmos)# modify cm device big50.f5jp.local { configsync-ip 10.1.30.50 mirror-ip 10.1.30.50 mirror-secondary-ip 10.1.20.50 unicast-address {{ ip 10.1.30.50 }} }


- 一旦cm設定を消去します。このことで、冗長化に必要な設定 (証明書など)が新しいホスト名で再生成されます。

.. code-block:: bash

   (tmos)# delete cm trust-domain all


- NTP同期の設定をします。

.. code-block:: bash

   (tmos)# modify sys ntp servers add { 10.1.20.202 }


- 一旦TMSHから抜けて、BASHに戻り、NTP同期状態を確認します。

.. code-block:: bash

   (tmos)# quit
   config # ntpq -p
        remote           refid      st t when poll reach   delay   offset  jitter
   ==============================================================================
   *10.1.20.202     133.243.238.164  2 u   39  256  377    0.537    4.167   2.251


- 再び、TMSHへ戻ります。

.. code-block:: bash

   config # tmsh
   (tmos)#


- コンフィグ保存

.. code-block:: bash

   (tmos)# save sys config


Standby機 (big40)での設定
--------------------------------------

Standby機で、冗長化に必要な設定を実施します。

- 初期設定

.. code-block:: bash

   (tmos)# modify sys global-settings gui-setup disabled
   (tmos)# modify sys global-settings hostname big40.f5jp.local
   (tmos)# modify sys ntp timezone Japan


- VLAN設定

.. code-block:: bash

   (tmos)# create net vlan external interfaces replace-all-with { 1.1 }
   (tmos)# create net vlan internal interfaces replace-all-with { 1.2 }
   (tmos)# create net vlan HA interfaces replace-all-with { 1.3 }


- Self-IP設定

.. code-block:: bash

   (tmos)# create net self external-ip address 10.1.10.40/24 vlan external
   (tmos)# create net self internal-ip address 10.1.20.40/24 vlan internal allow-service default
   (tmos)# create net self HA-ip address 10.1.30.40/24 vlan HA allow-service default


- 冗長化用の設定

.. code-block:: bash

   (tmos)# mv cm device bigip1 big40.f5jp.local
   (tmos)# modify cm device big40.f5jp.local { configsync-ip 10.1.30.40 mirror-ip 10.1.30.40 mirror-secondary-ip 10.1.20.40 unicast-address { { ip 10.1.30.40 }}}
   (tmos)# delete cm trust-domain all


- NTP設定

.. code-block:: bash

   (tmos)# modify sys ntp servers add { 10.1.20.202 }


- adminのパスワード変更

.. code-block:: bash

   (tmos)# modify auth password admin
   changing password for admin
   new password:
   confirm password:


- コンフィグ保存

.. code-block:: bash

   (tmos)# save sys config


Active機 (big50)での設定 (再度)
--------------------------------------

- Device-Trustの実施

.. code-block:: bash

   (tmos)# modify cm trust-domain Root add-device { device-ip 10.1.30.40 device-name big40.f5jp.local username admin password ilovef5 ca-device true }


- Device-Groupの設定

.. code-block:: bash

   (tmos)# create cm device-group Device-Group-001 { type sync-failover devices add { big50.f5jp.local big40.f5jp.local }}


- Floating-IPの設定

.. code-block:: bash

   (tmos)# create net self external-flo-ip address 10.1.10.70/24 traffic-group traffic-group-1 vlan external
   (tmos)# create net self internal-flo-ip address 10.1.20.70/24 traffic-group traffic-group-1 vlan internal allow-service default


- コンフィグ保存

.. code-block:: bash

   (tmos)# save sys config


- Config-Syncの実行

.. code-block:: bash

   (tmos)# run cm config-sync to-group Device-Group-001


Active機 (big50)での実行
--------------------------------------

冗長化を構成した最初だけ、アドレスの大きいほうがActiveになります。
よって、本ガイドでは、1号機 (big50)がActiveとなるので、Traffic-Groupを2号機 (big40)へ切り替えてみます。

.. code-block:: bash

   (tmos)# run sys failover standby traffic-group traffic-group-1

