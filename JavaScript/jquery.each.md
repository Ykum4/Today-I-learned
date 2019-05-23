#jQueryでのeach文について

```javascript
HTML要素.each(function(index, element){
  //繰り返し処理を記入
});
```
```html
<ul>
  <li>sample1</li>
  <li>sample2</li>
  <li>sample3</li>
</ul>
```

```javascript
$('li').each(function(index, ele){
  console.log(index); => 0, 1, 2,,,,
  console.log($(ele).text()); => sample1, sample2,,,
})
```
わざわざ$(ele)にしているのはtext()メソッドがjQueryのメソッドでありそれを使用出来るようにするため。


##配列やオブジェクトに対するeachメソッドの使い方
array = [3, 6, 2];

```javascript
$.each(array, function(index, value){
  console.log(index + ':' + value);
  // => 0: 3, 1: 6,,,,
})
```
