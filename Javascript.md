# jQuery
- jQueryオブジェクト
$('li') => jQueryオブジェクトは[]配列のようになっている。

- indexメソッド

#jquery
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
