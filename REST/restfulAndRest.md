#ステートレスとステートフルの違い

```
まずは、ステートフルの例:

客: こんにちは
店員: いらっしゃいませ。○○バーガーへようこそ
客: ハンバーガーセットをお願いします
店員: サイドメニューは何になさいますか?
客: ポテトで
店員: ドリンクは何になさいますか?
客: ジンジャーエールで
店員: +50円でドリンクをLサイズにできますがいかがですか?
客: Mでいいです
店員: 以上でよろしいですか?
客: はい
店員: かしこまりました
これはいたって普通の会話に見える。では、ステートレスな場合はどうなのか。

客: こんにちは
店員: いらっしゃいませ。○○バーガーへようこそ
客: ハンバーガーセットをお願いします
店員: サイドメニューは何になさいますか?
客: ハンバーガーセットをポテトでお願いします
店員: ドリンクは何になさいますか?
客: ハンバーガーセットをポテトとジンジャーエールでお願いします
店員: +50円でドリンクをLサイズにできますがいかがですか?
客: ハンバーガーセットをポテトとジンジャーエール(M)でお願いします
店員: 以上でよろしいですか?
客: ハンバーガーセットをポテトとジンジャーエール(M)でお願いします。以上
店員: かしこまりました
```

**ステートレスに関しては明らかに冗長である**

ステートフルの会話に関して2回目以降の会話は客(クライアント)はそれまでの前提（ハンバーガーセット)について言及しなくてもよかった。
それは店員（サーバー）が客(クライアント)の注文状態を覚えていたからである。
店員は客が’ハンバーガーセットのポテトを頼んでいる’ということを覚えている。
これをアプリケーション状態、もしくはセッション状態と呼ぶ。次に客が何かドリンクを注文するとセッション状態をハンバーガーセットのポテトでコーラとして更新する

ステートレスとは「状態がない」という意味になるのでサーバーはクライアントのセッション情報を保持していないということになる。