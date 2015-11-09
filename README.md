iscsiStorage01 Cookbook
=======================
ソフトレイヤーのパフォーマンス・ストレージやエンデュランス・ストレージのブロック・ストレージサービスは、iSCSIストレージとして提供されるサービスです。 このクックブックは、これらのiSCSIストレージの認証ファイルの作成、マルチパス設定、fstab設定、マウントまでを実行します。


要件(Requirements)
------------

#### CHEFのバージョン
- Chef 12.5 以上 (これより前のバージョンで確認していません。)

#### 対応オペレーティングシステム
- CentOS 7.x - Minimal Install (64 bit) 
- CentOS 6.x - Minimal Install (64 bit) 
- Debian GNU/Linux 8.x jessie/Stable - Minimal Install (64 bit) 
- Ubuntu Linux 14.04 LTS Trusty Tahr - Minimal Install (64 bit) 

#### 対応ストレージ
- Endurance Block Storage
- Performance Block Storage
このクックブックの適用前までに、ブロック・ストレージがオーダーが完了している必要があります。

#### SoftLayer カスタマーポータルの操作
- ブロック・ストレージがオーダーが完了していること
- 仮想サーバーまたはベアメタルサーバーのオーダーが完了していること
- ブロック・ストレージの Authorized Hosts に対象サーバーが含まれていること

Authorized Hostsのリストへの追加方法は、ソフトレイヤー活用ガイドの次の章をご参照ねがいます。
- [1.6.6 パフォーマンス・ストレージを利用するには？](https://www.change-makers.jp/post/10318)
- [1.6.7 エンデュランス・ストレージを利用するには？](https://www.change-makers.jp/post/10319)


属性(Attributes)
----------
サーバーインスタンスから、これらのiSCSIブロック・ストレージへアクセスするためには、次の属性が正しく設定されていなければなりません。

#### iscsiStorage01::default
<table>
  <tr>
    <th>Key</th>
    <th>Type</th>
    <th>Description</th>
    <th>備考</th>
  </tr>
  <tr>
    <td>["iscsi_target_ipaddr"]</td>
    <td>String</td>
    <td>iSCSIのターゲットIP</td>
    <td>必須</td>
  </tr>
  <tr>
    <td>["iscsi_user_name"]</td>
    <td>String</td>
    <td>購入時付与されるユーザID</td>
    <td>必須</td>
  </tr>
  <tr>
    <td>["iscsi_user_password"]</td>
    <td>String</td>
    <td>ユーザIDのパスワード</td>
    <td>必須</td>
  </tr>
  <tr>
    <td>["initiator_name"]</td>
    <td>String</td>
    <td>iSCSI の World Wide ID</td>
    <td>必須</td>
  </tr>
  <tr>
    <td>["multipath_device"]["name1"]</td>
    <td>String</td>
    <td>マルチパスのメタデバイス名</td>
    <td>必須 /dev/mapper/**** </td>
  </tr>
  <tr>
    <td>["multipath_device"]["mount1"]</td>
    <td>String</td>
    <td>マウントポイント</td>
    <td>必須 /data1など</td>
  </tr>
  <tr>
    <td>["iscsi_host"]</td>
    <td>String</td>
    <td>択一 master/slave</td>
    <td>選択必須</td>
  </tr>
</table>



Usage
-----
#### iscsiStorage01::default
TODO: Write usage instructions for each cookbook.

e.g.
Just include `iscsiStorage01` in your node's `run_list`:

```json
{
  "name":"my_node",
  "run_list": [
    "recipe[iscsiStorage01]"
  ]
}
```

Contributing
------------
TODO: (optional) If this is a public cookbook, detail the process for contributing. If this is a private cookbook, remove this section.

e.g.
1. Fork the repository on Github
2. Create a named feature branch (like `add_component_x`)
3. Write your change
4. Write tests for your change (if applicable)
5. Run the tests, ensuring they all pass
6. Submit a Pull Request using Github

License and Authors
-------------------
Authors: TODO: List authors
