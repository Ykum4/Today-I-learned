#deviseでsign_in or sign_outをした後のroutingを設定

deviseの場合はoverrideする必要がある。
新規登録のpath変更であれば**devise:contorollers xxx**コマンドで作成されるカスタマイズ可能なcontrollerを作成しregistrationsControllerでoverrideが可能になる。

##sign_out
**sign_out**の場合、adminなどdeviseのモデルを複数持ちたい状況があると思う。
その際はApplicationControllerにて
```
def after_sign_out_path_for(resource_or_scope)
  if resource_or_scope == :customer
    root_path
  elsif resource_or_scope == :organizer
    new_organizer_session_path
  end
end
```
を記入してあげるとうまくいく。

##sign_in
```
def after_sign_in_path_for(resource)
  case resource
    when Organizer
      admin_events_path
  end
end
```
これでうまくいく。

[参考](https://github.com/plataformatec/devise/wiki/How-To:-Change-the-redirect-path-after-destroying-a-session-i.e.-signing-out)
