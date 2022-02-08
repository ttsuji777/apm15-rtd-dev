showコマンドのサンプル
======================================

いくつかのshowコマンド (設定の確認コマンド)を記載します。

コネクションテーブルの確認
--------------------------------------

クライアントPCから、設定したSSH (22) Virtual Serverへアクセスし、コネクションテーブルの状態を確認します。

- 現存する全コネクションの確認

.. code-block:: bash

   (tmos)# show sys connection
   10.1.30.40:12028  10.1.30.50:1026  10.1.30.40:18649  10.1.30.50:1026  udp  0  (tmm: 1)  none  none
   10.1.20.50:123  10.1.20.202:123  10.1.20.50:123  10.1.20.202:123  udp  2  (tmm: 0)  none  none
   10.1.30.50:38234  10.1.30.40:1026  10.1.30.50:38234  10.1.30.40:1026  udp  0  (tmm: 0)  none  none
   Total records returned: 3

- 確認したいコネクションの絞込み

.. code-block:: bash

   (tmos)# show sys connection cs-client-addr 10.1.10.100
   Sys::Connections
   10.1.10.100:49930  10.1.10.60:80  any6.any  any6.any  tcp  5  (tmm: 1)  none  none
   10.1.10.100:49931  10.1.10.60:80  10.1.20.70:49931  10.1.20.202:80  tcp  5  (tmm: 0)  none  none
   Total records returned: 2


- 絞り込んだコネクションの詳細

.. code-block:: bash

   (tmos)# show sys connection cs-client-addr 10.1.10.100 all-properties
   Sys::Connections
   10.1.10.100:49931 - 10.1.10.60:80 - 10.1.20.70:49931 - 10.1.20.202:80
   ---------------------------------------------------------------------
     TMM           0
     Type          any
     Acceleration  none
     Neuron Rules  none
     Protocol      tcp
     Idle Time     19
     Idle Timeout  300
     Unit ID       1
     Lasthop       /Common/external 52:54:00:65:ad:80
     Server Nexthop /Common/internal 52:54:00:d4:7d:9f
     Ingress Dest  none
     Virtual Path  10.1.10.60:80
     Conn Id 0  
                
                         ClientSide        ServerSide
     Client Addr  10.1.10.100:49931  10.1.20.70:49931
     Server Addr      10.1.10.60:80    10.1.20.202:80
     Bits In                   5.0K             34.8K
     Bits Out                 35.2K              5.0K
     Packets In                   6                 5
     Packets Out                  6                 6
   
   Total records returned: 1


ハードウェアに関わる情報 (CPUの詳細やシリアル番号等)の確認
------------------------------------------------------

.. code-block:: bash

   (tmos)# show sys hardware


各パーティションのOSの確認
------------------------------------------------------

.. code-block:: bash

   (tmos)# show sys software


現在利用中のOSバージョンの確認
------------------------------------------------------

.. code-block:: bash

   (tmos)# show sys version


Virtual Serverの状態確認
------------------------------------------------------

.. code-block:: bash

   (tmos)# show ltm virtual ssh-vs-001 raw

