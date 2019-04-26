# Credentialsの使い方

最終課題では使用するAPIキーを環境変数として定義して呼び出していたがその時の選択肢としてあったのがgem dotenvもしくはconfig, secrets.ymlを使用するだった。
**Rails5.2からはcredentials.yml.encが使用できるようになったのでこの使い方を記述して行こうと思う**

credentials.yml.encはファイルを直接編集することは出来ないのでviを利用する！
credentialsファイルの内容は暗号化されているので編集が出来ない。

```
Q+GBLmbxagoirjyHWkJDdaMdg0cJR...
```

viを利用してcredentials.yml.encを編集する場合は環境変数: EDITORにviを指定してrails credentials:editコマンドを実行！

```
$ EDITOR="vi" bin/rails credentials:edit
```

.bash_profileに環境変数: EDITORを設定しておけば先頭に付けていたEDITOR="vi"は不要になる。

## Credentialsファイルの読み取り方法
credentials.yml.encに設定した資格情報を取り出すにはRails.application.credentials.xxxを指定する。

```
aws:
  access_key_id: 123
  #=> Rails.application.credentials.aws[:access_key_id]
  secret_access_key: 345
  #=> Rails.application.credentials.aws[:secret_access_key]

secret_key_base: 8be8e637d755f79c799048bed8be0c...
#=> Rails.application.credentials.secret_key_base
```
credentialsファイルから読み取りが出来ているかを確認する際はrails cで確認すると良い！

##config/master.key
credentials.yml.encはmaster.keyを利用して暗号化・複合されている。
このmaster.keyは初めからgitignoreされていてファイルが存在しない場合は**rails credentials:editコマンドを実行した際に生成される。もしくは手動でもファイルは作れる（keyとなる文字列が有効でないと意味ないが）**
