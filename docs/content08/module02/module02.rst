各オブジェクトの設定
======================================

DNS/NTP設定
----------------------------------------

認証サーバ (Active Directory)の設定
----------------------------------------

 「Access」 → 「Authentication」 → 「Active Directory」にて、「Create」ボタンを押します。

Lease Poolの設定
----------------------------------------

クライアントに割当てるIPアドレス群：リースプールを設定します。
「Access」 → 「Connectivity / VPN」 → 「Network Access(VPN)」 → 「IPV4 Lease Pools」にて、「Create」ボタンを押します。

Network Accessの設定
----------------------------------------

- 「Access」 → 「Connectivity / VPN」 → 「Network Access (VPN)」 へ移動します。「Network Access List」タブを選択し、右に表示された「Create」ボタンを押すと以下の画面が出ます。以下のように値を入力し、「Finished」ボタンを押します。

- その後、以下のような画面 (タブメニューが追加された画面)に遷移します。

- 次にNetwork Settingsタブを選択し、既に設定したLease Poolを選択します。スプリット・トンネルの設定もここで行います。

- クライアントに割り当てるDNSやhostsを設定します。

Webtopの設定
----------------------------------------

 「Access」 → 「Webtops」を選択します。右上に表示された「Create」ボタンを押すと、以下の画面が現れます。
以下の2ヶ所を設定し、「Finished」ボタンを押します。

Connectivity Profileの設定
----------------------------------------

 「Access」 → 「Connectivity / VPN」 → 「Connectivity」で以下の画面が現れます。右上に表示される「Add」ボタンを押すと、以下の画面が現れます。以下2ヶ所を設定し、「OK」ボタンを押します。

Access ProfileとAccess Policyの設定
----------------------------------------

 - 「Access」 → 「Profiles / Policies」 → 「Access Profiles (Per-Session Policies」を選択し、右上に表示された「Create」ボタンを押して以下のように設定します。

 - 同ページの下方にて、利用したい言語を選択し、「Finished」ボタンを押します。

 - その後、以下の画面に遷移します。ここで、Access Policyを設定するために、「Edit…」をクリックします。

- 以下の画面：Visual Policy Editor (VPE) が表示されます。"Start"と"Deny"の線上にある、「+」をクリックします。

- その後、以下の画面が現れます。「Logon」タブで、「Logon Page」を選択し、「Add Item」ボタンを押します。

- その後、以下の画面が現れます。ここでは特に変更は行わず、「Save」ボタンを押します。

- 以下のような状態になりますので、Logon Pageの後ろにある「+」をクリックします。

- その後、以下の画面が現れます。「Authentication」タブで、「AD Auth」を選択し、「Add Item」ボタンを押します。

- その後、以下の画面が現れます。「Server」の項目で、既に設定したAAAサーバ：Active Directoryを選択し、「Save」ボタンを押します。

- 以下のような状態になります。「AD Auth」の後ろにある、Successful側の「+」をクリックします。

- その後、以下の画面が現れます。「Assignment」タブで、「Advanced Resource Assign」を選択し、「Add Item」ボタンを押します。

- その後、以下の画面が現れます。「Add new entry」ボタンを押して、Expressionを1つ追加します。その下の「Add/Delete」をクリックします。

- その後、以下の画面が現れます。「Network Access」タブで、既に設定したNetwork Accessリソースのチェックボタンにチェックを入れます。

- 「Webtop」タブで、既に設定したNetowrk Access用Webtopのチェックボタンにチェックを入れます。「Update」ボタンを押します。

- その後、以下のような状態になります「Save」ボタンを押します。

- 以下のような状態になります。最後に「Advance Resource Assign」の後ろにある「Deny」を「Allow」に変更する必要があるので、その「Deny」をクリックします。

- 以下のような画面が現れます。「Allow」を選択し、「Save」ボタンを押します。

- VPEの設定は以上ですが、まだ設定した値は適用されていません。左上に表示されている「Apply Access Policy」をクリックすることで、設定が適用されます。




