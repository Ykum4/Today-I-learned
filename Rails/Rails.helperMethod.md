#Railsでhelperメソッドを自作して使用する
helperメソッドはlink_toやsubmit_tagのようなviewで用いるメソッドのこと。
これをRailsでは自作できる。
helperメソッドの実体は**module**

- helperのinclude
moduleなのでincludeする必要がある思うがRails5ではデフォルトで全てinludeされる。

```
 By default, each controller 
   # will include all helpers. These helpers are only accessible on the controller through <tt>#helpers</tt> |
   # 
   # In previous versions of \Rails the controller will include a helper which |
   # matches the name of the controller, e.g., <tt>MyController</tt> will automatically |
   # include <tt>MyHelper</tt>. To return old behavior set +config.action_controller.include_all_helpers+ to +false+. 
```

***意図しないhelperを呼んでしまうことがあるかもしれないので下記を追加すればデフォルトでなくなる。***
```ruby:config/application.rb
module xxx
  class Application < Rails::Application
    config.action_controller.include_all_helpers = false #これをセット！！
  end
end
```
(https://github.com/rails/rails/blob/3464cd5c288323ca115a4929d1e6b435c4afc8d4/actionpack/lib/action_controller/metal/helpers.rb#L8)

```
module xxxHelper
  def test
    "test1"
  end
end
```
helperファイルが作られるのでそこに記述をしてviewで呼び出す。

```
<h1><%= test %> => test1が表示される。
```