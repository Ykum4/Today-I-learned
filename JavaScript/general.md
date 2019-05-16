#javascriptを書く時scriptタグを使えばコードを幾つでも読み込むことが出来るので他人が宣言した定数や変数との衝突を避けるためにコードをブロックで囲って置くのが良い。

#オブジェクト
[とても分かりやすい記事](https://developer.mozilla.org/ja/docs/Learn/JavaScript/Objects/Basics)

サブ名前空間
name: {first: 'bob', last: 'smith'}
=
name: {
  first: 'bob',
  last: 'smith'
}

```
```


##クラス
概念などはRubyのクラスとインスタンスとそっくり。

```
  //クラスメソッドの定義
  class Player { //親クラス
    constructor(name, score) { //メソッド initializeメソッドのような感じ？
      this.name = name;
      this.score = score;
    }

    showInfo(){
      console.log(`name: ${this.name} score: ${this.score}`)
    }
  }

  class soccerPlayer extends Player { // 子クラス
    constructor(name, score, number) {
      super(name, score);  //親クラスで定義しているものを継承している。
      this.number = number;
    }
    kick() {
      console.log(`${this.name} got a shoot!!`);
    }
  }

  const kuma = new Player('kuma', 22); => kumaインスタンが出来る。
  kuma.name => kuma

  //メソッドの呼び出し
  kuma.showInfo();

  const honda = new soccerPlayer('honda', 33, 4);
  honda.kick();

```

##オブジェクト型の挙動
                          x        y
let x = [1, 2];         [1, 2]    undefined
let y = x;              [1, 2]     ←←・ xへの参照
x[0] = 5; => x = [5, 2]
y => [5, 2]

オブジェクト型の場合、"="とした時に値そのものがコピーされるのではなくてyはxの場所にあるよというような**参照**を示すだけなのでxを更新した時にyの値もxと同じになっている。

##要素を作成

```javascript:
  const h1 = document.createElement('h1');  //作成したい要素
  h1.textContent = 'Title'  //テキストを挿入
  document.body.appendChild(h1);

  const p = document.createElement('p');  //作成したい要素
  p.textContent = 'Title'  //テキストを挿入
  document.body.appendChild(p);

  // h1とp要素の間に要素を作成したいケースではinsertBeforeを使う

  const h2 = document.createElement('h2');  //作成したい要素
  h2.textContent = 'Sub Title'  //テキストを挿入
  document.body.insertBefore(h2, p); 
  //insertBefore(追加したい要素, 追加したい後の要素);

  //copy
  const copy = p.cloneNode(true);
  document.body.appendChild(copy);

```

