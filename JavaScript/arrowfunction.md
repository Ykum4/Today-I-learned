#arrow関数でのthis

アロー関数のthisは、関数を囲んでいる実行コンテキストのthisの値が設定されます。

JavaScriptでの関数のthisは、呼ばれ方によって決定されるという特徴があります。このため、関数が呼び出されるたびにthisが異なる可能性がありました。

ES5からは呼び出し方に関わらずthisの値を固定するためにbind()が導入されましたが、アロー関数は自動的にthisを設定することで、これまでの問題をより簡単に解決することができます。

```
'use strict'
function task(callback) {
  callback();
}

var ES5Chicken = {
  egg: "egg",
  wakeup: function(){
    //関数呼び出しのthisはundefinedになってしまうためthis.eggはundefiedになる。
    // そのためbindで関数の外側のスコープをthisに設定する。
    task(function(){
      console.log("ES5(コケコッコー), this.egg")
    }.bind(this));
  }
}

const ES6Chicken = {
  egg: 'egg',
  wakeup: function(){
    //アロー関数は、自動的に関数の外側のスコープがthisに設定される
    task(() => {
      console.log("ES6(コケコッコー), this.egg");
    });
  }
};

ES5Chicken.wakeup();
ES6Chicken.wakeup();
```