#firebaseについて

メッセージ送信機能実装するとき
まずfirebaseはNoSQLなのでRailsとはデータの保存の仕方が違う
Collection
	Document
		(field)
		・text:
		・image:
		・timestamp:
という様な構造を取っている。
collectionが(messages)でDocument(message)、fieldがカラムの様な役割を持つ
documentは一意になる。（同じ名前のdocumentが作成されることはない）

collectionはテーブル
documentはレコードの様なもの
fieldはカラムである
変わっているのがドキュメントには異なる情報のセットを含めることができることである。
例えばusesコレクションに2つのドキュメントがあるとして
１つのフィールドには(name, age)を含めていて
もう１つのフィールドには(name, age, sex)の様な別のフィールドを持たすことができる。
これはRailsでやっていたDB構造とは大きく異なる。



コレクションには値を持つ生のフィールドを直接含めることはできない。
##コレクション
// cloud firestoreを初期化している。
var db = firebase.firestore();

データはドキュメントに保存される。
コレクションやドキュメントは明示的に作成する必要はないので明示しなければランダムなidが振られる。

db.collection(“users”).add({
 	first: “abe”,
	last: “tuyoshi”,
 	age: 21
})

コレクションのデータを確認するにはfirebaseサイト上のコンソールを見るのが一番早いが
db.collection("users").get().then((querySnapshot) => {
    querySnapshot.forEach((doc) => {
        console.log(`${doc.id} => ${doc.data()}`);
    });
});
としても読み取れる。

##ドキュメント
ドキュメントを作成して値を与える場合はset()メソッドを用いる。
db.collection("cities").doc("LA").set({
    name: "Los Angeles",
    state: "CA",
    country: "USA"
})
これでcollection, docを明示的にしているので追加可能になる。
setをaddにしてらエラーが出る


1.
db.collection("cities").add({
    name: "Tokyo",
    country: "Japan"
})

2.
var newCityRef = db.collection(‘cities’).doc();
newCityRef.ser(data);

どちらの場合もdocIDは自動で生成される。
.add(…) and .doc().set(…)は完全に同等である。

ドキュメントの更新
var washingtonRef = db.collection("cities").doc("DC");

// Set the "capital" field of the city 'DC'
return washingtonRef.update({
    capital: true
})

ネストされたオブジェクトのフィールドを更新

// ドキュメンの作成
var frankDocRef = db.collection("users").doc("frank");
frankDocRef.set({
    name: "Frank",
    favorites: { food: "Pizza", color: "Blue", subject: "recess" },
    age: 12
});

// To update age and favorite color:
// 年齢を更新してネストされたフィールドに好きな色カラムを追加
db.collection("users").doc("frank").update({
    "age": 13,
    "favorites.color": "Red"
})

更新された日時を記録するフィールドを作成することも可能である。
var docRef = db.collection('objects').doc('some-id');

// Update the timestamp field with the value from the server
var updateTimestamp = docRef.update({
    timestamp: firebase.firestore.FieldValue.serverTimestamp()
});



##リファレンス
fieldの値を参照したい場合はリファレンスを作成する
var db = firebase.firestore();
var message1DocumentRef = db.collection(‘messages’).doc(‘message1);

リファレンスはデータベース内の場所を示す軽量なオブジェクトなのでリファレンスを作成してもネットワーク操作は実行されない。

##サブコレクション
チャットルーム作成の際roomAなどのドキュメントに膨大のデータを保存をよくない方法である。
なのでroomAというドキュメントにサブのコレクションを作ってやる。
rooms
	roomA
		name: “my chat room”
			messages(subCollection)
				message1(document)
					from: “who”
					msg: “hey”
この場合のメッセージ参照は
var messageRef = db.collection(‘rooms’).doc(‘roomA’)
						.collection(‘messages’).doc(‘message1’);となる。








