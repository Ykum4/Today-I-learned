#Javascript
javascriptにおいて関数というのは値になる。

function add(a, b) {
  return a + b;
}

console.log(add(1, 2)); => 3

関数は変数に入れることができる

const addFunc = function add(a, b) {
  return a + b;
}

console.log(addFunc(1, 2)); => 3

**関数を値として扱うには後ろのカッコをつけずに記述する**

function add(a, b) {
  return a + b;
}

// 定義した関数を変数に入れる
const addFunc = add;

console.log(add(1, 2), addFunc(1, 2)); => 3