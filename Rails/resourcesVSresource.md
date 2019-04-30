#ResourcesとResourceの違いについて
resourceはidを含めずshow, editアクションを生成できる。
- idつきのパスが生成されない。show, editアクションの実行に、idが必要ない場合に有効。
- indexアクション用のルーティングが生成されない。

```
# 生成されるルーティング
 new_users GET    /users/new(.:format)  users#new
edit_users GET    /users/edit(.:format) users#edit
     users GET    /users(.:format)      users#show
           PATCH  /users(.:format)      users#update
           PUT    /users(.:format)      users#update
           DELETE /users(.:format)      users#destr
```