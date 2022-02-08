================================================
iRulesの使い方
================================================

| iRulesはイベントベースのスクリプト言語で、アプリケーショントラフィック操作をカスタマイズ可能です。

.. note::
|  iRulesの文法詳細に関しては、こちらのページをご参照下さい。https://clouddocs.f5.com/api/irules/


| iRulesの作成は、BIG-IPのマネージメント管理画面 (TMUI)から実行可能です。
| また、F5 DevCentralが推奨するVisual Studio Code (VS Code)向けの拡張機能として、「F5 Networks iRules (https://marketplace.visualstudio.com/items?itemName=bitwisecook.irule)」があります。 


本ガイドではTMUIのiRules機能を使って、簡易的に、以下のようなiRuleを設定してみます。


**「HTTPリクエストに含まれるUser-Agentヘッダによって、アクセスするサーバを変える」**


具体的には、

| ・	FireFoxの場合は、10.1.20.201:80へ
| ・	Chrome (Firefox以外のブラウザ)の場合は、10.1.20.202:80へ

接続する、というルールを作成します。

.. toctree::
   :titlesonly:
   :caption: 目次:
   :glob:

   module**/module**