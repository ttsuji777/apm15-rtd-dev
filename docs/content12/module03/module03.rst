ネットワークの設定
======================================

- VLAN設定と確認

.. code-block:: bash

   (tmos)# create net vlan external interfaces replace-all-with { 1.1 }
   (tmos)# create net vlan internal interfaces replace-all-with { 1.2 }
   (tmos)# list net vlan
   net vlan external {
       fwd-mode 13
       if-index 400
       interfaces {
           1.1 { }
       }
       tag 4094
   }
   net vlan internal {
       fwd-mode 13
       if-index 416
       interfaces {
           1.2 { }
       }
       tag 4093
   }


- Self-IPの設定と確認

.. code-block:: bash

   (tmos)# create net self external-ip address 10.1.10.50/24 vlan external
   (tmos)# create net self internal-ip address 10.1.20.50/24 vlan internal allow-service default
   　
   (tmos)# list net self
   net self internal-ip {
        address 10.1.20.50/24
        allow-service {
             default
        }
        traffic-group traffic-group-local-only
        vlan internal
   }
   net self external-ip {
        address 10.1.10.50/24
        traffic-group traffic-group-local-only
        vlan external
   }


- ルーティングの設定と確認

.. code-block:: bash

   (tmos)# create net route default-GW gw 10.1.10.1 network default
   
   (tmos)# list net route
   net route default-GW {
       gw 10.1.10.1
       network default
   }

