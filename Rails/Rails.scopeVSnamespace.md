#Routingを設定するときのscopeとnamespaceの違い
```
namespace :admin do 
  resoures :products # => /admin/products etc...
end

scope :admin do 
  resources :prosucts # => products/new etc...
end
```

コントローラーへのアクセスの仕方が違う