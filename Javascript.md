# jQuery
- jQueryオブジェクト
$('li') => jQueryオブジェクトは[]配列のようになっている。

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
