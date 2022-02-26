冗長化のネットワークサンプル
======================================

もう一台BIG-IPを追加して、L3構成の冗長化設定を行います。


.. figure:: images/mod7-2.png
   :scale: 20%
   :align: center


[Active機 (big50.f5jp.local) 設定項目]

.. csv-table:: :header: "項目","名称","設定値"

   "ホスト名","","big50.f5jp.local"
   "管理インタフェース","","10.1.1.5"
   "Externalインタフェース","external","10.1.10.50"
   "Internalインタフェース","internal","10.1.20.50"
   "デフォルトゲートウェイ","Default-GW","10.1.10.1"
   "仮想サーバ","NetAccess-001_vs","10.1.10.60:443"
   "PPPアダプタ用IPプール","NetAccess-001_Ip","10.1.20.211-220"
   "認証サーバ (Active Directory)","NetAccess-001_aaa_srvr","10.1.20.100"
   "DNSサーバ (Active Directory)","","10.1.1.2"
   "NTPサーバ","","10.1.20.202"
   "サーバが存在するネットワーク","","10.1.20.0/24"
   "HA用インタフェース","HA","10.1.30.50"
   "External共用 (floating)IPアドレス","External-flo-ip","10.1.10.70"
   "Internal共用 (floating)IPアドレス","Internal-flo-ip","10.1.20.70"

[Standby機 (big40.f5jp.local) 設定項目]

.. csv-table:: :header: "項目","名称","設定値"

   "ホスト名","","big40.f5jp.local"
   "管理インタフェース","","10.1.1.4"
   "Externalインタフェース","external","10.1.10.40"
   "Internalインタフェース","internal","10.1.20.40"
   "デフォルトゲートウェイ","Default-GW","10.1.10.1"
   "仮想サーバ","NetAccess-001_vs","(設定同期によりコピー)"
   "PPPアダプタ用IPプール","NetAccess-001_Ip","(設定同期によりコピー)"
   "認証サーバ (Active Directory)","NetAccess-001_aaa_srvr","(設定同期によりコピー)"
   "DNSサーバ (Active Directory)","","10.1.1.2"
   "NTPサーバ","","10.1.20.202"
   "サーバが存在するネットワーク","","(設定同期によりコピー)"
   "HA用インタフェース","HA","10.1.30.40"
   "External共用 (floating)IPアドレス","External-flo-ip","(設定同期によりコピー)"
   "Internal共用 (floating)IPアドレス","Internal-flo-ip","(設定同期によりコピー)"


このサンプルではNTPサーバを"10.1.20.202"とし、BIG-IPはこのサーバとの時刻同期を行うことします。
(冗長化を行うBIG-IP同士は、時刻を合わせておく必要があります。)


BIG-IP間のHA (High Availability) VLANは、冗長化の制御パケットをやり取りする専用のVLANです。ExternalやInternal VLANを利用することも可能ですが、HA専用のVLANを追加することを推奨しています。よって、本構成においては、HA VLANを追加しています。
