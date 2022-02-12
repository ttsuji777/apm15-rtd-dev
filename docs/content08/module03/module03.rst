Access ProfileとAccess Policyの設定
======================================

- 「Access」 → 「Profiles / Policies」 → 「Access Profiles (Per-Session Policies」を選択し、右上に表示された「Create」ボタンを押して以下のように設定します。

.. figure:: images/mod8-3-1.png
   :scale: 20%
   :align: center

- 同ページの下方にて、利用したい言語を選択し、「Finished」ボタンを押します。

.. figure:: images/mod8-3-2.png
   :scale: 20%
   :align: center

- その後、以下の画面に遷移します。ここで、Access Policyを設定するために、「Edit…」をクリックします。

.. figure:: images/mod8-3-3.png
   :scale: 20%
   :align: center

- 以下の画面: Visual Policy Editor (VPE)が表示されます。"Start"と"Deny"の線上にある、「+」をクリックします。

.. figure:: images/mod8-3-4.png
   :scale: 20%
   :align: center

- その後、以下の画面が現れます。「Logon」タブで、「Logon Page」を選択し、「Add Item」ボタンを押します。

.. figure:: images/mod8-3-5.png
   :scale: 20%
   :align: center

- その後、以下の画面が現れます。ここでは特に変更は行わず、「Save」ボタンを押します。

.. figure:: images/mod8-3-6.png
   :scale: 20%
   :align: center

- 以下のような状態になりますので、Logon Pageの後ろにある「+」をクリックします。

.. figure:: images/mod8-3-7.png
   :scale: 20%
   :align: center

- 以下の画面が現れます。「Authentication」タブで、「AD Auth」を選択し、「Add Item」ボタンを押します。

.. figure:: images/mod8-3-8.png
   :scale: 20%
   :align: center

- 以下の画面が現れます。「Server」の項目で、既に設定したAAAサーバ: Active Directoryを選択し、「Save」ボタンを押します。

.. figure:: images/mod8-3-9.png
   :scale: 20%
   :align: center

- 以下のような状態になります。「AD Auth」の後ろにある、Successful側の「+」をクリックします。

.. figure:: images/mod8-3-10.png
   :scale: 20%
   :align: center

- 以下の画面が現れます。「Assignment」タブで、「Advanced Resource Assign」を選択し、「Add Item」ボタンを押します。

.. figure:: images/mod8-3-11.png
   :scale: 20%
   :align: center

- 以下の画面が現れます。「Add new entry」ボタンを押して、Expressionを1つ追加します。その下の「Add/Delete」をクリックします。

.. figure:: images/mod8-3-12.png
   :scale: 20%
   :align: center

- 以下の画面が現れます。「Network Access」タブで、既に設定したNetwork Accessリソースのチェックボタンにチェックを入れます。

.. figure:: images/mod8-3-13.png
   :scale: 20%
   :align: center

- 「Webtop」タブで、既に設定したNetowrk Access用Webtopのチェックボタンにチェックを入れます。「Update」ボタンを押します。

.. figure:: images/mod8-3-14.png
   :scale: 20%
   :align: center

- 以下のような状態になります。「Save」ボタンを押します。

.. figure:: images/mod8-3-15.png
   :scale: 20%
   :align: center

- 以下のような状態になります。最後に「Advance Resource Assign」の後ろにある「Deny」を「Allow」に変更する必要があるので、「Deny」をクリックします。

.. figure:: images/mod8-3-16.png
   :scale: 20%
   :align: center

- 以下のような画面が現れます。「Allow」を選択し、「Save」ボタンを押します。

.. figure:: images/mod8-3-17.png
   :scale: 20%
   :align: center

- VPEの設定は以上ですが、まだ設定した値は適用されていません。左上に表示されている「Apply Access Policy」をクリックすることで、設定が適用されます。

.. figure:: images/mod8-3-18.png
   :scale: 20%
   :align: center





