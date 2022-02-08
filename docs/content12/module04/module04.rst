PoolとVirtual Serverの設定
======================================

HTTP (80)用PoolとVS
--------------------------------------

- Pool設定と確認

.. code-block:: bash

   (tmos)# create ltm pool http-pool-01 { members add { 10.1.20.201:http { } 10.1.20.202:http { } } monitor http }
   (tmos)# list ltm pool
   ltm pool http-pool-01 {
       members {
           10.1.20.201:http {
               address 10.1.20.201
               session monitor-enabled
               state up
           }
           10.1.20.202:http {
               address 10.1.20.202
               session monitor-enabled
               state up
           }
       }
       monitor http 
   }


- VS設定

.. code-block:: bash

   (tmos)# create ltm virtual http-vs-001 { destination 10.1.10.60:http pool http-pool-01 profiles add { http } source-address-translation { type automap } }
   (tmos)# list ltm virtual
   ltm virtual http-vs-001 {
       creation-time 2019-07-01:18:07:15
       destination 10.1.10.60:http
       ip-protocol tcp
       last-modified-time 2019-07-01:18:07:15
       mask 255.255.255.255
       pool http-pool-01
       profiles {
           http { }
           tcp { }
       }
       source 0.0.0.0/0
       source-address-translation {
           type automap
       }
       translate-address enabled
       translate-port enabled
       vs-index 23
   }


- パーシステンス設定

.. code-block:: bash

   (tmos)# modify ltm virtual http-vs-001 { persist replace-all-with { source_addr }}
   (tmos)# list ltm virtual
   ltm virtual http-vs-001 {
       creation-time 2019-07-01:18:07:15
       destination 10.1.10.60:http
       ip-protocol tcp
       last-modified-time 2019-07-01:18:07:15
       mask 255.255.255.255
       persist {
           source_addr {
               default yes
           }
       }
       pool http-pool-01
       profiles {
           http { }
           tcp { }
       }
       source 0.0.0.0/0
       source-address-translation {
           type automap
       }
       translate-address enabled
       translate-port enabled
       vs-index 23
   }


HTTP (80)用PoolとVS
--------------------------------------

後のshowコマンドで、コネクションテーブルの確認が行いやすいので、SSH用VSも作っておきます。

- Pool設定

.. code-block:: bash

   (tmos)# create ltm pool ssh-pool-001 { members add { 10.1.20.201:ssh { } 10.1.20.202:ssh { } } monitor tcp }
   (tmos)# list ltm pool ssh-pool-001 
   ltm pool ssh-pool-001 {
       members {
           10.1.20.201:ssh {
               address 10.1.20.201
               session monitor-enabled
               state up
           }
           10.1.20.202:ssh {
           address 10.1.20.202
               session monitor-enabled
               state up
           }
       }
       monitor tcp 
   }


- VS設定

.. code-block:: bash

   (tmos)# create ltm virtual ssh-vs-001 { destination 10.1.20.60:ssh pool ssh-pool-001 profiles replace-all-with { tcp } source-address-translation { type automap } }
   (tmos)# list ltm virtual ssh-vs-001 
   ltm virtual ssh-vs-001 {
       creation-time 2019-07-01:18:18:09
       destination 10.1.20.60:ssh
       ip-protocol tcp
       last-modified-time 2019-07-01:18:18:09
       mask 255.255.255.255
       pool ssh-pool-001
       profiles {
           tcp { }
       }
       source 0.0.0.0/0
       source-address-translation {
           type automap
       }
       translate-address enabled
       translate-port enabled
       vs-index 24
   }

