- indexメソッド　

  #javascript
  <ul>
    <li>インデックス１</li>
    <li>インデックス２</li>
    <li>インデックス３</li>
  </ul>
  $(function(){
   $('li').click(function({
      var index = $('li').index($(this));
   })

  });

 indexを用いるとindex番号を取得する事が出来る。

- mapメソッド

  const numbers = [1, 2, 3];

  const doubledNumbers = numbers.map((number) => {　 //=> というのはアロー関数と呼ばれるもの。
    return number * 2;    //returnする事でconsole.logの呼ばれているところで値を返している。
  });

  console.log(doubledNumbers);

  => [2, 4, 6]
  mapメソッドは配列内の全ての要素に処理を行い返り値を新しい配列として返す。

#Scope
これはjavascriptだけの話ではないがローカルスコープとスローバルスコープがある
ローカルスコープ
その変数が定義された関数内でしか使えない！
function info() {   var name = “ren”;
  # 変数nameは関数info内では使える。
}
x 関数の外では変数nameを使うことはできない。

グローバルスコープ
var name = “ren”
function info(){   #この中では変数nameを使うことができる。
}
当然関数の外でも変数nameは使える（nameのスコープ内であるから)