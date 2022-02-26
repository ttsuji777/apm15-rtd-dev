[VPEサンプル-4] マクロを使う
=======================================================

VPEには、マクロ機能があります。繰り返し利用されるポリシーをマクロ化して再利用する、またはデフォルトで用意されている便利なマクロを利用することもできます。ここでは、以下2つの要件に対して、デフォルトで用意されているマクロを利用する例を示します。

- Active Directory認証の誤り回数をカウントしたい。さらに指定回数を超えたらロックし、ロック解除するまで使えないようにしたい。
- AndroidとiOSは同じ設定なので、一つの設定にまとめたい。

AD認証の誤り回数カウント
--------------------------------------

- まず、ユーザエントリの存在しない空のLocal User DBのInstanceを作ります。「Access」 → 「Authentication」 → 「Local User DB」 → 「Instances」で、右上の「Create New Instance」をクリックします。

.. note::
   Local User DBの利用は、少人数ユーザの場合や検証時に有効です。

.. figure:: images/mod6-6-1-1.png
   :scale: 20%
   :align: center

- VPE設定に戻ります。ここまでの設定では以下の状態になっています。「Logon Page」と「ADAuth」の2つをボックスの右上「×」をクリックして、削除します。

.. figure:: images/mod6-6-1-2.png
   :scale: 20%
   :align: center

- 以下の状態になりますので、「Add New Macro」ボタンを押します。

.. figure:: images/mod6-6-1-3.png
   :scale: 20%
   :align: center

- 「Select macro template:」から「AD auth and LocalDB lockout」を選択し、Saveボタンを押します。

.. figure:: images/mod6-6-1-4.png
   :scale: 20%
   :align: center

- 以下の「＋」をクリックすると、マクロが展開されます。

.. figure:: images/mod6-6-1-5.png
   :scale: 20%
   :align: center

- 「*」部分は設定が不十分であることを表しています。以降、「*」の部分を設定していきます。

.. figure:: images/mod6-6-1-6.png
   :scale: 20%
   :align: center

- 「LocalDB - Read」をクリックすると、以下の画面が現れます。設定したDBインスタンス (この例では"AD_lockout_counts")を選択し、「Save」ボタンを押します。

.. figure:: images/mod6-6-1-7.png
   :scale: 20%
   :align: center

- 「AD Auth」をクリックすると、以下の画面が現れます。設定済みのActive DirectoryServer設定を選択し、「Save」ボタンを押します。

.. figure:: images/mod6-6-1-8.png
   :scale: 20%
   :align: center

- 「LocalDB - Write (Reset)」をクリックすると、以下の画面が現れます。設定したDBインスタンス (この例では"AD_lockout_counts")を選択し、「Save」ボタンを押します。

.. figure:: images/mod6-6-1-9.png
   :scale: 20%
   :align: center

- 「LocalDB - Write (Incr)」をクリックすると、以下の画面が現れます。設定したDBインスタンス (この例では"AD_lockout_counts")を選択し、「Save」ボタンを押します。

.. figure:: images/mod6-6-1-10.png
   :scale: 20%
   :align: center

- 本サンプルでは、「AD Query」の前にマクロを入れることにします。「AD Query」の前の「+」をクリックします。

.. figure:: images/mod6-6-1-11.png
   :scale: 20%
   :align: center

- 「Macros」タブで、設定した「Ad auth and LocalDB lockout」を選択し、「Add Item」ボタンを押します。

.. figure:: images/mod6-6-1-12.png
   :scale: 20%
   :align: center

- 以下の状態になりますので、「Apply Access Policy」をクリックして設定を適用します。

.. figure:: images/mod6-6-1-13.png
   :scale: 20%
   :align: center

クライアントからのアクセス
^^^^^^^^^^^^^^^^^^^^^^^^^

- まずは、クライアントPCから正しいIDとパスワード (F5 UDF Labの場合は**test1001/ilovef5!**)でアクセスします。「Access」 → 「Authentication」 → 「Local User DB」 → 「Users」を確認します。すると、ユーザ: test1001がエントリされていることが分かります。

.. figure:: images/mod6-6-1-1-1.png
   :scale: 20%
   :align: center

- 次に、「誤ったパスワード」で3回程度アクセスしてみます。以下のように、アクセスが拒否されたメッセージが表示されます。

.. figure:: images/mod6-6-1-1-2.png
   :scale: 100%
   :align: center

- 「Access」 → 「Authentication」 → 「Local User DB」 → 「Users」を確認すると、ユーザ: test1001がロックアウトされていることが分かります。対象ユーザを選択して「Unlock User」をクリックすると解除が可能です。

.. figure:: images/mod6-6-1-1-3.png
   :scale: 20%
   :align: center

同じ設定をまとめる
--------------------------------------

要件として、「iOSとAndroidは同じ設定を行う」と仮定します。iOSとAndroidそれぞれに同じ設定を追加しても問題はないですが、見た目上、少し煩雑になります。そこで、ここではサンプルとして、「共通のマクロを生成して再利用する」という設定を行います。

- ここで一旦、iOSの分岐上にあるボックス全てを削除します。その後、「Add New Macro」ボタンをクリックします。

.. figure:: images/mod6-6-2-1.png
   :scale: 20%
   :align: center

- ここではサンプルとして「AD auth and resources」を選択して、「Save」ボタンを押します。

.. figure:: images/mod6-6-2-2.png
   :scale: 20%
   :align: center

- 追加したマクロ: 「AD Aurh and resources」の「*」マークの付いたボックス: 「AD Auth」と「Resource Assign」をそれぞれ設定します (ここでは、設定内容は任意のもので結構です。)。
- その後、iOSとAndroidの分岐の「+」をクリックしてそのマクロを追加します。
- AndroidはEndingが「Deny」になっている場合は「Allow」に変更し、最後に「Apply Access Policy」をクリックして設定を適用します。

.. figure:: images/mod6-6-2-3.png
   :scale: 20%
   :align: center

その他にも、APMでワンタイムパスワードを作成しメールで送信する設定や、AntivirusやFirewallのチェック機能の設定など、すぐに利用できる便利なマクロがありますので、確認してみてください。