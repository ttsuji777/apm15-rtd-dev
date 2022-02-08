初期設定
======================================

- GUIで実行されるウィザードの停止

.. code-block:: bash

   (tmos)# modify sys global-settings gui-setup disabled


- ホスト名の設定

.. code-block:: bash

   (tmos)# modify sys global-settings hostname big50.f5jp.local


- 設定の確認

.. code-block:: bash

   (tmos)# list sys global-settings
   sys global-settings {
        gui-setup disabled
        hostname big50.f5jp.local
        mgmt-dhcp disabled
   }


- タイムゾーンの指定と確認

.. code-block:: bash

   (tmos)# modify sys ntp timezone Japan
   (tmos)# list sys ntp
   sys ntp {
        timezone Japan
   }


- adminのパスワード変更

.. code-block:: bash

   (tmos)# modify auth password admin
   changing password for admin
   new password:
   confirm password:
