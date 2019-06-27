#PHPにおけるクラスとインスタンスについて
「public」とは … 変数やメソッドに「public」をつけることで、その属性は「クラスの外から参照・変更することができる」ということを表します。
「private」とは … 変数やメソッドに「private」をつけることで、その属性は「そのクラスの内側でのみ参照・変更することができる」ということを表します。

```php
<?php 
  class Person {
    public $height;
  }
  $me = new Person();  // インスタンス化
  // 参照するときは->で表す
  $me->height = 170;
  echo $me->height; //これで出力
?>
```

**staticについて**
Rubyで言うクラスメソッドのような感じ
personクラスを考えた時に「走る」、「歩く」などのメソッドは全てのインスタンスが実行するものでその行為自体を一つの場所に作り各インスタンスがその場所を参照するようにした方が効率が良い。

```php
  class Person {
    public static function greeting(){
      echo 'こんにちは！';
    }
    public function some_other_method(){
      //クラス内でstatic関数を呼ぶ際は[self::]とする。
      self::greeting();
    }
  }

  //クラス外からstatic関数を呼び出す際は「class::」とする
  Person::greeting();
```

date関数では 以下のような形式で日付を取得することができます。

date("Y") // 現在の年
date("n") // 現在の月
date("j") // 現在の日付
date("w") // 現在の曜日

mktime 関数を date関数と絡めて使用することにより、「1日前」「3ヶ月後」「10年後」等というような指定が可能になります。
mktime関数は以下の項目から構成されています。

mktime( 時, 分, 秒, 月, 日, 年 )

このmktime関数を date関数の第二引数として以下の例のように渡すと 月の最後の日を取得することができます。
このように記述することにより、「翌月の0日」→「今月の最終日」というように認識されます。

date("j", mktime(0,0,0, $month+1, 0, $year))